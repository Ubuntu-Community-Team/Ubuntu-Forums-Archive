---
title: "Kismet, Ubuntu 9.04, Intel 2200BG Wireless Card"
date: 2009-06-10
forum: Networking &amp; Wireless
---

### Post by twistedlndscapes on 2009-06-10
Hello again :)

I have a Dell Inspiron 8600 (before you laugh at that it's my third backup laptop :) ). I'm trying to configure Kismet to work under Ubuntu 9.04. I got Kismet to install correctly. The command "lspci" gives me:

*02:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)*

The command "iwconfig" gives me the interface by the following line:
[I]
eth1      IEEE 802.11g  ESSID:"belkin54g"[/I]

I have edited the kismet.conf file based on what I read through online guides and the configuration file of Kismet to include the following line for the source (based on the example in the configuration file that shows the syntax: source=sourcetype,interface,name):
[I]
source=ipw2200,eth1,eth1[/I]

However, when I "sudo kismet" I get:

*Kismet started with no packet sources defined. No sources were defined or all defined sources encountered unrecoverable errors. kismet will not be able to capture any data until a capture interface is added.*

I then try to add it again through the interface and I get the following:

*Couldn't auto-detect a driver for interface 'eth1'. There may be a problem with the device (such as it not existing) or it may use one of the drivers which cannot be auto-detected. See the README section 'Caveats and quirks for specific drivers' to learn how to configure the specific driver.*

And...

*"ERROR: Failed Kismet client command: ADDSOURCE command failed"*

I see nothing in the README under that section that applies. You can find the same README here ([http://www.kismetwireless.net/documentation.shtml](http://www.kismetwireless.net/documentation.shtml)). Any ideas?

---

### Post by chili555 on 2009-06-10
We may have a few problems here. First, I'd amend my kismet.conf to be:```
source=ipw2200,eth1,[COLOR="Red"]Intel[/COLOR]
```Second, I suggest putting the card in monitor mode manually:```
sudo ifconfig eth1 down
sudo iwconfig eth1 mode monitor
sudo kismet
```Did it start?

---

### Post by twistedlndscapes on 2009-06-10
Nope. Same issues :(

---

### Post by chili555 on 2009-06-11
Please post the following section from kismet.conf. I have posted mine for an example of the wording we need to see. Yours, obviously, will have differences:```
# Sources are defined as:
# source=sourcetype,interface,name[,initialchannel]
# Source types and required drivers are listed in the README under the
# CAPTURE SOURCES section.
# The initial channel is optional, if hopping is not enabled it can be used
# to set the channel the interface listens on.
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
source=ipw3945,wlan0,Intel
```Thanks.

---

### Post by ~aris on 2009-07-09
Thanks. Working great!

---

