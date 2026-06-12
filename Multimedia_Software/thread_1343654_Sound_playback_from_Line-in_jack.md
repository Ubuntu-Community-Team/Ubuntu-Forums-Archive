---
title: "Sound playback from Line-in jack?"
date: 2009-12-02
forum: Multimedia Software
---

### Post by etienne@Rofti on 2009-12-02
Hi!

I had no problem in the past to play sound through my speakers from the line-in input on my inbuilt Intel soundcard.

However, since I upgraded to Karmic Koala, I have not been able to replicate this, probably due to the dependance on PulseAudio. I have played around in the PulseAudio mixers, but have not been able to work out how to get playback from either the Microphone or Line-in inputs.

Does anyone by any chance know what I'm doing wrong?

Thanks!
Etienne

---

### Post by OolongBrothers on 2009-12-06
Hi etienne@Rofti,

this is actually not a problem with PulseAudio (but it's always easy to suspect that one isn't it ;) ). Monitoring your audio input at the output is a functionality your soundcard offers. Hence it is controlled on the alsa driver level. The functionality is neither actually gone from alsa. The problem is that the new gnome-volume-control applet is currently not offering a way any more to configure the input monitoring.

There is already a bug on Launchpad to make Ubuntu devs aware of that lack. I added a comment there with a workaround to get monitoring going for the time being, until we get the functionality in the volume applet. Please go there and mark that the bug affects you too and perhaps add a comment. So we drum up some attention to the issue and perhaps get the fix in the next release.

The bug report can be found here: [https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/486164](https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/486164)

Regards, Alex

---

### Post by etienne@Rofti on 2010-01-03
Thanks, Alex! At least I know now that there is a possiblity for it to work! Since I am really into sound manipulation and music editing, this will help me greatly, since I cannot yet afford proper music hardware!

---

### Post by etienne@Rofti on 2010-01-06
Hey, Alex...

Your workaround using the "alsamixer" app did not work for me... Am I doing something wrong do you think?

Or perhaps my computer's current semi-broken status (I can only log in to GNOME-Failsafe at the moment) has something to do with it? (The broken status of my computer can be seen at [http://ubuntuforums.org/showthread.php?t=1369528](http://ubuntuforums.org/showthread.php?t=1369528) )

Thanks!

---

### Post by markbuntu on 2010-01-06
There is a pulseaudio module called module-loopback that will enable you to do what you want. It is not enabled by default in Karmic. It is pretty simple and easy to get it working. There is a thread around here about that...stand by..

ahh here it is:

[http://ubuntuforums.org/showthread.php?t=1324135](http://ubuntuforums.org/showthread.php?t=1324135)

---

### Post by etienne@Rofti on 2010-01-07
Thanks for the link, markbuntu...

Unfortunately none of the solutions at that thread seemed to help me. Any other suggestions, anyone? I would really like to be able to solve this...

Thanks in advance!

---

### Post by markbuntu on 2010-01-07
You can get the gnome-alsamixer from the repo and see if it gives you the controls you need. It tends to have more controls than the volume control in the panel so give it a try. It may be that the line in is muted or a switch is set wrong, gnome-alsamixer will let you find that out.

---

### Post by OolongBrothers on 2010-01-12
I had problems with the alsamixer at first because I did not understand that I had to unmute the input channel. But otherwise I don't know what could go wrong in setting up the input monitoring.
Hm, if none of the alsamixers work for you, you might have some other problem there. No clue really what that could be. Not sure if the Failsafe mode makes a difference for sound. Otherwise your sound works fine and as expected?

Funky stuff anyways.

-Alex

---

