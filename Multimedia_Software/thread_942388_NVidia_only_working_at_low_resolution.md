---
title: "NVidia only working at low resolution"
date: 2008-10-09
forum: Multimedia Software
---

### Post by Tybear241083 on 2008-10-09
Hi everyone...

I just installed Ubuntu on my new PC last week and have been tearing my hair out ever since to try and get two things. 1280x1024 resolution on my screen and 5.1 surround sound.... even if it would just give me the same thing out of the 5 and at least a peep out of the .1.

Anyway, I installed ubuntu, I enabled the nvidia accelerated graphics driver. I have installed nvidia-settings. the problem is that I can't access all of the buttons in nvidia-settings cos the res is too low. the window just jumps up and down without doing anything.

I have tried editing the xorg.config file manually but the problem is that it will adjust the res of the windows but the reast of the stuff is huge.

Do you think that getting a low end graphics card could get it to work better?

my specs are

Intel core 2 Duo. BioStar mother board. Nvidia 7050/nforce610i chipsets. I also have a sound card C-Media 7838. my LCD is a samsung SyncMaster 720N.

Thanks to anyone that is able to help

---

### Post by xc3RnbFO8P on 2008-10-09
Try:
atl+f2
gksudo displayconfig-gtk
see if your screen is suported, if not,
choose Generic
and resolution that your monitor supports.

---

### Post by Tybear241083 on 2008-10-09
You're a genius. I have been struggling with this thing for a week and a half now. one command. are you kidding me?

Anyway, it worked!!!!! I am so happy. any ideas about how to configure my sound card?

Thanks again

---

