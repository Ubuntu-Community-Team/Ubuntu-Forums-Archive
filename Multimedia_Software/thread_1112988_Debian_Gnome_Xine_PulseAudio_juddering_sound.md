---
title: "Debian Gnome Xine PulseAudio juddering sound"
date: 2009-04-01
forum: Multimedia Software
---

### Post by Manu311 on 2009-04-01
Hi,

I upgraded my Debian System to PulseAudio, I used to use Alsa only before.
It nearly perfectly worked, but I'm also used to Amarok, and Amarok uses Xine.
The problem is: each new media the Xine Engine plays is juddering while the first ~5 Secounds. It also happens with gxine, and gstreamer-xine.
I thought I maybe evade it in amarok and installed yauap engine (never heard about it ^^) and it does realy work this way.
But I'm used to use xine engine in amarok and like having everything working perfect (its linux, not windows ^^).
So I hope someone here has a solution, because google don't have :(.

Btw:
I raised the priority (nice) of pulse, xine and amarok - nothing helped :(.
If it matters:
I'm using the actual builds of each package and Debian Squeeze. And ofc Gnome.
Xine worked before I installed pulseaudio, but not even pasuspender fixes the problem (pasuspender does what it should, but doesn't fix the problem).

---

### Post by markbuntu on 2009-04-01
Hmm, someone was just somplaining about this exact problem in the pa mailing list. Lennart thinks it is an xine-alsa problem since one user had the problem when xine played through alsa and the other user did not using the pulse native driver. 

Do you have xine set to use pulseaudio?

You can try changing the number of audio buffers and/or changing the priority of the decoders in the xine preferences.

---

### Post by Manu311 on 2009-04-02
> **markbuntu said:**
> Hmm, someone was just somplaining about this exact problem in the pa mailing list. Lennart thinks it is an xine-alsa problem since one user had the problem when xine played through alsa and the other user did not using the pulse native driver. 

Do you have xine set to use pulseaudio?

You can try changing the number of audio buffers and/or changing the priority of the decoders in the xine preferences.


xine works well without pulseaudio installed.
I tried very much different settings in pulseaudio and xine including buffers and priorities.
I meanwhile reinstalled debian because I thought maybe it's because of something I installed before.
Result:
I installed Debian Lenny with only base-packages and:
apt-get install gdm pulseaudio totem-xine xineui (and ofc all depencies)
It sounds horrible.

I'll return to alsa now (reinstalling Debian again) because I had an other, much worse problem - the sound others hear from my microphone (skype, mumble, ts, ventrilo) is that much juddering that no1 even understand if I say "hi".
I'll wait till it's standard for a Debian Release. Alsa isn't that bad, is it?
Anyway if some1 find a solution, I'll give everything a try.

---

### Post by eye208 on 2009-04-02
I switched from Ubuntu to Debian last weekend. The fact that Debian does not include PulseAudio by default is a big plus in my opinion.

---

### Post by Manu311 on 2009-04-02
> **eye208 said:**
> I switched from Ubuntu to Debian last weekend. The fact that Debian does not include PulseAudio by default is a big plus in my opinion.

Debian includes nearly nothing. Thats the reason I started with Debian - not with Ubuntu.
But the Ubuntu Community is huge, and the Debian Community not existant? ^^

---

### Post by markbuntu on 2009-04-02
Well, I am having no problems with Amarok and pulseaudio in Ubuntu hardy, intrepid and jaunty and Mandriva....and debian squeeze is not exactly stable and uses pulse0.9.14 which is not exactly stable either. 

You should file a bug report at debian.

---

### Post by eye208 on 2009-04-03
> **markbuntu said:**
> and debian squeeze is not exactly stable
It's not supposed to be stable. Lenny is.

> and uses pulse0.9.14 which is not exactly stable either.
I doubt that there has ever been a stable version of Pulse.

Debian uses PulseAudio only if the user installed it. And that makes it infinitely more stable than Ubuntu where Pulse is installed by default.

What the Debian devs seem to recognize is that a component which offers features demanded by 5% of users should not be forced upon the remaining 95% if there is a remote chance of the component causing trouble.

---

### Post by Manu311 on 2009-04-03
The Version info: 0.x means it's not stable. So there is no stable pulseaudio.

And I know Squeeze is not stable - its testing. But even if it's testing it works very well. I tried booting a ubuntu live cd and hoped there will be pulseaudio preinstalled. But I'm unable to make it boot ^^. After 40 Minutes (or 2000.xxxx secounds) loops trying to start X i gave up. I guess it uses the old nvidia drivers which don't support my geforce 8600GT which isn't the newest one ^^. So I can't test it. I think my onboard nvidia soundcard is just not supported yet.

---

### Post by eye208 on 2009-04-03
Try booting the disc in safe graphics mode. That should make X use the VESA driver which works with all graphics cards.

---

### Post by Manu311 on 2009-04-04
> **eye208 said:**
> Try booting the disc in safe graphics mode. That should make X use the VESA driver which works with all graphics cards.

Sry I have Debian, so my Safe Mode is console based. Anyways, why should my graphic make pulseaudio juddering? That's not logical - so it won't work in linux (maybe it would in windows ^^).

---

### Post by eye208 on 2009-04-04
> **Manu311 said:**
> Sry I have Debian, so my Safe Mode is console based.
I was talking about the Ubuntu Live CD that you said you could not boot.

> Anyways, why should my graphic make pulseaudio juddering?
I don't think that the graphics card is causing it.

---

