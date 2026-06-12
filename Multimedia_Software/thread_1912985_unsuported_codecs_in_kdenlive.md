---
title: "unsuported codecs in kdenlive"
date: 2012-01-21
forum: Multimedia Software
---

### Post by leeper69 on 2012-01-21
hi I have recently downloaded kdenlive on the xubuntu desktop and cannot get it to render the following formats I get the corasponding error mesages when trying to render.
mp4 unsuported audio codec libmp3lame
xvid4 unsuported video codec libxvid
h.264 unsuported video codec libx264
flash unsuported audio codec libmp3lame
I have downloded xubuntu restricted extras but still get the above errors when trying to render to the above formats.
I have kubuntu loaded on a differant partision and all the above formats work with that install. so I set up another partision and downloaded kubuntu on it after downloading kaffeine, libxine-all,libdvdread4 and adding the repository ppa:sunab/kdeniive-release then downloading kdenlive which also loads its suporting files and xine then opening the terminal and installing libdvdcss. I have the same problems with the above codecs so it seems somthing has changed in the repositorys to make the above lib files no longer work or I am missing somthing. 
can anyone tell me what I am missing to make the above formats work?
aperantly this is a nowen issue that may be caused by the mlt acording to the answer I got from my post on there forum.

---

### Post by sgtGarcia on 2012-01-26
Hi. As far as I know You should search in Synaptic for package:
```
libavcodec-extra-52
```
And then in KDEnLive go to Settings->Run Config Wizzard
Go through wizzard & then You should be able to use those formats ( maybe You will need to restart KDEnLive ).

---

### Post by leeper69 on 2012-02-10
I tryed to find libavcodec-extra-52 and came up with no matching file in synaptic. what repository would this file be in?
I do have libavcodec-extra-53 installed and the above mp4,h264,xvid4and flash still dont work in xubuntu.
Yuo got me curious so I loged into the working partision and serched for libavcodec and found the same libavcodec-extra-53 file there
that is in xubuntu.

---

### Post by sgtGarcia on 2012-02-10
Did You tried in KDEnLive
```
Settings->RunConfigWizzard
```
Go through all the Wizzard settings and than restart KDEnLive.
That should do.

I don't have version 53 of this lib cause I have U11.04.
Version 53 is probably in >=11.10 ( Hint: You should update Your profile info ;)

---

### Post by shantiq on 2012-02-10
not sure which version you are using but ob oneiric i hac problems ans was advised to use this [here]("http://ubuntuforums.org/showpost.php?p=11393050&postcount=2") which corrected incomplete version i had

might be worth a try:KS

---

### Post by sgtGarcia on 2012-02-15
I've just installed Ubuntu Studio 11.10 64bit ( XFCE ).
```
KDEnLive version 0.8.2.1 from sunab ppa-repo
```
```
MLT version 0.7.6-0ubuntu0~sunab~oneiric3 from sunab ppa-repo
```
```
libavcodec-extra-53 version 4:0.7.3ubuntu0.11.10.1
```
I can render properly all mentioned by You leeper69 formats.
You have to go trough config wizard once again ( see my previous post ).

---

### Post by leeper69 on 2012-02-23
thanks sgGarcia for your post as of 2/2012 the mlt was upgradeded to ver 0.7.6 and all rendering formats are now working.

---

