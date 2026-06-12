---
title: "ShockWave Flash removing sound"
date: 2013-02-23
forum: Multimedia Software
---

### Post by xxnomyxx on 2013-02-23
Hello,

I've been attempting to fix this problem for the best part of two days. Despite this problem being present for a number of months.

The problem started when I updated my laptop. I know the problem is shockwave flash for a fact, not my speakers or any other fault. 
Youtube videos will only work if I "Pop out" the video frames.

The music player will play music and films etc.

I've read through multiple guide claiming they have the "fix" for the issue when they clearly done. I've re-installed flash and installed alternatives. However non has worked.

Any advice would be appreciated.

12.04 (32 bit)

---

### Post by sirriffsalot on 2013-02-23
What did you update? Are you running pulseaudio, alsa, jack?

---

### Post by xxnomyxx on 2013-02-23
Hello,

Keeping in mind I've had this problem for quite a while. 
But I believe it's pulseaudio, as I've seen that in the terminal before.

---

### Post by sirriffsalot on 2013-02-24
Edit: Just to be clear, how exactly did you install flash? You need the  restricted-extras package for Ubuntu along with the Adobe Flash plugin  for Mozilla (just use firefox for now to find the issue if you aren't using it at the moment).  Go to the Software Center and get ubuntu-restricted-extras and Adobe  Flash plugin and try that first in case you haven't before you do the  below! Important that you get the Ubuntu-restricted and not Xubuntu or Kubuntu :)

All I can advise from this is that you install pavucontrol (PulseAudio Volume Control) from Synaptic Package Manager or Software Center, or a terminal if you please: 

```
 sudo apt-get install pavucontrol 
```Then open up the control and see if you can work a solution there - I'm being very obvious because I don't know much of what you have tried.

If this fails, try to remove pulseaudio altogether, just to see if that's the problem. Follow this link -- [http://ubuntuforums.org/showthread.php?t=1313253](http://ubuntuforums.org/showthread.php?t=1313253) -- and see if the ALSA sound architecture which it has you replace pulseaudio with gives you any sound watching flash videos.

Keep me posted and apologies for late reply!

---

### Post by xxnomyxx on 2013-02-26
I tried all the steps you said, same result currently.

I have no idea what's causing the problem. When it stopped playing sound in youtube/flash websites was a few months ago when I updated by "Update Manage"

---

### Post by sirriffsalot on 2013-02-26
Do you really need the updates you did? If not, I'd suggest saving some time by reverting back to a point where it works, and test every now and then to see if it "fixes itself" (developers fixes the error somehow). If not after a while, file a bug report and they'll get you through the steps to finding the cause nitty-gritty-style.

Just to make sure that hardware is not broken, install QJackCtl, and hence jackd etc, which is a different sound server. Click the setup button of QJackCtl, go to misc and tick the "run script on startup" and type in the field next to it "killall pulseaudio -9". If it starts successfully, see if you can route some sound or other to your speakers?

---

