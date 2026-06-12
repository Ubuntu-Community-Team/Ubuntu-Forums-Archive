---
title: "Any way to use a remote and LIRC to control Unity Launcher?"
date: 2013-04-10
forum: Multimedia Software
---

### Post by Bullwinkle_Moose on 2013-04-10
One thing I have wanted for a while now it to use my MCE compatible remote to do basic moving around and selection in Unity Launcher.  Although I'm not the original poster on this thread, it appears he wants to do exactly the same thing I want to do, and it looks like the first reply is about ¾ of the solution:

[URL="http://askubuntu.com/questions/254417/can-i-set-up-lirc-to-enable-me-to-navigate-the-unity-launcher-using-my-mce-remo"]Can I set up LIRC to enable me to navigate the Unity Launcher, using my MCE Remote Control, and how would I do this?
[/URL]

I've tried the proposed solution and noted exactly the same results - if you add this to your .lircrc file, and then install and run the irxevent software from the lirc-x package in the repository (I had to use Synaptic to get it, it didn't seem to appear in Ubuntu's software center), it works fine when you are out at the desktop:

```
begin
 prog = irxevent
 button = KEY_UP
 repeat = 0
 config = Key Up unity-2d-shell
end

begin
 prog = irxevent
 button = KEY_DOWN
 repeat = 0
 config = Key Down unity-2d-shell
end

begin
 prog = irxevent
 button = KEY_LEFT
 repeat = 0
 config = Key Left unity-2d-shell
end

begin
 prog = irxevent
 button = KEY_RIGHT
 repeat = 0
 config = Key Right unity-2d-shell
end

begin
 prog = irxevent
 button = KEY_PLAY
 config = Key Return unity-2d-shell
 repeat = 0
end

begin
 prog = irxevent
 button = KEY_OK
 config = Key Return unity-2d-shell
 repeat = 0
end
```

Unfortunately, if you are inside another program such as XBMC, using any of those buttons will bring the Launcher to the foreground and the button presses will try to control both Launcher and whatever program you are in, or maybe just Launcher.  And as the text notes, the Focus option (which should restrict it to working only if the selected program has focus) doesn't seem to work.

If one of you guys that knows your way around could take a look at that thread and maybe figure out a way around this problem, it would probably help a lot of folks that would actually like to use their remote to navigate around in Launcher.

By the way, I posted this in here because I figured that this was the most appropriate forum, given that most of the folks in here probably have some experience with remote controls, which is something not true of the typical Ubuntu desktop user.

---

### Post by Bullwinkle_Moose on 2013-04-11
Well I have spent WAY too many hours trying to get this to work.  What I did was create a bash script that disables irxevent if certain pieces of software are running, and enables it otherwise.  Please be aware that I am NOT a programmer and I've maybe written one or two small bash scripts before.  I named it irxeventlauncher.sh and made it executable.  Note that in this script it looks for any of three programs - XBMC, the MythTV frontend, and Boxee, and kills irxevent if any of those are running .  If none of them are running and irxevent is not started, it starts it.  You can of course remove programs you don't use and add others you do, if you like.  You can run this from a terminal window or at startup but there is a small hitch with running it at startup.  I am SURE this can be improved upon so feel free to have at it:

```
#!/bin/bash
function irxeventoff {
        if pidof irxevent >/dev/null 2>&1
        then
                killall irxevent
        fi
}
function irxeventon {
        if pidof irxevent >/dev/null 2>&1
        then
                :
        else
                irxevent &
        fi
}
while :
do
if pgrep xbmc >/dev/null 2>&1
then
        irxeventoff
elif pgrep mythfrontend >/dev/null 2>&1
then
        irxeventoff
elif pgrep Boxee >/dev/null 2>&1
then
        irxeventoff
else
        irxeventon
fi
sleep 2
done
```

This starts an endless loop that runs at 2 second intervals (determined by the sleep statement) that keeps checking to see if any of the monitored software is running, and kills or starts irxevent accordingly.

A few questions I am sure some of you may have:

*Do I have to make the additions to .lircrc in the first post and follow the directions there?*  Yes!

*Does killing irxevent affect use of the remote in any program that has native LIRC support?*   Not that I've seen, other than that it means the two programs won't interfere with each other or steal remote clicks from each other!

*Why did you use pidof to check irxevent and pgrep to check everything else?*  Because that's the only way it worked!  Initally I tried using pgrep all the way through and it appeared to work initially, but then for some reason it stopped working with respect to checking irxevent.  Darned if I know why, but I sure wasted a lot of time and probably got a few gray hairs trying to figure that one out.

*Why do you use if-then-else in the irxeventon function?*  Because that's the only way I could find that reliably tested for irxevent not being running.  I almost think that irxevent is some weird program because I looked at several pages that purportedly showed how to test for a program NOT running in bash, and couldn't get anything to work halfway reliably except that.  However, if you know a better way, feel free to try it.  I actually think the way I did it might be less CPU-intensive than any other solution, but what do I know?

*Have you tested this extensively?*  NO.  Use it at your own risk.

*Will it run if I make it a startup item using Ubuntu's Startup Applications utility?*  Maybe.  You need to include the full path to the script.  And I found something really weird when I set it to run at startup - when Ubuntu's first comes up it does not seem to work (the remote has no effect).  But if I use a keyboard or mouse an maneuver around, at some point it starts working.  For example, if I start a terminal window, it starts working immediately, and continues to work even if I close that window.  This bugs the hell out of me because the whole point of this was to be able to select a program from the Unity Launcher using the remote, even if you don't have a keyboard or mouse plugged in or handy.

*Do you know that your code sucks and you don't know what the hell you're doing?*  Yes I do!  By all means, please feel free to fix or improve upon it!

---

### Post by Rich.T. on 2013-04-23
Hi, Bullwinkle.

That's some great work!
I'm the original poster of the askubuntu question and as I said in reply to the first answerer, Jack;  I have been trying to get a MythTV Backend server up and running lately, so this one has gone on the back burner for the time being, but I will get around to looking into it soon, I hope!

However, around the Start-up issue:

> **Bullwinkle_Moose said:**
> Will it run if I make it a startup item using Ubuntu's Startup Applications utility? Maybe. You need to include the full path to the script. And I found something really weird when I set it to run at startup - when Ubuntu's first comes up it does not seem to work (the remote has no effect). But if I use a keyboard or mouse an maneuver around, at some point it starts working. For example, if I start a terminal window, it starts working immediately, and continues to work even if I close that window. This bugs the hell out of me because the whole point of this was to be able to select a program from the Unity Launcher using the remote, even if you don't have a keyboard or mouse plugged in or handy.

[LIST]
[*]Does irxevent need to be started as a daemon, ie. irxevent -d and would it need to be started (at the beginning of the script) and already running for this script's loop to work?
[*]Also would running the script from /etc/rc.local or turning it into a recurring cron job (no need for the loop) work, rather than making it a Startup Application?
[/LIST]


I don't have the ability to try this at the moment (and I'm not exactly a veteran bash scripter myself, so I may be barking up the wrong tree here), so maybe you could look into this.

Thanks for all the hard work!

---

### Post by Rich.T. on 2013-05-17
> **Bullwinkle_Moose said:**
> You can run this from a terminal window or at startup but there is a small hitch with running it at startup.

Could this be your problem?

[http://ubuntuforums.org/showthread.php?t=1494535&p=9392428#post9392428](http://ubuntuforums.org/showthread.php?t=1494535&p=9392428#post9392428)

> ...that's because you dont wait for lirc daemon to start. The simplest way to solve such problems (not only with lirc) is to write small script like that:
Code:

#!/bin/bash
while [ -z "$(pidof lircd)" ]; do
  sleep 1
done
irxevent ....<your xevents>
exit 0

...then invoke it as startup application
...and don't forget to give it execution permission. 

Maybe add
> while [ -z "$(pidof lircd)" ]; do
  sleep 1
done
to the beginning of the startup script?

---

### Post by Rich.T. on 2013-05-17
@Bullwinkle_Moose

So...
I seem to have everything working, except for actually controlling the Launcher with it!!

I don't know if it is the fact that I'm now running 13.04 (Raring) or that it's simply because I'm using Unity 3D as opposed to 2D, but the .lircrc script that you outlined does not seem to work for me.

I have, however verified that it's up and running by using **CurrentWindow** instead of **unity-2d-shell** and it works fine in a couple of applications.

Here's what I've done:

Script run on start-up **IR.sh** :
```
#!/bin/bash
while [ -z "$(pidof lircd)" ]; do
sleep 1
done 

function irxeventoff {
        if pidof irxevent >/dev/null 2>&1
        then
                killall irxevent
        fi
}
function irxeventon {
        if pidof irxevent >/dev/null 2>&1
        then
                :
        else
                irxevent &
        fi
}
while :
do
if pgrep xbmc >/dev/null 2>&1
then
        irxeventoff
elif pgrep mythfrontend >/dev/null 2>&1
then
        irxeventoff
elif pgrep Boxee >/dev/null 2>&1
then
        irxeventoff
else
        irxeventon
fi
sleep 2
done

```
Script **.lircrc** :
```
#Custom lircrc generated via mythbuntu-lirc-generator
#All application specific lircrc files are within ~/.lirc
include ~/.lirc/unity 
include ~/.lirc/mythtv 
include ~/.lirc/mplayer 
include ~/.lirc/xine 
include ~/.lirc/vlc 
include ~/.lirc/xmame 
include ~/.lirc/xmess 
include ~/.lirc/totem 
include ~/.lirc/elisa 
include ~/.lirc/irexec 
```

Script **~/.lirc/unity**
```
begin
 remote = mceusb
 prog = irxevent
 button = KEY_UP
 repeat = 0
 config = Key Up CurrentWindow
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_DOWN
 repeat = 0
 config = Key Down CurrentWindow
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_LEFT
 repeat = 0
 config = Key Left CurrentWindow
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_RIGHT
 repeat = 0
 config = Key Right CurrentWindow
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_PLAY
 config = Key Return CurrentWindow
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_OK
 config = Key Return CurrentWindow
 repeat = 0
end

```

I'll look further into this when I get a chance, but for now, all I can say is that it *kind of works*.

Thanks.

---

### Post by Rich.T. on 2013-05-19
[SIZE=6]**[COLOR="#2C001E"]Unity Remote Control[/COLOR]**[/SIZE]
[RIGHT][ATTACH=CONFIG]242872[/ATTACH]
[SIZE=1][URL="http://ubuntuforums.org/attachment.php?attachmentid=242872&d=1369186620"]remote-control.png (28.5 KB)
(Save to your ~/Icons folder)[/URL][/SIZE][/RIGHT]
[SIZE=3][CENTER]**[COLOR="#5E2750"]Enabling LIRC Remote Buttons for Unity Desktop on Ubuntu, Including Full Access to the Unity Launcher, Unity Dash and Several Programs and Applications. Remote Control Mouse-Emulation is also available at the push of a button.[/COLOR]**[/CENTER][/SIZE]
[HR][/HR]
**[SIZE=3][COLOR="#77216F"]Tested and working on: [/COLOR][/SIZE]**[INDENT][INDENT][INDENT][INDENT][INDENT][SIZE=3] [Ubuntu 13.04 (Raring Ringtail)]("http://releases.ubuntu.com/raring/")[/SIZE]
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]
[SIZE=3]**[COLOR="#77216F"]Applications:[/COLOR]**
[INDENT][INDENT][INDENT][INDENT][INDENT][table="width: 300"]
[tr]
	[td][[S]Boxee[/S]]("http://bbx.boxee.tv/download#box")[/td]
	[td][/td]
[/tr]
[tr]
	[td][[S]MPlayer[/S]]("http://www.mplayerhq.hu/design7/news.html")[/td]
	[td][[IMG]http://ubuntuforums.org/asset.php?fid=242059&uid=708376&d=1369787389[/IMG]]("apt://mplayer")[/td]
[/tr]
[tr]
	[td][[S]Mythfrontend[/S]]("http://www.mythtv.org/wiki/Mythfrontend")[/td]
	[td][[IMG]http://ubuntuforums.org/asset.php?fid=242059&uid=708376&d=1369787389[/IMG]]("apt://mythtv")[/td]
[/tr]
[tr]
	[td][Onboard]("https://launchpad.net/onboard")[/td]
	[td][/td]
[/tr]
[tr]
	[td][[S]Steam[/S]]("http://store.steampowered.com/")[/td]
	[td][[IMG]http://ubuntuforums.org/asset.php?fid=242059&uid=708376&d=1369787389[/IMG]]("apt://steam-launcher")[/td]
[/tr]
[tr]
	[td][[S]Totem[/S]]("http://projects.gnome.org/totem/")[/td]
	[td][/td]
[/tr]
[tr]
	[td][VLC]("http://www.videolan.org/vlc/index.html")[/td]
	[td][[IMG]http://ubuntuforums.org/asset.php?fid=242059&uid=708376&d=1369787389[/IMG]]("apt://vlc")[/td]
[/tr]
[tr]
	[td][XBMC]("http://xbmc.org/")[/td]
	[td][[IMG]http://ubuntuforums.org/asset.php?fid=242059&uid=708376&d=1369787389[/IMG]]("apt://xbmc")[/td]
[/tr]
[tr]
	[td][[S]xine[/S]]("http://www.xine-project.org/home")[/td]
	[td][[IMG]http://ubuntuforums.org/asset.php?fid=242059&uid=708376&d=1369787389[/IMG]]("apt://xine-ui")[/td]
[/tr]
[tr]
	[td][[S]Xmame[/S]]("http://freecode.com/projects/xmame")[/td]
	[td][/td]
[/tr]
[tr]
	[td][[S]Xmess[/S]]("http://jausoft.com/Files/GLMame/old/xmame-doc-3.html")[/td]
	[td][/td]
[/tr]
[/table][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/SIZE]
[HR][/HR]
[SIZE=3]**[COLOR="#5E2750"]The Aim:[/COLOR]**[/SIZE]
[INDENT][INDENT][INDENT][INDENT][INDENT][COLOR="#2C001E"]The applications listed above (and others, through careful configuration) should work either with or alongside this Unity IR setup; either through [irexec]("http://www.google.co.uk/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&cad=rja&ved=0CDEQFjAA&url=http%3A%2F%2Fwww.lirc.org%2Fhtml%2Firexec.html&ei=oDelUYisLfOT0QXn9oHABA&usg=AFQjCNGz-5XxVq97x8BamhHwlpSTuDbQCg&bvm=bv.47008514,d.d2k"), [irxevent]("http://www.google.co.uk/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&cad=rja&ved=0CDEQFjAA&url=http%3A%2F%2Fwww.lirc.org%2Fhtml%2Firxevent.html&ei=wzelUdipJemX1AXGiYHACA&usg=AFQjCNGM8G5sI1leUGYo7pWvDWj7iNCZPw&bvm=bv.47008514,d.d2k"), [lircmd]("http://www.google.co.uk/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&cad=rja&ved=0CDEQFjAA&url=http%3A%2F%2Fwww.lirc.org%2Fhtml%2Flircmd.html&ei=6DelUfrOB-ey0QXZw4HIDQ&usg=AFQjCNGHgqgQ6CnePtZMnvHVFwpXXpMZAg&bvm=bv.47008514,d.d2k") or through their own IR parser. This set-up aims to ensure that these processes do not interfere with each other, causing conflicts between key-presses and making the user experience unbearable.[/COLOR][/INDENT]
[/INDENT][/INDENT][/INDENT][/INDENT]
[HR][/HR]
[SIZE=3]**[COLOR="#5E2750"]The Process:[/COLOR]**[/SIZE]
[INDENT][INDENT][INDENT][INDENT][B][COLOR="#dd4814"][LIST=1]
[*]Get a LIRC Compatable Remote and Receiver and plug it in to your PC.
[*]Install needed programs.
[*]Create scripts in your ~/Scripts folder.
[*]Add Unity IR script to start-up applications.
[*]Use command-line tools to identify the programs you wish to start and the buttons they are to be mapped to.
[*]Use the gathered information to construct the necessary configuration files.
[*]Configure IR mouse daemon lircmd.
[*]Reboot and try it out!
[*]Additional References.
[/LIST][/COLOR][/INDENT][/INDENT][/INDENT][/INDENT][/B]
[HR][/HR]
[SIZE=3]**1.** Get a LIRC Compatible Remote and Receiver and plug it in to your PC.[/SIZE]

This is pretty self explanatory, really. [The LIRC website]("http://www.lirc.org/") has all the information you will need as to what is or isn't compatible.
Here's the remote control that I used to set up this configuration:
[INDENT][ATTACH=CONFIG]243210[/ATTACH][ATTACH=CONFIG]243181[/ATTACH][/INDENT]
It's an HP branded Windows Media Center Remote from HP and comes with a receiver and transmitter unit (mceusb).
During the LIRC installation process, I select this remote with the option: **Windows Media Center Transceivers/Remotes (all)**.
[HR][/HR]
[SIZE=3]**2.** Install needed programs:[/SIZE]

[INDENT][HIGHLIGHT]Sudo apt-get install lirc lirc-x xdotool gksu[/HIGHLIGHT][/INDENT]
[HR][/HR]
[SIZE=3]**3.** Create scripts in your ~/Scripts folder:[/SIZE]

[INDENT][SIZE=1][COLOR="#5E2750"]Note: Replace any instances of **~/foo/bar/etc** with the full path;
ie. **/home/[username]/foo/bar/etc**, if the script is to be run as root.[/COLOR][/SIZE][/INDENT]

[INDENT]**3a.** [HIGHLIGHT]geany ~/Scripts/Unity-IR.sh[/HIGHLIGHT]
```
#!/bin/bash

# Script to enable irevent and irexec on start-up and then disable them
# as soon as certain programs are launched. Also starts lircmd.
# http://ubuntuforums.org/member.php?u=708376
# http://askubuntu.com/users/113523/rich-t
# Thanks go to Bulwinkle_Moose for getting the ball rolling:
# http://ubuntuforums.org/member.php?u=193624
# http://askubuntu.com/users/149558/bullwinkle-moose

notify-send -i ~/Icons/remote-control.png "Waiting for" "Remote Control"

while [ -z "$(pidof lircd)" ]; do
sleep 1
done 

sudo lircmd --uinput

function irxeventoff {
        if pidof irxevent >/dev/null 2>&1
        then
                killall irxevent
        fi
}
function irxeventon {
        if pidof irxevent >/dev/null 2>&1
        then
                :
        else
                irxevent &
        fi
}
function irexecoff {
        if pidof irexec >/dev/null 2>&1
        then
                killall irexec
        fi
}
function irexecon {
        if pidof irexec >/dev/null 2>&1
        then
                :
        else
                killall notify-osd
                sleep 1
                notify-send -i ~/Icons/remote-control.png "Desktop Remote Control" "Active" &
                irexec &
        fi
}
# For readability, list the applications to be monitored in this script alphabetically.
# Programs which require irxevent support should call irexecoff only.
# Those which have their own IR support should call both irexecoff and irxeventoff.
while :
do
if pgrep Boxee >/dev/null 2>&1
then
        irxeventoff
        irexecoff
elif pgrep elisa >/dev/null 2>&1
then
        irexecoff
elif pgrep IR-Mouse.sh >/dev/null 2>&1
then
        irxeventoff
        irexecoff
elif pgrep mplayer >/dev/null 2>&1
then
        irexecoff
elif pgrep mythfrontend >/dev/null 2>&1
then
        irxeventoff
        irexecoff
elif pgrep onboard >/dev/null 2>&1
then
        irxeventoff
        irexecoff
elif pgrep steam >/dev/null 2>&1
then
        irxeventoff
        irexecoff
elif pgrep totem >/dev/null 2>&1
then
        irexecoff
elif pgrep vlc >/dev/null 2>&1
then
        irexecoff
elif pgrep xbmc >/dev/null 2>&1
then
        irxeventoff
        irexecoff
elif pgrep xine >/dev/null 2>&1
then
        irexecoff
elif pgrep xmame >/dev/null 2>&1
then
        irexecoff
elif pgrep xmess >/dev/null 2>&1
then
        irexecoff
else
        irxeventon
        irexecon
fi
sleep 2
done
```
[INDENT][HIGHLIGHT]chmod a+x ~/Scripts/Unity-IR.sh[/HIGHLIGHT]
[INDENT][SIZE=1]
[http://ubuntuforums.org/showthread.php?t=1494535](http://ubuntuforums.org/showthread.php?t=1494535)
[http://ubuntuforums.org/showthread.php?t=1411620](http://ubuntuforums.org/showthread.php?t=1411620)
[http://askubuntu.com/a/190397/113523](http://askubuntu.com/a/190397/113523)
[http://www.webupd8.org/2010/05/finally-easy-way-to-customize-notify.html](http://www.webupd8.org/2010/05/finally-easy-way-to-customize-notify.html)
[https://launchpad.net/~leolik/+archive/leolik/+packages](https://launchpad.net/~leolik/+archive/leolik/+packages)[/SIZE][/INDENT][/INDENT]

**3b.** [HIGHLIGHT]gksu geany ~/Scripts/Play_Blueray.sh[/HIGHLIGHT]
```
#!/bin/bash
# Play Blueray on Ubuntu
# Thanks to Brendan at http://fozztech.wordpress.com/ for this script.
# http://fozztech.wordpress.com/2011/08/22/bluray-on-ubuntu/
# To install MakeMKV (Thanks to Jeff Bower at https://www.ebower.com):
# https://www.ebower.com/docs/ubuntu-bluray/#MakeMKV
# sudo add-apt-repository ppa:ubuntu-ebower/ebower && sudo apt-get update && sudo apt-get install makemkv-install
# Visit http://www.makemkv.com/forum2/viewtopic.php?f=3&t=224 to find latest version number.
# sudo makemkv-install VERSION (eg. 1.8.2)
# For free MakeMKV beta key:
# http://www.makemkv.com/forum2/viewtopic.php?f=5&t=1053

#start makemkvcon on a new thread writing to a log in /tmp/
makemkvcon stream dev:/dev/sr0 > /tmp/makemkvcon.log &

#Notify the desktop user
notify-send -i media-optical "Starting Disc" "Bluray"

#wait for the port to open, this indicates makemkvcon is ready
DATA=''
while [[ -z $DATA ]]; do
sleep 1
DATA=`netstat -lnp | grep 51000 2>/dev/null`
done

#grep the log and parse out the list of titles
cat /tmp/makemkvcon.log | grep "was added as title" | awk '{print $7 }' | sed -e 's/^#//' > /tmp/titles.list

#load each title from the list as a url
TITLES=""
while read line
do
TITLES="$TITLES http://localhost:51000/stream/title$line.ts"
done < /tmp/titles.list

#clean up
rm /tmp/title.list
rm /tmp/makemkvcon.log

#open vlc with all titles in order
vlc -I lirc -f $TITLES &
```

[INDENT][HIGHLIGHT]sudo chmod a+x ~/Scripts/Play_Blueray.sh[/HIGHLIGHT]

[INDENT][SIZE=1][COLOR="#5E2750"]Note: As mentioned in the script; to play Blueray on Ubuntu, you must first install MakeMKV.
[HIGHLIGHT]sudo add-apt-repository ppa:ubuntu-ebower/ebower && sudo apt-get update && sudo apt-get install makemkv-install[/HIGHLIGHT]
Visit [http://www.makemkv.com/forum2/viewtopic.php?f=3&t=224](http://www.makemkv.com/forum2/viewtopic.php?f=3&t=224) to find latest version number.
[HIGHLIGHT]sudo makemkv-install VERSION[/HIGHLIGHT] (eg. 1.8.2)
For free MakeMKV beta key:
[http://www.makemkv.com/forum2/viewtopic.php?f=5&t=1053](http://www.makemkv.com/forum2/viewtopic.php?f=5&t=1053)[/COLOR][/SIZE][/INDENT][/INDENT]

**3c.** [HIGHLIGHT]geany ~/Scripts/keyboard.sh[/HIGHLIGHT]
```
#!/bin/bash

# A little script to allow the onscreen keyboard
# to be toggled on and (completely) off with one
# remote control button or desktop shortcut.

if pgrep onboard >/dev/null 2>&1
        then
                killall onboard
                exit
        else
                onboard &
        fi
```
[INDENT][HIGHLIGHT]chmod a+x ~/Scripts/keyboard.sh[/HIGHLIGHT][/INDENT]

**3d.** [HIGHLIGHT]sudo cp /usr/share/applications/onboard.desktop /usr/share/applications/onboard.desktop.old[/HIGHLIGHT]
[HIGHLIGHT]gksu geany /usr/share/applications/onboard.desktop[/HIGHLIGHT]

[INDENT]Change the line [HIGHLIGHT]Exec=onboard[/HIGHLIGHT]
to: [HIGHLIGHT]Exec=~/Scripts/keyboard.sh[/HIGHLIGHT]

[INDENT][SIZE=1][COLOR="#5E2750"]Note: Application shortcuts can be dragged from [HIGHLIGHT]/usr/share/applications/[/HIGHLIGHT]
and dropped on to the Sidebar (unity-launcher).
[https://wiki.ubuntu.com/Accessibility/Specs/SOK](https://wiki.ubuntu.com/Accessibility/Specs/SOK)
[https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles#Adding_shortcuts_to_a_launcher](https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles#Adding_shortcuts_to_a_launcher)
[https://launchpad.net/ubuntu/+spec/sok](https://launchpad.net/ubuntu/+spec/sok)

Note: Onboard, the Ubuntu on-screen keyboard works nicely with **mceusb**
selected as the input device through its **Scanning** interface.
This, however does not work at all when LIRC is installed. :-(
We will therefore need to use LIRC's Mouse-Mode daemon **lircmd**.[/COLOR][/SIZE][/INDENT][/INDENT]

**3e.** [HIGHLIGHT]geany ~/Scripts/IR-Mouse.sh[/HIGHLIGHT]
```
#!/bin/bash

# Script to display a dialog box to toggle LIRC mouse-mode off.
# This will help to prevent conflicts between lircmd, irexec and
# irxevent when used in combination with Unity-IR.sh.

killall notify-osd
sleep 1
notify-send -i mouse "Unity Remote-Control" "Mouse-Mode Active" &
sleep 1
zenity --info \
  --no-wrap \
  --title="IR-Mouse" \
  --window-icon="/home/richard/Icons/remote-control.png" \
  --text="<big><b>Unity Remote-Control Mouse-Mode Activated:</b></big>
Please leave this window open while <i>mousing around</i>.
  
     <small>This will help to prevent conflicts between
     remote control interpreters from occurring.</small>
     
     Please click <b>OK</b> to return to
     Push-Button Browsing mode.
     
<b>Thank You. &#9786;</b>"
# lircmd must be run as root, so you must add /usr/sbin/lircmd
# to your /etc/sudoers file, or (recommended) add to /etc/sudoers.d.
sudo killall lircmd
sleep 1
sudo lircmd --uinput
Exit
```
[HIGHLIGHT]chmod a+x ~/Scripts/IR-Mouse.sh[/HIGHLIGHT]

[INDENT][SIZE=1][http://manpages.ubuntu.com/manpages/hardy/man1/zenity.1.html](http://manpages.ubuntu.com/manpages/hardy/man1/zenity.1.html)
[https://help.gnome.org/users/zenity/stable/](https://help.gnome.org/users/zenity/stable/)
[http://ubuntuforums.org/showthread.php?t=1250143&p=7860216#post7860216](http://ubuntuforums.org/showthread.php?t=1250143&p=7860216#post7860216)[/SIZE][/INDENT][/INDENT]
[HR][/HR]
[SIZE=3]**4.** Add Unity IR script to start-up applications:[/SIZE]

[INDENT]Name: [HIGHLIGHT]Unity IR[/HIGHLIGHT]
Command: [HIGHLIGHT]/home/<USERNAME>/Scripts/Unity-IR.sh[/HIGHLIGHT]
 Comment: [HIGHLIGHT]Script to enable irxevent and irexec on start-up and then disable them as soon as certain programs are launched.[/HIGHLIGHT][/INDENT]
[HR][/HR]
[SIZE=3]**5.** Use command-line tools to identify the programs you wish to start and the buttons they are to be mapped to:[/SIZE]

[LIST]
[*]Use the text editor of your choice to edit or create config files.
[*]Use [HIGHLIGHT]xwininfo[/HIGHLIGHT] to find window ids etc.
[SIZE=1][INDENT][http://manpages.ubuntu.com/manpages/hardy/man1/xwininfo.1.html](http://manpages.ubuntu.com/manpages/hardy/man1/xwininfo.1.html)[/INDENT][/SIZE]
[*]Use [HIGHLIGHT]irw[/HIGHLIGHT] to give button names on your remote control.
[SIZE=1][INDENT][http://www.lirc.org/html/irw.html](http://www.lirc.org/html/irw.html)[/INDENT][/SIZE]
[*]Use [HIGHLIGHT]xdotool[/HIGHLIGHT] to simulate keyboard presses etc. (eg. [HIGHLIGHT]xdotool key alt+F1[/HIGHLIGHT])
[SIZE=1][INDENT][http://manpages.ubuntu.com/manpages/lucid/man1/xdotool.1.html](http://manpages.ubuntu.com/manpages/lucid/man1/xdotool.1.html)
[http://askubuntu.com/questions/28086/what-are-unitys-keyboard-and-mouse-shortcuts](http://askubuntu.com/questions/28086/what-are-unitys-keyboard-and-mouse-shortcuts)[/INDENT][/SIZE]
[*]Use [HIGHLIGHT]irexec[/HIGHLIGHT] to test your *irexec* config file.
[SIZE=1][INDENT][http://www.lirc.org/html/irexec.html](http://www.lirc.org/html/irexec.html)
[http://www.lirc.org/html/irxevent.html](http://www.lirc.org/html/irxevent.html)[/INDENT][/SIZE]
[*]Use [HIGHLIGHT]sudo service lirc restart[/HIGHLIGHT] to restart lirc and reload your *irxevent* config files.
[SIZE=1][INDENT][http://askubuntu.com/questions/202404/lirc-how-to-enable-changes-in-etc-lirc-lircrc-without-reboot?rq=1](http://askubuntu.com/questions/202404/lirc-how-to-enable-changes-in-etc-lirc-lircrc-without-reboot?rq=1)[/INDENT][/SIZE]
[*]Check out [HIGHLIGHT]/usr/include/X11/keysymdef.h[/HIGHLIGHT] and [HIGHLIGHT]/usr/include/X11/XF86keysym.h[/HIGHLIGHT] for keyboard definitions and key names.
[SIZE=1][INDENT][http://www.wh9.tu-dresden.de/~heinrich/lirc/irxevent/irxevent.keys](http://www.wh9.tu-dresden.de/~heinrich/lirc/irxevent/irxevent.keys)
[http://askubuntu.com/a/93789/113523](http://askubuntu.com/a/93789/113523)
[http://ubuntuforums.org/showthread.php?t=1459689](http://ubuntuforums.org/showthread.php?t=1459689)[/INDENT][/SIZE][/LIST]
[HR][/HR]
[SIZE=3]**6.** Use the gathered information to construct the necessary configuration files.[/SIZE]

[SIZE=1][INDENT][COLOR="#5E2750"]Note: Use Find/Replce in your text editor to quickly alter recurring terms in your config files.[/COLOR][/INDENT][/SIZE]
[INDENT][SIZE=3]Examples from my IR configuration:[/SIZE]

[INDENT][SIZE=1][COLOR="#5E2750"]Note: I find it handy to use irexec as a general IR parser for the Unity Desktop and so have
mapped all of my remote control's buttons to the **~/.lirc/irexec** script. If you wish to be more
focussed in your approach and minimise conflicts, then comment out all unwanted buttons in this
script and then uncomment the [HIGHLIGHT]#include ~/.lirc/unity-launcher_nofocus[/HIGHLIGHT] line in the **~/.lircrc** script.[/COLOR][/SIZE][/INDENT]

**My [HIGHLIGHT]~/.lircrc[/HIGHLIGHT] file:**
```
#Custom lircrc generated via mythbuntu-lirc-generator
#All application specific lircrc files are within ~/.lirc

#include ~/.lirc/unity-launcher 
#include ~/.lirc/unity-dash
# Activating both unity-launcher and unity-dash scripts causes
# conflicts.
# Activate only one of them, but without the FOCUS attribute:
#include ~/.lirc/unity-launcher_nofocus 
# Activating unity-launcher irxevent script is not necessary when
# irexec is configured for general desktop use and will cause
# conflicts. Configure irxevent scripts for unique key bindings
# in individual applications and disable irxevent when they are
# launched. This is done via UnityIR.sh.
#include ~/.lirc/unity-panel 
# Unity Panel doesn't accept irxevent!
#include ~/.lirc/CurrentWindow 
# CurrentWindow - For Testing Remote Control.
include ~/.lirc/mythtv 
include ~/.lirc/mplayer 
include ~/.lirc/xine 
include ~/.lirc/vlc 
include ~/.lirc/xmame 
include ~/.lirc/xmess 
include ~/.lirc/totem 
include ~/.lirc/elisa 
include ~/.lirc/irexec 
```

**My [HIGHLIGHT]~/.lirc/irexec[/HIGHLIGHT] file:**
```
# LIRCRC Auto Generated by Mythbuntu Lirc Generator
# Author(s): Mario Limonciello, Nick Fox, John Baab
# Created for use with Mythbuntu
begin
    remote = mceusb_hauppauge
    prog = irexec
    button = Power
    button = Clear
    config = (kill $(pgrep mythfrontend) || true) && mythfrontend --service &
    repeat = 0
    delay = 0
end

begin
    remote = vista_mce
    prog = irexec
    button = Power
    button = Clear
    config = (kill $(pgrep mythfrontend) || true) && mythfrontend --service &
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = irexec
    button = KEY_POWER
    button = KEY_CLEAR
    config = (kill $(pgrep mythfrontend) || true) && mythfrontend --service &
    repeat = 0
    delay = 0
end

#begin
#    remote = mceusb
#    prog = irexec
#    button = KEY_DVD
#    config = /usr/bin/xdotool key XF86TopMenu
#    repeat = 0
#    delay = 0
#end

begin
    remote = mceusb
    prog = irexec
    button = KEY_DVD
    config = ~/Scripts/Play_Blueray.sh
    repeat = 0
    delay = 0
end

#begin
#    remote = mceusb
#    prog = irexec
#    button = KEY_POWER
#    config = /usr/bin/xdotool key XF86PowerOff
#    repeat = 0
#    delay = 0
#end

begin
    remote = mceusb
    prog = irexec
    button = KEY_POWER
    config = /usr/bin/gnome-session-quit --power-off
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = irexec
    button = KEY_TV
    config = /usr/bin/xdotool key XF86Video
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = irexec
    button = KEY_RADIO
    config = steam steam://open/bigpicture
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = irexec
    button = KEY_AUDIO
    config = /usr/bin/xdotool key XF86Music
    repeat = 0
    delay = 0
end

#begin
#    remote = mceusb
#    prog = irexec
#    button = Pictures
#    config = /usr/bin/xdotool key XF86Pictures
#    repeat = 0
#    delay = 0
#end

begin
    remote = mceusb
    prog = irexec
    button = Pictures
    config = /usr/bin/shotwell
    repeat = 0
    delay = 0
end

#begin
#    remote = mceusb
#    prog = irexec
#    button = KEY_VIDEO
#    config = /usr/bin/xdotool key XF86Video
#    repeat = 0
#    delay = 0
#end

begin
    remote = mceusb
    prog = irexec
    button = KEY_VIDEO
    config = /usr/bin/xbmc
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = irexec
    button = KEY_RECORD
    config = /usr/bin/xdotool key XF86AudioRecord
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = irexec
    button = KEY_PLAY
    config = /usr/bin/xdotool key XF86AudioPlay
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = irexec
    button = KEY_STOP
    config = /usr/bin/xdotool key XF86AudioStop
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = irexec
    button = KEY_REWIND
    config = /usr/bin/xdotool key XF86AudioRewind
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = irexec
    button = KEY_FORWARD
    config = /usr/bin/xdotool key XF86BackForward
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = irexec
    button = KEY_AGAIN
    config = /usr/bin/xdotool key XF86AudioPrev
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = irexec
    button = KEY_NEXT
    config = /usr/bin/xdotool key XF86AudioNext
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = irexec
    button = KEY_PAUSE
    config = /usr/bin/xdotool key XF86AudioPause
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = irexec
    button = KEY_BACK
    config = /usr/bin/xdotool key Escape
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = irexec
    button = More
    config = /usr/bin/xdotool key Menu
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = irexec
    button = KEY_UP
    config = /usr/bin/xdotool key Up
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = irexec
    button = KEY_DOWN
    config = /usr/bin/xdotool key Down
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = irexec
    button = KEY_LEFT
    config = /usr/bin/xdotool key Left
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = irexec
    button = KEY_RIGHT
    config = /usr/bin/xdotool key Right
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = irexec
    button = KEY_OK
    config = /usr/bin/xdotool key Return
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = irexec
    button = KEY_VOLUMEUP
    config = /usr/bin/xdotool key XF86AudioRaiseVolume
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = irexec
    button = KEY_VOLUMEDOWN
    config = /usr/bin/xdotool key XF86AudioLowerVolume
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = irexec
    button = KEY_HOME
    config = /usr/bin/xdotool key alt+F1
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = irexec
    button = KEY_MUTE
    config = /usr/bin/xdotool key XF86AudioMute
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = irexec
    button = KEY_CHANNELUP
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = irexec
    button = KEY_CHANNELDOWN
    config = /usr/bin/xdotool key XF86Back
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = irexec
    button = LiveTV
    config = /usr/bin/xdotool key XF86Video
    repeat = 0
    delay = 0
end

#begin
#    remote = mceusb
#    prog = irexec
#    button = Guide
#    config = /usr/bin/xdotool key XF86Video
#    repeat = 0
#    delay = 0
#end

begin
    remote = mceusb
    prog = irexec
    button = Guide
    config = usr/bin/yelp
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = irexec
    button = RecTV
    config = /usr/bin/xdotool key XF86Video
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = irexec
    button = KEY_1
    config = /usr/bin/xdotool key 1
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = irexec
    button = KEY_2
    config = /usr/bin/xdotool key 2
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = irexec
    button = KEY_3
    config = /usr/bin/xdotool key 3
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = irexec
    button = KEY_4
    config = /usr/bin/xdotool key 4
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = irexec
    button = KEY_5
    config = /usr/bin/xdotool key 5
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = irexec
    button = KEY_6
    config = /usr/bin/xdotool key 6
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = irexec
    button = KEY_7
    config = /usr/bin/xdotool key 7
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = irexec
    button = KEY_8
    config = /usr/bin/xdotool key 8
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = irexec
    button = KEY_9
    config = /usr/bin/xdotool key 9
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = irexec
    button = KEY_0
    config = /usr/bin/xdotool key 0
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = irexec
    button = Star
    config = /usr/bin/xdotool key asterisk
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = irexec
    button = Hash
    config = /usr/bin/xdotool key numbersign
    repeat = 0
    delay = 0
end

#begin
#    remote = mceusb
#    prog = irexec
#    button = KEY_CLEAR
#    config = /usr/bin/xdotool key Clear
#    repeat = 0
#    delay = 0
#end

begin
    remote = mceusb
    prog = irexec
    button = KEY_CLEAR
    config = /home/richard/Scripts/IR-Mouse.sh
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = irexec
    button = Print
    config = /usr/bin/xdotool key Print
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = irexec
    button = KEY_ENTER
    button = More
    config = /usr/bin/xdotool key alt+F10
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = irexec
    button = KEY_ENTER
    button = KEY_CLEAR
    config = /home/richard/Scripts/keyboard.sh
    repeat = 0
    delay = 0
end
```

**My [HIGHLIGHT]~/.lirc/unity-launcher[/HIGHLIGHT] file:**
```
begin
 remote = mceusb
 prog = irxevent
 button = KEY_UP
 repeat = 0
 config = Key Up Focus unity-launcher
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_DOWN
 repeat = 0
 config = Key Down Focus unity-launcher
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_LEFT
 repeat = 0
 config = Key Left Focus unity-launcher
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_RIGHT
 repeat = 0
 config = Key Right Focus unity-launcher
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_PLAY
 config = Key Return Focus unity-launcher
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_STOP
 config = Key Escape Focus unity-launcher
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_OK
 config = Key Return Focus unity-launcher
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_FORWARD
 config = Key Return Focus unity-launcher
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_REWIND
 config = Key BackSpace Focus unity-launcher
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_NEXT
 config = Key Return Focus unity-launcher
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_AGAIN
 config = Key BackSpace Focus unity-launcher
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_BACK
 config = Key Escape Focus unity-launcher
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = More
 config = Key Menu Focus unity-launcher
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_1
 config = Key 1 Focus unity-launcher
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_2
 config = Key 2 Focus unity-launcher
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_3
 config = Key 3 Focus unity-launcher
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_4
 config = Key 4 Focus unity-launcher
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_5
 config = Key 5 Focus unity-launcher
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_6
 config = Key 6 Focus unity-launcher
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_7
 config = Key 7 Focus unity-launcher
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_8
 config = Key 8 Focus unity-launcher
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_9
 config = Key 9 Focus unity-launcher
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_0
 config = Key 0 Focus unity-launcher
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = Star
 config = Key KP_Multiply Focus unity-launcher
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = Hash
 config = Key numbersign Focus unity-launcher
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_ENTER
 config = Key KP_Enter Focus unity-launcher
 repeat = 0
end

#begin
# remote = mceusb
# prog = irxevent
# button = KEY_
# config = Key  Focus unity-launcher
# repeat = 0
#end
```

**My [HIGHLIGHT]~/.lirc/unity-dash[/HIGHLIGHT] file:**
```
begin
 remote = mceusb
 prog = irxevent
 button = KEY_UP
 repeat = 0
 config = Key Up Focus unity-dash
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_DOWN
 repeat = 0
 config = Key Down Focus unity-dash
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_LEFT
 repeat = 0
 config = Key Left Focus unity-dash
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_RIGHT
 repeat = 0
 config = Key Right Focus unity-dash
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_PLAY
 config = Key Return Focus unity-dash
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_STOP
 config = Key Escape Focus unity-dash
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_OK
 config = Key Return Focus unity-dash
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_FORWARD
 config = Key Return Focus unity-dash
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_REWIND
 config = Key BackSpace Focus unity-dash
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_NEXT
 config = Key Return Focus unity-dash
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_AGAIN
 config = Key BackSpace Focus unity-dash
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_BACK
 config = Key Escape Focus unity-dash
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = More
 config = Key Menu Focus unity-dash
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_1
 config = Key 1 Focus unity-dash
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_2
 config = Key 2 Focus unity-dash
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_3
 config = Key 3 Focus unity-dash
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_4
 config = Key 4 Focus unity-dash
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_5
 config = Key 5 Focus unity-dash
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_6
 config = Key 6 Focus unity-dash
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_7
 config = Key 7 Focus unity-dash
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_8
 config = Key 8 Focus unity-dash
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_9
 config = Key 9 Focus unity-dash
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_0
 config = Key 0 Focus unity-dash
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = Star
 config = Key KP_Multiply Focus unity-dash
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = Hash
 config = Key numbersign Focus unity-dash
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_ENTER
 config = Key KP_Enter Focus unity-dash
 repeat = 0
end

#begin
# remote = mceusb
# prog = irxevent
# button = KEY_
# config = Key  Focus unity-dash
# repeat = 0
#end
```

**My [HIGHLIGHT]~/.lirc/unity-launcher_nofocus[/HIGHLIGHT] file:**
```

begin
 remote = mceusb
 prog = irxevent
 button = KEY_UP
 repeat = 0
 config = Key Up unity-launcher
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_DOWN
 repeat = 0
 config = Key Down unity-launcher
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_LEFT
 repeat = 0
 config = Key Left unity-launcher
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_RIGHT
 repeat = 0
 config = Key Right unity-launcher
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_PLAY
 config = Key Return unity-launcher
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_STOP
 config = Key Escape unity-launcher
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_OK
 config = Key Return unity-launcher
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_FORWARD
 config = Key Return unity-launcher
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_REWIND
 config = Key BackSpace unity-launcher
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_NEXT
 config = Key Return unity-launcher
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_AGAIN
 config = Key BackSpace unity-launcher
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_BACK
 config = Key Escape unity-launcher
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = More
 config = Key Menu unity-launcher
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_1
 config = Key 1 unity-launcher
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_2
 config = Key 2 unity-launcher
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_3
 config = Key 3 unity-launcher
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_4
 config = Key 4 unity-launcher
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_5
 config = Key 5 unity-launcher
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_6
 config = Key 6 unity-launcher
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_7
 config = Key 7 unity-launcher
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_8
 config = Key 8 unity-launcher
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_9
 config = Key 9 unity-launcher
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_0
 config = Key 0 unity-launcher
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = Star
 config = Key KP_Multiply unity-launcher
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = Hash
 config = Key numbersign unity-launcher
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_ENTER
 config = Key KP_Enter unity-launcher
 repeat = 0
end

#begin
# remote = mceusb
# prog = irxevent
# button = KEY_
# config = Key  unity-launcher
# repeat = 0
#end
```

**My [HIGHLIGHT]~/.lirc/unity-panel[/HIGHLIGHT] file:**
```
begin
 remote = mceusb
 prog = irxevent
 button = KEY_UP
 repeat = 0
 config = Key Up unity-panel
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_DOWN
 repeat = 0
 config = Key Down unity-panel
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_LEFT
 repeat = 0
 config = Key Left unity-panel
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_RIGHT
 repeat = 0
 config = Key Right unity-panel
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_PLAY
 config = Key Return unity-panel
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_STOP
 config = Key Escape unity-panel
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_OK
 config = Key Return unity-panel
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_FORWARD
 config = Key Return unity-panel
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_REWIND
 config = Key BackSpace unity-panel
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_NEXT
 config = Key Return unity-panel
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_AGAIN
 config = Key BackSpace unity-panel
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_BACK
 config = Key Escape unity-panel
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = More
 config = Key Menu unity-panel
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_1
 config = Key 1 unity-panel
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_2
 config = Key 2 unity-panel
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_3
 config = Key 3 unity-panel
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_4
 config = Key 4 unity-panel
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_5
 config = Key 5 unity-panel
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_6
 config = Key 6 unity-panel
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_7
 config = Key 7 unity-panel
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_8
 config = Key 8 unity-panel
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_9
 config = Key 9 unity-panel
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_0
 config = Key 0 unity-panel
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = Star
 config = Key KP_Multiply unity-panel
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = Hash
 config = Key numbersign unity-panel
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_ENTER
 config = Key KP_Enter unity-panel
 repeat = 0
end

#begin
# remote = mceusb
# prog = irxevent
# button = KEY_
# config = Key  unity-panel
# repeat = 0
#end
```

**My [HIGHLIGHT]~/.lirc/CurrentWindow[/HIGHLIGHT] file:**
```
begin
 remote = mceusb
 prog = irxevent
 button = KEY_UP
 repeat = 0
 config = Key Up CurrentWindow
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_DOWN
 repeat = 0
 config = Key Down CurrentWindow
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_LEFT
 repeat = 0
 config = Key Left CurrentWindow
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_RIGHT
 repeat = 0
 config = Key Right CurrentWindow
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_PLAY
 config = Key Return CurrentWindow
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_STOP
 config = Key Escape CurrentWindow
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_OK
 config = Key Return CurrentWindow
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_FORWARD
 config = Key Return CurrentWindow
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_REWIND
 config = Key BackSpace CurrentWindow
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_NEXT
 config = Key Return CurrentWindow
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_AGAIN
 config = Key BackSpace CurrentWindow
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_BACK
 config = Key Escape CurrentWindow
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = More
 config = Key Menu CurrentWindow
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_1
 config = Key 1 CurrentWindow
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_2
 config = Key 2 CurrentWindow
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_3
 config = Key 3 CurrentWindow
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_4
 config = Key 4 CurrentWindow
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_5
 config = Key 5 CurrentWindow
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_6
 config = Key 6 CurrentWindow
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_7
 config = Key 7 CurrentWindow
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_8
 config = Key 8 CurrentWindow
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_9
 config = Key 9 CurrentWindow
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_0
 config = Key 0 CurrentWindow
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = Star
 config = Key KP_Multiply CurrentWindow
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = Hash
 config = Key numbersign CurrentWindow
 repeat = 0
end

begin
 remote = mceusb
 prog = irxevent
 button = KEY_ENTER
 config = Key KP_Enter CurrentWindow
 repeat = 0
end

#begin
# remote = mceusb
# prog = irxevent
# button = KEY_
# config = Key  CurrentWindow
# repeat = 0
#end
```[/INDENT]
[HR][/HR]
[SIZE=3]**7.** Configure IR mouse daemon lircmd:[/SIZE]
[INDENT][SIZE=1][http://www.mythtv.org/wiki/Lircmd](http://www.mythtv.org/wiki/Lircmd)
[Re: remote mouse via lircmd]("http://ubuntuforums.org/showthread.php?t=1329662&p=10730816#post10730816")[/SIZE][/INDENT]

[INDENT]**7a.** Add Device to your X11 configuration:

First you have to know that to use ANY mouse in x11, you have to add it to your xorg.conf.

Add "InputDevice" lines to your xorg.conf:

[HIGHLIGHT]sudo cp /etc/x11/xorg.conf /etc/x11/xorg.conf.old[/HIGHLIGHT]
[HIGHLIGHT]gksu geany /etc/x11/xorg.conf[/HIGHLIGHT]
```
Section "InputDevice"
         Identifier "Remote"
         Driver "mouse"
         Option "Protocol" "IntelliMouse"
         Option "SendCoreEvents"
         Option "Buttons" "5"
         Option "ZAxisMapping" "4 5"
EndSection
```

**My [HIGHLIGHT]/etc/x11/xorg.conf[/HIGHLIGHT] file:**
```
Section "Screen"
        Identifier      "Default Screen"
        DefaultDepth    24
EndSection

Section "Module"
        Load    "glx"
EndSection

Section "Device"
        Identifier      "Default Device"
        Driver  "nvidia"
        Option  "NoLogo"        "True"
EndSection

Section "InputDevice"
         Identifier "Remote"
         Driver "mouse"
         Option "Protocol" "IntelliMouse"
         Option "SendCoreEvents"
         Option "Buttons" "5"
         Option "ZAxisMapping" "4 5"
EndSection
```

**7b.** Load Driver on Startup:

Next you have to load the correct driver to make it work. Add to the file [HIGHLIGHT]/etc/modules[/HIGHLIGHT] the entry:

[HIGHLIGHT]uinput[/HIGHLIGHT]

[HIGHLIGHT]sudo cp /etc/modules /etc/modules.old[/HIGHLIGHT]
[HIGHLIGHT]gksu geany /etc/modules[/HIGHLIGHT]

**My [HIGHLIGHT]/etc/modules[/HIGHLIGHT] file:**
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
# Parameters can be specified after the module name.

loop
lp
rtc

# Generated by sensors-detect on Wed May 15 03:41:41 2013
# Chip drivers
coretemp
w83627ehf

uinput
```

Create a new file [HIGHLIGHT]/etc/udev/rules.d/55-uinput[/HIGHLIGHT] with one line:

[HIGHLIGHT]KERNEL=="uinput", MODE="0666"[/HIGHLIGHT]

[HIGHLIGHT]gksu geany /etc/udev/rules.d/55-uinput[/HIGHLIGHT]

**7c.** Edit your hardware.conf file:

Now you must tell lirc to start the mouse daemon and where the config file is. Edit your [HIGHLIGHT]/etc/lirc/hardware.conf[/HIGHLIGHT] to have these settings:

[HIGHLIGHT]START_LIRCMD="true"[/HIGHLIGHT]
[HIGHLIGHT]LIRCMD_CONF="/etc/lirc/lircmd.conf"[/HIGHLIGHT]

[HIGHLIGHT]sudo cp /etc/lirc/hardware.conf /etc/lirc/hardware.conf.old[/HIGHLIGHT]
[HIGHLIGHT]gksu geany /etc/lirc/hardware.conf[/HIGHLIGHT]

**My [HIGHLIGHT]lirc/hardware.conf[/HIGHLIGHT] file:**
```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Windows Media Center Transceivers/Remotes (all)"
REMOTE_MODULES="lirc_dev mceusb"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="mceusb/lircd.conf.mceusb"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

#Disable kernel support.
#Typically, lirc will disable in-kernel support for ir devices in order to
#handle them internally.  Set to false to prevent lirc from disabling this
#in-kernel support. 
#DISABLE_KERNEL_SUPPORT="true"

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"

# Default configuration files for your hardware if any
LIRCMD_CONF="/etc/lirc/lircmd.conf"

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD="true"
```

**7d.** Create [HIGHLIGHT]lircmd.conf[/HIGHLIGHT]

Create a new file [HIGHLIGHT]/etc/lirc/lircmd.conf[/HIGHLIGHT]. You have to tell lirc which buttons will move the cursor what direction. Use irw to determine your button names if you need. Also note the TOGGLE_ACTIVATE is the button you will push to turn on and off your mouse capabilities of your remote. You must push this button before the other buttons will command the cursor, and you must push it again for these buttons to have their regular usage.
[HIGHLIGHT]gksu geany /etc/lirc/lircmd.conf[/HIGHLIGHT]

**My [HIGHLIGHT]/etc/lirc/lircmd.conf[/HIGHLIGHT] file:**
```
#
# lircmd config file
# 
# CONFIGURED
#
# To find out how to get a proper configuration file please read:
# 
#	/usr/share/doc/lirc/README.Debian

PROTOCOL IntelliMouse
#PROTOCOL MouseSystems

# ACCELERATOR start max multiplier

ACCELERATOR 2 30 5

TOGGLE_ACTIVATE * KEY_CLEAR
MOVE_N * KEY_2
MOVE_NE * KEY_3
MOVE_E * KEY_6
MOVE_SE * KEY_9
MOVE_S * KEY_8
MOVE_SW * KEY_7
MOVE_W * KEY_4
MOVE_NW * KEY_1
MOVE_N * KEY_UP
MOVE_E * KEY_RIGHT
MOVE_S * KEY_DOWN
MOVE_W * KEY_LEFT
MOVE_IN * KEY_CHANNELUP
MOVE_OUT * KEY_CHANNELDOWN
BUTTON1_TOGGLE * KEY_5
BUTTON2_TOGGLE * Hash 
BUTTON3_TOGGLE * Star
BUTTON1_CLICK * KEY_OK
BUTTON1_CLICK * KEY_HOME
BUTTON3_CLICK * KEY_MUTE
# BUTTONx_CLICK, BUTTONx_UP, BUTTONx_DOWN are also possible
```

[INDENT][SIZE=1][COLOR="#5E2750"]Note: According to this configuration the **CLEAR** button (at the very bottom left of my remote) will be used to toggle LIRC Mouse Mode.[/COLOR][/SIZE][/INDENT]

**7e.** Edit your /etc/init.d/lirc file:

There is an issue with the init script in Ubuntu. There is no way to pass arguments to the lircmd daemon at start up. We need to start it with the --uinput flag. to do this you need to edit [HIGHLIGHT]/etc/init.d/lirc[/HIGHLIGHT]. Note: line 194 added [HIGHLIGHT] -- -- uinput[/HIGHLIGHT]

```
191                 if [ "$START_LIRCMD" = "true" ]; then
192                         [ -d "/var/run/lirc" ] || mkdir -p "/var/run/lirc"
193                         log_daemon_msg "Starting remote control mouse daemon : LIRCMD "
194                         start-stop-daemon --start --quiet --oknodo --exec /usr/sbin/lircmd -- -- uinput< /dev/null
195                         log_end_msg $?
196                 fi
```

[HIGHLIGHT]sudo cp /etc/init.d/lirc /etc/init.d/lirc.old[/HIGHLIGHT]
[HIGHLIGHT]gksu geany /etc/init.d/lirc[/HIGHLIGHT]

**My [HIGHLIGHT]/etc/init.d/lirc[/HIGHLIGHT] file:**
```
#! /bin/sh
### BEGIN INIT INFO
# Provides:          lirc
# Required-Start:    $remote_fs $syslog
# Required-Stop:     $remote_fs $syslog
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Starts LIRC daemon.
# Description:       LIRC is used to control different
#                    infrared receivers and transceivers.
### END INIT INFO

load_modules ()
{
	MODULES_MISSING=false

	log_daemon_msg "Loading LIRC modules"
	for mod in $*; do
		if [ $mod = "udev" ]; then
			log_end_msg 0
			log_success_msg "Restarted via udev, don't reload modules"
			break
		else
			modprobe $mod 2> /dev/null || MODULES_MISSING=true
		fi
	done
	log_end_msg $?

	if $MODULES_MISSING; then
		log_failure_msg "Unable to load LIRC kernel modules. Verify your"
		log_failure_msg "selected kernel modules in /etc/lirc/hardware.conf"
		START_LIRCMD=false
		START_LIRCD=false
	fi
}

build_remote_args ()
{
	REMOTE_ARGS="$*"

	#For remote only detection support, we need
	#both REMOTE_DEVICE and TRANSMITTER_DEVICE undefined
	if [ -z "$REMOTE_DEVICE" ] && [ -z "$TRANSMITTER_DEVICE" ] && [ -c $dev ]; then
		REMOTE_DEVICE="$dev"
	fi

	#If we have a REMOTE_DEVICE or REMOTE_DRIVER defined (either because no devices
	#were defined, OR if we explicitly did), then populate REMOTE_ARGS
	if [ ! -z "$REMOTE_DEVICE" ] || [ ! -z "$REMOTE_DRIVER" ]; then
		if [ -n "$REMOTE_DEVICE" ] && [ "$REMOTE_DEVICE" != "none" ]; then
			REMOTE_ARGS="--device=$REMOTE_DEVICE $REMOTE_ARGS"
		fi
		if [ -n "$REMOTE_DRIVER" ] && [ "$REMOTE_DRIVER" != "none" ]; then
			REMOTE_ARGS="--driver=$REMOTE_DRIVER $REMOTE_ARGS"
		fi

		#Now, if we ALSO have a transmitter defined, add some args
		#To make the first lircd listen up
		if [ ! -z "$TRANSMITTER_DEVICE" ] || [ ! -z "$TRANSMITTER_DRIVER" ]; then
			REMOTE_ARGS="$REMOTE_ARGS --listen"
		fi
		REMOTE_ARGS="--output=$REMOTE_SOCKET $REMOTE_ARGS"
	fi
	echo $REMOTE_ARGS
}

build_transmitter_args ()
{
	TRANSMITTER_ARGS="$*"

	#Transmitters must be explicitly be defined
	if [ ! -z "$TRANSMITTER_DEVICE" ] || [ ! -z "$TRANSMITTER_DRIVER" ]; then
		if [ -n "$TRANSMITTER_DEVICE" ] && [ "$TRANSMITTER_DEVICE" != "none" ]; then
			TRANSMITTER_ARGS="--device=$TRANSMITTER_DEVICE $TRANSMITTER_ARGS"
		fi
		if [ -n "$TRANSMITTER_DRIVER" ] && [ "$TRANSMITTER_DRIVER" != "none" ]; then
			TRANSMITTER_ARGS="--driver=$TRANSMITTER_DRIVER $TRANSMITTER_ARGS"
		fi

		#Now, if we ALSO have a remote defined, add some args
		#To make the second lircd connect
		if [ ! -z "$REMOTE_DEVICE" ] || [ ! -z "$REMOTE_DRIVER" ]; then
			TRANSMITTER_ARGS="$TRANSMITTER_ARGS --connect=localhost:8765 --pidfile=/var/run/lirc/lircd1.pid"
		fi
		TRANSMITTER_ARGS="--output=$TRANSMITTER_SOCKET $TRANSMITTER_ARGS"
	fi
	echo $TRANSMITTER_ARGS
}

in_kernel_support() {
	if [ -d /sys/class/rc ] && [ "$DISABLE_KERNEL_SUPPORT" = "true" ]; then
		for file in `find /sys/class/rc/*/ -name protocols`; do
			if [ "$1" = "disable" ]; then
				echo "lirc" > $file
			else
				echo "none" > $file
				for protocol in `cat $file`; do
					echo "+${protocol}" > $file
				done
			fi
		done
	fi
}
. /lib/lsb/init-functions

test -f /usr/sbin/lircd || exit 0
test -f /usr/sbin/lircmd || exit 0

START_LIRCMD=true
START_LIRCD=true
START_IREXEC=true
DISABLE_KERNEL_SUPPORT=true


if [ -f /etc/lirc/hardware.conf ];then
	. /etc/lirc/hardware.conf
fi

if [ ! -f /etc/lirc/lircd.conf ] || grep -q "^#UNCONFIGURED" /etc/lirc/lircd.conf; then
	if [ "$1" = "start" ]; then
		log_success_msg "No valid /etc/lirc/lircd.conf has been found."
		log_success_msg "Remote control support has been disabled."
		log_success_msg "Reconfigure LIRC or manually replace /etc/lirc/lircd.conf to enable."
	fi

	START_LIRCD=false
	START_LIRCMD=false
	START_IREXEC=false
fi

if [ ! -f /etc/lirc/lircmd.conf ] || grep -q "^#UNCONFIGURED" /etc/lirc/lircmd.conf; then
	START_LIRCMD=false
fi

if [ ! -f /etc/lirc/lircrc ] || grep -q "^#UNCONFIGURED" /etc/lirc/lircrc; then
	START_IREXEC=false
fi

#We need default socket locations
OLD_SOCKET="/dev/lircd"
if [ -z "$REMOTE_SOCKET" ]; then
	REMOTE_SOCKET="/var/run/lirc/lircd"
fi
if [ -z "$TRANSMITTER_SOCKET" ]; then
	TRANSMITTER_SOCKET="/var/run/lirc/lircd"
	#Now, if we ALSO have a remote defined,
	#change the default transmitter socket
	if [ ! -z "$REMOTE_DEVICE" ] || [ ! -z "$REMOTE_DRIVER" ]; then
		TRANSMITTER_SOCKET="${TRANSMITTER_SOCKET}1"
	fi
fi

case "$1" in
	start)
		if [ "$LOAD_MODULES" = "true" ] && [ "$START_LIRCD" = "true" ]; then
			load_modules $2 $REMOTE_MODULES $TRANSMITTER_MODULES $MODULES
			in_kernel_support "disable"
		fi

		if [ "$START_LIRCD" = "true" ]; then
			[ -d "/var/run/lirc" ] || mkdir -p "/var/run/lirc"
			log_daemon_msg "Starting remote control daemon(s) : LIRC "
			REMOTE_LIRCD_ARGS=`build_remote_args $REMOTE_LIRCD_ARGS`
			TRANSMITTER_LIRCD_ARGS=`build_transmitter_args $TRANSMITTER_LIRCD_ARGS`

			#if we have a remote defined, it is primary process
			if [ ! -z "$REMOTE_LIRCD_ARGS" ]; then
				start-stop-daemon --start --quiet --oknodo --exec /usr/sbin/lircd -- $REMOTE_LIRCD_ARGS < /dev/null
				log_end_msg $?
				if [ -S "$REMOTE_SOCKET" -a "$OLD_SOCKET" != "$REMOTE_SOCKET" ]; then
					rm -f $OLD_SOCKET && ln -s $REMOTE_SOCKET $OLD_SOCKET
				fi 

				#now if we additionally have a transmitter defined, it is secondary process
				if [ ! -z "$TRANSMITTER_LIRCD_ARGS" ]; then
					/usr/sbin/lircd $TRANSMITTER_LIRCD_ARGS < /dev/null
					if [ -S "$TRANSMITTER_SOCKET" ]; then
						rm -f ${OLD_SOCKET}1 && ln -s $TRANSMITTER_SOCKET ${OLD_SOCKET}1
					fi 
				fi
			elif [ ! -z "$TRANSMITTER_LIRCD_ARGS" ]; then
				start-stop-daemon --start --quiet --oknodo --exec /usr/sbin/lircd -- $TRANSMITTER_LIRCD_ARGS < /dev/null
				log_end_msg $?
				if [ -S "$TRANSMITTER_SOCKET" -a "$OLD_SOCKET" != "$TRANSMITTER_SOCKET" ]; then
					rm -f $OLD_SOCKET && ln -s $TRANSMITTER_SOCKET $OLD_SOCKET
				fi 
			else
				log_end_msg 1
			fi
		fi

		if [ "$START_LIRCMD" = "true" ]; then
			[ -d "/var/run/lirc" ] || mkdir -p "/var/run/lirc"
			log_daemon_msg "Starting remote control mouse daemon : LIRCMD "
			start-stop-daemon --start --quiet --oknodo --exec /usr/sbin/lircmd -- -- uinput < /dev/null
			log_end_msg $?
		fi

		if [ "$START_IREXEC" = "true" ]; then
			[ -d "/var/run/lirc" ] || mkdir -p "/var/run/lirc"
			log_daemon_msg "Starting execution daemon: irexec"
			start-stop-daemon --start --quiet --oknodo --exec /usr/bin/irexec -- -d /etc/lirc/lircrc < /dev/null
			log_end_msg $?
		fi
		;;
	stop)
		in_kernel_support "enable"
		if [ "$START_IREXEC" = "true" ]; then
			log_daemon_msg "Stopping execution daemon: irexec"
			start-stop-daemon --stop --quiet --exec /usr/bin/irexec
			log_end_msg $?
		fi

		if [ "$START_LIRCMD" = "true" ]; then
			log_daemon_msg "Stopping remote control mouse daemon: LIRCMD"
			start-stop-daemon --stop --quiet --exec /usr/sbin/lircmd
			log_end_msg $?
		fi

		if [ "$START_LIRCD" = "true" ]; then
			log_daemon_msg "Stopping remote control daemon(s): LIRC"
			start-stop-daemon --stop --quiet --exec /usr/sbin/lircd
			log_end_msg $?
			[ -h "$OLD_SOCKET" ] && rm -f $OLD_SOCKET
			[ -h "${OLD_SOCKET}1" ] && rm -f ${OLD_SOCKET}1
		fi
		;;
	reload|force-reload)
		if [ "$START_IREXEC" = "true" ]; then
			start-stop-daemon --stop --quiet --signal 1 --exec /usr/bin/irexec
		fi

		if [ "$START_LIRCD" = "true" ]; then
			start-stop-daemon --stop --quiet --signal 1 --exec /usr/sbin/lircd
		fi

		if [ "$START_LIRCMD" = "true" ]; then
			start-stop-daemon --stop --quiet --signal 1 --exec /usr/sbin/lircmd
		fi
		;;
	restart)
		$0 stop
		#passes parameter $2 which is possibly our udev paramater
		$0 start $2
		;;
	*)
		echo "Usage: /etc/init.d/lircd {start|stop|reload|restart|force-reload}"
	exit 1
esac

exit 0
```

[S]**7f.** Add lircmd --uinput to /etc/rc.local to run on startup:

[HIGHLIGHT]gksu geany /etc/rc.local[/HIGHLIGHT]

**My [HIGHLIGHT]/etc/rc.local[/HIGHLIGHT] file:**
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

lircmd --uinput

exit 0
```[/S]

**7f.** Create configuration files for lircmd and killall to /etc/sudoers.d/ to enable them to run from a script:
[INDENT][SIZE=1][http://luiseth.wordpress.com/2012/04/15/in-a-nutshell-add-permissions-with-configuration-files-in-etcsudoers-d/](http://luiseth.wordpress.com/2012/04/15/in-a-nutshell-add-permissions-with-configuration-files-in-etcsudoers-d/)
[http://ubuntuforums.org/showthread.php?t=1132821](http://ubuntuforums.org/showthread.php?t=1132821)
[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

[COLOR="#5E2750"]Note: Create the files using the following as a template;[/SIZE]
```
[SIZE=1]# Enable me to mount/umount simply
Host_Alias HOST = your_machine_name. You can get it by running cat /etc/hostname

Cmnd_Alias MOUNT    = /bin/mount,/bin/umount
Cmnd_Alias FILEPERM = /bin/chown

your_username HOST=(root) NOPASSWD:MOUNT,FILEPERM[/SIZE]
```
[SIZE=1]and enable them with variations of the following commands;
[HIGHLIGHT]$sudo chown root:root mount_conf
$sudo chmod 0440 mount_conf
$sudo mv mount_conf /etc/sudoers.d/[/HIGHLIGHT][/SIZE]
[SIZE=1]then check everything went fine, by running [HIGHLIGHT]sudo -l[/HIGHLIGHT][/SIZE]
```
[SIZE=1]$sudo -l
Matching Defaults entries for luis on this host:
 env_reset

User luis may run the following commands on this host:
 (ALL) ALL
 (root) NOPASSWD: /bin/mount, /bin/umount, (root) /bin/chown[/SIZE]
```[/COLOR][/INDENT]
 
**My [HIGHLIGHT]sudoers.d[/HIGHLIGHT] files:**
[HIGHLIGHT]geany killall_conf[/HIGHLIGHT]
```
# Enable me to run killall as user.

Cmnd_Alias KILLALL = /usr/bin/killall

richard htpc=(root) NOPASSWD:KILLALL
```
[HIGHLIGHT]geany lircmd_conf[/HIGHLIGHT]
```
# Enable me to run lircmd as user.

Cmnd_Alias LIRCMD = /usr/sbin/lircmd

richard htpc=(root) NOPASSWD:LIRCMD
```

[HIGHLIGHT]sudo chown root:root lircmd_conf
sudo chmod 0440 lircmd_conf
sudo mv lircmd_conf /etc/sudoers.d/[/HIGHLIGHT]
[HIGHLIGHT]sudo chown root:root killall_conf
sudo chmod 0440 killall_conf
sudo mv killall_conf /etc/sudoers.d/[/HIGHLIGHT]

[HIGHLIGHT]sudo -l[/HIGHLIGHT]
```
Matching 'Defaults' entries for richard on this host:
    env_reset, mail_badpass,
    secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin

User richard may run the following commands on this host:
    (ALL : ALL) ALL
    (root) NOPASSWD: /usr/bin/killall
    (root) NOPASSWD: /usr/sbin/lircmd
```

[COLOR="#dd4814"][SIZE=1]**WARNING: The first time I tried to do this, I created the configuration files as:**[/SIZE]
```
[SIZE=1]# Enable me to run killall as user.

Host_Alias HOST    = htpc

Cmnd_Alias KILLALL = /usr/bin/killall

richard HOST=(root) NOPASSWD:KILLALL[/SIZE]
```
```
[SIZE=1]# Enable me to run lircmd as user.

Host_Alias HOST   = htpc

Cmnd_Alias LIRCMD = /usr/sbin/lircmd

richard HOST=(root) NOPASSWD:LIRCMD[/SIZE]
```
[SIZE=1][B]This caused sudo to break, giving me an error report telling me that the command alias on line 3 of lircmd_conf
already existed. From that point on I was unable to get *root access to anything* on my system!
I was able to fix this by booting from an Ubuntu Live USB (or CD) and editing the files to remove the command alias
as shown in my example files.[/SIZE]

_Please be careful!!!_[/B][/INDENT][/COLOR]
[HR][/HR]
[SIZE=3]**8.** Reboot and try it out![/SIZE]

[INDENT][SIZE=5][COLOR="#dd4814"]Please let me know if any of this works for you and if you have any ideas about improving on it. ;)[/COLOR][/SIZE][/INDENT]
[HR][/HR]
[SIZE=3]**9.** Additional References:[/SIZE]

[SIZE=1][INDENT][http://lifehacker.com/5527752/control-your-desktop-pc-with-a-remote-using-lirc](http://lifehacker.com/5527752/control-your-desktop-pc-with-a-remote-using-lirc)
[http://sourceforge.net/projects/irexecosd/](http://sourceforge.net/projects/irexecosd/)
[http://askubuntu.com/questions/283984/what-is-the-shutdown-command-in-13-04](http://askubuntu.com/questions/283984/what-is-the-shutdown-command-in-13-04)[/INDENT][/SIZE]
[HR][/HR]
[ATTACH=CONFIG]243201[/ATTACH]

---

