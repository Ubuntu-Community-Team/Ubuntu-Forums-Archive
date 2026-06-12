---
title: "How to install windows media player plugin to mozilla"
date: 2007-10-16
forum: Multimedia &amp; Video
---

### Post by Akacko on 2007-10-16
Hi,
i found some stream videos ([here]("http://www.wwe.com")) that can be played only in WMPlayer. I'm using Mozilla Firefox and i didnt found any useable plugin.

Do you have experiences whit this problem. Can you give me some advices? thx

---

### Post by yabbies on 2007-10-16
make sure Universe and Multiverse repositories are open.

system>administration>system sources

on the Ubuntu Software tab
make sure the Universe and Multiverse boxes are checked.

close out system sources

go back to system>administration>synaptic package manager

in the synaptic search for 

totem-xine-firefox-plugin   

mozilla-mplayer 

flashplugin-nonfree

check the box on each one for installation and click apply

---

### Post by Akacko on 2007-10-17
it works. Thank you very much ;)

---

### Post by nisarg on 2007-10-17
Hello there, 

I am facing some real serious problems streaming windows media videos on Firefox. I have tried all the HOW Tos and instructions I could find on internet.
I believe I have everything installed. I also have totem-xine-firefox-plugin  and Mediaplayer connectivity tool along with all the players that I think I should need.
However, I am still unable to view windows media streams. I can watch flash video (eg Youtube videos) but not any other streams (eg: mms://...... .wmv). 

Please see the attached screenshot of the installed Sound & Videos softwares.
Any help to resolve the problem will be more than appreciated.

Any suggestions if this might be problem due to vga drivers? If so, should I try installing ATI drivers as mentioned here [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
 
Thanks in advance.



> **yabbies said:**
> make sure Universe and Multiverse repositories are open.

system>administration>system sources

on the Ubuntu Software tab
make sure the Universe and Multiverse boxes are checked.

close out system sources

go back to system>administration>synaptic package manager

in the synaptic search for 

totem-xine-firefox-plugin   

mozilla-mplayer 

flashplugin-nonfree

check the box on each one for installation and click apply

---

### Post by nisarg on 2007-10-18
I think Ubuntu is a great OS, and want to make it my primary working systems but I admit being a n00b. But its this type of bits that it is frustrating, and putting me off. I would hate to go back to ms windows or have a dual boot..
I know Ubuntu has a great community here, and there are folks who know a lot about their machines and are ready to help

---

### Post by perixx on 2007-10-18
Hi nisarg,


did you install the proprietary 'w32codecs' from the medibuntu repositories? If not, go to the last page of this link and follow that description:

[http://ubuntuforums.org/showthread.php?t=574241](http://ubuntuforums.org/showthread.php?t=574241)

greetz,


perixx

---

### Post by nisarg on 2007-10-18
Hi,
Thank you for you response Perixx.
Yes - I do have w32codecs installed. 
I installed Gutsy Gibbon today in anticipation that I will manage to get it to work. But no luck. A lot of the streams I watched on windows does not work.
I have Mplayer, Mplayer-Mozilla, gstreamer, w32codecs, flash and for dvd playback libdvdcss2 installed..
But I still cannot view certain streams. Some seem to work though not all.. Unfortunately I heavily rely on the ones that dont.. Like this one mms://starplus.servehttp.com/BollyWoodPromo.com-AajTak-lebeesadwwddTVe
The video seems to have got some flash intro which plays, and it shows stopped
I appreciate all your help. Please let me know if I can post any addition information that will help to diagnose and fix the issue.
Thanks

---

### Post by capt scroggins on 2007-10-21
Having exact same problem. Totem-mozilla starts up, it buffers and looks like it is going to play and then nothing ever happens. I tried Totem and mplayer.

---

### Post by perixx on 2007-10-22
Hmm. Maybe I should mention, that I'm using Xubuntu 7.04 and I really tried MANY things in order to get all the videos playing. ONE thing first, though: I cannot remember getting .wmv's to work with Mplayer! The only combinations that worked for me with .wmv's were: Totem-gstreamer or VLC. There was some odyssey in adding new repositories and codecs to be done  - so in the end I'm really not sure, what lead to success...

Unfortunately, I messed up my desktop by reverting to German repositories again and I can't access crap now :P
So, if I have made it working again or set it up once again, I'll be able to dig up some more info again for you... might take a few days, though.

greetz,


perixx

---

### Post by perixx on 2007-11-07
Update: 

I DID get SMPlayer/Mplayer to work with .wmv files now, also in Firefox! It plays some sorts without any hassle (I think wmv9) and some others I only managed to have them opened by the external Mplayer, but they DO get played at least... 

I would prefer SMPlayer over Mplayer any time, it is a pretty neat frontend!


perixx

---

