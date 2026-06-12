---
title: "Windows detects Audigy2, Linux doesn't"
date: 2008-02-01
forum: Multimedia &amp; Video
---

### Post by AxAeo on 2008-02-01
I recently switched up a lot of things on my regular desktop - I changed my motherboard, got a new video card, new RAM chips to go with the new board, and a new case. :D Everything works fine on Windows, but for a while in Linux I had no sound. It's worked perfectly before, but now it wasn't detecting my regular Sound Blaster Audigy 2 (which I have used forever with Linux). Instead it picked up a new card... One I hadn't seen before: "VT82xx". After a couple of quick checks I determined this was the onboard sound on the new motherboard, which output to the headphone jack on the front of my new case. (It's actually quite aggravating to use, especially because it's mono sound and it makes my left ear hurt.) 

To top it all off, alsamixer isn't working either - trying to run it returns the following:

alsamixer: function snd_ctl_open failed for default: No such device

Does anybody have any advice on how to get my regular card working on Linux again? Like I said before, it works perfectly fine in Windows...

---

### Post by taurus on 2008-02-01
Have you tried going into the BIOS and turn the onboard soundcard off?

---

### Post by AxAeo on 2008-02-01
> **taurus said:**
> Have you tried going into the BIOS and turn the onboard soundcard off?

I did... And now I have no sound cards detected at all on Linux.

---

### Post by taurus on 2008-02-01
Can you post the output of this command from a terminal?

```
lspci
```

Also, you didn't happen to blacklist your soundblaster in /etc/modprobe.d/blacklist?

```
cat /etc/modprobe.d/blacklist
```

---

### Post by AxAeo on 2008-02-01
> **taurus said:**
> Can you post the output of this command from a terminal?

```
lspci
```

Also, you didn't happen to blacklist your soundblaster in /etc/modprobe.d/blacklist?

```
cat /etc/modprobe.d/blacklist
```

```
00:00.0 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. P4M890 I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. P4M890 Security Device
00:00.7 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. P4M890 PCI to PCI Bridge Controller
00:03.0 PCI bridge: VIA Technologies, Inc. P4M890 PCI to PCI Bridge Controller
00:0f.0 IDE interface: VIA Technologies, Inc. Unknown device 5337 (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:13.0 Host bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
02:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1)
[B]04:03.0 Multimedia audio controller: Creative Labs SB0400 Audigy2 Value
[/B]
```

I assume the last line is what you were looking for? I was doing that just as I saw your post...

And it hasn't been blacklisted, it's certainly not under there.

---

