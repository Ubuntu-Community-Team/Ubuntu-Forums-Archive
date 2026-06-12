---
title: "Ubuntu Audio through HDMI on HTPC"
date: 2010-02-28
forum: Multimedia Software
---

### Post by adacosta on 2010-02-28
I am currently running Intel DG45fc Mobo.  works great with Ubuntu thus far.  However when connecting to my LCD through HDMI I can not receive any sound.  

Anyone come across this issue?  any help is greatly appreciated!

Cheers,
AD

---

### Post by jweaver28 on 2010-03-02
I have the same problem, and my posts on other threads haven't been answered. I'm hoping that by replying to posts like yours, maybe someone will notice. Hope springs eternal!

---

### Post by adacosta on 2010-03-02
Just got it fixed!

here is the link the HTPC-Linux Forum for Ubuntu on [AVS]("http://www.avsforum.com/avs-vb/showthread.php?p=18230928#post18230928").  that I go an answer on.  Basically here is what i needed to do:

First, unmute the IEC958  channels:
open terminal
type "alsamixer"
scroll all the way to the right (off screen probably) and unmute the  IEC958 channels using the m key, it will then show a '00' to represent unmutued.
close terminal

then go to Sound Settings under system>>preferences>>sound settings 

go to the output tab,. then under the drop down menu choose the HDMI interface...


and that worked for me!

---

### Post by jweaver28 on 2010-03-02
I'm glad you found a solution for your problem. However, it doesn't work for mine. Typing alsamixer in terminal produces: alsamixer: function snd_ctl_open failed for default: Invalid argument

---

### Post by farbird on 2010-03-02
pls show us your output after typing this

```


aplay -l


```

> **adacosta said:**
> I am currently running Intel DG45fc Mobo.  works great with Ubuntu thus far.  However when connecting to my LCD through HDMI I can not receive any sound.  

Anyone come across this issue?  any help is greatly appreciated!

Cheers,
AD

---

### Post by farbird on 2010-03-02
if there are any hdmi devices listed in the output of "aplay -l"

then do the following...

the output shd tell u what card number and device number of the hdmi

with the card and device number..

just do this if the hdmi device is card0 and device3

```

speaker-test -D plughw:0,3 -c2


```


*edited speaker-test command*
previously misspelled as speakertest

---

### Post by adacosta on 2010-03-02
farbird,

i was able to get mine to work through alsamixer, however just as I am learning some of these commands... would you mind explaining what the the two above commands actually do?

Cheers,
AD

---

### Post by adacosta on 2010-03-02
> **jweaver28 said:**
> I'm glad you found a solution for your problem. However, it doesn't work for mine. Typing alsamixer in terminal produces: alsamixer: function snd_ctl_open failed for default: Invalid argument


I cant help you to much as I am quite the noob on Ubuntu, and have not done cli since college, however here are two resources to help you with either fixing alsamixer or installing a like application.

Application: Amixer
[http://www.linuxquestions.org/questions/debian-26/alsamixer-command-line-arguments-376678/](http://www.linuxquestions.org/questions/debian-26/alsamixer-command-line-arguments-376678/)

Alsamixer fix?: 
[http://forums.fedoraforum.org/showthread.php?t=95284](http://forums.fedoraforum.org/showthread.php?t=95284)

let me know if this helps.. I will follow the error to the end with you as i want to fully understand the issue.

TD

---

### Post by adacosta on 2010-03-02
> **jweaver28 said:**
> I'm glad you found a solution for your problem. However, it doesn't work for mine. Typing alsamixer in terminal produces: alsamixer: function snd_ctl_open failed for default: Invalid argument


Jweaver, also, you can install alsa-utils via the synaptic PackageManager >>system>>administration>>Synaptic Package Manager


search for alsami...  and you will see alsa-utils come up... is it installed?  if it is mark for update/reinstall... if its not, install it.. then try the above commands. again.

hope this helps.

TD

---

### Post by Thallid on 2010-03-02
> **adacosta said:**
> Just got it fixed!

here is the link the HTPC-Linux Forum for Ubuntu on [AVS]("http://www.avsforum.com/avs-vb/showthread.php?p=18230928#post18230928").  that I go an answer on.  Basically here is what i needed to do:

First, unmute the IEC958  channels:
open terminal
type "alsamixer"
scroll all the way to the right (off screen probably) and unmute the  IEC958 channels using the m key, it will then show a '00' to represent unmutued.
close terminal

then go to Sound Settings under system>>preferences>>sound settings 

go to the output tab,. then under the drop down menu choose the HDMI interface...


and that worked for me!
Anybody got a CLI-version of this?

I've got a G43 with HDMI. aplay -l recognizes a HDMI output device, but the sound wont go through it. How do I define which device to be used by ALSA?

I'm running Ubuntu Server, so I won't be able to do the "sound settings"-trick. :(

Grateful for any help I can't get, this is getting on my nerves.

---

### Post by farbird on 2010-03-03
aplay -l

shows the sound hardware in the system

speaker-test is a script to output a buzzing sound on the system.

the parameters -D plughw:0,3 means to play the sounds on card0, device3.

to find out which numbers to use, aplay -l will show the devices present.

the parameter -c 2 means to output 2 channels sound..
ie the speaker-test will play left and right channels separately...

btw, thallid,

u might want to write a .asoundrc file..



> **farbird said:**
> if there are any hdmi devices listed in the output of "aplay -l"

then do the following...

the output shd tell u what card number and device number of the hdmi

with the card and device number..

just do this if the hdmi device is card0 and device3

```

speaker-test -D plughw:0,3 -c2


```

---

### Post by jweaver28 on 2010-03-03
Thanks adacosta for replying. I don't want to mess up your thread, but I've tried those solutions. Unfortunately, the problem doesn't seem to be with alsamixer, which is installed (and reinstalled). The problem seems to be that lscpi shows both my MB onboard sound and the ATI all-in-wonder card, but aplay either shows no devices, or after reinstalling alsa utils as you suggested, shows

ALSA lib conf.c:1589:(snd_config_load1) _toplevel_:7:0:Unexpected end of file
ALSA lib conf.c:2850:(snd_config_hook_load) /home/j/.asoundrc may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2714:(snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3079:(snd_config_update_r) hooks failed, removing configuration
aplay: main:608: audio open error: Invalid argument
.
Frankly, I'm a noob too, having mostly used ubuntu for the past couple of years from dual boot PCs. And problems like this keep me from using that boot more, despite my appreciation of ubuntu's speed and relative safety.

---

### Post by sam.reader on 2010-03-03
I have got the same problem with my laptop.
I am using a HP pavilion DV6 1154tx model
I got all the connections right and even the output sound settings are perfect as have made them just as you gave
Please help me:)

---

