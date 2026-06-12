---
title: "BCM43225 and limitation UK/Europe Channels 12/13"
date: 2012-05-11
forum: Networking &amp; Wireless
---

### Post by Martyn Thompson on 2012-05-11
Hi, 

I am using the BCM43225 in my Acer Aspire 5551.  It has always worked well with my own wireless router but suddently stopped working with my friends router.  A bit of sleuthing came up with the fact that he has changed the frequency of his connection to channel 13.  

It seems that the "brcmsmac" driver is optimised for US use and therefore limits channels from 1 to 11.  

Is there any (easy) hacks that I can apply to gain the extra two channels which are legal in my country (United Kingdom). The following is from nm-tool when connected via Channel 11.  

Any advice would be gratefully accepted.  I am using 12.04 with pae but believe this is not related to just this release. 

nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan0  [*** ESSID HIDDEN ***] ----------------------------------------------
  Type:              802.11 WiFi
  Driver:            brcmsmac
  State:             connected
  Default:           yes

---

### Post by chili555 on 2012-05-11
> It seems that the "brcmsmac" driver is optimised for US use and therefore limits channels from 1 to 11. I haven't seen that and if you have a link, I'd be anxious to add it to my meager files on Broadcom drivers.

You might try this:```
sudo gedit /etc/modprobe.d/cfg80211.conf
```Add one line:```
options cfg80211 ieee80211_regdom=UK
```Proofread, save and close gedit. Unload and reload brcmsmac:```
sudo modprobe -r brcmsmac
sudo modprobe brcmsmac
```Check:```
sudo cat /var/log/syslog | grep cfg | tail -n20
cat /sys/module/cfg80211/parameters/ieee80211_regdom
```Any improvement?

It may take a reboot.

---

### Post by Martyn Thompson on 2012-06-03
Hi chili555.

Sorry for not getting back sooner.  I tried the fixes you suggested and although it seems the settings have been corrected to EU/GB.  Unfortunately it still not pick up channels 12 and 13.  This is made even more frustrating because the other half has a Compaq using the "**ath9k**" module which works perfectly on her board.  (To be fair, it makes it easier for swapping the Wireless Router settings over for testing purposes).  

I have included the output requested.

Thanks for any advice. 

Martyn.


sudo cat /var/log/syslog | grep cfg | tail -n20

```
Jun  3 21:00:36 Aspire-5551 kernel: [    9.582976] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
Jun  3 21:00:36 Aspire-5551 kernel: [    9.582979] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jun  3 21:00:36 Aspire-5551 kernel: [    9.582981] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
Jun  3 21:00:36 Aspire-5551 kernel: [    9.582984] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jun  3 21:00:36 Aspire-5551 kernel: [    9.582987] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
Jun  3 21:00:36 Aspire-5551 kernel: [    9.582989] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jun  3 21:00:36 Aspire-5551 kernel: [    9.582992] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
Jun  3 21:00:36 Aspire-5551 kernel: [    9.582995] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jun  3 21:00:36 Aspire-5551 kernel: [    9.582997] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
Jun  3 21:00:36 Aspire-5551 kernel: [    9.583000] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jun  3 21:00:36 Aspire-5551 kernel: [    9.583002] cfg80211: Disabling freq 2467 MHz
Jun  3 21:00:36 Aspire-5551 kernel: [    9.583004] cfg80211: Disabling freq 2472 MHz
Jun  3 21:00:36 Aspire-5551 kernel: [    9.583005] cfg80211: Disabling freq 2484 MHz
Jun  3 21:00:36 Aspire-5551 kernel: [    9.583008] cfg80211: Current regulatory domain intersected:
Jun  3 21:00:36 Aspire-5551 kernel: [    9.583010] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jun  3 21:00:36 Aspire-5551 kernel: [    9.583013] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Jun  3 21:00:36 Aspire-5551 kernel: [    9.583015] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 1700 mBm)
Jun  3 21:00:36 Aspire-5551 kernel: [    9.583018] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Jun  3 21:00:36 Aspire-5551 kernel: [    9.583020] cfg80211:     (5490000 KHz - 5600000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Jun  3 21:00:36 Aspire-5551 kernel: [    9.583023] cfg80211:     (5650000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2000 mBm)
```

cat /sys/module/cfg80211/parameters/ieee80211_regdom
```
GB
```

---

### Post by Martyn Thompson on 2012-06-03
As requested - here is the link:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/288401](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/288401)

---

### Post by praseodym on 2012-06-03
Can you try:
```

sudo apt-get install iw
iw reg get
sudo iw reg set UK
iw reg get
```
Check:
```
iwlist chan
```

---

### Post by chili555 on 2012-06-03
> sudo iw reg set UK'UK' is not a valid code: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2)

---

### Post by praseodym on 2012-06-04
Right. It needs to be

> sudo iw reg set GB

---

### Post by katletz on 2012-06-06
This is driving me crazy, too :(.

Dell Latitude E6220 with BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)

once in a while, I see all 13 channels (disabling network-manager, starting wpa_supplicant with a line containing "country=AT", a couple of "iw reg set AT" , export COUNTRY=AT, etc.). BUT, I can't find any system behind this. Anyway, even when iwlist chan gives me all 13, it doesn't connect with my AP:

wlan0: authentication with 00:15:f2:yy:yy:yy timed out
[ 3625.988010] wlan0: authenticate with 00:15:f2:yy:yy:yy (try 1)
[ 3626.184631] wlan0: authenticate with 00:15:f2:yy:yy:yy (try 2)
[ 3626.384409] wlan0: authenticate with 00:15:f2:yy:yy:yy (try 3)

no problem when I set my router to channel 11 (or use Windows 7 on the same laptop _and_ channel 13)! So it's definitely the bloody driver (someone on a forum suggested it's etched in silicon which frequencies are accessible)

However, most of the time I only see:
 cfg80211: Regulatory domain changed to country: AT
....
cfg80211: Calling CRDA for country: US
cfg80211: Disabling freq 2467 MHz
[ 4487.700051] cfg80211: Disabling freq 2472 MHz
[ 4487.700052] cfg80211: Disabling freq 2484 MHz
[ 4487.700054] cfg80211: Current regulatory domain intersected:

I have a # cat /etc/modprobe.d/cfg80211.conf 
options cfg80211 ieee80211_regdom=AT

It looks someone is calling crda (after setting the regdomain), which falls back to US (miles away), and channels 12&13 are gone.

anyone knows how to fix this, please? :confused:

thanks,
stefan

---

### Post by chili555 on 2012-06-06
> It looks someone is calling crda (after setting the regdomain), which falls back to US (miles away), and channels 12&13 are gone.

anyone knows how to fix this, please? Do I *know* how to fix this? No. Am I willing to google and help you experiment. Certainly yes.

I don't think there is any doubt that wireless devices have CRDA information written in their EEPROM and/or firmware; that is,'etched in silicon.' Here are two interesting links. First the scary one: [https://bbs.archlinux.org/viewtopic.php?id=124574](https://bbs.archlinux.org/viewtopic.php?id=124574)> crda will only read regulatory.bin's which are signed with the same key as crda itself is built with. While I could/should probably edit a PKGBUILD to allow me to drop in my own keys, what I actually did was grab the source of crda and wireless-regdb from linux-wireless. Within the crda README, there's a paragraph describing how to produce your own regulatory.bin - essentially, create your private and public keys, edit db.txt (in my case, copying GB settings into World and US, just to make sure), and running a python script from wireless-regdb to create regulatory.bin (note, I had to edit these scripts to use python2 instead of python). Then, I could put bit in the right place, run make; make install on crda, and reboot. After reboot, iw list returned the correct channels.Yikes!!! 

And one less scary: [http://linuxwireless.org/en/developers/Documentation/cfg80211](http://linuxwireless.org/en/developers/Documentation/cfg80211)  > If an AP supports sending the Country IE it will send the country IE appended on every beacon. So it may be that your router is saying it's located in or manufactured in the US.

As a start, you might edit /etc/default/crda to add AT and reboot. Check the syslogs and see if anything has improved.

---

### Post by katletz on 2012-06-07
Hi,

thanks for the reply, it was really useful (though it still didn't solve my problem completely).

> **chili555 said:**
> Do I *know* how to fix this? No. Am I willing to google and help you experiment. Certainly yes.

I don't think there is any doubt that wireless devices have CRDA information written in their EEPROM and/or firmware; that is,'etched in silicon.'


I've googled a bit myself (always do before going public):  see the paragraph above [http://linuxwireless.org/en/users/Drivers/brcm80211#Mainline_patches](http://linuxwireless.org/en/users/Drivers/brcm80211#Mainline_patches)
> 
The devices use a single  worldwide regulatory domain, with channels  12-14 (2.4 GHz band) and  channels 52-64 and 100-140 (5 GHz band)  restricted to passive operation.  Transmission on those channels is  suppressed until appropriate other  traffic is observed on those  channels. Within the driver, we use the  ficticious country code "X2" to  represent this worldwide regulatory  domain.
So broadcom does this differently than e.g. atheros (I had to set the regdomain in firmware before another atheros card worked properly). Also, windows7 would have refused to connect to my AP on channel 13 either...

> **chili555 said:**
> 
So it may be that your router is saying it's located in or manufactured in the US.

As a start, you might edit /etc/default/crda to add AT and reboot. Check the syslogs and see if anything has improved.

This was really useful. I found the settings for my AP (asus 500g deluxe) and enabled the regulatory mode (802.11h or d), and edited the /etc/default/crda file (have missed both on my experiments before). Now crda sets the regdomain to either AT or DE (haven't found how to set the AP's regdomain to AT - but, technically, the differences between DE and AT are tiny ;)).

"iwlist chan" automatically lists all channels 1-13, I see my AP, BUT, I still get only

wlan0: authenticate with 00:15:f2:yy:yy:yy (try 1)
[ 3631.497671] wlan0: authenticate with 00:15:f2:yy:yy:yy (try 2)
[ 3631.697413] wlan0: authenticate with 00:15:f2:yy:yy:yy (try 3)
[ 3631.897151] wlan0: authentication with 00:15:f2:yy:yy:yy timed out

I have turned off all authentication (open system, no key) and access control (mac filter), so anyone could connect (except my dell running ubuntu).
Is brcmsmac broken?

Anyother suggestions?
Stefan

PS: This doesn't make sense at all: With my AP set to channel 13, when I boot my Dell I get:

[   19.594555] cfg80211: Calling CRDA to update world regulatory domain
[   19.702853] cfg80211: Calling CRDA for country: DE
[   20.493152] cfg80211: Calling CRDA for country: US

of course, I can't connect, since I'm restricted to chan 1-11. I think what happens is this: If a single AP around me is set to US (or no reg domain), the broadcom driver falls back to US mode, so one bad apple destroys it for all. The reason why I'm trying to move to chan 13 is because is really crowded around me...

Then, when I switch my AP to chan 6, for example, I can connect and another line pops up:
[  463.624399] cfg80211: Calling CRDA for country: DE

When I'm on chan 6, I don't need any special regdomain. AAAARRRGGH

Without overriding any automatic detection (and actually being able to associate on channel 13), this is a useless piece of software.

---

### Post by chili555 on 2012-06-07
> Is brcmsmac broken?Funny you should ask. brcmsmac is new for us as of 12.04. We who work with these things frequently on the forum have, of consequence, little experience with it. The few times I've seen it, once a few issues are sorted, it just works. Of course, it may 'just work' in the USA, and it may 'just work' on channel 6, etc., but not so well in other situations like yours. 

We learn the subtleties because someone posts a problem and we figure out a solution sometimes by trial and error. Ouch. 

The issues, that is, whether to use brcmsmac, b43 or wl (also known as Broadcom STA), depends on the pci.id. I believe your BCM43225 is 14e4:4727. Please check:```
lspci -nn | grep 0280
```If so, we believe brcmsmac is correct. You should check to be sure that the others are *not* loaded:```
lsmod | grep -e wl -e b43
```If they are, we have some work to do.

If your pci.id is different, please post it and we'll learn together.

Quite a few Linux wireless drivers are troubled (read: won't work at all) by N speeds. Is there any improvement with the router set to do B and G only?

---

### Post by katletz on 2012-06-07
Update:

I compiled the drivers from broadcom myself:
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)
according to the readme file, but I had to apply this patch:
[http://www.linuxquestions.org/questions/slackware-14/compiling-broadcom-driver-947294/](http://www.linuxquestions.org/questions/slackware-14/compiling-broadcom-driver-947294/)

module loads, reg domain is correct, still no connects on channels >11:

[ 3319.767177] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[ 3319.768396] lib80211_crypt: registered algorithm 'TKIP'
[ 3319.839399] eth1: Broadcom BCM4727 802.11 Hybrid Wireless Controller 5.100.82.112
[ 3323.657903] cfg80211: Calling CRDA for country: DE
...
Regulatory domain changed to country: DE
[ 3396.795772] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 3396.795778] cfg80211:     (2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 3396.795783] cfg80211:     (5150000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 3396.795788] cfg80211:     (5250000 KHz - 5350000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 3396.795793] cfg80211:     (5470000 KHz - 5725000 KHz @ 40000 KHz), (N/A, 2698 mBm)
[ 3749.048194] ERROR @wl_cfg80211_connect : error (-22)
[ 3756.697069] ERROR @wl_cfg80211_connect : error (-22)
[ 4078.184269] ERROR @wl_cfg80211_connect : error (-22)
[ 4133.499934] ERROR @wl_cfg80211_connect : error (-22)
[ 4155.614619] ERROR @wl_cfg80211_connect : error (-22)
[ 4234.694238] ERROR @wl_cfg80211_connect : error (-22)

1-11 run smoothly, except for the neighbours trying to interfere...
maybe I should just upgrade my router to 802.11n.

iwlist eth1 chan
eth1      32 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 34 : 5.17 GHz
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Current Frequency:2.462 GHz (Channel 11)

stefan

---

### Post by katletz on 2012-06-07
lspci -nn |grep 0280
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)

wl or b43 are not present (except when I insmod'ed my compiled wl.ko module, and rmmod'ed all brcm* modules before).

---

### Post by chili555 on 2012-06-07
Whaaaatt??? Now I'm confused. You are using wl and not brcmsmac? > Is brcmsmac broken?What is your pci.id?```
lspci -nn | grep 0280
```:confused:

---

### Post by chili555 on 2012-06-07
> **katletz said:**
> lspci -nn |grep 0280
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)

wl or b43 are not present (except when I insmod'ed my compiled wl.ko module, and rmmod'ed all brcm* modules before).However, eth1 is typical of the wl driver, not brcmsmac.> [ 3319.767177] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[ 3319.768396] lib80211_crypt: registered algorithm 'TKIP'
[ 3319.839399] [COLOR="Red"]eth1[/COLOR]: Broadcom BCM4727 802.11 Hybrid Wireless Controller 5.100.82.112
[ 3323.657903] cfg80211: Calling CRDA for country: DE

EDIT: If you get a 4727 to work with the STA driver, even patched, you'll be a first. Not impossible, but a first.

---

### Post by katletz on 2012-06-07
sorry for the confusion.

1. I started with brcmsmac, because it allows me to use iw reg set

2. since that didn't work, I compiled my own STA driver from the broadcom webpage with option[FONT=monospace]
[/FONT]make API=CFG80211
so I can still use iw.

With this driver, my 
02:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
(from lscpi) is reported as
eth1: Broadcom BCM4727 802.11 Hybrid Wireless Controller 5.100.82.112
(in dmesg)
Of course, I paid attention to use only one of the drivers at the same time.

Bottom line: still can't connect on channel 13.
I also tried B only (or G only) on the AP, with both drivers.

I'm giving up, and switch to channel 6.
Stefan

---

### Post by chili555 on 2012-06-07
Sorry I couldn't be of more help. To confirm, 4727 will work with a compiled *with a patch* STA driver.

---

### Post by Fuxy on 2012-06-07
Bug confirmed!
I have an **Acer Aspire 5742** with a **broadcom** **BCM43225 **card that for some reason starts of initialized with a domain of US even though I'm in the UK.

Doing
```
sudo iw reg set GB
```will give me all 13 channels however if i set my router to channel 12 or 13 and try to connect to it it keeps on trying ocassionally asking for the router password.

Also setting the /etc/default/crda to ```
REGDOMAIN=GB
``` will change my it on startup from US to GB however the same effect.

Seriously what the hell it can see it why can't it connect? ](*,)

---

### Post by chili555 on 2012-06-07
> I have an Acer Aspire 5742 with a broadcom BCM43225Which driver are you using?```
lsmod | grep -e wl -e brcm
lspci -nn | grep 0280
```

---

### Post by Fuxy on 2012-06-07
~$ lsmod | grep -e wl -e brcm ```
brcmsmac              570859  0 
mac80211              506816  1 brcmsmac
brcmutil               15139  1 brcmsmac
cfg80211              205544  2 brcmsmac,mac80211
crc8                   12893  1 brcmsmac
cordic                 12535  1 brcmsmac

```$ lspci -nn | grep 0280 ```
02:00.0 Network controller [0280]: Broadcom Corporation BCM43225 802.11b/g/n [14e4:4357] (rev 01)
```I removed the STA driver so i could access channels 12 and 13

---

### Post by chili555 on 2012-06-07
I actually think the STA driver is correct; however, if it's working well with the exception of channels 12 and 13, then I guess brcmsmac is no better or worse than STA. 

If you have done this:> Also setting the /etc/default/crda to
Code:

REGDOMAIN=GB...and this:> You might try this:
```
sudo gedit /etc/modprobe.d/cfg80211.conf
```

Add one line:
```
options cfg80211 ieee80211_regdom=GB
```

Proofread, save and close gedit. Unload and reload brcmsmac:

```
sudo modprobe -r brcmsmac
sudo modprobe brcmsmac
```And you've checked the router for any available changes, then you've done all I know to do.

---

### Post by Fuxy on 2012-06-07
Yep done all that.

I'm actually considering trying to connect to my AP via terminal mabe i can get some clues.

Do you reckon i would have better luck installing b43 as far as i know it should support my card?

---

### Post by chili555 on 2012-06-07
> **Fuxy said:**
> Yep done all that.

I'm actually considering trying to connect to my AP via terminal mabe i can get some clues.

Do you reckon i would have better luck installing b43 as far as i know it should support my card?> Broadcom Corporation BCM43225 802.11b/g/n [[COLOR="Red"]14e4:4357[/COLOR]] (rev 01)The vendor and product ids are actually in b43's loyal sidekick, ssb. As you can see, 4357 isn't included:> chili@LAPTOP60:~$ modinfo ssb | grep 4357
chili@LAPTOP60:~$ So, no, b43 won't work.

With Network Manager running, it is doubtful you'll connect or even see any significant clues in the terminal. You might instead check here:```
sudo cat /var/log/syslog | grep -e etwork -e wl | tail -n25
```

---

### Post by Fuxy on 2012-06-07
That's wierd this [URL="http://linuxwireless.org/en/users/Drivers/b43#Supported_devices"]http://linuxwireless.org/en/users/Drivers/b43#Supported_devices
[/URL] seems to imply it is. Whats up with that?

---

### Post by chili555 on 2012-06-07
> **Fuxy said:**
> That's wierd this [URL="http://linuxwireless.org/en/users/Drivers/b43#Supported_devices"]http://linuxwireless.org/en/users/Drivers/b43#Supported_devices
[/URL] seems to imply it is. Whats up with that?I don't know for sure. I just read *modinfo* and report what I see. You can always try and report.

---

### Post by Fuxy on 2012-06-08
I did some more digging and did some research on brcmsmac and apparently it's a known problem.
Here's a thread on it: 
[http://www.gossamer-threads.com/lists/linux/kernel/1532375]("http://www.gossamer-threads.com/lists/linux/kernel/1532375") 
and a related blog post 
[http://133nux.blogspot.co.uk/2011/12/missing-channel-13-this-time-broadcom.html](http://133nux.blogspot.co.uk/2011/12/missing-channel-13-this-time-broadcom.html)

O please somebody tell me this is getting backported and punt into ubuntu.

---

### Post by andyhelloween on 2012-06-09
Amazing! I was trying to get my wife's laptop up and running for the past 3 hours... until I run into this thread! Ubuntu community is great!

So, I switched from channel 13 to channel 10 and wireless is up and running now! It's good wireless networks aren't many in my area!

Laptop is HP DV6-7032TX

lsmod | grep -e wl -e brcm
```

brcmsmac              570859  0 
mac80211              506816  1 brcmsmac
brcmutil               15139  1 brcmsmac
cfg80211              205544  2 brcmsmac,mac80211
crc8                   12893  1 brcmsmac
cordic                 12535  1 brcmsmac

```lspci -nn | grep 0280
```

0a:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)

```Cheers,
Andres.

---

### Post by eggsome on 2012-12-16
Same problem here in Australia with a BCM4314.
Looks like I'll have to go to my backup install of Ubuntu 10.10 - thank goodness for Clonezilla :)

Has this been reported as a bug on Launchpad so that the devs know that it is a problem?

---

### Post by praseodym on 2012-12-17
Thats a known bug with the Broadcom station driver. Try the native one:

```
sudo modprobe -rfv wl
sudo modprobe -v brcmsmac
```
Check:

```
iwconfig
iwlist chan
sudo iwlist scan
dmesg | grep brcm
```
You are sure with BCM 4314? Please check:

```
lspci -nnk | grep -iA2 net
```

---

### Post by eggsome on 2012-12-17
Here are the results of the commands you suggested.

```

ubuntu@ubuntu:~$ sudo modprobe -rfv wl
FATAL: Module wl not found.
ubuntu@ubuntu:~$ sudo modprobe -v brcmsmac
ubuntu@ubuntu:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.

ubuntu@ubuntu:~$ iwlist chan
lo        no frequency information.

wlan0     11 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
eth0      no frequency information.

ubuntu@ubuntu:~$ dmesg | grep brcm
[   87.859550] brcmsmac 0000:02:00.0: bus 2 slot 0 func 0 irq 10
[   87.859641] brcmsmac 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   87.859660] brcmsmac 0000:02:00.0: setting latency timer to 64
[   95.099833] ieee80211 phy0: brcms_ops_config: change monitor mode: false (implement)
[   95.099847] ieee80211 phy0: brcms_ops_config: change power-save mode: false (implement)
[   95.103150] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: false (implement)
ubuntu@ubuntu:~$ lspci -nnk | grep -iA2 net
01:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8132 Fast Ethernet [1969:1062] (rev c0)
    Subsystem: Acer Incorporated [ALI] Device [1025:0349]
    Kernel driver in use: atl1c
--
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
    Subsystem: Broadcom Corporation Device [14e4:0510]
    Kernel driver in use: brcmsmac
ubuntu@ubuntu:~$ 

```Do you have a link to this bug on launchpad so I can keep track of when it is resolved?

Thanks in advance,
Kirin.

---

### Post by praseodym on 2012-12-18
If you use the Broadcom-STA you need to blacklist the modules brcmsmac, bcma and brcm80211.

[https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/462466](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/462466)

---

### Post by chili555 on 2012-12-18
> **praseodym said:**
> If you use the Broadcom-STA you need to blacklist the modules brcmsmac, bcma and brcm80211.

[https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/462466](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/462466)The install process for bcmwl-kernel-source does that quite well.

---

### Post by Forceflow on 2013-02-27
Hi there. Spent ages debugging this. I recently changed my AP's channel to 13 (busy neighbourhood), and poof, it was gone from the iwlist scan.

I have the same Broadcom chip as the OP. (On a Dell Latitude E6430)

lspci -nn | grep 0280

```
jeroen@naboo:~$ lspci -nn | grep 0280
03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)

```

After a quick read-through of this thread, doing

sudo modprobe -rfv wl
sudo modprobe -v brcmsmac

seems to fix the issue, and I can connect to my AP. Problem is, after a while, the connection seems to bug out. I can surf for about 15-ish minutes.

What's the status of this bug?

---

### Post by Bergschreck on 2013-03-05
I'm running into the same problems. I have a very busy neighbourhood and try to find a free channel. Neither brcmsmac nor broadcom-sta-dkms can connect on channels 12 & 13.With the patch from this blog: [http://133nux.blogspot.de/2011/12/missing-channel-13-this-time-broadcom.htmlthe](http://133nux.blogspot.de/2011/12/missing-channel-13-this-time-broadcom.htmlthe) brcmsmac can connect on 12 & 13, but not on 14. Since wifi channels must have a distance of 4 channels from the neighbour channel (20 MHz), channel 13 has not enough distance from 11. So I would try to use 14, but it does not work.I'm giving up and ordered an AP with dual band (5 GHz), and now there seem to be more problems with drivers: the brcmsmac cannot operate in 5GHz band. The broadcam sta list channels from 5 GHz, but I don't know if they work. I can report on this when my AP arrives.

---

