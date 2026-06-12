---
title: "90% Edgy Sound Problems Solved - Here's How"
date: 2007-08-04
forum: Multimedia &amp; Video
---

### Post by RHorse on 2007-08-04
I installed Edgy Kubuntu a few days ago, and hve been frantically trying to get my system to where it should be in terms of connectivity, multimedia and software installation.  I have been making very good progress.  One of the last hurdles I had was getting audio and video to play, especially from the web.

A couple of hours poring through the threads on Ubuntu forums and elsewhere led me to the solution of nearly all of these problems.  And these I now share with y'all. :)


First get your hands on the w32codecs package, and install it.  You will have to do some searching around, and may have to add a repository to your sources.list.  You also may have to follow detailed instructions on downloading and installing a gpg key for these repositories.  But, whatever it takes, get your sweaty palms on this package and install it! [Note: I came across some other web sites purporting to have the proprietary windows codecs.  These may or may not work, but I'd be partial to the Medibuntu repos if at all possible.

Next step, install the following packages:

libxine-extracodecs
libmad0

When I tried to do the first one, I got dependency error, but when I installed the second one, libmad0 first, it went smoothly. You may have to dig around for libxine-extracodecs. I found it finally on a 3rd party site. Be sure to install the one for Edgy or whatever other distro you're using.

Install the firefox video plugin. Other browsers? You're on your own.

Install libdvdcss2 package, for playing DVD's.

Install the latest flashplayer plugin: Firefox will direct you to the site when you first click on a youtube video.  Follow the instrc on Flash site to install the flashplayer plugin (it's really easy). But I suggest you download the .gz file and follow the instruc on the site of installing this way (by command line).  It's always worked perfectly for me.  I can't vouch for doing it any other way.

That is it.  This setup has worked for me.  Let me know how it works for you.  Now, lets you watch some...movies! :lolflag:

*R* *H*

---

