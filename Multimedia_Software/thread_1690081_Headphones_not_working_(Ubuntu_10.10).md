---
title: "Headphones not working (Ubuntu 10.10)"
date: 2011-02-17
forum: Multimedia Software
---

### Post by LHC2009 on 2011-02-17
Hey guys and girls :)

I've been trying to get my headphones to work on my dell studio xps 1640 and now I'm pretty much frustrated...Just not working...I haven't muted them or anything...Checked the settings in the "sound" menu under prefrences...checked with the terminal command alsamixer...nothing muted...
When I don't have 'em plugged in, the sound works perfectly via the built in speakers...as soon as i plug them in, the sound stops (which i believe to be the correct behavior in this situation) but then the headphones just remain silent (which is NOT the correct behavior :D ). Maybe this will provide you guys with the necessary info to help me out:
[http://www.alsa-project.org/db/?f=d082f89dbef70aa29e840254aa0c7537aa59f3b7](http://www.alsa-project.org/db/?f=d082f89dbef70aa29e840254aa0c7537aa59f3b7)

Thanks in advance!

Best Regards!

Edit: Forgot to mention: The Headphones are to be connected via a regular audio jack...NOT Usb...

---

### Post by BicyclerBoy on 2011-02-18
Have you tried using the pulse audio mixer control ?
pavucontrol

This seems to allow a bit more control.

Is there a unique module mask for your hardware ?

---

### Post by LHC2009 on 2011-02-19
Thanks for your answer. I've tried using pavucontrol, but it seemed quite okay...didn't see anything muted...
What exactly do you mean by unique mask for my hardware? Thx once again :)

---

### Post by kittkatt on 2011-02-19
Just double check to make sure your headphones work with your cd player or ipod or something.  You may have forgotten to turn the on switch on or maybe your cord got damaged somehow.

---

### Post by LHC2009 on 2011-02-19
I just retested them again...they work fine on the mp3-player and other notebooks (ubuntu and windows)...I'm kinda starting to lose my mind over this issue...really driving me crazy...

---

### Post by BicyclerBoy on 2011-02-19
What I meant was..some hardware, especially laptops & custom mobos in small boxes, can have odd audio connector arrangements. i.e. headphones & mics on different DAC/ADCs to normal. This can require a module parameter to be set to allow the driver to know the diff hardware setup.

A search for your model PC etc did not find anything relevant, sorry..

---

### Post by SleepWalkerX on 2011-02-20
My bro has a Dell XPS Studio 7 and I vaguely recall a similar issue.  Might be the alsa driver.  Try compiling the latest alsa source or grabbing the latest version from one of the ppa's.

---

### Post by tdashroy on 2011-02-22
I also have a Studio XPS 16 and this fix worked for me.

First open your /etc/modprobe.d/alsa-base.conf
```

gksu gedit /etc/modprobe.d/alsa-base.conf

```

Then, at the bottom of the file, add the following:
```

options snd-cpsp index=-2
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=dell-m6
options snd-hda-intel enable_msi=1

```

Save the file and reboot your computer.

Now, I'm not sure if I have the Dell XPS Studio 1640 or the 1647. The guide is for the 1647, but I think it's probably at least worth a shot for you to try it.

For anybody else that is having problems but with different hardware I found this fix here: [http://doc.ubuntu-fr.org/audio_intel_hda](http://doc.ubuntu-fr.org/audio_intel_hda).

---

### Post by offensive on 2011-03-18
i had to change modprob.d in the afformentioned instructions to "modprobe.d"

gksu gedit /etc/modprobe.d/alsa-base.conf
otherwise, i was pasting into a blank file

worked like a charm though, thank you much for posting this fix

---

### Post by tdashroy on 2011-03-18
Oh yeah...whoops sorry about that. I fixed the post, thanks :)

---

### Post by lidex on 2011-03-19
Could one of you guys do me a huge favor? For that model I have the fix as simply:
```
options snd-hda-intel model=dell-eq
```
If you would comment out the added lines in alsa-base.conf and add this one, reboot and check your audio devices I would greatly appreciate it.

---

### Post by pt2000 on 2011-07-15
Thanks tdashroy! Your solution (editing alsa-base.conf) worked perfectly for me: Ubuntu 11.04, Dell XPS 1647.

---

