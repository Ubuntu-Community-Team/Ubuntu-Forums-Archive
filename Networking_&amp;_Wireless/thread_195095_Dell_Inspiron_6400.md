---
title: "Dell Inspiron 6400"
date: 2006-06-12
forum: Networking &amp; Wireless
---

### Post by dbott67 on 2006-06-12
I purchased a new laptop back in March and the only issues I had had were getting the video working properly (I had to wait for ATI to release the drivers) and wi-fi.  After trying multiple solutions to get my wi-fi working on my Dell Inspiron 6400 I finally succeeded.  Here is what I did to get things working:

**_Specs:_**

Dell Inspiron 6400
Dual Core T2400 (1.83 GHz)
ATI x1400 (256 MB RAM)
2 GB RAM
100 GB Hard Drive

**_Installing ATI Drivers for ATI x1400_**

1. Follow the "Automatic Driver Installation Option" at [ATI's site]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.25.18-inst.html").

**_Enabling Broadcom Wi-fi_**

1. For enabling wi-fi, I tried this [Broadcom How-to]("http://www.ubuntuforums.org/showthread.php?t=185174") first, but it did not work for me.

2. I found another thread that suggested downloading the latest version of [ndiswrapper]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation").

There are some pre-requisites required, such as gcc for compiling ndiswrapper, your kernel source files and maybe a few dependencies.  I used Synaptic to install gcc, as well as all of the "Mark Recommended for Installation" and "Mark Suggested for Installation" packages.

My kernel is:
```
dbott@dapperdrake:~$ uname -r
2.6.15-23-686

```

My Broadcom wi-fi is detected as:
```
dbott@dapperdrake:~$ lspci | grep Broadcom
0000:03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
0000:0b:00.0 Network controller: Broadcom Corporation: Unknown device 4311 (rev 01)
```

After following the instructions on the ndiswrapper site, my wi-fi worked.  I'm not sure if it's just because of the latest ndiswrapper (1.16 in my case), or because I had also followed the previous howto that installed new firmware.

-Dave

---

### Post by chuckao on 2006-08-04
Hi,
> **dbott67 said:**
> 
..........
My Broadcom wi-fi is detected as:
```
dbott@dapperdrake:~$ lspci | grep Broadcom
0000:03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
0000:0b:00.0 Network controller: Broadcom Corporation: Unknown device 4311 (rev 01)
```
-Dave

I have the same laptop, I'm sure that you did a mistake. 

**Broadcom** is your ethernet 10/100 network device and it isn't your wi-fi device. Your wi-fi device is **Intel 3945abg**, and this device works out-of-box (ubuntu 6.06). You just need to set the SSID, WEP, etc.

I really don't know how you did to put your ethernet device to works like wi-fi device :D 

Cheers,

---

### Post by dbott67 on 2006-08-04
Actually, my laptop does have the Broadcom chipset for the wireless card.  Dell offers a number of different wireless chipsets to choose from (and depending on supply & demand) have to switch chipsets.

Here is the [page with all of the current chipsets.]("http://www1.ca.dell.com/content/learnmore/learnmore.aspx?c=ca&cs=19&l=en&ref=CFG&s=dhs&~id=dfamilywireless&~lt=popup&~series=inspn&~tab=details")  If you scroll to the bottom, you'll notice that the first chipset uses the **Intel Centrino** logo, while the other 3 use the **Broadcom** logo.

At the time I bought mine, had I done a little more research, I may have chosen the Intel chipset for native driver support.  As it stands, I have the latest ndiswrapper compiled and it works with my Broadcom.

```
 *-network
                description: Wireless interface
                product: Broadcom Corporation
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0b:00.0
                logical name: wlan0
                version: 01
                serial: 00:16:ce:31:88:6f
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ndiswrapper driverversion=1.16 firmware=Broadcom,11/02/2005, 4.10.40.0 ip=192.168.1.105 link=yes multicast=yes wireless=IEEE 802.11b

```

-Dave

---

### Post by chuckao on 2006-08-05
Hi Dave,

I'm sorry! :-( I really didn't know that there are Dell 6400 laptops without Centrino tech.

cheers,

---

### Post by dbott67 on 2006-08-05
No worries, chuckao! :)  I just wanted to point out that Dell (and many others) can offer different configurations of hardware and also change some of the innards if supplies of one part run low. 

When I was looking to buy a laptop, I had a number of things in mind:

- dual-core (either Intel or AMD)
- decent 3D video (preferably nVidia for *nix support, but would settle for a decent ATI)
- 2 GB RAM (to run VMware, XP, 2K3, Ubuntu)
- 100 GB+ hard drive (for multi-boot OS: XP Pro, XP MCE, Win2K3 Server, Ubuntu)
- good battery life

I eventually decided to go Intel Core Duo, as AMD did not have a dual core Turion (at the time), which would have provided better battery time than the Athlon 64 x2 chip and a heck of a lot less heat.  32-bit OSes are here for at least one more generation (i.e. Vista), as well as having much better driver support than 64-bit.

I also wanted a decent video card for those times that I might want to get back into Quake/Half-life/etc. (but having 2 kids under the age of 5 cuts into most of Dad's free time).  As I was preparing to make my purchase, Dell only had the Intel GMA 950 on their Inspiron 6400.  Even though I was hoping for a better card, Dell had the best deal and I knew that the GMA 950 was supported in Linux, so I decided to go ahead with the purchase.

A few hours after I placed my order, I went back to check the site and noticed that Dell was now offering the 6400 with the ATI x1300, x1400 and x1600 chipsets.  ZOIKS!  What to do?

I decided that since my primary function for the laptop was to help me plan, configure & deploy a Windows 2003 AD system, I should go for the ATI x1400 (for better 3D performance in Windows) and sacrifice 3D in Ubuntu (at least until ATI released linux drivers for the new x-1000 series).

I called my Dell rep the next day to change the order and got the ATI x1400.  Better yet, within a few weeks of receiving my laptop, ATI released the linux drivers.   I got the best of both worlds! :)

Of course now they have a number of dual-core notebooks with nVidia, so had I waited I could've ordered an Inspiron XPS 1210 with 256MB NVIDA® GeForce&#8482; Go 7400.  Oh well.

Overall, I am very pleased with the 6400.  Dapper installed perfectly, although I did have to download the latest ndiswrapper and compile it to get wifi working, and I also needed to download the ATI drivers to enable 3D support.

A very heart-felt THANK YOU to the Ubuntu team. :)

-Dave

---

### Post by chuckao on 2006-08-06
> A few hours after I placed my order, I went back to check the site and noticed that Dell was now offering the 6400 with the ATI x1300, x1400 and x1600 chipsets. ZOIKS! What to do?

Yes, and now the Dell 6400 has Soundblaster Audigy  :( I want it!! :-p

cheers,

---

