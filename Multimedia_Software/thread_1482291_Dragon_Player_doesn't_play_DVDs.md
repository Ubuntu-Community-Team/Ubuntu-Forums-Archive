---
title: "Dragon Player doesn't play DVDs"
date: 2010-05-13
forum: Multimedia Software
---

### Post by stee_35 on 2010-05-13
Hi

I run lucid. I already have installed Medibuntu and the package  libdvdcss2. Nevertheless, I still can't get DragonPlayer to play a DVD properly. Indeed, Dragon starts to play the DVD. However, the image is distorted and you can't recognize anything... This is what the terminal messages say when I start Dragon over the terminal:

```
norma@norma:~$ dragon --play-dvd /media/cdrom0/
dragonplayer(2265)/kdeui (kdelibs): Attempt to use QAction   "aspect_ratio_menu" with KXMLGUIFactory! 
dragonplayer(2265)/kdeui (kdelibs): Attempt to use QAction   "audio_channels_menu" with KXMLGUIFactory! 
dragonplayer(2265)/kdeui (kdelibs): Attempt to use QAction   "subtitle_channels_menu" with KXMLGUIFactory! 
libdvdnav: Using dvdnav version 1.1.17 from [http://xine.sf.net]("http://xine.sf.net/")
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav: DVD Title: ICE AGE 3 DVD3
libdvdnav: DVD Serial Number: 3b465e18
libdvdnav: DVD Title (Alternative): ICE AGE 3 DVD3
libdvdnav: Unable to find map file '/home/norma/.dvdnav/ICE AGE 3   DVD3.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fd0000. Regions:   2

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient 
```I went through the threads. However, I was not able to find any solution

Thanks a lot for your help in advance!

---

### Post by Meskarune on 2010-05-13
This sounds like a problem with CSS (thats what makes the video messed up, its supposed to prevent piracy, but in in the end its just really annoying)

Can you play dvd's via vlc player?

This might help you out: [http://cvalcarcel.wordpress.com/2009/04/26/help-my-dragon-player-is-not-working-in-kubuntu-904/](http://cvalcarcel.wordpress.com/2009/04/26/help-my-dragon-player-is-not-working-in-kubuntu-904/)

---

### Post by stee_35 on 2010-05-13
thanks a lot for the information! VLC and SMPlayer work both fine. I can do it without Dragon:)

---

