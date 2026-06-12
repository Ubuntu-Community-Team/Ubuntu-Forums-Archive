---
title: "DRM playability in Mint/Ubuntu hardy"
date: 2008-10-07
forum: Multimedia Software
---

### Post by archangel74 on 2008-10-07
Can someone kindly tell me how to play a .wma drm file that I bought for school?    

CB

---

### Post by minky311 on 2008-10-07
Look in the synaptic package manager System->Administration->Synaptic and search for ubuntu-restricted-extras and make sure it is installed.

---

### Post by archangel74 on 2008-10-07
make sure what is installed??

---

### Post by archangel74 on 2008-10-07
that doesn't change anything although it was not installed...I figured out what you meant after reading your post again.  NM the last posting.  I really need to find a way to make this work.

---

### Post by ubuntu27 on 2008-10-07
First of all install all the codecs and media formts by following the following guides:

[Restricted Formats]("https://help.ubuntu.com/community/RestrictedFormats")

[Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

Now that you done that. Let;g go in to the top secret trick in which it will be able to play DRM.


I am assuming that what you have is mp3 or other digital song files:

_Burn a CD filled with your DRM'ed files and then rip the CD to **ogg** file in Ubuntu._

Source: [Replacing iTunes on Ubuntu]("http://www.psychocats.net/ubuntu/itunes")

---

### Post by buzzmandt on 2008-11-09
if that doesnt work install vlc

---

### Post by Kangarooo on 2009-04-20
i have vlc and totem but none of the is playing .wma files .. audio wma on totm says error - Windows Media Speech decoder required
wma files cant play..
installed xubuntu restricted
totem gives still same error and vlc playback line goes but no sound but when change audio cahannel in vlc to audio 1 i get error   p, li { white-space: pre-wrap; }  No suitable decoder module: VLC does not support the audio or video format "wmas". Unfortunately there is no way for you to fix this. 

how to get medibuntu i even cat see it synaptic and if solution after that is vlc then i already have it..

WMA DRM WMAS

---

### Post by ubuntu27 on 2009-04-20
> **Kangarooo said:**
> i have vlc and totem but none of the is playing .wma files .. audio wma on totm says error - Windows Media Speech decoder required
wma files cant play..
installed xubuntu restricted


So, did you add the Medibuntu repository?

If so, then do the following:

For Ubuntu 32-bit or i386:

```
sudo apt-get install w32codecs
```

For Ubuntu 64-bit: 
```

sudo apt-get install w64codecs
```

If the files that you are trying to play has [DRM]("http://www.learnoutloud.com/content/blog/archives/2006/11/the_top_10_argu.html"), then there is no hope for you.  Just kidding (joking)

Burn the MP3 DRM to a cd as an CD Audio (cda), and then rip it again in Ubuntu. It is preferable if you choose ogg (vorbis) format as the output.

NOTE: I never tried the above, I am only posting what I've read in some threads. 
I never buy DRM'ed file, and you should avoid it too.

---

### Post by Kangarooo on 2010-03-24
Ok i found u can play drm wma on linux so also ubuntu with mplayer and that means also smplayer and other same player versions.
so just install mplayer and it will work
> sudo aptitude install mplayer-gui
now also i found some video files also have some protection but thats another topic.
So resume: i have all codecs tryd vlc totem restricted extras and medibuntu and only mplayer plays drm wma music files. Also it would be good if someone checks if on clean installation theese files work on mplayer heres link to one file to ckech on it [http://kangarooo.times.lv/90secondsorless1a.wma](http://kangarooo.times.lv/90secondsorless1a.wma)
and that i can open with mplayer-gui
but i cant open [http://kangarooo.times.lv/03track3.wma](http://kangarooo.times.lv/03track3.wma)
both of them have DRM protection but both act differentin vlc and in mplayer

---

### Post by mike555 on 2010-03-24
I clicked on the link and it plays audio in "Miro" on my computer ,but not in VLC or movie player .........

---

