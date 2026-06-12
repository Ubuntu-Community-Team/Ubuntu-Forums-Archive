---
title: "HowTo capture Screenshots while in mythfrontend or mythbackend"
date: 2008-08-19
forum: Mythbuntu
---

### Post by LarryJ2 on 2008-08-19
You are configuring MythBuntu and, for example,  you are in the mythbackend program.  Since the backend and frontend programs by default take up the whole screen, how does one take a screen shot and save the snap to a file.

1. You need a screen capture program such as ksnapshot.  While part of the KDE desktop, it works well with gnome.  It provides delayed, cursor determined region, whole screen and whole window snapshots saved to your choice of image file format. Install from the repository:

```
sudo apt-get install ksnapshot
```

2. Start myth[backend][frontend] then navigate to the screen you wish to preserve. The mythbuntu (backend or frontend) configuration programs will hog the entire screen.

3. While in the gnome desktop, hold the left Ctl+Alt  hit Tab.  Your Applications menu should become visible. Click there and navigate through Graphics to KSnapshot. Click there you can snap and save almost all the mythbuntu configuration screen to a file and to a location of your choice if you have installed and are using the gnome desktop.  I haven't discovered the key combination that returns to the desktop in XFCE (the desktop manager that mythbuntu defaults to). I think that info maybe available here:** [http://www.xfce.org/documentation/4.0/manuals/xfdesktop#xfdesktop-menu](http://www.xfce.org/documentation/4.0/manuals/xfdesktop#xfdesktop-menu)** Not using the gnome desktop manager?  Install it from the Mythbuntu Control Center application which is part of the default mythbuntu installation.

4. If you plan to post your screen captures,  the mythbuntu forum favors **.png** or **.jpg** format in that the maximum file size is 976KB.  Other file formats must be much smaller in size.

---

### Post by LarryJ2 on 2008-08-23
Another way is to use the Vinagre remote desktop viewer.

1.  On your muthbuntu box, in Mythbuntu's Myth Control Center,  check Allow VNC and give a password.  Maybe use the same as your login on the mythbox.

2.  In a terminal on the remote PC, enter vinagre.

3. Within vinagre, find then connect to your mythbuntu box. You may need the IP of the mythbuntu box. If "find" fails, return to your mythbox. Open a terminal, enter ifconfig. The current IP of your mythbuntu box should be visible. (something perhaps like 192.168.1.100)

4.  Vinagre has a "screen" snap shot button which will save the XFCE or Gnome or KDE desktop showing mythbuntu frontend or backend screens.

Vinagre example screen shot attached below.

---

### Post by Sharft 6 on 2010-08-27
sudo apt-get install xfce4-screenshooter

---

### Post by iamlindoro on 2010-08-27
Alternately, bind the "screenshot" keybinding (Utilities/Setup->Edit Keys->JumpPoints->Screenshot) in MythTV.  Then press whatever button you've bound.

---

### Post by mathog on 2010-08-27
> **iamlindoro said:**
> Alternately, bind the "screenshot" keybinding (Utilities/Setup->Edit Keys->JumpPoints->Screenshot) in MythTV.  Then press whatever button you've bound.

Then what?  Presumably if this would be done through the lirc IR controlled front end it would be because there is no other interface (keyboard, ssh, etc.)  Where would the snapshot go?

This does give me an idea though.  Set up a script to take a snapshot and save it to a file with a unique name, and put it where the slideshow (MythGallery) feature can see it.  Bind this script to a lirc controlled button.  Then one could snap pictures at will, and review the shots from the front end too.

---

### Post by mathog on 2010-08-29
> **mathog said:**
> 
This does give me an idea though.  Set up a script to take a snapshot and save it to a file with a unique name, and put it where the slideshow (MythGallery) feature can see it.  Bind this script to a lirc controlled button.  Then one could snap pictures at will, and review the shots from the front end too.

This method works - except when it doesn't.  Here is the part that works.

If imagemagick is not yet installed, do

```
sudo apt-get install imagemagick

```
Then set up the script

```
cat >/usr/local/bin/take_shot.sh <<EOD
#!/bin/sh
# take a screenshot and save to a file whose name is the data+time
fprename=`date | tr ' ' _ `
fname=`echo "screenshot-${fprename}.png"`
logger "snapshot fname $fname"
cd /var/lib/mythtv/pictures
import -window root $fname
EOD
chmod 755 /usr/local/bin/take_shot.sh

```

```
cd ~MYTHTVUSER/.lirc
#
# use appropriate buttons/remote for your configuration
#
cat >>irexec <<EOD
begin
    remote = RM-VL600_8201
    prog = irexec
    button = twinview
    config = /usr/local/bin/take_shot.sh
    repeat = 0
    delay = 0
end
EOD

```
And finally...

```
reboot

```
*******
After that when a Mythtv screen is up one can press "twinview" and 
it takes a snapshot.  Except...

It only works for Mythtv screens. If a TV show is running, or a recording is playing, the result is a blank screen.  This system uses VDPAU playback and I believe that results in an X11 display that cannot be imported.  

Anybody have a tool that will take a snap shot of a VDPAU display???

---

### Post by mathog on 2010-08-31
> **mathog said:**
> 
Anybody have a tool that will take a snap shot of a VDPAU display???

The folks in the NvNews linux support forum had the answer, put

  VDPAU_NVIDIA_NO_OVERLAY=1

in the script which (eventually) starts MythTV, and then the regular snapshot programs work.  On my system I added this to the script which starts mythwelcome.

---

### Post by bcg30506 on 2010-08-31
> **mathog said:**
> The folks in the NvNews linux support forum had the answer, put

  VDPAU_NVIDIA_NO_OVERLAY=1

in the script which (eventually) starts MythTV, and then the regular snapshot programs work.  On my system I added this to the script which starts mythwelcome.

What, if any, is the performance penalty of doing this?

---

### Post by mathog on 2010-08-31
> **bcg30506 said:**
> What, if any, is the performance penalty of doing this?

None that I have seen so far, but it has only been a day.  The people who could best answer your question hang out here:

  [http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

---

### Post by mathog on 2010-09-03
> **bcg30506 said:**
> What, if any, is the performance penalty of doing this?

It looks like there is a slight tendency for one line of tearing on fast motion, near the center of the screen.  Not very obtrusive, and it could well have been there before and I never looked closely enough to notice it.  This might not be present with a newer Nvidia driver - the one on this box is quite old.

---

