---
title: "problem playing 1080p"
date: 2011-05-14
forum: Multimedia Software
---

### Post by ddimit on 2011-05-14
i can play any video file even 720p but when im trying to play 1080p video files my video lags any help

---

### Post by shantiq on 2011-05-14
of course you first need a graphics card which can handle 1080 but i take it you do



which program are you using/?  

**1.**   with VLC   best advice i have seen is [**this  **]("http://ubuntuforums.org/showpost.php?p=10702231&postcount=2")


**2.**  with smplayer ( in your synaptic ) you need to go options/preferences/video   and pick vdpau see image



**3.** also [**xbmc**]("http://xbmc.org/") has no problem with 1080


```
sudo add-apt-repository ppa:team-xbmc
sudo apt-get update
sudo apt-get install xbmc
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by beew on 2011-05-14
> **shantiq said:**
> of course you first need a graphics card which can handle 1080 but i take it you do



which program are you using/?  

**1.**   with VLC   best advice i have seen is [**this  **]("http://ubuntuforums.org/showpost.php?p=10702231&postcount=2")


If you have to do this you may as well use a different player because the result is not good. VLC uses only one core so it may not be the right player for 1080P. The multi-threaded build of mplayer works much better in my experience. (This may change with future builds of VLC because the ffmpeg-mt has been merged into the main trunk in late March)

> **2.**  with smplayer ( in your synaptic ) you need to go options/preferences/video   and pick vdpau see image

Only if OP has a recent Nvidia card.

> **3.** also [**xbmc**]("http://xbmc.org/") has no problem with 1080

I don't know, in my experience XBMC actually works worst than VLC **unless** you have a recent Nvidia card, in that case XBMC uses vdpau and playback is excellent.

---

### Post by ddimit on 2011-05-14
1:my graphic card is ati x1300(does it support 1080p??)
2:im using smplayer before i had another option and now i selected the one you told me and now it does not show any video only audio
3:i have added the ppa of the [**xbmc**]("http://xbmc.org/") but it tells me 
```
W: Failed to fetch http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/natty/main/binary-amd64/Packages  404  Not Found
```

---

### Post by beew on 2011-05-14
> **ddimit said:**
> 
2:im using smplayer before i had another option and now i selected the one you told me and now it does not show any video only audio


vdpau only works with Nvidia graphic cards like I told you. If you don't have Nvidia set video output to xv. 

To use vlc with ati cards you may want to check out this ppa.

[https://launchpad.net/~dtl131/+archive/catalysthacks]("https://launchpad.net/%7Edtl131/+archive/catalysthacks")

---

### Post by shantiq on 2011-05-15
> **beew said:**
> If you have to do this you may as well use a different player because the result is not good. VLC uses only one core so it may not be the right player for 1080P. The multi-threaded build of mplayer works much better in my experience. (This may change with future builds of VLC because the ffmpeg-mt has been merged into the main trunk in late March)

Only if OP has a recent Nvidia card.

I don't know, in my experience XBMC actually works worst than VLC **unless** you have a recent Nvidia card, in that case XBMC uses vdpau and playback is excellent.


you might be right on vlc but at least that trick lets 1080 through

as regards smplayer and XMBC i took it as read that the hardware was already in place

looking around for [**ati card**]("http://www.google.co.uk/#q=ati+x1300+support+1080p&hl=en&prmd=ivnsfd&ei=woDPTaCyAoKDhQfQhtD5DA&start=10&sa=N&fp=1512da287c2ebdcb") it does not seem like it is straightforward



ddimit that is all the advice i personally had

---

