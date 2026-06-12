---
title: "need help, module configuration for ISA SB16"
date: 2006-04-03
forum: Multimedia &amp; Video
---

### Post by johnpipe on 2006-04-03
Hi, I have a SoundBlaster Value16, ISA, non-pnp. Works on my normal partiton, with these OSS modules:

# insert the sound modules:
#
insmod soundcore
insmod sound
insmod uart401
insmod sb io=0x220 irq=5 dma=1 dma16=5
# do you need MIDI?
insmod opl3 io=0x388

What I need is help on what modules, and their arguments, are needed to do the equivalent under alsa? I know that I need to install the alsa OSS package, as it doesn't seem to be installed by default in breezy.

If anyone can help in translating the above to the equivalent "snd-" modules, please do.

Thanks in advance,

 johnpipe

---

### Post by FarEast on 2006-04-04
Hi Johnpipe;) ,

Here is a success story...
[http://ubuntuforums.org/showthread.php?t=127402](http://ubuntuforums.org/showthread.php?t=127402)

Other items may be similar to ones of oss driver.
[http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Vibra16X.&chip=sb16&module=sb16](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Vibra16X.&chip=sb16&module=sb16)

---

### Post by johnpipe on 2006-04-06
Thanks, FarEast, but unfortunately snd-sb16 crashes x; it may be that I need snd-pcm1-oss to prevent this, but can't find it.  Will have to do a new post asking how to get it, I've installed everything PCM/386 shown in sysinstall and still no pcm1!

Thanks,

Johnpipe

---

### Post by FarEast on 2006-04-06
What do you mean by 'snd-sb16 crashes x'?  Do you mean that the volume applet on the upper panel is disabled?

And I think that the module you need is '[COLOR="SeaGreen"]snd-pcm-oss[/COLOR]' which emulates OSS API.

---

### Post by johnpipe on 2006-04-08
"FarEast 	What do you mean by 'snd-sb16 crashes x'? Do you mean that the volume applet on the upper panel is disabled?"

What happens is, if snd-sb16 is enabled in /etc/modules, then the ubuntu login screen appears with a "drumroll" sound; approximately 8 seconds after login, the mouse and keyboard freeze, and the desktop never appears.

"And I think that the module you need is 'snd-pcm-oss' which emulates OSS API."

The alsa info at [http://www.alsa-project.org/alsa-doc...16&module=sb16](http://www.alsa-project.org/alsa-doc...16&module=sb16)
specifically calls for "snd-pcm1-oss" for configuring for the Vibra16 which is what I have ; I've seen howto info around that specifically says DON'T use "snd-pcm-oss".  The  possibility is that 'pcm1' may be available, but only by building  a custom kernel; since this is a default ubuntu install, the kernel sources are not installed so I can't check this (I may get inspired to install them just to check this out).

snd-pcm-oss does not help with this card so far.  Also, I don't know enough abou

Thanks, johnpipe

---

### Post by FarEast on 2006-04-08
> What happens is, if snd-sb16 is enabled in /etc/modules, then the ubuntu
> login screen appears with a "drumroll" sound; approximately 8 seconds after
> login, the mouse and keyboard freeze, and the desktop never appears.

Oh... that's too bad:-k 

Please note that documents on the web of ALSA have not been updated recently, while the way the system configures devices has been changed a lot.

Speaking about sound devices, new users who try to install Linux on an old-fashoned machine with an ISA sound chip are often complaining about the difficulty.  All I can advise them is to try loading the appropriate module with parameters found in success stories.

---

### Post by johnpipe on 2006-04-11
[QUOTE=FarEast]> What happens is, if snd-sb16 is enabled in /etc/modules, then the ubuntu
> login screen appears with a "drumroll" sound; approximately 8 seconds after
> login, the mouse and keyboard freeze, and the desktop never appears.

Oh... that's too bad:-k 

Please note that documents on the web of ALSA have not been updated recently, while the way the system configures devices has been changed a lot.

Speaking about sound devices, new users who try to install Linux on an old-fashoned machine with an ISA sound chip are often complaining about the difficulty.  All I can advise them is to try loading the appropriate module with parameters found in success stories.[/QUOTE]


You've raised valid points, and it gets right to the problem; it's difficult to know what should be expected to work when documentation is outdated.  

The crashing problem might have something to do with having to use a third-party driver for my ATI 3D Mach II, as X.org doesn't support older video cards; I found that if I disabled snd-sb16 for boot-up, and modprobe'd it after login, it would lock-up X once a sound was played, oh well!

I briefly considered a new, cheap SoundBlaster Audigy SE from Staples, but the box says "Minimum Requirements 1GHZ Pentium"!

Fortunately, it isn't mandatory for me to get sound working on Ubuntu on this box, it was originally installed for practice, and to see what it was like, and now I use it for reference (I need to provide support for the ubuntu install on my son-in-law's computer, he decided he was ready to try something else after various problems with WinXP!). 

Thanks very much for the input,

Johnpipe

---

### Post by FarEast on 2006-04-11
Hi Johnpipe,

> You've raised valid points, and it gets right to the problem; it's difficult
> to know what should be expected to work when documentation is outdated.

As most PCI/USB audio devices are configured automatically now, few users need to read documentations about how to configure their audio devices.  I think it is the reason that the docs have not been updated.

One more thing... ISA sound chips often seem to have less capability than what they have under Windows.  So the time to spent in trying to configure them may be 'watste of time'.  With a USB port, a brief solution for users of old-fashoned machines is to buy a cheap USB speaker, etc.

> I need to provide support for the ubuntu install on my son-in-law's
> computer, he decided he was ready to try something else after various 
> problems with WinXP!

I hope he will enjoy Linux ;) .

---

