---
title: "[No more sound] SIS 7012 / intel8x0"
date: 2008-05-05
forum: Multimedia Software
---

### Post by BOK on 2008-05-05
This issue has been posted MANY times before, but nevertheless...

I had sound working on a previous install of Ubuntu (6.06 did!), but with 8.04 and now back to Gutsy 7.10 (complete clean re-install- **8.04 was crashing too often**) my system keeps silent...
I've tried every possible tweak in /etc/modprobe.d/alsa-base

[FONT="Courier New"]options snd-intel8x0 buggy_semaphore=1 / ac97_quirk=-1,0,1,2,3,4 / etc.[/FONT]

but still nothing...

FYI - see [Pastebin]("http://pastebin.ca/1008701") for extremely detailed output from the tsalsa-script.

I've gone through the "Comprehensive Sound Problem Solutions Guide", but besides getting  a little too long thread, this solved nothing so far.
And as said: Ubuntu was (the first) giving me sound on this piece of hardware (besides WinXP)!

---

### Post by BOK on 2008-05-06
**UPDATE**

[FONT="Courier New"]speaker-test -Dplug:surround40 -c4 -twav[/FONT]
and / or
[FONT="Courier New"]speaker-test -Dplug:surround51 -c6 -twav[/FONT]

**[COLOR="Red"]gives SOUND!![/COLOR]** But... only as "Rear Right" and "Rear Left"... :-k

Is there a way to reroute this to "Front Left" and "Front Right" through e.g. $HOME/.asoundrc?

But nevertheless, a good workaround so far is using this $HOME/.asoundrc:

[FONT="Courier New"]pcm.default     pcm.ch51dup

pcm.intel8x0 {
    type hw
    card 0
}

ctl.intel8x0 {
    type hw
    card 0
}

# for 5.1 speakers
pcm.ch51dup {
         slave.pcm surround51
         slave.channels 6
         type route
         ttable.0.0 1
         ttable.1.1 1
         ttable.0.2 1
         ttable.1.3 1
         ttable.0.4 0.5
         ttable.1.4 0.5
         ttable.0.5 0.5
         ttable.1.5 0.5
}[/FONT]

---

