============================================================================
 Example Code -- Builtin Topics
============================================================================


Building C++ example
====================
Make sure you are using one of the relevant RTI Data Distribution Service versions, as specified at the top of the Solution.

Before compiling or running the example, make sure the environment variable NDDSHOME is set to the directory where your version of RTI Data Distribution Service is installed.

Run rtiddsgen with the -example option and the target architecture of your choice (for example, i86Win32VS2005). The RTI Data Distribution Service Getting Started Guide describes this process in detail. Follow the same procedure to generate the code and build the examples. Do not use the -replace option.

After running rtiddsgen like this...

C:\local\Builtin_Topics\c++> rtiddsgen -language C++ -example i86Win32VS2005 msg.idl

...you will see messages that look like this:

File C:\local\Builtin_Topics\c++\msg_subscriber.cxx already exists and will not be replaced with updated content. If you would like to get a new file with the new content, either remove this file or supply -replace option.
File C:\local\Builtin_Topics\c++\msg_publisher.cxx already exists and will not be replaced with updated content. If you would like to get a new file with the new content, either remove this file or supply -replace option.

This is normal and is only informing you that the subscriber/publisher code has not been replaced, which is fine since all the source files for the example are already provided.

Running
======
In two separate command prompt windows for the publisher and subscriber, navigate to the objs/<arch> directory and run these commands:

Windows systems:

    * msg_publisher.exe <domain#> 3
    * msg_subscriber.exe <domain#> 5 password foo

UNIX systems:

    * ./msg_publisher <domain#> 3
    * ./msg_subscriber <domain#> 5 password foo

The applications accept up to four arguments:

   1. The <domain #>. Both applications must use the same domain # in order to communicate. The default is 0.
   2. How long the examples should run, measured in samples for the publisher and sleep periods for the subscriber. A value of '0' instructs the application to run forever; this is the default.
   3. (subscriber only) The participant authorization string. This is checked against the authorization that the publisher is expecting. The default is "password".
   4. (subscriber only) The reader authorization string. If and only if the reader's participant didn't get authorized, then this value is checked against the authorization that the publisher is expecting. The default is "Reader_Auth".

While generating the output below, we used values that would capture the most interesting behavior.

Publisher Output
============
Built-in Reader: found participant
        key->'0a1e01dd 000009b8 00000001'
        user_data->'password'
instance_handle: dd011e0ab8090000 01000000c1010000 0000001000000001
Built-in Reader: found subscriber
        participant_key->'0a1e01dd 000009b8 00000001'
        key->'0a1e01dd 000009b8 00000001'
        user_data->'foo'
instance_handle: dd011e0ab8090000 0100000004000080 0000001000000001
publication_matched, current count = 1
Writing msg, count 0
Writing msg, count 1
Writing msg, count 2

Subscriber Output
=============
   x: 0
   x: 1
   x: 2