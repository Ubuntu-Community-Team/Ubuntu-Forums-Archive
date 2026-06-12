---
title: "Huawei E1550 not connecting"
date: 2009-11-24
forum: Networking &amp; Wireless
---

### Post by dob99 on 2009-11-24
I have just bought an Huawei E1550 3G modem for use with 3 Ireland. I am trying to get it working with Kubuntu 9.10.

First of all, I manually created a new Mobile Broadband connection in Network Manager using variations of the following settings:
```
Number: *99#, *99***1#
APN: 3internet, 3ireland, 3ireland.ie
```

Then to get the kernel to recognize the modem, I issue the following:
```
sudo modprobe usbserial vendor=0x12d1 product=0x1001
```
(the values for vendor and product correspond to those output by **lsusb**)

Now, the NetworkManager icon turns into a mobile phone. So, I click on this and select the connection I created above. It appears to be doing something for about 5-10 seconds and then just stops without any information as to why. (When I roll over the icon, a tooltip pops up saying "Obtaining Network Address" and when I roll over the menu entry, a different one pops up with some more information including the message "Preparing to connect".)

The modem works fine in Windows (after the requisite software is installed), but I don't have Windows on my laptop (nor do I feel I should have to). I also tried using the modem in a Windows VM in VirtualBox, but it wasn't able to install the drivers for it unfortunately.

I tried it on Ubuntu 9.10 (on an eeePC) and it all works. The only difference I can see in the settings (between Ubuntu and Kubuntu) is that, in Gnome, I can set the IPv4 settings whereas this does not seem possible in KDE.


Is there any way to see what is actually going on in NetworkManager? (There don't appear to be any logs - at least not in /var/log.) Is there a command-line equivalent I can run to try to get some more information?

Or even better, has anyone had the same problem and been able to solve it?

---

### Post by alexfish on 2009-11-24
look here as well
[http://ubuntuforums.org/showthread.php?t=1336310](http://ubuntuforums.org/showthread.php?t=1336310)

and here

[http://ubuntuforums.org/showthread.php?t=1335118](http://ubuntuforums.org/showthread.php?t=1335118)

keep posting

---

### Post by dob99 on 2009-11-24
Thanks for the quick reply. However, I'm still non-the-wiser. I previously tried adding a udev rule, which didn't seem to help. So, I just tried running the following directly:
```
sudo /lib/udev/modem-modeswitch -d -v 0x12d1 -p 1x1001 -t option-zerocd
```
I got the following response:
```
D: Found mass storage device:
D:   Endpoints: 3
D:   Class:     0xFF
D:   SubClass:  0xFF
D:   Protocol:  0xFF
E: no device found
```

It would appear that it can detect that the modem is present and at least attempt to connect. (I'm guessing this because the phone icon appears when I plug the modem in.)

The best way (I think) to diagnose the problem, would be to get NetworkMamager to provide more information, but I don't know how to go about this.

---

### Post by dob99 on 2009-11-25
OK. I got it working as follows:

1) In a terminal, type
[INDENT][FONT="System"]sudo apt-get install network-manager-gnome[/FONT][/INDENT]
and accept the additional packages.

2) Type
[INDENT][FONT="System"]killall knetworkmanager[/FONT][/INDENT]
This removes the NetworkManager Plasma widget.

3) Run
[INDENT][FONT="System"]nm-connection-editor[/FONT][/INDENT]
and set up your connection.

4) Run
[INDENT][FONT="System"]nm-applet[/FONT][/INDENT]
This will add the Gnome NM Applet to your Notification Area.

5) You can now select and connect to your broadband connection from the Applet's menu.

This is far from an ideal solution. There should be a way to do this in KDE without having to install components from Gnome. (It could even be considered a bug that you can't - or that it appears that you can't.) 

I'm not sure I'm willing to live with this solution as it is and I may switch to Gnome on this laptop for this reason. I also don't know how to permanently replace the KDE NetworkManager applet with Gnome's one. If I have a mind to find out, I will post the instructions here.

---

### Post by dob99 on 2009-11-25
At this point, I'd prefer a command-line solution to either running the Gnome applet in KDE or switching to Gnome. (I'm not particularly happy with Gnome's session management, but that's another discussion altogether.)

Any help on the commands required would be appreciated.

---

### Post by alexfish on 2009-11-25
may be 

[solved] here

[http://ubuntuforums.org/showthread.php?t=1336197](http://ubuntuforums.org/showthread.php?t=1336197)

---

### Post by omegadestroy on 2010-09-24
I'm completely new to the Linux world and badly needs help. I installed Kubuntu 10.04 two days ago and it has been a disaster because it has inconsistencies detecting the e1550. There are instances that it's working but after a reboot/hibernate it goes to a haywire. I need to delete and re-setup the mobile broadband connection settings once Kubuntu detects it after multiple reboots. Another thing I noticed is it's not being recognized as a USB modem to automatically connect as configured hence just a storage device when it's acting up. I'm also using Ubuntu 10.04 on the same netbook but I never got a problem using the same broadband connection. Is there a fix for this?

---

### Post by alexfish on 2010-09-26
> **omegadestroy said:**
> I'm completely new to the Linux world and badly needs help. I installed Kubuntu 10.04 two days ago and it has been a disaster because it has inconsistencies detecting the e1550. There are instances that it's working but after a reboot/hibernate it goes to a haywire. I need to delete and re-setup the mobile broadband connection settings once Kubuntu detects it after multiple reboots. Another thing I noticed is it's not being recognized as a USB modem to automatically connect as configured hence just a storage device when it's acting up. I'm also using Ubuntu 10.04 on the same netbook but I never got a problem using the same broadband connection. Is there a fix for this?

if your connection is 3g, try Sakis3g

details of how to install:

From the terminal:
Codes:

[COLOR=Blue]sudo bash[/COLOR]

[COLOR=Blue]cd /usr/bin[/COLOR]

[COLOR=Blue]wget  'http://www.sakis3g.org/versions/latest/sakis3g.gz'
[/COLOR]
[COLOR=Blue]echo "dda70fd95fb952dbb979af88790d3f6e sakis3g.gz" | md5sum  -c[/COLOR]

You should see: sakis3g.gz: OK

Codes:

[COLOR=Blue]gunzip sakis3g.gz

chmod +x sakis3g[/COLOR]


then  run sakis3g from the terminal

Code:

[COLOR=Blue]sakis3g[/COLOR]


Have  a look through the menus , and try the options from the menu , it won't  harm your system:

regards

alexfish

or download  at
[http://www.sakis3g.org/](http://www.sakis3g.org/)

---

