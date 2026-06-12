---
title: "problem with microphone on HP t645uk"
date: 2006-11-07
forum: Multimedia &amp; Video
---

### Post by andy101 on 2006-11-07
Hi

I just realised I posted this in the wrong place, so I am posting it here in the correct place in the hope the people who know about these things might be reading this forum.

I have asked about this problem several times, where is the best place to seek help? forums, mailling list (ubuntu-users), IRC? too many choices, how are people meant to know which support method to use?


I have a HP Pavilion t645uk with Ubuntu Linux 6.06 installed.

My computer has two sets of sound connections, one at the front and one at the back.

the rear set has audio out, line in and microphone sockets, the front has headphone, line in and microphone sockets.

The microphone socket on the front of the machine won't work. No sound is recorded from it when I connect my microphone. 

The rear socket works fine but is inaccessible, and as its a headset mic the headphone cable won't reach to the front (the rear audio goes to the monitor).

The front socket works fine in Windows (but I would rather not have to use windows)

My sound is provided by onboard RealTek ALC650 6-channel audio CODEC
subsystem (AC'97 2.2 compliant)


System Details:
[HP Pavilion t645uk web site ](http://h10025.www1.hp.com/ewfrf/wc/product?lc=en&cc=us&dlc=&product=433051&)

[Motherboard Spec](http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&cc=us&dlc=&product=433051&docname=c00063272)

[PC Spec (PDF)](http://h10032.www1.hp.com/ctg/Manual/c00243431.pdf)

the wiki suggested checking /proc/asound/cards this contains
```

0 [ICH5           ]: ICH4 - Intel ICH5
                    Intel ICH5 with ALC650F at 0xfebff800, irq 209

```

arecord shows the following devices:
```

$ arecord --list-devices
**** List of CAPTURE Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
 Subdevices: 1/1
 Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 1: Intel ICH - MIC ADC [Intel ICH5 - MIC ADC]
 Subdevices: 1/1
 Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 2: Intel ICH - MIC2 ADC [Intel ICH5
- MIC2 ADC]
 Subdevices: 1/1
 Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 3: Intel ICH - ADC2 [Intel ICH5 - ADC2]
 Subdevices: 1/1
 Subdevice #0: subdevice #0

```
Should it be listed 4 times? Is that once for each of the line in and
headphone sockets?

lspci -v gives:
```

0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER
(ICH5/ICH5R) AC'97 Audio Controller (rev 02)
       Subsystem: ASUSTeK Computer Inc.: Unknown device 8095
       Flags: bus master, medium devsel, latency 0, IRQ 209
       I/O ports at d800 [size=256]
       I/O ports at dc00 [size=64]
       Memory at febff800 (32-bit, non-prefetchable) [size=512]
       Memory at febff400 (32-bit, non-prefetchable) [size=256]
       Capabilities: <available only to root>

```

ALSA's website suggests I need the snd-intel8x0 module.
lsmod lists snd_intel8x0 as already loaded.

Any ideas on how I can fix this, or find out whats wrong with it?
Any help gratefully received.

What further information should I be providing, any output from other commands needed?

Thanks
Andy (in need of help)

---

### Post by mafitzpatrick on 2006-11-07
Hi Andy, I saw your post about this post on the Ubuntu UK list.

The downside with specific hardware problems like this is it's incredibly unlikely somebody has experienced the same issue & even more unlikely someone knows how to fix. I haven't found a solution for you, but hopefully something to send you in the right direction...

> **andy101 said:**
> Hi
I have a HP Pavilion t645uk with Ubuntu Linux 6.06 installed.
My computer has two sets of sound connections, one at the front and one at the back.

It's strange that these aren't hard-wired together in some way - I would have thought that would make most sense.  In effect you've got stereo MIC input then?

> My sound is provided by onboard RealTek ALC650 6-channel audio CODEC
subsystem (AC'97 2.2 compliant)
card 0: ICH5 [Intel ICH5], device 1: Intel ICH - MIC ADC [Intel ICH5 - MIC card 0: ICH5 [Intel ICH5], device 2: Intel ICH - MIC2 ADC [Intel ICH5
- MIC2 ADC]

So at least you know it's being picked up by the system then.

After all this I suspect the problem is actually just telling the application which mic to source the input from. Looking <a href="http://www.linuxtv.org/v4lwiki/index.php?title=Talk:Em2820&printable=yes">here</a> found me this example for capturing TV:

```
mplayer -zoom -ao sdl -tv driver=v4l2:amode=1:input=0:norm=PAL:alsa:outfmt=yuy2:adevice=hw.0:forceaudio:immediatemode=0 tv://

```
Of course, this is possibly hugely irrelevant, but the important bit there is adevice=hw.0.  In this instance you would be using hw.1 or hw.2 to select the appropriate microphone.  I'm not sure if you can do this without setting up the appropriate video stuff, but it might make a good test if you can.

Without knowing what you're trying to use the microphone for I can't give much more help, but hopefully this has got your started.

---

### Post by andy101 on 2006-11-08
I have found the cause of the problem, I'm an idiot.

Although a checked volume of mic and mic boost and capture where enabled I failled to select 'Mic2', mainly because this page is hidden in volume control program.

Solution:
Open gnome-volume-control, go to edit -> preferances,
scroll down the long list till you get to 'mic select' and check that box.
Now go to options and choose 'mic2' not mic1.
Oddly the rear socket appears to still work with mic2 selected.

Sorry to have wasted your time.

---

### Post by mafitzpatrick on 2006-11-08
> **andy101 said:**
> Sorry to have wasted your time.

Not at all, glad you got it sorted!

---

