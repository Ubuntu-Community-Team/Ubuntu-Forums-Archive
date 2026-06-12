---
title: "Listening to music in Mythbuntu = low volume"
date: 2009-05-01
forum: Mythbuntu
---

### Post by mode on 2009-05-01
Hi all,

I just got my mythbuntu install up and running.  Please keep in mind that I'm capable of following instructions but I'm barely functional (without a quick google search) in this environment.  

In any case, I've been searching all over the forums / internet and can't seem to find an answer to the following.

Essentially, if I boot my system and watch a video, the volume is great (100%).  However, as soon as I flip over to listen to music, the volume is reduced dramatically ... almost inaudible.  In order to resolve this, I have to close mythbuntu and run aslamixer and boost the master volume from 70% to 100%.  Then, I do "sudo alsactl store"

Once I do that, I can watch as many videos as I want, however, as soon as I open the music player (from within MythBuntu), the volume drops again.

Can anyone make a few suggestions on what I'm doing wrong?  I'm currently running a Dell Optiplex 745 w/ Intel integrated sound and an ATI 2400 XT.  I didn't make any changes during the installation and accepted most (if not all of the defaults).

Thanks in advance :-)

---

### Post by kadafi69 on 2009-05-02
check in the general settings, the page for audio settings, there will be master setting and pcm i think, (also see if the internal audio is selected) the TV works on one and music player seems to work on the other, so it might be that master is at 100 but pcm is at 50, if so pull the lower one up and check that.

one problem that I have experienced is that, while I have the audio at and acceptable level, my remote wont change the volume in the audio player. but it works for tv. if I change the settings around the problem switches around.

hope this helps in some way.

---

### Post by mode on 2009-05-02
> **kadafi69 said:**
> check in the general settings, the page for audio settings, there will be master setting and pcm i think, (also see if the internal audio is selected) the TV works on one and music player seems to work on the other, so it might be that master is at 100 but pcm is at 50, if so pull the lower one up and check that.

one problem that I have experienced is that, while I have the audio at and acceptable level, my remote wont change the volume in the audio player. but it works for tv. if I change the settings around the problem switches around.

hope this helps in some way.

Wow ... somehow I missed that setting.  I always figured MythTv was linked to the volume within the mixer.  

Thanks for your help.

---

