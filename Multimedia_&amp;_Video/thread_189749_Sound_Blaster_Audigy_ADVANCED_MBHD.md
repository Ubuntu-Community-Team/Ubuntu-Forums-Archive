---
title: "Sound Blaster Audigy ADVANCED MB/HD"
date: 2006-06-05
forum: Multimedia &amp; Video
---

### Post by MarioFuentes on 2006-06-05
Hi

I buy a new laptop (Dell Inspiron 640m) with an optional sound card "Sound Blaster Audigy ADVANCED HD", and install Ubuntu Dapper on this. The sound works fine, but with the "snd-hda-intel" module.  The pre-installed Windows have the Creative Tools for the sound card, but in my Ubuntu  lspci say "Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)" and I have a confusion, the "snd-hda-intel" uses the intel integrated sound or the sound blaster audigy? any body know if this laptop have two sound cards? or the Audigy integrated have a intel chip?

thanks.

---

### Post by lazyron on 2006-07-02
I'm curioius about this as well. Here's the output from lspci:

0000:00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 03)
0000:00:02.0 VGA compatible controller: Intel Corporation Mobile Integrated Graphics Controller (rev 03)
0000:00:02.1 Display controller: Intel Corporation Mobile Integrated Graphics Controller (rev 03)
0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
0000:00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
0000:00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
0000:00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
0000:00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
0000:00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
0000:00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
0000:00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
0000:00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
0000:00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
0000:00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controllers cc=IDE (rev 01)
0000:00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
0000:02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
0000:02:01.0 FireWire (IEEE 1394): Ricoh Co Ltd: Unknown device 0832
0000:02:01.1 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
0000:02:01.2 System peripheral: Ricoh Co Ltd: Unknown device 0843 (rev 01)
0000:02:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
0000:02:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0000:0c:00.0 Network controller: Intel Corporation: Unknown device 4222 (rev 02)

I'd guess I'm expecting something that says, "I'm a SB audio device" instead of an Intel listing in there.

---

### Post by Aldoo on 2006-07-04
Hi !
I just ordered an Inspiron 640m too !
Does it work well with Dapper ?

To answer your question, the 640m does not have a Sound Blaster but a Sigmatel chipset. In the spec list on Dell's site, they talk about SB audigy, but in fact it is only the SB software for windows (so that you have the nice features of a SB when under windows). 
I agree Dell's site is quite confusing.

---

### Post by lazyron on 2006-07-08
> **Aldoo said:**
> Hi !
I just ordered an Inspiron 640m too !
Does it work well with Dapper ?


For the most part my e1405 has done fairly well. I had to apply the 915resolution fix [https://help.ubuntu.com/community/i915Driver](https://help.ubuntu.com/community/i915Driver)

and the fix posted here: [http://www.ubuntuforums.org/showthread.php?t=201657](http://www.ubuntuforums.org/showthread.php?t=201657)
to get the headphone/speaker situation sorted.

a couple of other tweaks, but nothing unexpected or insumountable :)

> **Aldoo said:**
> 
To answer your question, the 640m does not have a Sound Blaster but a Sigmatel chipset. In the spec list on Dell's site, they talk about SB audigy, but in fact it is only the SB software for windows (so that you have the nice features of a SB when under windows). 
I agree Dell's site is quite confusing.

Ugh. I wish I hadn't known that. Ah well, still a decent laptop.

---

### Post by colgate on 2006-07-22
Hi,
I'm intrested in this laptop, too!
Does supend to ram and suspend to disk (hibernate) workd?
it's really important!

thanks!

Federico

---

### Post by Aldoo on 2006-08-26
> **colgate said:**
> Hi,
I'm intrested in this laptop, too!
Does supend to ram and suspend to disk (hibernate) workd?
it's really important!

thanks!

Federico
For me suspend to ram or to disk does not work (well suspend to disk sometimes does). But some people report it to work...

So I don't know. It would be a good thing to have a working howto for the ACPI support on those machines.

---

### Post by zPCz on 2006-08-31
Hi!
Well, suspend to disk works for me. But Card Reader does not.

Anybody has a working card reader on inspiron 640m?

---

### Post by AlCaLoIdE on 2006-09-15
Ok about the Sound Blaster Audigy ADVANCED MB/HD

I bought a Dell XPSM1210 From dell and i ask to have Sound Blaster Audigy ADVANCED MB. 

But you no what this sound card is not a creative, this song card is a Sigmatel, I verified my self the chipset.

So I call DELL about this and they make a change on the USwebsite,[www.dell.com](www.dell.com) now if you go verify on the web side about this sound card Sound Blaster Audigy ADVANCED MB you will se Software Edition.But they foget to make the change on the canadien webside [www.dell.ca](www.dell.ca)So i sugest you to make a screen short if you whant to do some thing.

Yea the think you have buy for is the software of Sound Blaster Audigy ADVANCED MB, Is only the program that’s it, 
And this program is for windows only.

But the Sigmatel chipset is Intel HI Definition audio.

I fund this information on this audio card.

The Dell™ XPS™ M1210 comes with an audio solution that is a major upgrade from the existing AC '97 standard. The Intel® High Definition (HD) Audio technology is also known by the code name Azalia. The actual audio chipset on the system is the SigmaTel® STAC9200.

Intel HD audio not only provides an enriched playback experience but is intended to deliver a better quality input for voice and communication applications. The higher quality audio is possible in part to an upgraded architecture and increased bandwidth that allows for 192 kHz, 32-bit, multichannel audio and support for evolving high-quality audio formats. Other improvements include increased support for multichannel array microphones for higher quality input, dynamically allocated bandwidth, and flexible audio device configuration.

Features 
Here are some of the features of Intel's HD audio technology: 
Delivers higher quality audio experience 

Improve accuracy of speech input, improved speech recognition 
Telephony (VoIP, or voice over IP), conferencing and IM (instant messaging) applications 
Higher sample rate and more bits per sample 
Enables lower power operation 
CPU can be in C3 state with audio activity 
Designed for dynamic CE quality audio 
DVD-Audio and Super Audio CD (SACD) 
96 KHz, 24-bit audio support 
Dynamic jack configuration
 
The sound will work on linux but not the microphone so if you no how to code this well you cant fix it your self and make a post for the people.
 
So if you have this sound card well forget to use skype or other program cause the microphone DONT Work on linux for now.

I try with alsa driver sound work but no microphone. I try with OSS driver and same thing sound work but no microphone.

Some people post to alsa community about this bug,[https://bugtrack.alsa-project.org/alsa-bug/view_all_bug_page.php](https://bugtrack.alsa-project.org/alsa-bug/view_all_bug_page.php) but no one having fix it yet, so I will make a post my self and will see what is gone append after this.

I wish I reply to your entire question about this sound card.
Enjoy
AlCaLoIdE

---

### Post by sceon on 2007-01-08
woops

---

### Post by mccurry on 2007-10-05
the OSS works for the onboard mic only at least for me, I am using a M1210.

---

