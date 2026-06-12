---
title: "Can't connect to wireless"
date: 2009-11-29
forum: Networking &amp; Wireless
---

### Post by tarat on 2009-11-29
What I am running:
ubuntu 9.10 on a (crappy old) Gateway Model No. MA2 laptop
On the installation CD for my router it says that it is D-Link DIR-615 Ver 3.00
My connection shows up on my mac just as dlink, there's no security or anything fancy. The only other info it gives to me about it is the "base station ID"

I'm a brand new user, I'm used to just clicking the network name, entering the password if there is one, and failing that, shutting off the modem/router power for a few seconds and then turning it back on. I have no idea what I am doing. But I'm determined to figure it out.

What I have tried already:

-installed ndisgtk  and ndiswrapper (then I installed a driver I found; in the ndisgtk window, under the name of the driver, it says "hardware present: no")

-system-administration- hardware drivers (nothing comes up)

- entered commands that I saw in various places (help, forums) into terminal. Here's what it told me:

Following the instructions listed on the wireless troubleshooter:
sudo lshw -C network
it says that my wireless interface is DISABLED (after this point in the troubleshooter it tells me to check that my device is on. Everything is enabled in my BIOS settings, and my router is turned on, my roommate is using it)

iwconfig:
> wlan0
IEEE 802.11bg   ESSID:""
Mode:Managed Frequency:2.412 GHz Access Point: Not associated
Tx-Power=0 dBm
Retry long limit:7 RTS:thr:off Fragment thr:off
Power management:off
Link Quality:0 Signal level:0 Noise level:0
Rx invalid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0ifconfig: no IP comes up

cat /etc/resollv/conf
no such file or directory

Then it tells me to contact my ISP.... but since I know that my internet *is* working, do I really have to?

onto the next step:
gksudo gedit /etc/modprobe.d/aliases

This brings up a blank text document, so I checked the location, there is no file named aliases there.

And that's all the troubleshooter from the help button does, so then I looked at the troubleshooter on the internet:

when I typed in lspci to terminal, this is what looked relevant:

> 02:04.0 Network Controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

00:1e.0 PCI Bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)

00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)it says that if ifconfig brings up ESSID="" (which it does), to see section "configuring WPA Support". wpasupplicant is installed, so I checked the wiki, but it doesn't seem to apply to what I am doing.

My D-Link CD didn't have a .sys file anywhere on it, so I downloaded a driver off of the web that did, and installed it.

Then I went to the ndiswrapper troubleshooting guide stickied in this forum.

ndiswrapper -l gives me:
> installed ndis drivers:
net5513     driver presentI found my card's device ID, searched the google cache of it in there, but unfortunately, the links required a username and password to download, annd since my laptop is past its warranty, I do not have these.

Then I tried 
[FONT=monospace]dmesg | grep -e ndis -e wlan.
When I did it the first time it gave me two lines similar to what ptheas22 posted for the working example, but not the rest, and no errors. Now it isn't doing anything.

And now I am feeling ready to give up. Any help is appreciated! Will post info as needed. 

Edit: wired connection works without any problems, and now I have all my info from that? (IP address, hardware address, etc)
[/FONT]

---

### Post by tarat on 2009-11-29
A few things that I think may be causing a problem:
-etc/modprobe.d/aliases does not exist.
-I may have the wrong driver, but do not know how to find the right one
-my wireless is apparently disabled, despite my router and modem being turned on, and the boot menu telling me that everything is enabled

Can anyone help me fix any of this?

---

### Post by tarat on 2009-11-29
Is there something I forgot? Or is everyone else just as stumped as I am?

---

