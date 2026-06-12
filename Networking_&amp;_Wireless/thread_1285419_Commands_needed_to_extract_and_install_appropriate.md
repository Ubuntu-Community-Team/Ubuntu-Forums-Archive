---
title: "Commands needed to extract and install appropriate BCM4312 wlan card Firmware."
date: 2009-10-07
forum: Networking &amp; Wireless
---

### Post by scrypt on 2009-10-07
Hi Everyone.

I hane NO wirless conectivity on my Dell Laptop with A BCM4312 WLAN card.

 I need to install the Firmware update to my WLAN Card.

Can anybody help A begginer make sense of this?

Im still learning all about Ubuntu, and I have been looking and searching for the correct firmware to install but I cannot find it.

I have tried various commands but not had any luck.

I cannot correctly Download, Extract and install the correct Firmware for my BCN4312 WLAN Card.

I have fwcutter installed and it is the latest version.

Also can anyone please post me the correct commands to Download, Extract and install the appropriate firmware for my BCN4312 Wlan card.

I then can study the commands and teach myself how it was Downloaded.
How to correctly extract the firmwhere and where too.
and then finally how to install the Firmware.

I hope somebody can help me out

---

### Post by t0mppa on 2009-10-07
Well, the only driver that needs firmware is b43, so [here]("http://linuxwireless.org/en/users/Drivers/b43")'s a pretty detailed page about it. Jaunty runs on 2.6.28 kernel, in case you go by the manual approach.

---

### Post by scrypt on 2009-10-07
I dont mind admitting im struggling with this one,

can you please post the commands foe me?

---

### Post by t0mppa on 2009-10-07
Well, if you already have fwcutter installed, then they'd be:

```
export FIRMWARE_INSTALL_DIR="/lib/firmware"
wget http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2
tar xjf broadcom-wl-4.150.10.5.tar.bz2
cd broadcom-wl-4.150.10.5/driver
sudo ../../b43-fwcutter-012/b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" wl_apsta_mimo.o
```

Except that you would replace the *../../b43-fwcutter-012/b43-fwcutter* with the path where it can be found on your system (hint: **which b43-fwcutter** or **locate b43-fwcutter**).

Note that you might want to go into a download subdirectory first (~/ where the terminal opens by default refers to your home directory), instead of just running these commands at some random place, since the wget downloads the file into the directory where you're at.

---

### Post by scrypt on 2009-10-08
Hello Tompa.
Hope you can still help me.

Im really stuggling with this.

My firmware is installed and kept in /lib/firmware.

I have ran the commands as is and restarted but still no wireless.

These are the correct commands i need to run, download, extract and install the appropriate firmware

Code:

wget [http://bu3sch.de/b43/fwcutter/b43-fwcutter-012.tar.bz2](http://bu3sch.de/b43/fwcutter/b43-fwcutter-012.tar.bz2)
tar xjf b43-fwcutter-012.tar.bz2
cd b43-fwcutter-012
make
cd ..

export FIRMWARE_INSTALL_DIR="/lib/firmware"
wget [http://mirror2.openwrt.org/sources/b...0.10.5.tar.bz2](http://mirror2.openwrt.org/sources/b...0.10.5.tar.bz2)
tar xjf broadcom-wl-4.150.10.5.tar.bz2
cd broadcom-wl-4.150.10.5/driver
sudo ../../b43-fwcutter-012/b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" wl_apsta_mimo.o

I ran these commands as is.

is there anything i need to change with any of these commands?

My firmware is installed and kept in /lib/firmware.

can you list the correct commands i need to run to get my wlan card working. im not getting any where!

Im am not sure what to do next can you help??

---

### Post by scrypt on 2009-10-08
i do not understand this bit you wrote.
can you clarify please?

"Except that you would replace the ../../b43-fwcutter-012/b43-fwcutter with the path where it can be found on your system (hint: which b43-fwcutter or locate b43-fwcutter).

Note that you might want to go into a download subdirectory first (~/ where the terminal opens by default refers to your home directory), instead of just running these commands at some random place, since the wget downloads the file into the directory where you're at."

---

### Post by scrypt on 2009-10-08
Should I change these:

export FIRMWARE_INSTALL_DIR="/lib/firmware"
wget [http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2)
tar xjf broadcom-wl-4.150.10.5.tar.bz2
cd broadcom-wl-4.150.10.5/driver
sudo ../../b43-fwcutter-012/b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" wl_apsta_mimo.o

To this:

export /lib/firmware
wget [http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2)
tar xjf broadcom-wl-4.150.10.5.tar.bz2
cd broadcom-wl-4.150.10.5/driver
sudo ../../b43-fwcutter-012/b43-fwcutter -w /lib/firmware wl_apsta_mimo.o


????

---

### Post by t0mppa on 2009-10-08
Ok, so just out of curiousity, I have to ask: do you really need to install the firmware manually for some specific purpose? Because we're doing this the hard way. You could simply go to System / Administration / Hardware Drivers and enable the Broadcom STA or b43 there (will need Internet connection active to download the packets), if all you want is a working wireless.

If the answer to above is yes, then here's a thorough version of what happens and why. When you're running a terminal, at the beginning of each line, it shows: ```
<user>@<computer>:<path>$
```

Let's say the user name is Mr. Anderson and computer name is Matrix. Then starting the terminal would show this: ```
Mr. Anderson@Matrix:~$
```

~ there refers to the users home directory (/home/Mr. Anderson/). Now, if you wanted to keep your downloads in a subdirectory called *Downloads*, you'd simply run **cd Downloads** (cd as in Change Directory) or if you don't have a place for them yet, you can make one with **mkdir Downloads** and then change into it. Going there would make the prompt look like: ```
Mr. Anderson@Matrix:~/Downloads$
```

The export is simply storing the location of the firmware library in a variable, so that if there's a need to change this value, it's as simple as simply changing said variable and all the commands afterwards remain the same. This is called softcoding the value and is helpful when the value needs to be used in a number of different places. For your purposes, you can simply use the hardcoded version and write the location straight into the command, since it's only used once and just skip the whole export step. It's just a pattern that a programmer would use. Will get back to the command itself later.

Now, if we followed the tutorial, it would go along the lines of (red part is the prompt that is shown automatically on terminal and black part are the commands you'd type): ```
[COLOR="Red"]Mr. Anderson@Matrix:~/Downloads$[/COLOR] wget http://bu3sch.de/b43/fwcutter/b43-fwcutter-012.tar.bz2
[COLOR="Red"]Mr. Anderson@Matrix:~/Downloads$[/COLOR] tar xjf b43-fwcutter-012.tar.bz2
[COLOR="Red"]Mr. Anderson@Matrix:~/Downloads$[/COLOR] cd b43-fwcutter-012
[COLOR="Red"]Mr. Anderson@Matrix:~/Downloads/b43-fwcutter-012$[/COLOR] make
[COLOR="Red"]Mr. Anderson@Matrix:~/Downloads/b43-fwcutter-012$[/COLOR] cd ..
[COLOR="Red"]Mr. Anderson@Matrix:~/Downloads$[/COLOR] export FIRMWARE_INSTALL_DIR="/lib/firmware"
[COLOR="Red"]Mr. Anderson@Matrix:~/Downloads$[/COLOR] wget http://mirror2.openwrt.org/sources/b...0.10.5.tar.bz2
[COLOR="Red"]Mr. Anderson@Matrix:~/Downloads$[/COLOR] tar xjf broadcom-wl-4.150.10.5.tar.bz2
[COLOR="Red"]Mr. Anderson@Matrix:~/Downloads$[/COLOR] cd broadcom-wl-4.150.10.5/driver
[COLOR="Red"]Mr. Anderson@Matrix:~/Downloads/broadcom-wl-4.150.10.5/driver$[/COLOR] sudo ../../b43-fwcutter-012/b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" wl_apsta_mimo.o
```

So, as you can see [COLOR="Red"]..[/COLOR] refers to: "one directory up from here". But since you have already installed the b43-fwcutter, it should be on the path (locations where the system automatically looks for executable files).

So, what you'd need to do was go into the downloads directory (or then just download it into your home directory - where the terminal opens by default - if that doesn't bother you) and run the following commands: ```
wget http://mirror2.openwrt.org/sources/b...0.10.5.tar.bz2
tar xjf broadcom-wl-4.150.10.5.tar.bz2
cd broadcom-wl-4.150.10.5/driver
sudo b43-fwcutter -w /lib/firmware wl_apsta_mimo.o
```

---

### Post by scrypt on 2009-10-08
Should I change these:

export FIRMWARE_INSTALL_DIR="/lib/firmware"
wget [http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2)
tar xjf broadcom-wl-4.150.10.5.tar.bz2
cd broadcom-wl-4.150.10.5/driver
sudo ../../b43-fwcutter-012/b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" wl_apsta_mimo.o

To this:

export /lib/firmware
wget [http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2)
tar xjf broadcom-wl-4.150.10.5.tar.bz2
cd broadcom-wl-4.150.10.5/driver
sudo ../../b43-fwcutter-012/b43-fwcutter -w /lib/firmware wl_apsta_mimo.o


????

---

### Post by scrypt on 2009-10-08
Hello Tommpa.

Thanks alot for your posts especially the last one.

I will study them and try to make sense of them later when I get Home.

The reason I want to do it the hard way is I need to learn about downloading, extraction and installation.

and I thought this would be a perfect opportunity for me to learn this.

You probably think its sort of defeating the object you posting the Commands and explanations.
But I think otherwise.
I can now see for myself how and what these commands do!

Also the commands you gave me are commands that are very important in Ubuntu.
   In my experience I will be repeating similar commands a fair bit in the future.
So it will now stand me in good stead to tackle future extraction and installation tasks with A bit more confidence.

Thanks Scrypt

---

### Post by scrypt on 2009-10-08
Heya Tomppa..

thanks for your post.
I have followed them to the letter but I still have no wireless connectivity.

can you help me to rectify this??

Here are the commands I ran, Do they look okay to you??

Im sure I have followed the commands correctly. but still no wlan connectivity.

what can I do now????


2
--2009-10-08 20:01:55-- [http://bu3sch.de/b43/fwcutter/b43-fwcutter-012.tar.bz2](http://bu3sch.de/b43/fwcutter/b43-fwcutter-012.tar.bz2)
Resolving bu3sch.de... 62.75.166.246
Connecting to bu3sch.de|62.75.166.246|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 14138 (14K) [application/x-bzip2]
Saving to: `b43-fwcutter-012.tar.bz2.2'

100%[======================================>] 14,138 --.-K/s in 0.09s

2009-10-08 20:01:55 (148 KB/s) - `b43-fwcutter-012.tar.bz2.2' saved [14138/14138]

modus@modus-laptop:~$ tar xjf b43-fwcutter-012.tar.bz2
modus@modus-laptop:~$ cd b43-fwcutter-012
modus@modus-laptop:~/b43-fwcutter-012$ make
make: Nothing to be done for `all'.
modus@modus-laptop:~/b43-fwcutter-012$ cd ..
modus@modus-laptop:~$ export FIRMWARE_INSTALL_DIR="/lib/firmware"
modus@modus-laptop:~$ wget [http://mirror2.openwrt.org/sources/b...0.10.5.tar.bz2](http://mirror2.openwrt.org/sources/b...0.10.5.tar.bz2)
--2009-10-08 20:02:57-- [http://mirror2.openwrt.org/sources/b...0.10.5.tar.bz2](http://mirror2.openwrt.org/sources/b...0.10.5.tar.bz2)
Resolving mirror2.openwrt.org... 88.198.39.176
Connecting to mirror2.openwrt.org|88.198.39.176|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3888794 (3.7M) [application/x-tar]
Saving to: `broadcom-wl-4.150.10.5.tar.bz2.1'

100%[======================================>] 3,888,794 952K/s in 4.4s

2009-10-08 20:03:02 (869 KB/s) - `broadcom-wl-4.150.10.5.tar.bz2.1' saved [3888794/3888794]

modus@modus-laptop:~$ tar xjf broadcom-wl-4.150.10.5.tar.bz2
modus@modus-laptop:~$ cd broadcom-wl-4.150.10.5/driver
modus@modus-laptop:~/broadcom-wl-4.150.10.5/driver$ sudo ../../b43-fwcutter-012/b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" wl_apsta_mimo.o
This file is recognised as:
ID : FW13
filename : wl_apsta_mimo.o
version : 410.2160
MD5 : cb8d70972b885b1f8883b943c0261a3c
Extracting b43/pcm5.fw
Extracting b43/ucode15.fw
Extracting b43/ucode14.fw
Extracting b43/ucode13.fw
Extracting b43/ucode11.fw
Extracting b43/ucode9.fw
Extracting b43/ucode5.fw
Extracting b43/lp0bsinitvals15.fw
Extracting b43/lp0initvals15.fw
Extracting b43/lp0bsinitvals14.fw
Extracting b43/lp0initvals14.fw
Extracting b43/a0g1bsinitvals13.fw
Extracting b43/a0g1initvals13.fw
Extracting b43/b0g0bsinitvals13.fw
Extracting b43/b0g0initvals13.fw
Extracting b43/lp0bsinitvals13.fw
Extracting b43/lp0initvals13.fw
Extracting b43/n0absinitvals11.fw
Extracting b43/n0bsinitvals11.fw
Extracting b43/n0initvals11.fw
Extracting b43/a0g1bsinitvals9.fw
Extracting b43/a0g0bsinitvals9.fw
Extracting b43/a0g1initvals9.fw
Extracting b43/a0g0initvals9.fw
Extracting b43/b0g0bsinitvals9.fw
Extracting b43/b0g0initvals9.fw
Extracting b43/a0g1bsinitvals5.fw
Extracting b43/a0g0bsinitvals5.fw
Extracting b43/a0g1initvals5.fw
Extracting b43/a0g0initvals5.fw
Extracting b43/b0g0bsinitvals5.fw
Extracting b43/b0g0initvals5.fw
modus@modus-laptop:~/broadcom-wl-4.150.10.5/driver$
Edit/Delete Message

---

### Post by scrypt on 2009-10-08
I still have no wireless interface or connectivity

can someone help me out please??

---

### Post by t0mppa on 2009-10-09
Ok, just wanted to be sure you weren't doing it for the wrong reasons. :)

And looks like things worked out far as those commands are concerned. Well then, it's down to normal wireless troubleshooting, it seems. Open up a terminal, run **lshw -C network** and post back with the results.

---

### Post by scrypt on 2009-10-09
Hi tOmmpa

here is the output :

modus@modus-laptop:~$ sudo lshw -C network
  *-network UNCLAIMED
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: NetLink BCM5784M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 10
       serial: 00:22:19:de:c3:e0
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.97 duplex=full firmware=sb v2.17 ip=192.168.0.3 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s

---

### Post by t0mppa on 2009-10-09
Ok, so no driver is getting associated with your wireless interface, thus the UNCLAIMED part.

Try running ```
sudo modprobe -r b43
sudo modprobe b43
``` to first unload (in case it was already loaded) and then load the b43 driver module. Then run the lshw again and see if it picks up the interface.

---

### Post by scrypt on 2009-10-09
I ran the two commands

sudo modprobe -r

sudo modprobe

and here is lshw -C network output:

modus@modus-laptop:~$ sudo lshw -C network
  *-network UNCLAIMED
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: NetLink BCM5784M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 10
       serial: 00:22:19:de:c3:e0
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.97 duplex=full firmware=sb v2.17 ip=192.168.0.3 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
modus@modus-laptop:~$

---

### Post by scrypt on 2009-10-09
Hey TOmmpa.

can you clarify this for me.

you wrote this in post number :

Well, if you already have fwcutter installed, then they'd be:

Code:

export FIRMWARE_INSTALL_DIR="/lib/firmware"
wget [http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2)
tar xjf broadcom-wl-4.150.10.5.tar.bz2
cd broadcom-wl-4.150.10.5/driver
sudo ../../b43-fwcutter-012/b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" wl_apsta_mimo.o

Except that you would replace the ../../b43-fwcutter-012/b43-fwcutter with the path where it can be found on your system (hint: which b43-fwcutter or locate b43-fwcutter).

Note that you might want to go into a download subdirectory first (~/ where the terminal opens by default refers to your home directory), instead of just running these commands at some random place, since the wget downloads the file into the directory where you're at.




  Here is my output for "locate b43-fwcutter" :


Code:

""export FIRMWARE_INSTALL_DIR="/lib/firmware"
wget [http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2)
tar xjf broadcom-wl-4.150.10.5.tar.bz2
cd broadcom-wl-4.150.10.5/driver
sudo ../../b43-fwcutter-012/b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" wl_apsta_mimo.o

Except that you would replace the ../../b43-fwcutter-012/b43-fwcutter with the path where it can be found on your system (hint: which b43-fwcutter or locate b43-fwcutter).

Note that you might want to go into a download subdirectory first (~/ where the terminal opens by default refers to your home directory), instead of just running these commands at some random place, since the wget downloads the file into the directory where you're at.""



I am unsure about this bit:

""Except that you would replace the ../../b43-fwcutter-012/b43-fwcutter with the path where it can be found on your system (hint: which b43-fwcutter or locate b43-fwcutter).""

can you show me what i should change it to because I still do not have any wirless connectivity!!

---

### Post by scrypt on 2009-10-09
I have also tried reinstaling b43-fwcutter from synaptics and it seems to install okay.
BUt does not give me any options to extract and install the firmware.

what programs should be installed to allow this??

---

### Post by scrypt on 2009-10-09
I seem to be getting somewhere with a bit of help from Mark Rijckenberg from Launchpad/Ubuntu Forum support.

He gave me these links to view

I got the Official Broadcom driver for my BCM4312 from the broadcom web site:

Here

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

I then used the README.txt page file from the same driver download page.

which seem to have got me partially there.

I now have my laptp's WIFI light illuminated .
But, I still have no wireless connectivity.

have you got any suggestion??

---

### Post by t0mppa on 2009-10-09
You already had the firmware loaded, there's no need to do anything about that one. It's just a matter of getting a driver to associate with your interface.

From the last post, it sounds like you ended up installing the Broadcom STA instead. For troubleshooting why the wireless doesn't work, take another look at the lshw to see if it now gets associated with a driver and then do **sudo iwlist scanning** to see, if it can pick up networks.

---

### Post by scrypt on 2009-10-11
Hi TOmmpa.

we seem to be getting somewhere now.

My WIFI light now lights up and my wireless interface shows in ifconfig 

eth0      Link encap:Ethernet  HWaddr 00:22:19:de:c3:e0
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::222:19ff:fede:c3e0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19785 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14424 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:24773481 (24.7 MB)  TX bytes:1874340 (1.8 MB)
          Interrupt:17

eth1      Link encap:Ethernet  HWaddr 00:24:2b:70:48:b4
          inet6 addr: fe80::224:2bff:fe70:48b4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:198 errors:0 dropped:0 overruns:0 frame:0
          TX packets:198 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:85693 (85.6 KB)  TX bytes:85693 (85.6 KB)

BUT. I still cannot connect to the internet wirelessly.

Here is lshw -C network output:

us@modus-laptop:~$ sudo lshw -C network
  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth1
       version: 01
       serial: 00:24:2b:70:48:b4
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
  *-network
       description: Ethernet interface
       product: NetLink BCM5784M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 10
       serial: 00:22:19:de:c3:e0
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.97 duplex=full firmware=sb v2.17 ip=192.168.0.3 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s


Here is the sudo iwlist scanning output


modus@modus-laptop:~$ sudo iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:1F:9F:ED:8B:4B
                    ESSID:"O2wireless0B7E07"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:4/5  Signal level:-63 dBm  Noise level:-92 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 02 - Address: 00:1E:74:6C:22:96
                    ESSID:"SKY08853"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:5/5  Signal level:-53 dBm  Noise level:-90 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 03 - Address: 00:24:2B:48:10:B1
                    ESSID:"BTHomeHub2-H6NR"
                    Mode:Managed
                    Frequency:2.457 GHz (Channel 10)
                    Quality:2/5  Signal level:-77 dBm  Noise level:-90 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s

---

### Post by scrypt on 2009-10-11
Hi TOmmpa.

I appreciate all the help and advice ,

I have proof read the README.txt and your replies. and slowly but surely I created A WLAN interface

I now have A WLAN interface as iwconfig shows below:

modus@modus-laptop:~$ iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

eth1 IEEE 802.11 Nickname:""
          Access Point: Not-Associated
          Link Quality:5 Signal level:0 Noise level:0
          Rx invalid nwid:0 invalid crypt:0 invalid misc:0

I also can see that my WLAN card can successfully see my Router using the sudo iwlist scanning command.

I have also used wicd network manager to create the required encryption methods to connect to my router.

But for some reason I am still not able to connect wirelessly.

I am hoping you might be able to shed a little light on this for me.

---

### Post by kevdog on 2009-10-11
Which AP are you trying to connect to and how are you trying to do it?

---

### Post by scrypt on 2009-10-11
Hey Kevdog...

Good question.

I am using wicd network manager and I can see my router so I enter my WPA key and click connect

I used this to configure my wlan card: [http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt)

It is what I have had the most luck with.

I think it might be trouble blacklisting the below drivers that might be causing the trouble.

When I run these commands:
 echo "blacklist ssb" >> /etc/modprobe.d/blacklist.conf
 echo "blacklist b43" >> /etc/modprobe.d/blacklist.conf 

Nothing happens.
i have posted from the readme.txt below


3: Remove any other drivers for the Broadcom wireless.

There are several open source drivers that are used to drive Broadcom 802.11
chips such as b43 and ssb. If any of these are present they need to be removed before this 
driver can be installed.  Any previous revisions of the wl driver also need to
be removed.

# lsmod  | grep "b43\|ssb\|wl"

If any of these are installed, remove them:
# rmmod b43
# rmmod ssb
# rmmod wl

To blacklist these drivers and prevent them from loading in the future:
# echo "blacklist ssb" >> /etc/modprobe.d/blacklist.conf
# echo "blacklist b43" >> /etc/modprobe.d/blacklist.conf

4: Insmod the driver.

If you were already running a previous version of wl, you'll want to provide a
clean transition from the older driver. (The path to previous driver is usually
/lib/modules/<kernel-version>/kernel/net/wireless)

# rmmod wl 
# mv <path-to-prev-driver>/wl.ko <path-to-prev-driver>/wl.ko.orig
# cp wl.ko <path-to-prev-driver>/wl.ko
# depmod
# modprobe wl

Otherwise, if you have not previously installed a wl driver do this:

# modprobe lib80211
# insmod wl.ko

wl.ko is now operational.  It may take several seconds for the Network Manager
to notice a new network driver has been installed and show the surrounding
wireless networks.

---

### Post by kevdog on 2009-10-11
A lot of explanation there, but I'm still confused.

Just a couple of things you might want to take stock of for now.

Adding stuff to the blacklist and things are good, however I believe this file is only read at boot, and you only need to add modules that come within the kernel itself -- basically they were compiled into the kernel (if you ever compile a vanilla kernel you will see that you have a selection of drivers to compile along with the kernel).

When just playing around with various drivers, you dont need to keep adding things to the blacklist file.  I usually only do this at the very end after I know what works and what doesn't.

Feel free to rmmod / modprobe at will without repercussion just to figure out what works.  

Again what AP are you trying to connect to?  Just to dumb down the complexity of your situation, can you turn encryption off at the router.  I usually only configure WPA once I can confirm the driver is working via making an unencrypted connection.

---

### Post by scrypt on 2009-10-12
I disabled encryption and I can now connect wirelessly.
So this proves that my wireless driver is installed correctly.

I am writing this whilst connected wirelessly.

I am not sure what sure what i can do now to correct my wireless connection with encryption.

Im using wicd network manager

---

### Post by scrypt on 2009-10-12
Thanks for the help.

I think i've fixed my issue.

I tried configuring wicd network manager with different encryption settings to mt AP.

Until I found the correct configuration.

I now have wireless connectivity with my BCM4312

---

### Post by kevdog on 2009-10-12
What was the correct combination?

---

