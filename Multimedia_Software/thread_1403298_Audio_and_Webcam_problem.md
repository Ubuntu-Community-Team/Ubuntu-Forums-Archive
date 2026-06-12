---
title: "Audio and Webcam problem"
date: 2010-02-10
forum: Multimedia Software
---

### Post by iggy pop on 2010-02-10
I am running Ubuntu 9.10 (Karmic Koala) on a five year old desktop computer with no problems what-so-ever until that is when i try to use aMSN.

The aMSN program is great and problems only arise when i try to configure the audio and webcam. When i open up Preferences -> Edit audio and video settings and try to configure the audio and webcam everything just freezes solid and the only way i can un-freeze the computer is to disconnect the plug from the power connection.

On other occasions when i have again attempted to configure the audio and webcam the whole aMSN program just vanishes off the screen altogether? 

I have a Logitech QuickCam 8.1.1

Could someone help me out here please! Thanks

---

### Post by Claus7 on 2010-02-10
Hello,

I face exactly the same problem except the vanishing thing. Except if by vanishing you mean that the window of amsn exists, yet only the borders, while the content is empty. It seems that is a [bug]("https://bugs.launchpad.net/ubuntu/+source/amsn/+bug/424240"). Either use a lower version of amsn or a lower distro of ubuntu or try multiple times to configure the audio and video, without tweaking with the options and just leaving the defaults. At least I suppose that you can get sound, yet you are not able to make configurations. I have also the problem of freezing, while trying to send a sound clip, yet in previous versions I did not face such an issue. The freezing happens while trying to configure audio and video from the sound menu to the mic menu. 

If you leave your computer in peace for 10' or so, it might be possible to unfreeze and then kill the process of amsn.

Also, I hope that next time you won't pull out the plug of your pc as you are risking loosing valuable data, as well as damaging the hardware of your pc. One alternative which is not good, yet for sure better is either to press the resume button or to hold down the power button till the pc is off.

Regards!

---

### Post by iggy pop on 2010-02-10
Hello Claus7,

I know this will seem stupid but i got the version of aMSN that i'm using from Synaptic Package Manager. Where would i be able to get an older version of aMSN?

I will do as you have suggested regarding pulling out the plug. But sometimes when i close down the computer at night i usually click on Log out and then shut down but for some reason the computer won't close down?

---

### Post by Claus7 on 2010-02-10
Hello,

first of it will be very helpful to know which version of ubuntu you are using. 

The shutting down problem is an entirely different issue. I did not understand which you press the log out button in order to shut down your computer... May be here you can shed some more light, yet this thing it entirely different than your problem here.

I would suggest you to go in [this page]("http://packages.ubuntu.com/jaunty/amsn") and download amsn, yet this version is old enough. If you search by different versions of ubuntu you will be able to find a different one, yet do not try an older version than 0.97. Just download the deb file and install it.

What exactly are the configurations you want to do in audio and video support of amsn? Are you not happy with the ones you get by default? I would suggest you not to mess with older ones, expept if you know what you are doing (you might face dependency problems and cause some version conflict, first try to get rid of the installed version of amsn you have).

Regards!

---

### Post by iggy pop on 2010-02-10
I am running Linux Mint 8 on another equally aging computer and i installed aMSN without changing any of the default settings and now aMSN is functioning really well. Thanks for the replies.

---

