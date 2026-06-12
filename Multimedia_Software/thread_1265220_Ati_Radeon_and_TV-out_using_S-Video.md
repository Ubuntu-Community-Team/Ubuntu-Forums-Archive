---
title: "Ati Radeon and TV-out using S-Video"
date: 2009-09-13
forum: Multimedia Software
---

### Post by orbital on 2009-09-13
I have Ati Radeon X1400 graphics card and would like to connect my laptop to a TV using S-Video. With XP everything works smoothly, how can I set up tv-out connection for Ubuntu? Any help appreciated.

---

### Post by frogotronic on 2009-09-25
> **orbital said:**
> I have Ati Radeon X1400 graphics card and would like to connect my laptop to a TV using S-Video. With XP everything works smoothly, how can I set up tv-out connection for Ubuntu? Any help appreciated.

same problem here

---

### Post by dlowerre on 2010-02-18
This issue has frustrated me greatly.  I have a friend using Windows (Friends don't let friends...) so I have been trying to switch him to Ubuntu.  Problem is he likes to use a TV as his monitor.

I have wrestled with the Display settings every which way, and cannot get his TV to work RELIABLY.  

The scorcher is that windows does this perfectly without any intervention.  Very embarrassing.

---

### Post by frogotronic on 2010-02-18
it only works with the FGLRX driver; not the open source driver.

---

### Post by sturmey on 2010-07-08
According to the wiki, the open source radeon driver is *supposed* to work with the s-video out on almost every card.

The problem is that it doesn't. if you try to search for an answer, you get 500 responses related to the proprietary drivers and ubuntu 7.x or 8.x 

What we really need is a way to search these posts and ignore anything that's not related to the new version, and maybe lock out the old version threads when the new version is released.

Does anyone actually know how to get the Radeon drivers (open source) to output s-video?

---

### Post by xtrakt on 2010-07-26
Use this script to enable S-Video:

/usr/bin/tvon
```

#!/bin/bash
# Enable S-Video at 800x600
xrandr --addmode S-video 800x600 && xrandr --output S-video --mode 800x600 --pos 200x200 && xvattr -a XV_CRTC -v 1

```It takes an 800x600 portion of your screen and ouputs it via S-Video.

Use this to disable S-Video:

/usr/bin/tvoff
```

#!/bin/bash
# Disable S-Video
xvattr -a XV_CRTC -v 0 && xrandr --output S-video --off

```Use this for a dual screen setup:

/usr/bin/dualscreen
```

#!/bin/bash
# Enable dual screen
xrandr --addmode S-video 800x600
xrandr --output S-video --mode 800x600 --right-of VGA-0

```Replace VGA-0 with your primary output name. You can also replace right with left.

The two first scripts are taken from the Internet. I made the last one myself. It requires you to add "Virtual" option to xorg.conf, like this:

```

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    DefaultDepth    24
        SubSection "Display"
                Virtual          2080 1024
        EndSubSection
EndSection

```Calculate the virtual resolution like this: Sum the X resolution of S-Video (800) and your primary display (mine is 1280). Then compare the Y resolutions of your screen and S-Video (600) and pick the higher one (most likely your primary screen). Hope this helps.

If these scripts give any errors, please run
```

sudo apt-get install xrandr

```Naturally you need to make the scripts executable:
```

sudo chmod +x /usr/bin/tvon
sudo chmod +x /usr/bin/tvoff
sudo chmod +x /usr/bin/dualscreen

```

---

### Post by iblazev on 2010-07-29
Hello ppl:) 

Just to join in on a subject:)

I tried all those things u mentioned, xtrakt, but there isn't much improvement. I do have picture on TV via S-Video but it's scrambled although u can see somewhat of the desktop. 

Funny thing is that when I tried restarting X, sometimes I do get normal pic on TV but lately even that doesn't work. Maybe it was because of some updates but how can one tell:/

Any other ideas?

---

### Post by drogve on 2012-07-06
> **xtrakt said:**
> Use this script to enable S-Video:

/usr/bin/tvon
```

#!/bin/bash
# Enable S-Video at 800x600
xrandr --addmode S-video 800x600 && xrandr --output S-video --mode 800x600 --pos 200x200 && xvattr -a XV_CRTC -v 1

```It takes an 800x600 portion of your screen and ouputs it via S-Video.

Use this to disable S-Video:

/usr/bin/tvoff
```

#!/bin/bash
# Disable S-Video
xvattr -a XV_CRTC -v 0 && xrandr --output S-video --off

```Use this for a dual screen setup:

/usr/bin/dualscreen
```

#!/bin/bash
# Enable dual screen
xrandr --addmode S-video 800x600
xrandr --output S-video --mode 800x600 --right-of VGA-0

```Replace VGA-0 with your primary output name. You can also replace right with left.

The two first scripts are taken from the Internet. I made the last one myself. It requires you to add "Virtual" option to xorg.conf, like this:

```

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    DefaultDepth    24
        SubSection "Display"
                Virtual          2080 1024
        EndSubSection
EndSection

```Calculate the virtual resolution like this: Sum the X resolution of S-Video (800) and your primary display (mine is 1280). Then compare the Y resolutions of your screen and S-Video (600) and pick the higher one (most likely your primary screen). Hope this helps.

If these scripts give any errors, please run
```

sudo apt-get install xrandr

```Naturally you need to make the scripts executable:
```

sudo chmod +x /usr/bin/tvon
sudo chmod +x /usr/bin/tvoff
sudo chmod +x /usr/bin/dualscreen

```
Well I a Linux noob but I gat a mirror image on the tv, so at least  I can watch Movies thnx bud..If I knew what I wass doing Id say you post is rihgt on but I only used the dual screen setup comand for now

---

### Post by wildmanne39 on 2012-07-07
Hi, this is an old thread so it has been closed, if you need help please start a new thread with a descriptive title.
Thanks

---

