---
title: "Pulling My Hair Out: Belkin F6D4050 V1"
date: 2010-02-11
forum: Networking &amp; Wireless
---

### Post by nigsy on 2010-02-11
Hi all,
Linux newbie so go easy!!

I have a belkin F6D4050 v1 USB dongle and I can not get it to work and trust me I have tried EVERYTHING.
I have followed the guide to the wrapper at the start of this forum and can't get anywhere, I have tried other solutions from other forums with no joy, I was directed to "railtech" for native drivers, but all the links are broken on that site.

So I back to the wrapper and windows drivers.

**Lsusb output:**

Bus 001 Device 011: ID 050d:935a Belkin Components 

definitely plugged in!

**ndiswraaper -l output:**

rt2870 : driver installed
    device (050D:935A) present

So it's picking up the device and the driver (I have tried the vista driver as well with no luck)

**lshw -C network output:**

WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: nForce2 Ethernet Controller
       vendor: nVidia Corporation
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: a1
       serial: 00:0e:a6:17:27:45
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.64 latency=0 maxlatency=20 mingnt=1 multicast=yes

Only picks up the onboard Ethernet card. I have tried blacklisting this device. Still no joy.

**lsmod | grep ndis output:**

nigsy@Tylers-PC:~$ lsmod | grep ndis
ndiswrapper           185532  0 
nigsy@Tylers-PC:~$ dmesg | grep -e ndis -e wlan
[   13.284852] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   14.344767] usbcore: registered new interface driver ndiswrapper
[ 1355.648092] usbcore: deregistering interface driver ndiswrapper
[ 1355.671688] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[ 1355.950797] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'MmGetSystemRoutineAddress'
[ 1355.950983] ndiswrapper (load_sys_files:206): couldn't prepare driver 'rt2870'
[ 1355.951498] ndiswrapper (load_wrap_driver:108): couldn't load driver rt2870; check system log for messages from 'loadndisdriver'
[ 1355.951563] usbcore: registered new interface driver ndiswrapper
[ 2117.042429] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'MmGetSystemRoutineAddress'
[ 2117.042614] ndiswrapper (load_sys_files:206): couldn't prepare driver 'rt2870'
[ 2117.043115] ndiswrapper (load_wrap_driver:108): couldn't load driver rt2870; check system log for messages from 'loadndisdriver'
[ 2847.230361] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'MmGetSystemRoutineAddress'
[ 2847.230546] ndiswrapper (load_sys_files:206): couldn't prepare driver 'rt2870'
[ 2847.231063] ndiswrapper (load_wrap_driver:108): couldn't load driver rt2870; check system log for messages from 'loadndisdriver'

This points to an issue with the driver I believe?
I seem to be going round in circles with this one, can anyone help??
Thanks in advance.

Forgot to add version:  Linux 9.10 Karmic Koala

Nigel.

---

### Post by The Toxic Mite on 2010-02-11
Hey!

Do you still have the Driver CD for it? If you do, find the **Windows XP** drivers for your dongle, and copy them to wherever you wish. Then, place your Ubuntu CD in, go to Applications > Accessories > Terminal and type in the following commands:

```

sudo apt-get install ndiswrapper
sudo apt-get install ndisgtk

```

Once that's done, go to System > Administration > Windows Wireless Drivers, click "Install New Driver", and locate the rt2870.inf file that you copied earlier. Reboot, and you should have wireless now. :)

BTW - I say this because the rt2870 drivers from the Ralink website are a mess. Also, Ubuntu's default driver under-performs.

---

### Post by nigsy on 2010-02-11
> **The Toxic Mite said:**
> Hey!

Do you still have the Driver CD for it? If you do, find the **Windows XP** drivers for your dongle, and copy them to wherever you wish. Then, place your Ubuntu CD in, go to Applications > Accessories > Terminal and type in the following commands:

```

sudo apt-get install ndiswrapper
sudo apt-get install ndisgtk

```Once that's done, go to System > Administration > Windows Wireless Drivers, click "Install New Driver", and locate the rt2870.inf file that you copied earlier. Reboot, and you should have wireless now. :)

BTW - I say this because the rt2870 drivers from the Ralink website are a mess. Also, Ubuntu's default driver under-performs.


Cheers for your reply. I already have the wrapper installed, and the driver I am using is the one off the original Belkin Install disc
In the "Wireless Network Drivers screen" it says rt2870: Hardware Present.
I have tried both downloaded and straight off the cd versions of the driver (both vista and XP), I'm sticking with the XP driver, as most people seem to have better luck with that.

---

### Post by nigsy on 2010-02-12
Bump!!

---

### Post by nigsy on 2010-02-12
> **nigsy said:**
> Bump!!


C'mon guys, someone must have the answer, or do I go back to windows??

---

### Post by SeaJayEmm on 2010-02-14
How did you install the driver? Did you use ndisgtk? or ndiswrapper?

---

### Post by SeaJayEmm on 2010-02-14
Also, did you use the correct drivers. There is a 64 bit driver and a 32 bit driver.

---

### Post by lyngawyfrmu2 on 2010-07-11
I too have the same issue as above. I have been using the correct driver from the installation cd provided with the usb stick. I have followed everything stated here and another guide showing how to install through ndiswrapper also. Both do not seem to work. I am on the said machine right now plugged in wired. It says the stick is present and the driver is installed correctly...but still nada???


Just a note. I tried to do this stuff when I was still using Karmic...since I have tried it, I have now been updated to 10.4.....so any help regarding any differences with 9.10 and 10.4 are appreciated!

---

### Post by qelqoth on 2010-10-14
I am also experiencing problems with this.  This morning, my girlfriend installed Ubuntu 8.04 and all the latest updates and apart from ndiswrapper and ndisgtk, nothing else has been installed.  Then we installed the XP_2K drivers for the Belkin F6D4050 v1 USB wireless network adapter.  When we use lsusb, we get the following:

> Bus 004 Device 003: ID 05e3:0710 Genesys Logic, Inc. USB 2.0 33-in-1 Card Reader
Bus 004 Device 002: ID 050d:935a Belkin Components 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  


Then when we use ndiswrapper -l, we get this:

> rt2870 : driver installed
    device (050D:935A) present


However, we don't seem to be getting any further.  The Belkin network adapter is not showing up in the network connections menu.  If anyone could help us further with this, we'd really appreciate it as she's tearing her hair out right now.  Thanks.   :)

---

### Post by qelqoth on 2010-10-14
Also pulled up this information, in case it helps:

> kay@pileofpants:~$ sudo modprobe ndiswrapper
kay@pileofpants:~$ tail /var/log/messages
Oct 14 15:09:46 pileofpants dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.domain_name
Oct 14 15:09:46 pileofpants dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Oct 14 15:09:46 pileofpants dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Oct 14 15:09:46 pileofpants dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu
Oct 14 15:09:47 pileofpants kernel: [   59.667568] NET: Registered protocol family 10
Oct 14 15:09:47 pileofpants kernel: [   59.668002] lo: Disabled Privacy Extensions
Oct 14 15:09:50 pileofpants pulseaudio[5759]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Oct 14 15:09:50 pileofpants pulseaudio[5759]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Oct 14 15:12:03 pileofpants kernel: [  195.473723] UDF-fs: Partition marked readonly; forcing readonly mount
Oct 14 15:12:03 pileofpants kernel: [  195.496930] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'Belkin_F6D4050v1', timestamp 2009/01/23 04:36 (103c)
kay@pileofpants:~$ 


---

### Post by CommuneOfLoon on 2010-10-14
[http://ubuntuforums.org/showthread.php?t=1509403&highlight=belkin](http://ubuntuforums.org/showthread.php?t=1509403&highlight=belkin)

Post #2 got my **** working :)

---

