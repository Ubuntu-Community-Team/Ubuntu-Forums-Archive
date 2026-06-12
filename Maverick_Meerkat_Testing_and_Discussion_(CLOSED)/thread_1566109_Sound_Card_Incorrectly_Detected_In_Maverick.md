---
title: "Sound Card Incorrectly Detected In Maverick"
date: 2010-09-01
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by NightwishFan on 2010-09-01
My sound card in previous versions of Ubuntu was detected as:
VIA VT1708

In Maverick running lshw -C sound gets me:
```

WARNING: you should run this program as super-user.
  *-multimedia            
       description: Audio device
       product: 82801I (ICH9 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:45 memory:fe9f4000-fe9f7fff

```

Running lshw as a super user gets me a hard lockup. Any ideas of what I can go on? I thought about blacklisting the module however there were a lot of question marks when it came to enabling the other driver.

Symptoms of this incorrect detection are sound chopping randomly, it tends to bring video down with it. I still think the sound is the root of the cause.

I am testing a mainline kernel I will post my results later. Thanks in advance! ):P

---

### Post by ranch hand on 2010-09-02
That looks like your integrated audio controller.

what do you get from;
```

lspci

```
One thing you might do, probably a waste of time but it would eliminate one thing, is get into your bios and make sure that the onboard controller is disabled.

I know that Ubuntu will change bios settings in some cases.  This box had 2 cpus disabled when we got it with Vista 32bit on it.  Installed hardy and that was changed to all 4 working with out my intervention.

---

### Post by NightwishFan on 2010-09-02
Thanks for responding my friend.

This is a laptop so I think that is just my device. On the same bios settings in previous versions it is detected as the via card. lspci gets me:
```
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
```

---

### Post by ranch hand on 2010-09-02
Ah, I see said the blind man as he picked up his hammer and saw (one of my fathers favorite sayings).

Must just be going by the chipset in 10.10 instead of the brand identifier tag.

I have no idea what to do, I bet someone here does though.  Pretty good bunch with a lot of different hardware and some of these guys have been testing a long time and know more tricks than is probably legal in some places.

Good luck.  I am going to have to keep an eye on this one.  Too many interesting threads in this forum.

---

### Post by NightwishFan on 2010-09-02
Actually that makes sense, and I wanted to confirm it before I reported it. The card does behave like a 'via' and has the features from it. I assume it is being used correctly. It just must be misbranded. Though this is odd on top of all the other issues I have been having with sound.

The mainline 2.6.36rc3 kernel still has this issue but does not glitch in some applications that the Maverick kernel does (will have to confirm under different situations though). Adding myself to the rtkit group (not sure if this helps or not, as the pulse-rt group is gone) I did not notice as much stutter though I will have to do some more thorough testing to know if this does anything at all and not just a placebo.

The branding of the card in lshw/lspci is the only thing I noticed different.

Also, the backport alsa drivers in lucid (2.6.34 I believe) do not have the stutter in video/audio but backporting a 2.6.35 kernel from the xorg edgers ppa does.

---

### Post by NightwishFan on 2010-09-03
Sorry for double post. Ranch, I found out more about the problem. Pulse has to be causing some serious issues for me. I get a lot of ratelimit errors and my touchpad locks up. Changing the TTYS fixes it, however it takes a while to 'chill out' to be able to. I filed a bug.

```
Sep  2 16:11:44 virgil-laptop pulseaudio[1460]: ratelimit.c: 1 events suppressed
Sep  2 16:11:49 virgil-laptop kernel: [ 5070.317977] psmouse.c: Touchpad at isa0060/serio4/input0 lost synchronization, throwing 1 bytes away.
Sep  2 16:11:50 virgil-laptop pulseaudio[1460]: ratelimit.c: 1 events suppressed
Sep  2 16:11:50 virgil-laptop kernel: [ 5071.618605] psmouse.c: resync failed, issuing reconnect request
Sep  2 16:11:55 virgil-laptop kernel: [ 5076.916065] psmouse.c: Touchpad at isa0060/serio4/input0 lost synchronization, throwing 1 bytes away.
Sep  2 16:11:59 virgil-laptop kernel: [ 5080.988574] psmouse.c: resync failed, issuing reconnect request
Sep  2 16:12:00 virgil-laptop pulseaudio[1460]: ratelimit.c: 1 events suppressed
Sep  2 16:12:05 virgil-laptop pulseaudio[1460]: ratelimit.c: 787 events suppressed
Sep  2 16:12:11 virgil-laptop pulseaudio[1460]: ratelimit.c: 2 events suppressed
Sep  2 16:12:17 virgil-laptop kernel: [ 5098.792920] Skipping EDID probe due to cached edid
Sep  2 16:12:23 virgil-laptop pulseaudio[1460]: ratelimit.c: 536 events suppressed
Sep  2 16:12:51 virgil-laptop kernel: [ 5132.738697] psmouse.c: Touchpad at isa0060/serio4/input0 lost synchronization, throwing 1 bytes away.
Sep  2 16:12:52 virgil-laptop kernel: [ 5133.843711] psmouse.c: resync failed, issuing reconnect request
Sep  2 16:13:01 virgil-laptop kernel: [ 5142.188306] psmouse.c: Touchpad at isa0060/serio4/input0 lost synchronization, throwing 1 bytes away.
Sep  2 16:13:10 virgil-laptop kernel: [ 5151.562450] psmouse.c: resync failed, issuing reconnect request
Sep  2 16:13:12 virgil-laptop kernel: [ 5153.950068] Skipping EDID probe due to cached edid
Sep  2 16:13:25 virgil-laptop kernel: [ 5166.771712] psmouse.c: Touchpad at isa0060/serio4/input0 lost synchronization, throwing 1 bytes away.
Sep  2 16:13:30 virgil-laptop kernel: [ 5171.623805] psmouse.c: resync failed, issuing reconnect request
Sep  2 16:13:40 virgil-laptop kernel: [ 5181.221044] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Sep  2 16:13:40 virgil-laptop kernel: [ 5181.227038] ADDRCONF(NETDEV_UP): eth0: link is not ready
Sep  2 16:13:42 virgil-laptop kernel: [ 5183.703248] psmouse.c: Touchpad at isa0060/serio4/input0 lost synchronization, throwing 1 bytes away.
Sep  2 16:13:46 virgil-laptop kernel: [ 5187.766934] psmouse.c: resync failed, issuing reconnect request
Sep  2 16:13:50 virgil-laptop kernel: [ 5191.870668] Skipping EDID probe due to cached edid
Sep  2 16:14:01 virgil-laptop kernel: [ 5202.324855] psmouse.c: Touchpad at isa0060/serio4/input0 lost synchronization, throwing 1 bytes away.
Sep  2 16:14:01 virgil-laptop kernel: [ 5202.834568] psmouse.c: resync failed, issuing reconnect request
```

---

### Post by kyleabaker on 2010-09-03
> **ranch hand said:**
> Ah, I see said the blind man as he picked up his hammer and saw (one of my fathers favorite sayings).

The version I always heard was, "I see said the blind man to his deaf daughter."

Anyhoo, I just did a fresh install of the Beta and my sound is borked from the start. It worked fine when I was updating from alphas, but I had to reinstall for other reasons.

I guess my builtin sound card isn't so much misdetected as just not loading.

lspci prints out:
> 
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev f3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev f2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev f3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:06.0 Network controller: RaLink RT2500 802.11g (rev 01)
04:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 LE] (rev a1)


Where my sound device appears to be:
Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)

Oddly enough, my line in isn't working either (and it did before). Would this be related to detection, pulse audio or alsa or something like that? All I see for Line Out in sound prefs is "Dummy Output" and nothing at all for line in. Any tips?

---

### Post by ranch hand on 2010-09-03
I put an OLD sound card in this box when we got it, still under Vista.  Onboard sound was terrible (60s pocket transistor radio quality.  My son said he used a Audigy1 5.1  card with Linux.

That is what is in here.  Very cheap.

Linux loves it can't get it to quit.  Had a little trouble under 8.10 and discovered the gnome-alsamixer.  Not really anything special, it just gives a gui to the alsamixer that does every thing the CLI control does for alsamixer.  With that on board there has not been a problem sense 8.10.

Sounds absolutely great with my Altec Lansing surround sound speaker system, another OLD, cheap find on ebay.  Now that I am in town I can share my music with the neighbors.  Not sure they appreciate it but I do it occasionally.

---

### Post by ktp on 2010-09-03
> **ranch hand said:**
> Sounds absolutely great with my Altec Lansing surround sound speaker system, another OLD, cheap find on ebay.  Now that I am in town I can share my music with the neighbors.  Not sure they appreciate it but I do it occasionally.

I got one of those old Altec Lansing system...you got to love them.

---

### Post by cariboo on 2010-09-04
> I put an OLD sound card in this box when we got it, still under Vista. Onboard sound was terrible (60s pocket transistor radio quality. My son said he used a Audigy1 5.1 card with Linux.

I had the same thing with an onboard ati sound chipset, sound quality was just horrible, I replaced it with an Audigy SE sound card. I just finished digitizing a bunch of 70-80's vinyl lp's, the sound quaility was just as good as the source.

---

### Post by ranch hand on 2010-09-04
I bet, great input side to these cards.

---

### Post by NightwishFan on 2010-09-04
I have some more interesting logs I think that are related:
```
Sep  1 19:29:14 virgil-laptop rtkit-daemon[1410]: The canary thread is apparently starving. Taking action.
Sep  1 19:29:14 virgil-laptop rtkit-daemon[1410]: Demoting known real-time threads.
Sep  1 19:29:14 virgil-laptop rtkit-daemon[1410]: Successfully demoted thread 1652 of process 1589 (n/a).
Sep  1 19:29:14 virgil-laptop rtkit-daemon[1410]: Successfully demoted thread 1589 of process 1589 (n/a).
Sep  1 19:29:14 virgil-laptop rtkit-daemon[1410]: Demoted 2 threads.
```

```
Sep  1 20:36:06 virgil-laptop pulseaudio[1589]: alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
Sep  1 20:36:06 virgil-laptop pulseaudio[1589]: alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report this issue to the ALSA developers.
Sep  1 20:36:06 virgil-laptop pulseaudio[1589]: alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.
```

Any ideas?

---

### Post by NightwishFan on 2010-09-04
Double post again I found a solution. It is the glitch free audio in pulse again. If I append tsched=0 to the line: load-module module-udev-detect in /etc/pulse/default.pa the audio/video work correctly.

---

### Post by ranch hand on 2010-09-04
Makes you feel pretty good too doesn't it.

Good job.

---

### Post by NightwishFan on 2010-09-04
Quite, thanks.

Now all that is left is a heck of a lot of debugging so I can send them a solid bug report. Hopefully I can get this fixed since I administrate a lot of this specific model of laptop. I had this same thing happen in hardy, only the line was module-hal-detect back then. The fact I needed udev now was a guess.

---

### Post by kyleabaker on 2010-09-04
*cough cough* Any tips on how I can get my sound working? :P

---

### Post by NightwishFan on 2010-09-04
I have not marked as solved as the solution is a mere workaround and the root of the problem has not been identified. Here is a link to my bug report:
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/629339](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/629339)

---

### Post by stmiller on 2010-09-05
This was my audio 'fix' for 10.10:

```
sudo apt-get remove --purge pulseaudio
```

*ducks*

:)

I've got an audiophile 2496 card that just does not work with pulse. Just removing pulse did not do the trick ; you have to purge to rid all of the startup and other pulse files related.

ICE1712 [Envy24] PCI Multi-Channel I/O Controller

---

### Post by Killigrew on 2010-09-05
thx a lot, had a problem with TeamSpeak3 which was solved with this tip too :)

greetings :)

> **NightwishFan said:**
> I have not marked as solved as the solution is a mere workaround and the root of the problem has not been identified. Here is a link to my bug report:
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/629339](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/629339)

---

### Post by NightwishFan on 2010-09-07
Audio still drops into a crackling hissing sound at random times, so this is not as fixed as I thought.

---

### Post by ktp on 2010-09-07
i am hearing these "cracking" since past few days...I have not had any issue before...maybe I just never noticed it before.

---

### Post by freefal67 on 2010-09-24
I have this same problem.  When I got to the sound preferences, under the Hardware tab there are no devices listed.
I get the following when I run lspci:

00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)

and this when I run sudo lshw -C sound


  *-multimedia            
       description: Audio device
       product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:46 memory:b0000000-b0003fff

---

### Post by dino99 on 2010-09-24
install paprefs & alsamixer and set your pref (app sound alsamixer)

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

