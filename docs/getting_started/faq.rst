Frequently Asked Questions (FAQ)
================================


Installation
------------

When I install from PyPI, it complains "Could not find a version that satisfies the requirement".
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
We have only uploaded SPU binaries with limited version.
Please check https://pypi.org/project/spu/#files to confirm whether your environment meets the requirement of tags.
Please refer to https://github.com/pypa/manylinux to check the tags.

What is the requirement for glibc?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

If you are using the binaries provided from us, the minimum requirement of glibc is 2.17.
If you couldn't meet this restriction, please build your own binary from source.


Usage
-----

How can I check logs of SPU?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

You have to enable these flags in :doc:`/reference/runtime_config` when you start SPU cluster:

- enable_action_trace
- enable_pphlo_trace

How could I use Cheetah protocol?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

You only need to select Cheetah protocol in :doc:`/reference/runtime_config`. Please search for *protocol* field in RuntimeConfig.
And please keep in mind that Cheetah protocol is a 2PC protocol.


General
-------

Does SPU support PyTorch?
~~~~~~~~~~~~~~~~~~~~~~~~~~

At this moment, we only ship SPU with JAX support. But theoretically, all the frontend languages which could be transferred into XLA could be
consumed by SPU compiler, please check other opensource projects which work on transferring other languages to XLA.

I have met huge inconsistency between SPU result and Plaintext(JAX) result.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Arithmetic operation of SPU is based on Fxp. Please check :doc:`/development/fxp`. In most cases, you have
to choose:

1. Use large field or modify fraction bits.
2. Modify arithmetic ops approximation approach.

But there's no such thing as a free lunch. More accurate result sometimes requires a huger cost.

Could I convert any Jax code to XLA and run by SPU?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Well, first you must make sure your Jax code is **jitable**. You have to apply some tricks to achieve this actually.
Then even your code is jitable, sometime we will still disappoint you since we haven't implemented all XLA ops. Please
check :doc:`/reference/xla_status`. We are working hard to finish them, you have my word!

