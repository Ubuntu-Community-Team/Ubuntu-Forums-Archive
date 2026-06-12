---
title: "[SOLVED] JACK distortion when adding usb harddrive"
date: 2007-07-09
forum: Multimedia Production
---

### Post by distort on 2007-07-09
Hi,

I'm running a native Ubuntustudio in low-latency mode with JACK on a Pentium D 805 2,6 GHz (2 cores) machine with 2 GB of DDR2 RAM in dualchannel mode.
My Audiointerface is an RME Hammerfall LE 9636 which is clocked by an external AD/DA interface via ADAT @96 kHz.
I did install the closed Nvidia driver, and there were more xruns without it.
For no xruns to happpen during production (not starting programs), i have to run JACK at 512 frames/period 2 periods/buffer resulting in a latency of 10.7 msec.

Is this normal? cause I heard of people with USB interfaces running at 1.3 msecs with no xruns and  lesser processing power.

When I connect, switch on and mount an external HDD with FAT32 via USB2.0 while JACK is running, any sound is totally distorted so that I have to restart JACK to go back to normal sound.
Should I file a bug report regarding this? If so, where?

regards,

d.

---

### Post by zettberlin on 2007-07-09
> **distort said:**
> Hi,

For no xruns to happpen during production (not starting programs), i have to run JACK at 512 frames/period 2 periods/buffer resulting in a latency of 10.7 msec.

Is this normal? 


No - with your equipment you should be able to run the session with 128/5,8 ms perfectly flawless.
 But mind the nature of the xruns you get: are they from the alsa-backend or from jackd? How many you have per houre? And most interesting: are they periodically(exactly every 10 min that is...)?
In my experience 4-8 xruns/houre do not hurt too much. If my session has not much more. I cannot hear any errors in recorded material....

> **distort said:**
> 
When I connect, switch on and mount an external HDD with FAT32 via USB2.0 while JACK is running, any sound is totally distorted so that I have to restart JACK to go back to normal sound.
Should I file a bug report regarding this? If so, where?

regards,

d.

Try it ;-)
But to me, all this sounds a bit like conflicting IRQs and/or improper prioritysettings for the IRQ you soundcard uses. The card should have its own and it should be set to 9,10 or 11.

---

### Post by distort on 2007-07-09
d

---

### Post by distort on 2007-07-09
thanks for your reply.

according to /proc/interrupts the hammerfall has irq 20, and it isn't shared with another device.
does a lower irq number mean higher priority?

---

### Post by fredj on 2007-07-10
When you say you are running with low latency do you mean you are using the low latency kernel?
If so you will get much better performance with the realtime kernel (see the Sticky at the top of this
forum) once you have configured it properly. You talk about mounting your usb drive, do you mean plugging
it in while jack is running. If so plug it in before you start jack or stop jack and restart it. Xruns don't
matter too much unless they happen while you are recording audio, so don't do anything else while you
are recording. If other programs are allowed to interrupt jack for a long time then it can loose track of
the audio stream that is why the realtime kernel is important.

---

### Post by distort on 2007-08-13
Thanks for pointing out that there's a difference between the "low latency" and "realtime" kernels. I'm installing the realtime kernel at this moment. Let's see how it works.

To my usb problem: it happens when I insert the switched-on drive into the usb port while JACK is running. Or when I switch on the drive that is plugged in my usb port while JACK is running.

And there are not only xruns, but it distorts _all_ audio currently happening, so that I have to restart jackd to be able to listen to it again (i don't do recording, so I can't elaborate on that).

---

### Post by fredj on 2007-08-16
Yes when something crashes jack the only way to recover often involves a
complete restart. The answer to this is don't install Usb drives while using jack.
However see how you get on with the low latency kernel and running jack
under realtime mode first.
Do you know the tweaks to the limits.conf file that you need to enter for best
performance? If not, post again.

---

### Post by distort on 2007-08-29
I've installed the realtime kernel and yes, the usb problem went away.
Thanks again for this hint!
I can run Jack at a much lower latency now (2.6 ms) after having applied the tips on this site:

[http://tapas.affenbande.org/wordpress/?page_id=40](http://tapas.affenbande.org/wordpress/?page_id=40)

However, each time I change a tab in Firefox or copy a large file, Xmms playback skips a bit, but resumes normally after the skip. I have to run Jack at ~20 ms latency to achieve stable background playback with Xmms.
Maybe it's because I'm using the proprietary Nvidia drivers for my 7600gs graphics card?

There are the following three lines at the end of my limits.conf:

@audio - rtprio 95
@audio - memlock 512000
@audio - nice -19

I have confirmed that my user is  in the audio group.

Are there any other things I could try to tweak? Maybe lowering the IRQ of the graphics card?

---

### Post by fredj on 2007-09-01
Firefox isn't well behaved as far as sound goes. I don't think your
video drivers are a problem. In the end it all depends on how powerful
your PC is and how well the Operating system shares out resources.
Under the realtime kernel it is possible to use Ubuntu as a stable multi-
track recorder but you shouldn't expect to be able to run other
programs like Firefox at the same time.
In Ubuntu as in xp or VISTA you can achieve stable audio playback by
increasing the buffers and the latency. This is fine for a multi-media
machine but not ideal for an audio workstation where low latency is
important.

---

