---
title: "Can I watch recorded TV on a remote XBMC or Win7 box?"
date: 2011-09-09
forum: Mythbuntu
---

### Post by NooB Frank on 2011-09-09
Sorry - I know google is my friend but I am in information overload here.  

I have a mythbuntu 11.04 box that I have set up and after a month of wrenching I got the TV card to work.  

Next up - be able to watch the recorded content in the living room.  I have found 100 posts on various things but nothing seems to do the trick.  I found where they are stored and would love to just navigate to that location over the network on my XBMC but??  

If someone could just take a second and point me in the right direction I would appreciate it.

Thanks - Frank

---

### Post by madverb on 2011-09-09
[http://www.mythtv.org/wiki/XBMC](http://www.mythtv.org/wiki/XBMC)

XBMC has a mythtv fontend.

---

### Post by nickrout on 2011-09-10
> **NooB Frank said:**
> Sorry - I know google is my friend but I am in information overload here.  

I have a mythbuntu 11.04 box that I have set up and after a month of wrenching I got the TV card to work.  

Next up - be able to watch the recorded content in the living room.  I have found 100 posts on various things but nothing seems to do the trick.  I found where they are stored and would love to just navigate to that location over the network on my XBMC but??  

If someone could just take a second and point me in the right direction I would appreciate it.

Thanks - Frank

I believe that the xbmc frontend will not work at present - needs fixing.

However you can install a frontend on the computer, even on windows.

---

### Post by williammanda on 2011-09-10
> **nickrout said:**
> However you can install a frontend on the computer, even on windows.

How can this be done for windows Vista and or 7?

---

### Post by nickrout on 2011-09-10
> **williammanda said:**
> How can this be done for windows Vista and or 7?I am tempted to simply tell  you to google it but as I had the page open recently and have the link to hand:

[http://members.iinet.net.au/~davco/](http://members.iinet.net.au/~davco/)

I have used it on w7 but on a vista laptop it failed, I don't know why. Others have successfully used these binaries on vista.

---

### Post by badger_fruit on 2011-09-11
hello OP
For my Windows "back-ends" I use this --> [http://sudu.dk/mythtvplayer/](http://sudu.dk/mythtvplayer/)
There's still a number of bugs/issues but it's the quickest to get going and in 99 times out of 100, it works without any  issue ... as I write this, I am on my XP laptop, watching F1 on Live BBC1 over the mythplayer 

[[IMG]http://img5.imageshack.us/img5/2268/mythplayerforwindows.jpg[/IMG]]("http://imageshack.us/photo/my-images/5/mythplayerforwindows.jpg/")

Good luck but I think that client shown above will help you :D
Sorry, I forgot to say this client is my client of choice for W7 as well (can't comment on Vista as it's a 'bag o crap' and I have no vista machines) ... note that in W7 you need to RUN AS ADMINISTRATOR for some reason but as you can set that in the shortcut it's not a big deal

---

### Post by williammanda on 2011-09-11
badger_fruit
Thanks! This seems to work well so far on Windows 7.

---

### Post by nickrout on 2011-09-11
> **badger_fruit said:**
> hello OP
For my Windows "back-ends" I use this --> [http://sudu.dk/mythtvplayer/](http://sudu.dk/mythtvplayer/)

I assume you mean front-ends?

---

### Post by badger_fruit on 2011-09-12
> **nickrout said:**
> I assume you mean front-ends?
 
d'oh yes sorry, obviously concentrating more on the GP then posting lol, well spotted haha

---

### Post by praganzi on 2011-09-23
XBMC and Myth:  Yes, the current (Sep 2011) XBMC release (Dharma) doesn't support Myth 0.24.  If you have an earlier version of Myth, then the XBMC plugin works fine.  Dharma is V10, and "they" expect a 0.24 fix for XBMC 11.

The way I do it is to have Myth transcode the videos (took me a while to get it to work, until I manually set up a new transcoder profile that I named "Autodetect from 1080i"), and then UserJob#1 to move the transcoded video from /var/lib/mythtv/recordedtv (or whatever the hell it's called) to /home/*YOUR_USERNAME_HERE*/*YOUR_PUBLIC_FOLDER*, and the other XBMC boxes (including Xbox Classic) can then view the video over the internal network.

If your XBMCs can view the video resolution that you record in (my classic couldn't, hence the transcode), I see no reason why you can't just share your default recorded TV folder (subject to the usual security caveats). 

I use XBMC on the PVR computer wherever possible (it's plugged into the main TV), and the Myth plugin used as a frontend allows me to set recordings, and by (the plugin) getting Myth to stream, I can also watch un-transcoded recorded TV through the one XBMC interface.

XBMC supports UPnP, so I can't see any reason why it can't "serve" your videos (including transcoded recorded TV, but not untranscoded TV) to the rest of the network, be it Win7, XBMC_any_platform, 360, PS3 or Vista.  Even XP and Puppy.

---

### Post by RichardK3 on 2011-09-23
> **NooB Frank said:**
> Sorry - I know google is my friend but I am in information overload here.  

I have a mythbuntu 11.04 box that I have set up and after a month of wrenching I got the TV card to work.  

Next up - be able to watch the recorded content in the living room.  I have found 100 posts on various things but nothing seems to do the trick.  I found where they are stored and would love to just navigate to that location over the network on my XBMC but??  

If someone could just take a second and point me in the right direction I would appreciate it.

Thanks - Frank

Just install the MythBox plugin for XBMC.  

[http://code.google.com/p/mythbox/](http://code.google.com/p/mythbox/)

[http://forum.xbmc.org/showthread.php?t=43115&highlight=mythbox](http://forum.xbmc.org/showthread.php?t=43115&highlight=mythbox)

It provides a pretty complete MythTV frontend within XBMC.  Live TV does not currently work, but will with the next release of XBMC.  But scheduling and watching recordings from a MythTV backend on your home network works fine.

---

### Post by RichardK3 on 2011-09-23
> **RichardK3 said:**
> Just install the MythBox plugin for XBMC.  

[http://code.google.com/p/mythbox/](http://code.google.com/p/mythbox/)

[http://forum.xbmc.org/showthread.php?t=43115&highlight=mythbox](http://forum.xbmc.org/showthread.php?t=43115&highlight=mythbox)

It provides a pretty complete MythTV frontend within XBMC.  Live TV does not currently work, but will with the next release of XBMC.  But scheduling and watching recordings from a MythTV backend on your home network works fine.

Forgot to mention a couple of things:

Be sure to perform the steps in "Setup in MythTV" here:

[http://wiki.xbmc.org/?title=MythTV](http://wiki.xbmc.org/?title=MythTV)

And, since the current XBMC cannot stream recordings directly (the XBMC Eden release will), you will need to set up Samba shares for your recordings directories on the MythTV backend, and mount those shares on each computer running XBMC.  The MythBox options screen has a place to enter the share name(s).  

Hope this helps!

---

### Post by nickrout on 2011-09-23
> **praganzi said:**
> XBMC and Myth:  Yes, the current (Sep 2011) XBMC release (Dharma) doesn't support Myth 0.24.  If you have an earlier version of Myth, then the XBMC plugin works fine.  Dharma is V10, and "they" expect a 0.24 fix for XBMC 11.

The way I do it is to have Myth transcode the videos (took me a while to get it to work, until I manually set up a new transcoder profile that I named "Autodetect from 1080i"), and then UserJob#1 to move the transcoded video from /var/lib/mythtv/recordedtv (or whatever the hell it's called) to /home/*YOUR_USERNAME_HERE*/*YOUR_PUBLIC_FOLDER*, and the other XBMC boxes (including Xbox Classic) can then view the video over the internal network.

If your XBMCs can view the video resolution that you record in (my classic couldn't, hence the transcode), I see no reason why you can't just share your default recorded TV folder (subject to the usual security caveats). 

I use XBMC on the PVR computer wherever possible (it's plugged into the main TV), and the Myth plugin used as a frontend allows me to set recordings, and by (the plugin) getting Myth to stream, I can also watch un-transcoded recorded TV through the one XBMC interface.

XBMC supports UPnP, so I can't see any reason why it can't "serve" your videos (including transcoded recorded TV, but not untranscoded TV) to the rest of the network, be it Win7, XBMC_any_platform, 360, PS3 or Vista.  Even XP and Puppy.

Hard to know why you bother with all this when you could simply use mythfrontend. I use xbmc for what it is good at, but not for a mythtv frontend.

---

### Post by RichardK3 on 2011-09-23
> **nickrout said:**
> Hard to know why you bother with all this when you could simply use mythfrontend. I use xbmc for what it is good at, but not for a mythtv frontend.

I've never been able to make the MythTV frontend work reliably on a Windows box.  Using XBMC gives us an identical user interface on all of our computers, both Linux and Windows.

---

### Post by praganzi on 2011-09-23
Yup.  Wife Approval Factor.  All media interfaces have a universal look around the house, and with a shared database, films can be "resumed" from any room.  I haven't found a good frontend for the classic Xbox that isn't XBMC.

---

### Post by nickrout on 2011-09-23
> **RichardK3 said:**
> I've never been able to make the MythTV frontend work reliably on a Windows box.  Using XBMC gives us an identical user interface on all of our computers, both Linux and Windows.

On that basis, use myth for everything.

---

