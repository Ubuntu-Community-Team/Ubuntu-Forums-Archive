---
title: "Cnn"
date: 2008-01-15
forum: Multimedia &amp; Video
---

### Post by sumithar on 2008-01-15
This is most frustrating,when I tried a video on the CNN site I get the message
UNSUPPORTED PLATFORM ERROR:
This video is not supported on the current platform (browser/operating system). For technical issues, use the FAQ

I tried changing the UserAgent (using the FF extension) to IE.  Now I get a nice black screen.

I am using FF 2.0.08 on Ubuntu Feisty.

After looking at some earlier posts I have removed the totem plugin and have the much touted mozilla-mplayer plugin.   
sudo apt-get install mozilla-mplayer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mozilla-mplayer is already the newest version.

sudo apt-get remove totem-mozilla mozilla-plugin-vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package totem-mozilla is not installed, so not removed

Quite frankly, to all you incredibly  helpful souls out there, I don't know if I can take too much more of this plugin-codec crap.

I spent aeons getting the BBC site's videos to work.  It is just too much of a hassle.

For instance I came across this great site
[www.idesitv.com](www.idesitv.com) which works perfectly fine in FF on XP but no dice on Ubuntu!

---

### Post by yabbadabbadont on 2008-01-15
I'm pretty sure that CNN uses Flash for videos, so the mplayer-plugin wouldn't help.  Don't quote me on that though.

Edit: [www.idesitv.com](www.idesitv.com) works for me with mplayer-plugin.

---

### Post by wolfen69 on 2008-01-15
> **sumithar said:**
> 

For instance I came across this great site
[www.idesitv.com](www.idesitv.com) which works perfectly fine in FF on XP but no dice on Ubuntu!

[www.idesitv.com](www.idesitv.com)  works perfectly for me. but then again, im using the ubuntu spinoff- LinuxMint. codecs in mint are near flawless. but then again, ubuntu ***can*** be setup the same way.

---

### Post by kostkon on 2008-01-15
Please check [this documentation here]("https://help.ubuntu.com/community/RestrictedFormats").

You have to install the *w32codecs* codec package from the [*Medibuntu repository*]("https://help.ubuntu.com/community/Medibuntu") in order to play *Windows Media* files and streams.

I assume that [http://www.idesitv.com/](http://www.idesitv.com/) uses *Windows Medi*a that's why it does not work for you.

---

### Post by sumithar on 2008-01-16
Well, the regular CNN videos work- perhaps they do use flash, if I click on "live video" i get that unsupported platform error.  I followed the instructions on that link about adding restricted repositories.
Then I tried to add the medibuntu w32codecs.   It said they were already installed but I reinstalled them anyway.
Still no luck with idesitv.com

It says on the top
mplayer plugin
embedded video player for mozilla

Then...
I get a series of messages
Initializing
connecting to string of numbers (an IP address)
buffering
then stopped

about : plugins shows 2 entries for mplayer.  
First one is
**Windows Media Player Plugin**

    File name: mplayerplug-in-wmp.so
    mplayerplug-in 3.31

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets
followed by a table with a bunch of mime-type and description entries

Second one is
**mplayerplug-in 3.31**

    File name: mplayerplug-in.so
    mplayerplug-in 3.31

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

Both look more or less the same to me.

I don't see an entry for totem plugin.
 
Honestly, is it this difficult to get the mplayer plugin to work?

I have been using Ubuntu for well more than a  year now and it has been an uphill struggle- it took me ages to get my wireless lan adapter to work, my sound card support was erratic till I found a page on this forum that was the canonical guide, i wasted a lot of time figuring out that shockwave support didn't exist, I miss being able to use Irfanview, I miss having a utility like YankeeClipper that lets me accumulate my clipboard entries, I miss being  able to play music on [www.musicindiaonline.com](www.musicindiaonline.com) and now this!

Ok- I had to get that off my chest, sorry about that...

---

### Post by sumithar on 2008-01-18
OK- I upgraded to 7.10 and that seems to have fixed the idesitv problem- kinda sorta.

I can see the video and listen to audio but both are very choppy...any suggestions?

Thanks

---

