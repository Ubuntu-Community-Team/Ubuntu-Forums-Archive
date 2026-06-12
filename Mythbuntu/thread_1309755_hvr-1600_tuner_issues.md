---
title: "hvr-1600 tuner issues"
date: 2009-11-01
forum: Mythbuntu
---

### Post by zapstrap on 2009-11-01
Thought I had this licked, but not so.  I have an HVR-1600 tuner card, along with a PVR-150.  The NTSC tuners work with no issue, but the ATSC tuner in the HVR-1600 has an issue.  When digital (QAM256) channels are tuned, the audio drifts all over the place and drops out periodically, and the picture frequently goes garbled and comes back.

I thought this was a PCI bus latency problem, as from what I've read, the hard drives need to have a little more latency time than out of the box.  A little homework, and I got this far:

*** lspci -v | grep -A8 cx18*** gives me

```

02:0b.0 Multimedia video controller: Conexant Systems, Inc. CX23418 Single-Chip MPEG-2 Encoder with Integrated Analog Video/Broadcast Audio Decoder
    Subsystem: Hauppauge computer works Inc. Device 7444
    Flags: bus master, medium devsel, latency 64, IRQ 23
    Memory at f8000000 (32-bit, non-prefetchable) [size=64M]
    Capabilities: <access denied>
    Kernel driver in use: cx18
    Kernel modules: cx18

```Next, ***lspci -v | grep -A8 00:1f**,* gives: 

```

00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
    Flags: bus master, medium devsel, latency 0
    Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: ASUSTeK Computer Inc. Device 80a6
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at efe0 [size=8]
    I/O ports at efac [size=4]
    I/O ports at efa0 [size=8]
    I/O ports at efa8 [size=4]
    I/O ports at ef90 [size=16]
    Memory at 50000000 (32-bit, non-prefetchable) [size=1K]
--
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: ASUSTeK Computer Inc. Device 80a6
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 18
    I/O ports at ef88 [size=8]
    I/O ports at ef84 [size=4]
    I/O ports at ef68 [size=8]
    I/O ports at ef80 [size=4]
    I/O ports at ee60 [size=16]
    Kernel driver in use: ata_piix

```Notice all the pci devices have a latency of 0?  If I try ***setpci -v -s 00:1f.2 latency_timer=f0***

I get ***00:1f.2:0d f0***

This looks sensible enough, but when I do an ***lspci -v | grep -A8 00:1f.2***,  the latency value is still 0.

How do I increase the latency time for the SATA drive (which is my media drive)?  I suspect this is the problem, but could it be something else?

---

### Post by zapstrap on 2009-11-03
Anyone?!?

I've continued to snoop through the bios trying to figure this out, flashed it to the last release ASUS did for this mobo, but so far everything related to the IDE interface is stubbornly locked at 0.  I tried setting the PCI latency timer in the bios to 248, and it affected the Hauppauge cards, but nothing else.  Looking around, this may be a more general problem with ASUS and/or the Intel 82801EB chipset.  Is there a better place to ask this question?

---

### Post by epi 1:10,000 on 2009-11-07
Try [Devin Heitmueller]("http://www.kernellabs.com/blog/?author=3")'s improved drivers. They are new and experimental but they greatly improved my HVR-1600's QAM reception.

[http://www.kernellabs.com/blog/?p=1027](http://www.kernellabs.com/blog/?p=1027)



in your favorite terminal

change to your home directory

then

hg clone [http://kernellabs.com/hg/~dheitmueller/hvr-1600-perf-2]("http://kernellabs.com/hg/%7Edheitmueller/hvr-1600-perf-2")

cd hvr-1600-perf-2

make

sudo make install

reboot

---

### Post by epi 1:10,000 on 2009-11-07
If you have problems were the tv and the cable box tune channels that the HVR-1600 can't then you may need to aplify your signal w/ a digital cable amp. 

Measure signal level/quality w/ azap or use the service menu on your motorola settop box 
[http://en.wikibooks.org/wiki/How_to_use_a_Motorola_DVR](http://en.wikibooks.org/wiki/How_to_use_a_Motorola_DVR)

I would suggest a motorola.

[http://www.amazon.com/Motorola-Booster-484095-001-00-Bi-Directional-Amplifier/dp/B000066E6Y](http://www.amazon.com/Motorola-Booster-484095-001-00-Bi-Directional-Amplifier/dp/B000066E6Y)

[http://www.amazon.com/Motorola-Signal-Booster-BDA-S4-Amplifier/dp/B000WPGRKK/ref=dp_cp_ob_e_title_1](http://www.amazon.com/Motorola-Signal-Booster-BDA-S4-Amplifier/dp/B000WPGRKK/ref=dp_cp_ob_e_title_1)

The HVR-1600 does not work well with to weak or to strong a signal.  The motorola cable boxes have much more sensitive/advanced tuners.

---

### Post by zapstrap on 2009-11-07
Thanks!

I tried Devin's new drivers, and it helped tremendously with the garbled video and audio drop-outs.  Unfortunately, the sound is still sometimes off by over 500mS.  If it gets out by over 700mS, myth doesn't seem able to handle correcting it.  The sound and video both go really choppy.

Also, since I wasn't using the HVR-1600 ATSC tuner for much of anything, I never noticed it before, but the device does not see 1080i broadcast signals.  There are several of these available, but none of them are seen by the HVR-1600.  The TV can tune them in directly, so I'm a little disappointed.  I don't have a decoder box, just a TV, a receiver and the myth box.

As to signal strength, cable comes in, goes through a 15dB amplifier, hits a 4-way splitter, goes to the TV, the receiver, a TV in a different room, then the last of the four splitter outputs goes to...another 4-way splitter, going to the PVR-150, the HVR-1600 NTSC input, the HVR-1600 ATSC input, and the HVR-1600 FM input.  Ratsnest anyone?  Since I was having so much trouble in the beginning, I disconnected everything, and piped the 15dB amplified cable directly to the HVR-1600 ATSC input.  It made no difference.

I'll try the azap app too.  In for a penny...

---

### Post by zapstrap on 2009-11-26
On a reporting back note, upgrading from Mythbuntu 9.04 to 9.10 has had a negative effect on the HVR-1600.  Using Devin's improved drivers for the card, I initially had the card almost working perfectly.  The only major issue was a large delay in audio on the digital tuner, upwards of 1/2 second.

Now that I've upgraded, on both the NTSC and ATSC tuners, the audio cuts out within about 5 seconds of tuning a channel (on the first time tuning).  Returning to the MythTV menu and going back to watching TV a second time gets the audio working, sort of.  The ATSC tuner audio now produces a buzz every 10-20 seconds.  It sounds like a buffer underrun, as if the sound gets momentarily stuck repeating the same 100mS or so of audio for up to a second.  The ATSC tuner has also resumed producing momentarily garbled video every 5 to 10 seconds.  I tried recompiling the driver for the card, but it made no difference.

Oddly enough the HVR-1600 NTSC tuner still seems able to record programs without losing sound.  Perhaps this is a hint that the problem isn't in the driver, but more in the rest of the system.

I'd love to increase the PCI latency to the hard drive, but this motherboard locks the latency timer at 0 pci clocks:

```
setpci -v -s 00:1f.2 LATENCY_TIMER=20
```responds showing the register has been changed, but subsequent 
```
lspci -v -s 00:1f.2
```shows the latency timer is still 0.

If anyone has any ideas on how to solve these problems, I'm all ears.

---

### Post by oqion on 2009-12-11
How did you get the channels at all, I can't seem to get the 1600 to be recognized or scan.

---

### Post by zapstrap on 2009-12-14
You have to add support for the cx23418, which I don't believe was properly set up in the  build I had (Mythbuntu 9.04).  I could be wrong, as I had a bad hvr-1600 out of the box the first time I tried to install it.  By the time I got the second card, I had added the support drivers already.  Try this page:

[http://www.mythtv.org/wiki/Hauppauge_HVR-1600](http://www.mythtv.org/wiki/Hauppauge_HVR-1600)

That was a good start, and outlines how to get the card up and running.  If you want the latest drivers (experimental, but a little better than the standard ones) go here:

[http://www.kernellabs.com/blog/?p=1027](http://www.kernellabs.com/blog/?p=1027)

Use the drivers you find through the second link, and follow the installation instructions from the first link above.  This should get the card found, and your scans should work.

I'm still not thrilled with the performance of the card, and have serious enough problems with it that I don't bother with the ATSC tuner.  The NTSC tuner is superior to the PVR-150 sitting next to it, but as of the Ubuntu 9.10 upgrade fiasco, is no longer usable for watching live tv.  It is still acceptable for recording.  ATSC is just too fussy to set up.  The built in channel-scan never produced anything that could sync up with schedules direct, so I always had wrong channel information and could never record anything.  Searching around kept pulling in alternative methods of scanning channels and manually creating tables, plus my cable provider kept moving channels around, encrypting one week, not the next.  Every time the channels got moved I'd have to rescan the channels, and this operation is at least an hour of fussing.  I upgraded to ubuntu 9.10, and that seemed to really degrade the performance of the ATSC tuner (and many other things).  Now whenever I try to watch something with it, the audio locks up, playing buzzing sounds for 1/2 second every 30 seconds or so, and the picture goes momenarily garbled for about 1/2 second out of every 10.  I had another post on this looking for ideas, but so far, I seem to be the only one posting messages to it, and the digital tuner's been unusable for several weeks.  I regret upgrading to Ubuntu 9.10, and consider it a big disappointment.  So many things work less reliably or not at all now (see my post on xscreensaver).  The money and time invested in this system seems, well, wasted.  I sure wish Canonical would stop screwing around with new features and do a release concentrating strictly on bug-fixes and reliability.  I don't really want to bother with it until 10.04 comes out.

---

### Post by the_pod on 2009-12-15
Out of curiosity, what is your video chipset?  

I have a 1600 as well and have been less than pleased with the digital pick-up.  I also have a 1250 and this has been much better. (I don't have an NTSC signal...).  

While my 1600 isn't as bad as you report, I've definitely had video tearing and bad signal decoding.  On a regular basis the front-end will simply hang and crap out, more often than not on an HD video feed for a network.  

My work around has been restarting the front-end but this is less than optimal.  My hope was that these issues were largely related to having an ATI video card and am getting an upgraded Nvidia card for the holidays w/ an HDMI output and 1080 support.... Will report back in a few weeks if you're interested.  

That said, I wish I had the cash to just throw away my 1600 and get something better - been a bear to make it acceptable.

---

### Post by zapstrap on 2009-12-15
I frequently get the video front end hanging and not coming back when viewing ATSC/QAM-256 signals.  Usually restarting the front end is enough, but probably 1/3 of the time this happens, a full cycling of power is needed.  Something on the tuner card locks up, and even a  soft reboot of the machine is not enough.  It's especially a problem if the cable provider moves or encrypts the channel you were last watching before you exited to the myth menu.  When the tuner tries to lock onto the now missing or encrypted channel, it fails and crashes the card.  The only way around this is to go into the backend setup and change the initial channel for the ATSC tuner to one that is functioning.  If you don't you will crash the tuner 100% of the time.  If you think you're quick and can just change it right away before it crashes, think again.  If the card even tries to access an encrypted/missing  channel, down she goes.

To answer your question about the video card directly, I have an nvidia FX6200 card in the box, along with the proprietary nvidia drivers.  BEWARE that if you install an nvidia card along side the hvr-1600 you have to make a minor change to how the kernel loads.  I believe you need something like vmalloc=256M on the kernal load line in grub.conf.  I can't recall the thread this is discussed in, but it's an unresolved issue as of this writing.  When I upgraded to mythbuntu 9.10, the installation didn't check for kernel load customization and hence didn't bring forward the previous mods.  The first time I rebooted after the upgrade was complete, X refused to launch and I got the screen blanking about 2-3 times a second, writing some sort of "holy sh*t I'm in a state of panic" text, then blanking and repeating.  I watched it for a while, trying to glimpse the text long enough to read it, but in the end, I just guessed at what it was.  The previous release required this mod but its symptoms without it were different, so it wasn't so obvious.

---

