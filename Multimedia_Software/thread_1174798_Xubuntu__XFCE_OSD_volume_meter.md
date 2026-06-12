---
title: "Xubuntu / XFCE OSD volume meter"
date: 2009-05-31
forum: Multimedia Software
---

### Post by calraith on 2009-05-31
This is a howto and a plea for help.  First, the howto.

I've seen a couple of other threads regarding hardware volume controls (keyboard volume controls, laptop volume wheel, etc), and displaying them using a notification.  Personally, I prefer osd_cat over notify-send.  How bout a screenshot?

[IMG]http://headcandy.org/rojo/volume_ctl_screenshot.jpg[/IMG]

Pretty.  So, here's how to do it.  In a terminal window, install xosd-bin and create the script:

```
sudo apt-get update
sudo apt-get install xosd-bin
cd /usr/local/bin
sudo mousepad volume_ctl
```Copy this script and paste into mousepad (or whatever text editor you're using):

```
#!/bin/sh

# amixer options
CHANNEL=Master  # usually Master, but for Asus EEE, this is iSpeaker
CARD=0          # Which sound card, if your system has more than one?
VOL_STEP=2      # amount to increase / decrease volume

# osd_cat options
POS=bottom      # top, middle or bottom
ALIGN=center    # left, center or right
OFFSET=0        # offset from the top or bottom
COLOR=gray      # white, blue, yellow, cyan, magenta, green, etc
MUTECOLOR=brown # color to use instead when muted
SHADOW=2        # offset of shadow, 0 for none
DELAY=3         # seconds to show the OSD
AGE=0           # seems broken :\
BARMODE=slider  # percentage or slider
FONT=-*-helvetica-medium-r-*-*-*-320-*-*-*-*-*-*

if [ "$1" = "mute" ]; then
    amixer -c $CARD set $CHANNEL toggle >/dev/null 2>&1
elif [ "$1" = "up" ]; then
    amixer -c $CARD set $CHANNEL $VOL_STEP+ >/dev/null 2>&1
elif [ "$1" = "down" ]; then
    amixer -c $CARD set $CHANNEL $VOL_STEP- >/dev/null 2>&1
else
    echo "Usage: $0 up|down|mute"
    exit 1
fi


STATUS=$(amixer -c $CARD sget ${CHANNEL} | grep -c "\\[on\\]")
VOLUME=$(amixer -c $CARD sget ${CHANNEL}  | awk '$0 ~ "%" { vol=$(NF-2); \
     gsub("\\[", "", vol); gsub("\\]", "",vol); print vol; exit; }' )

if [ $STATUS -eq 0 ]; then
    STATUS=" (muted)"
    COLOR=$MUTECOLOR
else
    STATUS=""
fi

killall osd_cat >/dev/null 2>&1   # if the -a switch worked, we wouldn't need this

osd_cat -p $POS -c $COLOR -s $SHADOW -a $AGE -d $DELAY -o $OFFSET -A $ALIGN \
-b $BARMODE -P $VOLUME -f $FONT -l 1 -T "Volume: $VOLUME$STATUS"
```Note: Thanks to Vermind for giving me a couple of ideas, and for his excellent rewrite of the awk command.   I still like my script better than his, though.  ;)

Save and close the script after you've salted to taste.  Go back to the terminal window, make the script executable, and test it out.

```

sudo chmod 755 volume_ctl
./volume_ctl up
./volume_ctl down

```After making sure the script works from a terminal window, the next step is to bind your hardware volume controls to it.  Go to the Applications menu --> Settings --> Keyboard.  Go to the Application Shortcuts tab.  Create three new shortcuts as follows.
```
COMMAND                           SHORTCUT
-------                           --------
/usr/local/bin/volume_ctl mute    XF86AudioMute
/usr/local/bin/volume_ctl down    XF86AudioLowerVolume
/usr/local/bin/volume_ctl up      XF86AudioRaiseVolume

```The XF86Audio* shortcuts are filled in by your hitting the volume controls / rolling the volume knob / whatever when you're prompted for the command shortcut, after choosing the shortcut command.  It's kind of confusing, but I'm sure you'll figure it out.

Thus endeth the howto.  Now, my plea for help is this.  According to osd_cat --help and the man page, the -a | --age switch is supposed to force currently displaying messages to expire instantly so an updated message can be displayed.  It doesn't appear to be working that way for me.  Should I file this as a bug, or is this a mistake on my part?

---

### Post by keratos on 2009-08-01
Hi

This is a GREAT HOWTO

I've run xubuntu alongside my Arch, Ubuntu, Fedora and Slack installs and just couldnt bloody well work out how to get my laptop volume slider working in Xubuntu. The others work fine after default install. I never thought of using the combination of X Macro and Keyboard shortcut menu. Simple! Works fine now in Xubuntu.

Well done.

Cheers.

---

### Post by sammik2 on 2009-08-16
Thanks, works fine on Dreamlinux, just needed to change

STATUS=$(amixer sget Master | awk '$1 == "Mono:" { print $NF; }')

to

STATUS=$(amixer sget Master | awk '$2 == "Mono:" { print $NF; }')

---

### Post by Vermind on 2009-11-05
Hi, I made this a bit more generic. See [this post.]("http://ubuntuforums.org/showthread.php?p=8247224#post8247224")

---

### Post by calraith on 2009-12-07
> **Vermind said:**
> Hi, I made this a bit more generic. See [this post.]("http://ubuntuforums.org/showthread.php?p=8247224#post8247224")

I made your generic script a bit more generic.  Thanks for the ideas!

It's always a pleasure to meet one of the half dozen people on the planet who know how to use awk beyond the basic '{print $1}' and so forth.

Oh, something else.  You mentioned that the OSD looks like an old TV volume display.  I confess that that was sort of the effect I was going for on my laptop.  It might help you to play with the COLOR and MUTECOLOR variables.  They take canonical names (red, blue, green, magenta, cyan, orange, etc), and they also take light and dark modifiers (darkred, lightblue, etc).  Play around and see what matches your color scheme yet contrasts against your background.

---

### Post by Vermind on 2009-12-07
> It's always a pleasure to meet one of the half dozen people on the planet who know how to use awk beyond the basic '{print $1}' and so forth.

:)

> You mentioned that the OSD looks like an old TV volume display. I confess that that was sort of the effect I was going for on my laptop.
orange and top aligned with 24 px from top works for my orange adaptation of Demlits or the included DarkRoom Ubuntu theme. My "it looks like an old TV volume display" was supposed to give an idea to people trying it, not to be taken as a negative remark. I find it goes well with movie players and things. The only problem is that it undermines desktop consistency. For me though, it's enough that I can put it at the top like other notifications. I think it's great.


> CHANNEL=Master  # usually Master, but for Asus EEE, this is iSpeaker
I made the mute_switch separate variable for checking mute status, because on older alsa and the EEE, you had to use a switch for muting the speakers (iSpeaker, not a volume control) and a separate volume control (PCM or Master) for the volume of the speakers. If you muted master, the speakers still put out a high crackling that corresponded to the highest hertz sounds being played by the "muted" audio. This has been fixed in Karmic's version of ALSA though; now it's Master on EEE too.

Oh and I don't mind; progress is always welcome.

P.S. Found a fix for the blinking/killing the osd when calling the command a few times in succession?

---

### Post by Raigedas on 2010-02-12
[LIST]
[*]first, about the AGE argument. i have found this workaround: launch osd_cat to the background. that is - add "&" at the end of command. so that your command should look like:
```
osd_cat -p $POS -c $COLOR -s $SHADOW -a $AGE -d $DELAY -o $OFFSET -A $ALIGN \
-b $BARMODE -P $VOLUME -f $FONT -l 1 -T "Volume: $VOLUME$STATUS" &
```
[*]it is possible to use default notification mechanism - just make sure that **xfce4-volumed** is started
[/LIST]

---

