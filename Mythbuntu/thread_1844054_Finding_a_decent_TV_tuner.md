---
title: "Finding a decent TV tuner"
date: 2011-09-14
forum: Mythbuntu
---

### Post by the_dark_light on 2011-09-14
Greetings all,

Firstly I'd like to say I'm glad I discovered Mythbuntu and am looking forward to getting this software up and running.

I'm in the process of replacing an HTPC running Windows 7 (running the default Windows Media Center software) with Mythbuntu.  When I originally specced out the machine I purchased a BlackGold TV card, and later a Hauppage HVR-2200, as Linux compatibility was not an issue at the time (stupid me!)

Since looking in to Mythbuntu I've found that TV tuners are not as well supported in Linux as other devices are.

From my research I've found that there is support for the HVR-2200 through the latest version of hg.  So far I have not had much luck getting the card running on my test machine, to rule out problems with the card (which I am thinking of replacing) can anyone who has this card let me know if they have been able to set it up?

Also, if anyone has got the HVR-2200 running was it:
1)  Analogue or DVB?
2)  Running with single or dual tuners?

I seem to be having better luck with an old Freecom DVB-T USB stick which I'd like to use in the final installation as worst case scenario I could pair it with another compatible tuner or ideally pair it with the HVR-2200 and ideally get 3 tuners in total.  The Freecom was relatively painless to set up as I was able to use "Additional Drivers" to grab the driver and have been able to view live TV with it.

If anyone has any recommendations for tuners that are relatively simple to set up I'd be very grateful to hear suggestions.  (Please note that a limitation is that PCI/PCI-E cards must be half hight sue to the case I'm using)

Finally, is it a good idea to use the over the air EPG or to use an online service?  When I tried pulling up the channel guide/EPG when using the over the air listings through the Freecom the interface seemed to get stuck on the loading listings popup.  (I could not clear the popup, but the live TV was still showing in the corner and I was viewing it through VNC so the machine can't have crashed)

I'm hoping that using mythbuntu can solve the reliability headaches I've had with Win7 and the remote management (SSH/VNC) will certainly make my life easier!

---

### Post by klc5555 on 2011-09-14
The HVR 2200 has supposedly been fully supported Analog and DVB in  Linux since 2009.

Linuxtv's standard wiki page for the card is here: [http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-2200](http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-2200)

You may already have the necessary drivers and firmware installed. Checking the output from commands like "lspci" and  "dmesg | grep saa7164" and comparing the output to what the wiki shows for sample output should give an indication about whether your machine has found and identified the card at power-up, whether it's loaded the saa7164 driver, and whether it's loaded the required firmware for the card. Missing firmware will need to be supplied; a too old or a missing saa7164 driver will need need to be compiled and installed as indicated in the wiki.

Among the older generation of PCI cards, a half-height one that designed specifically for Linux and works (usually) out-of-the-box is the pchdtv-hd5500. Analog and digital, but unfortunately only one input port (which causes problems if you need a cable or satellite box output fed to an analog input, but you have digital coming in via clear QAM or DVBT).

Once it's running, your PVR is only as useful as the scheduling data it receives. Therefore, in the US SchedulesDirect is worth every penny of the (now) $25 annually they charge.

---

### Post by the_dark_light on 2011-09-14
Many thanks for the information.  I ran dmesg on a fresh install on my test box and got the following output.

The output is:

```
dan@mythbuntu-test:~$ dmesg | grep saa7164
[   10.880642] saa7164 driver loaded
[   10.880902] saa7164 0000:02:00.0: PCI INT A -> Link[APC4] -> GSI 19 (level, low) -> IRQ 19
[   10.880909] saa7164[0]: Your board isn't known (yet) to the driver.
[   10.880910] saa7164[0]: Try to pick one of the existing card configs via
[   10.880912] saa7164[0]: card=<n> insmod option.  Updating to the latest
[   10.880913] saa7164[0]: version might help as well.
[   10.880917] saa7164[0]: Here are valid choices for the card=<n> insmod option:
[   10.880920] saa7164[0]:    card=0 -> Unknown
[   10.880923] saa7164[0]:    card=1 -> Generic Rev2
[   10.880925] saa7164[0]:    card=2 -> Generic Rev3
[   10.880928] saa7164[0]:    card=3 -> Hauppauge WinTV-HVR2250
[   10.880931] saa7164[0]:    card=4 -> Hauppauge WinTV-HVR2200
[   10.880933] saa7164[0]:    card=5 -> Hauppauge WinTV-HVR2200
[   10.880936] saa7164[0]:    card=6 -> Hauppauge WinTV-HVR2200
[   10.880939] saa7164[0]:    card=7 -> Hauppauge WinTV-HVR2250
[   10.880941] saa7164[0]:    card=8 -> Hauppauge WinTV-HVR2250
[   10.881788] CORE saa7164[0]: subsystem: 0070:8940, board: Unknown [card=0,autodetected]
[   10.881795] saa7164[0]/0: found at 0000:02:00.0, rev: 129, irq: 19, latency: 0, mmio: 0xd5000000
[   10.881802] saa7164 0000:02:00.0: setting latency timer to 64
[   10.881828] saa7164_initdev() Unsupported board detected, registering without firmware
dan@mythbuntu-test:~$ 

```

Looks like time for an update.

Update:

According to lspci -v

```
02:00.0 Multimedia controller: Philips Semiconductors SAA7164 (rev 81)
	Subsystem: Hauppauge computer works Inc. WinTV HVR-2200 (submodel 89619)
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at d5000000 (64-bit, non-prefetchable) [size=4M]
	Memory at d5400000 (64-bit, non-prefetchable) [size=4M]
	Capabilities: <access denied>
	Kernel driver in use: saa7164
	Kernel modules: saa7164

```

---

### Post by the_dark_light on 2011-09-14
Seem to have some progress.  Created a file:
/etc/modprobe.d/saa7164.conf

with the contents:
options saa7164 card=4

and downloaded a copy of the NXP firmware file by stephen toth.  Dmesg now gives the more promising:

```
dan@mythbuntu-test:~$ dmesg | grep 7164
[    0.181364] pci 0000:02:00.0: [1131:7164] type 0 class 0x000480
[   20.768068] saa7164 driver loaded
[   20.772009] saa7164 0000:02:00.0: PCI INT A -> Link[APC4] -> GSI 19 (level, low) -> IRQ 19
[   20.772760] CORE saa7164[0]: subsystem: 0070:8940, board: Hauppauge WinTV-HVR2200 [card=4,insmod option]
[   20.772766] saa7164[0]/0: found at 0000:02:00.0, rev: 129, irq: 19, latency: 0, mmio: 0xd5000000
[   20.772773] saa7164 0000:02:00.0: setting latency timer to 64
[   20.970101] saa7164_downloadfirmware() no first image
[   20.970171] saa7164_downloadfirmware() Waiting for firmware upload (NXP7164-2010-03-10.1.fw)
[   21.596048] saa7164_downloadfirmware() firmware read 4019072 bytes.
[   21.596053] saa7164_downloadfirmware() firmware loaded.
[   21.596065] saa7164_downloadfirmware() SecBootLoader.FileSize = 4019072
[   21.596071] saa7164_downloadfirmware() FirmwareSize = 0x1fd6
[   21.596073] saa7164_downloadfirmware() BSLSize = 0x0
[   21.596075] saa7164_downloadfirmware() Reserved = 0x0
[   21.596077] saa7164_downloadfirmware() Version = 0x1661c00
[   28.830019] saa7164_downloadimage() Image downloaded, booting...
[   28.940021] saa7164_downloadimage() Image booted successfully.
[   31.280017] saa7164_downloadimage() Image downloaded, booting...
[   32.710023] saa7164_downloadimage() Image booted successfully.
[   32.760434] tveeprom 2-0000: audio processor is SAA7164 (idx 43)
[   32.760437] tveeprom 2-0000: decoder processor is SAA7164 (idx 40)
[   32.760442] saa7164[0]: Hauppauge eeprom: model=89619
[   33.235484] DVB: registering new adapter (saa7164)
[   36.248566] DVB: registering new adapter (saa7164)
[   36.249807] saa7164[0]: registered device video0 [mpeg]
[   36.482532] saa7164[0]: registered device video1 [mpeg]
[   36.694012] saa7164[0]: registered device vbi0 [vbi]
[   36.694130] saa7164[0]: registered device vbi1 [vbi]

```

I would test it out with the mythtv backend config but I've just noticed my screen is full of garbage.  I guess it's just one of those days :(

UPDATE:

After performing an update I'm able to get GUI access.  The card is being picked up in mythtv-setup as a DVB device.  Once I move it to my main antenna location I'll see if I can get any channels.  Looks like progress is being made :-)

---

### Post by klc5555 on 2011-09-15
Well, hopefully you'll find your card working after one of the 3 modprobe possibilities the original dmesg output returned for you.

You didn't specify which version of Ubuntu you were using. But a quick check over at linuxtv.org showed that there has been quite a bit of work going with regards to to the saa7164 driver, much of it between about Sept 2010 and March 2011. This would not have made it into Ubuntu 10.04 or 10.10, but most of it is likely to have made it into 11.04. If you installed 10.04 LTS or 10.10 and found that the driver is not quite doing it for you, you may do better compiling and installing it from current source. If however you installed 11.04, it would appear that your saa7164 is essentially up to date.

Of course, if after configuring the saa7164 it works fine, then leave it alone, whatever version it is. :)

---

### Post by the_dark_light on 2011-09-15
The version I'm using is 11.04 (AMD64)

I'm performing a scan now and unfortunately can't seem to find any channels.  Still, progress anyway

---

### Post by LowSky on 2011-09-15
The 2250 is the same card. I wrote this tutorial a bit ago:

[http://ubuntuforums.org/showpost.php?p=11205874&postcount=425](http://ubuntuforums.org/showpost.php?p=11205874&postcount=425)

---

### Post by tumutanzi on 2011-09-15
In my case, i just use Sopcast or online site to watch TV, and i do not watch TV so often.

---

### Post by the_dark_light on 2011-09-17
The card is up and running, just a matter of downloading the appropriate firmware (NXP is not included in the firmware package) and setting the driver options (card=4 for the 2200)

Thanks for the help :)

---

