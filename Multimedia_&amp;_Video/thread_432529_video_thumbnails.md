---
title: "video thumbnails?"
date: 2007-05-04
forum: Multimedia &amp; Video
---

### Post by bionnaki on 2007-05-04
hello. I'm running fiesty with gnome. I remember with previous releases videos would appear in nautilus as thumbnails, but with fiesty they do not come up. what could I be doing wrong?

---

### Post by Vixis on 2007-05-04
In Nautilus  Edit -> Prefences -> Preview. Other Priviewable Files for video & images.

---

### Post by bionnaki on 2007-05-04
yes. I have those options selected. still no thumbnails for videos.

---

### Post by bionnaki on 2007-05-04
bump

---

### Post by trotur on 2007-05-05
I got thumbnails for videos after I installed a xine-based player and then forced nautilus to generate new thumbnails by executing
```
rm -r $HOME/.thumbnails/fail
rm -r $HOME/.thumbnails/normal
killall -9 nautilus
```

Hope this helps.

---

### Post by darundal on 2007-05-05
Didn't do anything for me, still got nothing.

---

### Post by bionnaki on 2007-05-05
thanks.

I installed gxine (which includeds xine-gui). I also reinstalled totem and entered those commands. still no thumbnails. I'll try rebooting.

---

### Post by bionnaki on 2007-05-05
nope, still no thumbnails. 
hmmm

---

### Post by trotur on 2007-05-06
Do you have libxine1-ffmpeg installed? That may be needed for some thumbnails.
Try
```
sudo apt-get install libxine1-ffmpeg
```
and repeat commands from post [#5]("http://ubuntuforums.org/showthread.php?p=2596537#post2596537").

---

### Post by bionnaki on 2007-05-08
works now. thanks!

---

### Post by trotur on 2007-05-09
I'm pleased to hear that.

---

### Post by ryth on 2007-11-18
> **trotur said:**
> I got thumbnails for videos after I installed a xine-based player and then forced nautilus to generate new thumbnails by executing
```
rm -r $HOME/.thumbnails/fail
rm -r $HOME/.thumbnails/normal
killall -9 nautilus
```

Hope this helps.

This solution worked perfectly for me.  Thanks for the help.

---

### Post by Agret on 2008-05-28
Mine still wasn't working after following the steps here. I attempted to play a movie over SMB and it opened in Totem (I usually use VLC but it doesn't support smb:// for some reason...) and then Totem prompted me to install codecs, after installing those the thumbnails worked. :guitar:

---

