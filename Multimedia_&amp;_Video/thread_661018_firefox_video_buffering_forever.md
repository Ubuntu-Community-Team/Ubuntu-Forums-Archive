---
title: "firefox video buffering forever"
date: 2008-01-07
forum: Multimedia &amp; Video
---

### Post by msrk on 2008-01-07
I have read lots of forum pages and tried lots of things and installed many video packages, plug-ins, codecds etc.  I cannot get streaming video working in firefox 2.0.0.11.  I can watch videos from my disk using mplayer.

At this point I'm not even sure what software/plug-in firefox is using.

Any advice would be appreciated.

Thank you,
Marc

---

### Post by msrk on 2008-01-10
After a lot of experimentation and documentation searching I have solved this problem for myself.  It is disconcerting that ubuntu 7.10 does not have basic web browser features working out of the box.  I would think anyone doing a little Q/A work before making the install iso files would have tested the default browser with a video feed like Reuters.com or cnn or the like.

So, here is the solution that worked for me.

1. Remove firefox completely.
2. Remove totem, mplayer, gnash, kaffeine, completely.
3. Install the iceweasel browser which requires adding the following repository.

    deb [http://http.us.debian.org/debian](http://http.us.debian.org/debian) etch main non-free contrib

    You can add this repository in the Synaptic Package Manager by menus Settings->Repositories.  Then choose "Third-Party Software".  Then click on "Add" and enter the line above verbatim.  Hit the "Reload" button on the Synaptic main window.  Syanptic may complain about a few problems with the repository and a GPG signature error.  I ignored them.

4. Search and install the iceweasel package.
5. Search and install the mplayer package.
6. Start iceweasel and visit cnn.com
7. You may be prompted to install the adobe flash player.  Do it.

This is what I did and it worked.  I would really love it if an Ubuntu expert could fix this.  I would appreciate it if anyone knows of a better way to solve this problem.

Marc.

---

### Post by Thoop on 2008-01-10
This is a bad solution as you are using a debian repository which could potentially break your ubuntu setup ;)
By default totem streams media in firefox I believe, otherwise install mozilla-mplayer

---

### Post by msrk on 2008-01-10
Thank you.  I tried your suggestion.  I have it working now with firefox and without the extra repository.  Here are the steps I took.

1. Remove firefox completely.
2. Remove totem, mplayer, gnash, kaffeine, completely.
3  Install firefox and mozilla-mplayer
4. visit cnn.com and 
    install "Adobe Flash Player" as suggested by firefox.

I think the 'mozilla-mplayer' package is necessary even though it is not suggested by synaptic.  I had tried this method before and it didn't work until I removed all other video plays and firefox first.  It didn't work until I installed mozilla-mplayer.

Thank you.

---

### Post by ubuntu-freak on 2008-01-10
Try my settings and advice to get the most out of the mplayer plugin.
 
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)
 
Nathan

---

### Post by msrk on 2008-01-10
Nathan, and all others.  Thank you for your replies.  The information you provided was useful and I believe I have my Ubuntu Firefox singing nicely and stable.

I still wonder why there wasn't good Q/A in this area to make sure the desktop ubuntu 7.10 desktop install didn't work out of the box.

---

### Post by ubuntu-freak on 2008-01-11
You might want to 
 
sudo apt-get install ubuntu-restricted-extras
 
Gets you everything you need for audio, video (DVD too) and browsing with one simple command. 
 
Nathan

---

### Post by msrk on 2008-01-24
Hi again,

I just set up another Ubuntu 7.10 desktop and installed ubuntu-restricted-extras.  This worked fabulously before but not this time.  When I try to view a video on the web Firefox requests that I install the adobe flash plugin.  I do and it seems to install flashplugin-nonfree.  But the video doesn' t play and the same flash install flash plugin request pops up.  I tried restarting firefox and reinstalling ubuntu-restricted-extras but I still can't get it to play.

Please advise.

Thank you,
Marc

---

### Post by ubuntu-freak on 2008-01-24
> **msrk said:**
> Hi again,

I just set up another Ubuntu 7.10 desktop and installed ubuntu-restricted-extras.  This worked fabulously before but not this time.  When I try to view a video on the web Firefox requests that I install the adobe flash plugin.  I do and it seems to install flashplugin-nonfree.  But the video doesn' t play and the same flash install flash plugin request pops up.  I tried restarting firefox and reinstalling ubuntu-restricted-extras but I still can't get it to play.

Please advise.

Thank you,
Marc

 
It's still broken. Go to my how-to
 
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)
 
Nathan

---

### Post by sf657 on 2008-01-24
msrk and reassuringly offensive- you have solved my biggest issues so far- thanx for the advice. I'm sure i'll be back for more real soon........

---

### Post by ubuntu-freak on 2008-01-25
> **sf657 said:**
> msrk and reassuringly offensive- you have solved my biggest issues so far- thanx for the advice. I'm sure i'll be back for more real soon........

 
No problem. Just thought it would be good to put all the info in one place. It's how I set my system up.
 
Nathan

---

