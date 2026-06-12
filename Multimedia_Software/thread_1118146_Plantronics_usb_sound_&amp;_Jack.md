---
title: "Plantronics usb sound &amp; Jack?"
date: 2009-04-06
forum: Multimedia Software
---

### Post by siabost on 2009-04-06
Hi,
Packard Bell EasyNote Laptop F5280HR
Celleron 2.8Ghz
768Mb Memory Installed (64Mb of this used for graphics)
SiS built-in soundcard loading AC97 driver.
Kernel 2.6.24.24-rt

Loaded Ubuntu 8.04.2 (with difficulty) then added Ubuntustudio soundsystem (keeping the standard Ubuntu desktop).

I can get the soundcard to work under 2.6.24.24-generic but not under -rt. The quality of the sound & the signal to noise when it does work is awful in anycase so I am looking into a USB soundcard option.

I have a Plantronics USB headset which works on the laptop under 2.6.24.24-generic for general use but I cannot get it to work with Jack nor at all under 2.6.24.24-rt!

This headset set is my tester, if you like, to see if I can get usb sound to work before buying a dedicated usb soundcard.

The laptop is to be used as an synthesiser/instrument so semi-decent & reliable sound quality is a must.

Why have I the problems with the real-time kernel?
How do I configure Jack to recognise a usb sound output device?

I can work with the generic kernel if I have to as there seems to be no noticeable latency whilst playing live.

Many thanks in advance.

---

### Post by markbuntu on 2009-04-07
You need to select the usb headset in the jack control setup Input and Output. click on the > and it should be listed there.

Is jack setup to use rt?

---

### Post by siabost on 2009-04-07
Hi markbuntu,

I will try that jack control setup for the usb headset.

The -rt kernel kills my sound right away but maybe it comes back if I tick Real Time in jack. I will try that also.

Jack allows me to select real time when I use the -generic kernel but I don't know if this makes any difference.

Thanks much. I will let you know how I get on.

---

### Post by siabost on 2009-04-07
Hi,

Thanks, I now get sound via the usb headset. It breaks up a little sometimes and must be something to do with rt as it's a lot worse when Realtime is deselected in Jack.

The above is all with the generic kernel. With the realtime kernel Alsa fails to load and I cannot select any output in jack.

The rt kernel seems to perform ok on my desktop but doesn't seem to like this laptop!

Any help appreciated.

Thanks

---

### Post by markbuntu on 2009-04-07
That is weird. jack will not start with rt selected if there is no rt kernel so maybe your grub menu.lst is mixed up. There is more about setting up and using jack here, near the bottom


[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

