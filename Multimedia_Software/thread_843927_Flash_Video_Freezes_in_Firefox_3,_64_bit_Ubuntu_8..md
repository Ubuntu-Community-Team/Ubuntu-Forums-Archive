---
title: "Flash Video Freezes in Firefox 3, 64 bit Ubuntu 8.04"
date: 2008-06-28
forum: Multimedia Software
---

### Post by dbsoundman on 2008-06-28
I'm having an issue that I've seen others allude to but I'm not sure if my problem is the same. I just built this new computer today, 2.7GHz Athlon 64 dual core processor, Asus mobo with built-in ATI Radeon 3200 graphics, and for a while youtube was working fine. Just now, I tried watching a couple youtube videos, but both videos playback froze at 2 seconds in, even with the full video loaded. I tried myspace videos too. I'm pretty sure this has something to do with flash, but I'm not sure what. I installed the regular flash plugin. Is there something I need to tweak?

Thanks,
Dan

---

### Post by markbuntu on 2008-06-29
I fixed that by getting flash 10. You can download the tar.gz from adobe and unpack it with archive manager and replace the libflashplayer.so in usr/lib/flashplugin-nonfree with the new one and throw the rest in the trash. Do not run the installer.

That should be all you need to do.

---

### Post by dbsoundman on 2008-06-30
I just tried that. It worked when I made the switch (which was not long after turning the computer on), but now the videos freeze every 2 seconds again. Any ideas as to what changes that would make the videos freeze once the PC has been running for a while?

-Dan

---

### Post by thegr8brian on 2008-07-03
any sollution to this?

---

### Post by dbsoundman on 2008-07-03
Not so far...I've tried the other flash plugins like gnash and the other I can't remember of the name of, and they worked, but not on all sites (ex. gnash wouldn't work on youtube, the other one wouldn't work on weather.com)...

-Dan

---

### Post by thegr8brian on 2008-07-03
Yea I actually tried two different plugins as well but not success.  This is really annoying...

---

### Post by benign on 2008-07-04
I had the same problem in both Opera and FF, and came up with a solution that worked at least for me. I just reinstalled the packages.

```

sudo apt-get --reinstall install flashplugin-nonfree lib32nss-mdns

```

---

### Post by ubuntu-freak on 2008-07-04
Make sure that libflashsupport isn't installed. Also, see if the troubleshooting section of my [how-to](ubuntuforums.org/showthread.php?t=766683) helps.

---

### Post by thegr8brian on 2008-07-05
> **reassuringlyoffensive said:**
> Make sure that libflashsupport isn't installed. Also, see if the troubleshooting section of my [how-to](ubuntuforums.org/showthread.php?t=766683) helps. If you still have problems, give the beta 1 Flash a try:
 
[http://launchpadlibrarian.net/14730407/flashplugin-nonfree_10.0.1.218ubuntu1~8.04~mt.tar.gz](http://launchpadlibrarian.net/14730407/flashplugin-nonfree_10.0.1.218ubuntu1~8.04~mt.tar.gz)

wow I think this worked for me...turns out libflashsupport was installed so I uninstalled it and it seems to be working...Thanks!!!

---

### Post by ubuntu-freak on 2008-07-05
Yeah, that package was only needed when Hardy was first released.
 
The beta of Flash v10 is worth trying, you can always revert to v9 afterwards if you want.

---

### Post by tehquickness on 2008-07-10
I am stuck. I have tried all of the above, and I still have no luck. Ubuntu 8.04 64bit, I am also getting no sound with flash either. Any idea what could be causing this or how to trouble shoot it?

Thanks

---

### Post by ubuntu-freak on 2008-07-10
> **tehquickness said:**
> I am stuck. I have tried all of the above, and I still have no luck. Ubuntu 8.04 64bit, I am also getting no sound with flash either. Any idea what could be causing this or how to trouble shoot it?

Thanks

 
Have a look at the troubleshooting section in my [how-to](ubuntuforums.org/showthread.php?t=766683), you need to install Adobe Flash Player v10 beta for better audio and video performance.

---

### Post by markbuntu on 2008-07-10
You also need to install nspluginwrapper for flash to work on 64bit. There is a guide at the top of the 64 bit forum. There is also one for getting java to work.

---

### Post by ubuntu-freak on 2008-07-10
> **markbuntu said:**
> You also need to install nspluginwrapper for flash to work on 64bit. There is a guide at the top of the 64 bit forum. There is also one for getting java to work.

 
The nspluginwrapper package is installed automatically with flashplugin-nonfree and stays installed even if you purge flashplugin-nonfree, that's why I didn't mention it.

---

### Post by tchalvakspam on 2008-08-31
Yeah, I'm getting the same problem, the weird thing is that the problem arose, so I can only guess that it might have to do with some software that I installed or some update to firefox that was done.  Or even an extension that's installed.  *sighs*

---

### Post by koolguynet on 2008-08-31
I too am getting the same problem.  Does this have anything to do with the new kernel?  When I use flash it only displays the first two seconds of a video and kills my sound for the rest of the session.  This really sucks!  Help!

---

