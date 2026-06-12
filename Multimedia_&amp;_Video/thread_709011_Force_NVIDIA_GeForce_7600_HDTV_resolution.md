---
title: "Force NVIDIA GeForce 7600 HDTV resolution"
date: 2008-02-27
forum: Multimedia &amp; Video
---

### Post by linuxmunky on 2008-02-27
Hello and thanks for reading,

I've been working all day on switching my HTPC from Windows XP to Linux and I finally found success with Mythbuntu.  Here's the situation: I have the HTPC connected to the HDTV via component running from my GeForce 7600GS card.  I initially set up Mythbuntu to run at 720p, but the issue is that my Sony TV cuts off some of the screen (horizontally and vertically - some kind of widescreen mode).  Looking for solutions, someone suggested using 1152x648 as my resolution.  Sounds good, but as a newbie, I'm stuck as to how to do this.  Can someone give me a basic guide?

Thank you for any and all help!

---

### Post by Flying caveman on 2008-02-27
you may have to edit your /etc/X11/xorg.conf to add that resolution.

---

### Post by linuxmunky on 2008-02-27
Okay, I added the Modelines to the monitor section and the resolution to the card section, but still no luck.  In /var/log/Xorg.0.log, it says that my resolution is not defined.  Any ideas?  Thanks.

---

### Post by yoshimitsuspeed on 2008-03-14
I need to do the exact same thing. I have a HDTV as my second monitor and Nvidia-settings won't let me select the proper resolution. I figured I would need to edit xorg.conf but I don't know exactly what I need to edit.

I was also wondering if the nvidia driver on nvidias site is the same as the one in the repo or is there any difference?

---

### Post by elchico04 on 2008-03-15
Hey, I'm kind of a noobie at linux so bear with me.

I have a HDTV as my monitor and am using a nVidia FX series gfx card.
My monitors native resolution is 1360x768 (720p).

To change it to that what I did was open the nvidia-settings utility and then under "X Server Display Configuration". There I found that I had a lot more resolution options than I did in the screens and graphics utility that comes with ubuntu. I selected it and then clicked "save to X configuration file".
I have learned that it is best to back up your current xorg.conf file incase you mess something up.
I save the xorg.conf file as something with a different name, stop the X server, overwrite the xorg.conf with the new one you just made, then start the X server and cross your fingers.


Hope I could help.

---

### Post by yoshimitsuspeed on 2008-03-15
The most Nvidia-settings would allow is 1200something by 700 something. 
In windows I am running 1768 x 992 
I know I need to add this to xorg I just don't know what I need to do.

---

### Post by linuxmunky on 2008-03-15
Can anyone help us?  Thanks in advance!

---

### Post by Harksaw on 2008-03-18
I've got the exact [same problem]("http://ubuntuforums.org/showthread.php?t=678280"). Help?

---

### Post by yoshimitsuspeed on 2008-03-20
I found this thread which should help but haven't gotten around to trying it yet. 
[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)
I am also going to try to instal the driver from nvidias site to see if there is any diff since there was no reply on that question. I will let you guys know how it turns out.

---

### Post by yoshimitsuspeed on 2008-03-20
I have also been trying to figure out how to get it to function like dual screen does in windows. 
In linux twinview makes two monitors one big one. 
Seperate x screens completely seperates them but I don't want seperat x screens. 
I just want 2 seperate desktops that I can drag windows between like XP allows. 
How do I do that?

---

### Post by yoshimitsuspeed on 2008-03-22
> **linuxmunky said:**
> Hello and thanks for reading,

I've been working all day on switching my HTPC from Windows XP to Linux and I finally found success with Mythbuntu.  Here's the situation: I have the HTPC connected to the HDTV via component running from my GeForce 7600GS card.  I initially set up Mythbuntu to run at 720p, but the issue is that my Sony TV cuts off some of the screen (horizontally and vertically - some kind of widescreen mode).  Looking for solutions, someone suggested using 1152x648 as my resolution.  Sounds good, but as a newbie, I'm stuck as to how to do this.  Can someone give me a basic guide?

Thank you for any and all help!

I think what we need is NVTV. If you search here you will find a bunch of threads about it. 
I installed the kubuntu 8.x alpha with kde 4 and it has the resolution I need but the desktop is still bigger than my screen. NVTV has overscan modes and If I remember correctly this is what fixed the problem in windows. 
However if you search here it seems more people have trouble with NVTV than sucess. THere are a couple good How to threads here but I am too much of a noob to make them work so far.  I'm gonna keep trying though lol. 
I am thinking maybe we should mass a group of people to email Nvidia and let our presence be known.
I know Nvidia already has great support for the linux comunity compared to many others but their windows settings manager is still way nicer and more user friendly than linux. 

I tried the Beta driver from Nvidias site and as far as the settings manager as far as I can tell it's identical to Nvidia Settings.

---

### Post by linuxmunky on 2008-03-24
Interesting - yeah, thanks for the link.  I'm looking into NVTV, but I'll have to reinstall Ubuntu (I had to convert back to Windows because I just couldn't get it to work).  I like your idea about notifying NVidia, too.  Any further progress on your side, yosh?

---

### Post by yoshimitsuspeed on 2008-03-26
Been too busy to mess with it the last few days.

---

