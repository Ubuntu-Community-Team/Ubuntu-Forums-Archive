---
title: "Dell Inspiron E1405 - Ubuntu 13.04 - 32 bit - Won't detect networks"
date: 2013-06-20
forum: Networking &amp; Wireless
---

### Post by aviatorknight on 2013-06-20
[http://ubuntuforums.org/showthread.php?t=2120218&page=2&p=12699613](http://ubuntuforums.org/showthread.php?t=2120218&page=2&p=12699613)

^^^
The above link leads to a 2 page long VERY similar problem complete w/ solution.
I had recently replied to it with the problem at hand, in hopes of rescue.
So far, no response.

Anyway,
The device in question, My Dell INSPIRON | E1405 has recently had the 32-bit version of Linux Ubuntu 13.04 installed on it to replace Windows Vista. (The computer clearly wasn't meant to handle Vista, as could be seen during functionality.)
It was a hand me down from my Uncle.
Moving on.

After installation, the computer seemed completely unable to detect any form of network.
This naturally is a bad thing.

Connected to it currently is an ethernet cord.

The device refuses to acknowledge it's existence.
There is a present and secure WiFi network available the device ALSO seems oblivious to. 

I need help reconnecting it to the internet.

Things of note:
At my disposal is a 2gb sd card and an ARM Samsung Chromebook. 
Google has been of little to no help.
YouTube is equally useless.
I still have the installation disk.
The internet functioned perfectly before the change in OS, suggesting the network interface card is functioning at a suitable level.
I have no money. Times are hard. This means part suggestions are out of the question.
The computer seems to be bias to my charger, allowing it to function as plugged in, but refusing to let it charge the battery. (Just... Why? [Not the point.] )
I'm not certain how to reinstall linux off of the disk. I'm pretty sure it was ment for use on windows...
[COLOR=#ff0000]I don't have syncopate, and without connection through the device, can't seem to obtain it. This means the solution from the thread listed above is in accessible.


[/COLOR][COLOR=#000000]I do have hope however...
If somehow I could get syncopate onto the sd card and install it through the terminal, then I could at least finish attempting the solution from the other thread.

I want to get this device on the internet again...
Please,
Someone...
Help.

[/COLOR]

---

### Post by ahallubuntu on 2013-06-20
~

---

### Post by aviatorknight on 2013-06-20
> **ahallubuntu said:**
> Try this:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

Go to the section "STA - No Internet access" .

Your wireless card most likely a Broadcom BCM4311 (you can verify this by doing "sudo lshw -C network").

If you want to solve this problem permanently, buy a full-height Intel WiFi Link 5100 card off eBay for about $5 USD used - make sure to get the full-height card that is *NOT* for HP/Lenovo.  Ubuntu recognizes these Intel wireless cards automatically.

I don't really care how permanent the solution is, so long as I'm given one. XD

The section yielded no fruitful solutions,
the terminal commands did nothing, and all that was achieved was my learning that my kernel is

3.8.0-19-generic

and that upon entering - -get-selections | grep headers

linux-[COLOR=#ff0000]headers[/COLOR]-3.8.0-19                             install
linux-[COLOR=#FF0000]headers[/COLOR]-3.8.0-19-generic                  install
linux-[COLOR=#FF0000]headers[/COLOR]-generic                               install

all appeared on the textbox.

Also, attempting to download the folders the page recommended from the disk only revealed that it *WAS* downloaded.
Attempting to re-install them only ends in frustration as an account is needed that can only be made online.

I had prior alerted you to my lack of money, so for now, that solution is a no-go. I'll keep it in mind however, so thank you! :D

Anyone else?

---

### Post by wildmanne39 on 2013-06-20
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named wireless-info.tar.gz in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by ahallubuntu on 2013-06-20
~

---

### Post by varunendra on 2013-06-21
> **ahallubuntu said:**
> If you want to fix it once and be good until 2017, use 12.04 LTS and the suggested solutions.

I would +1 to 12.04 for several reasons including above one.

However, if it turns out to be indeed a BCM4311 card, the solution would be as easy as downloading the "linux-firmware-nonfree" package from [here]("http://packages.ubuntu.com/precise/all/linux-firmware-nonfree/download") and double-click it to install. Same for any version of Ubuntu.

If unsure, just run Wild Man's script, and post back the results here.

---

