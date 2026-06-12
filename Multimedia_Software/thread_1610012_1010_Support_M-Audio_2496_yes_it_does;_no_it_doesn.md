---
title: "10:10 Support M-Audio 2496: yes it does; no it doesn't......"
date: 2010-10-31
forum: Multimedia Software
---

### Post by XEtedBear on 2010-10-31
Reading through the posts here I see there have been many problems with support for this widely used and highly regarded card throughout the life of Ubuntu. Further more, in general the reliable and consistent support for sound is arguably the number one topic of threads across all forum categories. There's clearly a systemic issue here.

Most of the discussion and suggested work-arounds is/are totally above my head - I just want to record and listen to music; I have no desire (or ability) to become some sort of technical guru.

Now I have the same problem (sort of). I moved my M-Audio 2496 to my Ubuntu system. The system failed to recognise it, though I was able to record and playback through it using Audacity - for a day or two; then it was totally quiet.. (And there is no problem at all when I boot to Win/XP - sound works first time every time).

I found a thread that I was able to partially follow; it lead me to a bug report with about 150 comments in it. I followed the advice in comments 54, 63 and 64 and was able to get record and replay using Audacity, again for a day or two.

Now I'm back where I started - the system does not recognise the card - but it does recognise the in-built AC'97 capability on my ASUS A8V board - even though it's disabled in BIOS.

This amazes me: Ubuntu doesn't find a card which is installed, but does find one which isn't! How can that be?


My problem really is that I have become too frustrated by the long history of lack of reliable sound support in all forms of Linux over the years. I first started trying to use Linux in preference to Windows with Fedora 4 - I gave up - too flaky and no sound support. I tried OpenSuse for some years, spending almost 2 years trying to get support for soundblaster to work. Now I have worked through 4 releases of Ubuntu - always with similar issues of unreliable sound support - yes it works; automatic system update; not it doesn't - time and time again.

(In the meantime Win 2k, Win Xp, Win 7 have never given me anything like as many sound card support problems; M-Audio installation has always been trouble free).

There should be a standard procedure for doing PSI on this sort of problem - but I can't find one.

Any advice?

---

### Post by cchhrriiss121212 on 2010-10-31
> Any advice?
Remove/disable pulse audio, or choose a distro that does not use it, like Kubuntu 10.04 or Lubuntu or Crunchbang. 

I had the same issues with a my delta card, and it is down to bad pulse/ALSA integration. When you remove pulse you will have a system that just uses ALSA, and the card will work flawlessly.

The only steps I need to do to set up my card in a non-pulse OS:
1.Install OS
2.Open alsamixer and raise default volume

It really is that simple without pulse.

---

### Post by XEtedBear on 2010-11-01
> **cchhrriiss121212 said:**
> Remove/disable pulse audio, or choose a distro that does not use it, like Kubuntu 10.04 or Lubuntu or Crunchbang. 

I had the same issues with a my delta card, and it is down to bad pulse/ALSA integration. When you remove pulse you will have a system that just uses ALSA, and the card will work flawlessly.

The only steps I need to do to set up my card in a non-pulse OS:
1.Install OS
2.Open alsamixer and raise default volume

It really is that simple without pulse.

The advice is very tempting - I remember concluding that Puleaudio was the source of all the probelms I had in OpenSuse - but I also remeber that some thing didn't work after I disabled Pulseaudio.

What I cannot remember is how to disable Pulseaudio (it was about 3 years ago I was trying that). And if I choose to remove it altogether, how do I do that and is it reversible?

Finally, just to show how really irritating the whole thing is, this evening sound seems to work just fine - and I have made no changes because the system has been powered of all day. I thought computers were bound to act in a consistent way.....

And I also thought that ALSA was the strategic sound architecture for Linux - so why is Ubuntu using Pulse and ALSA?

---

### Post by cek on 2010-11-01
The change to pulse audio was relatively recent (10.04?), prior to that Ubuntu was using ALSA directly, and I never had problems with my M-Audio card.

I have the M-Audio Delta 44 which is a slightly different card, but has the same issues with Pulse Audio.

After following the advice in this link (again, for a delta 44, so you can try it, but YMMV), everything appears to be working well in 10.10.

[http://ubuntuforums.org/showthread.php?t=1468235](http://ubuntuforums.org/showthread.php?t=1468235)

---

### Post by XEtedBear on 2010-11-02
> **cek said:**
> The change to pulse audio was relatively recent (10.04?), prior to that Ubuntu was using ALSA directly, and I never had problems with my M-Audio card.

I have the M-Audio Delta 44 which is a slightly different card, but has the same issues with Pulse Audio.

After following the advice in this link (again, for a delta 44, so you can try it, but YMMV), everything appears to be working well in 10.10.

[http://ubuntuforums.org/showthread.php?t=1468235](http://ubuntuforums.org/showthread.php?t=1468235)

No, I don't think that's going to work - if it is fo different hardware.

Yesterday the system was in 'yes it does' mode. Today it's in 'no it doesn't' mode. That's not only very irritating but it seriously undermines the credibility of the offering, doesn't it? Maybe sound works only on Mondays, Wednesday's and Fridays....?

---

### Post by cchhrriiss121212 on 2010-11-02
> **XEtedBear said:**
> 
What I cannot remember is how to disable Pulseaudio (it was about 3 years ago I was trying that). And if I choose to remove it altogether, how do I do that and is it reversible?

See [here]("http://ubuntuforums.org/showpost.php?p=9969635&postcount=198"), and it is reversible if you just undo the steps.

> why is Ubuntu using Pulse and ALSA? 	
Pulse just adds a nice GUI and some small features on top of ALSA. It is redundant for me but is fine for most users (when it works properly).

---

### Post by tommcd on 2010-11-02
One thing I should have added to this:
[http://ubuntuforums.org/showpost.php?p=9969635&postcount=198](http://ubuntuforums.org/showpost.php?p=9969635&postcount=198)
After removing pulseasudio and gstreamer0.10-pulseaudio, open a terminal and run 
**gstreamer-properties** and set everything to alsa. Running gstreamer-properties may not be necessary. I was running Ubuntu without pulseaudio for a couple months before I found out about it; but running gstreamer-properties ensures that everything is using alsa.

If you ever want pulseaudio back just reinstall pulseaudio.

---

### Post by dangene57 on 2010-11-04
I have finally fixed my sound problem with my m-audio 2496 in Ubuntu 10.10! It took only 2 short lines of code! Thanks be to Alexandre Touret for I am not smart enough to have found the answer myself. Google Bug # 515874 and look for Alexandre's solution. It worked for me. I now have Digital input and Analog output in sound preferences and SOUND! I did not need to add the options snd-ice... line. This was a simple fix even for a newbie like me!

---

### Post by Yellow Pasque on 2010-11-04
> **cchhrriiss121212 said:**
> Pulse just adds a nice GUI and some small features on top of ALSA.

Pulse also replaces ALSA's software mixer layer (dmix) because dmix isn't so good. If you're using a decent audio card with its own hardware mixer, this probably doesn't help you, but if you're stuck with onboard audio (or no hardware mixer-enabled driver), pulse is better (when it works).

---

