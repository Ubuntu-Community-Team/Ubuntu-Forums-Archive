---
title: "Drivers for internal Qualcomm HS-USB 9212 in Aspire One"
date: 2009-07-15
forum: Networking &amp; Wireless
---

### Post by amartz on 2009-07-15
Does anybody have any hints to getting the internal Qualcomm 3G modem working (HS-USB 9212) in an Acer Aspire One netbook running Ubuntu 9.04 netbook remix? Wireless is OK. Netbook is dual-boot with XP, and 3G works fine with XP. Ubuntu doesn't see the modem, and I suspect it doesn't have the right drivers for it. lsusb returns "Bus 001 Device 004: ID 05c6:9212 Qualcomm, Inc."
Art

---

### Post by amartz on 2009-08-04
I have had good results in getting my 3G modem to work thru UNR 9.04.  If anybody else wants to try what I've done, I'd be willing to collaborate off-line and see if it works for you also.
Art

---

### Post by brownb2 on 2009-08-04
> **amartz said:**
> I have had good results in getting my 3G modem to work thru UNR 9.04.  If anybody else wants to try what I've done, I'd be willing to collaborate off-line and see if it works for you also.
Art

Come on... you can tell the rest of us... we won't bite... does it have something to do with the Linpus "drivers" here...?

[http://support.acer-euro.com/drivers/notebook/as_one_110.html](http://support.acer-euro.com/drivers/notebook/as_one_110.html)

---

### Post by amartz on 2009-08-04
No, it is a combination of loading the Qualcomm drivers mine needs from XP, rebooting to UNR, running the modprobe usbserial command after UNR boots, and modemmanager so that networkmanager shows the connect option for the 3G modem. I looked at your link with the Linpus linux driver. I would think that is specific to whatever kind of internal modem is in that particular Aspire.

---

### Post by Chiapo on 2009-11-25
When I run the modprobe command it returns a FATAL: error about usbserial not found.

---

### Post by amartz on 2009-11-25
> **Chiapo said:**
> When I run the modprobe command it returns a FATAL: error about usbserial not found.

Here's all the notes I compiled from when I set mine up:

First thing, the modem needs it's firmware reloaded every time you turn it on. Without the firmware, it's just an empty shell. I've seen somebody putting together something to load the Qualcomm Gobi firmware from linux, but for now I do it from windows.

Boot to windows first, to load firmware into modem, then reboot to Ubuntu, without powering off.

wiki.ubuntu.com/Networkmanager/Hardware/3G/Probing

art@art-laptop:~$ lsusb
Bus 001 Device 004: ID 05c6:9212 Qualcomm, Inc. 

This is the only command you really need, the chat command is not needed, but is a convenient way to tell if the modem is talking.
~$ sudo modprobe usbserial vendor=0x05c6 product=0x9212
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.

~$ ls -lha /dev/ttyU*
crw-rw---- 1 root dialout 188, 0 2009-07-23 11:29 /dev/ttyUSB0

The probe.txt is as defined in wiki.ubuntu.com/Networkmanager/Hardware/3G/Probing
~$ chat -s -f ~/probe.txt >/dev/ttyUSB0 </dev/ttyUSB0
chat:  Jul 23 11:30:02 +GCAP: +CGSM,+DS,+ES
chat:  Jul 23 11:30:02 +COPS: 0,0,"AT&T",2
chat:  Jul 23 11:30:02 +CREG: 0,1

I would put the modprobe command in the file /etc/rc.local.
That is the last command which is run at boot time. As it is run as root
anyway, there is no need for sudo. To make the change, use the command

sudo gedit /etc/rc.local

and put the line

modprobe usbserial vendor=0x05c6 product=0x9212

_before_ the line

exit 0 
 
Modem Manager software repository, add
deb [http://ppa.launchpad.net/modemmanager/ppa/ubuntu](http://ppa.launchpad.net/modemmanager/ppa/ubuntu) jaunty main 
then run
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys EF2A6AFA
and
sudo apt-get update

goto the Synaptic Package Manager, search for and install modemmanager

run update manager, reboot, make the ttyUSB0 (modprobe), and the Mobile Broadband modem connection shows up when you click on network manager. Edit connections for the modem, go to IPv4 tab, change to Automatic (PPP) addresses only, and manually enter a DNS server address.  I got mine by rebooting back to windows, and doing a IPCONFIG /ALL. Now you can left-click on network manager, and choose the modem to connect.

---

### Post by Chiapo on 2009-11-25
Many thanks to you amartz!

I'll give your instructions another try.

I downloaded a different kernel last night, & the modprobe command now gives no error.
Also, apparently /dev/ttyUSB0 is appearing when I issue ls -lha /dev/ttyUSB*

So it appears I'm getting closer.

Many thanks for your help amartz!

---

