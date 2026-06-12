---
title: "VLC audio stutters with PulseAudio"
date: 2008-05-19
forum: Multimedia Software
---

### Post by Aikon- on 2008-05-19
I've been using VLC for a while now because it worked well with video hardware acceleration on my 9600xt (back under Dapper and then Gutsy, Totem always had screen tearing problems, and also video from VLC looks a lot better).

Since the upgrade to Hardy, I've been having a problem with it though.. first, CPU usage is higher than it used to be (sits at ~30% now, used to be down around 10% or so). Totem now seems to run at around 20% CPU, but the video doesn't look as nice, so I've been sticking with VLC. Not a huge issue, but annoying nonetheless.

Second, and this one is an actual problem.. the audio seems to "hiccup". It will run fine for a few seconds (3, 10, 30.. doesn't seem to be a pattern to it) and then there will be a slight stutter, as if the audio pauses for just a millisecond.

I suspect the problem is with the interaction between VLC and PulseAudio.. I've had problems with Pulse before, causing MPD to have very high CPU usage until I explicitly set an output type of "pulse" in the config file.

I have tried setting the PulseAudio output module, but there's no change.

Suggestions?

-Aikon

---

### Post by Aikon- on 2008-05-19
**UPDATE**

Okay.. I'm pretty sure these two problems are related. I disabled the audio in VLC entirely, and the CPU usage returned to the pre-Hardy levels, meaning that the *audio output* from VLC to PulseAudio is consuming ~20% CPU usage, which is completely unacceptable.

As I said, I had a similar problem with MPD, which I solved by adding the following to */etc/mpd.conf* and enabling network access in *paprefs*:

```
audio_output {
	type	"pulse"
	name	"MPD PulseAudio Output"
}
```

Aikon-

---

### Post by rainwalker on 2008-05-19
I just noticed this, too. I don't know if it always did this, or if it's because of what I did by following this thread: [http://ubuntuforums.org/showthread.php?t=776739](http://ubuntuforums.org/showthread.php?t=776739)

---

### Post by Aikon- on 2008-05-20
I have not made any progress and so have filed a (more complete) bug report here:

[https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/232297](https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/232297)

Please contribute if you are experiencing a similar issue.

Aikon-

---

### Post by Artemis3 on 2008-05-20
Its just like you say. As a workaround, I just kill pulseaudio before using VLC (killall pulseaudio), stutter solved.

To restart pulseaudio, do: pulseaudio &

---

### Post by Aikon- on 2008-05-20
> **Artemis3 said:**
> Its just like you say. As a workaround, I just kill pulseaudio before using VLC (killall pulseaudio), stutter solved.

To restart pulseaudio, do: pulseaudio &

This is not a solution, this is a hack. VLC should be able to work just as well with PulseAudio as any other application, such as MPD. I shouldn't have to kill a sound server everytime I want to watch a video, and then re-start it afterwards.

First, I don't want to take the time to do it. I have to open a terminal, enter the commands, watch my video, then remember to re-start the server afterwards.

Second, if I forget to restart it, then I lose the ability to listen to music etc. because all of a sudden I don't have a sound server.

---

### Post by jocheem67 on 2008-05-20
But do you need pulse? I just select alsa or my soundboard and approach it directly. It's easily done from the audio preferences tab.
I'm not too convinced of pulse. Xine based programs won't work at the moment, so to watch a dvd I have to use vlc, which is not my fasvourite program.
Maybe you could also try to not use pulse at all??

---

### Post by Aikon- on 2008-05-20
No, I don't *need* Pulse.. however it has a lot of interesting features, some of which are quite appealing. A lot of people have put a lot of hard work in getting Pulse integrated into Ubuntu, and all indications point towards Pulse being the major sound platform for some time to come.

Instead of trying to fight these efforts by hacking away at my system to revert it to the way it used to work, I would prefer to find solutions to these problems that will help things to work better using the *new* way of doing things.

As I figure things out, I keep records of them.. either making a blog post, or in bug reports, or on these forums etc, so that other people can benefit from the solutions I have found as well. Hopefully at least someone else experiencing similar problems will be able to overcome them as well, or maybe the solution even gets integrated into the next version of the relevant packages etc.

I have workarounds for this issue already, be it disabling Pulse as you suggested, or using a different media player such as Totem or MPlayer, however my preference would be to configure VLC to work *properly* with Pulse. That is the difference between a solution and a work-around.

---

### Post by jocheem67 on 2008-05-22
Okat then, cannot help you here. I'm experiencing a lot of probs using pulse in combi with my maudio delta 1010LT.So I just disabled the whole thing. It's what you say probably, it's for the time to come, not the present and I'm kind of disappointed that canonical decided to implement yet another still buggy framework.
Hardy is supposed to be a LTS OS, but to me it's way from that.
Just my two cents.

---

### Post by Aikon- on 2008-05-22
> **jocheem67 said:**
> Okat then, cannot help you here. I'm experiencing a lot of probs using pulse in combi with my maudio delta 1010LT.So I just disabled the whole thing. It's what you say probably, it's for the time to come, not the present and I'm kind of disappointed that canonical decided to implement yet another still buggy framework.
Hardy is supposed to be a LTS OS, but to me it's way from that.
Just my two cents.

I would agree with you here.. quite a few things that don't seem to be quite ready. It feels like a late-stage Beta.

---

### Post by Zorael on 2008-05-22
Well, LTS means "long term support", not "everything works for everyone without hitches". We're only a couple of months in on the 3 year support period.

That said, I agree it's unfortunate that design decisions made certain stuff included as defaults in 8.04 that seem unpolished, such as Firefox 3.0b5. However, these may be the de facto standards in a couple of months, at which point 8.04 will come across as an up-to-date LTS release, and not an old release with FF2 and without Pulse that people can't wait to replace with 8.10.

---

### Post by chiefci on 2008-05-26
Same problem, since I use Pulseaudio, VLC player works bad. Sounds stottered.
But Kill ist not a solution. I change something in xorg,conf speed flox f.e.
Better now but not perfect VLC player. Totem and SM Player are much better.
I read Bug Report, but lot of people have this problem after change to Hardy.
I work on it.

Chief

---

