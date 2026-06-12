---
title: "BlueZ - Sdp hci channel selection"
date: 2009-02-04
forum: Networking &amp; Wireless
---

### Post by fabrition on 2009-02-04
Hi, 
I have to search for a service using sdptool (i'm using bluez3), but i need to specify the hci channel to use in that sdp request (this because i need to do many sdp requests and i want to perform them on different hci channels).
Following i report the first part of the sdptool help :

sdptool - SDP tool v3.36
Usage:
        sdptool [options] <command> [command parameters]
Options:
        -h              Display help
        -i              Specify source interface

It says that using the option -i i can specify the source interface. But in fact i can only specify -i 0: even if i mounted four bluetooth dongles to the pc, when i specify -i 1, -i 2 and so on i've got the following output (where a mac address is in the place of XX...): 
Failed to connect to SDP server on XX:XX:XX:XX:XX: No route to host

Another strange observation: if i specify hci1 in the -i option it works, but it works also with hci7, hci8 and so on... it seems to ignore the -i option if i write hciX (but it doesn't throw en error...)

I tried to browse the web but i find nothing... :-(

Now my questions are:
Is that "source interface" the hci channel?
      If yes: why it doesn't accept all the available hci channels, but only 0? 
      If not: how can i specify the hci channel?
Thanks in advance, 
greetings,
Fabris.

---

