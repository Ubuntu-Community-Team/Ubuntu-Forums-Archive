---
title: "ZoneMinder Help: Disk Usage"
date: 2008-06-24
forum: Multimedia Software
---

### Post by yochaigal on 2008-06-24
Hello, all.
For reasons beyond my understanding, the PurgeWhenFull Filter stopped working. It's never been 100%, but I think that might be do more to my ignorance then anything else.

Here's a pic attached...

That's looks okay, right?
I have it set to run in background as well.
Can someone please give me a step-by-step guide on how to setup a purgewhenfull filter?

Thanks!

ps

I'm double-posting this here and in the zoneminder forums.
[http://www.zoneminder.com/forums/viewtopic.php?p=43325#43325](http://www.zoneminder.com/forums/viewtopic.php?p=43325#43325)

---

### Post by szirakitamas on 2008-07-31
hi!  i can't solve your problem but can ask mine: how can i start zoneminder 'cos after install i found nothing to do this. i can't find the program (no console, no alt+F2). thanks tamas

---

### Post by yochaigal on 2008-07-31
zoneminder is a process, like apache.
The easiest way to see if it is running is to open a terminal and type:
ps -ef

This will bring up a list of processes.  Look for zma or zmc.

Another way: open up a browser, navigate to :

[http://localhost/zm/zm.php](http://localhost/zm/zm.php)

See if you can see the Zoneminder login screen.  
Keep in mind that zoneminder is pretty advanced stuff, you should have some idea how to setup a LAMP server at the very least. Make sure you do:

sudo apt-get install zoneminder apache2 php5-mysql libapache2-mod-php5 mysql-server ffmpeg

and then:

sudo ln -s /etc/zm/apache.conf /etc/apache2/conf.d/zoneminder.conf
sudo /etc/init.d/apache2 force-reload


Some guides:
[http://ubuntulinuxhelp.com/video-surveillance-with-zoneminder-on-ubuntu/](http://ubuntulinuxhelp.com/video-surveillance-with-zoneminder-on-ubuntu/)
[http://www.howtoforge.com/video_surveillance_zoneminder_ubuntu](http://www.howtoforge.com/video_surveillance_zoneminder_ubuntu)
[http://ubuntuforums.org/showthread.php?t=136108](http://ubuntuforums.org/showthread.php?t=136108)

Just remember: firefox 3 and Zoneminder don't mix well yet. Don't use them together!

---

### Post by jetole on 2008-09-05
> **yochaigal said:**
> zoneminder is a process, like apache.
The easiest way to see if it is running... 

Typically your answer should be that this is unrelated and to ask it in a new question or to search for it since you don't want your question filling up with a 100 other questions that don't relate to yours.

---

### Post by yochaigal on 2008-09-05
As much as I agree with you, I think it is important to fill up the web with step-by-step guides to things... even snippets like mine help.  If I had googled something like "install" AND "zoneminder" AND "ubuntU" I would have found mine very helpful.  Of course, what I posted was pulled from other guides, but still... the more the merrier.

---

### Post by szirakitamas on 2008-11-24
sorry for delaying. from that time i didn't try it, but later i will i hope. thanks :)

---

