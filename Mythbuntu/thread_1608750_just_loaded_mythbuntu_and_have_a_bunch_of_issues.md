---
title: "just loaded mythbuntu and have a bunch of issues"
date: 2010-10-29
forum: Mythbuntu
---

### Post by troypearce on 2010-10-29
I took the plunge after crashing my win xp snapstream while installing a hd homerun and figured if I am going to have to wipe it clean I should try myth tv.    I am a newbie to linux but I am persistant and fairly tech savy..

I just installed the new mythbuntu and have gone through the wiki insallation manual to configure front and backends, using mostly the default settings.

my system
asus m4a77td motherboard
amd quad core processor
newer nvidea vid ard HDMI ot sure what model)
using the computer as a front/backend

hdhomerun 
hdovr

my logs here [http://mythbuntu.pastebin.com/AJXgxc6u](http://mythbuntu.pastebin.com/AJXgxc6u) using the log grabber(kind a cool if I got it right)

my problem is that while i have tried changing settings I am not able to view tv and from the info on the front end it appears that the hd homerun and the hdpvr are not working even though i have run through the config for each of them.

I go to watch tv and I get the old test pattern for a few seconds then back to the front end screen.

I would greatly appreciate any help, but please remember I am a complete newbie and if you could give me as much direction as possible.:confused:

Thanks so much

---

### Post by LowSky on 2010-10-29
Hi welcome to the forums.

EDIT: I read your system logs and the info was there

Nvidia 210
HDPVR model 4902
neither model should cause issues. 

The Nvidia 210 might be using the wrong setting for VDPAU, try Slim. That might be one fix.

I took a look a the the logs a bit more and I'm thinking its an issue with folder permissions. Did you set a certain folder for recording to instead of the defaults? If yes its not a big deal you just need to fix that folders permission to be used by the mythtv group

Also change your theme or install the package named:  ttf-mscorefonts-installer, you are trying to use a font that doesn't exist on the system. or so its says in the logs.

---

### Post by troypearce on 2010-10-29
Thanks lowsky,

changed the vdpau to slim and hanged the theme,  but could not find the file permissions.... thought i stayed with the defaults.  Where would i find them.... sorry but this is so foreign to me at this point.

I tried again with the changes that you suggested but still tv will not start.... it says wait and then goes back to the front end screen.

you probably don't need them but here are my logs
[http://mythbuntu.pastebin.com/21nuuJHX](http://mythbuntu.pastebin.com/21nuuJHX)

thanks
Troy

---

### Post by LowSky on 2010-10-29
Please review your setups, maybe something was done wrong.
[http://www.mythtv.org/wiki/Hauppauge_HD-PVR](http://www.mythtv.org/wiki/Hauppauge_HD-PVR)
[http://www.mythtv.org/wiki/Silicondust_HDHomeRun](http://www.mythtv.org/wiki/Silicondust_HDHomeRun)

file permission would be done from outside Mythtv. Mythtv backend hold the locations for file recording (option 5 I believe) in the set up process, normal location is /var/lib/mythtv/LiveTV for live tv



* also in frontend theme setting change from Qt to OpenGL, that way it uses your nvidia card and not the processor

---

### Post by nickrout on 2010-10-29
it's pretty hard to read log files that long. Try and look at the mythfrontend.log and mythbackend.log at the point where you start trying to watch.

However I do note this:
```

#
2010-10-29 11:30:22.578 Channel(/dev/video0)::Tune(): Error -1 while setting frequency (v2): Invalid argument
#
2010-10-29 11:30:22.615 TVRec(1) Error: Failed to set channel to 897. Reverting to kState_None
#
2010-10-29 11:30:22.648 TVRec(1): Changing from WatchingLiveTV to None
#
20
```

Are you really trying to watch channel 897?

---

