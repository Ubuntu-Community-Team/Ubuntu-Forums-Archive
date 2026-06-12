---
title: "MPlayer/Totem video only plays in half of the video window"
date: 2006-10-19
forum: Multimedia &amp; Video
---

### Post by McVitie on 2006-10-19
Hello,

Bit of a newbie to Linux and made the transition recently at home - love Ubuntu and won't be turning back now!

My problem is this, frequently I try and watch a video file and it only occupies the full left-half of the available video window like this:

```

 _______________
/xxxxxxx|           \
|xxxxxxx|           |
|xxxxxxx|           |
|xxxxxxx|           |
\----------------------/

```

The image is stretched to fit the vertical space but squashed into half the horizontal space.

The ONLY way I have found so far to remedy this is to restart gnome.

I am using the ATI drivers as advised in another thread (I think on here somewhere ;))

Help!

MV.

---

### Post by dixonstalbert on 2006-10-23
hello 

not sure if you are still looking for an answer for this...

I had a problem with the various movie players ignoring my screensize setting and squishing movie in player

I found the answer in one of the forums about putting in DisplaySize setting in my xorg.conf file. I run 2 monitors so I have a really long and narrow total desktop and the players kept scaling the movie to that kind of shape. could you have a similar problem?

The xorg.conf file is the config file for the X display system so you should back up your current file first before monkeying with it in case something goes wrong. to do that open a terminal window and type

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorgoct23.conf
```

then type
```
sudo gedit /etc/X11/xorg.conf
```


find your Section "Monitor" and below the Identifier section insert a new line and add DisplaySize 360 135

my looks like this but yours will have the name of your monitor:

```
Section "Monitor"
	Identifier   "SyncMaster"
	DisplaySize     360 135
	Option	    "DPMS"
```

close any open programs and reboot

if something went wrong and you don't get a graphics display, type

```
sudo cp /etc/X11/xorgoct23.conf /etc/X11/xorg.conf 
```

this will restore you back to your orginal config and you have to try something else

good luck

---

### Post by McVitie on 2006-10-25
Thanks!

I will try that tonight and let you know if this works :)

---

### Post by McVitie on 2006-10-30
Nope - that made no difference.

It still views in one half of the screen...:(

---

