---
title: "Inspiron 1501 Wireless Troubles"
date: 2009-02-17
forum: Networking &amp; Wireless
---

### Post by d2macken on 2009-02-17
Hi Everyone,

So let me quickly try to tell you all my story - my girlfriend's dell inspiron 1501 has always given her trouble, and I'll do the occasional 'amateur fix', however it had gotten to the point where no web browser was stable for more than 3 minutes... so with a stroke of genius, I decided to download/install Ubuntu Hardy via Wubi. After getting over the first hurdles of screen resolution and flicker, I'm faced with the lack of wireless connectivity.

Now, I realize that this is a well documented problem, however I am unable to fix it, no matter which of the many google generated fixes I try. So, I'm hoping that someone can ask me the right questions and get me to post the proper stats so that we can get it working. We'll probably have to start by somehow cleaning up the messes I've made by trying other fixes...

Lastly, the router I use is 2wire, and it's set for a WEP open password. When I use the 'connect manager' thingy  on my toolbar, my local network shows up, however I am never able to connect...

Any and all help would be immensely appreciated.... thanks

PS. I'm new with Linux and am not super familiar with CLI commands, so you'll have to bear with me.

---

### Post by superprash2003 on 2009-02-17
post output of the following commands from the terminal
1)lshw -C network
2)iwlist scanning
3)iwconfig

---

### Post by d2macken on 2009-02-17
Alrighty, here are the request stats - thanks for the reply

val@val-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:09:d9:7d:b8
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.2.20 latency=64 module=ssb multicast=yes

val@val-laptop:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

val@val-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


Not that it makes a difference, but I did these commands with an ethernet cord plugged in.

Also, in the past, I had run those commands and gotten some meaningful output for the iwconfig, however I've since run a few commands that were supposed to 'get rid of things' before starting a new attempt at ndiswrapper...

---

### Post by d2macken on 2009-02-17
no takers?

---

### Post by superprash2003 on 2009-02-18
which ubuntu are you running?? if 8.10 then follow this [http://www.prash-babu.com/2008/11/how-to-configure-broadcom-wireless-in.html](http://www.prash-babu.com/2008/11/how-to-configure-broadcom-wireless-in.html) .. if not follow this [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff) .. if the first link doesnt work for you , then try the second link.. even though the second link is for feisty it would work!!

---

### Post by d2macken on 2009-02-18
Hi superprash... originally, this was a Hardy problem, however last night, I uninstalled that version and went for intrepid because it is supposed to have better driver sets for this broadcom issue. Anyhow, I've followed the first tutorial you sent me, but I still cannot connect to my router. It sees it, I enter my WEP password, but it can't establish the connection.

What's weird, though, is that if I boot into Windows, I can't connect to the net via wireless either...
When I go to the device manager, both the Broadcom 440X and Dell Wireless 1390 mini-card look fine, but if I launch the "Broadcom Control Suite 2" from the control panel, both of these interfaces have a Red X through them. So, at the CMD prompt, I type ipconfig, and I get a message saying Media Disconnected. Odd...

---

### Post by superprash2003 on 2009-02-19
so you are able to find a wifi network?? have you chosen the right authentication type 64/128 bit etc.. try all combinations if your not sure... also post output of **iwconfig** and **ifconfig** again
  the red cross usually indicates that it is disabled , just right click and enable it

---

