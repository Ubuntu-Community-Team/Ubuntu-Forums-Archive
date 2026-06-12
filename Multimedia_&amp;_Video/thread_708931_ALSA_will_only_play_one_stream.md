---
title: "ALSA will only play one stream"
date: 2008-02-26
forum: Multimedia &amp; Video
---

### Post by malfist on 2008-02-26
Alsa is about to drive me insane. I have a chipset that is supported CMI8768 and every time I turn around there is a new problem. I don't want to reinstall my OS like I do with some other well known OS's.
What's happening now:
Alsa will only play one stream. I can have something going on the browser, or Rhythmbox, or MPlayer, or any other sound source. But only one at a time and both have to be shutdown before I can get the other one to work, pausing doesn't work.

Can anyone help me?

---

### Post by simonjcruse on 2008-02-27
same problem here, but different sound card mines the creative live 24bit 7.1 surround. Identical problem. Plz help...

---

### Post by derby007 on 2008-02-27
Did ye try and mess around with the Alsamixer program (run 'alsamixer' from the command line), or select a different device (& settings) in the VolumeControl GUI.

---

### Post by gali98 on 2008-02-27
You could also try a gui mixer.

```
sudo apt-get install gnome-alsamixer
```

This is sometime helpful in figuring out what all the bars are actually for.
Kory

---

### Post by Yellow Pasque on 2008-02-27
Yeah, ALSA is no good for multiple sound streams. That's why Ubuntu 8.04 is going to have PulseAudio on top of ALSA by default.

Of course, my solution was to ditch ALSA entirely and use OSS4, which CAN play multiple sound streams.

---

### Post by malfist on 2008-02-27
> **Temüjin said:**
> Yeah, ALSA is no good for multiple sound streams. That's why Ubuntu 8.04 is going to have PulseAudio on top of ALSA by default.

Of course, my solution was to ditch ALSA entirely and use OSS4, which CAN play multiple sound streams.

Alsa supports more than one stream of sound at the same time in 'software-mixing.' Not only does OSS not, it has became depreciated and was replaced by alsa.

Yes, I've tried alsamixer, that wouldn't effect multipule streams anyway sense that's only volume and some switches. I can get sound just fine with only one stream of sound. Anymore locks alsa.

Malfist

P.S. gnome-alsa mixer comes as part of ubuntu by default. --I think.

---

### Post by Yellow Pasque on 2008-02-27
> Not only does OSS not, it has become depreciated and was replaced by alsa.


Just to clear things up, I'm referring to OSS4, not the old/deprecated OSS3.  OSS4 has vmix for software mixing.

---

### Post by malfist on 2008-02-27
So do you think switching to OSS4 fix the problem? How long and complicated is it, considering I've put probably a total of at least 12 hours (cummulative) on my ALSA issues (resolving, maintanance, tinkering (which may cause the two before)), I don't want to put much more.

How is OSS4 better than OSS3?

---

### Post by Melcar on 2008-02-27
I'm using ALSA and all my apps. work, so it does support multiple streams.  Just make sure nothing in the Sound manager in GNOME, or in the preferences of your individual apps., are linking to the card itself.  Check both the Multimedia Systems Selector and Sound under your Preferences menu.

---

### Post by Yellow Pasque on 2008-02-27
It's not too complicated. I recommend building from source rather than using the .deb procedure I have linked in my sig.

For the ALSA vs. OSS thing, this is good reading [http://4front-tech.com/hannublog/?p=5](http://4front-tech.com/hannublog/?p=5)

And if you get stuck anywhere along the way, good help is available in the OSS forums.

---

### Post by malfist on 2008-02-27
That article is rather bad :P I could tear it to pieces from a logical stand point, not counting the thumping I could give it from my programming experience.

It's extremely biased, presents ad-hoc arguments and false dilemmas, just to name a few. It also seems to like conspiracy theories about how alsa 'forced' it's way into the kernel tree. I'll find other sources.

---

### Post by Yellow Pasque on 2008-02-28
Well, I'm a programmer too. I would much rather use OSS (familiar POSIX C functions) than do kernel-level programming with ALSA

I honestly don't care what sound system you use. (I help people with ALSA issues all the time.) But the bottom line is, I can listen to multiple sound streams with OSS4 and you can't with ALSA, so I think you should reconsider who's really biased here.

> I'll find other sources.
You can lead a horse to water, but you can't make it drink. I just hope you don't pass out from frustration and/or someone guides you to the next watering hole :P

---

### Post by Melcar on 2008-02-28
> **Temüjin said:**
> Well, I'm a programmer too. I would much rather use OSS (familiar POSIX C functions) than do kernel-level programming with ALSA

I honestly don't care what sound system you use. (I help people with ALSA issues all the time.) But the bottom line is, I can listen to multiple sound streams with OSS4 and you can't with ALSA, so I think you should reconsider who's really biased here.


You can lead a horse to water, but you can't make it drink. I just hope you don't pass out from frustration and/or someone guides you to the next watering hole :P

ALSA does do multiple sound streams.  Don't know were you're getting that it doesn't.

---

### Post by Yellow Pasque on 2008-02-28
The OP is not able to listen to multiple sound streams. That was my point, not that ALSA couldn't do it in general.

---

### Post by malfist on 2008-02-28
> **Temüjin said:**
> But the bottom line is, I can listen to multiple sound streams with OSS4 and you can't with ALSA, so I think you should reconsider who's really biased here.

The reason why ALSA cannot play multiple streams is unkown, if it was always like this, I wouldn't be asking how to fix it because there would be nothing to fix!

ALSA supported multipule streams long before OSS did. I would consider the Lead programming of OSS to be more biased than a simple end user who doesn't care as long as it works, wouldn't you?

---

### Post by malfist on 2008-02-28
> **Temüjin said:**
> The OP is not able to listen to multiple sound streams. That was my point, not that ALSA couldn't do it in general.

So you didn't say this:

> **Temüjin said:**
> Yeah, ALSA is no good for multiple sound streams. That's why Ubuntu 8.04 is going to have PulseAudio on top of ALSA by default.

---

### Post by malfist on 2008-03-02
OSS4 gets my channels are mixed up and it most sound I can get nothing out of the center speaker.
I guess this is acceptable until Hardy Heron comes out, I don't feel like doing a clean install right now.

---

### Post by redcrayon on 2008-03-30
Hey guys... i came to this thread to find an answer for my sound having the same issue.
tried oss and alsa... same issue.

I just jumped into system\preferences\sound and changed everything to "PulseAudio sounds server"

Solved my problem that easy...
Movies + mp3 at the same time.

The only issue i have found is that VLC doesnt seem to use pulse audio.
Im going to try read about that now... 

peace

---

### Post by malfist on 2008-03-31
Well, OSS worked fine for a while, but Skype wouldn't use it so I switched back to ALSA and skype still wouldn't work so I tried switching back to OSS and everything broke. Needless to say, I'm on the new beta.

---

### Post by otchie1 on 2008-04-05
> **malfist said:**
> Alsa supports more than one stream of sound at the same time in 'software-mixing.' Not only does OSS not, it has became depreciated and was replaced by alsa.

Yes, I've tried alsamixer, that wouldn't effect multipule streams anyway sense that's only volume and some switches. I can get sound just fine with only one stream of sound. Anymore locks alsa.

Malfist

P.S. gnome-alsa mixer comes as part of ubuntu by default. --I think.

OSS was never 'deprecated'.

OSS was ditched in favour of ALSA for reasons that I for one was never clear about. OSS predates ALSA and used a nice simple /dev/ stream structure. Never did figure out what ALSA uses...hw: something or other. Certainly it wasn't ditched for any lack of technical ability.....Doom3 & ETQW to name but two were written in OSS parlance and require ALSA to run compatibility modules.

I always had better results with OSS and certainly a far richer ossxmix environment on any hardware. Certainly I used to fix ALSA faults by simply installing OSS but then I am old and crusty. :)

---

### Post by feizex on 2008-05-03
Well from my limited knowledge (I am new to linux), OSS was free, then proprietory, that's when ALSA was needed, then OSS became free again with OSS4.

I don't think either of these have the TOTAL solution. 

I tried Alsa. Played with asound.conf and dsnoop / dmix. That was not very productive. I managed to share an input, but only at a fixed sampling rate.

I did some searching and found OSS4. It does seem to share alot better. Multiple programs playing sounds. But I still have issues with it. Can't seem to record with it.

I am now on to trying pulseaudio.

BTW, you can get an OSS version of Skype. Google skype_static-2.0.0.68-oss

Regards,
Feizex

---

