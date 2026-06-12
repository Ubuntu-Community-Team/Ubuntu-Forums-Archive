---
title: "HOWTO Add a working 'Enqueue in VLC' option to your Nautilus context menu"
date: 2009-03-19
forum: Multimedia Software
---

### Post by danboid on 2009-03-19
PRE(R)AMBLE

I was not a fan on the fact that if I wanted to play multiple flv files under GNU/Linux I found myself having to start vlc, open a playlist window, locate my desired files, drag them into the vlc playlist window and then push play; what a load of faff that is when under everybodys' fave monopoly OS I could just right click on a bunch of files then choose 'Open with VLC' and it would behave as expected instead of opening x instances of vlc for x number of files. 

I had a search on the net but failed to find a way to get vlc to play nicely with nautilus. I got it working as I wanted and so I wanted to share my tweak with as many free software users as possible and this seemed as good a place as any. I would really love to see vlc replace totem as the standard media player of Ubuntu but now that vlc has switched to using QT4 I think the chances of this happening are slim  indeed.

INSTRUCTIONS

Install the package nautilus-actions

from a terminal run nautilus-actions-config

Click 'Add'

Under the 'Menu Item and action tab' set the values as such:

Label: Enqueue in VLC

Icon: gtk-justify-right (or whatever you like best)

Path: vlc

Parameters: %M

Then under the 'Conditions' tab set the fields as follows:

filenames: *.ogg; *.mp3; *.flv; *.avi; *.mp4; *.mov; *.wav; *.flac

Untick 'Match case' if it isn't already deselected

Choose 'Only files' option and tick 'Appears if selection has multiple files or folders'

Choose OK, close nautilus-actions-config and restart GNOME (by logging out and back in or restarting). Now when you right click on one or more media files under GNOME you should get a 'Enqueue in VLC' option in the top level of you nautilus context menu- that is just above where 'Send to..' normally is and not under the 'Open with..' context sub-menu, as you may expect.

After applying this tweak I'm much more comfortable and efficient with playing media under GNOME- hope you enjoy it too!

---

### Post by mc4man on 2009-03-19
Because in the version I'm using now in 8.10 (0.9.8a) the "enqueue files in playlist when in one instance mode" doesn't work I set up a nautilus action slightly different

For the command i use this which will queue the files but not stop playing the current trak. (using just vlc as a command will queue the selected file and also start playing it, bypassing previously queued/current playing tracks.

```
vlc --playlist-enqueue
```

or even as a d. left click file asoiaction, enqueued in order of clicking without distirbing current track, file, ect.

---

### Post by danboid on 2009-03-20
Hi mc4man!

I'm running Intrepid with the standard intrepid vlc version here (0.9.4) and I couldn't get your --playlist-enqueue option to work so maybe that switch has only been introduced after 0.9.4? Sounds great if it does work as you say it does.

Using %M instead of --playlist-enqueue doesn't stop your current tracks/ videos, it will start a new vlc session and playlist leaving any existing ones to play on.

I did however amend my instructions to include the fact that you need to restart GNOME after installing/ setting up nautilus-actions before the option appears in the menu.

---

### Post by mc4man on 2009-03-20
It should work in 0.9.4

What you do need to do is go Tools -> preferences and ck. the box for "Allow only one instance"

There's a box for "Enqueue files..." that doesn't work right in any 0.9.x or 1.0 ver.


Other uses of the vlc --playlist-enqueue can be  for d.  left clicking on any particular file ext.

Just right click on any file with .xxx ext. -> properties -> open with -> add -> use a custom command. Then use the above comm.

Then d. left clicking on any file with that ext. will queue in vlc. (if vlc isn't open then it will open vlc, load and play the file, any add. are queued.


As far as the d.left click on a file type you only need to create one custom association, then assign it to any other ext you wish. What's confusing with that is by default it will only show up as "vlc" and it's possible to have several.

What I like to do is give it a distinctive name so if i want to use with another ext. it's easy to pick. See screen, easy to do once you get the idea

---

### Post by jminker on 2009-03-21
> **mc4man said:**
> 
What I like to do is give it a distinctive name so if i want to use with another ext. it's easy to pick. See screen, easy to do once you get the idea

Hello mc4man,

I now have my audio files to open as you've detailed, but how do you give it the distinctive name with the VLC icon?

Thanks, Jim

---

### Post by mc4man on 2009-03-21
Whenever you use a custom command from the r. click a 'userapp.desktop' is created. The actual name is individualized, the display name will be the app or command in lowercase.
The actual name follows this format - Ex. a custom comm. for vlc (the XXXXXX is different every time
userapp-vlc-XXXXXX.desktop

For what you wish to do the actual name isn't too important.

Navigate to home folder -> .local/share/applications
Inside look for a blue diamond named vlc, right click on -> properties, that's where you can change the display name and icon.

If you have more than one blue diamond named vlc, check them all to find the one with the vlc --playlist-enqueue command. (when a userapp.desktop is created on a file a %f is added to the command, leave as is.

To give a vlc icon, click on the icon box and browse to the icon you wish in the pop up.
I don't have the repo vlc installed but I'd think your best bet would be to browse to file system -> /usr/share/pixmaps

Vlc icons would also be in /usr/share/vlc, but the one in pixmaps is better suited (48/48 .png

Note that all vlc 0.9.x and 1.0 versions are broken in varing ways, if vlc ever stops responding 1st 2 things to ck.
Open system monitor -> processes and if vlc is there and sleeping then r. click on and 'kill process'
Open vlc from a terminal with
```
vlc --reset-config
```

The 'allow only one instance' works properly in 0.9.x, may not in some 1.0 rev.'s

---

### Post by jminker on 2009-03-21
mc4man,

Thank you very much! Quick and easy to follow.

I would add a Thankyou, but it seems that option has been disabled lately.

Jim

---

### Post by craptree on 2010-03-06
The problem with the current method is that using the "only allow one instance" option in VLC stops you from loading more then one vlc when you need to! 

If this is an issue (as it was for me) a better option is to allow vlc to allow more then one instance (untick the only allow one instance) box, and then create a open with custom from the right click menu and add the following command

```
vlc --started-from-file --playlist-enqueue
```

This adds files to the current running instance, even if that instance doesn't have one instance mode enabled. You will also still be able to open new instances with the standard open in vlc option which will still be there!

Riz

---

### Post by LintonHanes on 2010-03-17
sweet, good looking out thank you

---

### Post by gilbert wham on 2010-07-03
Hm. I'm having problems getting this to work in 10.04. I've just sacked Windows off completely after years of vacillating, because I like being able to right-click a folder & choose 'enqueue in Winamp'.
This is what I've configured it like:
[IMG]http://yfrog.com/75screenshotfcyp[/IMG]

[IMG]http://yfrog.com/emscreenshot1chp[/IMG]

[IMG]http://yfrog.com/0iscreenshot2rep[/IMG]

I hope  I'm just doing something slightly wrong & someone can help me fix it. I hate playlists with a passion. I already have a way of organising my music; it's called a 'filesystem, dammit. Is there really *not one* Linux music player that does this off the bat?

---

### Post by gilbert wham on 2010-07-03
Gah! Screenshots here, as I am an idiot...

---

### Post by mc4man on 2010-07-03
@gilbert wham
your command is wrong - screen 2
use this instead

```
vlc --started-from-file --playlist-enqueue
```

Note that  vlc may not enqueue a directory of files correctly in the 1.0.X version as far as the order - has been fixed in 1.1

---

### Post by Airris on 2011-01-23
Let me note i was unable to get this to work properly on the filename conditions unless there were no spaces between the semicolons. So if anyone's having trouble make sure they do :

*.ogg;*.mp3;*.flv;*.avi;*.mp4;*.mov;*.wav;*.flac

Thanks though this is awesome :D

---

### Post by zydar on 2011-03-08
```
#! /bin/sh
# A small script to enqueue media files in vlc
# Edit by zydar
# According to the original script (totem) of: Thura and Deepak John


is_player_present=$(ps -e | grep vlc)

walk()
{
    for file in "$1"/*
    do
        if [ -d "$file" ];then
            walk "$file"
        else
            if [ -n "$is_player_present" ];then
                vlc --started-from-file --playlist-enqueue "$file"
            else
                vlc "$file"
            fi
        fi
    done
}

if [ -d "$arg" ];then
    walk "$arg"
else
    if [ -n "$is_player_present" ];then
        vlc --started-from-file --playlist-enqueue "$@"
    else
        vlc "$@"
    fi
fi


```
 According to the original script (totem) of: Thura and Deepak John

---

### Post by LewRockwellFAN on 2011-04-21
Anyone not getting perfect results yet, see posts 8 through 11 in
[http://ubuntuforums.org/showthread.php?t=850053](http://ubuntuforums.org/showthread.php?t=850053)
Method was posted almost 3 years ago and it works great for me.

---

