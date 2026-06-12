---
title: "I can not play disks! cd or dvd. I used to be able too please help!"
date: 2009-07-23
forum: Multimedia Software
---

### Post by jcm1107 on 2009-07-23
Hi, I can not play audo cd's or movie dvd's any more. I don't know what happened. I used to be able too, I have all free and non free codecs installed and I get errors with any media player I try to use. They all say no valid files or I might not have a codec installed to play this media type. When I put in a cd that I bought at wal mart it says no audo files found and it is an audio cd. All my disks work on anything else, and they used to work so something I did must have changed something I just don't know what. I would appreciate any help, Thanks!

---

### Post by igorzwx on 2009-07-23
somebody told that this might be caused by audio problems

ALSA geeks are doing something like this: kill pulse and restart alsa.

search in the forum, keyword "killall pulseaudio"

---

### Post by jcm1107 on 2009-07-23
> **igorzwx said:**
> somebody told that this might be caused by audio problems

ALSA geeks are doing something like this: kill pulse and restart alsa.

search in the forum, keyword "killall pulseaudio"

Thanks, but this did not solve the problem. I found a thread that said something like sudo killall pulseaudio and then it had a command to restart alsa and I did that with no luck. I want to say I do have sound and I can play video off of the hard drive and an external drive I have and also from flash drive just not my dvd burner drive. I wonder if mabe that just went bad but it was working and I can see files on disks I just can not play movies when I try the drive sounds like a helicopter taking off and it only does that when it can not find the files on it. Any other time it is quiet when it used to play movies. Maybe it is broke, I just want to be sure before I buy another one. I also want to mention I had an error message say that only the guest has permission to mount this drive one time (referring to my dvd burner) so it could be permission issue? I tried to check that and it seemed I have permission to mount it, but I have virtual box and everything else on this computer so something else could be taking it over and mounting it making me not have permission I don't know how to check all of this. If someone could give me a command to check or something I think that may help. Thanks for trying to help! I really appreciate it!

---

### Post by igorzwx on 2009-07-23
aplay -l

---

### Post by jcm1107 on 2009-07-23
thanks here are the results of that:

justin@justin-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
justin@justin-desktop:~$ 


I don't know how that helps but if it tells you something then great!

---

### Post by igorzwx on 2009-07-23
you have HDA

if you would have something more simple...

I solved all my problems by OSS4.

You can ask on OSS4 forum, if your card is supported
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

---

### Post by xc3RnbFO8P on 2009-07-23
Did you try to reinstall the codecs?
[http://ubuntuforums.org/showpost.php?p=7197110&postcount=5]("http://ubuntuforums.org/showpost.php?p=7197110&postcount=5")

---

### Post by jcm1107 on 2009-07-23
> **igorzwx said:**
> you have HDA

if you would have something more simple...

I solved all my problems by OSS4.

You can ask on OSS4 forum, if your card is supported
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)


What does that mean? I thought hda would of been the first hard drive? what would be more simple? I will try anything. And what would you do if you were me? for hardware I have onboard audio that I dont use, I use soundblaster live 24 bit sound card and I am listining to music right now, just I cant play any disks.

---

### Post by jcm1107 on 2009-07-23
> **Ringi said:**
> Did you try to reinstall the codecs?
[http://ubuntuforums.org/showpost.php?p=7197110&postcount=5]("http://ubuntuforums.org/showpost.php?p=7197110&postcount=5")

thanks I will try this and let you know if it works or not.

---

### Post by jcm1107 on 2009-07-23
I just noticed that those codes are for jaunty I have 8.04 hardy. I already have media ubuntu added for it I guess it should work to just do sudo apt-get install for all the codecs in there right?

---

### Post by jcm1107 on 2009-07-23
I just tryed to install those codecs and it didn't find  libdvdread4  do you think this is my problem?

---

### Post by xc3RnbFO8P on 2009-07-23
> I just noticed that those codes are for jaunty I have 8.04 hardy. I already have media ubuntu added for it **I guess it should work to just do sudo apt-get install for all the codecs in there right?**
Yes Hardy codecs

---

### Post by igorzwx on 2009-07-23
HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]

HDA  may mean high definition audio
[http://www.google.com/search?hl=en&q=hda+audio&aq=f&oq=&aqi=g10](http://www.google.com/search?hl=en&q=hda+audio&aq=f&oq=&aqi=g10)

---

### Post by jcm1107 on 2009-07-23
reinstalling the codecs did not help. I could not get the libdvdread4 to install but I never had it before, I think that is a new one for jaunty. with an audio disk my error is:

UNABLE TO MOUNT AUDIO DISK
Drive /dev/scd0 does not contain audio files

I get this error with everything, every disk every media player, and I have a lot of different media players. I just want to know if my drive is broke or my system. I think it is my system but I cant figure it out this time.

---

### Post by igorzwx on 2009-07-23
I would do this:

install another Ubuntu in dual boot (better 9.04)
and see how it works.
I would try OSS4, if my card is supported.
and codecs form Medibuntu, of course.

---

### Post by jcm1107 on 2009-07-23
What I did I really don't understand why it fixed it but everything is good again!! What I did was all the stuff y'all told me to do, and it still was not playing. I noticed that the error said scd0 well that would be sata drive right? well my drive is ide so I rebooted went in the bios and looked at it my controller is ide like it always was but I have a external usb hard drive and also usb flash drive plugged in to my comp. Well they were somehow set to boot first so I changed that back to boot from cdrom and then hard drive and not the usb drives and then I saved and rebooted and all is great. Makes no sense other than the computer must have changed boot orders because of a new flash drive device that I started using to save some files on to take to another computer. I have rebooted before and that didn't fix my problem it must have been the boot order that caused the conflict!! But Thanks Guys!!! This is SOLVED I NOW CAN PLAY CD'S AND DVD'S!!

---

### Post by xc3RnbFO8P on 2009-07-23
Great news :)

---

### Post by jcm1107 on 2009-07-23
Crazy confusing problem to figure out isn't it!

---

### Post by xc3RnbFO8P on 2009-07-23
> Crazy confusing problem to figure out isn't it!
Yes it is.

---

### Post by igorzwx on 2009-07-23
it is very convenient to have several different Ubuntus installed
and several browsers too.
If one does not work, you can try another

---

