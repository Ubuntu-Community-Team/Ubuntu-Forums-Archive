---
title: "Any DVD Player in Gutsy"
date: 2008-01-15
forum: Multimedia &amp; Video
---

### Post by mschraier on 2008-01-15
OK OK.   I have spent the last few days attempting to get some dvd player to work properly.  I have tried both veriosn of Totem (gstreamer is a waster), VLC, MPLayer and Kaffeine.  With the exception of Totem GST, they more or less work ok, however the dispaly quality is horrible  colors are not sharp and birght.  how and what do i install to tyr to start this process from the beginning?  i dont want to re-install the OS.  I know Totem Xine worked fine, but I had to tinker around with it.  So, help me uninstall everything related and re-install Totem Xine will all required codecs and files.    :confused::confused::confused::confused:

---

### Post by ubuntu-freak on 2008-01-15
Give my complete how-to a go 

[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)

The second post focuses more on DVD playback 

Nathan

P.S. If you want to reinstall it's **sudo apt-get --reinstall install**

---

### Post by mschraier on 2008-01-15
Your instructions look as th ough they are to install mplayer.  does this cover all the ciodecs?  I hear Mplayer is difficult to get wokring properly.  Also, does Mplayer handle DVD menus?  One time I did try it,  it owuld always show subtitles.  I could not find where to make no subtitles the default.  I do see where you show how to unistanll all the other players.  I want to make this a clean type install without reinstalling the OS.

:guitar::guitar::guitar:

---

### Post by jordansdad253 on 2008-01-15
You could always try VLC player. No need to install any codecs

---

### Post by mschraier on 2008-01-15
did that. did not enjoy the interface and i dont think it handles DVD menus

thank you       :KS

---

### Post by jordansdad253 on 2008-01-15
It does handle DVD menus, when you open a new file just click on the disc tab > DVD menus. 
Then you just click the menu button with your mouse. To make it full screen just double click the video screen, and for play,pause, stop, forward options just right click and they all show up.

---

### Post by jrusso2 on 2008-01-15
My personal preference is for Kaffeine for playing DVD's with the xine backend.

Second choice would be kmplayer.

---

### Post by SunnyRabbiera on 2008-01-15
xine-ui is a great bet, it works just as well as any windows dvd player.

---

### Post by mschraier on 2008-01-15
ok then, has anyone had an issue with the quality of the playback? Specifically it not being sharp and colors are kinda muted and fuzzy?  I erally want to unload everything related to DVD and do a fresh instrall of everything required for just one of the players.  I have been given sort of that for Mplayer, but it gives me some issues.  I think using the xine back end with either totem or xine-gui would be cool. what are all the fiels, codecs whatever i need to make sure i have ?  will add/remove give me the latest??

:guitar::guitar:

---

### Post by SunnyRabbiera on 2008-01-15
add/ remove has a limited selection, you might be better off with synaptic.

---

### Post by ubuntu-freak on 2008-01-15
> **mschraier said:**
> Your instructions look as th ough they are to install mplayer.  does this cover all the ciodecs?  I hear Mplayer is difficult to get wokring properly.  Also, does Mplayer handle DVD menus?  One time I did try it,  it owuld always show subtitles.  I could not find where to make no subtitles the default.  I do see where you show how to unistanll all the other players.  I want to make this a clean type install without reinstalling the OS.

:guitar::guitar::guitar:

 
No. My first post there was to get streaming working. It's easy if you follow the instructions carefully. Just a matter of cutting and pasting. 
 
The post further down deals with getting DVD playback working properly. VLC is best for that and supports menus.
 
Make sure you do the first part of the streaming how-to as it installs packages you need. Then you can do the DVD section. Best to complete the whole streaming how-to though.
 
Nathan

---

### Post by chips24 on 2008-01-15
dont worry ive been trying over a year to run a dvd player on ubuntu:-x:-x:-x

---

### Post by Omnios on 2008-01-15
I have totem Xine and extra codec installed with Animatix 

 I can watch DVD's in it just fine.

---

### Post by AJB2K3 on 2008-01-15
> **chips24 said:**
> dont worry ive been trying over a year to run a dvd player on ubuntu:-x:-x:-x :confused: You seam to not be loking in the right place. :confused::confused::confused:

Try **google** or the **ubuntu wiki's** because it took 5 mins to get working on my acer laptop.

---

### Post by ubuntu-freak on 2008-01-15
> **AJB2K3 said:**
> :confused: You seam to not be loking in the right place. :confused::confused::confused:

Try **google** or the **ubuntu wiki's** because it took 5 mins to get working on my acer laptop.

 
I agree. It's frustrating that people don't find my how-to. 
 
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)
 
Gets absolutely everything working and it's right here in these forums.
 
Nathan

---

### Post by Melcar on 2008-01-15
I prefer VLC for DVD playback, or Kaffeine with Xine, but I tend to avoid Xine whenever possible.

---

### Post by mschraier on 2008-01-15
ok, maybe i am a bit exhausted with DVD playback.  I have gotten al but Totem GST to work.  The main problem is the video clarity  sucks.  I had it installed before with Totem xine and it worked great.  But i had to re-install the OS and ever since i cannot get the video to be crisp as it was.  So i guess i want to find out if there is a fix for that.  I am on a Dell E1505 with on board Intel graphics.

---

### Post by cor2y on 2008-01-15
Enable the restricted repos specifically medibuntu or download the libdvdcss2 package from the medibuntu site
[http://medibuntu.org/](http://medibuntu.org/)

Install totem-xine if you desire dvd menu navigation. I would have suggested using the default totem-gstreamer but it doesn't seem to be playing nice with dvd playback, and i don't know why.
You can find the totem packages via Synaptic (not sure about add/remove)
I know with the gstreamer backend some colors look muted particularly among asf files never compared a screenshot of a dvd played in say totem-xine and one in totem-gstreamer.
If its muted colors i don't know what else to suggest besides try playing around with the media player controls see it that helps.

---

### Post by mschraier on 2008-01-16
Issue Resolved !!!!   I followed reassuringlyoffenseives directions for installing VLC  via terminak.  Not only does it work, but the video is also cleared up.  Thanks guys !!!   :):):):):):):):)

---

### Post by ubuntu-freak on 2008-01-16
I added faac and faad to the essential extras bit in my post. You need them for making 3g2 and mp4 vids. 
 
Have another look at the DVD section cos I made some additions.
 
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)


Nathan

---

