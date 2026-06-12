---
title: "adding facebook account at pidgin accounts"
date: 2009-08-16
forum: Networking &amp; Wireless
---

### Post by shaon3343 on 2009-08-16
hey, i'm a novice ubuntu user. I evev cant modify any opensource software. I've noticed that in pidgin I can add my yahoo,msn,gtalk , myspace accounts but I cant add facebook account. how can I add facebook account in my pidgin? please help.

---

### Post by sledtv on 2009-08-16
Hi
In synaptic search for facebook and install pidgin-facebookchat or sudo apt-get install pidgin-facebookchat in terminal

Eric

---

### Post by tacantara on 2009-08-16
> **shaon3343 said:**
> hey, i'm a novice ubuntu user. I evev cant modify any opensource software. I've noticed that in pidgin I can add my yahoo,msn,gtalk , myspace accounts but I cant add facebook account. how can I add facebook account in my pidgin? please help.

Welcome to Ubuntu.  I'm fairly new at this myself (about 6 months), and I'm not tech-savvy enough to get into the code stuff.  The best thing you can do is continue to bring questions to the Forum, and run Google searches for information.  That's exactly what I did to come up with this solution to Facebook on Pidgin.

Solution 1:  You can download a plugin for Pidgin at [http://code.google.com/p/pidgin-facebookchat/](http://code.google.com/p/pidgin-facebookchat/).  On the right side of that page, click the link to download the file with the .deb extension.  The .deb files are pretty easy to install in Ubuntu.

Solution 2:  The Synaptic Package Manager has the plugin as well.  It's not the updated version that you can download from the website, but the software is supported by Ubuntu/Canonical, so updates are likely to become available through the Update Manager.  Open Synaptic, type Facebook into the quick search field (make sure that "All" is highlighted in the left pane).  The package you're looking for is "pidgin-facebookchat."  Mark it for installation, and click install.

Solution 3:  This is a good time to learn the terminal/console.  Open a terminal window and type (or cut & paste) this command:

```
 sudo apt-get install pidgin-facebookchat 
```When prompted, enter your password.  The installation package will download and automatically install.

Once you're done, open Pidgin.  Click on Accounts>Manage Accounts>Add.  Select Facebook from the list of available protocols.

---

### Post by zee on 2009-08-17
The connection to Facebook keeps on failing. It connects for a brief instant, but then it simply disconnects.

Could the problem be caused by the fact I use one email address for MSN, GoogleTalk and Facebook ? I cannuse MSN and GoogleTalk without any problems.

Best regards,
zee

---

### Post by danlaptic on 2009-08-31
I have the same problem with the pidgin facebook plugin where I connect for an instant and get disconnected.

Found this thread which seems to be tracking the problem:
[http://code.google.com/p/pidgin-facebookchat/issues/detail?id=246](http://code.google.com/p/pidgin-facebookchat/issues/detail?id=246)

Also, this is not an issue with my 32-bit version of Ubuntu 9.04, but is with my 64-bit version of Ubuntu 9.04.

*Edit* I should probably add that I'm running Pidgin 2.5.5 on the 64-bit version of Ubuntu 9.04

*Edit 2* Looks like it's been one of those days.  Anyway, there's a Pidgin Facebook plugin users group on Facebook that links you to this page: [http://code.google.com/p/pidgin-facebookchat/](http://code.google.com/p/pidgin-facebookchat/) which has a .deb of the 1.60 Facebook chat plugin.  After removing the 1.47 version (the one available through Synaptic) and installing the most recent version (.deb) everything works fine and the connection holds. 

Goodnight everybody!

---

### Post by anibalismo on 2009-09-12
Hey, I just found another (I think) solution to this:
Just downloaded 
[http://mirror.ne.gov/ubuntu/pool/universe/j/json-glib/libjson-glib-1.0-0_0.7.6-0ubuntu1_i386.deb](http://mirror.ne.gov/ubuntu/pool/universe/j/json-glib/libjson-glib-1.0-0_0.7.6-0ubuntu1_i386.deb)
Then, double click on it, to install (or do whatever you do in your console to install)

Afterwards, you need to download 
[http://pidgin-facebookchat.googlecode.com/files/pidgin-facebookchat-1.61.deb](http://pidgin-facebookchat.googlecode.com/files/pidgin-facebookchat-1.61.deb)

install that, and you are good to go!
Cheers XD

---

### Post by green0eggs on 2009-09-29
I am finding I can't install the .deb file (see attached screenshot) and installing via terminal gives the following error

> username@computer:~$ sudo apt-get install pidgin-facebookchat
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package pidgin-facebookchat

I'm using 8.10 if that makes a difference. Is there a way to add the package? (or get around the error for gdebi-gtk) How can I do this?

Cheers

---

### Post by dps9682 on 2009-09-29
> **anibalismo said:**
> Hey, I just found another (I think) solution to this:
Just downloaded 
[http://mirror.ne.gov/ubuntu/pool/universe/j/json-glib/libjson-glib-1.0-0_0.7.6-0ubuntu1_i386.deb](http://mirror.ne.gov/ubuntu/pool/universe/j/json-glib/libjson-glib-1.0-0_0.7.6-0ubuntu1_i386.deb)
Then, double click on it, to install (or do whatever you do in your console to install)

Afterwards, you need to download 
[http://pidgin-facebookchat.googlecode.com/files/pidgin-facebookchat-1.61.deb](http://pidgin-facebookchat.googlecode.com/files/pidgin-facebookchat-1.61.deb)

install that, and you are good to go!
Cheers XD

Hey thanks anibalismo, worked a treat on my 9.04 setup.

---

### Post by green0eggs on 2009-09-29
> **anibalismo said:**
> Hey, I just found another (I think) solution to this:
Just downloaded 
[http://mirror.ne.gov/ubuntu/pool/universe/j/json-glib/libjson-glib-1.0-0_0.7.6-0ubuntu1_i386.deb](http://mirror.ne.gov/ubuntu/pool/universe/j/json-glib/libjson-glib-1.0-0_0.7.6-0ubuntu1_i386.deb)
Then, double click on it, to install 

Cheers, I've just tried that and it worked, I guess I needed a more recent libjson package (hence the error message attached to above post).

Magic!

---

### Post by miles.sharpe on 2009-10-09
Thank You very much. Windows fans told me it was impossible. Well done

---

### Post by ArcaVex on 2009-10-09
> **miles.sharpe said:**
> Thank You very much. Windows fans told me it was impossible. Well done

May be in windows? :P

I've been using this plugin for a while, received mixed views about it, but i like it.

---

