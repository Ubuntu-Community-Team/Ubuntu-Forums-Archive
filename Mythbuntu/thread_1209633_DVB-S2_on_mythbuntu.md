---
title: "DVB-S2 on mythbuntu"
date: 2009-07-10
forum: Mythbuntu
---

### Post by vincent orange on 2009-07-10
Hi,

I'm trying get my TeVii S470 DVB-S2 PCIe Satellite Card working on ubuntu 9.04 AMD 64 with the MythTv package installed.

I live in the UK and I have a Sky Digital Dish outside my home. I think that it is pointing at 28.2 and/or 28.5 either Astra 2 or Eurobird 1.

Luckily the card comes with Linux drivers from the manufacturers website [www.tevii.com](www.tevii.com) I've followed the instructions to install that and I need to use Kaffeine to scan for channels. I think I'm half way there as Kaffeine scans and finds signal strength 19.2Eto be 56%. But it doesn't find any channels at all.

I've read a lot of about Transponder files but I don't understand what I need to edit/do/fix to have that working.

I need some kind of walk through to help me. I've done as much as I can on my own but I would like some help to get me further.

edit: I've tried to scan in MythTV interface however, there are lots of options and variables so I don't know if they're correct to be set at default. Also it does attempt a scan but doesn't move off 0%.

---

### Post by utar on 2009-07-10
I use the Tevii s650 USB box with Myth, which I assume is the USB version of your card.

In the first instance I would check that the card is initialised.  Type "dmesg | grep dvb" into a terminal and post the output.

I'm guessing that you may not have set up a LNB in myth (look under DiSEqC settings in the card settings).

I forget if I actually needed a transponder file or not. Try the above first and see what happens.


Utar

---

### Post by vincent orange on 2009-07-10
dmesg | grep dvb shows the following
```
[    7.689476] cx23885_dvb_register() allocating 1 frontend(s)
[    7.689480] cx23885[0]: cx23885 based dvb card
```

I have installed the linux drivers as given on TeVii's website.

I setup the card in myth. I setup LNB too. I tried to scan for channels using "scan for channels and exsiting transports" and "scan for channels (tuned)" both of which provide "parameter error" and "transport error".

I don't understand what the problem is.

---

### Post by utar on 2009-07-10
> **vincent orange said:**
> dmesg | grep dvb shows the following



I have installed the linux drivers as given on TeVii's website.

I setup the card in myth. I setup LNB too. I tried to scan for channels using "scan for channels and exsiting transports" and "scan for channels (tuned)" both of which provide "parameter error" and "transport error".

I don't understand what the problem is.

I'm not sure if the card is set up properly.  The output from that command on my system gives:

```
[   10.195959] dvb-usb: found a 'TeVii S650 USB2.0' in cold state, will try to load a firmware
[   10.195962] firmware: requesting dvb-usb-dw2104.fw
[   10.514990] dvb-usb: downloading firmware from file 'dvb-usb-dw2104.fw'
[   10.640057] dvb-usb: found a 'TeVii S650 USB2.0' in warm state.
[   10.640092] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   10.640120] dvb-usb: MAC address reading failed.
[   11.020716] dvb-usb: no frontend was attached by 'TeVii S650 USB2.0'
[   11.048104] dvb-usb: schedule remote query interval to 150 msecs.
[   11.048109] dvb-usb: TeVii S650 USB2.0 successfully initialized and connected.
[   11.050468] dvb-usb: TeVii S650 USB2.0 successfully deinitialized and disconnected.
[   11.176396] dvb-usb: found a 'Hauppauge Nova-T 500 Dual DVB-T' in cold state, will try to load a firmware
[   11.176399] firmware: requesting dvb-usb-dib0700-1.20.fw
[   11.220064] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.20.fw'
[   11.924059] dvb-usb: found a 'Hauppauge Nova-T 500 Dual DVB-T' in warm state.
[   11.924105] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   12.425115] dvb-usb: found a 'TeVii S650 USB2.0' in cold state, will try to load a firmware
[   12.425117] firmware: requesting dvb-usb-dw2104.fw
[   12.426202] dvb-usb: downloading firmware from file 'dvb-usb-dw2104.fw'
[   12.548024] dvb-usb: found a 'TeVii S650 USB2.0' in warm state.
[   12.548072] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   12.562737] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   12.739330] dvb-usb: MAC address: f7c3178c
[   12.776089] dvb-usb: schedule remote query interval to 150 msecs.
[   12.776093] dvb-usb: TeVii S650 USB2.0 successfully initialized and connected.
[   13.140079] dvb-usb: schedule remote query interval to 50 msecs.
[   13.140082] dvb-usb: Hauppauge Nova-T 500 Dual DVB-T successfully initialized and connected.
[   13.140221] usbcore: registered new interface driver dvb_usb_dib0700
[   30.240160] cx24116_firmware_ondemand: Waiting for firmware upload (dvb-fe-cx24116.fw)...
[   30.240166] firmware: requesting dvb-fe-cx24116.fw

```

Your output makes me think that the card is not working.

To get my card to work I just installed the latest V4L-DVB device drivers (which have support for the Tevii).  You may want to check the following page:

[http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers](http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers)


Utar

---

### Post by utar on 2009-07-10
You may want to (before trying the above) download the Astra transponder file from:

[http://joshyfun.260mb.com/transponders/kaffeine.html](http://joshyfun.260mb.com/transponders/kaffeine.html)

I think you need to rename the file channels.conf then import it into myth before doing a scan.


Utar

---

### Post by vincent orange on 2009-07-10
I went to V4L-DVB device drivers  and installed the drivers as instructed on the website. I still get errors for dmesg | grep dvb as follows

```
[    8.900528] cx23885_dvb_register() allocating 1 frontend(s)
[    8.900532] cx23885[0]: cx23885 based dvb card
[    8.979773] cx23885_dvb_register() dvb_register failed err = -1
[    8.979775] cx23885_dev_setup() Failed to register dvb adapters on VID_B

```

should i do this process again?

also I tried to use kaffeine again and sadly it doesn't detect the DVB card anymore. But when it did I was able to scan and it would happily scan for 20 minutes but no channels would show up.

It seems I need to really hit this on the head for it to work. I areally appreciate your help utar

---

### Post by utar on 2009-07-10
I think that this is a driver problem, rather then a software one.  I'm not a linux expert by any means so I'm not sure what to suggest.  Hopefully someone who know more will be able to help out.

Sorry I can't help any more.



Utar

---

### Post by vincent orange on 2009-07-11
> **utar said:**
> I think that this is a driver problem, rather then a software one.  I'm not a linux expert by any means so I'm not sure what to suggest.  Hopefully someone who know more will be able to help out.

Sorry I can't help any more.



Utar

In any case Utar I appreciate the help, narrowing the problem down means we can try to solve it.

I've also dual booted with Mythbuntu but i get the same output for dmesg | grep dvb....again, it enforces the idea that it's a driver issue.

---

### Post by utar on 2009-07-11
You could always email Tevii directly.  I emailed them when I was looking to buy the S650 and they were very helpful.

You may also want to try installing the drivers on Tevii's website again.  Last time you tried did they look to install properly or were there any error messages?

Can you also try typing "dmesg | grep TeVii" in a terminla just on the chance that this gives a slughtly different output.



Utar

---

### Post by vincent orange on 2009-07-11
> **utar said:**
> You could always email Tevii directly.

I will try that now and I'll follow their advice. I bet there is a really simple fix but my cluelessness is adding to the problems.

I've got Kaffeine working again although I tried scanning with the custom channels.conf and nothing comes up.

> **utar said:**
> Can you also try typing "dmesg | grep TeVii"
```

[    9.749998] CORE cx23885[0]: subsystem: d470:9022, board: TeVii S470 [card=15,autodetected]
```

i will update my progress.

---

### Post by vincent orange on 2009-07-12
I red on another thread 

[http://ubuntuforums.org/showpost.php?p=4652724&postcount=5](http://ubuntuforums.org/showpost.php?p=4652724&postcount=5)

that I can use the default v4l-dvb in ubuntu/mythbuntu rather than using the mecurial packages. I will try that and report back.

---

### Post by Neon Dusk on 2009-07-12
Is the firmware getting loaded?

What does 'dmesg | grep firmware' return?

---

### Post by vincent orange on 2009-07-12
> **Neon Dusk said:**
> Is the firmware getting loaded?
What does 'dmesg | grep firmware' return?

terminal command dmeg | grep firmware does not respond.....silly thing acting up.

I looked at the logs manually through the admin panel...I get something interesting..

```
[   10.203015] cx23885 driver version 0.0.1 loaded
[   10.203063] cx23885 0000:02:00.0: PCI INT A -> Link[AE0A] -> GSI 16 (level, low) -> IRQ 16
[   10.203066] cx23885[0]: Your board isn't known (yet) to the driver.
[   10.203067] cx23885[0]: Try to pick one of the existing card configs via
[   10.203067] cx23885[0]: card=<n> insmod option.  Updating to the latest
[   10.203068] cx23885[0]: version might help as well.
[   10.203069] cx23885[0]: Here is a list of valid choices for the card=<n> insmod option:
[   10.203071] cx23885[0]:    card=0 -> UNKNOWN/GENERIC
[   10.203072] cx23885[0]:    card=1 -> Hauppauge WinTV-HVR1800lp
[   10.203073] cx23885[0]:    card=2 -> Hauppauge WinTV-HVR1800
[   10.203075] cx23885[0]:    card=3 -> Hauppauge WinTV-HVR1250
[   10.203076] cx23885[0]:    card=4 -> DViCO FusionHDTV5 Express
[   10.203077] cx23885[0]:    card=5 -> Hauppauge WinTV-HVR1500Q
[   10.203078] cx23885[0]:    card=6 -> Hauppauge WinTV-HVR1500
[   10.203079] cx23885[0]:    card=7 -> Hauppauge WinTV-HVR1200
[   10.203081] cx23885[0]:    card=8 -> Hauppauge WinTV-HVR1700
[   10.203082] cx23885[0]:    card=9 -> Hauppauge WinTV-HVR1400
[   10.203083] cx23885[0]:    card=10 -> DViCO FusionHDTV7 Dual Express
[   10.203084] cx23885[0]:    card=11 -> DViCO FusionHDTV DVB-T Dual Express
[   10.203086] cx23885[0]:    card=12 -> Leadtek Winfast PxDVR3200 H
```

possible to use "card="n"" option during v4l driver build?

if so this is the card list [http://enpc3240.eas.asu.edu/lxr/linux/http/source/Documentation/video4linux/bttv/CARDLIST](http://enpc3240.eas.asu.edu/lxr/linux/http/source/Documentation/video4linux/bttv/CARDLIST) my card isn't listed yet.

and reference to insmod arguments for good measure [http://enpc3240.eas.asu.edu/lxr/linux/http/source/Documentation/video4linux/bttv/Insmod-options](http://enpc3240.eas.asu.edu/lxr/linux/http/source/Documentation/video4linux/bttv/Insmod-options)

anyone have experience in this?

---

### Post by Neon Dusk on 2009-07-12
That's the cardlist for the bttv module. Your card uses the cx23885 module

You had the card detected in your [previous post](http://ubuntuforums.org/showpost.php?p=7598935&postcount=10). As this is a new card support isn't built in yet so you'll need to use a newer v4l-dvb (as you did previously)

---

### Post by vincent orange on 2009-07-13
Thanks for your help Neon Dusk.

I've updated the v4l-dvb drivers by using:

```
hg pull -u http://linuxtv.org/hg/v4l-dvb

hg update

```

output shows there are not updates to be had. Then I did

```
make rminstall
```

To remove to current driver set and then built the v4l-dvb driver set again. The card still isn't detected dmesg | grep cx23885 shows:

```
[    9.669707] cx23885 driver version 0.0.1 loaded
[    9.669772] cx23885 0000:02:00.0: PCI INT A -> Link[AE0A] -> GSI 16 (level, low) -> IRQ 16
[    9.669775] cx23885[0]: Your board isn't known (yet) to the driver.
[    9.669776] cx23885[0]: Try to pick one of the existing card configs via
[    9.669776] cx23885[0]: card=<n> insmod option.  Updating to the latest
[    9.669777] cx23885[0]: version might help as well.
[    9.669778] cx23885[0]: Here is a list of valid choices for the card=<n> insmod option:
[    9.669780] cx23885[0]:    card=0 -> UNKNOWN/GENERIC
[    9.669781] cx23885[0]:    card=1 -> Hauppauge WinTV-HVR1800lp
[    9.669782] cx23885[0]:    card=2 -> Hauppauge WinTV-HVR1800
[    9.669783] cx23885[0]:    card=3 -> Hauppauge WinTV-HVR1250
[    9.669785] cx23885[0]:    card=4 -> DViCO FusionHDTV5 Express
[    9.669786] cx23885[0]:    card=5 -> Hauppauge WinTV-HVR1500Q
[    9.669787] cx23885[0]:    card=6 -> Hauppauge WinTV-HVR1500
[    9.669788] cx23885[0]:    card=7 -> Hauppauge WinTV-HVR1200
[    9.669789] cx23885[0]:    card=8 -> Hauppauge WinTV-HVR1700
[    9.669791] cx23885[0]:    card=9 -> Hauppauge WinTV-HVR1400
[    9.669792] cx23885[0]:    card=10 -> DViCO FusionHDTV7 Dual Express
[    9.669793] cx23885[0]:    card=11 -> DViCO FusionHDTV DVB-T Dual Express
[    9.669794] cx23885[0]:    card=12 -> Leadtek Winfast PxDVR3200 H
[    9.669897] CORE cx23885[0]: subsystem: d470:9022, board: UNKNOWN/GENERIC [card=0,autodetected]
[    9.795730] cx23885_dev_checkrevision() Hardware revision = 0xb0
[    9.795737] cx23885[0]/0: found at 0000:02:00.0, rev: 2, irq: 16, latency: 0, mmio: 0xfd200000
[    9.795742] cx23885 0000:02:00.0: setting latency timer to 64
```

I've just learned something new..dmesg | grep firmware/dvb/TeVii didn't show an output because there wasn't anything in tht logs...never had that happen to me before, lol.

The card list for my module cx23885 is found here [http://www.mjmwired.net/kernel/Documentation/video4linux/CARDLIST.cx23885#16](http://www.mjmwired.net/kernel/Documentation/video4linux/CARDLIST.cx23885#16) it's listed as > 15 -> TeVii S470                                          [d470:9022]
 but on the same page it shows "based on kernel 2.6.30"....however, uname -r tells me I have "2.6.28-13-generic"...should I update my Kernel or does this effect my drivers?

---

### Post by utar on 2009-07-13
Think that means that the card is supported out of the box on kernel 2.6.30 (as this is built including later v4l drivers then are shipped with Ubuntu).  I really wouldn't try and update the kernel as everything is likely to break.

However compiling the latest v4l-dvb drivers, as you have done, should add support for the card and I'm confused why it doesn't seem to be working.

I assume you ran "make" using sudo?

You could try using the insmod command to manually load the driver as  your output suggests.  Perhaps "sudo insmod cx23885 card=0" may work?  See [http://linux.about.com/od/commands/l/blcmdl8_insmod.htm](http://linux.about.com/od/commands/l/blcmdl8_insmod.htm) for the manual.

[Edit: actually looking at the output a second times makes me think your kernel has already set the card type to 0.]

[Edit 2: what does "dmesg | grep cx24116" show.  As I note from [http://www.linuxtv.org/wiki/index.php/TeVii_S470](http://www.linuxtv.org/wiki/index.php/TeVii_S470) the card has both chips.]



Utar

---

### Post by vincent orange on 2009-07-13
> **utar said:**
> 
what does "dmesg | grep cx24116" show.Utar

doesn't show anything.

I didn't run make in sudo....but i did run make install in sudo. will try again and report back

edit: Removed the drivers and ran everything again as sudo. but still nothing dmesg | grep dvb shows:

> [    9.927145] cx23885_dvb_register() allocating 1 frontend(s)
[    9.927149] cx23885[0]: cx23885 based dvb card
[    9.960752] cx23885_dvb_register() dvb_register failed err = -1
[    9.960754] cx23885_dev_setup() Failed to register dvb adapters on VID_B

---

### Post by utar on 2009-07-13
It may be helpful if you could post the entire output from dmesg.

"dmesg > dmesg.txt" should work.


Utar

---

### Post by vincent orange on 2009-07-13
I've attached tried to attached it here but it's too big...

..so, it's available here [http://pastebay.com/29128](http://pastebay.com/29128)

edit: in the v4l INSTALL file it seems that insmod has to be used during sudo make install, not sure if this is correct.

The system that i'm using is fresh i'm happy to try out kernel 2.6.30 and if it breaks then i'll reinstall mythbuntu. I'll wait a few days before i do that.

---

### Post by utar on 2009-07-13
Well the interesting lines are the following:

```

#
[    9.754598] cx23885 driver version 0.0.2 loaded
#
[    9.754653] cx23885 0000:02:00.0: PCI INT A -> Link[AE0A] -> GSI 16 (level, low) -> IRQ 16
#
[    9.754740] CORE cx23885[0]: subsystem: d470:9022, board: TeVii S470 [card=15,autodetected]
#
[    9.880593] cx23885_dvb_register() allocating 1 frontend(s)
#
[    9.880596] cx23885[0]: cx23885 based dvb card
#
[    9.918036] Invalid probe, probably not a CX24116 device
#
[    9.918088] cx23885[0]: frontend initialization failed
#
[    9.918091] cx23885_dvb_register() dvb_register failed err = -1
#
[    9.918093] cx23885_dev_setup() Failed to register dvb adapters on VID_B
#
[    9.918096] cx23885_dev_checkrevision() Hardware revision = 0xb0
#
[    9.918102] cx23885[0]/0: found at 0000:02:00.0, rev: 2, irq: 16, latency: 0, mmio: 0xfd200000
#
[    9.918108] cx23885 0000:02:00.0: setting latency timer to 64
```

This time the card has been correctly recognised as card number 15 unlike your last post.  What did you change?

I have the same CX24116 error line in my dmesg, but the cx24116 does initialise later.  What does look strange is that there is no firmware upload for the card.

Looks like you are getting closer, just not sure what else to suggest.

[Edit: Was the card set up in mythbackend and was myth loaded before you did dmesg?  Just wondering if when software calls the card this starts the firmware upload]


Utar

---

### Post by vincent orange on 2009-07-13
the only thing i changed was that i ran "make" as sudo. nothing else.

---

### Post by utar on 2009-07-13
> **vincent orange said:**
> the only thing i changed was that i ran "make" as sudo. nothing else.

Well you are getting closer.  See my edit on my last post.


Utar

---

### Post by vincent orange on 2009-07-13
> **utar said:**
> [Edit: Was the card set up in mythbackend and was myth loaded before you did dmesg?  Just wondering if when software calls the card this starts the firmware upload]Utar

myth was loaded before i ran dmesg. this is the case for each session as it auto starts. i haven't run myth-setup yet to configure the card in mythTV.

I'm getting closer to this being fixed but no cigar moment yet though.

TeVii have got back to me but want me to try out their MyTeVii software.

---

### Post by utar on 2009-07-13
Can you go into mythbackend setup, configure the card, quit setup and see if anything interesting appears in dmesg.


Utar

---

### Post by vincent orange on 2009-07-13
i've setup the card in mythTV here is the new dmesg [http://pastebay.com/29142](http://pastebay.com/29142)

mythbackend also says it "failed to open card".

---

### Post by utar on 2009-07-13
I note that the DVBWorld DVB-S2 card has different install instructions from the usual V4L driver ones:

[http://www.linuxtv.org/wiki/index.php/DVBWorld_DVB-S2_2005_PCI-Express_Card](http://www.linuxtv.org/wiki/index.php/DVBWorld_DVB-S2_2005_PCI-Express_Card)

Given that this uses the same chips (and drivers from what I can tell) as the Tevii S470 you could give these a try.

Other then that I'm not sure what to suggest.



Utar

---

### Post by vincent orange on 2009-07-14
for a laugh I installed Win 7 RC. I now have a triple boot system to see where the faults are and how to fix them. The win driveres that came with it are rubbish, so is the TV software on disc. I used the M$ drivers and the thing picked up 400 channels and is working as I type this. I'm using Windows Media Center. Even the HD Channels in England are picked up. So I can confirm that the card works along with all the other pieces in the chain.

I'll continue trying the linux setup...it's either that or fork out another £100 on vista/win7...ouchie!!

---

### Post by utar on 2009-07-15
Well at least you know the card isn't broken.

To be frank there is a argument that it's worth paying for a commercial product because you know it will just work and it saves hours of messing around.  I'm not saying that to be critical of Linux as it's free and I personally love Myth and spending time learning about a new OS.

Let me know how you get on.


Utar

---

### Post by vincent orange on 2009-07-16
lol, I'm familiar with that particular argument, it's almost legendary. 

Fact is I've not bought a windows machine or software for 14 years. I  feel a little guilty if i did buy windows, kinda feel like I'm selling out.

WMC does "just work", but there is little if any tinkering that can be done with/to it. For MthTV there are plugins upon plugins that I would love to compile and use - MythVodka caught my eye.

I'll get on mythbuntu tonight and see what progress I can make.

---

### Post by vincent orange on 2009-07-20
I guess this is the final update.

I've tried all options available and the situation is still the same.

Because of my reluctance to buy windows I've decided to use win7 RC until 1st Jun 2010 when it expires and then try again on ubuntu. By then I'm hoping that an upgraded kernel and stable 2.3.60-XXX build will mean an easier installation and running of the S470 card.

I thank everyone for their help and perhaps open this thread again in 10 months time. 

Thanks :)

---

### Post by zaurus on 2009-07-25
It seems to me that the only problem you have is that the firmware is not loaded for your card. I had a similar problem with my Hauppage HVR-4000.
But after several trying it was fixed. I would suggest give it a new try on a fresh kernel. Install via synaptic 2.6.28-12-generic for example boot in it, stop your mythtv-backend and follow the instructions coming with your Linux driver. Do not forget sudo for each command you type.

KR

---

### Post by macjones on 2010-02-11
What I did to get rid of the failed in dmesg

from dmesg ... (dvb_register() dvb_register failed err = -1)

**My card is s470 pci-e**


*#did all the mythbuntu updates (9.10 for me)*
# uname -ar

Linux grant-mythtv 2.6.31-19-generic #56-Ubuntu SMP Thu Jan 28 01:26:53 UTC 2010 i686 GNU/Linux

*get root and stop mythtv backend*

sudo su 
# /etc/init.d/mythbackend stop

*installed rar*
apt-get install rar
*installed other stuff*
apt-get install mercurial linux-headers-$(uname -r) build-essential
*(mercurial may not be needed)*



*downloaded the tevii s470 drivers from..*

*[http://www.tevii.com/100205_linux_tevii_ds3000.rar](http://www.tevii.com/100205_linux_tevii_ds3000.rar)*

*followed their README*

*(from readme...)*
# cp *.fw /lib/firmware
# tar xjvf linux-tevii-ds3000.tar.bz2
# cd linux-tevii-ds3000
# make && make install

*#did all this as root user*

reboot

dmesg | grep cx

[    9.247651] cx23885 driver version 0.0.2 loaded
[    9.247699] cx23885 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    9.247767] CORE cx23885[0]: subsystem: d470:9022, board: TeVii S470 [card=15,autodetected]
[    9.373943] cx23885_dvb_register() allocating 1 frontend(s)
[    9.374666] cx23885[0]: cx23885 based dvb card
[    9.768907] DVB: registering new adapter (cx23885[0])
[    9.769283] cx23885_dev_checkrevision() Hardware revision = 0xb0
[    9.769295] cx23885[0]/0: found at 0000:01:00.0, rev: 2, irq: 16, latency: 0, mmio: 0xfe800000
[    9.769305] cx23885 0000:01:00.0: setting latency timer to 64
[    9.769312] IRQ 16/cx23885[0]: IRQF_DISABLED is not guaranteed on shared IRQs

looks good !!

---

### Post by jetro007 on 2010-09-26
I had the same problems, but i downloaded the driver from the Tevii site (it's a beta now), copied the firmware and did a make/make install from linux-tevii-ds3000 (make takes a long time)

It worked directly!

Does anyone use the infrared reciever? since I've heard it giver errors

---

### Post by joko66 on 2010-11-27
After updating the kernel the driver wasn't loaded. Solved by

[LIST]
[*]make distclean
[*]make
[*]make install
[/LIST]

---

