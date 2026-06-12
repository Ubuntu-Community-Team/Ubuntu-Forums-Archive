---
title: "Wireless Adapter Setup"
date: 2005-02-14
forum: Networking &amp; Wireless
---

### Post by frizzy on 2005-02-14
I've searched and searched for a possible solution to my problem, trying to get wireless to work on my ubuntu desktop computer.  Currently I am trying to get this computer to work with my D-link dwl 122 wireless usb adapter (supposedly supported by linux by many different drivers/applications).

I've tried many things mentioned in these forums as well as else where.  The only thing I have left to try I think, is to build my own kernel and then install the linux wlan-ng driver.  

Does anyone know where I can find a good walk trhough on how to build my own kernel and make it work with the linux wlan-ng driver?  Or find a good walkthrouh on the process of builing my own kernel?

Thanks

---

### Post by scoon on 2005-02-14
hey there, 

start here: [http://www.holtmann.org/linux/kernel/debian.html](http://www.holtmann.org/linux/kernel/debian.html)

scoon

---

### Post by frizzy on 2005-02-14
Great walk through I think I should be able to do accomplish this task using that link. 

Thanks

One question though, from what I've found Ubuntu doesn't really have a root directory so on this walk through when it says to do th following:

> debian:/usr/src# tar xzf /root/linux-2.4.20.tar.gz 

how would i change this command so that I get the kernel source extracted to the correct place?

---

### Post by jimmyfergus on 2005-02-15
Just checking that you've noticed that you can just install linux-wlan-ng through the Synaptic Package Manager?

It seems to work to some extent at least.  I'm also trying to get my Prism USB adapter working - I entered some commands  from [this thread](http://www.ubuntuforums.org/showthread.php?t=15490&highlight=usb+wireless), and it showed the signal on the desktop wireless applet, though I didn't get further.

---

### Post by az on 2005-02-15
You may also use ndiswrapper, if you do not mind using proprietairy drivers.  Youwill need a more recent version, since Warty's version does not support the dwl-122.  Again, you do not have to recompile your kernel (!) just build a module.
Install build-essential, linux-headers and the ndiswrapper source(from the website).

Put the ndiswrapper source in /usr/src
cd /usr/src
tar xvzf ndiswrapper*
cd ndiswrapper*
sudo debian/rules binary
cd ..
dpkg -i ndiswrapper*.deb
edit /etc/hotplug/blacklist and add
prism2_usb
p80211
To avoid the modules being loaded (they interfere with ndiswrapper)
cd to your driver's directory
sudo ndiswrapper -i NETPRISM.inf
sudo modprobe ndiswrapper
Then, use the network utility to configure your interface.


If you want to use the linux-wlan-ng driver:

You should install linux-wlan-ng and linux-wlan-ng-doc

You can read up on how to use /etc/wlan settings for wep and such.


basically:
sudo wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable 
sudo wlanctl-ng wlan0 lnxreq_autojoin ssid="" authtype=opensystem (for any within range) OR
sudo wlanctl-ng wlan0 lnxreq_autojoin ssid=(Your ESSID Here) authtype=opensystem
sudo iwconfig (to see your access point).

sudo dhclient wlan0

---

### Post by puelly on 2005-02-16
I have also been trying to use my DWL-122 with ubuntu.  I have followed your instructions for using the ndiswrapper and I am able to bring up and configure the wlan0 device.  I am able to access the net for about two mins before the connection is dropped.  Do you have any idea why this might be occouring?

Please tell me what log I need to post to help diagnose the prob.

[QUOTE=azz]You may also use ndiswrapper, if you do not mind using proprietairy drivers.  Youwill need a more recent version, since Warty's version does not support the dwl-122.  Again, you do not have to recompile your kernel (!) just build a module.
Install build-essential, linux-headers and the ndiswrapper source(from the website).

Put the ndiswrapper source in /usr/src
cd /usr/src
tar xvzf ndiswrapper*
cd ndiswrapper*
sudo debian/rules binary
cd ..
dpkg -i ndiswrapper*.deb
edit /etc/hotplug/blacklist and add
prism2_usb
p80211
To avoid the modules being loaded (they interfere with ndiswrapper)
cd to your driver's directory
sudo ndiswrapper -i NETPRISM.inf
sudo modprobe ndiswrapper
Then, use the network utility to configure your interface.


If you want to use the linux-wlan-ng driver:

You should install linux-wlan-ng and linux-wlan-ng-doc

You can read up on how to use /etc/wlan settings for wep and such.


basically:
sudo wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable 
sudo wlanctl-ng wlan0 lnxreq_autojoin ssid="" authtype=opensystem (for any within range) OR
sudo wlanctl-ng wlan0 lnxreq_autojoin ssid=(Your ESSID Here) authtype=opensystem
sudo iwconfig (to see your access point).

sudo dhclient wlan0[/QUOTE]

---

### Post by frizzy on 2005-02-16
I've been trying to do this as well using Ndis wrapper (i decided to try this first before trying a kernel rebuild).  All of the commands complete successfully, but when I got to networking and try to add a new wireless connection, no device shows up.  From the looks of thigs to, the driver is loaded on the computer when the usb device is connected, do anyone have any suggestions.  I would much prefer using ndiswrapper to rebuiling my kernel (and possibly destroying my install).

---

### Post by az on 2005-02-16
Why rebuild the kernel?

When dnsiwrapper is installed, do 
iwconfig

to see a list of available devices.  You may need to enter wlan0 by hand in the netwoking tool.

Be sure that you did not have prism2_usb loaded before you loaded ndiswrapper.  It won't work until you reboot.

My dwl-122 worked fine for a few months.  It stopped working recently.  It will connect for about three seconds and then no worky.  I had read that it was a crappy device before I bought it...






...and for a third time:

You Do Not Need To Rebuild Your Kernel!
Don't Panic!

---

### Post by puelly on 2005-02-17
how do I load the ndiswrapper driver on bootup and configure the wireless interface.

I have been only able to get it to work manually after bootup.  I have to run "modprobe ndiswrapper" and then I use the GUI to configure the device.  The connection is most times dropped after 2-5mins and it is deactivated.  When I check the network GUI the eth0 is set to active even after I have deactivated it.

Any suggestions?  This wireless thing is driving me crazy.

PS. Adding it to "/etc/modules" didb't help. I guess because it wasn't configured on startup.  I have the entires corrent in the "/etc/network/interfaces" file

---

### Post by songochain on 2005-02-18
Hi guys, i did all but i get this
```
root@ximian64:/home/songochain/descargas/setupXP2000/USB/WINXP # ndiswrapper -i sis163u.inf
Installing sis163u

root@ximian64:/home/songochain/descargas/setupXP2000/USB/WINXP # modprobe ndiswrapper
FATAL: Could not load /lib/modules/2.6.10.18022005/modules.dep: No such file or directory

```
ndiswrapper -l says:```
Installed ndis drivers:
sis163u driver present

```So... what's wrong here??
Thanks

---

### Post by frizzy on 2005-02-18
This is just a guess but, in ubuntu you may have to put sudo before that last command I see from the line that you are logged in as root but, from what i understand you will need sudo (in ubuntu) in order for that command to compelete successfully

Also, Does anyone have an example wlan0 configuration script since it looks like i may have to configure my wlan by hand and not through the networking config tool in ubuntu.

---

### Post by kubla on 2005-02-27
Songochain: i've been working on this problem today and the problem is that we're on a 64 bit architecture and the driver we're trying to load is 32 bit.

Have a look at the output of dmesg:

ndiswrapper (check_nt_hdr:145): Windows driver is not 64-bit; bad magic: 010B
ndiswrapper (load_sys_files:450): unable to prepare driver 'sis162u'
ndiswrapper (ndiswrapper_load_driver:98): loadndiswrapper failed (65280); check

I was having a hell of a time even figuring out where to begin on this one. lscpi wasn't showing anything on the card . I pulled out a spare laptop drive I had, installed windows, and saw that it was loading sis162u for the card. A quick google later revealed that that was a usb driver... lsusb revealed all...

Anyway, it doesn't seem there's much hope for those of us in 64 bit land until SIS releases a 64 bit driver for either Windows or Linux. :\

Ian

---

### Post by archibald on 2005-03-04
THANKYOU, azz, your guide worked like a charm!!! why cant everyone be as helpful&clear as you??? Ive now FINALLY got my ma111 working perfectly on linux!!!! you should maybe add that into the wikiguide about the ndiswrapper, as the one there is already sucks pretty much...

---

### Post by songochain on 2005-03-04
[QUOTE=kubla]Songochain: i've been working on this problem today and the problem is that we're on a 64 bit architecture and the driver we're trying to load is 32 bit.

Have a look at the output of dmesg:

ndiswrapper (check_nt_hdr:145): Windows driver is not 64-bit; bad magic: 010B
ndiswrapper (load_sys_files:450): unable to prepare driver 'sis162u'
ndiswrapper (ndiswrapper_load_driver:98): loadndiswrapper failed (65280); check

I was having a hell of a time even figuring out where to begin on this one. lscpi wasn't showing anything on the card . I pulled out a spare laptop drive I had, installed windows, and saw that it was loading sis162u for the card. A quick google later revealed that that was a usb driver... lsusb revealed all...

Anyway, it doesn't seem there's much hope for those of us in 64 bit land until SIS releases a 64 bit driver for either Windows or Linux. :\

Ian[/QUOTE]
Yes dude, i saw it when finally i could install the driver and i saw dmesg output that the driver was to 32bit version LOL. I think that the driver is soon because winxp64 is soon too

---

### Post by Mr F on 2005-05-01
I'm trying to use this steps for my Linksys WUSB54g.

Now I'm stuck with the following step: modprobe ndiswrapper

I get the following error:

FATAL: Error inserting ndiswrapper (/lib/modules/2.6.8.1-3-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid module format

Can someone help me or telling me what I'm doing wrong here.

Thnx,

F

PS: With ndiswrapper -l (wusb54g driver present)

---

