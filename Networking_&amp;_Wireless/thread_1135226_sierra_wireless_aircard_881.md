---
title: "sierra wireless aircard 881"
date: 2009-04-24
forum: Networking &amp; Wireless
---

### Post by perlsyntax on 2009-04-24
I just download ubuntu 9.04 and i try to get my sierra wireless card to work.But it pick up the card but when the light is on but when i try to connect it the light is not on and my internet will not work.Do i ned to update something or what.


I hope someone can help me.And it did work in 8.10 after i updated the network manger.:(

---

### Post by rlzyoner on 2009-04-24
Have you ran updates for 9.04

Maybe try that if it worked for 8.10.

Let us know if the issue remains afterwards

---

### Post by perlsyntax on 2009-04-24
i did the update thing before i put the pc card in.

---

### Post by rlzyoner on 2009-04-24
I'm not sure what drivers your card would use.
You might find more info on [http://www.linuxwireless.org/](http://www.linuxwireless.org/)

Lots of useful info there

---

### Post by perlsyntax on 2009-04-24
I don't see my driver on that page.

---

### Post by rlzyoner on 2009-04-24
Try this [http://www.sierrawireless.com/faq/ShowFAQ.aspx?ID=607](http://www.sierrawireless.com/faq/ShowFAQ.aspx?ID=607)

---

### Post by perlsyntax on 2009-04-24
I have kernel 2.6.28-11

---

### Post by rlzyoner on 2009-04-24
"This guide is for Linux users who would like to install and use a Sierra Wireless device on a recent kernel (2.6.21 or newer)"

So you should be good to go !

---

### Post by perlsyntax on 2009-04-24
Still think it my network-manger howwould i update this do i have to download a tar file?

---

### Post by rlzyoner on 2009-04-24
Did you try the guidelines in the link I provided ?
I doubt its a network manager issue.
If you still think it might be, then try connecting manually in the shell.

---

### Post by perlsyntax on 2009-04-24
How would i do that?

---

### Post by rlzyoner on 2009-04-24
Off the top of my head

iwconfig wlan0 essid YOUR_ESSID
iwconfig wlan0 mode managed
iwconfig wlan0 YOUR_KEY
dhclient3

You'll probably need to sudo those

There's a load of info online mate.

Maybe start here if needs be
[https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)

---

### Post by perlsyntax on 2009-04-24
This for a 3G or 2G network

---

### Post by rlzyoner on 2009-04-24
Sorry mate, excuse the ignorance, it's been a long day.

What do you mean "This for a 3G or 2G network"

---

### Post by CorporateGoth on 2009-04-24
Check /var/log/messages for stuff coming from pppd.  You might be getting the same problem I am having where your PPP connection looks fine, you get an IP and DNS server info, but no default route is created and then after a short period of time, NetworkManager kills the connection.

I am finding this ONLY happens after I've established a connection once and every subsequent connection attempt will fail.  Rebooting fixes this for me, but only for the 'first' connection, and if I disconnect (due to, say, suspend or whatever) then I will not be able to make another connection using the sierra card until I reboot again.

I think it might be NetworkManager or more probably, the network manager plugin for pppd.

---

### Post by krgp on 2009-04-24
Could someone please provide a tutorial for how to get Sierra Aircards working in Jaunty for noobs? I run a USBConnect 881 3G on Cingular/At&t. I had it working on Intrepid. When I plug it in, Jaunty recognizes it, "configures" network mgr, and then it can't connect. The Sierra page is way too cryptic for me. Please! I'll send sweet southern karma your way. Thanks.

---

### Post by ceefour on 2009-04-27
> **krgp said:**
> Could someone please provide a tutorial for how to get Sierra Aircards working in Jaunty for noobs? I run a USBConnect 881 3G on Cingular/At&t. I had it working on Intrepid. When I plug it in, Jaunty recognizes it, "configures" network mgr, and then it can't connect. The Sierra page is way too cryptic for me. Please! I'll send sweet southern karma your way. Thanks.

I understand your frustration.

I too own a Sierra Aircard Wireless USBConnect 881U that worked well in Ubuntu/Kubuntu Intrepid Ibex 8.10 that is now not working in Ubuntu/Kubuntu Jaunty Jackalope 9.04.

I thought it was a problem with 3G in general in Jaunty but I also owned a Nokia E71 and (thankfully) I can connect to my 3G using Nokia E71 flawlessly to do initial package installation.

I think you should report a bug on Launchpad for this issue.

But here's a workaround using UMTSMon that works for me.

[LIST=1]
[*]Find a WiFi hotspot or something so that you can install packages and download files
[*]Install the [FONT="Courier New"]libqt3-mt[/FONT] package using Synaptic. This is the only prerequisite of UMTSMon.
[*] Checkout this forum thread: [http://ubuntuforums.org/showthread.php?p=5449081](http://ubuntuforums.org/showthread.php?p=5449081) . I opt to use the compiled version, which is easiest. Refer to the instructions here.
[*] Extract the file you downloaded. Refer to the instructions there.
[*] To run UMTSMon, a plain run doesn't work for me. I had to use gksu, e.g.:
```
gksu ./umtsmon-0.8/umtsmon
```
[/LIST]

It's not very convenient (UI not very integrated, Firefox detects as offline, etc.), but after installing UMTSMon I can connect to 3G using my Sierra 3G/HSDPA modem just fine.

Plus, using UMTSMon I can force my modem to connect to 3G only or 2G only.

Of course, this is no replacement for "real" 3G support in Ubuntu but until Ubuntu made a fix, this makes my life sustainable. :)

---

### Post by ceefour on 2009-04-28
I've reported this as Launchpad Bug #368457

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/368457](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/368457)

---

### Post by the_llama on 2009-05-01
> **krgp said:**
> Could someone please provide a tutorial for how to get Sierra Aircards working in Jaunty for noobs? I run a USBConnect 881 3G on Cingular/At&t. I had it working on Intrepid. When I plug it in, Jaunty recognizes it, "configures" network mgr, and then it can't connect. The Sierra page is way too cryptic for me. Please! I'll send sweet southern karma your way. Thanks.

I'm in the same exact boat. Worked fine in Intrepid, doesn't work in Jaunty. Please update this thread if you find the solution.

---

### Post by networkthinking on 2009-05-01
Same here...looking for an update on this...

---

### Post by dconvery on 2009-05-07
I figured it out...There is a firmware update on SIerra's site. I applied that and now it works. Unfortunately, you will need a winders or mac machine to update the fw

[http://www.sierrawireless.com/support/show_support_and_downloads.aspx?id=4,45,1,1](http://www.sierrawireless.com/support/show_support_and_downloads.aspx?id=4,45,1,1)

[http://www.sierrawireless.com/support/show_support_and_downloads.aspx?id=4,45,1,2](http://www.sierrawireless.com/support/show_support_and_downloads.aspx?id=4,45,1,2)

Dave

---

### Post by DirtyBirdflock on 2009-05-08
does this firmware update do anything to the card itself cause i use the sierra wireless usbconnect 881 card for my ubuntu which like everyone else it worked fine for the previous version but know does not work at all for the 9.04 version. but i'm not the only one that uses the card in my house hold. another person in my house uses a sony viao with vista on it and uses the card frequently so i dont want to do anything that is going to prevent them from being able to use the card. but i would like it to work for my ubuntu as well as the other computer any help on this one or am i just thinking to much into it?

---

### Post by crayzeewulf on 2009-05-12
> **dconvery said:**
> I figured it out...There is a firmware update on SIerra's site. I applied that and now it works.

Same here. The 881 stopped working with Jaunty and had similar behavior on at least one Windows XP machine. Everything works after the firmware update. :P

---

### Post by satx_nole on 2009-06-04
After upgrading the firmware, I was also able to successfully connect.   

Thanks for the Tip!

---

### Post by brian mcgee on 2009-07-06
> **dconvery said:**
> There is a firmware update on SIerra's site. I applied that and now it works.

Upgrading to the latest firmware worked for me too. Thanks!

---

### Post by digus on 2009-08-17
btw - just in case anyone that reads this thread is confused - the aforementioned solution applies to the Sierra _USB_ 881 aircard only. If you have the regular old Sierra 881 "PC-Card" or "PCMCIA" card (old-school, non-USB laptop card slot), you need the firmware here (for winderz only):
 
 [http://www.sierrawireless.com/support/show_support_and_downloads.aspx?id=4,12,1,1](http://www.sierrawireless.com/support/show_support_and_downloads.aspx?id=4,12,1,1)
 
 If you don't have the drivers installed or the installation CD that came with the card, you may have to install the "3G_Watcher" first (not sure about this), also located on that page. The PC-Card/PCMCIA 881 also suffers from the same issue that the USB 881 does in Ubuntu 9.04. It used to work in 8.10 - now it doesn't - until you update the firmware.
 
I'm not sure if this solution/firmware is really specific to AT&T (as stated somewhere above) - my card is unlocked and has been used (and works) with T-Mobile's network also (in the USA). After updating the firmware, my card is now getting about 4 times better bandwidth and one-third of the latency (600kbps/300kbps - ~100ms - in a fairly small city). The blue 3G light is actually lit up now, whereas it only used to be a red 2G light. I used to only get 50-150kbps and anywhere from 300ms to several seconds of latencly...

Good Luck!

---

### Post by CDrewing on 2009-11-27
**@digus:**

Well, *W32...* ](*,)
Can I update the firmware by letting the update run under a virtual guest system (i.e. Win7@VMware)? This wouldn't be a problem, because it is already running here.

Greetz
Christian

---

### Post by CDrewing on 2009-12-04
**[COLOR="Red"]W O R K E D !![/COLOR]**

OK, I ran Windows 7 Ultimate MSDNAA under VMware Workstation and installed the original drivers from Sierra. Card worked perfectly in the guest OS (ridiculous!). So I started the update process. VMware is giving warnings frequently that it has to "steal" the card from the host OS to have complete access. So I granted this procedure. After a while the firmware update tool told me that the update succeeded. The card still worked fine under Win7 (guest).

Then I tried umtsmon again. Login perfect, but no IP connection. Same scenario as before I did the update.

So then I started looking for solutions regarding the card, again. And then I realized that I was on UMTS (I switched off WiFi to be sure to know if the card will work via Win7 or not)!!


_Here are my stats:_

[[IMG]http://www.pingtest.net/result/5065110.png[/IMG]](http://www.pingtest.net) [[IMG]http://www.speedtest.net/result/642762476.png[/IMG]](http://www.speedtest.net)

```
lsusb:
Bus 006 Device 003: ID 1199:6851 Sierra Wireless, Inc. AirCard 881 Device
```

Well it's not that much for 3G, I am logged in with HSDPA but E-Plus is limiting a customer's bandwidth with 384 kbit/s so that the huge HSDPA-network resources will be availabe to a higher number of customers instead of being available for just some powerusers (who would be logged in at 7.2 MBit/s... theoretically, but practically with almost zero). Due to my location (Berlin, Germany, 3 Mio. people) I think this makes sense.

Thank you for all the help!
Christian.

---

