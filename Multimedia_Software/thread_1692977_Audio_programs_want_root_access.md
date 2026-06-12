---
title: "Audio programs want root access?"
date: 2011-02-22
forum: Multimedia Software
---

### Post by Mariane on 2011-02-22
At least this is what it looks like to me. 
Amarok can play music but asks to open kde wallet manager for some password. All other programs (vlc, media player, audacity, etc) seem to function normally but no sound comes out of the speakers. 

```

lspci -v
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
        Subsystem: CLEVO/KAPOK Computer Device 0573
        Flags: bus master, fast devsel, latency 0, IRQ 33
        Memory at f0f00000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

```

```

sudo lspci -v
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
        Subsystem: CLEVO/KAPOK Computer Device 0573
        Flags: bus master, fast devsel, latency 0, IRQ 33
        Memory at f0f00000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
        Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
        Capabilities: [100] Virtual Channel <?>
        Capabilities: [130] Root Complex Link <?>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

```

Problems are like:
 
```

sudo vlc
VLC is not supposed to be run as root. Sorry.
If you need to use real-time priorities and/or privileged TCP ports
you can use vlc-wrapper (make sure it is Set-UID root and
cannot be run by non-trusted users first).

```

So simply running program requiring sound enabling as root does not work - plus it would not be very good practice, IMHO. 

What should I do, please? 

Mariane

---

### Post by Mariane on 2011-02-23
I'm trying:
```

cd /
sudo find ./ -name alsa

```
./sbin/alsa
./usr/src/linux-headers-2.6.32-28-generic/include/config/thinkpad/acpi/alsa
./usr/src/alsa
./usr/src/alsa/alsa-lib-1.0.23/include/alsa
./usr/src/modules/alsa-driver/debian/alsa-modules-2.6.32-28-generic/lib/modules/2.6.32-28-generic/updates/alsa
./usr/include/alsa
./usr/share/sounds/alsa
./usr/share/alsa
./var/lib/alsa
./lib/modules/2.6.32-28-generic/updates/alsa
./etc/apm/scripts.d/alsa
./etc/default/alsa
./etc/alsa

Then I'll increase the permissions of all the alsa directories. 

Mariane

---

### Post by Mariane on 2011-02-23
Didn't work. but I found what to do: 

In my home/user directory I had a directory named .pulse. As I know pulse-audio causes nothing but problems on this machine I renamed it to save.pulse. 

Now the sound is fine. 

Mariane

---

