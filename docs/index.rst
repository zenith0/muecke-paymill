muecke_paymill
===========

What is it?
-----------

muecke_paymill is the integration of the payment processor `Paymill`_ for `LFS`_.

Installation
------------

#. Register at https://www.paymill.com

#. Within ``buildout.cfg`` add ``muecke_paymill`` to eggs within the
   ``django`` section::

    eggs =
        django-muecke == 0.7.0b1
        gunicorn
        muecke_paymill

#. Run the installer::

    $ bin/buildout -Nv

#. Within ``settings.py`` add ``muecke_paymill`` to ``INSTALLED_APPS``::

    INSTALLED_APPS = [
        ...
        "muecke_paymill",
    ]

#. Within ``settings.py`` add ``muecke_paymill`` to ``LFS_PAYMENT_METHOD_PROCESSORS``::

    LFS_PAYMENT_METHOD_PROCESSORS = [
        ["muecke_paymill.models.PaymillPaymentMethodProcessor", "Paymill"],
    ]

#. Within ``settings.py`` add muecke_paymill specific settings::

    PAYMILL_PUBLIC_KEY = your_public_key
    PAYMILL_PRIVATE_KEY = your_private_key

#. Restart your instance

#. Within the LFS Management go to ``Shop/Payment Methods`` and add a new
   payment processor.

    * Select ``Paymill`` for the ``Module`` field.
    * Select ``Credit Cart`` for the ``Type``field.

#. Within ``base.html`` load the ``muecke_paymill`` specific javascript. A tag
   comes with ``muecke_paymill``::

    <!-- Other load tags go here -->

    {% load muecke_paymill_tags %}

    <!-- muecke javascript goes here -->

    {% muecke_paymill_js %}

See also
--------

* `LFS Settings <http://docs.getmuecke.com/en/latest/developer/settings.html>`_

.. _`Paymill`: https://www.paymill.com
.. _`LFS`: http://pypi.python.org/pypi/django-muecke
