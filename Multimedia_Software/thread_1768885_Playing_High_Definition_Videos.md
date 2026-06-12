---
title: "Playing High Definition Videos"
date: 2011-05-27
forum: Multimedia Software
---

### Post by ChemMeister on 2011-05-27
Hello,

I am having hard time playing a high definition video file (.mp4), the video initially  plays fine, but after 5 mins, it starts to skip and stutter, (I use Movie Player with some codes that Ubuntu installed when I first tried to play file)
I have a Dell XPS M1330 Intel Core Duo @2.20 GHz with 4 GB RAM. Any ideas? 

Thanks,

---

### Post by vanadium on 2011-05-27
Can you do me a favour and test the following:

1) Turn off swap (temporarily)
2) Run the video

For 1), open a terminal and type "sudo swapoff -a"

Let the video play and continue playing on stuttering: my expectations are that after a "stutter", it goes well again for some time.

Report back if there are changes  over a situation where your swap is active
- The stuttering could be gone
- The stuttering could still be there, but less frequent and less long
- Nothing may change
- Your system could freeze (so do not do this with open applications)

---

### Post by ChemMeister on 2011-05-27
> **vanadium said:**
> Can you do me a favour and test the following:

1) Turn off swap (temporarily)
2) Run the video

For 1), open a terminal and type "sudo swapoff -a"

Let the video play and continue playing on stuttering: my expectations are that after a "stutter", it goes well again for some time.

Report back if there are changes  over a situation where your swap is active
- The stuttering could be gone
- The stuttering could still be there, but less frequent and less long
- Nothing may change
- Your system could freeze (so do not do this with open applications)


Thanks for your reply Vanadium,

I tried turning the swap off, however i didn't see any changes. The video plays fine for the  5 mins and then starts to stutter and skip. It is rather surprising given my computer specs and the fact that I am using 64-bit Ubuntu.

---

### Post by doas777 on 2011-05-27
ok, first off, have you installed the [mediubuntu]("http://medibuntu.org/repository.php") codecs and the [ubuntu-restricted-extras package]("https://help.ubuntu.com/community/RestrictedFormats")?

for HD content that lags in Totem (Movie Player) I use SMPlayer. it uses the Zine backend instead of GStreamer, and deals with heavier content much more easily.
[http://www.howtogeek.com/howto/12125/getting-started-with-smplayer-on-ubuntu-to-play-movies-better/](http://www.howtogeek.com/howto/12125/getting-started-with-smplayer-on-ubuntu-to-play-movies-better/)

---

### Post by shantiq on 2011-05-28
> **doas777 said:**
> ok, first off, have you installed the [mediubuntu]("http://medibuntu.org/repository.php") codecs and the [ubuntu-restricted-extras package]("https://help.ubuntu.com/community/RestrictedFormats")?

for HD content that lags in Totem (Movie Player) I use SMPlayer. it uses the Zine backend instead of GStreamer, and deals with heavier content much more easily.
[http://www.howtogeek.com/howto/12125/getting-started-with-smplayer-on-ubuntu-to-play-movies-better/](http://www.howtogeek.com/howto/12125/getting-started-with-smplayer-on-ubuntu-to-play-movies-better/)





yes i concur here


smplayer has no problem even with 1080p 


choose    options/preferences/video/output driver/vdpau     and you are away:KS      


 [** xbmc**]("http://xbmc.org/download/") has also always worked for me for 1080p



also just tested a new one called **umplayer** which is a fork from smplayer   it too works brilliantly for 1080p same settings as smplayer with vdpau ( options/preferences/video/output driver/vdpau)



first saw it mentioned [here]("http://ubuntuforums.org/showpost.php?p=10841310&postcount=2") thank you beew


install UMPlayer using the following commands:


```
sudo add-apt-repository ppa:nilarimogard/webupd8
sudo apt-get update
sudo apt-get install umplayer
```

A few readers have reported that using Mplayer from the Ubuntu official repositories UMPlayer doesn't work so you may want to install the latest MPlayer from the MPlayer daily builds PPA (this PPA is even linked in the MPlayer download page). Add it and upgrade MPlayer using the following commands:

```
sudo add-apt-repository ppa:motumedia/mplayer-daily
sudo apt-get update
sudo apt-get upgrade
```

---

