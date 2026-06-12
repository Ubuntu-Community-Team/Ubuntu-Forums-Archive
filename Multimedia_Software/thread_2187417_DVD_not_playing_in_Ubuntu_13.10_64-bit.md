---
title: "DVD not playing in Ubuntu 13.10 64-bit"
date: 2013-11-12
forum: Multimedia Software
---

### Post by jhilp on 2013-11-12
[TABLE]
[TR="bgcolor: transparent"]
[TD="class: postcell, bgcolor: transparent"]I installed Ubuntu Gnome 13.10 on my computer, but it isn't reading video or audio CD's and DVD's. At first, I inserted a DVD video, and it played normally for maybe 30-45 seconds before coming up with a "internal data flow error". I was using the Totem player when the problem occurred, so I tried installing the VLC media player. It wouldn't read the disc at all, so I uninstalled the player. Now, the Totem player won't even begin playing the DVD. The player sometimes doesn't even open up when I insert the DVD, and other times it will but says it can't read it. I've tried several different DVD's and CD's with similar results. The computer is recognizing the optical drive, because when I open "Files", it shows the drive and the disc, but can't play it. [COLOR=#444444]I've tried all the usual ideas, like installing VLC, encryption libraries, region codes, etc. The error that comes up is "internal data flow error". I can't believe no one else has been having this problem! I've had this issue every time I install 13.10 on a computer, in both Unity and Gnome desktops. It's been the same thing with 3 or 4 different computers. [/COLOR]Previously, I ran Ubuntu 13.04 with the Gnome desktop installed from the software center, and I had no issues. Any help is appreciated!



[TABLE="class: fw, width: 656"]
[TR="bgcolor: transparent"]
[TD="class: vt, bgcolor: transparent"]

[/TD]
[TD="class: post-signature owner, bgcolor: #E8E7E5"][/TD]
[/TR]
[/TABLE]

[/TD]
[/TR]
[TR="bgcolor: transparent"]
[TD="class: votecell, bgcolor: transparent"][/TD]
[TD="bgcolor: transparent"][COLOR=#444444][TABLE="width: 660"]
[TR="class: comment, bgcolor: transparent"]
[TD="bgcolor: transparent"][/TD]
[TD="class: comment-text, bgcolor: transparent"]

[/TD]
[/TR]
[/TABLE]
[/COLOR]
[/TD]
[/TR]
[/TABLE]

---

### Post by farump2 on 2013-12-19
Bump!

---

### Post by speartip on 2013-12-20
I notice you've bumped a thread that you did not start or are you the same person?
Anyway, I assume you've tried the usual stuff, if not:
```
sudo apt-get install ubuntu-restricted-extras
```
Make sure libdvdread4 is installed.
In 13.10 you will also need libdvdcss2, its not in the repos as far as I know, but you can download & install the .deb file from here:
[http://download.videolan.org/ubuntu/saucy/](http://download.videolan.org/ubuntu/saucy/)
Choose the one for your architecture, either the "_amd64.deb" or the "_i386.deb" not the "-dev" files.
You should be good to go now.

---

### Post by lots.o.lentils on 2013-12-29
Hello,

I am seeing this problem as well.  I installed 13.10 a couple days ago.  To try to get DVDs to work, I have installed the following:

libdvdread4 (and ran install-css.sh)
ubuntu-restricted-extras
regionset vlc
libdvdcss2 from the link above, 64 bit, not the -dev file

I still get the message "Internal data flow error" after a DVD has played for about a second.  The same hardware and DVD work on Ubuntu 12.04.   Anything else to try?

---

### Post by hellolife on 2014-01-24
Bump

---

### Post by fischerking2 on 2014-02-19
I'm running Ubuntu 13.10 64bit and I've managed to fix this. I installed the latest GStreamer plugins. You need to add theGStreamer repository.
Open up a terminal, and enter:

sudo apt-add-repository[SIZE=2][FONT=arial][/FONT][/SIZE] ppa:gstreamer-developers/ppa

sudo apt-get update

sudo apt-get dist-upgrade

Then restart computer and you should be good to go.

---

### Post by Steve_Newbury on 2014-04-09
You can just install 3 packages from Trusty which fixed the problem for me
I have written a short guide on my blog: [http://www.sjnewbs.net/?p=558](http://www.sjnewbs.net/?p=558) which includes links to the relevant packages. 

The version of GStreamer in Saucy is broken I think. The Trusty version works

---

