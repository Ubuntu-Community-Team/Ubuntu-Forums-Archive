---
title: "usbwifi RTL8188SU Install"
date: 2013-02-27
forum: Networking &amp; Wireless
---

### Post by RPisces on 2013-02-27
Hi all,

First off, please play nice as I'm new to Linux (especially embedded) :biggrin:. I just installed ubuntu-12.10-r3-minimal-armhf, and am trying to get my generic USB wifi adapter to work.

```
ubuntu@arm:/sys/bus/usb/drivers$ lsusb
Bus 001 Device 002: ID 0424:9514 Standard Microsystems Corp.
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0424:ec00 Standard Microsystems Corp.
Bus 001 Device 004: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 006: ID 0bda:8171 Realtek Semiconductor Corp. RTL8188SU 802.11n WLAN Adapter

```
 
I think it uses the r8192s_usb driver which I cannot find with apt-cache search, and I don't think is installed:

ubuntu@arm:/sys/bus/usb/drivers$ ls
```

cdc_ether  hub     rndis_host  usb    usbhid
cdc_ncm    r8712u  smsc95xx    usbfs  usb-storage
ubuntu@arm:/sys/bus/usb/drivers$ modprobe r8192s_usb
FATAL: Module r8192s_usb not found.

```

Assuming this adapter requires the r8192s_usb driver, how can I install this driver for Ubuntu? I know it's easy for Debian:
[http://wiki.debian.org/rtl819x](http://wiki.debian.org/rtl819x)

But I've been scouring the web for the past few hours and can't seem to find a solution :sad: Any help/pointers would be greatly appreciated! Thanks.

---

### Post by bellaseem on 2013-02-27
First go here:
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&ProdID=230&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&ProdID=230&DownTypeID=3&GetDown=false&Downloads=true)

Download the driver for Linux...

Then extract it, open the readme files and read the instructions in it on how to install...

they should go something like this:
make
make install

Basically you have to change directory into the folder you extracted, using the command " cd " in terminal

for example [in a terminal] : 
cd /home/user/downloads/driver [tells the terminal to change directory to where you extracted the folder]
then type in " sudo make " [tells it to compile the files]
then type in " sudo make install " [tells it to install]
[without the parenthesis of course...]

also if that doesn't work then search for a tutorial on how to use ndiswrapper to install the windows driver for the adapter (if the adapter is working on windows for you, then it should work perfectly fine with ndiswrapper)

---

### Post by varunendra on 2013-02-27
Welcome to the forums RPisces !

Please try r8712u -
```
sudo modprobe -v r8712u
```
Post back how it goes.

---

### Post by RPisces on 2013-02-27
```
sudo modprobe -v r8712u
```

Returns nothing. Shall I just go to the Realtek website and make/install the drivers? This is an embedded linux box (no screen; I'm in SSH) so it's no so easy as 'point-and-click'...

---

### Post by chili555 on 2013-02-27
> Returns nothing. Shall I just go to the Realtek website and make/install the drivers? This is an embedded linux box (no screen; I'm in SSH) so it's no so easy as 'point-and-click'...Did an interface get created, ideally wlan0?```
iwconfig
```Does it scan?```
sudo iwlist wlan0 scan
```The good and bad thing about headless systems running no desktop GUI is that nothing happens at all unless you command it.

If the interface scans and sees your network, then edit /etc/network/interfaces to add your connection details. Something like:```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
address 192.168.1.105
netmask 255.55.255.0
gateway 192.168.1.1
dns-nameservers 192.168.1.1 8.8.8.8
wpa-essid your_router
wpa-psk yoursecretkey
```Now get the system to re-read the file:```
sudo ifdown wlan0 && sudo ifup wlan0
```Confirm you connected:```
ping -c3 www.google.com
```If there is any problem along the way, post:```
dmesg | grep r8712u
```

---

### Post by RPisces on 2013-02-27
Silly me! #-o I forgot to bring it up with ifconfig!

Problem solved. Thanks Chili, you're probably one of the most helpful sources of ubuntu networking information I've found here! Close this thread, thanks.

---

### Post by RPisces on 2013-02-27
Actually, before closing this, please help me answer this: Is there a problem with assigning the same static IP address/gateway IP to multiple interfaces in /etc/network/interfaces as long as only one is connected at a time? I want the same IP for eth0/wlan0 so SSH'ing in is painless.

---

### Post by chili555 on 2013-02-27
> **RPisces said:**
> Actually, before closing this, please help me answer this: Is there a problem with assigning the same static IP address/gateway IP to multiple interfaces in /etc/network/interfaces as long as only one is connected at a time? I want the same IP for eth0/wlan0 so SSH'ing in is painless.I doubt there is any problem. If you intend to do so, I'd comment out the auto lines and bring up the desired interface at the command line:```
sudo ifup eth0
```I suppose some routers might be troubled releasing the IP address associated with a particular MAC address; it would be interesting to see.

I assume once the development work is done, it will be put in place permanently with one or the other.```
auto lo
iface lo inet loopback

[COLOR="Red"]#[/COLOR]auto wlan0
iface wlan0 inet static
address 192.168.1.105
netmask 255.55.255.0
gateway 192.168.1.1
dns-nameservers 192.168.1.1 8.8.8.8
wpa-essid your_router
wpa-psk yoursecretkey
```

---

### Post by varunendra on 2013-02-27
Thank you for making it fast dr. chili, you certainly are a life saver! It could have taken me much longer to reply back :)

@ RPisces,
> **RPisces said:**
> Close this thread, thanks.
Threads are rarely closed and only Mods/Admins can do that. But you certainly can (and should) mark it as** [Solved]** using "**Thread Tools**" link above the top post on this page.

If you think your problem is solved and pertaining questions have been answered, please mark it as [Solved] now. It would be much appreciated by us and others looking for help on same/similar problem.

Thank you! :)

---

