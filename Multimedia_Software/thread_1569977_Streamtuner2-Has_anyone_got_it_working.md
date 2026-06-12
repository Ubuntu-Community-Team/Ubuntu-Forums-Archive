---
title: "Streamtuner2-Has anyone got it working"
date: 2010-09-07
forum: Multimedia Software
---

### Post by petatkinson on 2010-09-07
Downloaded the above as a Deb package, installed but got nothing working.Anyone had any look with this yet.Its exactly what I need as I had the original Streamtuner installed and it was perfect

---

### Post by kostkon on 2010-09-07
Run it in the terminal and post any error messages here if you want.

---

### Post by kostkon on 2010-09-07
I just downloaded its latest deb and updated it from 2.0.6 to 2.0.8 and it works just fine (like its previous version).

The only thing you need to do is to open its preferences and set the media player.

It's very good, I mean, it has support for almost everything.

Screenshot attached.

---

### Post by Rinzwind on 2010-09-07
> **petatkinson said:**
> Downloaded the above as a Deb package, installed but got nothing working.Anyone had any look with this yet.Its exactly what I need as I had the original Streamtuner installed and it was perfect


From the readme?


how to run
----------

You can just execute the main binary "st2.py". All the other files
need to be copied into /usr/share/streamtuner2/ however. If it
doesn't work, make sure you have Python and gtk/pygtk installed:

  sudo apt-get install python python-gtk2 python-glade2 python-xdg



are all of these installed on your system? :)

---

### Post by petatkinson on 2010-09-07
Had all the required Python modules installed.Ran sudo as suggested.All the latest and 0 installed.Removed the Shoutcast at *** from the /etc/host file that was needed to direct the original Streamtuner.Restarted and everything working now.I wonder why Streamtuner2 is not in the repos.Anyway I'm back in business and again its great

---

### Post by fresnofred on 2010-09-12
i have lucid lynx and downloaded it and love it!  Bookmarks even work now.  Cannot get live 365, google to work but shoutcast and xiph and a few new services work great.  at first, i would tune into the wrong station when clicking on one, but now it SEEMS to tune the right station.  In edit- preferences, i changed a couple of engines from audacious, the one that came with it, to VLC.  Audacious seems to save all my previous stations which I dont like.  May try XMMS or something else.  May try Xine as I like the special effects.  I think I will uninstall the Streamtuner  package.  BUT, with Lucid, I got the old version of Amarok and it still works with Shoutcast.  Don't u just love Ububtu!!

---

### Post by aggie_surfer on 2011-01-26
Has anyone had the problem with newest  of Streamtuner2 where the edit preferences box appears larger than viewer screen?  You cannot save the edit because you cannot scroll down.  The box cannot be resized.  I have experienced this problem with 9.04 and 10.10.  Streamtuner2 version that installs with 10.10 works except for Shoutcast.  Can anyone help me resolve this sizing problem?  Thanks!

---

### Post by mekon on 2011-02-03
> **kostkon said:**
> 
The only thing you need to do is to open its preferences and set the media player.

Thanks for this. I was wondering why mine wasn't working.

---

### Post by mekon on 2011-02-03
> **aggie_surfer said:**
> Has anyone had the problem with newest  of Streamtuner2 where the edit preferences box appears larger than viewer screen?  You cannot save the edit because you cannot scroll down.  The box cannot be resized.  I have experienced this problem with 9.04 and 10.10.  Streamtuner2 version that installs with 10.10 works except for Shoutcast.  Can anyone help me resolve this sizing problem?  Thanks!

Mine looks fine on 800 x 600. You're not using an eee machine are you ?

---

### Post by aggie_surfer on 2011-02-12
Mekon .... Sorry for the late reply.  Yes, I'm using my eee!

---

### Post by Dogmudgeon on 2012-06-27
Two years later, the regressions seem to still be there. 

My complaint is that when clicked, the station lists play completely different stations than are listed. E.g., the ogg station list plays several mms (Microsoft WMA/ASF) stations. 

As it is, Streamtuner2 is useless. 

Any suggestions about how to get it going again? I'm a Pythonista of mediocre but occasionally effective skills, and I'd be willing to poke around under the hood and not just whine about it.

TIA!

---

