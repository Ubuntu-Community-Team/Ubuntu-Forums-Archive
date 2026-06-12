---
title: "Compaq Presario B1900 - No Sound"
date: 2006-10-01
forum: Multimedia &amp; Video
---

### Post by Tim.R on 2006-10-01
Hi

I just bought a Compaq Presario B1900 (which is an awesome laptop if all the hardware was working).  I'm at the moment using Edgy, but I have the same problem in Dapper: my sound isn't working.  I get no sound at all through headphones or through the main speakers.  I also noticed that in KMix (I'm using Kubuntu) and in alsamixer there is a PCM and a front volume, but no Master.

I've attached my lsmod -v, lspci and aplay -l.

I've also tried downloading the newest sound drivers for windows from the HP/Compaq website and loading them in ndiswrapper, but that didn't work (it said they were invalid drivers).

Anyway if anybody can point me in the right direction of what to try next, that would be great.

Cheers,
Tim

P.S. My sound volume is up and is unmuted.  Also, there is no switch for autodetect headphones like there usually is.

---

### Post by Tim.R on 2006-10-01
Forgot to attach the files

---

### Post by Hero_boy on 2006-10-21
I have just ordered one of these laptops, a B1916TU to be specific. I wouldn't mind running Ubuntu as a dual boot.

Did you manage to fix your sound driver issue?

---

### Post by Tim.R on 2006-11-01
Not only did I not get the sound working, I took it back to the place I bought it because of a design fault.  It turns out that the lid was made of quite a flexible material, and it turned itself on inside my bag as you can turn on the power button by pressing the back of the lid when it's closed.

---

### Post by Hero_boy on 2006-11-17
Yes I have to confirm the above design fault. It is a HUGE flaw because in my bag the laptop heated up so much it was almost too hot to hold!

For those looking at this laptop this doesn't seem like a bad place for a quick review (Model B1916TU):

+ve's
-----
+ Small
+ Considering the price (cheap) it has:
      + Good processing power
      + ATi Dedicated Chipset
      + DVD-RW

Neutral
-------
*The battery life is short (>2hrs) but this is OK for a 4cell battery
*Sound is laughable BUT most laptops don't come with great sound.

-ve's
-----
- Keyboard slopes in-ward (check out the H key)
- Keyboard flex's
- Unit heats up readily
- The Compaq screen is good but NOT great, sometimes blurry and the contrast always seems out of ratio
-- A design fault means the power button can be pressed by the lid flexing (ie. when it is in your bag) It got very very hot and happens every time I put it in my bag to carry around.
--My 1.4GHz Celeron laptop starts 5 seconds slower then this Dual-Core 1.7ghz, and runs WoW slightly better?
--Not Ubuntu Friendly - no sound & wireless drivers etc.

Conclusion
----------

I like this laptop and am happy with my purchase, but only because it is a fantastic price for this form factor (cost me $1600AU). If I had paid $1000 more and received this unit I would have sent it back by now. Be prepared to buy a very hard case/bag :)

To get back to Ubuntu, it is a lot of work to get it going. I might wait for the next release and see if it is more compatible :)

---

### Post by dakvid on 2006-11-29
Hi, just came across this thread. I know it's a little old but thought I'd mention that there's currently no support for this laptop's sound card in ALSA. Hopefully Realtek will soon release a driver, or give the ALSA devs the specs to do it themselves. Annoyingly most of the information is already in the driver but there's some sort of quirk in this (and at least one other card) that stop things from working fully.

However, it is possible to get some sound going to a somewhat acceptable standard on headphones. Compile the ALSA driver with the debug option and use the parameter model=test. The test driver allows you to listen on headphones through the *microphone* jack.

Cheers
David

PS I didn't manage to confirm the design fault, but I was worried about damaging the screen. I've had no problems transporting it in my backpack so far.

---

### Post by Paps on 2007-06-27
Hi There,

I got a Comapq B1959TU (The dual core edition) for NZ$1895. This was a good price for the form factor and performance ratio...

On Debian (Sid) I successfully managed to get the whole unit perfectly working (sound, wifi, sleep and hibernate) using ndiswrapper, alsa source and suspend2ram...

All this was working perfectly until my unit internal speaker broke and had to send it for repair... Now, the problem with Debian Sid is the new numbering system that they use with xorg (incompatible with ATI proprietary driver (Take Nvidia chip if you have the opportunity))

So I installed ubuntu and set up my wifi using ndiwrapper, compiz fusion through XGL, etc. However, no matter how many time I compiled the alsa source it won't work! 

Here my couple of relevant outputs:

paps@powerswiss:~$ lspci -nv
00:00.0 0600: 1002:5a31 (rev 01)
        Subsystem: 103c:30ba
        Flags: bus master, 66MHz, medium devsel, latency 64

00:01.0 0604: 1002:5a3f (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: c0000000-c00fffff
        Prefetchable memory behind bridge: d0000000-dfffffff
        Capabilities: <access denied>

00:04.0 0604: 1002:5a36 (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=04, sec-latency=0
        Memory behind bridge: 40000000-400fffff
        Capabilities: <access denied>

00:05.0 0604: 1002:5a37 (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=07, sec-latency=0
        Capabilities: <access denied>

00:12.0 0101: 1002:4379 (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: 103c:30ba
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
        I/O ports at 8440 [size=8]
        I/O ports at 8430 [size=4]
        I/O ports at 8420 [size=8]
        I/O ports at 8410 [size=4]
        I/O ports at 8400 [size=16]
        Memory at c0507000 (32-bit, non-prefetchable) [size=512]
        [virtual] Expansion ROM at 40100000 [disabled] [size=512K]
        Capabilities: <access denied>

00:13.0 0c03: 1002:4374 (rev 80) (prog-if 10 [OHCI])
        Subsystem: 103c:30ba
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
        Memory at c0504000 (32-bit, non-prefetchable) [size=4K]

00:13.1 0c03: 1002:4375 (rev 80) (prog-if 10 [OHCI])
        Subsystem: 103c:30ba
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
        Memory at c0505000 (32-bit, non-prefetchable) [size=4K]

00:13.2 0c03: 1002:4373 (rev 80) (prog-if 20 [EHCI])
        Subsystem: 103c:30ba
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
        Memory at c0506000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:14.0 0c05: 1002:4372 (rev 83)
        Subsystem: 103c:30ba
        Flags: 66MHz, medium devsel
        I/O ports at 8450 [size=16]
        Memory at c0507400 (32-bit, non-prefetchable) [size=1K]

00:14.1 0101: 1002:4376 (rev 80) (prog-if 82 [Master PriP])
        Subsystem: 103c:30ba
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 18
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 8460 [size=16]
        Capabilities: <access denied>

00:14.2 0403: 1002:437b (rev 01)
        Subsystem: 103c:30ba
        Flags: bus master, slow devsel, latency 64, IRQ 18
        Memory at c0500000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:14.3 0601: 1002:4377 (rev 80)
        Subsystem: 103c:30ba
        Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 0604: 1002:4371 (rev 80) (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=08, subordinate=0a, sec-latency=64
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: f0200000-f02fffff
        Prefetchable memory behind bridge: f0300000-f03fffff

01:05.0 0300: 1002:5a62 (prog-if 00 [VGA])
        Subsystem: 103c:30ba
        Flags: bus master, 66MHz, medium devsel, latency 255, IRQ 21
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        I/O ports at 9000 [size=256]
        Memory at c0000000 (32-bit, non-prefetchable) [size=64K]
        [virtual] Expansion ROM at c0020000 [disabled] [size=128K]
        Capabilities: <access denied>

02:00.0 0280: 14e4:4312 (rev 01)
        Subsystem: 103c:1361
        Flags: bus master, fast devsel, latency 0, IRQ 18
        Memory at 40000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

08:07.0 0c00: 1180:0832 (prog-if 10 [OHCI])
        Subsystem: 103c:30ba
        Flags: bus master, medium devsel, latency 64, IRQ 16
        Memory at c0200000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>

08:07.1 0805: 1180:0822 (rev 19)
        Subsystem: 103c:30ba
        Flags: bus master, medium devsel, latency 64, IRQ 20
        Memory at c0200800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

08:07.2 0880: 1180:0843 (rev 01)
        Subsystem: 103c:30ba
        Flags: bus master, medium devsel, latency 0, IRQ 15
        Memory at c0200c00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

08:07.3 0880: 1180:0592 (rev 0a)
        Subsystem: 103c:30ba
        Flags: medium devsel, IRQ 15
        Memory at c0201000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

08:08.0 0200: 10ec:8139 (rev 10)
        Subsystem: 103c:30ba
        Flags: bus master, medium devsel, latency 64, IRQ 19
        I/O ports at a000 [size=256]
        Memory at c0201400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>


paps@powerswiss:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC260 Analog [ALC260 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

paps@powerswiss:~$ cat /dev/sndstat 
Sound Driver:3.8.1a-980706 (ALSA v1.0.14rc4 emulation code)
Kernel: Linux powerswiss 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686
Config options: 0

Installed drivers: 
Type 10: ALSA emulation

Card config: 
HDA ATI SB at 0xc0500000 irq 18

Audio devices:
0: ALC260 Analog (DUPLEX)

Synth devices: NOT ENABLED IN CONFIG

Midi devices: NOT ENABLED IN CONFIG

Timers:
31: system timer

Mixers:
0: Realtek ALC260

paps@powerswiss:~$ dmesg | grep intel
[   41.720240] hda-intel: Invalid position buffer, using LPIB read method instead.

I had options snd-hda-intel model=hp in both /etc/modprobe.d/alsa-base and /etc/modprobe.d/sound

Here is where the issue seems to be... And invalid position... What I cannot understand is that sound works great under Debian but not with Ubuntu... I will keep trying for while but in the worse will have to switch back to Debian without 3D support (Thanks ATI)

Finally an advice DO NOT BUY COMPAQ computer at all cost! Their construction is crape and are a cheap brand from HP and their services under warranty is even worse! DO NOT also BUY ATI!

I stuck here... Every suggestions or help welcome to solve my sound problem...

Thanks guys

++ Paps

P.S. If i do lspci -nv as root the capabilities are ok (ie: not access denied>

---

### Post by Paps on 2007-06-27
Forgot to say in my previous post... 

I got it working under Debian by muting the external amplifier the problem is that I cannot find in alsamixer and whatever mixer I'm using the option external amplifier actually it doesn't even show up as an option in gnome alsamixer preferences...

Thanks for the help

++ Paps

---

### Post by kathryn on 2008-02-13
I've had a Compaq Presario B1959TU laptop (but B1900 printed near the power button) for about a year.  It was shipped with Vista Business but after loving Gutsy on my desktop I want to install Gutsy on the laptop too.  Probably as a dual boot.

Aside from the potential problems associated with dual-booting Vista, has anyone resolved the hardware issues mentioned in previous posts of this thread?  I've been using the 7.10 release of Gutsy... wondering if the compatibility has improved over time.

P.S.  I've not encountered the design fault; my laptop has never switched itself on.

---

### Post by kathryn on 2008-02-18
Any readers with a similar laptop to mine might be interested to hear that Ubuntu Gutsy (7.10) dual boots perfectly with Vista pre-installed.  I used the Vista disk management tool to create an empty partition before installing Gutsy.

The laptop was shipped with a separate drive/partition for the recovery disk content (as opposed to a CD or DVD).  Prior to installation of Gutsy I noted that Ubuntu recognized Vista as **sda1**, while the recovery partition was **sda2**.

After installation, Grub listed Vista *and* the recovery drive as Vista boot options with the **same name**.  I checked the menu.lst file to confirm which was which: 

```
gksudo gedit /boot/grub/menu.lst
```

Note that Vista boot options appear at the very bottom of the file. 
The entry for sda1 was obviously Vista.  I commented out (with # character at the start of each line) the second Vista entry to prevent accidental selection of the recovery drive.  I can easily remove the # character, should I wish to return the laptop to its factory settings.  

By the way, the sound works OK for me, and wireless was quickly up and running after a single synaptic installation (see [http://ubuntuforums.org/showthread.php?p=4354200#post4354200](http://ubuntuforums.org/showthread.php?p=4354200#post4354200)).

> **kathryn said:**
> I've had a Compaq Presario B1959TU laptop (but B1900 printed near the power button) for about a year.  It was shipped with Vista Business but after loving Gutsy on my desktop I want to install Gutsy on the laptop too.  Probably as a dual boot.

Aside from the potential problems associated with dual-booting Vista, has anyone resolved the hardware issues mentioned in previous posts of this thread?  I've been using the 7.10 release of Gutsy... wondering if the compatibility has improved over time.

P.S.  I've not encountered the design fault; my laptop has never switched itself on.

---

