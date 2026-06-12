---
title: "RTL 8191SU I cannot manage to install wireless driver!!"
date: 2011-01-24
forum: Networking &amp; Wireless
---

### Post by andy123456 on 2011-01-24
Hi
So I am trying to install my Realtek 8191SU wireless Driver but because I am a noob I don't understand everything that they say in the read me file from where I downloaded the linux version of this driver. The Realtek 8191SU wireless driver can be foun here:     

[http://www.realtek.com.tw/Downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/Downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)     

Also I found another site where someone explains how to instlall the driver but I don't know where driver directory is. Here is the site

 [http://www.downloadatoz.com/driver/articles/fix-realtek-rtl8191su-wireless-usb-adapter-issues-on-ubuntu.html](http://www.downloadatoz.com/driver/articles/fix-realtek-rtl8191su-wireless-usb-adapter-issues-on-ubuntu.html)

Also if it helps I use and acer aspire Z5751 and I have ubuntu 64-bit installed. 

Thanks in advance!

---

### Post by chili555 on 2011-01-24
Forget those instructions. As the kid who lives in my basement says, "Dat's messed up." 

In order to compile this beauty, you will need to first do, in a terminal with an internet connection:```
sudo apt-get install build-essential linux-headers-generic
```

Where is the file you downloaded? On your desktop? Right-click it and select 'Extract here.' A folder will be created called rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111. Inside it is a folder called 'driver.' Open it and see a file called rtl8712blahetc. Right-click it and select 'Extract here.' A folder will be created called rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111. Now back to the terminal:```
cd Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111
```You don't need to carefully type all that! Just type in:```
cd Desktop/rtl
```Press Tab and the rest of the first part will fill in. Add driver/rtl and press Tab and the remainder will fill in. Now do:```
sudo su
make
make install
modprobe 8712u
exit
```Post back and let us know how it goes.

---

### Post by andy123456 on 2011-01-24
Hello I tried the steps you have shown me but no wireless network shows up at all. Also after the modprobe 8712u command at the end nothing happened but there also was no error message. And also I have a RTL8191SU wireless card why did I need to type modprobe 8712u ( just curious). I also typed the  Ifconfig command but no wlan0 has showed up. Thanks you for your help!!

---

### Post by chili555 on 2011-01-25
> I have a RTL8191SU wireless cardLet's take a look and be sure. Please insert the device and run and post:```
lsusb
```> why did I need to type modprobe 8712u ( just curious).Because that's the name of the module that's built. In many cases, the name of the module doesn't match the identification of the card.

---

### Post by andy123456 on 2011-01-25
Maybe this will be helpful I have an all in one desktop computer and the wireless card is in the computer but because I am only familiar with opening up towers I didn't unplug anything in the computer so the wireless card is always inserted. Also when i needed to type     cd Dekstop/rtl    and press tab then I did not press enter but I continued and typed      rtl/driver         and pressed tab and then I clicked enter and then I typed all of the following commands, always pressing enter after each command. Did I do it right?? (just making sure) And here is the output for lsusb:     



andy@andy-Aspire-Z5751:~$ lsusb
  Bus 002 Device 008: ID 0bda:8172 Realtek Semiconductor Corp. RTL8191S WLAN Adapter
  Bus 002 Device 007: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
  Bus 002 Device 006: ID 058f:6391 Alcor Micro Corp.
  Bus 002 Device 005: ID 1cb6:6672  
  Bus 002 Device 004: ID 0c45:62c2 Microdia
  Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
  Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
  Bus 001 Device 003: ID 04ca:0058 Lite-On Technology Corp.
  Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
  Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by chili555 on 2011-01-25
> Bus 002 Device 008: ID [COLOR="Red"]0bda:8172[/COLOR] Realtek Semiconductor Corp. RTL8191S WLAN AdapterThe module 8712u is correct for your device as reported in *modinfo*:```
$ modinfo 8712u | grep 8172
alias:          usb:v[COLOR="Red"]0BDA[/COLOR]p[COLOR="Red"]8172[/COLOR]d*dc*dsc*dp*ic*isc*ip*

```Let's see if it's loaded:```
lsmod | grep 8712
```And, let's see if there are any informative messages:```
dmesg | grep -e 8712 -e wlan
```Thanks.> Did I do it right?? If you got as far as *modprobe 8712u* and there was no error, you did it right.

---

### Post by walt.smith1960 on 2011-01-25
ID 0bda:8172 is the same as 2 of my adapters.  The fix is easy and for me reliable. It's documented here:

[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2620217.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2620217.html)

---

### Post by andy123456 on 2011-01-25
chilli555 here is the outcome from both commands:

andy@andy-Aspire-Z5751:~$ lsmod | grep 8712
8712u                 334039  0 
andy@andy-Aspire-Z5751:~$ dmesg | grep -e 8712 -e wlan
andy@andy-Aspire-Z5751:~$ 


and also I tried to use the steps walt.smith1960 documented through the webpage here is the result:


andy@andy-Aspire-Z5751:~$ wget [http://launchpadlibrarian.net/37387612/rtl8192sfw.bin.gz](http://launchpadlibrarian.net/37387612/rtl8192sfw.bin.gz)
--2011-01-25 12:30:56--  [http://launchpadlibrarian.net/37387612/rtl8192sfw.bin.gz](http://launchpadlibrarian.net/37387612/rtl8192sfw.bin.gz)
Resolving launchpadlibrarian.net... 91.189.89.229, 91.189.89.228
Connecting to [launchpadlibrarian.net]("http://launchpadlibrarian.net/")|91.189.89.229|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 31817 (31K)  [application/octet-stream]
Saving to: `rtl8192sfw.bin.gz'

100%[======================================>] 31,817      41.4K/s   in 0.7s    

2011-01-25 12:30:57 (41.4 KB/s) - `rtl8192sfw.bin.gz' saved [31817/31817]

andy@andy-Aspire-Z5751:~$ gunzip rtl8192sfw.bin.gz
andy@andy-Aspire-Z5751:~$ sudo mv rtl8192sfw.bin /lib/firmware/RTL8192SU/
[sudo] password for andy: 
mv: cannot move `rtl8192sfw.bin' to `/lib/firmware/RTL8192SU/': Not a directory
andy@andy-Aspire-Z5751:~$

---

### Post by walt.smith1960 on 2011-01-25
Two things you need to do.  One is to extract the .bin file, the other is to create a folder.  I'm not at all fluent in command line so I do this via point and click.  I must urge caution when using Nautilus with root privileges.  The "I can't let you do that" protections are silenced when logged on as root and it's possible to make a total hash of your system so don't click without checking what you're about to do.  Having said that:

in a terminal ```
gksu nautilus
```  Navigate to the location called for -> computer -> file system -> lib -> firmware.  Then file - create a new folder and name it RTL8192SU.  Copy the file you extracted from the download, rtl8192sfw.bin into the new empty folder.  Close everything and reboot.  The lovely blue light should come on and you should be in business.

---

### Post by chili555 on 2011-01-25
> andy@andy-Aspire-Z5751:~$ gunzip rtl8192sfw.bin.gz
andy@andy-Aspire-Z5751:~$ sudo mv rtl8192sfw.bin /lib/firmware/RTL8192SU/
[sudo] password for andy:
mv: cannot move `rtl8192sfw.bin' to `/lib/firmware/RTL8192SU/': Not a directory
andy@andy-Aspire-Z5751:~$Then let's create the directory:```
sudo mkdir /lib/firmware/RTL8192SU
sudo mv rtl8192sfw.bin /lib/firmware/RTL8192SU/
```The .bin file needs no extraction or other process. It just needs to be moved to the correct place which you have just done.

Is the ethernet cable attached at this time? Please detach it and reboot. Then run and post these tests again:```
lsmod | grep 8712
dmesg | grep -e 8712 -e wlan
```

---

### Post by andy123456 on 2011-01-25
It works!!!!! I typed the command         gksu nautilus         then I created a file called RTL8191SU like walt.smith1960 said and then without extracting it like chili555 said and then I dragged the .bin file over and rebooted the computer. For some reason it took a long time to shut down but this might be because the update manager downloaded some files and installed them while I was trying to get the driver working. After reboot I tried to connect to Internet and first it connected in like 15 seconds so I clicled on Firefox and I started running upstairs to tell my dad that the driver works and when I came downstairs again the wireless was disconnected so I clicked on connect again and after about a minute and asking me 3 times to type in the password it got connected and thats how I typed all this! From my wireless internet connection!! Is it normal that it loads like 1 minute to connect to the Internet ?? Anyways Thanks you very much to both of you!!

---

### Post by walt.smith1960 on 2011-01-25
Hi

Doncha love it when a plan comes together?:D.  Perhaps you could mark this thread solved?  That way if someone finds themselves with RTL8192SU problems, they can search for solutions that have been proven to work.

---

### Post by andy123456 on 2011-01-26
yap I love it when everything works out didn't know it could have been done in a few steps...anyways thanks

---

### Post by gonkyouka on 2011-02-19
> **walt.smith1960 said:**
> Two things you need to do.  One is to extract the .bin file, the other is to create a folder.  I'm not at all fluent in command line so I do this via point and click.  I must urge caution when using Nautilus with root privileges.  The "I can't let you do that" protections are silenced when logged on as root and it's possible to make a total hash of your system so don't click without checking what you're about to do.  Having said that:

in a terminal ```
gksu nautilus
```  Navigate to the location called for -> computer -> file system -> lib -> firmware.  Then file - create a new folder and name it RTL8192SU.  Copy the file you extracted from the download, rtl8192sfw.bin into the new empty folder.  Close everything and reboot.  The lovely blue light should come on and you should be in business.

Done this but it doesnt work after restart.

Heres the output of lsusb:
> Bus 001 Device 005: ID 0bda:8172 Realtek Semiconductor Corp. RTL8191S WLAN Adapter

---

### Post by chili555 on 2011-02-19
What is the result of:```
dmesg | grep 819
```Thanks.

---

### Post by pawan98 on 2011-04-17
Oh my god I love you so much!!! I looked for 2 days to fix this!! all didn't work... until I saw this topic, and I could fix it simply. In one second.

---

### Post by phoenix1/4 on 2011-05-21
> **walt.smith1960 said:**
> ID 0bda:8172 is the same as 2 of my adapters.  The fix is easy and for me reliable. It's documented here:

[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2620217.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2620217.html)


I used this bugfix to get mine working on Maverick 64 bit. Simply follow the instructions and unplug/replug device, give it a minute or so and it should be up and running. It should also be noted that upgrading to Natty will avoid this problem altogether.

---

### Post by MangoChampagne on 2011-12-17
I've been struggling to get my wireless adapter (it's a Trendnet TEW-649UB USB dongle ) to work on Ubuntu 11.10.  This is my first Ubuntu installation and I'd appreciate help getting this figured out.   

After some futzing around I've managed to get it to work when I switch off wireless security in my router.  But when I turn security on (WPA-PSK TKIP + WAP-PSK AES) I can't get the thing to work.  I believe the card use a RealTek 8192SU chipset though lsusb prints 

Bus 001 Device 002: ID 0bda:8172 Realtek Semiconductor Corp. RTL8191S WLAN Adapter

So perhaps it's an 8192SE? The device id is 8172, and I believe the loaded module r8712u supports it. Here's the output of modinfo r8712u|grep 8172

modinfo r8712u|grep 8172
alias:          usb:v0BDAp8172d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8172d*dc*dsc*dp*ic*isc*ip*

The command lsmod|grep 8712 ouputs 
r8712u                163310  0 

When I attempt to activate the wireless connection through network manager I get the following 8172-relevant lines in the output of dmesg

[   16.225574] r8712u: module is from the staging directory, the quality is unknown, you have been warned.
[   16.391025] r8712u: DriverVersion: v7_0.20100831
[   16.391076] r8712u: register rtl8712_netdev_ops to netdev_ops
[   16.391082] r8712u: USB_SPEED_HIGH with 4 endpoints
[   16.405923] r8712u: Boot from EFUSE: Autoload OK
[   20.352080] r8712u: CustomerID = 0x0000
[   20.352089] r8712u: MAC Address from efuse = 00:14:d1:6f:e6:35
[   20.357000] usbcore: registered new interface driver r8712u
[   21.254865] r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[   22.008739] r8712u: 1 RCR=0x153f00e
[   22.009492] r8712u: 2 RCR=0x553f00e
[   22.124742] ADDRCONF(NETDEV_UP): wlan0: link is not ready

Thanks, in advance, for all the help.

---

### Post by chili555 on 2011-12-18
So far, so good; however, this gives a valuable clue:> I've managed to get it to work when I switch off wireless security in my router. But when I turn security on (WPA-PSK TKIP + WAP-PSK AES) I can't get the thing to work.There is often trouble with mixed WPA modes in routers and Linux drivers. I suggest you try single mode WPA2-AES, unless all the devices on your network don't support it.

Are there any further clues here?```
sudo cat /var/log/syslog | grep -e etwork -e wlan
```Thanks.

---

### Post by MangoChampagne on 2011-12-18
Thanks for a prompt response chilli555.  I switched the WPA settings in my router (a 2WIRE router that my service provider AT&T Uverse installs) to single mode -- I tried, both, WPA TKIP and WPA AES, but to no avail.

However, as I kept playing around with various settings on my router this morning -- and this might be useful for other people who have AT&T Uverse service that have issues like this -- I noticed weird things on other wireless devices.  I power cycled the router each time. I'd turn on WPA on the router and yet my Windows 7 laptop would identify the network as unsecured AND manage to establish an unsecured connection!!  Other Windows devices would identify it as a WPA network but not be able to connect.

Finally, I reset the ROM in the router, power cycled it and reconfigured it to factory defaults (including a security setting of WPA-PSK TKIP + WPA-PSK AES).  And voila, wifi  worked everywhere -- my WIndows 7 laptop, my SONY TV and my ubuntu box!  So it looks like the router reconfiguration was messing up something in the router, and a hard reset was in order.

Thanks once again chilli.  I am glad my system is up and running.

---

### Post by chili555 on 2011-12-18
> I am glad my system is up and running.And so am I.

For what it's worth, I had spotty issues with my AT&T 2wire modem/wireless router as well. I resurrected the old Westell modem and attached a Linksys WRT-54G running DD-WRT and I have been happy ever since. I'm not a Uverse customer, so I don't know how or if it is usable in Uverse.

At least I suggest you ask AT&T for a replacement.

---

