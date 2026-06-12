---
title: "What is mms?"
date: 2008-05-23
forum: Multimedia Software
---

### Post by GoCool on 2008-05-23
Hi I have a streaming video link which plays fine in my windows machine, but in ubuntu, it keeps giving me the following error

> The following components are required: mms

In the repository I did not find anything for mms, but something for mimms which says:

> MMS (e.g. mms://) stream downloader
MiMMS is a program designed to allow you to download
streams using the MMS protocol and save them to your
computer, as opposed to watching them live. Similar
functionality is available in full media player suites
such as Xine and MPlayer, but MiMMS is quick and easy
to use, and for the time being, remains a useful program.

So my question is:

1. How to play an mms in ubuntu, the mimms is for downloading I suppose. But I might be wrong.

Thanx again.

---

### Post by xc3RnbFO8P on 2008-05-23
You should be able to play it with VLC.

---

### Post by cor2y on 2008-05-23
yes mimms is for downloading.
Any media player can play mms.
mms is a stream protocol for wma/wmv/asf streams so totem, mplayer, vlc can play media streamed via the mms protocol.
mimms can download the streams , as can mplayer or vlc.

---

### Post by GoCool on 2008-05-23
> **cor2y said:**
> yes mimms is for downloading.
Any media player can play mms.
mms is a stream protocol for wma/wmv/asf streams so totem, mplayer, vlc can play media streamed via the mms protocol.
mimms can download the streams , as can mplayer or vlc.

I get the following error while using:

**_Totem Player_**

> Could not open location; you might not have permission to open the file


**_Helix Player_**

> The player does not have the capabilities to play back this content.
The following components are required: mms

**_Real Player_**
> The player does not have the capabilities to play back this content.
The following components are required: mms


I tried to log into windows environment just to check the link. And there is no problem there. 

Any help on this would be highly appreciated.

---

### Post by cor2y on 2008-05-23
I am not familiar with either helix or the real player.
Helix is probably only designed for real media streaming while the real player requires some sort of addon/plugin to handle mms streams.
But i do know totem can play mms streams if that says theres is some error, try playing the stream in vlc or mplayer , in mplayer its Open->Player Url or via the terminal```
mplayer mms://mms address here
```Vlc File->Open Network Stream (Ctrl+N) or via the terminal```
vlc mms://mms address
```
Or give the mms address here.

---

### Post by audwan on 2008-05-23
You might need totem-xine.

Ref: [http://ubuntuforums.org/showthread.php?p=1777737](http://ubuntuforums.org/showthread.php?p=1777737)

---

### Post by GoCool on 2008-05-23
> **audwan said:**
> You might need totem-xine.

Ref: [http://ubuntuforums.org/showthread.php?p=1777737](http://ubuntuforums.org/showthread.php?p=1777737)

I installed totem-xine but still no luck. Its giving the below error now.

> There is no input plugin to handle the location of the movie.

---

### Post by GoCool on 2008-05-23
> **cor2y said:**
> I am not familiar with either helix or the real player.
Helix is probably only designed for real media streaming while the real player requires some sort of addon/plugin to handle mms streams.
But i do know totem can play mms streams if that says theres is some error, try playing the stream in vlc or mplayer , in mplayer its Open->Player Url or via the terminal```
mplayer mms://mms address here
```Vlc File->Open Network Stream (Ctrl+N) or via the terminal```
vlc mms://mms address
```
Or give the mms address here.

Thank you. mplayer is working for me via terminal 
Highly appreciated.

---

### Post by mario@chianti-doc.com on 2008-07-13
Any media player can play mms.
This simply NOT TRUE !

I have Hardy 8.04 and i tried for months to ply video in MMS protocol from this Italian WEB [www.tg5.mediaset.it](www.tg5.mediaset.it) Unfortunately with NO success !

Can anybody be able to play those video ?

Thanks for your Help


Mario

---

### Post by Vivaldi Gloria on 2008-07-14
I can play everything including

> **mario@chianti-doc.com said:**
>  [www.tg5.mediaset.it](www.tg5.mediaset.it) 

without a problem.

First add the medibiuntu repos. Then

```
sudo apt-get remove --purge totem-mozilla
sudo apt-get install mozilla-mplayer
```

---

### Post by mario@chianti-doc.com on 2008-07-14
> **Vivaldi Gloria said:**
> I can play everything including



without a problem.

First add the medibiuntu repos. Then

```
sudo apt-get remove --purge totem-mozilla
sudo apt-get install mozilla-mplayer
```
Thanks for the suggestion, but is NOT working: I can ply the video for 1 second and then i receive a STOP message and I also lousing the connetion with mediaset.it .
Maybe we need to install more plugins for Firefox.
Anyway thanks.

Mario

---

### Post by Vivaldi Gloria on 2008-07-14
> **mario@chianti-doc.com said:**
> I can ply the video for 1 second and then i receive a STOP message and I also lousing the connetion with mediaset.it .

Weird. Are you sure you are using the mplayer from the medibuntu repos? Try right clicking mplayer in firefox and change the settings. I can see those videos without a problem in firefox 3. Here's a snapshot.

---

### Post by mario@chianti-doc.com on 2008-07-15
Thank you again.
Since I'm not a super expert in Ubuntu, can you explain what you mean when you said open Firefox 3 right click and change the setting ...?
I can do   about:plugins    and see the registry of firefox, but this is as far i can go.

When I open that web I can play iy for 10 seconds, but then STOP and I even loose the internet connection?!? and my router crash and I have to reset the router to reconnect ?!? I really do not understand why this happen !

Thanks for your Help


Mario

---

### Post by Vivaldi Gloria on 2008-07-15
> can you explain what you mean when you said open Firefox 3 right click and change the setting ...?

I mean right click a playing video in mplayer in firefox and choose settings.

> When I open that web I can play iy for 10 seconds, but then STOP and I even loose the internet connection?!? and my router crash and I have to reset the router to reconnect ?!? I really do not understand why this happen !

That's really weird. It seems that your firefox is not to blame but you have a problem with your router. I've heard of emule crashing a router but never heard of a media stream (mms) crashing a router before.

If I were you I would borrow a different router from a friend and try if it works without crashing on that page. If it works then it is really your router which has a problem.

---

### Post by mario@chianti-doc.com on 2008-07-15
"I mean right click a playing video in mplayer in firefox and choose settings."

The problem is that now I never arrive to ply a video. When I go to the [www.tg5.mediaset.it](www.tg5.mediaset.it) and click on "Ultime Notizie" an other screen came up with the message "done" and nothing happen.

For the routher I do not understand why is working allways and only when I try to see mms videos I have the crash ?!?

Thanks again


Mario

---

### Post by Vivaldi Gloria on 2008-07-15
> The problem is that now I never arrive to ply a video. When I go to the [www.tg5.mediaset.it](www.tg5.mediaset.it) and click on "Ultime Notizie" an other screen came up with the message "done" and nothing happen.

Try another video site and right click there. For example try

[http://www.ntvmsnbc.com/modules/habervideo/video.asp](http://www.ntvmsnbc.com/modules/habervideo/video.asp)

>  For the routher I do not understand why is working allways and only when I try to see mms videos I have the crash ?!?

I don't understand either. ;) Try another router to make sure.

---

### Post by mario@chianti-doc.com on 2008-07-15
Yes I can play your site, but no audio (not a problem).
Then I right click on the video and I have several options: one is configuration.
Tell me what I need to do at this time !

Thanks


Mario

---

### Post by Vivaldi Gloria on 2008-07-15
> **mario@chianti-doc.com said:**
> Yes I can play your site, but no audio (not a problem).
Then I right click on the video and I have several options: one is configuration.
Tell me what I need to do at this time !


Click configuration.

Try changing sound to OSS. Reload the page. If sound still does not work try to change to others (alsa, pulse, etc). 

Enable wmv support. 

Try caching 5% using the slider.

Also try different video settings: x11, g1, xv.

But to be honest, I don't think that these changes will make a difference when it comes to watching your site, because your router screws up in that site. But try anyway.

---

### Post by mario@chianti-doc.com on 2008-07-15
The audio is still not working but all the test that you required are working.
Could be that the problem is the routher, but I'm not sure.
The funny thing is that when I try to watch the same video using MS XP operating system the routher is not crushing and I do not have any problems!!! Why, it is a mistery !

Thanks


Mario

---

### Post by Vivaldi Gloria on 2008-07-15
> The audio is still not working but all the test that you required are working.

Hardy uses the new pulseaudio and everybody is having problems with sound. I fixed mine following the guides:

[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

[http://ubuntuforums.org/showthread.php?t=776739](http://ubuntuforums.org/showthread.php?t=776739)

> Could be that the problem is the routher, but I'm not sure.
The funny thing is that when I try to watch the same video using MS XP operating system the routher is not crushing and I do not have any problems!!! Why, it is a mistery !

Yes, that's really weird. 

> Thanks

You're welcome.

---

