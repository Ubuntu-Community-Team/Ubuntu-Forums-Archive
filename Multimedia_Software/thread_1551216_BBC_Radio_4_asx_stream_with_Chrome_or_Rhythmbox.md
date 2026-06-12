---
title: "BBC Radio 4 asx stream with Chrome or Rhythmbox"
date: 2010-08-12
forum: Multimedia Software
---

### Post by Gordon D on 2010-08-12
Hi,

Using Ubuntu 10.4 LTS and having some difficulties streaming the BBC Radio 4 stream [http://www.bbc.co.uk/radio/listen/live/r4.asx](http://www.bbc.co.uk/radio/listen/live/r4.asx)

The stream seems to drop out on a regular basis, although I don't seem to have the same issue when I use WMP under WinXP.

I am listening via Google Chrome or Rythmbox - same issue with both.

Being new to Ubuntu, is there something I am missing that could be causing this?

Many thanks

Gordon

---

### Post by ron999 on 2010-08-12
Hi
Try playing the stream using a different player such as **VLC**.
Either load the URL (Media > Open network stream) or play from the command line:-

[SIZE="5"]```
vlc http://www.bbc.co.uk/radio/listen/live/r4.asx

```[/SIZE]
You can try this alternative link instead (though it might only work in UK):-
> mms://wmlive-acl.bbc.co.uk/wms/bbc_ami/radio4/radio4_bb_live_eq1_sl0

```
vlc mms://wmlive-acl.bbc.co.uk/wms/bbc_ami/radio4/radio4_bb_live_eq1_sl0
```

or 
```
mplayer mms://wmlive-acl.bbc.co.uk/wms/bbc_ami/radio4/radio4_bb_live_eq1_sl0
```

If these methods work for you then you can make a shortcut.
Copy and paste the text below into a text editor such as gedit and save it on your desktop as **BBC_Radio4.m3u**
Then 'Right-click Open With...' VLC or mPlayer or whatever.

Either this...

> #EXTM3U
#EXTINF:0,BBC Radio 4 FM - BBC Radio 4 FM
[http://www.bbc.co.uk/radio/listen/live/r4.asx](http://www.bbc.co.uk/radio/listen/live/r4.asx)
#
#
# Shortcut for BBC Radio 4 FM.

.

Or this...

> #EXTM3U
#EXTINF:0,BBC Radio 4 FM - BBC Radio 4 FM
mms://wmlive-acl.bbc.co.uk/wms/bbc_ami/radio4/radio4_bb_live_eq1_sl0
#
#
# Shortcut for BBC Radio 4 FM

:D

---

### Post by Gordon D on 2010-08-16
Thanks very much for the suggestions, although I had the same problems with each of them. Seems to work fine via the BBC iPlayer at [http://www.bbc.co.uk/iplayer/playlive/bbc_radio_fourfm/](http://www.bbc.co.uk/iplayer/playlive/bbc_radio_fourfm/) so I will just use that.

Many thanks again

Gordon

---

### Post by Bobby G on 2011-01-11
Hi, this thread's a little old but being a BBC radio fan and an Ubuntu user I've just been made very happy by 2 things & feel like sharing my pleasure:

AWN - a menu bar that looks a little like a Mac
Internet radio - an add on for the above that is smooth & stutter free

My interface experience is just so pleasing having just discovered the above combination.

AWN may be installed as normal using whichever software tool you normally use.
The internet radio applet is here: [http://pkgs.org/download/?distro=ubuntu-10.10&repo=webupd8-i386&pkg=awn-applet-radio_0.10-1~webupd8~maverick_all.deb](http://pkgs.org/download/?distro=ubuntu-10.10&repo=webupd8-i386&pkg=awn-applet-radio_0.10-1~webupd8~maverick_all.deb)

Go to the applets section of the AWN config once the above package is installed and low and behold you've got a radio applet!

...don't be put off by the 0.10 revision number - it works.

For AWN you can delete the bottom gnome panel then remove all you want from the top panel & set it to autohide to leave you with a very Mac-like view. Don't forget to add applets "indicator applet" and "notification area" to AWN so you get your wifi & other little icons that appear on your top panel. Also Cairo menu if you've removed that from your top panel too.

Hope this helps someone else stumbling across this post.

---

### Post by Carnwaj on 2011-03-31
Thanks very much for this - works a treat.

---

### Post by inearlygaveup on 2011-04-04
> **Bobby G said:**
> Hi, this thread's a little old but being a BBC radio fan and an Ubuntu user I've just been made very happy by 2 things & feel like sharing my pleasure:

AWN - a menu bar that looks a little like a Mac
Internet radio - an add on for the above that is smooth & stutter free

My interface experience is just so pleasing having just discovered the above combination.

AWN may be installed as normal using whichever software tool you normally use.
The internet radio applet is here: [http://pkgs.org/download/?distro=ubuntu-10.10&repo=webupd8-i386&pkg=awn-applet-radio_0.10-1~webupd8~maverick_all.deb](http://pkgs.org/download/?distro=ubuntu-10.10&repo=webupd8-i386&pkg=awn-applet-radio_0.10-1~webupd8~maverick_all.deb)

Go to the applets section of the AWN config once the above package is installed and low and behold you've got a radio applet!

...don't be put off by the 0.10 revision number - it works.

For AWN you can delete the bottom gnome panel then remove all you want from the top panel & set it to autohide to leave you with a very Mac-like view. Don't forget to add applets "indicator applet" and "notification area" to AWN so you get your wifi & other little icons that appear on your top panel. Also Cairo menu if you've removed that from your top panel too.

**Hope this helps someone else stumbling across this post**.

Yes thanks I found the post but need some help getting/installing the actual AWN radio applet.
Installed the AWN - menu bar ok. 
Thought I had got the correct radio but ended up with "Radio Tray" installed on my top panel.
Sounds a good radio but like you I wanted it in the AWN bar.

Any simple help/instructions on downloading and installing the radio applet please.

I am using Ubuntu 10.10 - the Maverick Meerkat

---

