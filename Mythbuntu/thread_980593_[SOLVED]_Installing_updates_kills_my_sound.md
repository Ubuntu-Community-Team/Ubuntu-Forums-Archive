---
title: "[SOLVED] Installing updates kills my sound"
date: 2008-11-13
forum: Mythbuntu
---

### Post by Meph1st0 on 2008-11-13
After installing 8.10 my sound works fine.  As soon as I install all the updates my sound stops working.  I found a script to run that basically runs a diagnostic and then uploads the results to the alsa website.  It provided me a link so that I can use it in my post. Here it is [click here]("http://www.alsa-project.org/db/?f=31349939419b0cff3e377708fc04f43f818d99aa")

Also, when I look at the sound settings in xfce settings manager everything is blank under the default device (when there was items to check before the update).  If I look at the volume control window the window is blank except for the menu bar at the top.  If I go to the terminal and run alsamixer I get an error message that says, "alsamixer: function snd_mixer_load failed: Invalid argument"

Doing a search in Google for that error message I find a number of posts about certain linux kernels that don't work and being related to the amd64 distros (I am running the 64 bit version of mythbuntu 8.10).  The resolution to those posts are that they just reverted back to an older kernel but I don't know how to do that.

Also, searching for common sound problems in this forum revealed that some people found issues with the 177 version of the nvidia restricted drivers. [click here]("http://ubuntuforums.org/showthread.php?t=966956&highlight=sound")  They reverted back to 173 and they got their sound back.  I did the same but I still did not get my sound back.

Other posts mentioned that they had to make sure that master and pcm were activated in the sound settings.  I can't do this as the window is literally blank and I can't open alsamixer.

Anyway, I could just format and reload and avoid updating my software until a later date when the problem could be potentially fixed but I like to keep my machine updated as much as possible.  I'm learning now this might not be the best thing to do.  Any help on this would be appreciated.  Thanks.

---

### Post by Meph1st0 on 2008-11-23
I never did figure out how to get my sound working, but by moving to the 32 bit version of mythbuntu this particular sound issue went away.

---

### Post by linuxishard on 2008-12-03
this happens to me to, my sound works great until updates, all i can do is re-install, the first time this happened all i had to do was remove alsa re-boot and re-install it, but this time its really killed my sound for good, cant even detect my soundcard, 

please some one help me, my laptop is really quite a pain to setup after re-install, i really dont wanna have to do this everytime,

if anyone needs and output report or somethin just let me know and tell me how, i think i mite just re-install now though, get it over and done with, i really should use the x64 installer too, but i only got the i386 disk.

hope someone can help, 

thanx

---

### Post by linuxishard on 2008-12-31
still not sure what my issue was really,every update after fresh installs killed my sound beyond any seemingly reasonably fixable nature, but after a few days of trying my problem just stopped, my thought is that a bugged update perhapse that was fixed, who knows, sound works great now though,

one thing i have noticed though.. the alsa volume output is much quieter than my typical windows volume output, even with all levels up at their max, the volume is never as loud, 
anyone have a clue why, or better yet, how to squeez a bit of extra volume out of my alsa output?

---

