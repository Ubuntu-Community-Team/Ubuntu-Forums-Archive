---
title: "Sound clicks incessantly under Karmic"
date: 2009-11-04
forum: Multimedia Software
---

### Post by Faximili on 2009-11-04
Hey folks,

Having a handful of problems with my clean install of 9.10 that I wasn't having with 9.04. I'll post them separately so they can be addressed separately.

I'm getting an incessant clicking sound when plugged into external speakers.  Basically, this is how the problem manifests: I play some sound, either through rhythm box or a Flash video.  Sometimes this sound output is very long, i.e., an entire album.  There are no problems.  When sound stops there is a loud click, echoed by two softer clicks.  There's a brief pause, then another loud click and another echo.  This continues for five to ten minutes until eventually it stops.  If I am disconnected from the external speakers there will be a pause after the sound stops and then a single click, followed by nothing.  Often simply plugging into the external speakers initiates this trouble.  These are the same speakers I used with 9.04 with no problem and the clicking began the moment I upgraded.

The system is an HP Pavilion laptop.

Any thoughts?

Thanks!
~Faximili

---

### Post by ganny on 2009-11-04
I am getting a *very* similar problem - that is, with *any *music player I have tried (Banshee, Songbird, Amarok, Rhythmbox...), it'll play for a certain amount, then suddenly stop and click. If I close the player and start again its all good though.

I noticed that if you check sound preferences when this error occurs, in the Applicatiosn tab the player randomly flashes.

---

### Post by Vermind on 2009-11-04
Same here. With Banshee and Regnum Online, Regnum loses sound after a bit, while banshee keeps playing. Then 3 minutes later banshee sound stops too, and the player is appearing and disappearing in the sound preferences application tab. Later it stabilizes and appears there permanently, but there is no sound. On song change, it works for a few seconds again, then goes off again.

---

### Post by ganny on 2009-11-04
Good to see that I'm not the only one with this issue... Perhaps it has something to do with PulseAudio? It used to be really dodgy so I just disabled it and used ALSA in the previous versions, but I thought I'd give it a chance this time...

---

### Post by Vermind on 2009-11-04
Hello,
I am very sure it is a pulseaudio issue.
For one, the applications section and the whole sound preferences application is pulse-specific, so the application flashing there probably reflects how pulse intermittently sees the app connected/disconnected.

Secondly, in my case, if I close banshee and regnum online in that setup, they both hang. While the process list in system monitor shows both are supposed to be sleeping, they still consume humongous amounts of cpu. Interestingly, killall pulseaudio makes both of them quit cleanly.

I am now experimenting with [The latest ALSA packaged by Marley]("https://launchpad.net/~thefirstm/+archive/karmic-testing"). To quickly add ppa's into your ubuntu, use [the automatic ppa adder]("http://ubuntuforums.org/showthread.php?t=1232171").

---

### Post by ganny on 2009-11-04
You're right... Let us know how you go with ALSA, it would be great if we could solve this.

---

### Post by TheBuzzSaw on 2009-11-04
Whenever my system goes to make it sound, it hesitates, the speakers pop, and the sound streams fine after that. In other words, if a program requests control of sound and holds onto it for a while, it works great. However, whenever it goes to make a brief sound only (such as a login sound in Skype), it does the hesitate/pop/sound pattern.

Ideas?

---

### Post by xenogia on 2009-11-04
> **Vermind said:**
> Hello,
I am very sure it is a pulseaudio issue.
For one, the applications section and the whole sound preferences application is pulse-specific, so the application flashing there probably reflects how pulse intermittently sees the app connected/disconnected.

Secondly, in my case, if I close banshee and regnum online in that setup, they both hang. While the process list in system monitor shows both are supposed to be sleeping, they still consume humongous amounts of cpu. Interestingly, killall pulseaudio makes both of them quit cleanly.

I am now experimenting with [The latest ALSA packaged by Marley]("https://launchpad.net/%7Ethefirstm/+archive/karmic-testing"). To quickly add ppa's into your ubuntu, use [the automatic ppa adder]("http://ubuntuforums.org/showthread.php?t=1232171").


Thanks for this PPA Vermind, it will come in very handy in the future :)

---

### Post by cKGunslinger on 2009-11-04
I have the same issue with VLC.  Videos play fine for X amount of time, then the audio just dissapears.  If I exit VLC and reload the video, I can resume.  Makes watching anything longer than ~15 minutes a hassle.

---

### Post by suzypeppercorn on 2009-11-04
I had a similar problem. I followed what someone said in this thread. Worked like a charm. I also have an HP pavilion laptop.

[http://ubuntuforums.org/showthread.php?p=8246102#post8246102]("http://ubuntuforums.org/showthread.php?p=8246102#post8246102")

---

### Post by ganny on 2009-11-05
> **suzypeppercorn said:**
> I had a similar problem. I followed what someone said in this thread. Worked like a charm. I also have an HP pavilion laptop.

[http://ubuntuforums.org/showthread.php?p=8246102#post8246102](http://ubuntuforums.org/showthread.php?p=8246102#post8246102)

Thanks for the tip, but I tried this before and it didn't work for me :(

EDIT: Actually I checked the file, and it turns out I forgot to put a space between the # and the rest of it. It works fine now! :)

---

### Post by Vermind on 2009-11-05
I am officially going with ALSA on my 64-bit desktop.
Pulse makes my apps use much more CPU than normal and occasionally hang, and additionally the sound clicks, crackles and stutters.
Interestingly, with Rhythmbox and Regnum Online on my EEE PC 901 that is completely swamped under that load, both Regnum and Rhythmbox play flawless sound.

---

### Post by ganny on 2009-11-05
> **Vermind said:**
> I am officially going with ALSA on my 64-bit desktop.
Pulse makes my apps use much more CPU than normal and occasionally hang, and additionally the sound clicks, crackles and stutters.
Interestingly, with Rhythmbox and Regnum Online on my EEE PC 901 that is completely swamped under that load, both Regnum and Rhythmbox play flawless sound.
Do you mind posting how you do so? I'd be very interested to know. Although my problem has been fixed (as of the post above yours), I also find that Pulse is using the CPU a lot more - I've noticed every time I begin playing music my fan starts making a tonne of noise, which it never used to before... I'm thing ALSA would be the way to go.

---

### Post by Vermind on 2009-11-05
My ALSA solution is really simple:
Use synaptic and uninstall pulseaudio. It will ask you to remove also other parts of pulseaudio, and possibly the ubuntu-desktop virtual package. Don't worry, this is harmless. The ubuntu-desktop package only needs to be installed to keep track of Ubuntu guys' default programs, such as the change of Firefox 3 to 3.5 as default, the use of pulse on top of ALSA and so on. In my opinion, ubuntu-desktop (or ubuntu-netbook-remix or kubuntu-desktop or ... ) only needs to be installed when upgrading the system and you want the new defaults. 

Kill pulseaudio after.
Everything will revert to ALSA. If you have some apps that do not auto-detect the sound server and you have manually set them to pulse, time to set them to ALSA again.

Install gnome-alsa-mixer to have a GUI mixer for alsa (though its rather horrible). You lose the volume adjustment and mute shortcuts, which doesn't matter on my desktop, because I have an external Creative remote which I use for volume control. For the shortcuts, You would need to do some xbindkeys magic, which I am not keen to do as of yet. I may use some of the EEE PC ACPI scripts, they looked promising.

---

### Post by Vermind on 2009-11-05
I had some spare time and tried making a volume control script. However, I could not find info on how to show the volume bar with notify-send.
Luckily, [Somebody already solved this for Xubuntu]("http://ubuntuforums.org/showthread.php?t=1174798"), by using osd_cat instead. You need to install xosd-bin for this to work.

The good: it's instant response, unlike the notify bubbles. It shows the volume percentage. Using the gnome shortcuts does away with requiring xbindkeys.
The bad: it's not the same as notify, so it breaks the uniformity of the desktop. It kind of looks like an old TV volume bar.

The original script does not deal with different control names in ALSA, so I modified it a bit for that. Now the awk detects the lines with volume by the % in the volume percentage instead of the orininal "Mono:" keyword. I also added options for different mute and volume channels in ALSA (for example, the mute switch for EEE PC's (at least used to be) iSpeaker, not Master)

Procedure: Put this script anywhere, and make it executable.
Then go to System - Preferences - Keyboard Shortcuts.
Add shortcuts with the commands:
```
/home/you/location/of/the/script/volume-control.sh down
``````

/home/you/location/of/the/script/volume-control.sh up
``````

/home/you/location/of/the/script/volume-control.sh mute
```
Then click on the right side and press a button or button combination to bind to those commands. The script is below.

```

#!/bin/sh

# amixer options
mute_switch="Master" # For Asus EEE, this is iSpeaker
channel="Master" # usually Master. You can set this to PCM to keep headphone volume unchanged.
card=0;
VOL_STEP=2    # amount to increase / decrease volume
# osd_cat options
POS=bottom      # top, middle or bottom
ALIGN=center    # left, center or right
OFFSET=0        # offset from the top or bottom
COLOR=green     # white, blue, yellow, cyan, magenta, etc
MUTECOLOR=brown # color to use instead when muted
SHADOW=2        # offset of shadow, 0 for none
DELAY=3         # seconds to show the OSD
AGE=0           # seems broken :\
BARMODE=slider  # percentage or slider
FONT=-*-helvetica-medium-r-*-*-*-320-*-*-*-*-*-*

if [ "$1" = "mute" ]; then
    amixer -c $card set ${mute_switch} toggle
elif [ "$1" = "up" ]; then
    amixer -c $card set ${channel} $VOL_STEP+
elif [ "$1" = "down" ]; then
    amixer -c $card set ${channel} $VOL_STEP-
else
    echo "Usage: $0 up|down|mute"
    exit 1
fi

STATUS=$(amixer -c 0 sget ${mute_switch} | awk '$0 ~ "\\[off\\]" { print $NF; exit; }' )
VOLUME=$(amixer -c 0 sget ${channel}  | awk '$0 ~ "%" { vol=$(NF-2); gsub("\\[", "", vol); gsub("\\]", "",vol); print vol; exit; }' )
if [ "${STATUS}" = '[off]' ]; then
    STATUS=" (muted)"
    COLOR=$MUTECOLOR
else
    STATUS=""
fi

killall osd_cat

osd_cat -w -p $POS -c $COLOR -s $SHADOW -a $AGE -d $DELAY -o $OFFSET -A $ALIGN \
-b $BARMODE -P $VOLUME -f $FONT -l 1 -T "Volume: $VOLUME$STATUS"

```

---

### Post by ganny on 2009-11-05
Wow thanks very much for your efforts! I'll give it a go and hopefully I won't be back here begging for help :)

---

### Post by arrancaru on 2009-11-06
Best way to fix sound problems in ubuntu: remove pulseaudio and stop wasting time searching google and forums on how to solve these problems. My only wish in life is a ubuntu install option where I can choose between alsa and pulseaudio, and not forced to use this crap.

---

### Post by kennethtb on 2009-11-07
Thanks it worked for me and your instructions were clear and precise just the ticket for an inexperienced user - until now I have never fully grasped deleting items from the terminal.
regards   kenneth

---

### Post by fjornada on 2009-11-16
> **suzypeppercorn said:**
> I had a similar problem. I followed what someone said in this thread. Worked like a charm. I also have an HP pavilion laptop.

[http://ubuntuforums.org/showthread.php?p=8246102#post8246102]("http://ubuntuforums.org/showthread.php?p=8246102#post8246102")

it solved my problem completely. thanks!

---

### Post by calraith on 2009-12-07
> **Vermind said:**
> I had some spare time and tried making a volume control script. However, I could not find info on how to show the volume bar with notify-send.
Luckily, [Somebody already solved this for Xubuntu]("http://ubuntuforums.org/showthread.php?t=1174798"), by using osd_cat instead. You need to install xosd-bin for this to work.

Hey, thanks for the ideas, and the excellent rewrite of the awk statement in the VOLUME= line.  I edited my version and leeched some of your code.  I hope you don't mind.

In your script, the awk statement in the mute detection errors if sound isn't muted.  The script still works, but since I'm slightly OCD, I changed it to use grep -c to count the occurrences of [on].  You can see my changes [here](http://ubuntuforums.org/showthread.php?t=1174798).

---

### Post by sieve on 2009-12-10
I have the same issue with clicking and popping. It sounds like playing a copy of a CD where there were scratches or imperfections in the original that manifest themselves as clicks on the copy.

Very annoying to say the least.

After running around on this issue and trying all kinds of different things, I agree that the issue is with Pulseaudio. Unfortunately, PulseAudio is tightly integrated into Karmic. Nonetheless, removing PulseAudio is an option.  I followed the instructions in this thread

[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=8284273](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=8284273)

and the removal went fine.  However, I was unable to get the system to recognize my Creative Sound Blaster X-Fi Notebook external sound card.  Maybe there was a solution for that problem, but I didn't know it.

So I had no more clicks and pops, but only the sound quality of the internal sound card. I suppose that was an improvement.  But I ended up reinstalling Pulseaudio and playing around with the channel and volume settings to find an option that seemed to be audibly tolerable.

One thing I just thought of now...I have heard that there were sound quality issues with certain X-Fi cards in the past. I should do a control test by putting the card in a different computer (sans Pulseaudio) and see if it is a hardware vs. software issue. If so, I'll report back.

eta - not a hardware issue. Card performed fine sans Pulseaudio

---

### Post by Vermind on 2009-12-11
For extra sound cards and ALSA, you need to tell your ALSA mixer to look at card 1, not 0, and unmute the channels. The gnome-alsamixer (from synaptic) puts different sound cards in their own tabs. Also, in GNOME, you need to run gstreamer-properties and change the ALSA device to the other card if it does not happen automatically. For some applications, such as Skype, audacious, mplayer, and so on, you may need to adjust their sound settings separately.

---

### Post by sieve on 2009-12-11
> **Vermind said:**
> For extra sound cards and ALSA, you need to tell your ALSA mixer to look at card 1, not 0

A ha! But how do I do that?  Is is just as simple as selecting and unselecting tabs in Alsamixer as you discuss below, or is there some command or code I need to type? 


> **Vermind said:**
> and unmute the channels. The gnome-alsamixer (from synaptic) puts different sound cards in their own tabs.

When I looked, I didn't see different sound cards in different tabs. It's possible that I didn't scroll all the way to the right, or maybe they were labeled in a way that I wasn't expecting. I'm not at that computer right now, but I can check again. 


> **Vermind said:**
> Also, in GNOME, you need to run gstreamer-properties and change the ALSA device to the other card if it does not happen automatically. For some applications, such as Skype, audacious, mplayer, and so on, you may need to adjust their sound settings separately.

I'll check that out also.

---

### Post by sieve on 2009-12-14
I figured out how to make it work.

First, as mentioned above, I removed Pulseaudio as per the instructions laid out in this thread:

[http://ubuntu-ky.ubuntuforums.org/sh....php?p=8284273](http://ubuntu-ky.ubuntuforums.org/sh....php?p=8284273)

Pulseaudio successfully uninstalled, but once it's gone, you cannot just simply toggle through multiple installed soundcards . By default, the system recognized the internal soundcard and gave that one priority.  I had to reconfigure the system to give priority to the external soundcard.

To do so, I used the instructions in this thread as a base:

[http://forum.vectorlinux.com/index.php?topic=4888.0](http://forum.vectorlinux.com/index.php?topic=4888.0)

And then modified them based on this thread because the above instructions do not work for Karmic:

[http://kubuntuforums.net/forums/index.php?topic=3106282.new](http://kubuntuforums.net/forums/index.php?topic=3106282.new)

I've summarized the procedures below:

If you have multiple soundcards (like an onboard and an external one), you might have had the problem that the wrong one is the default soundcard. This is because the kernel module for the "wrong" card is loaded first, and if no option is passed when loading the module it gets the first available card number (0).

If they both use a different kernel module you can easily make sure the right one is the default card.

Find out what module is being used for your soundcards:

```
cat /proc/asound/modules
```

On my computer this could give

```
0 snd_intel8x0
1 snd_usb_audio
```

This means that the card that's currently the default soundcard (card 0) uses the internal snd_intel8x0 module.

I want the other one (Creative Soundblaster X-Fi Notebook) to be default.

You can't "reserve" card 0 for a particular module, because the options for a module are only passed when the module is loaded, and the whole problem was that the wrong module is loaded first. So, to make sure the right soundcard is default, we have to make sure the other one becomes card 1 when the module for it is loaded. 

To make the usb (external card) default, I added this line just before the '# Prevent abnormal drivers from grabbing index 0' line in /etc/modprobe.d/alsa-base.conf

```
options snd_intel8x0 index=1
```

And, if the external soundcard (options snd_usb_audio) is listed as one of the 'abnormal cards' right below, you need to put a # at the front of that line.

Then reboot.
Alsa now works right; it plays through the external sound card.

And - No clicking. No popping. No poor sound quality. The external card works like it should.

---

### Post by Vermind on 2010-03-24
For those of us who use ALSA, I recently found [David Lentz's PPA]("https://launchpad.net/~dtl131/+archive/ppa") that has for example gnome-applets, including the volume control applet, compiled against alsa, without pulseaudio. Enjoy.

---

### Post by SuilAmhain on 2010-04-06
I Increased my PCM Volume to max. Solved problem. 

No Config changes required anywhere else...

---

### Post by wasabishot on 2010-06-08
Hey there
Human kind has surprised me once again.
Thanks Vermin - those are great new gnome-applets... finally can control the volume like I should!!!

and thanks sieve - great explanation.. worked just right for me!!

Do you think someone will make it possible to toggle between sound cards with alsa???? it will make everything just perfect!!!

---

### Post by Vermind on 2010-06-08
If you press Alt-F2 or open a terminal,
and type gstreamer-properties
you should be able to change the sound cards used by gstreamer apps.
For others, gnome-sound-properties may do the trick.
For SDL apps, use ```
export SDL_AUDIODRIVER="ALSA"
export AUDIODEV=default
```, where default is the alsa device. ```
aplay -L
``` should list devices.

---

