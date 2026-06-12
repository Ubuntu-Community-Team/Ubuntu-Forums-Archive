---
title: "Divx in Ubuntu 11.04?"
date: 2011-05-14
forum: Multimedia Software
---

### Post by mamaj on 2011-05-14
I use a website to watch online episodes. Its based on  divX web player version 1.5 + FF greasemonkey script. Will this work if i upgrade from windows to ubuntu?

---

### Post by mamaj on 2011-05-14
any ideas?

---

### Post by jamesjenner on 2011-05-14
well I cannot comment about the FF greasemonkey script, but divX appears to work fine for me on 11.04. I've not noticed anyone posting problems with it either.

---

### Post by mamaj on 2011-05-15
but is that the new version or experimental from divx labs?

---

### Post by mamaj on 2011-05-15
can anyone with ubuntu actually confirm that this [site]("http://www.icefilms.info/ip.php?v=2105&") works in linux? thanks
you just have to play the video

---

### Post by mamaj on 2011-05-15
any0ne?

---

### Post by spur on 2011-05-15
I had a quick look at this site and it seems that if you use VLC, which is in the repository for Ubuntu, you probably can use this site. It seems that the players for playing directly are for win and Mac only, but a workaround could be out there.
The info for Vlc in the repository says playing streaming divx so would be worth a try.

---

### Post by jamesjenner on 2011-05-15
I can check when I get home (currently at work) but that won't be for another 9 hours.

Cheers,

James.

---

### Post by mamaj on 2011-05-15
could you check? im not quite sure how vlc workaround suppose to work

---

### Post by spur on 2011-05-15
I have successfully watched a video from the site.
I used Kmplyer,making sure first I had ac3 codec installed and Grease monkey and the script. Worked fine even if it took a little while to download the file.

---

### Post by mamaj on 2011-05-15
> **spur said:**
> I have successfully watched a video from the site.
I used Kmplyer,making sure first I had ac3 codec installed and Grease monkey and the script. Worked fine even if it took a little while to download the file.

So did you actually had to download a file or did you stream it form the web and just wait a bit for it to load first?

---

### Post by spur on 2011-05-16
I ended up downloading the file. To do that i had to use the method described on the site (GreaseMonkey and the script) It seams it should be possible to use VLC to stream, but I couldn't.

---

### Post by mamaj on 2011-05-16
> **spur said:**
> I ended up downloading the file. To do that i had to use the method described on the site (GreaseMonkey and the script) It seams it should be possible to use VLC to stream, but I couldn't.

how would exactly vlc streaming work?

---

### Post by spur on 2011-05-16
I only used it once, but you open it up and set it to auto reconnect (under video sources under settings). The under 'stream' you insert the url the start it. If you go to the page you can copy the adress, but its not immediatly apparent. You have to look.
VLC is easy to install being in the repositories and easy to find and simple to use.  Also the page you directed to has instructions on how to use it. It does stream so I don't think it downloads the whole file first.
If this is the only thing holding you back from installing Ubuntu why bot install using Wubi? That way you will be sure to retain your windows installation. You could also just run the live cd, but nay changes you make will not be permanent. Using the live cd does nothing to your computer. Thats nothing as in the big zero. :D

---

### Post by mamaj on 2011-05-17
well i tried both ways running ubuntu, but my pc just doesnt play nice, so the only way ( i hope) ubuntu will actually work is if i installed it. So id apprecialte if someone could test it out for me before i change my system from XP.
i've found out that if you also use gecko media player it might work:
sudo apt-get install gecko-mediaplayer

---

### Post by mamaj on 2011-05-17
can anyone test it or see if the site works in their browser?

---

### Post by beew on 2011-05-17
> **mamaj said:**
> can anyone test it or see if the site works in their browser?

A link?

---

### Post by mamaj on 2011-05-17
> **beew said:**
> A link?

[http://www.icefilms.info/ip.php?v=132950&](http://www.icefilms.info/ip.php?v=132950&)

you just have to select a source from the list and hit play after. At least thats the procedure in Windows

---

### Post by beew on 2011-05-17
Yeah, I can confirm that it works. Just click play and wait for it to load like you would in Windows. Also you can play the video in flash.

Basically you need to installl gecko-mediaplayer (which is a mplayer Firefox plugin) , Ubuntu restricted extras and a bunch of non free codecs (win32 is probably the relevant package for this site) from Medibuntu. (Edit: Of course you need greasemonkey and installing the script)

This is Ubuntu 10.10 though, I am experimenting with installing ffmpeg from source in 11.04 at the moment and I have uninstalled a bunch of stuffs so multimedia stuffs probably won't work. I wouldn't even try. :)

---

### Post by mamaj on 2011-05-17
> **beew said:**
> Yeah, I can confirm that it works. Just click play and wait for it to load like you would in Windows. Also you can play the video in flash.

Basically you need to installl gecko-mediaplayer (which is a mplayer Firefox plugin) , Ubuntu restricted extras and a bunch of non free codecs (win32 is probably the relevant package for this site) from Medibuntu. (Edit: Of course you need greasemonkey and installing the script)

This is Ubuntu 10.10 though, I am experimenting with installing ffmpeg from source in 11.04 at the moment and I have uninstalled a bunch of stuffs so multimedia stuffs probably won't work. I wouldn't even try. :)

Ok, now Im a bit confused. ISo you installed gecko + win32 package for the video to be able to stream, but now multimedia doesnt work?

---

### Post by beew on 2011-05-17
> **mamaj said:**
> Ok, now Im a bit confused. ISo you installed gecko + win32 package for the video to be able to stream, but now multimedia doesnt work?


No, I mean it works in ubuntu 10.10, as you can see from the screenshot.  But I haven't tested it on 11.04 because I am messing with the system at the moment so I don't expect it to work.

---

### Post by beew on 2011-05-18
It works on 11.04 too.

---

### Post by mamaj on 2011-05-18
> **beew said:**
> It works on 11.04 too.

fantastic! just 2 more things.
how do you actually install the player(can you do it from the new software store?)
and how did you make the resize/close buttons appear all the way on top?

---

### Post by beew on 2011-05-18
You need to install gecko-media player, you can find it in Synaptic (it is a much better tool to install software than the Software Centre, which I don't use). When you install that it will pull in all the dependencies including  mplayer, which is the backend.

The version of mplayer from the default repo is probably not up to date or broken based on past experience so I recommend installing it using a ppa. There are two good ones I know but I use this one[ https://launchpad.net/~ripps818/+archive/coreavc]("https://launchpad.net/%7Eripps818/+archive/coreavc")
(Don't worry about the coreavc stuffs and dshowserver, you just need mplayer, it is an excellent build) (another one is the MOTU ppa which most people recommend, but ripps' actually works better on my Natty install)

To add the ppa to your sources list you open Synaptic, go to Settings > Repositories > Other Software and add the line > **[B]ppa:ripps818/coreav**[/B] and then close the dialogue box and reload Synaptic, when you install gecko-mediaplayer it will pull the latest version of mplayer from the ppa instead of from the Ubuntu official repo.

I don't understand the second question, there are no buttons on the top, they are at the bottom (see first screen shot) when you go full screen the status bar becomes hidden but you can expose it by putting the mouse cursor at the bottom of the screen.

One little hint, gecko-player tends to start playing a bit too soon when streaming, so stop it and wait for it to load a bit more (say 40%) before start playing. If it starts playing  too soon (like 10% loaded) then chances are it will stop when the stream doesn't catch up with play back. There are ways to configure it to start when a certain % is loaded but I have to look it up.

BTW, I tested your link on my friend's Vista machine, it actually works better on Ubuntu (Firefox freezes in vista and divx player crashes several times). :)

Enjoy.

**EDITED:** Since Totem is the official video player the totem-mozilla plugin may be installed by default, you need to uninstall or disable it to use gecko for Divx. I don't know if the Totem plugin was installed because I removed Totem and installed mplayer as soon as I set upl Ubuntu.

---

### Post by beew on 2011-05-18
Oh, you need to get the media codecs from the Medibuntu ppa (non free)

Instructions here.
[URL="http://www.ubuntuupdates.org/ppas/11"]http://www.ubuntuupdates.org/ppas/11
[/URL]

---

