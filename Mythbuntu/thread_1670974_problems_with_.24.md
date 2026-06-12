---
title: "problems with .24"
date: 2011-01-19
forum: Mythbuntu
---

### Post by simonnev on 2011-01-19
Anybody having problems with .24?

system was running fine then totally screwed up, in the end tried reinstall (with updates) but to no-avail, just get problems ranging from bad dvb-s cards, mythweb not working... nvidia drivers up the wall..

or is it just me ?

mythfrontend version: fixes/0.24 [v0.24-112-g40df4b6]

doing clean install from disk to get hopefully a working sys again.. with no updates from mythbuntu repo's

simon

---

### Post by simonnev on 2011-01-19
Anybody having problems with .24?

system was running fine then totally screwed up, in the end tried reinstall (with updates) but to no-avail, just get problems ranging from bad dvb-s cards, mythweb not working... nvidia drivers up the wall..

or is it just me ?

mythfrontend version: fixes/0.24 [v0.24-112-g40df4b6]

doing clean install from disk to get hopefully a working sys again.. with no updates from mythbuntu repo's

simon

---

### Post by LowSky on 2011-01-19
working fine, with fixes and updates since release of 10.10

---

### Post by simonnev on 2011-01-19
mine was ok then all screwed after updates..
just did clean install 10.10 with .23 on and no problems!
simon

---

### Post by simonnev on 2011-01-19
just done a clean install with 10.10 and myth.23 no problems at all, 
think i will clone my drive before i update to again to .24..

the problem seems to have started when i added a secbackend which was updated to the latest ver on saturday then i updated the masterbackend to the same version. using the mythbuntu repo's 

simon

---

### Post by simonnev on 2011-01-19
just done a clean install with 10.10 and myth.23 no problems at all, 
think i will clone my drive before i update to again to .24..

the problem seems to have started when i added a secbackend which was updated to the latest ver on saturday then i updated the masterbackend to the same version. using the mythbuntu repo's 

simon

---

### Post by simonnev on 2011-01-19
sorry about double posts:confused::o

---

### Post by Chunk of Earth on 2011-01-20
> **simonnev said:**
> Anybody having problems with .24?
.
:
or is it just me ?
mythfrontend version: fixes/0.24 [v0.24-112-g40df4b6]
simon

I am. [http://ubuntuforums.org/showthread.php?t=1632963](http://ubuntuforums.org/showthread.php?t=1632963)
mythfrontend version: v0.24-112-g40df4b6  
(2:0.24.0+fixes.20110119.40df4b6-0ubuntu0mythbuntu2)
(and several prior versions)

It's a combination front end/back end. I've finally resorted to letting the back end handle the recordings and then firing up Xine to handle the playback. The wife is really impressed with that efficient maneuver (not!) The front end is totally useless to me except to when I manage to dredge up a little hope and try some settings changes.
The only "help" I received was to get chastised by the audio developer for changing configuration settings. Apparently, his presumptive code handles everything automagically -- except, oh wait, it doesn't.
My current research involves how to downgrade to .23 now that my database has a newer schema.
Good luck.

---

### Post by Chunk of Earth on 2011-01-20
> **simonnev said:**
> Anybody having problems with .24?
.
:
or is it just me ?
mythfrontend version: fixes/0.24 [v0.24-112-g40df4b6]
simon

I am. [http://ubuntuforums.org/showthread.php?t=1632963](http://ubuntuforums.org/showthread.php?t=1632963)
mythfrontend version: v0.24-112-g40df4b6  
(2:0.24.0+fixes.20110119.40df4b6-0ubuntu0mythbuntu2)
(and several prior versions)

It's a combination front end/back end. I've finally resorted to letting the back end handle the recordings and then firing up Xine to handle the playback. The wife is really impressed with that efficient maneuver (not!) The front end is totally useless to me except to when I manage to dredge up a little hope and try some settings changes.
The only "help" I received was to get chastised by the audio developer for changing configuration settings. Apparently, his presumptive code handles everything automagically -- except, oh wait, it doesn't.
My current research involves how to downgrade to .23 now that my database has a newer schema.
Good luck.

---

### Post by Chunk of Earth on 2011-01-20
> **simonnev said:**
> Anybody having problems with .24?
.
:
or is it just me ?
mythfrontend version: fixes/0.24 [v0.24-112-g40df4b6]
simon

I am. [http://ubuntuforums.org/showthread.php?t=1632963](http://ubuntuforums.org/showthread.php?t=1632963)
mythfrontend version: v0.24-112-g40df4b6  
(2:0.24.0+fixes.20110119.40df4b6-0ubuntu0mythbuntu2)
(and several prior versions)

It's a combination front end/back end. I've finally resorted to letting the back end handle the recordings and then firing up Xine to handle the playback. The wife is really impressed with that efficient maneuver (not!) The front end is totally useless to me except to when I manage to dredge up a little hope and try some settings changes.
The only "help" I received was to get chastised by the audio developer for changing configuration settings. Apparently, his presumptive code handles everything automagically -- except, oh wait, it doesn't.
My current research involves how to downgrade to .23 now that my database has a newer schema.
Good luck.

---

### Post by Chunk of Earth on 2011-01-20
> **simonnev said:**
> Anybody having problems with .24?
.
:
or is it just me ?
mythfrontend version: fixes/0.24 [v0.24-112-g40df4b6]
simon

I am. [http://ubuntuforums.org/showthread.php?t=1632963](http://ubuntuforums.org/showthread.php?t=1632963)
mythfrontend version: v0.24-112-g40df4b6  
(2:0.24.0+fixes.20110119.40df4b6-0ubuntu0mythbuntu2)
(and several prior versions)

It's a combination front end/back end. I've finally resorted to letting the back end handle the recordings and then firing up Xine to handle the playback. The wife is really impressed with that efficient maneuver (not!) The front end is totally useless to me except to when I manage to dredge up a little hope and try some settings changes.
The only "help" I received was to get chastised by the audio developer for changing configuration settings. Apparently, his presumptive code handles everything automagically -- except, oh wait, it doesn't.
My current research involves how to downgrade to .23 now that my database has a newer schema.
Good luck.

---

### Post by Chunk of Earth on 2011-01-20
> **simonnev said:**
> Anybody having problems with .24?
.
:
or is it just me ?
mythfrontend version: fixes/0.24 [v0.24-112-g40df4b6]
simon

I am. [http://ubuntuforums.org/showthread.php?t=1632963](http://ubuntuforums.org/showthread.php?t=1632963)
mythfrontend version: v0.24-112-g40df4b6  
(2:0.24.0+fixes.20110119.40df4b6-0ubuntu0mythbuntu2)
(and several prior versions)

It's a combination front end/back end. I've finally resorted to letting the back end handle the recordings and then firing up Xine to handle the playback. The wife is really impressed with that efficient maneuver (not!) The front end is totally useless to me except to when I manage to dredge up a little hope and try some settings changes.
The only "help" I received was to get chastised by the audio developer for changing configuration settings. Apparently, his presumptive code handles everything automagically -- except, oh wait, it doesn't.
My current research involves how to downgrade to .23 now that my database has a newer schema.
Good luck.

---

### Post by Chunk of Earth on 2011-01-20
> **simonnev said:**
> Anybody having problems with .24?
.
:
or is it just me ?
mythfrontend version: fixes/0.24 [v0.24-112-g40df4b6]
simon

I am. **  [http://ubuntuforums.org/showthread.php?t=1632963](http://ubuntuforums.org/showthread.php?t=1632963)**
mythfrontend version: v0.24-112-g40df4b6  
(2:0.24.0+fixes.20110119.40df4b6-0ubuntu0mythbuntu2)
(and several prior versions)

It's a combination front end/back end. I've finally resorted to letting the back end handle the recordings and then firing up Xine to handle the playback. The wife is really impressed with that efficient maneuver (not!) The front end is totally useless to me except to when I manage to dredge up a little hope and try some settings changes.
The only "help" I received was to get chastised by the audio developer for changing configuration settings. Apparently, his presumptive code handles everything automagically -- except, oh wait, it doesn't.
My current research involves how to downgrade to .23 now that my database has a newer schema.
Good luck.

---

### Post by Chunk of Earth on 2011-01-20
> **simonnev said:**
> Anybody having problems with .24?
.
:
or is it just me ?
mythfrontend version: fixes/0.24 [v0.24-112-g40df4b6]
simon

I am. **  [http://ubuntuforums.org/showthread.php?t=1632963](http://ubuntuforums.org/showthread.php?t=1632963)**
mythfrontend version: v0.24-112-g40df4b6  
(2:0.24.0+fixes.20110119.40df4b6-0ubuntu0mythbuntu2)
(and several prior versions)

It's a combination front end/back end. I've finally resorted to letting the back end handle the recordings and then firing up Xine to handle the playback. The wife is really impressed with that efficient maneuver (not!) The front end is totally useless to me except to when I manage to dredge up a little hope and try some settings changes.
The only "help" I received was to get chastised by the audio developer for changing configuration settings. Apparently, his presumptive code handles everything automagically -- except, oh wait, it doesn't.
My current research involves how to downgrade to .23 now that my database has a newer schema.
Good luck.

---

### Post by Chunk of Earth on 2011-01-20
> **simonnev said:**
> Anybody having problems with .24?
.
:
or is it just me ?
mythfrontend version: fixes/0.24 [v0.24-112-g40df4b6]
simon

I am. **  [http://ubuntuforums.org/showthread.php?t=1632963](http://ubuntuforums.org/showthread.php?t=1632963)**
mythfrontend version: v0.24-112-g40df4b6  
(2:0.24.0+fixes.20110119.40df4b6-0ubuntu0mythbuntu2)
(and several prior versions)

It's a combination front end/back end. I've finally resorted to letting the back end handle the recordings and then firing up Xine to handle the playback. The wife is really impressed with that efficient maneuver (not!) The front end is totally useless to me except to when I manage to dredge up a little hope and try some settings changes.
The only "help" I received was to get chastised by the audio developer for changing configuration settings. Apparently, his presumptive code handles everything automagically -- except, oh wait, it doesn't.
My current research involves how to downgrade to .23 now that my database has a newer schema.
Good luck.

---

### Post by Chunk of Earth on 2011-01-20
> **simonnev said:**
> Anybody having problems with .24?
.
:
or is it just me ?
mythfrontend version: fixes/0.24 [v0.24-112-g40df4b6]
simon

I am. **  [http://ubuntuforums.org/showthread.php?t=1632963](http://ubuntuforums.org/showthread.php?t=1632963)**
mythfrontend version: v0.24-112-g40df4b6  
(2:0.24.0+fixes.20110119.40df4b6-0ubuntu0mythbuntu2)
(and several prior versions)

It's a combination front end/back end. I've finally resorted to letting the back end handle the recordings and then firing up Xine to handle the playback. The wife is really impressed with that efficient maneuver (not!) The front end is totally useless to me except to when I manage to dredge up a little hope and try some settings changes.
The only "help" I received was to get chastised by the audio developer for changing configuration settings. Apparently, his presumptive code handles everything automagically -- except, oh wait, it doesn't.
My current research involves how to downgrade to .23 now that my database has a newer schema.
Good luck.

---

### Post by Chunk of Earth on 2011-01-20
> **simonnev said:**
> Anybody having problems with .24?
.
:
or is it just me ?
mythfrontend version: fixes/0.24 [v0.24-112-g40df4b6]
simon

I am. **  [http://ubuntuforums.org/showthread.php?t=1632963](http://ubuntuforums.org/showthread.php?t=1632963)**
mythfrontend version: v0.24-112-g40df4b6  
(2:0.24.0+fixes.20110119.40df4b6-0ubuntu0mythbuntu2)
(and several prior versions)

It's a combination front end/back end. I've finally resorted to letting the back end handle the recordings and then firing up Xine to handle the playback. The wife is really impressed with that efficient maneuver (not!) The front end is totally useless to me except to when I manage to dredge up a little hope and try some settings changes.
The only "help" I received was to get chastised by the audio developer for changing configuration settings. Apparently, his presumptive code handles everything automagically -- except, oh wait, it doesn't.
My current research involves how to downgrade to .23 now that my database has a newer schema.
Good luck.

---

### Post by Chunk of Earth on 2011-01-20
> **simonnev said:**
> Anybody having problems with .24?
.
:
or is it just me ?
mythfrontend version: fixes/0.24 [v0.24-112-g40df4b6]
simon

I am. **  [http://ubuntuforums.org/showthread.php?t=1632963](http://ubuntuforums.org/showthread.php?t=1632963)**
mythfrontend version: v0.24-112-g40df4b6  
(2:0.24.0+fixes.20110119.40df4b6-0ubuntu0mythbuntu2)
(and several prior versions)

It's a combination front end/back end. I've finally resorted to letting  the back end handle the recordings and then firing up Xine to handle the  playback. The wife is really impressed with that efficient maneuver  (not!) The front end is totally useless to me except to when I manage to  dredge up a little hope and try some settings changes.
The only "help" I received was to get chastised by the audio developer  for changing configuration settings. Apparently, his presumptive code  handles everything automagically -- except, oh wait, it doesn't.
My current research involves how to downgrade to .23 now that my database has a newer schema.
Good luck.

---

### Post by Chunk of Earth on 2011-01-20
> **simonnev said:**
> Anybody having problems with .24?
.
:
or is it just me ?
mythfrontend version: fixes/0.24 [v0.24-112-g40df4b6]
simon

I am. **  [http://ubuntuforums.org/showthread.php?t=1632963](http://ubuntuforums.org/showthread.php?t=1632963)**
mythfrontend version: v0.24-112-g40df4b6  
(2:0.24.0+fixes.20110119.40df4b6-0ubuntu0mythbuntu2)
(and several prior versions)

It's a combination front end/back end. I've finally resorted to letting  the back end handle the recordings and then firing up Xine to handle the  playback. The wife is really impressed with that efficient maneuver  (not!) The front end is totally useless to me except to when I manage to  dredge up a little hope and try some settings changes.
The only "help" I received was to get chastised by the audio developer  for changing configuration settings. Apparently, his presumptive code  handles everything automagically -- except, oh wait, it doesn't.
My current research involves how to downgrade to .23 now that my database has a newer schema.
Good luck.

---

### Post by Chunk of Earth on 2011-01-20
> **simonnev said:**
> Anybody having problems with .24?
.
:
or is it just me ?
mythfrontend version: fixes/0.24 [v0.24-112-g40df4b6]
simon

I am. **  [http://ubuntuforums.org/showthread.php?t=1632963](http://ubuntuforums.org/showthread.php?t=1632963)**
mythfrontend version: v0.24-112-g40df4b6  
(2:0.24.0+fixes.20110119.40df4b6-0ubuntu0mythbuntu2)
(and several prior versions)

It's a combination front end/back end. I've finally resorted to letting  the back end handle the recordings and then firing up Xine to handle the  playback. The wife is really impressed with that efficient maneuver  (not!) The front end is totally useless to me except to when I manage to  dredge up a little hope and try some settings changes.
The only "help" I received was to get chastised by the audio developer  for changing configuration settings. Apparently, his presumptive code  handles everything automagically -- except, oh wait, it doesn't.
My current research involves how to downgrade to .23 now that my database has a newer schema.
Good luck.

---

### Post by Chunk of Earth on 2011-01-20
> **simonnev said:**
> Anybody having problems with .24?
.
:
or is it just me ?
mythfrontend version: fixes/0.24 [v0.24-112-g40df4b6]
simon

I am. **  [http://ubuntuforums.org/showthread.php?t=1632963](http://ubuntuforums.org/showthread.php?t=1632963)**
mythfrontend version: v0.24-112-g40df4b6  
(2:0.24.0+fixes.20110119.40df4b6-0ubuntu0mythbuntu2)
(and several prior versions)

It's a combination front end/back end. I've finally resorted to letting  the back end handle the recordings and then firing up Xine to handle the  playback. The wife is really impressed with that efficient maneuver  (not!) The front end is totally useless to me except to when I manage to  dredge up a little hope and try some settings changes.
The only "help" I received was to get chastised by the audio developer  for changing configuration settings. Apparently, his presumptive code  handles everything automagically -- except, oh wait, it doesn't.
My current research involves how to downgrade to .23 now that my database has a newer schema.
Good luck.

---

### Post by Chunk of Earth on 2011-01-20
> **simonnev said:**
> Anybody having problems with .24?
.
:
or is it just me ?
mythfrontend version: fixes/0.24 [v0.24-112-g40df4b6]
simon

I am. **  [http://ubuntuforums.org/showthread.php?t=1632963](http://ubuntuforums.org/showthread.php?t=1632963)**
mythfrontend version: v0.24-112-g40df4b6  
(2:0.24.0+fixes.20110119.40df4b6-0ubuntu0mythbuntu2)
(and several prior versions)

It's a combination front end/back end. I've finally resorted to letting  the back end handle the recordings and then firing up Xine to handle the  playback. The wife is really impressed with that efficient maneuver  (not!) The front end is totally useless to me except to when I manage to  dredge up a little hope and try some settings changes.
The only "help" I received was to get chastised by the audio developer  for changing configuration settings. Apparently, his presumptive code  handles everything automagically -- except, oh wait, it doesn't.
My current research involves how to downgrade to .23 now that my database has a newer schema.
Good luck.

---

### Post by Chunk of Earth on 2011-01-20
> **simonnev said:**
> Anybody having problems with .24?
.
:
or is it just me ?
mythfrontend version: fixes/0.24 [v0.24-112-g40df4b6]
simon

I am. **  [http://ubuntuforums.org/showthread.php?t=1632963](http://ubuntuforums.org/showthread.php?t=1632963)**
mythfrontend version: v0.24-112-g40df4b6  
(2:0.24.0+fixes.20110119.40df4b6-0ubuntu0mythbuntu2)
(and several prior versions)

It's a combination front end/back end. I've finally resorted to letting  the back end handle the recordings and then firing up Xine to handle the  playback. The wife is really impressed with that efficient maneuver  (not!) The front end is totally useless to me except to when I manage to  dredge up a little hope and try some settings changes.
The only "help" I received was to get chastised by the audio developer  for changing configuration settings. Apparently, his presumptive code  handles everything automagically -- except, oh wait, it doesn't.
My current research involves how to downgrade to .23 now that my database has a newer schema.
Good luck.

---

### Post by Chunk of Earth on 2011-01-20
> **simonnev said:**
> Anybody having problems with .24?
.
:
or is it just me ?
mythfrontend version: fixes/0.24 [v0.24-112-g40df4b6]
simon

I am. **  [http://ubuntuforums.org/showthread.php?t=1632963](http://ubuntuforums.org/showthread.php?t=1632963)**
mythfrontend version: v0.24-112-g40df4b6  
(2:0.24.0+fixes.20110119.40df4b6-0ubuntu0mythbuntu2)
(and several prior versions)

It's a combination front end/back end. I've finally resorted to letting  the back end handle the recordings and then firing up Xine to handle the  playback. The wife is really impressed with that efficient maneuver  (not!) The front end is totally useless to me except to when I manage to  dredge up a little hope and try some settings changes.
The only "help" I received was to get chastised by the audio developer  for changing configuration settings. Apparently, his presumptive code  handles everything automagically -- except, oh wait, it doesn't.
My current research involves how to downgrade to .23 now that my database has a newer schema.
Good luck.

---

### Post by Chunk of Earth on 2011-01-20
**OMG!**
Sorry about the post storm. Every post received an error when I posted it and didn't show up on the forum. The server must have cached them.
Looks like the admins have [acknowledged the problem]("http://ubuntuforums.org/showthread.php?t=1669956").

---

### Post by simonnev on 2011-01-21
think you got it bad! we aint had tv for a week since all this started going up the wall.

 theres only so much one can take with this system, now got problems with the dvb-s card at the wrong freq  it was fine last week worked like a dream even the mrs and the kids used it I am now seriously thinking its time to move on!

Sage tv anyone?


simon

---

### Post by tgm4883 on 2011-01-21
Works fine on 10.04 and MythTV 0.24

---

### Post by simonnev on 2011-01-21
Got my backend running .24 fine now, sweet as a nut, frontends all work fine no issues with them (couple of revo's 3610)

However got a new pc for a secondary backend and frontend in the lounge and cannot get the nvidia drivers to install at all, using 10.10 and a g210 nvidia card anyone?


thanks simon

---

### Post by williammanda on 2011-01-21
> **simonnev said:**
> Got my backend running .24 fine now, sweet as a nut, frontends all work fine no issues with them (couple of revo's 3610)

However got a new pc for a secondary backend and frontend in the lounge and cannot get the nvidia drivers to install at all, using 10.10 and a g210 nvidia card anyone?


thanks simon

Using G210 on my system and everything is fine. How are you installing mythtv?

---

### Post by newlinux on 2011-01-21
I too have g210 on one of my systems (using 10.04). What problems are you having? What happens when you try and install nvidia drivers? What version and how are you installing them?

---

### Post by simonnev on 2011-01-22
hi 
I have been using this repo: sudo add-apt-repository ppa:ubuntu-x-swat/x-updates

then i run: sudo apt-get update && sudo apt-get install nvidia-current nvidia-current-modaliases nvidia-settings

then sudo nvidia-xconfig

reboot 

drops too shell, never had this problem before 

thanks simon

---

### Post by newlinux on 2011-01-22
Have you looked at

/var/log/Xorg.0.log

for clues on what's going wrong?

---

### Post by simonnev on 2011-01-22
xorg log mentions module not loaded..

however i feel something is more amiss anybody using a gigabyte mobo GA-M68M-S2P ?

---

### Post by simonnev on 2011-01-25
Got it all running at last..
Only thing is don't actually know what i did different to get the nvidia driver running, I downloaded from Nvidia again and re ran the install but this time it asked to remove Nouveau! which it did then after nvidia-xconfig and a reboot it works:-)

So now my setup (touch wood) is all running fine on .24

simon

---

