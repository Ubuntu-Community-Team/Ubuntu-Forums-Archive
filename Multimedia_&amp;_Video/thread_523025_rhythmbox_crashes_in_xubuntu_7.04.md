---
title: "rhythmbox crashes in xubuntu 7.04"
date: 2007-08-11
forum: Multimedia &amp; Video
---

### Post by glandeur on 2007-08-11
Hello,

I have been trying to use Rhythmbox with Xubuntu 7.04.  I installed additional gstreamer packages from the synaptic package manager (bad and ugly including multiverse variants) yet Rhythmbox just closes when I try to play an mp3.  It also won't play any of the pre-installed radio streams.  In addition, when I select "contents" under the help tab on the menu bar I get an error message saying "Couldn't display help.  There was an error launching the default action command associated with this location."

I'm working from a fresh install of Xubuntu and have installed Rhythmbox using the add programs tool.  Is there something else I need to do because Rhythmbox is a gnome app?

Any tips would be greatly appreciated

Thanks.

---

### Post by aysiu on 2007-08-11
I don't know what's going on, but the best way to diagnose this problem is to launch Rhythmbox from the terminal and look at the error message that pops up when you try to play an MP3.

Press Alt-F2 and type ```
xfce4-terminal
``` Then, type ```
rhythmbox
``` play an MP3 and paste back here the error message you get.

---

### Post by glandeur on 2007-08-11
I followed your instructions.  I don't know if this first part is significant, but after I ran Rhythmbox from the terminal I got several lines of this:

/bin/sh: /usr/bin/esd: not found

Rhythmbox opened and when I tried to play an mp3 this was the error:

(rhythmbox:5195): Rhythmbox-WARNING **: Couldn't find an x overlay
Segmentation fault (core dumped)

Thanks again.

---

### Post by mroven on 2007-08-14
glandeur,

Im getting the exact same error.  The thing is, I had Rhythmbox running just fine for a while, then reinstalled Xubuntu and now get this error.  

Im still investigating and will add notes here if I find anything.

---

### Post by mroven on 2007-08-14
Hmmm...   Someone suggested disabling the "Visualization" plugin.  I tried that and it worked for me.
:)

---

### Post by glandeur on 2007-08-14
mroven,

Thanks.  That did the trick for me as well.

However, the help contents still will not launch and apparently I'm still missing some codecs for internet radio because most of the stations I try to play give the error:

Couldn't start playback.  Could not determine type of stream.

Do you have these problems also?

---

### Post by glandeur on 2007-08-14
Update:

It seems I'm also unable to subscribe to podcasts.  I get an error saying that there was a problem with the feed (I've tried several) and to verify the url, which I have.  I am new to linux, but I briefly ran Rhythmbox with Ubuntu before trying Xubuntu and did not have any of these problems.  I wanted to run Xubuntu because I have an older machine and thought I could save some resources for my apps by running a less flashy desktop.

In fact, I first loaded Xubuntu from Ubuntu and everything worked fine when I logged on for an Xfce session.  However, since I didn't plan to use Ubuntu anymore I did a clean install of Xubuntu and that is when my troubles began.

Am I defeating the purpose of Xubuntu by trying to run gnome apps, or is it just a little more complicated to get up and going?  I'm using a p3 500mhz laptop with 512mb ram.

Any general or specific advice would be appreciated.  I'm still orienting myself in the Linux world.

Thanks

---

### Post by glandeur on 2007-08-22
Update:

Adding the libgnomevfs2-extra library fixed my podcatcher problems and allowed playback of the pre-loaded virgin radio station:

sudo apt-get install libgnomevfs2-extra

Still unsure why the help contents won't load and what the problem is I'm having with some other internet radio stations.

---

### Post by glandeur on 2007-09-18
Just to update, I got the internet radio stations working to my satisfaction.  The only problem was me.  I was trying to copy stream links directly from the station info in iTunes.  I could've sworn this worked for me when I was briefly running Ubuntu.  Anyhow, just going to the station web sites and using the stream links there worked.

I guess the only thing I would leave this post open with is the issue of the rhythmbox help contents being unable to load in Xubuntu from a clean install.  At this point I''m more just curious if anyone else has encountered this.

---

