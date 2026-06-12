---
title: "No sound playback Emu 1820..."
date: 2008-08-13
forum: Multimedia Software
---

### Post by k5dreadlord on 2008-08-13
I have a home studio at home using Ubuntu and I stumbled upon a small problem today, my sound does not playback on my Ubuntu partition... The sound card records just fine using Ardour and mixers show there is sound playing when I open a file or playback sound in Ardour, I see the volume levels moving and all. I beleive it may have something to do with drivers since the card looks like it works just fine, I didn't get any luck solving this yet...

Also, when I go to my sound options and try testing playback it doesn't give me anything exept when I use the Multichannel Playback option. I tried keeping this option but sound does not work in any program, on youtube etc. 

Thanks in advance,
FX

---

### Post by k5dreadlord on 2008-08-13
sudo lspci gives this:

00:00.0 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. PT894 I/O APIC Interrupt Controller
00:00.7 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. PT890 PCI to PCI Bridge Controller
00:0b.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
00:0b.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 01)
00:0c.0 FireWire (IEEE 1394): Texas Instruments TSB12LV26 IEEE-1394 Controller (Link)
00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 Host bridge: VIA Technologies, Inc. VT8237A Host Bridge
02:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1)

---

### Post by k5dreadlord on 2008-08-13
Update: I managed to get the sound back by unmuting and raising the sound volume of a channel called "Side" in the alsamixer.

Problem is now I only have my left speaker working and it plays only the left track of every song and recording I make... Right tracks are nowhere to be heard.

I've looked everywhere and I can't find any sort of pan control and I've tried raising the volume of every channel there is, sound just won't come out of the right speaker...

Any help would be appreciated!
FX

---

