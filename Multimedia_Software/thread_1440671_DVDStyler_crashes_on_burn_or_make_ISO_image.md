---
title: "DVDStyler crashes on burn or make ISO image"
date: 2010-03-27
forum: Multimedia Software
---

### Post by OrangeVixen on 2010-03-27
I'm trying to create a DVD, I'm using DVDStyler 1.7.2 on Jaunty.

The problem I'm having is that whenever I try to burn or make an ISO image, it crashes. Usually at the "Create menu mpeg" line on the Generate DVD dialog.

Does anyone else have a similar experience?

---

### Post by OrangeVixen on 2010-03-28
I tried 1.7.4 and it still does NOT work, crashes with the same problem.

Does anyone know of any good graphical DVD menu creating programs?

---

### Post by OrangeVixen on 2010-03-30
Anyone? Anyone ever got DVDStyler to work?

---

### Post by defensorfedei on 2010-04-02
I am in the same position as you.  For now I use DeVeDe to get by for simple DVD's, but if I figure it out, I will post back here with an answer.

---

### Post by defensorfedei on 2010-04-02
This is really strange.  I had the exact same problem as you, so I tried upgrading to the 1.8 version without much success due to all the unsatisfiable dependencies. 

I did however get 1.7.4 to work after I had uninstalled it.  I installed the 1.8 doc package from debian package when I tried to install the 1.8 version. I later decided to re-install the 1.7.4 from the repos, but it failed and said I needed 1.7.4 doc package.  So I unistalled the 1.8 doc package using synaptic and re-installed the 1.7.4 packages from the repos, and now it works great.  I can't understand why, but it works after the reinstall. No more crashing at 'creating menu mpeg'.  It goes right on to transcoding/remultiplexing and eventually spits out and .iso image.  I don't understand it, but now it works.

Did you install from the dvdstyler repo or from compiled debian packages? If you used the dvdstyler repo, maybe try to uninstall your version and then run 'sudo apt-get update' in terminal.  Then try a new re-install through synaptic.  If you installed through compiled debian packages, try to install through repos.  The DVDstyler website has instructions on how to add their repo to your apt sources list and procure their repo key.

****I forgot to mention this.  I had the getdeb repos on my machine, which received a lot of updates the other day. I received updates for DeVeDe and DVDStyler, and therefore by default, Mencoder.   That is when Mencoder, DeVeDe, and DVDStyler all failed to work properly.  I think the real fix came from when I deleted the getdeb repo, reloaded apt and reinstalled Mencoder, DeVeDe, and DVDStyler from the ubuntu/DVDStyler repos.  If you have the getdeb repos, get rid of them!!!!! If you installed from getdeb, uninstall and try from the DVDStyler repo that I referred to before.

Best of luck to you. Post back and let me know how you make out.

---

### Post by alegallo on 2010-04-02
For what it may mean, dvdstyler worked fine just "out of the box" for me.
I made several dvd's already and had never ever a single problem :neutral:

Just one doubt: have you ever tried NOT to make an .iso or to burn? 
I mean, did you think about making the dvd structure and then burning it using, for example, k3b?

I don't know, maybe you've got a buggy genisoimage ...

---

### Post by OrangeVixen on 2010-04-02
I never had the getdeb repos, I installed dvdstyler 1.7.4 from Synaptic using the dvdstyler repos.

I tried removing everything completely and reinstalling memcoder, devede, and dvdstyler but dvdstyler still crashes at the same spot, no matter if I tried burning or just making and ISO image. I also reinstalled genisoimage but same thing.

alegallo: how do I just make a dvd structure and burn it?

---

### Post by 2Stoned on 2010-05-06
If you have a decent machine you can install convertxtodvd on a virtual windows machine for creating DVD's. Thats what i do since i was getting frustrated with some of the open source dvd authoring software for linux. And i use my virtual win machine for streaming to my console, msn and some other things.

---

### Post by jtpoole99 on 2010-07-24
I'm using DVDStyler 1.8.02, Devede 3.16.8 and genisoimage 1.1.1.0 and anytime I use DVDStyler or Devede, during the process of transcoding the files, my computer reboots itself.  I was using Devede without any problem and all of a sudden, any time I use any DVD authoring tools my computers reboots during the transcoding process.  Does anyone know what's causing this issue?

---

