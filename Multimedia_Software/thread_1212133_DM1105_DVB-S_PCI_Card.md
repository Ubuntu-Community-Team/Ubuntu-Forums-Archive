---
title: "DM1105 DVB-S PCI Card"
date: 2009-07-13
forum: Multimedia Software
---

### Post by scrauny on 2009-07-13
Hi everyone,

I wondered if anyone can help me resolve / debug this issue? Thanks in advance! :)

I have been trying (at length!) to get a DVB-S PCI card working with Ubuntu.

It's one of these cards -> [COLOR="Blue"][link]("http://cgi.ebay.co.uk/DVB-S-Satellite-TV-Tuner-Video-Capture-PCI-Card-Remote_W0QQitemZ130314645048QQcmdZViewItemQQptZUK_Computing_Computer_Components_Graphics_Video_TV_Cards_TW?hash=item1e575bae38&_trksid=p3286.c0.m14&_trkparms=65:12|66:2|39:1|72:1690|293:1|294:50")[/COLOR]

It appears to have the DM1105 chipset, and lspci tells me the following:
```
03:09.0 Ethernet controller: Device 195d:1105 (rev 10)
```

I read that this would be supported in kernel 2.2.26, but in Jaunty (kernel 2.2.28 ) this card isn't recognised.

Ideally I would like it to integrate with my MythTV setup :)

Anyone got any ideas on this? Has anyone ever managed to configure one of these cards in Ubuntu successfully?

I've tried the Igor driver (found via Google) but it does nothing with this card. In any case, this should be in the kernel now.

Looking forward to some ideas!
Thanks
Shaun

---

### Post by scrauny on 2009-07-13
Hi again,

So - I've got a little further! :)

I built the latest v4l-dvb drivers and now the DVB-S PCI card is recognised by Ubuntu:

```
[   12.334998] dm1105 0000:03:09.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.335174] DVB: registering new adapter (dm1105)
[   12.585230] dm1105 0000:03:09.0: MAC ffff88007e4c0378

[   12.960572] DVB: registering adapter 0 frontend 0 (ST STV0299 DVB-S)...
```

Even if it does still think it's an Ethernet Controller :D
```
03:09.0 Ethernet controller: Device 195d:1105 (rev 10)
```

The problem I am having now is that I cannot get any channels any way I try to tune the card. Using Kaffeine I get ~95% Signal and 75% SNR, but it never finds any channels. I am using the most up-to-date everything (I apt-get upgrade almost daily). I am in the South of the UK and am trying to tune against Eurobird1-28.5E and Astra-28.2E - think this is OK.

I'm in a flat with a shared dish, if that makes any difference. A normal Sky box works fine, and if I get a good signal/snr in Kaffeine I guess it's something to do with the DVB card not getting a lock (driver issue?)?

Has anyone had this problem, or can help debugging it?

Thanks a load!! :)
Shaun

---

### Post by scrauny on 2009-07-15
Can anyone help on this? Please? I have reached a sticking point!

Thanks in advance! :)

If it helps, here's what [FONT="Courier New"]scan[/FONT] gives me:

```
sudo scan /usr/share/dvb/dvb-s/Astra-28.2E
scanning /usr/share/dvb/dvb-s/Astra-28.2E
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
......
>>> tune to: 11720:h:0:29500
DVB-S IF freq is 1120000
WARNING: >>> tuning failed!!!
>>> tune to: 11720:h:0:29500 (tuning failed)
DVB-S IF freq is 1120000
WARNING: >>> tuning failed!!!
```

The "[FONT="Courier New"]tuning failed[/FONT]" occurs over and over again, for every config file I try.

---

### Post by scrauny on 2009-07-21
BUMP!

Anyone?

Thanks!

---

### Post by magog45 on 2009-07-21
You say you have a shared dish, is it possible there is some kind of switch that isn't being recognized? I usually use and old DVB settop box to test connections and do an initial blind scan, if you can find one it may be worth it. At least you will know you are good to your end of the cable.

---

### Post by scrauny on 2009-07-22
Hi magog45,

Thanks for replying. It is possible that there is something special about the way Sky setup "Sky Shared Dish". I have tested with a Sky set-top box which detects the satellite, locks and displays channels fine - so I know the cable is OK. You can get to the tuning and LNB details on the Sky box, and I've tried using the same details for scan/dvbscan/Myth/etc, but I can never get it to lock.

So it seems that it is something to do with the Linux setup. Possibly a driver issue? (Even though there are no dmesg errors, looks OK..)

Thanks!
Shaun

---

### Post by scrauny on 2009-07-22
Here's the output from dvbtune, if it helps - can see that there is signal(?), but it can't lock. The settings are known good for a Sky set-top box:

```
$ sudo dvbtune -f 1177800 -s 27500 -p v -m -tone 1 -vvvvvvvvvvv
[sudo] password for shaun:
Using DVB card "ST STV0299 DVB-S"
tuning DVB-S to L-Band:0, Pol:V Srate=27500000, 22kHz=on
polling....
Getting frontend event
FE_STATUS:
polling....
Getting frontend event
FE_STATUS: FE_HAS_SIGNAL FE_HAS_CARRIER FE_HAS_VITERBI
polling....
Getting frontend event
FE_STATUS: FE_HAS_SIGNAL FE_HAS_CARRIER
polling....
Getting frontend event
FE_STATUS: FE_HAS_SIGNAL FE_HAS_CARRIER FE_HAS_VITERBI
polling....
Getting frontend event
FE_STATUS: FE_HAS_SIGNAL FE_HAS_CARRIER
polling....
Getting frontend event
FE_STATUS: FE_HAS_SIGNAL FE_HAS_CARRIER FE_HAS_VITERBI
polling....
Getting frontend event
FE_STATUS: FE_HAS_SIGNAL FE_HAS_CARRIER

```

Thanks!

---

### Post by scrauny on 2009-07-22
Few more traces, hopefully they all help :)
Scan gives:

```
>>> tune to: 11778:v:0:27500
DiSEqC: switch pos 0, 13V, hiband (index 2)
diseqc_send_msg:56: DiSEqC: e0 10 38 f1 00 00
DVB-S IF freq is 1178000
>>> tuning status == 0x03
>>> tuning status == 0x03
>>> tuning status == 0x03
>>> tuning status == 0x03
>>> tuning status == 0x03
>>> tuning status == 0x03
>>> tuning status == 0x03
>>> tuning status == 0x03
>>> tuning status == 0x03
>>> tuning status == 0x03
WARNING: >>> tuning failed!!!
>>> tune to: 11778:v:0:27500 (tuning failed)
```

Do the codes 0x03 mean anything to anyone?

I also occassionally get 0x07

---

### Post by xc3RnbFO8P on 2009-07-22
Did you check if the driver is loaded
> dmesg | grep DVB

---

### Post by scrauny on 2009-07-22
Hi,

Thanks for the reply - I did check, it seems to be loaded fine:

```
$ dmesg | grep DVB
[   12.188299] DVB: registering new adapter (dm1105)
[   12.767799] DVB: registering adapter 0 frontend 28025312 (ST STV0299 DVB-S)...
[   12.767935] input: DVB on-card IR receiver as /devices/pci0000:00/0000:00:1e.0/0000:03:09.0/input/input5
```

In Kaffeine I get 98% signal and 78% SNR. Just no lock.

I've tried both Astra and Eurobird 28 frequencies (/usr/share/dvb/dvb-s/). Also tried the frequencies the Sky box was using. Still no lock. Please see above for scan traces.

Thanks,
Shaun

---

### Post by xc3RnbFO8P on 2009-07-22
Something is wrong here, 
before:
> [   12.960572] DVB: registering adapter 0 frontend 0 (ST STV0299 DVB-S)
and now:
> [   12.767799] DVB: registering adapter 0 frontend **28025312** (ST STV0299 DVB-S)

---

### Post by xc3RnbFO8P on 2009-07-22
Read this:
[http://www.linuxtv.org/pipermail/linux-dvb/2009-January/031243.html]("http://www.linuxtv.org/pipermail/linux-dvb/2009-January/031243.html")

---

### Post by scrauny on 2009-07-22
Must have done something weird when testing - rebooted and it's the correct frontend being used:

```
$ dmesg | grep DVB
[   11.990944] DVB: registering new adapter (dm1105)
[   12.604442] DVB: registering adapter 0 frontend 0 (ST STV0299 DVB-S)...
[   12.604572] input: DVB on-card IR receiver as /devices/pci0000:00/0000:00:1e.0/0000:03:09.0/input/input5
```

The same still stands though - I can't lock despite having a good signal - Please see previous traces.

Thanks!

---

### Post by scrauny on 2009-07-22
> **Ringi said:**
> Read this:
[http://www.linuxtv.org/pipermail/linux-dvb/2009-January/031243.html]("http://www.linuxtv.org/pipermail/linux-dvb/2009-January/031243.html")

Thanks - OK, I'll try that repository. I am currently using the latest v4l-dvb checkout. I did try the liplianin one before without success, but perhaps it is updated - will try again and let you know. Unless you know that the latest v4l-dvb uses the same code?

---

### Post by scrauny on 2009-07-22
Hi,

I've moved to the liplianin drivers now, and the card is recognised - but I still can't lock a frequency:

```
$ dmesg | grep DVB
[   12.174738] DVB: registering new adapter (dm1105)
[   12.839501] DVB: registering adapter 0 frontend 0 (ST STV0299 DVB-S)...
[   12.839633] input: DVB on-card IR receiver as /devices/pci0000:00/0000:00:1e.0/0000:03:09.0/input/input5
```

&

```
$ sudo scan -vvvvvv /usr/share/dvb/dvb-s/Astra-28.2E
scanning /usr/share/dvb/dvb-s/Astra-28.2E
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'

>>> tune to: 11778:v:0:27500
DiSEqC: switch pos 0, 13V, hiband (index 2)
diseqc_send_msg:56: DiSEqC: e0 10 38 f1 00 00
DVB-S IF freq is 1178000
>>> tuning status == 0x03
>>> tuning status == 0x03
>>> tuning status == 0x03
>>> tuning status == 0x03
>>> tuning status == 0x03
>>> tuning status == 0x03
>>> tuning status == 0x03
>>> tuning status == 0x03
>>> tuning status == 0x03
>>> tuning status == 0x03
WARNING: >>> tuning failed!!!
```

I'm definitely using the new driver:
```
$ ls -altrh /lib/modules/2.6.28-13-server/kernel/drivers/media/dvb/dm1105/dm1105.ko
-rw-r--r-- 1 root root 34K 2009-07-22 11:44 /lib/modules/2.6.28-13-server/kernel/drivers/media/dvb/dm1105/dm1105.ko
```

Modinfo gives:
```
$ modinfo dm1105
filename:       /lib/modules/2.6.28-13-server/kernel/drivers/media/dvb/dm1105/dm1105.ko
license:        GPL
description:    SDMC DM1105 DVB driver
author:         Igor M. Liplianin <liplianin@me.by>
srcversion:     46C1B3C3627D1937F75D732
alias:          pci:v0000195Dd00001105sv*sd*bc*sc*i*
alias:          pci:v0000109Fd0000036Fsv*sd*bc*sc*i*
depends:        ir-common,dvb-core
vermagic:       2.6.28-13-server SMP mod_unload modversions
parm:           card:card type (array of int)
parm:           ir_debug:enable debugging information for IR decoding (int)
parm:           adapter_nr:DVB adapter numbers (array of short)

```


Any further ideas why I can't tune?

---

### Post by xc3RnbFO8P on 2009-07-22
Did you read this:
[http://ubuntuforums.org/archive/index.php/t-914766.html]("http://ubuntuforums.org/archive/index.php/t-914766.html")

---

### Post by scrauny on 2009-07-22
> **Ringi said:**
> Did you read this:
[http://ubuntuforums.org/archive/index.php/t-914766.html]("http://ubuntuforums.org/archive/index.php/t-914766.html")

Yeah, that's not the same problem. He can get the channels.conf from scan (so scan is working). I can't get that far :(

---

### Post by jamri11b on 2009-11-13
> **scrauny said:**
> Hi again,

So - I've got a little further! :)

I built the latest v4l-dvb drivers and now the DVB-S PCI card is recognised by Ubuntu:

```
[   12.334998] dm1105 0000:03:09.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.335174] DVB: registering new adapter (dm1105)
[   12.585230] dm1105 0000:03:09.0: MAC ffff88007e4c0378

[   12.960572] DVB: registering adapter 0 frontend 0 (ST STV0299 DVB-S)...
```Even if it does still think it's an Ethernet Controller :D
```
03:09.0 Ethernet controller: Device 195d:1105 (rev 10)
```The problem I am having now is that I cannot get any channels any way I try to tune the card. Using Kaffeine I get ~95% Signal and 75% SNR, but it never finds any channels. I am using the most up-to-date everything (I apt-get upgrade almost daily). I am in the South of the UK and am trying to tune against Eurobird1-28.5E and Astra-28.2E - think this is OK.

I'm in a flat with a shared dish, if that makes any difference. A normal Sky box works fine, and if I get a good signal/snr in Kaffeine I guess it's something to do with the DVB card not getting a lock (driver issue?)?

Has anyone had this problem, or can help debugging it?

Thanks a load!! :)
Shaun


Can you please tell the steps for loading V4L I failed to get the frontend correctly plugged.

Thanks,
jamri11b

---

### Post by scrauny on 2009-11-13
Hi,

I used the following how-to to install the drivers:

[http://www.linuxtv.org/repo/]("http://www.linuxtv.org/repo/")

However I was never able to get the card to tune, even using known good settings (I put the card into a Windows box and it tuned fine).

If you have any luck, I'd be interested to know!

Thanks,
Shaun

---

### Post by jamri11b on 2010-07-12
[SIZE=3][COLOR=Black]Hi,
I've got the same dvb dm1105 but I could not even get it to be recognised by ubuntu 10.04.

dmesg printout is as follow.[/COLOR][/SIZE]

[SIZE=2][COLOR=Navy]root@jamri11c:/home/jamri11c# dmesg | grep dm1105
[    8.894381] dm1105: Your board isn't known (yet) to the driver.
[    8.894382] dm1105: You can try to pick one of the existing
[    8.894383] dm1105: card configs via card=<n> insmod option.
[    8.894384] dm1105: Updating to the latest version might help
[    8.894385] dm1105: as well.
[    8.894596] dm1105:    card=0 -> UNKNOWN/GENERIC
[    8.894632] dm1105:    card=1 -> DVBWorld PCI 2002
[    8.894663] dm1105:    card=2 -> DVBWorld PCI 2004
[    8.894695] dm1105:    card=3 -> Axess/EasyTv DM05
[    8.894742] dm1105 0000:03:00.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    8.895008] DVB: registering new adapter (dm1105)
[    8.914870] dm1105 0000:03:00.0: MAC 00:00:00:00:00:00
[   11.636168] dm1105 0000:03:00.0: could not attach frontend
[   11.636628] dm1105 0000:03:00.0: PCI INT A disabled[/COLOR][/SIZE]

[SIZE=3][COLOR=Black]when I tried to  built the latest v4l-dvb drivers it is worst "unknown symbol" is presented in dmesg with 4 lines only none talks about the above statments.

My card is working fine with WINXP.

Can anyone help me or give me a hint, I am a newbie.[/COLOR][/SIZE]

jamri11c

---

### Post by armyofgayunicorns on 2011-01-12
Hi, I've also got one of these cards based on the DM1105 chipset which came from China. It's a PCI DVB-S card, I've got it working on my XP partition receiving all the free to air channels, but I've got absolutely nowhere getting Ubuntu to recognise it as a tuner card, I'm also getting it showing up as a network adaptor. I'm using Ubuntu 10.10.

If anyone would take the time to either post a step by step howto or a link to one explaining what I need to do to install the driver I'd massively appreciate it, I'm not a complete linux n00b so I'm not intimidated by using the command line terminal, this is just the first problem I've had with Ubuntu that I haven't found a working solution for with Google. Thanks.

---

