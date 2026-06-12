---
title: "Unable to play Radio Canada streams"
date: 2009-04-26
forum: Multimedia Software
---

### Post by DShad on 2009-04-26
I give up.

After reading so many HOW-TOs, I'm still unable to play video streams similar to this link:

[http://medias-wm.radio-canada.ca/diffusion/2009/medianet/CBFT/Lepicerie200904221930_3.wmv?MSWMExt=.asf](http://medias-wm.radio-canada.ca/diffusion/2009/medianet/CBFT/Lepicerie200904221930_3.wmv?MSWMExt=.asf)

I've got the latest flash plugin, the mplayer plugin for Firefox, but still no luck. MPlayer tries to open the link, but then it stops.

Any help please?

---

### Post by kostkon on 2009-04-26
I can play the video stream just fine with *Totem* (Xine backend).

The stream is a windows media video; thus, you'll need to install the *w32codecs* (or the *w64codecs* package for 64bit systems) that is offered by the [*Medibuntu* repository]("http://medibuntu.org/").

Add this repository to your software sources list (instructions are [here]("https://help.ubuntu.com/community/Medibuntu")) and then go to *synaptic* and search for this package and install it.

*MPlayer* will be able to use these codecs. If you have it open, just restart it in order to see the new codecs. Do the same for *Firefox*, if you have it open, so that the *Mplayer* plugin will see the codecs too.

Hope that helps.

---

### Post by DShad on 2009-04-27
> **kostkon said:**
> I can play the video stream just fine with *Totem* (Xine backend).

The stream is a windows media video; thus, you'll need to install the *w32codecs* (or the *w64codecs* package for 64bit systems) that is offered by the [*Medibuntu* repository]("http://medibuntu.org/").

Add this repository to your software sources list (instructions are [here]("https://help.ubuntu.com/community/Medibuntu")) and then go to *synaptic* and search for this package and install it.

*MPlayer* will be able to use these codecs. If you have it open, just restart it in order to see the new codecs. Do the same for *Firefox*, if you have it open, so that the *Mplayer* plugin will see the codecs too.

Hope that helps.

The thing is, I just installed 1 fresh Ubuntu 9.04 on 1 computer, and Kubuntu 9.04 on the other.

Both have installed (k)ubuntu-restricted-extras and both have w64codecs.

I can play that stream flawlessly on the Ubuntu, but not on Kubuntu.

I also did another test on another website.  Here'sthe website and following is the difference I noticed from the 2 systems:

[http://fr.video.canoe.tv/video/actualit%C3%A9s/faits-divers/14304190001/deux-personnes-meurent-dans-un-accident/21181431001](http://fr.video.canoe.tv/video/actualit%C3%A9s/faits-divers/14304190001/deux-personnes-meurent-dans-un-accident/21181431001)

The only difference I noticed is the fact that if I open the Flash player debug console, I get "Detected bandwith: Not able to detect" with the Kubuntu system while the other gives me a result?!

I decided to format and re-install the Kubuntu system and got the same result.

Why and How can I fix that.

Many thanks

---

### Post by stewacide on 2009-04-27
I've never been able to get Radio Canada media - not just video but the plain audio streams too - to play reliably in Linux or in OSX, and I've put some effort into it, and no other website has ever given me any trouble on my Mac. It absolutely boggles my mind how they could spend so much time and effort designing a website so broken it excludes all non-Windows/IE users, but that's our tax dollars at work for ya' :)

It's especially irksome since they could just swipe a fully modern and working web presence from the CBC side.

---

### Post by DShad on 2009-04-28
> **stewacide said:**
> I've never been able to get Radio Canada media - not just video but the plain audio streams too - to play reliably in Linux or in OSX, and I've put some effort into it, and no other website has ever given me any trouble on my Mac. It absolutely boggles my mind how they could spend so much time and effort designing a website so broken it excludes all non-Windows/IE users, but that's our tax dollars at work for ya' :)

It's especially irksome since they could just swipe a fully modern and working web presence from the CBC side.

Have you tried the link I provided from canoe.ca?

As told, it works everytime with Ubuntu but never worked on Kubuntu.   Ay ideas?

---

### Post by stewacide on 2009-04-28
The Canoe video plays fine for me in Gnome w/ Firefox and Opera.

This sounds like it could be a KDE/Konqueror bug. Does the video play in Firefox run in KDE?

---

### Post by DShad on 2009-04-28
> **stewacide said:**
> The Canoe video plays fine for me in Gnome w/ Firefox and Opera.

This sounds like it could be a KDE/Konqueror bug. Does the video play in Firefox run in KDE?

I can see the advertisement just fine, but the REAL video (after the 15-30sec ad) that I don't see.  I see the "waiting circle" spinning forever... Without any video starting.

No it won't work with Firefox neither.

That's why I would like to know if someone who has Kubuntu 9.04 installed has the same behavior...

I don't want to mess up everything or re-format if this occurs to everybody.

I'd rather fill-up a report bug...

---

### Post by Grothendieck on 2009-05-06
Here is a trick to listen to the Telejournal for example:

First download VLC.

When you click on a link on the Radio-Canada's website a window will appear. On the top
of this window you can read an http address, for example:

[http://www.radio-canada.ca/audio-video/pop.shtml#urlMedia%3D/medianet/2009/CBFT/Telejournal200905012200.asx&promo%3DZAPmedia_Telejournal](http://www.radio-canada.ca/audio-video/pop.shtml#urlMedia%3D/medianet/2009/CBFT/Telejournal200905012200.asx&promo%3DZAPmedia_Telejournal)


The number that you care about is 200905012200 which identifies the file corresponding to 
the date of the Telejournal on the time line i.e.  2009 / 05 / 01/ 22h00.

In order to play the file you open VLC, click on media, open file and click on network and then you enter the following http address:

[http://www.radio-canada.ca/Medianet/2009/CBFT/Telejournal*.asx](http://www.radio-canada.ca/Medianet/2009/CBFT/Telejournal*.asx)

where * stands for 200905012200.

Then you click on play. If you wait for 10 seconds the Telejournal should start playing.
You can figure out how to play other files.

Cheers!!

Grothendieck

---

### Post by stewacide on 2009-05-07
What exactly is Radio Canada doing that makes their media so difficult to play in Linux? (and Mac OS)

---

### Post by jenkin507 on 2009-10-22
Look at 

[http://www.radio-canada.ca/apropos/aide/pdf/Linuxconsolevideo.pdf](http://www.radio-canada.ca/apropos/aide/pdf/Linuxconsolevideo.pdf)

[]("http://www.radio-canada/apropos/aide/Linuxconsolevideo.pdf")It is in french but I was able to muddle through and get it to work for me.

Hope that helps.

p

---

