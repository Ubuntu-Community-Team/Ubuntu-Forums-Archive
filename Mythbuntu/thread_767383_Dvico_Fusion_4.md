---
title: "Dvico Fusion 4"
date: 2008-04-25
forum: Mythbuntu
---

### Post by GuiGuy on 2008-04-25
Before I spend time on it, does anyone know if the Dvico Fusion 4 is supported? 

If it isn't supported, would you know if the [these instructions]("https://help.ubuntu.com/community/DViCO_Dual_Digital_4") carry over to 8.04?

TIA

---

### Post by wombo on 2008-04-27
Currently Version 1 cards do work with Linux.

Version 2 cards currently do not work as the card has been totally changed.

---

### Post by hawko on 2008-05-10
and apparently I have something in between as only one tuner works

---

### Post by nasha on 2008-05-10
Dvico fusion is supported, as the previous poster said, currently only version one cards... There is plenty of documentation around for the Dvico4 cards in this forum alone let alone the rest of the web

[HTML]http://www.mythtv.org/wiki/index.php/DViCO_FusionHDTV_DVB-T_Dual_Digital_Installation
http://ubuntuforums.org/showthread.php?t=616103[/HTML]

Should get you started...

---

### Post by GuiGuy on 2008-05-10
> **nasha said:**
> 

Should get you started...

No, it only ended in tears. I managed to get the card recognised once, but only on one tuner.  I've given up for now.

---

### Post by nasha on 2008-05-10
Check your usb connection? All installing the fusion should need is downloading and compiling the latest v4l-dvb drivers then installing 
[HTML]https://help.ubuntu.com/community/DViCO_Dual_Digital_4[/HTML]
You attempted to diagnose the problem...?
lsusb output?

---

### Post by GuiGuy on 2008-05-10
> **nasha said:**
> Check your usb connection? All installing the fusion should need is downloading and compiling the latest v4l-dvb drivers then installing 
[HTML]https://help.ubuntu.com/community/DViCO_Dual_Digital_4[/HTML]
You attempted to diagnose the problem...?
lsusb output?

NB: I followed the instructions at [https://help.ubuntu.com/community/DViCO_Dual_Digital_4](https://help.ubuntu.com/community/DViCO_Dual_Digital_4) to the letter. I have now done so on two different machines, using both i386 and AMD64 (my systems are the latter) distros. 

lsusb lists two DVICO devices after compiling and installing etc. 

The problem is on a reboot. The machine crashes with a message that it cannot start X due to an unknown internal error. The scope of trouble shooting that is beyond my knowledge & skills. 

Thanks

---

### Post by nasha on 2008-05-10
Rather strange i must say... However aiding you any further is also outside my scope of knowledge...
What video card you using? Tried another?
There's plenty of info on editing the xorg.conf file for different reasons in this forum from memory (been away for a month, so memory is a bit shady)

---

### Post by GuiGuy on 2008-05-10
> **nasha said:**
> 
What video card you using? Tried another?

Yea, that was the first thing I did. Nvidia 6100 (on MOBO), 6600GT. 7300GT, and a couple of ATIs (9550 Radeon I think). All gave the "unknown internal error"

I'm reasonably confident on editing xorg.conf, but I don't think that's it as even taking the graphics back to basics doesn't avoid the unknown internal error. In any case, I have tested on two different hardware platforms. 

My initial thoughts were that the DD4 was stuffed, but it works fine on Windows XP MCE. 

PS: I have two brandnew COMPRO Videomate 700 dual tuner cards sitting here. Shame MythTV doesn't do PCIe. :(

Cheers

---

### Post by hawko on 2008-05-10
GuiGuy....You are my brother in the face of adversity!! I have exactly the same problems that you are encountering. In the best of circumstances, I get one tuner working, in the worst, my computer wont reboot.

I am also using an AMD64 platform.  Had it working OK under 7.10 (still only one tuner) and the then current build of the v4l-dvb tree.  Last weekend I installed 8.04 and the horrors began.  Now I find the latest tree causes the crash.  So I rolled back to a version of the tree that I found (the test tree on Chris Pascoe's page).  This got one tuner working again but it was very slow to tune.

I thought that it might be the OS so rolled back to 7.10, latest tree crashed system on reboot. I have tried mainly 386 versions of Ubuntu, however, had same results with AMD64 versions.

Suspected card also, so tried in windows box.  Worked fine.  It was a 386 box though.  Going to try installing windows on my AMD64 mythbox and see how I go.

---

### Post by GuiGuy on 2008-05-10
> **hawko said:**
> 

Suspected card also, so tried in windows box.  Worked fine.  It was a 386 box though.  Going to try installing windows on my AMD64 mythbox and see how I go.

I have also tried the card on 7.10, with no joy. I really think this is one for someone who knows what they're doing. 

Be warned that there are major issues with the DD4 on Windows Vista. Two issues:

[LIST]
[*]Lots of stuttering/ slow channel changes
[*]second USB tuner auto disconnects intermittently.
[/LIST]

I had raised these issues with DVICO, who replied some time later:

> 
We recopmmend you to install the 3.363.01 driver in advance.
[ftp://ftp.dvico.com/Products/FusionHDTV/etc/USB3.63.01.zip](ftp://ftp.dvico.com/Products/FusionHDTV/etc/USB3.63.01.zip)
Sometimes gently clean the contact (golden fingers) by a rubber eraser can help as well.

If you still have the problem, please reply again.
Thanks.

Essentially, I think the card is a piece of junk. It was only when I read that others were (are?) running it successfully on MythTV that I got interested in it again. 

Oh well, I'll have to be satisfied with two tuners until someone gets the PCIe cards sorted out for MythTV. :?

Cheers

---

### Post by hawko on 2008-05-10
Have you tried your card on 386 equipment running MythTV? I am interested to see if it will work and if it is just related to the AMD64 machines.  I don't want to have to swap my server and Mythbox, but will if it will make things work.

---

### Post by GuiGuy on 2008-05-10
> **hawko said:**
> Have you tried your card on 386 equipment running MythTV? I am interested to see if it will work and if it is just related to the AMD64 machines.  I don't want to have to swap my server and Mythbox, but will if it will make things work.

Yes. Once on an Athlon 2200+. I get one tuner on that. I haven't been able to repeat whatever it was I did. 

BTW, what I have done is created several installation scenarios. Although, I only have AMD CPUs. 

I brought each up to date, configured it including the EPG, which is a PITA Downhere. 

Then I took an Acronis backup image of each before mucking around with the DD4. That allowed me a quick and easy restore strategy when things went pear shaped. 

I've stepped through the process and can conclude that the unknown internal error crash occurs on all boxes if I compile and install v4l-dvb AND when the firmware is installed. I don't know if that's relevant. 

 



Cheers

---

### Post by hawko on 2008-05-10
I have some news.  Not sure if it is good or bad though.  I just bit the bullet and installed XP on my Mythbox (AMD64) and I only get one tuner.  This suggests to me that it is a AMD problem with this particular card.  I have installed it previously on a 386 system and both tuners worked just fine.

So, I am SOL with my current Mythbox, maybe I will have to jiggle systems around to get a 386 chip in my Mythbox.  Where to from here?!?

---

### Post by nasha on 2008-05-11
Is it possible you are using Version 2 of the Dual Digital? This card currently has no support...

Hawko: You sure your connecting the internal USB cable correctly?

Ive had no issues ever with this card, and i use it in every system i build (10+ succesfull installs so far)
Why'd you'd bother installing it on vista, let alone even running vista puzzles me :P

---

### Post by GuiGuy on 2008-05-11
> **hawko said:**
> I have some news.  Not sure if it is good or bad though.  I just bit the bullet and installed XP on my Mythbox (AMD64) and I only get one tuner.  This suggests to me that it is a AMD problem with this particular card.  I have installed it previously on a 386 system and both tuners worked just fine.

So, I am SOL with my current Mythbox, maybe I will have to jiggle systems around to get a 386 chip in my Mythbox.  Where to from here?!?


Did you do a clean install of the USB driver recommended by DVICO:

[ftp://ftp.dvico.com/Products/FusionHDTV/etc/USB3.63.01.zip](ftp://ftp.dvico.com/Products/FusionHDTV/etc/USB3.63.01.zip)

Cheers

---

### Post by GuiGuy on 2008-05-11
> **nasha said:**
> Is it possible you are using Version 2 of the Dual Digital? 

OK, you mean the original PCI/ USB card that required a cable for the second USB tuner!!

By Revision 1.0, I understood it to be the card identified on the back of the GREEN circuit board as "FUSION DVB-T Dual Digital 4 Rev. 1.0" - this card does not have a USB cable. Both USB tuners are supposed to be managed through the PCI. This is the card I have. 

I thought, and understood, [Revision 2 to be the new black circuit board card]("http://www.fusionhdtv.co.kr/ENG/Products/DVBTdual4.aspx")?

Maybe I better get it clear what the MythTV world means by DD4 Revision 1.0 before we go trouble shooting. 

 Thanks

---

### Post by hawko on 2008-05-11
> **nasha said:**
> Is it possible you are using Version 2 of the Dual Digital? This card currently has no support...

Hawko: You sure your connecting the internal USB cable correctly?


Not version 2.  Ver 1 of the Dual Digital 4.  As GuiGuy says below, there is no internal cable.  I think you are talking about the DD2 - wish I could have found one of those.


> **GuiGuy said:**
> Did you do a clean install of the USB driver recommended by DVICO:


Negative.  Didn't know it existed.  I am reinstalling Mythbuntu now. Would you believe that I tried it in the original windows computer that it worked on and now it isn't working!! The world is against me.  I don't know what is going on

> **GuiGuy said:**
> OK, you mean the original PCI/ USB card that required a cable for the second USB tuner!!

By Revision 1.0, I understood it to be the card identified on the back of the GREEN circuit board as "FUSION DVB-T Dual Digital 4 Rev. 1.0" - this card does not have a USB cable. Both USB tuners are supposed to be managed through the PCI. This is the card I have. 

I thought, and understood, [Revision 2 to be the new black circuit board card]("http://www.fusionhdtv.co.kr/ENG/Products/DVBTdual4.aspx")?

Maybe I better get it clear what the MythTV world means by DD4 Revision 1.0 before we go trouble shooting. 

 Thanks

I concur with that.  Do GuiGuy and I have some crappy ver 1.5 of the board?

---

### Post by nasha on 2008-05-11
Every dual digital 4 ive ever used has an internal usb cable... Id almost say that all dual tuners do, at least the ones that i know of....

With the exception on the Dual Digital 4 Ver. 2, thats the difference, and also the main reason why it isnt running under linux yet

> To use this card your PC must have one free PCI slot and one free USB 2.0 port. The USB port is needed for the second tuner, which does not run off the PCI bus. Only one antenna connection is needed though.

[HTML]http://www.pcworld.idg.com.au/index.php/id;204682295;fp;16;fpid;0[/HTML]
 Anybody done their research? Or read the manual?

---

### Post by GuiGuy on 2008-05-11
> **nasha said:**
> Every dual digital 4 ive ever used has an internal usb cable... Id almost say that all dual tuners do, at least the ones that i know of....

Definitely not on the card I have. Clearly marked as I wrote previously. Only connectors are for power switching . 


[ftp://ftp.dvico.com/Manual/FusionHDTV/FusionHDTV_Manual_English.pdf](ftp://ftp.dvico.com/Manual/FusionHDTV/FusionHDTV_Manual_English.pdf)

The DD4 hardware instructions are on page 14. As you'll see, no USB. I suspect you are referring to the earlier DD2 card, which does have a separate USB cable. 

EDIT: So it seems the Linux world calls the DD2 card the DD4 Revision one. Maybe a more accurate description would be VERSION 1, so as not not confuse it with the card's circuit board labeling.




regards

---

### Post by nasha on 2008-05-11
When i can be bothered i will scan one of my DD4 manuals. Im looking at the box right now, clearly says DD4

---

### Post by hawse1978 on 2008-05-12
I also have this rev 1 dual digital 4 card. The back of the board is printed with: 

> Fusion DVB-T Dual Digital 4
Rev:1.0
http:\\dvico.com
 (yes, the slashes are printed the wrong way around!)

My card has a number of pins on it... none of which were used when I had the card working perfectly previously in XP. In fact, no additional cables came with the card.

**With** the card plugged in to the PCI slot, lsusb returns nothing at all. It just hangs and can't be killed by Ctrl-C or Ctrl-Z etc. The [X] button closes the terminal, but the lsusb process is still running. Can't even be killed by kill -9

**Without** the card plugged in, lsusb returns a bunch of results for other usb devices.

other commands i've seen used for troubleshooting:
> michal@MyDesktop:~$ lsmod|grep dvb
dvb_usb_cxusb          27577  1 
dvb_usb                22924  1 dvb_usb_cxusb
dvb_core               80508  1 dvb_usb
i2c_core               24832  3 tuner_xc2028,zl10353,dvb_usb
usbcore               146028  8 dvb_usb_cxusb,dvb_usb,rtl8187,usbhid,ehci_hcd,uhci_hcd


> michal@MyDesktop:~$ dmesg|grep usb|grep dvb
[   63.254651] dvb-usb: found a 'DViCO FusionHDTV DVB-T Dual Digital 4' in warm state.
[   63.254746] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   63.530568] Modules linked in: tuner_xc2028 zl10353 dvb_usb_cxusb dvb_usb dvb_core i2c_core psmouse serio_raw arc4 pcspkr ecb blkcipher iTCO_wdt iTCO_vendor_support rtl8187 mac80211 evdev cfg80211 eeprom_93cx6 snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_page_alloc snd_hwdep fglrx(P) snd_seq_dummy sky2 snd_seq_oss snd_seq_midi agpgart snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device button snd i82975x_edac soundcore edac_core shpchp pci_hotplug ext3 jbd mbcache sg sr_mod sd_mod cdrom ata_piix pata_acpi usbhid hid floppy ata_generic libata scsi_mod ohci1394 ieee1394 ehci_hcd uhci_hcd usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
[   63.530669]  [<f8b681f2>] cxusb_dvico_xc3028_tuner_attach+0x52/0xc0 [dvb_usb_cxusb]
[   63.530677]  [<f8b68f00>] dvico_bluebird_xc2028_callback+0x0/0xb0 [dvb_usb_cxusb]
[   63.530684]  [<f8b62003>] dvb_usb_adapter_frontend_init+0x73/0x100 [dvb_usb]
[   63.530691]  [<f8b618bf>] dvb_usb_device_init+0x39f/0x620 [dvb_usb]
[   63.530702]  [<f8b68135>] cxusb_probe+0xe5/0x150 [dvb_usb_cxusb]
[   63.530789]  [<f8a01018>] cxusb_module_init+0x18/0x35 [dvb_usb_cxusb]


So Ubuntu (8.04, btw) clearly recognises the card and knows what it is, but still struggles to query it (or whatever) with lsusb.

I ran through the steps in this article: [https://help.ubuntu.com/community/DViCO_Dual_Digital_4]("https://help.ubuntu.com/community/DViCO_Dual_Digital_4") to the letter without a hitch.

I'm guessing this is an lsusb issue, but when the tv card is connected, my external USB drives are inaccessible as well.  

Any suggestions?!
Mike

---

