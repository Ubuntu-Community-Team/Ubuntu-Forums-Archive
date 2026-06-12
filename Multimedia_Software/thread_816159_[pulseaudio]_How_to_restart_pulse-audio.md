---
title: "[pulseaudio] How to restart pulse-audio?"
date: 2008-06-02
forum: Multimedia Software
---

### Post by kakyoism on 2008-06-02
When I open my *pavucontrol* interface, it says cannot connect
and my VMWare complained about /dev/dsp busy as well...

How do I restart my pulse-audio??

Thx!

---

### Post by jaygo on 2009-03-14
for the record ...
you can kill pulseaudio by running, as user, not root:
```
pulseaudio -k
```
or 
```
killall pulseaudio
```

```
pulseaudio --check
``` will check if any instances are still running.

Finally, simply start pulseaudio from the run dialog (Alt + F2 by default)

---

### Post by wmatthews on 2011-08-21
Thanks a lot still works in 2011! "pulseaudio -k" not being root user.

---

### Post by sawatdee on 2011-11-23
I ran pulseaudio --kill, as user not root. Then ran ps -A and verified pulseaudio was no longer running. Then I ran pulseaudio --start, as user not root. I can see that it is running now. Still no sound. Linux sound systems have never worked and it stops randomly for no reason at all. The only real solution is to restart the entire system, not much different than Microsoft Windows.

---

### Post by l300lvl on 2011-12-09
While that may be the case for some select few, I think a majority agreed that pulse is the way to go. For instance, pulse can handle many multiple applications through many multiple output variations, I can have different sound playing from 10 different applications on 10 different output devices. What else has that ability, point it out and I might use it.

Thanks for the commands, helped a lot!

---

### Post by mmxbass on 2011-12-12
> **l300lvl said:**
> What else has that ability, point it out and I might use it.Windows and OSX. Just saying...

---

### Post by alexxxm on 2011-12-13
I have the same problem, since recently (I started using Guayadeque in place of Amarok) pulseaudio crashes rather often.
For now I'm using
*pulseaudio >& /dev/null &*

There is a way so that it is automatically restarted once it gets killed?

On a related note (and sorry, I know we are in an Ubuntu forum): somebody knows where - under Fedora fc11 - pulseaudio is launched at startup?

thanks!

alessandro

---

### Post by l300lvl on 2011-12-19
> **mmxbass said:**
> Windows and OSX. Just saying...

Well okay. I was speaking in regards to alternative sound servers on linux. But you have a point, the question would be what you use to achieve this in Windows, not that I will, but I've never seen that ability.

As for OSX, I would gather you mean when the system runs, or once it's booted. Unless you're someone who uses their system 'lightly' because Macs are so delicate.

---

### Post by danteuk on 2012-01-13
pulseaudio stops working for me too at random times.

Sometimes I get warnings and something asking if I want to remove my sound card from the system (most often on login but not every time )! Obviously I don't, I want to use it for sounds!

I have same problems on 3 different machines with different versions of Kubuntu and different hardware.

Today it's done it again on my laptop ( Kubuntu 11.10 ) hence being here looking for a solution ( rather than a single person saying it works for them ).

One of the things I love about Linux is how if something stops working or fails you can just restart that bit, but pulseaudio 
once it fails I have to fully log out and back in, sometimes that doesn't work and only solution is a reboot.

Today my sound stopped again, I tried pulseaudio -k it stopped and restarted pulseaudio ( judge by it's PID ) but still no sound. Worse, when I looked at sound devices it only shows one instead of two. The one being the HDMI one that's no use since I have nothing connected to the HDMI socket. The main Internal sound device that drives the internal speaker and the headphones is gone!!  It was there before I restarted pulseaudio - it just wasn't outputting any sound to speaker or headphones despite the volumes being at max and nothing was muted.
Looks like I'll have to close all my programs and try logging out and back in again!! -- NOT FUN!

---

### Post by MoreOrLess on 2012-01-13
pulseaudio and phonon (the KDE sound system) always seem to have issues playing nice together, though I believe they are fixed in KDE 4.7.x. I would try removing pulseaudio and just using alsa.

---

### Post by danteuk on 2012-02-03
Nope, I'm using Kubuntu 11.4 so it's KDE 4.7.4

Sounds works, then it doesn't
Killing pulseaudio sometimes ( 1 in 5 ) helps - it auto restarts it's self

most of the time what happens is it just loses my sound card, so it only shows the one ( the wrong one, ie HDMI ! )

Logout and back in normally fixes it.

There MUST be a better fix than that though!!

---

### Post by rex86 on 2012-02-17
Just to note, I also have this problem. As far as I've noticed so far it occurs when I wake up my notebook from sleep.

Sometimes pulseaudio restarts by itself and sometimes it doesn't, so I have to restart it manually.

I believe this is new bug in kubuntu.

---

