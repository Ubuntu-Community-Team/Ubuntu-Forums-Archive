---
title: "HowTo make ALSA (sound) work after upgrading to Fesity 7.04!"
date: 2007-04-22
forum: Multimedia &amp; Video
---

### Post by oleoleole on 2007-04-22
It doesnt seem to be a bug, but just a new/updated configuration file.

What you need to do, is to backup your old config files:
```
cd ~
mv .asoundrc .asoundrc.bak
mv .asoundrc.asoundconf .asoundrc.asoundconf.bak
```

Then you run:
```
asoundconf list
```

Find your default sound card, and then run:
```
asoundconf set-default-card <sound card device>
```
ex:
```
asoundconf set-default-card CA0106
```
or
```
asoundconf set-default-card ICH5
```
or other sound devices you might have.

You can also run "asoundconf" in sudo also to make it default in "root", ex:
```
sudo asoundconf set-default-card CA0106
```

asoundconf should now have created two new configuration files in your home folder. You can check it by this command:
```
ls ~/.asoundrc*
```
This should display the files you backed up, including the new ones, and you can also check if the configuration file is empty or not, do this command:
```
cat ~/.asoundrc.asoundconf
```
Then you should get some output, and also see that your soundcard have been selected as default.

Restart any application using sound devices, and it should work. If not, try a simple reboot (should be unecessary).

This worked for me after upgrading from Kubuntu 6.10 to 7.04.

---

### Post by osarusan on 2007-04-24
Thank you SO MUCH!!!!!! :KS 

I went through pages and pages of stuff on this problem, and saw countless posts in the forum that went unanswered. I've been working on this for 3 hours, despite the fact that my sound worked just find last night!

Your simple, simple instructions fixed everything. Thanks a million times!

---

### Post by digbybare on 2007-04-24
I don't seem to have an .asoundrc in my home directory. When I run asoundconf list, nothing happens. Alsamixer also doesn't seem to work, I keep getting the following error: alsamixer: function snd_ctl_open failed for default: No such device.

Any ideas?

---

### Post by SB42 on 2007-04-24
**digbybare**

You may want to try the link below.  I bet your sound card is not being recognized.

[http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449")

Thanks **oleoleole**, this fixed my sound issues.

---

### Post by boarderpatrol on 2007-04-24
Thanks a bunch Oleo!!!  

  All of a sudden my sound in Feisty stopped working tonight.  I followed your post an

    BAM!!

   sound is up an running again.  I would not known how to fix this. Great community here


regards

---

### Post by techristian on 2007-04-25
I'm still not getting any sound. Under system I NOW have OSS PCM and ALSA drivers listed for   VIA V8237 AC97  !! 

Dan

---

### Post by Steve H on 2007-04-25
Wiil doing this help to get rid of the poor performance of ALSA when running VLC?

I keep getting clicking and popping with sounds when watching DVD with VLC, but not when I run Amarok. If i switch to the OSS driver i don't get the same problems.

---

### Post by cudjoe on 2007-04-25
Thank you so much oleoleole !!

I add a problem with additional users in Feisty. Contrary to the installation user, they had the wrong default sound card (even though it was correctly set in System > Prefs ).
I therefore copied .asoundrc and .asoundrc.asoundconf files to each newly created users, and they now have sound on the right default sound card !

Excellent !

---

### Post by jmar71n on 2007-04-25
Thank You!!!

My sound only worked with OSS, and only one app could use the sound card it at a time.
Anyway i did what you said, and now using ALSA and sound works perfectly.

Thank YOU again

---

### Post by PleaseEnjoyThis on 2007-04-25
I honestly can't thank you enough!  I am waaay noob and your steps were very easy to comprehend and fallow.  I'd hug ya if I could.  :P take care!

---

### Post by oleoleole on 2007-04-25
> **PleaseEnjoyThis said:**
> I honestly can't thank you enough!  I am waaay noob and your steps were very easy to comprehend and fallow.  I'd hug ya if I could.  :P take care!

Just come to Fredrikstad in Norway (about 100km south from Oslo:P) and you will receive a hug, hehe;o)

---

### Post by NoTiG on 2007-04-26
sweet this solved my problem . thanks! . should be stickied

---

### Post by Artorius on 2007-04-26
I am running Fiesty on an IBM Thinkpad 600e, my audio controller is a cirrus Logic CS 4610/11 [CrystalClear Sound Fusion Audio Acelerator] (rev 01)

When I enter asoundconf list I dont get any sound cards listed, and when I try the first step in this tutorial I get `.asoundrc': No such file or directory.

Any help would be greatly apreciated, btw I wasnt able to get sound working with edgy either.

---

### Post by rollinc on 2007-04-26
Yeah! Thanks for the post!

---

### Post by viz_e on 2007-04-27
Very good. This solved my problem. I still think that this is a bug though, because I didn't have any file to backup (after upgrade from edgy)...

---

### Post by Grenrose on 2007-04-27
God thank you, i was afraid nothing was going to work.

---

### Post by Rhapsody on 2007-04-28
> **oleoleole said:**
> ```
cd ~
mv .asoundrc .asoundrc.bak
mv .asoundrc.asoundconf .asoundrc.asoundconf.bak
```

I'm not sure where "cd ~" was supposed to take me, but I ended up in my /home directory, and neither of those files are there ('mv' produced errors on both).

---

### Post by Hexydes on 2007-04-28
Wow, that was pretty weak. Ubuntu devs, PLEASE fix this. What a waste of time for such a stupidly simple thing...

Thanks so much Oleoleole. This was driving me up the friggin' wall! :)

---

### Post by oleoleole on 2007-04-28
> **Rhapsody said:**
> I'm not sure where "cd ~" was supposed to take me, but I ended up in my /home directory, and neither of those files are there ('mv' produced errors on both).

"cd ~" is supposed to take you to the home-dir. If you dont have the files, there's no reason to move them either. Then you can just skip that step and continue, but it might be like you're souncard aint supported at all if the files aren't located there. I dunno, I'm not an ubuntu-developer and dunno what they make or do for default setups:P

---

### Post by matsberglund on 2007-04-29
Thank you, tack så mycket, mange takk !! =D>

Not only did this give me the sound back, but it also fixed a colour problem I had with video playback. Great!

---

### Post by viz_e on 2007-04-30
This solved my problem... but only until the next reboot.... After that I lost the sound again and this fix seems not to work anymore... :confused: :confused:

Edit: muting "Headset Jack Sense" did the trick...

---

### Post by heart_reaver on 2007-04-30
:guitar: 

it works......

---

### Post by heart_reaver on 2007-04-30
:(  after reboot it is not working.....

---

### Post by anirban.sam on 2007-05-05
Type alsamixer and press enter in a console to launch alsamixer. Disable all ICE devices in alsamixer and unmute all muted. Save settings by typing "sudo alsactl store".

---

### Post by Boodah on 2007-05-05
I was having a problem getting sound out of my USB Headphones and this solved it! I can't say thank you enough!!!!

---

### Post by AMHA on 2007-05-05
i have a small problem after upgrading to feisty. my speakers (5.1) are not working properly (just 3 of them). they used to work fine in edgy...
my sound card is sagem stac92xx.

is this guide here for me ?? if not please tell me how to fix it? 
thanx in advance

---

### Post by oleoleole on 2007-05-05
> **AMHA said:**
> i have a small problem after upgrading to feisty. my speakers (5.1) are not working properly (just 3 of them). they used to work fine in edgy...
my sound card is sagem stac92xx.

is this guide here for me ?? if not please tell me how to fix it? 
thanx in advance

This is mainly for users who lost their sound completelly due to upgrade. But you can try my step first, if it doesnt work, look somewhere else for your problems and give them some more information.

---

### Post by Selmer79 on 2007-05-05
I did a fresh install of 7.04, and I actually didn't have ANY configs to begin with, but now I have. :) Sound is working as is should have!
Now to maybe install 7.04 64-bit instead.. ;)

---

### Post by andreigbs on 2007-05-05
Hi,

I've also installed Feisty Fawn afresh, so I have no config files stored for sound and at startup it's saying it hasn't found any devices to control.  When typing in alsamixer, here is what it says my card is: HDA ATI SB, Chip: Generic 11c1 Si3054.  My sound was working in Edgy, didn't have ATI video acceleration though.  Now it's the other way around: i have video accel, but no sound.  What else can i try, having already done what the OP said?  Thanks.

---

### Post by rockingmtranch on 2007-05-06
Worked great. Thanks.

---

### Post by tjk on 2007-05-08
> **oleoleole said:**
> It doesnt seem to be a bug, but just a new/updated configuration file.

What you need to do, is to backup your old config files:

```
asoundconf list
```Find your default sound card, and then run:
```
asoundconf set-default-card <sound card device>
```ex:
```
asoundconf set-default-card CA0106
```This worked for me after upgrading from Kubuntu 6.10 to 7.04.

Hey thanks oleoleole!  After weeks of being soundless (after upgrading to Feisty-KDE) you solved my problem.  When using your commands I discovered that I didn't even have any ".asound*" files/folder on my computer.  So all I did was find out my card name, run the default card command (as per above) and everything seems to be back to normal. YES!!! O:)O:):)

---

### Post by divali on 2007-05-10
Thanks this fix worked for me , running Fiesty, I'm very grateful. Thanks again.

---

### Post by DivingWind on 2007-05-13
What a great community! I find here answer to every prob I encounter on Ubuntu!

---

### Post by mattr01 on 2007-06-18
Great HOW-TO!  I got my Plantronics Audio 550 playing music through it!  Although for some reason I can't get the microphone to work.  Can someone help me out?

---

### Post by dpu-ibrown on 2007-06-19
Good looks on the information man, solved the alsa problem right away.

---

### Post by ktucker on 2007-06-25
After trying many suggestions here and having no joy, I found a solution here (not fully tested but so far I can at least play sounds now):
[http://ubuntuforums.org/showthread.php?t=433514&highlight=cannot+hear+sound+in](http://ubuntuforums.org/showthread.php?t=433514&highlight=cannot+hear+sound+in)

Briefly, change the permissions of devices listed in /dev and /dev/snd

cd /dev
ls -l /dev/* | grep audio

and then for each one 'chmod 666 <name>'
e.g. 
sudo chmod 666 dsp

---

