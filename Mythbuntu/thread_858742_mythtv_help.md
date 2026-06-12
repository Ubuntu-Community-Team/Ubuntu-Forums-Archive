---
title: "mythtv help"
date: 2008-07-13
forum: Mythbuntu
---

### Post by fishbulb1022 on 2008-07-13
I can't get Mythtv to work. I ran all the setup stuff and it seeemed like it was going to work this time (i've tried in the past with no luck) but when i tried to watch live tv an error message came up saying the current channel had used all available inputs, and that if i wanted to watch live tv, i needed to delete some previous recordings. When i tried to do that, it said I had used 0% of my available space, but that my available space was 0.0 gigabytes. I tired to change the amount of space mythtv could use in the setup, but when i tried to watch again, i had the same error message come up, and going again to the recordings thing it said i had 0 gigs. Any help is appreciated. Also, i'm really new to Ubuntu, so the more simplistic the solution is and the more you are willing to explain, the better. thanks for any help!

I tried to install a newer version, the one in the add/remove hardware database doesn't seem to be the newest, and i couldn't get it to install, so i tried to go back and now it can't find the master backend (which should be this computer). I triied to check the IP address where it said in but i couldn't find anywhere to change it in the setup menu i thought it was directing me to...so now i need help with that as well. again, any help is appreciated, i really have no clue how to get this to work.

---

### Post by foxbuntu on 2008-07-14
There are 3 places the IP address should be set, however the default settings on the install should work for a Master Backend/Frontend install. 

Have you Setup [Storage Groups]("http://www.mythtv.org/wiki/index.php/Storage_Groups")?

---

### Post by DutchLoki on 2008-07-15
Hi Fishbulb,

I'have to say you don't give us much to work with. some questions about your problem: 

I'm wondering if you followed the MyhtBuntu installation guide? (from [www.mythbuntu.com](www.mythbuntu.com)) If so from which step did it went wrong? 

Did you use the latest version of the MythBuntu installation cd for your reinstall? Version 8.04? 

You installed a combined frontend/backend on the same system (which is fine, but important to know).

What hardware do you use? 

Do you have anything else connected to your computer besides a mouse, keyboard and monitor? If so, remove it and add it again after installation. 

Could you add some logfiles?

---

### Post by fishbulb1022 on 2008-07-19
ok, i think i found the problem, but i still can't fix it. Sorry, i probably sound like a complete idiot, but anyway, I checked the synaptic package manager and found out this computer wasn't set up as a master backend, so i installed that. Then i started checking the set-up. It found my card (an ATI tv wonder) but, when i tried to scan for channels, it said it "failed to open card." I would assume this would be the reason i can't watch tv. If anyone has any tips on how to get past this, they would be much appreciated.

---

### Post by fishbulb1022 on 2008-07-19
> **DutchLoki said:**
> Hi Fishbulb,

I'have to say you don't give us much to work with. some questions about your problem: 

I'm wondering if you followed the MyhtBuntu installation guide? (from [www.mythbuntu.com](www.mythbuntu.com)) If so from which step did it went wrong? 

Did you use the latest version of the MythBuntu installation cd for your reinstall? Version 8.04? 

You installed a combined frontend/backend on the same system (which is fine, but important to know).

What hardware do you use? 

Do you have anything else connected to your computer besides a mouse, keyboard and monitor? If so, remove it and add it again after installation. 

Could you add some logfiles?

ok, well, i'm not using mythbuntu, just ubuntu, i posted this first in the regular thread area and someone asked me to re-post it here. I'm using version 7.10.

yes, its a combined frontend/backend. 

by hardware i would assume you mean what kind of tv card, and that would be an ATI tv Wonder.

As far as logfiles go, i think i mentioned i'm completely new to ubuntu, but either way, i have no idea what those are or how to post them, sorry. I'd have no problem posting them if you explained how to do it though. thanks.

---

### Post by jb5 on 2008-07-20
Log files are usually stored in the  /var/log directory
I'm not at my Myth machine at the moment, but if you open a terminal...
```

cd /var/log
cat syslog > ~/Desktop/syslog.file

```

This will put a copy of your syslog on your home desktop.

Some other files you would probably want copies of are your frontend and backend logs, also look in the mythtv directory to see if there is anything in there that might prove useful to others. Also,
```
dmesg > ~/Desktop/dmesg.file
```
Someone may well want to refine or add to the specific logs you should post, but hopefully this will at least get you started.

To post the files, open the file in a text editor and copy the text. Paste that into your reply here. Enclose the text with code tags, the #
button in the toolbar above should do that for you.

HTH (at least a little) :)

---

### Post by fishbulb1022 on 2008-07-20
not sure it this is exactly what you want, but its what i could find...

```
[   58.906645] Linux video capture interface: v2.00
[   58.994753] input: ImExPS/2 Logitech Explorer Mouse as /class/input/input3
[   59.536710] bttv: driver version 0.9.17 loaded
[   59.536714] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   59.536797] bttv: Bt8xx card found (0).
[   59.536819] ACPI: PCI Interrupt 0000:02:02.0[A] -> GSI 22 (level, low) -> IRQ 22
[   59.536831] bttv0: Bt878 (rev 17) at 0000:02:02.0, irq: 22, latency: 32, mmio: 0xdfbff000
[   59.536847] bttv0: detected: ATI TV Wonder/VE [card=64], PCI subsystem ID is 1002:0003
[   59.536850] bttv0: using: ATI TV-Wonder VE [card=64,autodetected]
[   59.536878] bttv0: gpio: en=00000000, out=00000000 in=00ffffff [init]
[   59.537246] bttv0: using tuner=19
[   59.537250] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[   59.688217] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   59.688862] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[   59.846472] tuner 0-0060: All bytes are equal. It is not a TEA5767
[   59.846476] tuner 0-0060: chip found @ 0xc0 (bt878 #0 [sw])
[   59.846508] tuner 0-0060: type set to 19 (Temic PAL* auto (4006 FN5))
[   59.846512] tuner 0-0060: type set to 19 (Temic PAL* auto (4006 FN5))
[   59.901731] pnp: Device 00:0a activated.
[   59.921039] bttv0: registered device video0
[   59.921090] bttv0: registered device vbi0
[   59.921113] bttv0: PLL: 28636363 => 35468950 .. ok
[   59.951565] ACPI: PCI Interrupt 0000:02:01.0[A] -> GSI 21 (level, low) -> IRQ 21
[   59.988163] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 23
[   59.988185] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   60.028082] bt878: AUDIO driver version 0.0.0 loaded
[   60.310558] intel8x0_measure_ac97_clock: measured 52806 usecs
[   60.310561] intel8x0: clocking to 48000
[   60.311622] bt878: Bt878 AUDIO function found (0).
[   60.311643] ACPI: PCI Interrupt 0000:02:02.1[A] -> GSI 22 (level, low) -> IRQ 22
[   60.311651] bt878_probe: card id=[0x31002], Unknown card.
[   60.311652] Exiting..
[   60.311657] ACPI: PCI interrupt for device 0000:02:02.1 disabled
[   60.311662] bt878: probe of 0000:02:02.1 failed with error -22
[   60.611436] lp: driver loaded but no devices found
[   60.691202] Adding 3028212k swap on /dev/sda5.  Priority:-1 extents:1 across:3028212k
```

if this isn't what you needed, or if you need more, let me know and tell me how to get it, thanks again!

---

