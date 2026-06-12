---
title: "Help with D-Link DWA-131 Wireless N USB Adapter driver needed"
date: 2010-04-18
forum: Networking &amp; Wireless
---

### Post by jefferyawillis on 2010-04-18
](*,)Ok, I am new to Linux. I have a dual-boot desktop with Windows 7 and Ubuntu.
 
Problem: Linux does not recognize my D-Link DWA-131 Wireless N USB Adapter. So, I can't access my wireless router or the internet.
 
D-Link has a Linux driver for the DWA-131 posted on their website [http://www.dlink.com/products/?pid=738](http://www.dlink.com/products/?pid=738) that includes a readme file with long, strange, convoluted instructions on how to install the driver.
 
Can someone help me make Ubuntu recognize my Wireless N Adapter?

---

### Post by bkratz on 2010-04-18
> **jefferyawillis said:**
> ](*,)Ok, I am new to Linux. I have a dual-boot desktop with Windows 7 and Ubuntu.
 
Problem: Linux does not recognize my D-Link DWA-131 Wireless N USB Adapter. So, I can't access my wireless router or the internet.
 
D-Link has a Linux driver for the DWA-131 posted on their website [http://www.dlink.com/products/?pid=738](http://www.dlink.com/products/?pid=738) that includes a readme file with long, strange, convoluted instructions on how to install the driver.
 
Can someone help me make Ubuntu recognize my Wireless N Adapter?

Apparently this device uses the rather new 8192SU chip, and a lot of people have been fighting it.  The best in this forum, Chili555, fought it as below:

[http://ubuntuforums.org/showthread.php?t=1392153&highlight=8192SU](http://ubuntuforums.org/showthread.php?t=1392153&highlight=8192SU)

and seemed to have some success.  The linux driver seems to have some problems and the user ended up using ndiswrapper and got it working. It is pretty well documented-step by step, so I would look there. You will need the XP drivers from DLink

[http://www.dlink.com/products/default.aspx?pid=DWA-131&tab=3](http://www.dlink.com/products/default.aspx?pid=DWA-131&tab=3)
.  Here are a few other threads to look at.

[http://ubuntuforums.org/showthread.php?t=1350273&highlight=8192SU](http://ubuntuforums.org/showthread.php?t=1350273&highlight=8192SU)
[http://ubuntuforums.org/showthread.php?t=1318413&highlight=8192SU](http://ubuntuforums.org/showthread.php?t=1318413&highlight=8192SU)

If you go to the terminal ( Applications>>Accessories>>Terminal ) and type in 

```
lsusb
```

( that is LSUSB in lowercase) and receive the following in the listing

ID 07d1:3303 D-Link System

It is the same device.

---

### Post by st0kes on 2010-04-28
I have this usb adaptor, and I'm using it on ubuntu 9.10. 

Only thing is with ndiswrapper, is iwconfig shows it as "wlan1 IEEE 802.11g" but this dongle and my router are wireless-n. 

I'm interested in getting the full "n" potential out of this, will keep digging and post back here if I can work it out .... that is unless someone else can tell me how?

---

### Post by flash63 on 2010-04-29
Hallo,
the new Driver from Realtek for rtl9192su v0006 works.

[http://www.realtek.com.tw/DOWNLOADS/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true]("http://www.realtek.com.tw/DOWNLOADS/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true")

---

### Post by st0kes on 2010-05-04
OK I finally got it working after using the instructions in this blog post. 

[http://samiux.blogspot.com/2010/05/howto-realtek-8192su-usb-dongle.html](http://samiux.blogspot.com/2010/05/howto-realtek-8192su-usb-dongle.html)

I just had to do 'depmod -a' before I could use modprobe to load the driver. 

Phew!

---

### Post by dakk12 on 2010-06-14
great thread (well great links actually)
Samiux's blog was extremely helpful

I had some additional troubles since I was compiling this for a custom kernel on an embedded system running debian instead of ubuntu.  (I am a total linux noob, in way over my head, but I've always like the total immersion strategy of learning)

There were a couple additional changes I had to make, and while they're not necessarily related to ubuntu, this thread seems like a good place to post them.

First, I was getting an error about the autoconf file and I had to change the Makefile again from:

ifeq ($(CONFIG_BUILT_IN), y)
$(shell cp $(src)/autoconf_$(RTL871X)_usb_linux.h $(src)/include/autoconf.h)
else
$(shell cp $(PWD)/autoconf_$(RTL871X)_usb_linux.h $(PWD)/include/autoconf.h)
endif

to:

ifeq ($(CONFIG_BUILT_IN), y)
$(shell cp $(src)/autoconf_$(RTL871X)_usb_linux.h $(src)/include/autoconf.h)
else
ifeq ($(PWD), $(nullstring))
$(shell cp autoconf_$(RTL871X)_usb_linux.h include/autoconf.h)
else
$(shell cp $(PWD)/autoconf_$(RTL871X)_usb_linux.h $(PWD)/include/autoconf.h)
endif
endif

I'm not sure what the overall effect of that was, but it stopped the system from complaining.

The second issue was that the modprobe 8712u failed saying it was an invalid format.

This issue was because of my strange kernel setup and not the drivers themselves.

After digging around I found out that it was pointing to the wrong kernel sources.  
(dmesg was showing me 'version magic' errors to tip me off)
Once I changed the symlink in my /lib/modules/(my custom kernel)/build to the correct headers everything worked perfectly.

---

### Post by bmjbmj on 2010-08-01
[COLOR="Red"]BIG WARNING!!!! Read to the end of this discussion if your kernel version is higher then Kernel 2.6.32-22 [/COLOR]


The new drivers 2.60006.2010625 do NOT need more then 

download
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=2&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192SU]("http://http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=2&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192SU")

unpacking
unzip rtl8192SU_usb_linux_v2.6.0006.20100226.zip
cd rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100226/driver
tar -xvzf rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100226.tar.gz
cd rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100226
 
Building
sudo su
make clean
make
make install


Works great

---

### Post by matthewp131 on 2010-08-07
@bmjbmj - thanks for the guide, but now that i have installed the driver i want to clarify some details for your instructions so that others do not run into the problems i had:
1. download the driver (bmjbmj's link didn't work, but you can get it at the bottom of this page: [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=2&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192SU](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=2&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192SU)
2. cd ~/Downloads/
3. unzip [the name of the driver you downloaded, versions vary]
4. cd ~/Downloads/[the name of the driver you downloaded, versions vary]/driver/
5. now open nautilus and navigate to the above directory, copy the name of the tar.gz archive in the driver folder
6. tar -xvzf [the tar.gz archive name that you copied]
7. cd ~/Downloads/[the name of the driver you downloaded, versions vary]/driver/[the name of the archive you just decompressed, without "tar.gz" at the end of the name]/
8. remember, if the files and folders get confusing, look in nautilus to find the names you need.
9. Build the driver using these four commands in order, each may take a couple minutes, be patient:
   a. sudo su
   b. make clean
   c. make 
   d. make isntall
10. thanks again to bmjbmj for his instructions, im merely elaborating on them, for other noobs like myself.

---

### Post by rhinocero on 2010-08-27
I got my D-Link DWA-131 worked by using a 8712u module(it's actually 8192u chipset) but with a weird signal strength: 10%. The Wi-Fi of my laptop next to it works fine.

Does anybody have any idea about what problem this could be?

All debug info can be given based on demand

Thanks for any kind of help or prompt

---

### Post by tenfly on 2010-09-06
Hey [matthewp131]("http://ubuntuforums.org/member.php?u=1126063"), thanks so much for that!!! I have just installed Ubuntu last night, and wireless was my number one issue to sort out.  Thanks for all the help!

---

### Post by Wakunahum on 2010-09-14
> **rhinocero said:**
> I got my D-Link DWA-131 worked by using a 8712u module(it's actually 8192u chipset) but with a weird signal strength: 10%. The Wi-Fi of my laptop next to it works fine.

Does anybody have any idea about what problem this could be?

All debug info can be given based on demand

Thanks for any kind of help or prompt

I'm getting 10% as well following the instructions.

I'm now stuck and don't know what to do.

---

### Post by Sandstroh on 2010-10-18
I've tried it with bmjbmj's instructions too.
The extracting and building of the driver worked fine.
But when I plug the stick in, it's just blinking about 5-6 times and then the whole system freezes and I have to reboot.

Has anyone an idea, why it's not working?

---

### Post by bmjbmj on 2010-10-21
Kernel 2.6.32-25 may have something to with it! It worked in -22 and the built in driver worked in -23 it broke in -24 and do not work in -25.

I'm looking in to it .
My symptoms are this:
I get two entrys for the DW-131 (probably from both drivers) and non of them is possible to enable. In fact it is not possible to check activate WLAN at all in the network manager.

>sudo lshw -C network
returns *-network DISABLED for all interfeces

/var/lib/NetworkManager/NetworkManager.sate
is set to

[main]
NetworkingEnabled=true
WirelessEnabled=false
WWANEnabled=true

---

### Post by bmjbmj on 2010-10-21
Humm!

sudo rmmod 8712u
sudo rmmod ath9k
sudo rmmod mac80211
sudo modprobe 8712u

Made everything work for me! (No I'm NOT knowing what I'm doing I'm just guesing). Must be a conflict of some sort!

---

### Post by bmjbmj on 2010-10-21
To fix it for kernel 2.6.32-25 just build the drivers as before and then add 

#I hate this stuff what ever it is (-:
blacklist ath9k
blacklist mac80211

to the end of /etc/modprobe.d/blacklist.conf

and reboot

Worked on an eeepPC1001PX

---

### Post by Calandric on 2010-11-13
> **bmjbmj said:**
> To fix it for kernel 2.6.32-25 just build the drivers as before and then add 

#I hate this stuff what ever it is (-:
blacklist ath9k
blacklist mac80211

to the end of /etc/modprobe.d/blacklist.conf

and reboot

Worked on an eeepPC1001PX

I've had no problems for months using my DWA-131 dongle under a G connection. I've just bought a dual band router, and there is a separate SSID for 'N' connections, though under NetworkManager it doesn't see this SSID. It still sees and connects to the 'G' SSID, but not the 'N'.  Any ideas?

Hrm. Maybe this 'new' dongle doesn't support 5GHz connections? I'll search that now. Otherwise, any help would be greatly appreciated.

---

### Post by ThomasNovin on 2011-01-29
Could someone with this adapter (and preferably a 802.11n AP/router) try Ubuntu 11.04 which has kernel 2.6.38? I have read that driver for this adapter is included.

Trying a new version of Ubuntu can be done by booting from a CD or USB-memory. Download from here:

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

Please also post output from 'dmesg' and 'iwconfig' (if it works and you are connected to a WiFi network).

Thanks!

---

### Post by tedwils on 2011-01-30
> **matthewp131 said:**
> @bmjbmj - thanks for the guide, but now that i have installed the driver i want to clarify some details for your instructions so that others do not run into the problems i had:
1. download the driver (bmjbmj's link didn't work, but you can get it at the bottom of this page: [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=2&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192SU](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=2&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192SU)
2. cd ~/Downloads/
3. unzip [the name of the driver you downloaded, versions vary]
4. cd ~/Downloads/[the name of the driver you downloaded, versions vary]/driver/
5. now open nautilus and navigate to the above directory, copy the name of the tar.gz archive in the driver folder
6. tar -xvzf [the tar.gz archive name that you copied]
7. cd ~/Downloads/[the name of the driver you downloaded, versions vary]/driver/[the name of the archive you just decompressed, without "tar.gz" at the end of the name]/
8. remember, if the files and folders get confusing, look in nautilus to find the names you need.
9. Build the driver using these four commands in order, each may take a couple minutes, be patient:
   a. sudo su
   b. make clean
   c. make 
   d. make isntall
10. thanks again to bmjbmj for his instructions, im merely elaborating on them, for other noobs like myself.
Thanks for this. I'm really new at this so it took many tries before it (seemed to) work. It helped to be in the right directories, type code exactly as shown and without the square brackets. That was a steep learning curve for me but now I think I grasp the fundamentals. At least I think I have my driver installed correctly. I'm not sure how to test for that but I will read more posts to find out. The DWA 131 light is not yet on and no available networks are listed, although the title is there. I had to plug in the wire in order to send this off. I know it will have to be unplugged before the wireless will work. What must be done to get the usb adapter recognized? I'll look for that as well. Thanks for all your help bmjbmj and matthewp.

---

### Post by ThomasNovin on 2011-02-27
Ubuntu 11.04 will come as a first beta release next thursday.

Could someone with this adapter please try it so see if it works out-of-the-box?

The ISO will be downloadable from [http://www.ubuntu.com/testing](http://www.ubuntu.com/testing) and can easily be tried on a USB-memory by using the utility in Administration > Startup Disk Creator.

---

### Post by walt.smith1960 on 2011-02-27
> **ThomasNovin said:**
> Ubuntu 11.04 will come as a first beta release next thursday.

Could someone with this adapter please try it so see if it works out-of-the-box?

The ISO will be downloadable from [http://www.ubuntu.com/testing](http://www.ubuntu.com/testing) and can easily be tried on a USB-memory by using the utility in Administration > Startup Disk Creator.

I'm not sure about D-Link DWA-131, but another RTL-8192SU device (TrendNet TEW-649UB) is recognized natively under Natty 11.04A2.  My download of Natty has other issues but that device is recognized.

I've posted a link in other threads on getting an RTL8192SU device recognized. It's pretty simple, no building drivers required.  It has worked with my TrendNet on 3 different machines, don't know about other manufacturers.
[[Bug 492034] Re: [STAGING] realtek rtl8192su chipset based USB wireless]("http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2620217.html") .  This firmware file is part of the driver download for anyone who wants to get the latest & greatest from RealTek. Just extract the files from the package and it's in one of the folders.

---

### Post by ThomasNovin on 2011-02-28
> **walt.smith1960 said:**
> I'm not sure about D-Link DWA-131, but another RTL-8192SU device (TrendNet TEW-649UB) is recognized natively under Natty 11.04A2.  My download of Natty has other issues but that device is recognized.

I've posted a link in other threads on getting an RTL8192SU device recognized. It's pretty simple, no building drivers required.  It has worked with my TrendNet on 3 different machines, don't know about other manufacturers.
[[Bug 492034] Re: [STAGING] realtek rtl8192su chipset based USB wireless]("http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2620217.html") .  This firmware file is part of the driver download for anyone who wants to get the latest & greatest from RealTek. Just extract the files from the package and it's in one of the folders.

Ok sounds promising. I will buy a DWA-131 after B1 of Natty is released and try it out and do some benchmarking on 802.11n performance. If it sucks I'll just return it..

Edit: Oops, B1 of Natty is March 31st. Alpha 3 is March 3rd though.

---

### Post by walt.smith1960 on 2011-03-05
I wanted to add something to this thread RE Natty Alpha3.  I've installed 11.04A3 to a USB drive.  When I start from the USB key and the Trendnet device already plugged in, the WiFi device is not initially recognized.  If I unplug and replug, it is recognized and works with no further input.  I haven't installed to a hard drive so I don't know if this behavior will be the same or not.

---

### Post by sajattack on 2011-03-21
I tried st0kes' and dmjdmj's instructions. With st0kes' instructions, when I did the modprobe command, the caps and scroll lock lights on my keyboard flash while the rest of the computer hangs. With dmjdmj's, the same thing happens when I reboot with the DWA-131 plugged in, except the lights on the DWA-131 flash a bit also(in no pattern unlike the caps and scroll lights). Does anyone know why? I'll test the 11.04 build next.

---

### Post by rspain on 2011-03-25
Newbie - I just installed Ubuntu 10.10 on a Dell Latitude D600. The internal wireless isn't working and I was told by the clerk that the D-Link DWA-131 should work fine. I would like to get it to work but I see conflicting messages on different sites. Will this work on the newest Version of Ubuntu? If so..Can someone walk me through step by step. Please keep in mind I am new to linux and command line. Thanks

---

### Post by Calandric on 2011-05-14
Hate to do a little resurrecting but I am in need of input!

So, I've been using this adapter (DWA-131) for almost a year via the instructions by [bmjbmj]("http://ubuntuforums.org/member.php?u=705339") on a mythtv-frontend and its worked fine up till now. 

I was in the process of upgrading ubuntu install on said frontend (almost a year?! I know right?) and I read that the DWA-131 was natively supported. So, I was excited to see that! So, I did a fresh install on a spare box and it was found by ubuntu and I could connect to the router and had internet connection. Yay! Well, within a few seconds performance dropped to near nothing. Couldn't even find websites, etc :( 

I thought maybe it was the location, so I plugged in an old Linksys adapter, worked fine. A little slow (54g) but no connection drops, etc. So, hm, maybe the adapter is going bad? I have recently upgraded a Dell Mini9 netbook to Natty, so I tried it there. Shoo! lighting speed, no drops, etc etc. 

So, before I update this mythtv-frontend which is used alot, I'm wondering if anyone else has seen such activity from this little guy? I'm going to completely reformat/reinstall natty on that spare pc here shortly and see if it was just a fluke or what. Anyhow, any input or ideas are welcome. 

Have a nice day!

---

### Post by Calandric on 2011-05-14
UPDATE:

To further explore this issue, I've gone to the Realtek website and downloaded the latest drivers from this month from here:

[http://www.realtek.com.tw/DOWNLOADS/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#2292](http://www.realtek.com.tw/DOWNLOADS/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#2292)

and thus unpacked, cleaned, compiled, and installed them accordingly. Rebooted, and still no dice. I can still connect to the router, according to the wireless icon anyway, but I can't even resolve hostnames anymore. 

Unplugging and plugging the old Linksys adapter in still works fine, though strangely slow at loading pages etc, it still works as is evidence by me posting this message from the troubled machine. 

By the way, everything is still fast in all respects from an additional 10 feet away using the netbook and same adapter(s). I'm starting to think this is a on board usb issue? I'll try various other usb ports and report back later after dinner perhaps.

---

### Post by Calandric on 2011-05-15
UPDATE #2:

Ok, so I am happy to announce that evidently my test PC has a faulty USB hub on the back ports. Plugging this device into one of the front ports makes all things wonderful. Sorry to have freaked out on anyone. :) 

Have a nice day. :)

---

### Post by muzorewa on 2011-06-02
> **bmjbmj said:**
> [COLOR="Red"]BIG WARNING!!!! Read to the end of this discussion if your kernel version is higher then Kernel 2.6.32-22 [/COLOR]


The new drivers 2.60006.2010625 do NOT need more then 

download
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=2&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192SU]("http://http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=2&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192SU")

unpacking
unzip rtl8192SU_usb_linux_v2.6.0006.20100226.zip
cd rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100226/driver
tar -xvzf rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100226.tar.gz
cd rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100226
 
Building
sudo su
make clean
make
make install


Works great



When I try to execute the "make" command i get an error saying that the /lib/modules/2.6.32-31-386/build file or directory does not exist.

How do I correct this issue?

Thanks

---

### Post by Calandric on 2011-06-02
What version of Ubuntu? Latest (Natty) has baked in support.

---

### Post by muzorewa on 2011-06-02
I'm on Lucid Lynx, 10.0.4

---

### Post by muzorewa on 2011-06-02
Is there a way I can manually (point an click) install the driver from the downloaded zip file? I'm a Linux virgin but, frustratingly, I can't get over the first hurdle of getting on the internet to start this Linux adventure off.

---

### Post by cicciuzzu on 2012-05-04
How does one download the driver when one needs to driver first activate the D-Link device?

---

### Post by ulrichard on 2012-07-13
Hi guys,

when I plug in my 
Bus 001 Device 004: ID 07d1:3303 D-Link System DWA-131 802.11n Wireless N Nano Adapter(rev.A1) [Realtek RTL8192SU]
in my ubuntu precise workstation, it is recognized and immediately ready to use. 
Not so on the raspberry pi. I read on [http://wiki.debian.org/rtl819x](http://wiki.debian.org/rtl819x) that the driver is only for x86 and amd64.
Does anybody here know why not for ARM?

---

### Post by redgum78 on 2012-07-23
Hello all,
I am also very new to Ubuntu. Really loving it and so happy to move away from Windows.

I am also having trouble with a DWA -131 adapter. I think my problem is a little different again to others here?
I  Installed Ubuntu 12.4 on a PC with the mentioned D-link adapter. It  found my wireless network straight away and operated fine for a week as  did my laptop that I also installed 12.4 on.

A few days ago it  just stopped working?? My network is good as my laptop is fine. USB  is  good as other usb stuff works in the same port plus I tried different  ports on the PC. Nothing. Not even the blue light flashing on the end of  the DWA-131 (it flashes when I plug it into my laptop).
I am fairly sure the problem started on the 1st reboot after Ubuntu updates were installed but I couldn't be 100% sure. 

  I am really new to Ubuntu so any help would really be appreciated.

Thanks

Danny

---

### Post by Pierrot Lafouine on 2012-10-16
Hi
I'm trying to install the driver for DWA-131 on Ubuntu Lucid Lynx (10.04) and Debian Squeeze.  It look to me something changed from these instructions :

> Originally Posted by bmjbmj  
BIG WARNING!!!! Read to the end of this discussion if your kernel version is higher then Kernel 2.6.32-22 

The new drivers 2.60006.2010625 do NOT need more then download
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=2&PNid=48&PFid=48&Level=](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=2&PNid=48&PFid=48&Level=) 5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true #RTL8192SU

unpacking
unzip rtl8192SU_usb_linux_v2.6.0006.20100226.zip
cd rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100 226/driver
tar -xvzf rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100 226.tar.gz
cd rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100 226

Building
sudo su
make clean
make
make install

Unpacking instruction works fine, (but the driver I downloaded [_here_]("http://www.realtek.com.tw/DOWNLOADS/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true") changed version to v2.6.6.0.20120405)

Building instruction doesn't work at all, there is no 'make' file in any folder.  There is a bash file install.sh, that stop working after I entered the root password.  I wonder if anyone succeedded to install this new driver ?

Tks

An

---

### Post by linuxnoob12232 on 2013-06-25
When I try to do this, I type make install, and it says "cannot stat '8712u.ko': No such file or directory"

---

### Post by GFmdBkx on 2013-09-26
> **linuxnoob12232 said:**
> When I try to do this, I type make install, and it says "cannot stat '8712u.ko': No such file or directory"

I get an error regarding a cast from pointer to integer of different size, "[-Wpointer-to-int-cast]" in function rxmem_to_recvframe located in rt1871x_recv.h

which is slightly frustratingful.

is my compiler borked or something? does anyone else get this error?

---

### Post by Spirit of Yggdrasill on 2013-12-25
For anybody looking for solution this is all that is needed [http://ubuntuforums.org/showthread.php?t=2121020&p=12882623#post12882623](http://ubuntuforums.org/showthread.php?t=2121020&p=12882623#post12882623) no compiling and other mumbo jumbo...

---

