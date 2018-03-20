.. _v2/payments-cancel:

Payments API v2: Cancel payment
===============================
``DELETE`` ``https://api.mollie.com/v2/payments``

Authentication: :ref:`API keys <guides/authentication>`, :ref:`OAuth access tokens <oauth/overview>`

Some payment methods are cancellable for an amount of time, usually until the next day. Or as long as the payment status
is open. Payments may be cancelled manually from the Dashboard, or automatically by using this endpoint.

The ``canBeCancelled`` property on the :ref:`Payment object <v2/payments-get>` will indicate if the payment can be
cancelled.

Parameters
----------
Replace ``id`` in the endpoint URL by the payment's ID, for example ``tr_7UhSN1zuXS``.

Response
--------
``200`` ``application/hal+json; charset=utf-8``

A payment object is returned, as described in :ref:`Get payment <v2/payments-get>`.

Example
-------

Request
^^^^^^^
.. code-block:: bash

   curl -X DELETE https://api.mollie.com/v2/payments/tr_WDqYK6vllg \
       -H "Authorization: Bearer test_dHar4XY7LxsDOtmnkVtjNVWXLSlXsM"

Response
^^^^^^^^
.. code-block:: http

   HTTP/1.1 200 OK
   Content-Type: application/hal+json; charset=utf-8

   {
       "resource": "payment",
       "id": "tr_WDqYK6vllg",
       "mode": "live",
       "createdAt": "2018-03-19T10:18:33+00:00",
       "amount": {
           "value": "35.07",
           "currency": "EUR"
       },
       "description": "Order 33",
       "method": "banktransfer",
       "metadata": null,
       "status": "cancelled",
       "cancelledAt": "2018-03-19T10:19:15+00:00",
       "details": {
           "bankName": "Stichting Mollie Payments",
           "bankAccount": "NL53ABNA0627535577",
           "bankBic": "ABNANL2A",
           "transferReference": "RF12-3456-7890-1234"
       },
       "profileId": "pfl_QkEhN94Ba",
       "sequenceType": "oneoff",
       "redirectUrl": "https://webshop.example.org/order/33/",
       "_links": {
           "self": {
               "href": "https://api.mollie.com/v2/payments/tr_WDqYK6vllg",
               "type": "application/json"
           },
           "documentation": {
               "href": "https://www.mollie.com/en/docs/reference/payments/delete",
               "type": "text/html"
           }
       }
   }