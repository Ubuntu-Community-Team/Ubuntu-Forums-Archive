---
title: "[SOLVED] Sound Blaster Live! no sound"
date: 2008-05-08
forum: Multimedia Software
---

### Post by x1a4 on 2008-05-08
Hi,

I just installed a SoundBlaster Live! (internal) sound card.  Xubuntu recognizes it and when I play music it thinks it's playing, yet there is not sound.  I tried all sorts of different ALSA configurations to no avail.  What't the best way to configure ALSA?  

Thank you.

EDIT: lspci output is this: 
```

00:0b.0 Multimedia audio controller: Creative Labs SB Audigy LS
	Subsystem: Creative Labs SB0410 SBLive! 24-bit
	Flags: bus master, medium devsel, latency 32, IRQ 16
	I/O ports at e000 [size=32]
	Capabilities: [dc] Power Management version 2

```

EDIT2: I should mention that this card is the second sound device.  The first being on-board.

---

### Post by pogoyoyo on 2008-05-08
yeah if i dont get an answer to my problem with 5.1 surround im gonna be looking for this answer aswell cuz i also have an SB live ext sound card.. doesnt work :/

---

### Post by gladstone on 2008-05-08
I have a Emu-1616m that worked *once* I compiled the newest alsa. I then fiddled around with the volume levels in "volume control" item in XFCE panel and now I have no sound. Checked levels in alsamixer but they are fine. Any ideas?

---

### Post by x1a4 on 2008-05-08
> **pogoyoyo said:**
> yeah if i dont get an answer to my problem with 5.1 surround im gonna be looking for this answer aswell cuz i also have an SB live ext sound card.. doesnt work :/

Start by checking your motherboard's manual.  Many boards require that you tell them (by way of jumpers) that you're not using onboard sound.  Mine doesn't need this and things should work.

---

### Post by x1a4 on 2008-05-08
> **gladstone said:**
> I have a Emu-1616m that worked *once* I compiled the newest alsa. I then fiddled around with the volume levels in "volume control" item in XFCE panel and now I have no sound. Checked levels in alsamixer but they are fine. Any ideas?

Interesting problem, isn't it?  On my end, other than having no sound everything is fine.

---

### Post by x1a4 on 2008-05-09
[color=#6B6767]**Eureka!**[/color]

I figured it out--sort of.  I managed to get this sucker working, though not all of its features.  When I have the time I'll research this more thoroughly and write a detailed HOWTO in the [Xubuntu area of my site]("http://xubuntu.hex1a4.net/").

Here's how to get your Sound Blaster Live! to work.

First get a pen and paper, then open a terminal and get yourself root priviledges.
```
sudo -s
```

Now run
```
lspci -v | less
```

Scroll down until you come to the info about the sound card. On my system this looks like this: 
```

00:**0b**.0 Multimedia audio controller: Creative Labs SB Audigy LS
        Subsystem: Creative Labs SB0410 SBLive! 24-bit
        Flags: bus master, medium devsel, **latency 32**, **IRQ 16**
        **I/O ports at e000** [size=32]
        Capabilities: [dc] Power Management version 2

```

Write down the values I highlighted in bold (as they are displayed on your system of course).

The first value you need is the location of the card, this is the very first thing you see in the output
```
00:**0b**.0
```
You need the second item marked in bold.  The first is the bus, the second is the device on the bus, and the third is :confused:.  The values are in hexadecimal notation.  Later you will need it in decimal notation so you have to convert it like so: 

00 = 00
...
09 = 09
0a = 10
**0b = 11**
0c = 12
0d = 13
0e = 14
0f = 15
10 = 16
11 - 17
...

write this number down, for me it's **0b** so I wrote down **11**

Once you know where on the bus the card is sitting write down the IRQ and latency values along with the port address.  In the above output this is 16, 32 and e000 respectively.

Now you should have several values (use your own here): 
card device location: **11** 
IRQ: **16**
latency: **32** (same for all?)

Now you need the ID of the card.  In XFCE, I used Sound Settings to obtain the value **CA0106**.

Create (or edit if created) the file
```
/etc/modprobe.d/sound
```
and add the following line to it:
```
options snd-sblive index=0 id="**CA0106**" pci=**11** port=0x**e000** irq=**16** latency=**32** seq_ports=4 max_synth_voices=64 max_buffer_size=128
```

The **index=0** property tells the system which position the card should be on.  0 means first and default. 

The **id="CA0106"** property specifies the ID of the card. 

**pci=11** is the location of the device.

**port=[color=green]0x[/color]e000** is the beginning bit of the port address. Be sure to prefix the address with **[color=green]0x[/color]**

**irq=16** is the IRQ of the card

**latency=32** device latency, whatever this thing is.

[b]seq_ports=4
max_synth_voices=64
max_buffer_size=128[/b]

Some SB Live! options I was able to dig up.  All of these are default values.  If you have tons of memory you can probably increase the buffer size which is in MBs.

Save the file and exit the editor.

It used to be that all you had to do was run /sbin/update-modules to update kernel modules.  Now you have to use /sbin/modprobe.  I haven't figured this part out yet, so the simplest way is to **reboot**.

Make sure your speakers are plugged-in to your sound card and turned on before rebooting.

Your Sound Blaster Live! sound card should now work.

Be sure to post how things went.

Good luck.

---

### Post by gladstone on 2008-05-09
Cool, sounding like progress!

I've been trying to adapt it to my setup:

```
options snd_emu10k1 index=0 id="MAEM8950" pci=00 port=0x1400 irq=18 latency=64 seq_ports=4 max_synth_voices=64 max_buffer_size=128
```

```
cat /proc/asound/modules
``` gave me "**snd_emu10k1**", when I reboot I get:

```

May 10 00:37:47 xxx-laptop kernel: [   17.246013] snd_emu10k1: Unknown parameter `pci'
```

or if I take out **pci** from the /etc/modprobe.d/sound file:

```

May 10 00:37:47 xxx-laptop kernel: [   17.246013] snd_emu10k1: Unknown parameter `port'
```

So I guess these are not supported on my card? Argh this is ridiculous. I might just try a reformat on "/" - it could do with one anyway :(

---

### Post by x1a4 on 2008-05-09
> **gladstone said:**
> Cool, sounding like progress!

I've been trying to adapt it to my setup:

```
options snd_emu10k1 index=0 id="MAEM8950" pci=00 port=0x1400 irq=18 latency=64 seq_ports=4 max_synth_voices=64 max_buffer_size=128
```


The pci value here must be either decimal, which means no leading zeros, or hexadecimal in its correct notation, meaning prefixed with **0x**. **pci=00** is wrong.  Also, when setting pci location, you must specify the **_device_** location, _not_ the bus.  Run lspci and it's the second item at the beginning of the entry 
```
00:**0b**.0 Multimedia audio controller: Creative Labs SB Audigy LS
``` which you must convert to decimal and use as a value for pci= or try using 0x0b (replacing 0b with your system's value, of course).

To convert, use a scientific calculator (real or software), switch to Hex mode, enter the value (in the above this is 0b), then switch to Dec mode and you'll have its decimal value. 

> 
```
cat /proc/asound/modules
``` gave me "**snd_emu10k1**", when I reboot I get:


emu10k1 is the actual ALSA driver but you can't use this.  This is the first thing I tried and it didn't work.  After googling for a while I found the solution in my last post which works for me. I don't know exactly how ALSA works but I know that if you want to specify emu10k1 you have to set the options elsewhere, /etc/modprobe.d/alsa-base perhaps??  That's why you got those pci errors.  
> 
```

May 10 00:37:47 xxx-laptop kernel: [   17.246013] snd_emu10k1: Unknown parameter `pci'
```

or if I take out **pci** from the /etc/modprobe.d/sound file:

```

May 10 00:37:47 xxx-laptop kernel: [   17.246013] snd_emu10k1: Unknown parameter `port'
```

You get these because you can't use emu10k1 in /etc/modprobe.d/sound.

Don't use emu10k1.  Use snd-sblive and you **must** specify at least the index, id, pci, port and irq parameters (and most likely latency as well).  These options are passed to the kernel which absolutely needs to know the device identifier, index, where the device is and how it communicates.

> 
So I guess these are not supported on my card? Argh this is ridiculous. I might just try a reformat on "/" - it could do with one anyway :(

Don't give up... it's easy once you figure it out.  

Try this: 
```
options snd-sblive index=0 id="MAEM8950" pci=*<n>* port=0x1400 irq=18 latency=64 seq_ports=4 max_synth_voices=64 max_buffer_size=128
```

---

### Post by gladstone on 2008-05-10
This is my lspci -v | less

```

07:**00**.0 Multimedia audio controller: Creative Labs SB0400 Audigy2 Value
        Subsystem: Creative Labs Unknown device 4201
        Flags: bus master, medium devsel, latency 64, IRQ 18
        I/O ports at 1400 [size=64]
        Capabilities: [dc] Power Management version 2

```


The soundcard is PCMCIA, so the controller shows up as:

```

06:01.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
        Subsystem: Acer Incorporated [ALI] Unknown device 0066
        Flags: bus master, medium devsel, latency 168, IRQ 18
        Memory at b0108000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=06, secondary=07, subordinate=08, sec-latency=176
        Memory window 0: 34000000-37fff000 (prefetchable)
        Memory window 1: 38000000-3bfff000
        I/O window 0: 00001400-000014ff
        I/O window 1: 00002800-000028ff
        16-bit legacy interface ports at 0001

```

I just tried:

```
options snd-sblive index=0 id="MAEM8950" pci=0x00 port=0x1400 irq=18 latency=64 seq_ports=4 max_synth_voices=64 max_buffer_size=128
```

No errors showed up at boot, but I think thats probably because its looking for a different module (?) than snd-sblive? BTW, still no sound with that config ;)

---

### Post by dale_nx26 on 2008-05-10
try this site: [http://linux.iuplog.com/default.asp?item=94639](http://linux.iuplog.com/default.asp?item=94639)

I have the Audigy SE, and I used the last option on that website to fix my sound.

---

### Post by gladstone on 2008-05-11
**@ dale**: Cheers for the link, I tried all the possibilities from there but still no go.

hmm... just noticed this on startup:

```

May 11 15:56:39 xxx-laptop kernel: [    5.639934] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/emu10k1/emu10k1_main.c:765: emu1010: Loading Audio Dock Firmware file failed, reg=0x0

```

---

