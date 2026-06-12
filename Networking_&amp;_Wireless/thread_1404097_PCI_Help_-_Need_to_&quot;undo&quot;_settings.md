---
title: "PCI Help - Need to &quot;undo&quot; settings"
date: 2010-02-11
forum: Networking &amp; Wireless
---

### Post by Xog on 2010-02-11
If anyone happens to encounter the same problems I am, go to page 2 of this thread.

---

### Post by Xog on 2010-02-11
I've discovered that I'm using this card:
```
09:07.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface

```
as lspci says.

I've done some digging on this card and couldn't find anything 64-bit related. How can I get this bad boy to work?

---

### Post by chili555 on 2010-02-11
The acx driver that was previously in the mainline kernel has been removed because it is evidently quite buggy. No replacement is on the horizon that I have read about. You might try ndiswrapper.

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by Xog on 2010-02-11
I installed ndiswrapper **but what driver do I use?**

---

### Post by chili555 on 2010-02-11
I think this is going to work: [ftp://downloads.netgear.com/files/wg311v2_v2_0_0_7.zip](ftp://downloads.netgear.com/files/wg311v2_v2_0_0_7.zip)

Download the file, unzip it and navigate to 1.2B6/Driver/Windows XP. There are two files there that will probably work:* netwg311_XP.sys* and *wg311v2.inf*. Although ndiswrapper generally only uses the .inf file, I think this card also needs firmware, which is the .sys file. If they are in the same folder when you install the .inf, ndiswrapper should grab it.

Let me know. If it doesn't work, we can keep searching.

---

### Post by Xog on 2010-02-11
Sounds awesome. Been waiting for months to get internet on my ubuntu partition. I'll let you know when I get home which should be in about 9 hours. :(

The PCI card I have, I got from dealextreme.com, so it's manufactured in Hong Kong. The spelling errors printed on the back make a clear indication that this isn't made by any specific brand like netgear or linksys. There's nothing on the box except for a picture of the card itself with some nice designs and stuff.

But yeah. "Fit firmly on to the pus." Rofl.

The only indication of any company is where it says "EDUP" .. never heard of em.

If ndiswrapper can use 32-bit windows-based drivers on 64-bit karmic let me know. It came with a mini CD that has the drivers for it. The card wouldn't work without me installing the drivers in windows.

---

### Post by chili555 on 2010-02-11
> If ndiswrapper can use 32-bit windows-based drivers on 64-bit karmic let me know.I don't know. If you try it and it won't work, we'll just keep looking until we solve it!> It came with a mini CD What is the file on the CD? Maybe we can extract the .inf and .sys from there.

---

### Post by Xog on 2010-02-11
> **chili555 said:**
> What is the file on the CD? Maybe we can extract the .inf and .sys from there.

I'm at work and I'll be home in about 9 hours. The files I can easily extract, when you put the CD in, you actually have to open up the CD part and look for the setup.exe o_O.. 

then when you install the wireless LAN manager or whatever it is, I had to copy the folder with the drivers in it over to the Drivers folder to where I installed it. It's bootleg but it's the same as any other, it's just not all automated.

basically, dealextreme.com is a type of outsourcing company that sells their own products. They pretty much just copy whatever a regular higher priced brand has, remake it, and sell the exact same thing for a lower price. It's the chinese version of the products, not Americanized, so it won't have some big brand name on it. It's the same thing though. Gotta love Hong Kong.

---

### Post by chili555 on 2010-02-11
> setup.exeWe have ways to almost always extract .exe files, notably cabextract and unshield. Sometimes, these are actually zip or rar files, so the original XP drivers may be accessible. 

You may want to go here: [http://packages.ubuntu.com/karmic/allpackages](http://packages.ubuntu.com/karmic/allpackages)

Grab the 64-bit versions of cabextract, unshield, rar and unrar. Place them on your handy USB key and you'll have them if needed. 

I'll be around when you are ready.

---

### Post by Xog on 2010-02-11
Ready! Downloading the stuff you told me to. Let's see if it works.

---

### Post by chili555 on 2010-02-11
I'm here and ready for a good report!

---

### Post by Xog on 2010-02-12
Thanks for the few hours you helped me while we were on AIM chili.

For anyone that happens to be experiencing the same problems as me:

I'm using 64-bit Ubuntu 9.10.
Wireless PCI card: Texas Instruments ACX 111 54Mbps Wireless Interface ***(notice there is no brand here. Not linksys, not belkin, not anything.)***
Use NDISwrapper. If you can't get it from the internet, they can be found on the LiveCD. Navigate to cdrom/pool/n and you should see the NDISwrapper packages.

We tried a few different drivers from other similar cards and none of them worked (probably because there's no 64-bit drivers for this). We concluded that I need to either

1) Buy a new wireless PCI card that supports 64-bit drivers
2) Install 32-bit ubuntu (9.10) or (9.04 for the acx111 drivers). 9.10's distribution does not include the acx111 drivers in neither 64-bit nor 32-bit. You'll have to do a bit of searching for them.
3) compile. However I ran into some problems with dependencies and since I need the internet to get internet, that's just not going to work.

So overall, when I get home tonight I'm going to install 32-bit 9.10 and use NDISwrapper to install certain drivers.

There's two different drivers I'd like to try.
1) The drivers from the CD that came with the PCI card. I will try these first.
2) These: [http://downloads.linksysbycisco.com/downloads/wpc54gv2_driver_utility_v2.02.zip](http://downloads.linksysbycisco.com/downloads/wpc54gv2_driver_utility_v2.02.zip) I will try 2nd.

I'll make another post when I'm finished with everything and let the community know if this card is even compatible with ubuntu.


Here's a few things to look at:
[http://lxer.com/module/newswire/view/46385/](http://lxer.com/module/newswire/view/46385/)
[https://help.ubuntu.com/community/WifiDocs/Driver/acx111](https://help.ubuntu.com/community/WifiDocs/Driver/acx111)
[http://ubuntuforums.org/showthread.php?t=324148&highlight=Texas+Instruments+ACX+111+54Mbps+Wireless+Interface](http://ubuntuforums.org/showthread.php?t=324148&highlight=Texas+Instruments+ACX+111+54Mbps+Wireless+Interface)

---

### Post by Xog on 2010-02-12
Ahhh.. it feels great to be on ubuntu again!

Here's what I did:
1) Installed 32-bit version of ubuntu 9.10 
2) Installed NDISwrapper from the live-CD (the one you install ubuntu with)
3) Popped in the CD with the drivers, and copied them over to a location in ubuntu.
4) Opened NDISwrapper (System > Administration > Windows Wireless Drivers)
5) Selected the tnet1130.INF file, selected OK
6) Used ubuntu's default network manager (Network Manager, on the top right) and connected to my network!

---

### Post by chili555 on 2010-02-12
Great job! That will help the searchers with the dreaded ACX chipset. Thanks.

---

### Post by morganre on 2010-07-07
> **chili555 said:**
> The acx driver that was previously in the mainline kernel has been removed because it is evidently quite buggy. No replacement is on the horizon that I have read about. You might try ndiswrapper.

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

I"ve been using that buggy driver for years in previous versions of Ubuntu without a problem. I can't go to 10.04 without a hassle?

---

### Post by tudza on 2010-10-23
> **chili555 said:**
> I think this is going to work: [ftp://downloads.netgear.com/files/wg311v2_v2_0_0_7.zip](ftp://downloads.netgear.com/files/wg311v2_v2_0_0_7.zip)

Download the file, unzip it and navigate to 1.2B6/Driver/Windows XP. There are two files there that will probably work:* netwg311_XP.sys* and *wg311v2.inf*. Although ndiswrapper generally only uses the .inf file, I think this card also needs firmware, which is the .sys file. If they are in the same folder when you install the .inf, ndiswrapper should grab it.

Let me know. If it doesn't work, we can keep searching.


I installed Ubuntu 10.04.  I had to install ndiswrapper from the software manager as it didn't seem to be present with the install.

I downloaded the driver referenced and ran the ndiswrapper application to load the Windows XP .inf file.  Working wireless.

Thanks very much.  This posting helped much more than various other wireless How-To articles on the Ubuntu wiki etc.

---

### Post by theqkash on 2011-01-13
Sorry for bumping, here comes actual link for this driver: [http://homedownloads.cisco.com/downloads/driver/wpc54gv2_driver_utility_v2.02.zip](http://homedownloads.cisco.com/downloads/driver/wpc54gv2_driver_utility_v2.02.zip)
However, it haven't required files.

It is here: [ftp://ftp.lab.mlc.edu.tw/pub/Window/LAN/Planex_GW-NS54GM/Driver/winxp/](ftp://ftp.lab.mlc.edu.tw/pub/Window/LAN/Planex_GW-NS54GM/Driver/winxp/)

---

### Post by aaronLund on 2011-12-02
Holy crap.  I've had this card for years and it has never worked.

Then again, I've never seen this thread.

Wow.

I used the XP driver in the previously mentioned zip file.

Also, make sure you have this:

sudo apt-get install ndisgtk

So awesome.

---

