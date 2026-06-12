---
title: "Kubuntu Edgy, Sound Blaster Audigy, no sound"
date: 2007-01-18
forum: Multimedia &amp; Video
---

### Post by Rhapsody on 2007-01-18
I've made some [previous](http://ubuntuforums.org/showthread.php?t=336538) [threads](http://ubuntuforums.org/showthread.php?t=340328) about this in General Help (yes, I know, wrong place) but still haven't gotten anywhere. Here's what I know so far.

There is no sound coming out of the speakers whatsoever, no matter what application is generating it.
There is sound when I use a Kubuntu Edgy live CD, so it's this specific install, not the hardware.
The volume is not muted in any of the mixers I could find.
The drivers appear to be OK, and I reinstalled them anyway.
Kubuntu detects my sound card correctly.
This sound card worked perfectly in Kubuntu Breezy and Kubuntu Dapper with no help at all, it just worked.

It's been at least a week now, and I've gotten absolutely nowhere. All I've figured out is that I don't have a problem by any of the troubleshooting procedures I've found, but I'm still not getting anything out of the speakers.

Edit: I should also note that this started when I upgraded from Kubuntu Dapper to Kubuntu Edgy, which I did by reformatting my root partition and making a fresh install. So there should be nothing left over from Dapper Drake to mess things up, making this all the more mysterious.

---

### Post by deadgobby on 2007-01-18
OK so you have SB A. Just a silly question. Did you go into your BIOS and disable the on board sound so that Ubie will use your SB as default instead of the on board one???
Gobby

---

### Post by Rhapsody on 2007-01-18
> **deadgobby said:**
> OK so you have SB A. Just a silly question. Did you go into your BIOS and disable the on board sound so that Ubie will use your SB as default instead of the on board one???
Gobby

The last time I made BIOS changes was before I upgraded if I remember correctly, which had nothing to do with sound and didn't break sound after I rebooted back into Dapper. Besides that, I'm not even sure if this rather old (circa 2002) motherboard even has on-board sound.

---

### Post by deadgobby on 2007-01-18
Well you got me by the boo boo. If it work fine in Dapper and not in Edgy. I do not know what is going on. So I wish you luck.
Gobby

---

### Post by jbaloul on 2007-01-18
yup...something broke ...no sound here as well

```

root@jbdual:~ # lspci 
00:00.0 Host bridge: Advanced Micro Devices [AMD] AMD-760 MP [IGD4-2P] System Controller (rev 11)
00:01.0 PCI bridge: Advanced Micro Devices [AMD] AMD-760 MP [IGD4-2P] AGP Bridge
00:07.0 ISA bridge: Advanced Micro Devices [AMD] AMD-766 [ViperPlus] ISA (rev 02)
00:07.1 IDE interface: Advanced Micro Devices [AMD] AMD-766 [ViperPlus] IDE (rev 01)
00:07.3 Bridge: Advanced Micro Devices [AMD] AMD-766 [ViperPlus] ACPI (rev 01)
00:07.4 USB Controller: Advanced Micro Devices [AMD] AMD-766 [ViperPlus] USB (rev 07)
00:09.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:09.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:09.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 51)
00:0a.0 Mass storage controller: Promise Technology, Inc. PDC40775 (SATA 300 TX2plus) (rev 02)
00:0b.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61)
00:0c.0 Ethernet controller: D-Link System Inc RTL8139 Ethernet (rev 10)
00:0d.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
00:0d.1 Input device controller: Creative Labs SB Live! MIDI/Game Port (rev 07)
01:05.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)

```

--
Jacob
[http://howtoforums.net](http://howtoforums.net)

---

### Post by Rhapsody on 2007-01-19
I feel I have to bump this topic, as I ***still*** have no idea what this problem is or how to solve it.

---

### Post by jbaloul on 2007-01-19
ok, i got my problem out of the way....
apparently some progy was installed and removed the group "audio" from my user id....
logged in as root, usermod -G audio jacob

done.

yet to figure out what progy it was....



JB

---

### Post by RomeReactor on 2007-01-19
Rhapsody, have you tried changing the device in the volume applet (right-click the speaker on the top panel)?

---

### Post by Rhapsody on 2007-01-19
> **RomeReactor said:**
> Rhapsody, have you tried changing the device in the volume applet (right-click the speaker on the top panel)?

I don't have a top panel.

---

### Post by jbaloul on 2007-01-19
> **Rhapsody said:**
> I don't have a top panel.

alsamixer

in a shell

JB

---

### Post by Rhapsody on 2007-01-19
I've already messed around with AlsaMixer while trying to fix this. Changing the volumes does nothing and the card is listed as Audigy 1 [SB0090] as I'd expect. I don't see anything else I can do with it.

---

### Post by RomeReactor on 2007-01-19
> **Rhapsody said:**
> I don't have a top panel.

Right, Kubuntu...  my mistake :biggrin:

---

### Post by DraconicPhilosophies on 2007-02-11
Alright, I have the problem that sound doesn't work sometimes, but if I restart the computer I can get the sound to work. Oddly enough, if I use the MP3 player in FrostWire I can get sound.

So I am thinking it's an error that Edgy is making when it is starting up. Anyone bothered to check if the soundcard is getting initiated when Edgy boots?

---

