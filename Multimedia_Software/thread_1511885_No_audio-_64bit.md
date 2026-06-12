---
title: "No audio- 64bit"
date: 2010-06-17
forum: Multimedia Software
---

### Post by MDCCCX on 2010-06-17
I posted a while ago, but I've reinstalled since and figured I'd start a new post.
Since getting Ubuntu I've been having intermittent problems. This time however, it all seemed fine until today. I started up my computer and had no audio.
My user is in the audio group and I have updated to the latest ALSA.

aplay -l returns no sound card found.

Thanks for any help.

---

### Post by MDCCCX on 2010-06-17
Update:
I ran an audio test and got sound output. The script told me to raise master and PCM volume. However when I try to launch alsamixer I get
> jamie@jamie-desktop:~$ alsamixer
cannot open mixer: No such file or directory
any ideas?

Edit: I got it going with sudo. However all levels were at 100%. Still no soundcard with aplay however alsamixer did see it. Another note, I cant shut down my system from the menu I have to use the command line. Is this more than a sound problem?

Edit II:
After playing with sudo some more
sudo aplay -q question.wav produces sound output.
> 
jamie@jamie-desktop:~$ sudo aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0which makes me think it might be a group problem?






Solved:
/ect/group should read:
> audio:x:29:pulse,usernameand NOT
> audio:x:29:pulse:username

---

