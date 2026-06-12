---
title: "3 Mobile Broadband Dongle"
date: 2010-04-24
forum: Networking &amp; Wireless
---

### Post by pazzmon92 on 2010-04-24
Recently, I have upgraded to Ubuntu 10.04, just to be ale to use the newest operating system. Previous, I was using Ubuntu 9.10 (I think) and my Wireless 3 Dongle worked perfectly fine, but now with 10.04. My dongle won't create a connection or install properly.

What happens is I click on "3 Connect" (The software) and the 3 wireless menu comes up and says initializing, but doesn't go any further.

any help? :(

---

### Post by alexfish on 2010-04-24
Hi

from your post you say "3 Connect" (The software) . is this the option you are seeing in the network manager. 

could you also post details of these commands from the terminal

Code:

lsusb

Code:

dmesg | grep -e "modem" -e "tty"

also do you have usb modeswitch installed

thanks in advance

alexfish

---

### Post by pdc on 2010-04-24
If you read what Ubuntu say about 10.04 (Lucid Lynx)

.. they say .......

> **Ubuntu Lucid Lynx is in development, use only for testing purposes!!**!

and here is the forum for experienced developers, such as yourself, to post on 

[http://ubuntuforums.org/forumdisplay.php?f=310](http://ubuntuforums.org/forumdisplay.php?f=310)

they do also say

> Please note: Ubuntu Developers do not usually read the forums, to report a problem found in Lucid please report the bug in Launchpad.

Some would suggest that one use the word "CHANGE" rather than the word "upgrade" when installing an OS that is still actively being developed

---

