========================
Team and repository tags
========================

.. image:: http://governance.openstack.org/badges/openstack-ansible-os_panko.svg
    :target: http://governance.openstack.org/reference/tags/index.html

.. Change things from this point on

OpenStack panko
##############

Ansible role that installs and configures OpenStack panko as the alarm
functionality of Telemetry.

This role will install the following:
    * panko-api
    * panko-listener
    * panko-evaluator
    * panko-notifier

The role will configure panko to use MongoDB for data storage, but does
not install or configure MongoDB.

Default Variables
=================

.. literalinclude:: ../../defaults/main.yml
   :language: yaml
   :start-after: under the License.

Required Variables
==================

To use this role, define the following variables:

.. code-block:: yaml

   # Needed for panko to talk to MongoDB
   panko_container_db_password: "secrete"
   # Password used for Keystone panko service user
   panko_service_password: "secrete"
   # Needed for panko to talk to memcached
   memcached_servers: 127.0.0.1
   memcached_encryption_key: "some_key"
   # Needed for panko to locate and connect to the RabbitMQ cluster
   panko_rabbitmq_password: "secrete"
   rabbitmq_servers: "10.100.100.2"
   rabbitmq_use_ssl: true
   rabbitmq_port: 5671
   # Needed to setup the panko service in Keystone
   keystone_admin_user_name: admin
   keystone_admin_tenant_name: admin
   keystone_auth_admin_password: "SuperSecretePassword"
   keystone_service_adminuri_insecure: false
   keystone_service_internaluri_insecure: false
   keystone_service_internaluri: "http://1.2.3.4:5000"
   keystone_service_internalurl: "{{ keystone_service_internaluri }}/v3"
   keystone_service_adminuri: "http://5.6.7.8:35357"
   keystone_service_adminurl: "{{ keystone_service_adminuri }}/v3"
