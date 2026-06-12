---
title: "installing alsa-drivers give module problem"
date: 2009-02-17
forum: Multimedia Software
---

### Post by davemar on 2009-02-17
I'm trying to install the alsa-drivers to get snd-via82xx based sound working on a base 8.10 installation. I'm running a 2.6.25-2-386 kernel (it's a EPIA ME6000 mobo), and I downloaded the alsa-driver-1.0.19 source. The configure line I used was:
```
./configure --with-kernel=/usr/src/linux-headers-2.6.25-2-386 --with-cards=via82xx --with-oss=yes
```
Which seemed correct, and "make" worked fine. But when I did "make install", it finished off with these errors:
```
/sbin/depmod -a 2.6.25.4 
WARNING: Couldn't open directory /lib/modules/2.6.25.4: No such file or directory
FATAL: Could not open /lib/modules/2.6.25.4/modules.dep.temp for writing: No such file or directory
make: [install-modules] Error 1 (ignored)

```
Why is it looking for a 2.6.25.4 instead of 2.6.25-2-386?

I tried appending ```
--with-moddir=/lib/modules/2.6.25-2-386/kernel/sound
``` to the configure line, but it did the same again.

So how can I get it to place the modules in the right place? Until then I'm can't get "modprobe snd-via82xx" to work.

Thanks.

---

### Post by davemar on 2009-02-18
I decided to let it install the modules in 2.6.25-4 directory, then copy the content to the 2.6.25-2-386 directory. So if I do an "ls -l *" in the kernel/sound sub-directory I get:
```
me@xx:/lib/modules/2.6.25-2-386/kernel/sound$ ls -l *
lrwxrwxrwx 1 root root   12 Feb 18 00:55 soundcore.ko -> acore/snd.ko

acore:
total 2271
drwxr-xr-x 2 root root    1024 Feb 18 00:12 oss
drwxr-xr-x 3 root root    1024 Feb 18 00:12 seq
-rw-r--r-- 1 root root  189873 Feb 18 00:12 snd-page-alloc.ko
-rw-r--r-- 1 root root  840530 Feb 18 00:12 snd-pcm.ko
-rw-r--r-- 1 root root  208807 Feb 18 00:12 snd-timer.ko
-rw-r--r-- 1 root root 1069852 Feb 18 00:12 snd.ko

drivers:
total 1
drwxr-xr-x 2 root root 1024 Feb 18 00:12 mpu401

misc:
total 101
-rw-r--r-- 1 root root 101539 Feb 18 00:13 ac97_bus.ko

pci:
total 222
drwxr-xr-x 2 root root   1024 Feb 18 00:12 ac97
-rw-r--r-- 1 root root 224748 Feb 18 00:12 snd-via82xx.ko

```

When I now do a "sudo modprobe snd-via82xx" I get this:
```
FATAL: Error inserting snd (/lib/modules/2.6.25-2-386/kernel/sound/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_mpu401_uart (/lib/modules/2.6.25-2-386/kernel/sound/drivers/mpu401/snd-mpu401-uart.ko): Unknown symbol in module, or unknown param
eter (see dmesg)
WARNING: Error inserting snd_timer (/lib/modules/2.6.25-2-386/kernel/sound/acore/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd (/lib/modules/2.6.25-2-386/kernel/sound/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_timer (/lib/modules/2.6.25-2-386/kernel/sound/acore/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_pcm (/lib/modules/2.6.25-2-386/kernel/sound/acore/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd_pcm
WARNING: Error inserting snd_ac97_codec (/lib/modules/2.6.25-2-386/kernel/sound/pci/ac97/snd-ac97-codec.ko): Unknown symbol in module, or unknown parameter (se
e dmesg)
FATAL: Error inserting snd (/lib/modules/2.6.25-2-386/kernel/sound/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_mpu401_uart (/lib/modules/2.6.25-2-386/kernel/sound/drivers/mpu401/snd-mpu401-uart.ko): Unknown symbol in module, or unknown param
eter (see dmesg)
WARNING: Error inserting snd_timer (/lib/modules/2.6.25-2-386/kernel/sound/acore/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd (/lib/modules/2.6.25-2-386/kernel/sound/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_timer (/lib/modules/2.6.25-2-386/kernel/sound/acore/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_pcm (/lib/modules/2.6.25-2-386/kernel/sound/acore/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd_pcm
WARNING: Error inserting snd_ac97_codec (/lib/modules/2.6.25-2-386/kernel/sound/pci/ac97/snd-ac97-codec.ko): Unknown symbol in module, or unknown parameter (se
e dmesg)
FATAL: Error inserting snd_via82xx (/lib/modules/2.6.25-2-386/kernel/sound/pci/snd-via82xx.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error running install command for snd_via82xx
```

So it's still knackered. Anyone got any ideas what's going here?

---

### Post by davemar on 2009-02-19
OK, I decided to install the 2.6.22-16-386 kernel (even though its in the 8.04 pool, not the 8.10) as it looked like it'll be less trouble. I followed the instructions in [http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449") and now doing the "modprobe snd-via82xx" works (well it doesn't return any errors). So it looks like that's fine.

Now when I try "aplay -l" I get:
```
aplay: device_list:215: no soundcards found...
```
sheesh...

If I do a "lspci -v" I get (the important part):
```
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
	Subsystem: VIA Technologies, Inc. Device aa01
	Flags: medium devsel, IRQ 10
	I/O ports at e400 [size=256]
	Capabilities: <access denied>
	Kernel driver in use: VIA 82xx Audio
	Kernel modules: snd-via82xx

```
So it looks like the soundcard is known.

So what on earth is happening?

---

### Post by davemar on 2009-02-20
Found the problem! My user wasn't in the audio group, so by changing that aplay started working.

Now I get audio out, but weirdly from the line in socket! The line out socket is silent.

I know the EPIA mobo can be set up so that the three 3.5mm sockets become the 6 output channels for a 5.1 setup. But if that was the case I would expect front left and right from the line out, and nothing from line in which would be the rears. I'm playing stereo audio files in this case.

I couldn't find any settings in alsamixer to switch between 6 channel out and 2in+2out+2head out.

---

