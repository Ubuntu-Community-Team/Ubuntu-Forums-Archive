---
title: "Error: Can't open display: hostname when telnet to appserver"
date: 2012-08-03
forum: Networking &amp; Wireless
---

### Post by Petter72 on 2012-08-03
I am using a client running ubuntu 11.04 to connect to Sun Solaris app-server to run an application called XTOP.
On the ubuntu client, I type
xhost +
then telnet to the remote server, then
export DISPLAY=<hostname>:0.0
then I start the application XTOP
XTOP

A warning is then displayed:
Warning:  Your DISPLAY variable is wrongly setup !

Then I get:
/usr/openwin/bin/xmodmap:  unable to open display 'petter-VPCEH1S1E:0.0'

Does anyone have any idea how to solve this ? I do not understand why it says that the display variable is wrongly setup and why the display cannot be opened.

---

