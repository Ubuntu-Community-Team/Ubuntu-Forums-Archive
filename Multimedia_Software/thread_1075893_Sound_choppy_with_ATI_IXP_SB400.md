---
title: "Sound choppy with ATI IXP SB400"
date: 2009-02-20
forum: Multimedia Software
---

### Post by griffi on 2009-02-20
I recently loaded Intrepid on a Toshiba laptop with and ATI IXP SB400 sound card. Each sound is choppy and drawn out. Nothing I have done has been able to affect the sound. Has anyone else had that experience?

---

### Post by g0nzo on 2009-04-27
I've just installed Jaunty on Toshiba with the same soundcard and got exactly the same problem - I can hear some sound, but it's stuttering.

Any ideas how to fix it?

---

### Post by Swankyman on 2009-04-30
Please someone tells us how to fix this. 

I've been trying for ages with atiixp. 

I get sound playback for around ten seconds and then it crashes. It then plays a stuttering echo sound foreverrrrrrrr!!!

:confused:

---

### Post by Swankyman on 2009-05-04
Ok,

I've now got sound working with ATIIXP

Pulseaudio is the problem

heres how to get rid of the problem (not sure if all the steps are required though!)

Ignore A, because B and C remove the need for pulseaudio

[COLOR=Red]A)In a terminal copy and paste this:

sudo gedit /etc/pulse/daemon.conf

Go right to the end of the file and make sure there are semicolons (;) in front of these two lines 

;default-fragments = 2
;default-fragment-size-msec = 5

save the file[/COLOR]    

B)Copy and paste this to the terminal:

gstreamer-properties

and change both the input and output plugins to ALSA

C)In the menus go to the System -> Preferences -> Sound 

Make sure all the device options are set to ALSA (mixer = Alsa-mixer)

Then reboot and hopefully everything should work 

:popcorn:

does for me. Unless its one of the millions of other things I tried :(

---

### Post by Deathhunt on 2009-05-13
So, I followed all the instructions here. It did not fix the problem it just kinda improved it. Instead of the echo going on and on and on forever it ends after a few seconds. I'm on a Toshiba Satellite L25-S121 with Jaunty. Same sound card.

Please Help Going Crazy!!!
-DH

---

### Post by Deathhunt on 2009-05-13
Its back to going on forever.

---

### Post by BornOle on 2009-06-01
Hi guys,

Did you find a solution to this? I tried the fix provided by Swankyman with no success.

Edit: I also gave some things in the Comprehensive Audio Guide a shot, no go either.

---

### Post by chochem on 2009-06-21
After starting a new thread on the same issue, I got some information that prompted me to speculate that this was a SB400-specific issue and then google-stumbled my way to this thread.

I posted a fairly detailed specification of the problem (useful if a bug report needs to be filed, I guess) [here]("http://ubuntuforums.org/showpost.php?p=7489133&postcount=1").

I've gathered a collection of bookmarks that may or may not be relevant. If you wish to investigate:
[http://ubuntuforums.org/showthread.php?t=365342](http://ubuntuforums.org/showthread.php?t=365342)

[http://ubuntuforums.org/showthread.php?t=1097434](http://ubuntuforums.org/showthread.php?t=1097434)

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

[http://ubuntuforums.org/showthread.php?t=1130384](http://ubuntuforums.org/showthread.php?t=1130384)

[https://answers.launchpad.net/ubuntu/+question/59335](https://answers.launchpad.net/ubuntu/+question/59335)

[http://translate.google.com/translate?hl=en&sl=it&u=http://forum.ubuntu-it.org/index.php%3Ftopic%3D294568.msg2153704&ei=sEo-SomLLoLJ-Qbwj72tBQ&sa=X&oi=translate&resnum=2&ct=result&prev=/search%3Fq%3Dsb400%2Balsa%26hl%3Den%26sa%3DN%26tbo%3D1%26start%3D60%26tbs%3Dqdr:y](http://translate.google.com/translate?hl=en&sl=it&u=http://forum.ubuntu-it.org/index.php%3Ftopic%3D294568.msg2153704&ei=sEo-SomLLoLJ-Qbwj72tBQ&sa=X&oi=translate&resnum=2&ct=result&prev=/search%3Fq%3Dsb400%2Balsa%26hl%3Den%26sa%3DN%26tbo%3D1%26start%3D60%26tbs%3Dqdr:y)


I only booted into Ubuntu to review the problem, and now I can't get it to appear. Isn't that just typical... :o

---

### Post by chochem on 2009-06-22
**[COLOR="Red"]EDIT: This is NOT a fix and I doubt that it really changes anything. Please see post below.[/COLOR]**

Okay, I've got a hint of an idea of what might be a fix. The reason for my optimism is that I started a playlist nine hours ago and it's still playing now without hickups. If anybody wants to help with testing it, here's what I've done:

[LIST=1]
[*]Uninstalled pulseaudio (this probably isnt necessary in the long run but for simplicity's sake...): sudo apt-get remove pulseaudio.
[*]Blacklisted the pc speaker module and the modem module. This means adding the following to /etc/modprobe.d/blacklist ```
blacklist snd-atiixp-modem 
blacklist snd-pcsp
```
[*]Overwritten /etc/modprobe.d/alsa-base.conf with the following (a forced reinstall of alsa will return things to normal): ```
options snd-atiixp ac97_quirk=alc_jack
options snd-atiixp ac97_codec=0

```
[/LIST]

Of all these things I really only believe that the line 'options snd-atiixp ac97_codec=0' is needed but for completeness sake, I've listed all the changes I've made. Please post if this accomplishes anything on your laptop.

In my limited understanding of linux audio, this doesn't really make sense, as the modules are autoloaded once and should either work or not in which case there should be no audio at all. This has also been the case in some older posts dating back to 2006-7 which inspired adding the module options. But if it works, why argue?

---

### Post by chochem on 2009-07-16
I feel by now reasonably certain in saying that the only final fix for this problem is a kernel upgrade. I have tested this idea first by installing karmic koala (9.10) which uses 2.6.30, secondly compiling a kernel from source on an 'old' 9.04 system and finally installing the resulting package on a fresh 9.04. All three systems had working audio with no other alterations.

So for anybody still looking for a fix, I think I can say that those are your options. Either/or:
[LIST=1]
[*]'Upgrade' to karmic (which is alpha and therefore full of bugs)
[*]Compile your kernel from source. I spent an evening with this and found it far easier than I had feared. There is a nice tutorial here to get you started: [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)
[*]Find somebody who is compiling 2.6.30+ kernels and maintains a repository of them (and trust that (s)he means well and knows what (s)he is doing).
[/LIST]

---

### Post by Mandala 13 on 2009-07-29
Chochem, for the time being, you're GOD. For me, at least, hehe.

I was thinking about what you suggest, and obviously doing to Karmic Koala wasn't a real option unless nothing else would work. Downgrading to Hardy, where I do have sound 100% to perfection, wasn't an option either, because on 8.04 I have serious graphic and performance problems. 

So, I spent this whole day compiling. Let's say that I even had a lot of fun doing it. First compiling didn't work and I got myself worried about .deb files not appearing. Risked a bit of work time and did it again. Second time, everything was just too perfect. 

Changed Sound Preferences to ALSA, reboot, took my time to choose the 2.6.30.3 kernel version in the GRUB (just to be sure) and well... What can I say? I have been doing a lot of sound stuff (games, youtube, music, and more) and sound is still working, perfectly. I have even been able to hear sounds playing music and playing at the same time, and that's just the Trial of Fire for my ATI, hehe.

So, today my friend Chochem, you're my special divinity. You got sound working on Jaunty, after my months and months of deppresion. Hope that this would work for the rest of you that still have no sound in their ATI's.

---

### Post by R.M. on 2009-08-03
I tried everything, even installing OSS version 4, which replace all alsa drivers and pulseaudio too, and still i got the problem with sound.

I compiled a new kernel from the upstream sources and then i got no more problem with the sound, like chochem suggested, and then i got no more problems with the sound.

Furthermore, i installed a developer version of alsa and pulseaudio (on my custom kernel), has indicated on this blog:

[http://izanbardprince.wordpress.com/2009/03/26/how-to-fix-ubuntu-jaunty-warning-hacks-ahead/](http://izanbardprince.wordpress.com/2009/03/26/how-to-fix-ubuntu-jaunty-warning-hacks-ahead/)

But something curious happened... I booted with the old ubuntu generic kernel, and the sound seems to be working fine here?!?! No hanging or other problems.

I'm running some tests here to see if the sound still working and stable for a long period of time.

So, maybe, a simpler solution is to install the experimental version of ALSA and pulseaudio, indicated on that blog, instead of build the kernel from the upstream sources.

---

### Post by igorzwx on 2009-08-03
[COLOR=#980101]**[ubuntu]**[/COLOR] 			 			[How to remove PulseAudio and fix sound with ALSA and ESound]("http://ubuntuforums.org/showthread.php?t=1230561")
[http://ubuntuforums.org/showthread.php?t=1230561](http://ubuntuforums.org/showthread.php?t=1230561)

[B]Audacity works (playback and recording).
VLC works.
Skype works too.

[/B][State of sound in Linux not so sorry after all]("http://insanecoding.blogspot.com/2009/06/state-of-sound-in-linux-not-so-sorry.html")

---

