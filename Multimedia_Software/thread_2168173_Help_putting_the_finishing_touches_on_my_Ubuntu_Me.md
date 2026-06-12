---
title: "Help putting the finishing touches on my Ubuntu Media server."
date: 2013-08-16
forum: Multimedia Software
---

### Post by ccovemaker on 2013-08-16
Hello all,

Thank you in advance.

**Hardware:**
Lenovo ThinkCentre M58
3.0Ghz dual core 
3GB of Ram
2TB WD Green drive (OS and storage) 
Ubumtu 12.04 Desktop (I am hoping for appliance like reliability so LTS)
Linksys E1000 router

Feeding 2 Win 8 gaming PCs, Roku's, Android Phones, and 1 Nexus 7

**Background:** I work in IT maybe my best effort setting this up and it has worked for the most part but I work in an entire Windows OS environment so some of this I am having issues with.

[B]Problems:
[/B]So i won this desktop at work as we cycled them out EOF.  I thought it would make the perfect home media server for my movie and TV library.  It was hosted on my Win 8 gaming machine but that is quite loud even at idle so I wold give the dedicated server a go.

I was serving the various mobile devices and Roku's from the Plex Medis Server in Windows so that transition was easy as it was supported in Ubuntu straight away.

This is where this gets tricky at least for me.

I was intending to use this as a headless unit as the GF has put a global ban on more gear in the living room.  I do a great deal of my work on Windows RDC's and was hoping I was going to figure this out on my own.

Researching (aka Googling like mad):

I found some options:
[http://www.liberiangeek.net/2012/05/connect-to-ubuntu-12-04-precise-pangolin-via-windows-remote-desktop/](http://www.liberiangeek.net/2012/05/connect-to-ubuntu-12-04-precise-pangolin-via-windows-remote-desktop/)

Ran this process and seem to be running into the 2D error thing.  When I attempt to remote from windows all I get is a blank desktop with no icons and no way to interact.
Some of the comment brought up fixes but I didn't think blindly copy pasting commands into the Term sounded like a good idea.

Second attempt i followed:
[http://www.youtube.com/watch?v=KY3V79t5tKA](http://www.youtube.com/watch?v=KY3V79t5tKA)

Following his process never got me past the login as I am guessing I need to create accounts for the remote session.

That spins into new questions but I guess I will start there.

Can anyone help me get m Remote Desktop connection up and running.

Thanks,
Clayton

---

### Post by mikewhatever on 2013-08-16
> 
[http://www.liberiangeek.net/2012/05/...emote-desktop/](http://www.liberiangeek.net/2012/05/...emote-desktop/)

Ran this process and seem to be running into the 2D error thing. When I attempt to remote from windows all I get is a blank desktop with no icons and no way to interact.
Some of the comment brought up fixes but I didn't think blindly copy pasting commands into the Term sounded like a good idea.

Have you made sure the session is ubuntu-2d, as mentioned down the bottom?

---

### Post by ccovemaker on 2013-08-16
Following the link[URL="http://www.liberiangeek.net/2012/05/connect-to-ubuntu-12-04-precise-pangolin-via-windows-remote-desktop/"]

http://www.liberiangeek.net/2012/05/...emote-desktop/[/URL]

Yes infact I did but it got me to the same blank desktop.

Thinking i would try again I followed the video.  When I got to the bit about the .xsession file 

My file already contained the "gnome-session --session=ubuntu-2d" line.

In my not one of my better moments it had an addition line, thinking "hey thats not in the video!" I deleted it without backing it up just leaving "gnome-session --session=ubuntu-2d" as directed to in the video.

That actually back tracked the progress I had made as I am now not getting past the

"xrdp_mm_process_login_response:log in failed"


So login failed.  I was attempting to log into the admin account while it was running.  I thought maybe that was the issue so i created a second user in my name using the same password as either account.  I created both accounts and set both passwords and can verify all throughout the system that they do in fact work.

So I realize this step backwards was my mistake but when uninstalling and reinstalling and retrying to process i am back were I started.

Which is why i cam here for help as I guess I am over my head.

Does anyone have any idea what I need to add in that .xsession file to be able to get one step forward?

---

### Post by mikewhatever on 2013-08-16
Looks like you've been hitting [this bug]("https://bugs.launchpad.net/ubuntu/+source/xrdp/+bug/846407"). Essentially, xrdp can't display Unity, and the suggested workaround has not worked for everyone. Perhaps you should try Xubuntu or gnome-session-fallback (even though the latter is no longer supported).

---

### Post by ccovemaker on 2013-08-16
Well I have been using Teamviewer as a fall back plan which is OK but does not let me log in from a fresh reboot, i.e. not headless I have to log into the system then start teamviewer.

That and if I wanted something to constantly bug me for money I would have stayed with M$.

I was able to successfully set up VNC and Real VNCviewer as well  that seems to work but it does not get me past the log in again.

I would still like to have the Windows RDC working properly.

---

### Post by ccovemaker on 2013-08-16
I guess at this point what I really want is a service that will let me do the entire log in process from a fresh reboot.

---

### Post by mikewhatever on 2013-08-16
Just briefly tested xrdp, and it seems to work without messing with the .xsession file. The two machines run 12.04 with Unity2d, and cnnecting with Remmina was a piece of cake. I've only adjusted the resolution (the laptop I connected from has a very small screen) and color deapth (24bpp). Let me get hold of a Windows machine to test again.

---

### Post by mikewhatever on 2013-08-16
Doesn't work from Windows. It says "Failed to connect to session".

---

### Post by ccovemaker on 2013-08-17
Ok so after screwing my self with the deleting things I should not have (1st post).  I was looking for alternatives (5th post) installed VNC and RealVNC viewer.  Which works closer to what I want but still does not let me log in from a fresh login.


The good news is my default stock Window RDC is back to the 2D error so I back to were I started.

---

