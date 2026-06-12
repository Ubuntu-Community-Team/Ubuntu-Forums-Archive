---
title: "New to this and need help with MPlayer"
date: 2008-08-02
forum: Multimedia Software
---

### Post by CATM on 2008-08-02
Hello there. Let me start off by saying that I have been watching these forums for awhile and I must say the the support given here is by far the best. You helpers of the lost (me) are awesome. Thanks in advance

I am a complete new Linux user as I have used windows all of my life. I have been converted however, to a much happier existence with Ubuntu. This OS kicks ***....but,

did I mention I don't know anything. Therefore I read and read and read and my wife is mad at how much time I am spending. I just completely switched from windows vista to Ubuntu yesterday. I am doing ok, however, I was attempting to play a video with the standard video player and it was flickering. I searched the forum and found this thread. I

[http://ubuntuforums.org/showthread.php?t=636277&highlight=video+problem](http://ubuntuforums.org/showthread.php?t=636277&highlight=video+problem)

I followed the directions to the line, but when I tried to open MPlayer it shows me this

New_Face Failed.Maybe the font path is wrong. Please supply the text font file (~/.mplayer/subfont.ttf).

MPlayer will not respond. So I did what I always do and attempted to remove MPlayer completely from my computer so I could reinstall it the right way (maybe). 

Well, I removed MPlayer completely, however it is still in my Applications menu under sound and video...

HELP.....I don't know what I did or even if I have given the correct information, but I ask for forgiveness in advance for my ignorance. What do I do to remove this application and then how do I get my movies to play (,avi files and such) without flickering....

Thanks

---

### Post by kpkeerthi on 2008-08-02
Try VLC

[http://ubuntuguide.org/wiki/Ubuntu:Hardy#Installing_VLC_Media_Player](http://ubuntuguide.org/wiki/Ubuntu:Hardy#Installing_VLC_Media_Player)

---

### Post by CATM on 2008-08-02
Thank you, thank you, thank you. It works great. now how do I remove MPlayer. I tried sudo apt-get --purge autoremove MPlayer, but is says

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package MPlayer

However, it's still in my list of applications and I can still open the program????

---

### Post by kpkeerthi on 2008-08-02
Open System -> Admin -> Synaptics. Click on the search button in the toolbar. Search for mplayer. It should list mplayer packages (in green, if installed). Right-click and mark for complete removal. Click Apply.

You may want to spend some time reading about [Synaptic]("https://help.ubuntu.com/community/SynapticHowto")

---

### Post by shirilover on 2008-08-02
The error you describe is not that big of a deal. It only effects on screen display text.
You can always make a symlink to your preferred font if you wish.
```

ln -s /usr/share/fonts/truetype/ttf-bitstream-vera/Vera.ttf ~/.mplayer/subfont.ttf

```

---

### Post by CATM on 2008-08-04
You folks ROCK!!!! Thanks for the help, this Ubuntu thing is way easier than I thought it would be....But without the dedication and support of you folks, it wouldn't work at all......

---

