---
title: "Minitube does not play videos!!!!"
date: 2011-02-12
forum: Multimedia Software
---

### Post by pavelexpertov on 2011-02-12
I installed minitube 1.4 on ubuntu 10.10. I can search for videos in youtube, but i can not play  video. Help :confused:

---

### Post by beew on 2011-02-12
Can you be more specific about your problem? I have upgraded minitube from 1.3 to 1.4 recently and everything works flawlessly. 1.3 was unusable because it kept skipping clips, this is fixed in 1.4.

---

### Post by pavelexpertov on 2011-02-16
When I launch minitube 1.4, it launches. It works perfect when i search for videos, but when i click on them, i can only see a title of the video and its description, but video is not playing. Moreover, when i try to play a video, buttons such as "PLay" and "Previous" start to highlight themselves.

---

### Post by pavelexpertov on 2011-02-16
update: I have got a 64-bit ubuntu 10.10

---

### Post by A420X on 2011-02-16
I had the same problem, installing these dependencies worked for me: 


```
sudo apt-get install libqt4-network phonon-backend-gstreamer gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad


```
You say you're on 64bit, this site [http://flavio.tordini.org/minitube/minitube-linux-setup](http://flavio.tordini.org/minitube/minitube-linux-setup)
says that you need to build from source, but it's for an old version so the situation may 
have changed. 

Hope this helps

---

### Post by diabolicalangle on 2011-03-06
Have the same problem ,and the dependencies are already installed.. Going to try building from source

---

### Post by diabolicalangle on 2011-03-06
Built from source, and the same issue occurs. In terminal however, it says "buffering" each time it "flickers". not sure whats going on but apparently its not getting past the buffer stage..

EDIT:
If you remove the xine-backend, it works except for the seek function. 

Help on getting it?

Heres the terminal log:

pushSeek seek: 543431 
popSeek real seek: 543431 
seekInternal 543431 
stateChangedInternal newState: "StoppedState" previousState: "PlayingState" 
pushSeek seek: 0 
popSeek real seek: 0 
seekInternal 0 
play 
updateVolume Volume changed to -  50  From  50 
stateChangedInternal newState: "PlayingState" previousState: "StoppedState" 
videoWidgetSizeChanged video width 1920 height: 1072 
stateChangedInternal newState: "PlayingState" previousState: "PlayingState" 
stateChangedInternal newState: "PausedState" previousState: "PlayingState" 
paused

---

### Post by dima206 on 2011-03-22
Hi I have had the same problem
The issue worked for me is to reinstall all minitube dependencies
"libqt4-network phonon-backend-gstreamer gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad"
remove xine-beckend and run "sudo apt-get autoremove".

---

### Post by pavelexpertov on 2011-03-27
How do i reinstall all dependencies in terminal?

---

### Post by Claus7 on 2011-11-04
Hello,

> **pavelexpertov said:**
> How do i reinstall all 
dependencies in terminal?


```
sudo apt-get install --reinstall libqt4-network phonon-backend-gstreamer gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad
```

```
sudo apt-get remove phonon-backend-xine

```

no video though...

Regards!

---

### Post by beew on 2011-11-04
Which version of minitube are you talking about? 1.4 doesn't work. Youtube changed something a while back and minitube 1.4 was broken as a result. You can get an updated version  from the webupd8 ppa
[https://launchpad.net/~nilarimogard/+archive/webupd8]("https://launchpad.net/%7Enilarimogard/+archive/webupd8")

You can also download from minitube, it is a bin that doesn't require installation, just click and it will work.

---

### Post by Claus7 on 2011-11-04
Hello,

> **beew said:**
> Which version of minitube are you talking about? 1.4 doesn't work. Youtube changed something a while back and minitube 1.4 was broken as a result. You can get an updated version  from the webupd8 ppa
[https://launchpad.net/~nilarimogard/+archive/webupd8]("https://launchpad.net/%7Enilarimogard/+archive/webupd8")

You can also download from minitube, it is a bin that doesn't require installation, just click and it will work.

the versions I'm talking about are:
1.1x, 1.3x, 1.5.1, 1.5.2, where x number I do not remember.

I was able to download the deb files which were the default for the various ubuntu releases. They were installed nicely. I got rid of the phonon-xine package so as to make it play the links.

Compiz is enabled, which might interfere. I guess that the final version is 1.6. I'll wait for a deb file.

Regards!

---

