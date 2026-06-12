---
title: "auto play for cds and dvds"
date: 2008-11-26
forum: Multimedia Software
---

### Post by yotama9 on 2008-11-26
Hi guys. 

I have a machine running Ubuntu Intrepid Ibex and I want to make it auto play CD's and DVD's when they are insrted to the DVD drives (I'm speaking of music CD's and video DVD's). I searched the internet for a guide but cuoldn't find one for ubuntu Intrepid and the one I found refer to options I don't have on my machine (normally installed) 

Also, when I mount my cowon D2 player the Ubuntu open image editor (forgot it's name, not gimp) and I want it to stop doing so. 

any help from you guys?

thanks. 

Yotam

---

### Post by mc4man on 2008-11-26
Open nautilus (or home folder) and in upper panel -> edit -> preferences -> media.

You'll see all the currently available choices.
If something you  want isn't there go 'open with other application' (or something to that effect, not using 8.10 atm.

If some app you want to use still isn't available or doesn't run right off of 'autorun' post back

(some apps will need a custom launch command for 'autorun'

---

### Post by yotama9 on 2008-11-28
I tried what you said and indid rhystembox open but it won't play the CD. 

Any idea? I think I shuold add a command line parameter but I don't know what. I don't mind changing an app to other player. 

Thanks.

Yotam

---

### Post by mc4man on 2008-11-29
As far as i know rhythmbox can't auto play cd's  upon insertion, it will open and then you'll have to manually start it.
The same can be said for most players. (in 8.04 and 8.10

Amarok and vlc can with  custom launch commands. In both cases you are limited to one drive, I've yet to find a command that will properly work with two drives. (for audio cd's in a auto start and run.

8.10 has made using custom launch commands 'easier' to set for the default (autorun) players by adding that drop down in file management -> media which includes a 'use a custom command'

( right click on Applications -> edit menus -> highlight preferences and enable 'file management' ( the same as the nautilus -> edit ,ect.

In 8.04 that option doesn't exist so a different method had to be used that while a little more work, ultimately is 'cleaner'. Either way can be used in 8.10

When you use a custom command in this 'manner' a userapp.desktop is created, for example

"userapp-vlc-J7Q7JU.desktop"

The problem is that the display name for all userapp.desktops is just the app name, in this case 'vlc". Userapp.desktops are created in many ways, right click 'open with', right click -> properties -> 'open with', using custom commands.
 
You can quickly end up with alot of userapp.desktops for one app and you won't be able to tell them apart.
The solution is to edit the userapp.desktops display name or to use the 8.04 method (copy app's .desktops with a name change

Anyway if you only want to set vlc or amarok to autoplay it won't be a big issue or you can deal with it later

For vlc 
Because vlc is registered as a cd audio player (and doesn't work right) do this after the below but before trying out.

Go into home folder (show hidden files) open .local/share and delete the 'vlc' folder. ( apps tend to break in 8.10 for no good reason. deleting their config files usually solves.

In the media drop down for cd audio choose 'use another ...' -> 'use a custom command' (adjust red to match your intended drive
```
vlc cdda:///dev/scd[COLOR="Red"]0[/COLOR]
```

Click 'add' and exit out. Your new choice in file management -> media will just say 'vlc' 
Normally it should now be set, but 8.10 can be a little thick so you'll probably need to restart x first or just reboot.

For amarok
Amarok needs to be called from a script, using the command directly can cause problems.

See here and just follow the instr. for creating the script and making it executable, the rest you can ignore. (make sure you put the script created in your home folder

[http://ubuntuforums.org/showthread.php?p=5459412#post5459412](http://ubuntuforums.org/showthread.php?p=5459412#post5459412)

Then in file management -> media, blah, blah use this as a custom command

```
./play1
```

Your new choice will be called play1, again a restart will probably be needed


Edit; most dvd players will work fine with their default launch commands, if not just workout the command in a terminal and then use as above.
Three that I know need specific commands for auto run are gmplayer, xine-ui and obviously the dvdnav and or regular cli version of mplayer

---

### Post by yotama9 on 2008-11-29
It works but it doesn't work ok. 

It take my machine some time to load the cd (about 30 seconds) and then it skeep the first 10 seconds. (VLC) 

when I use the same command from command line it works flawlessly

Yotam

---

### Post by mc4man on 2008-11-29
> It works but it doesn't work ok

Overall I find 8.10 to be very inconsistent, that's why I'm sticking with 8.04.

I have 8.10 on a 2nd box and have seen things break for no good reason.
As far as vlc and cd's.

If I set it to autorun the normal vlc (VLC media player) nothing happens.

If I right click on the 'audio disk' icon -> open with VLC media player it opens vlc and starts playing except if there are 10 or more tracks, then it starts on track 10.

Using the custom command applied thru file management works here with a slight delay, when it works at all. Tends to stop altogether ala using Vlc media player as the default player

This is the best way I've found for 8.10

If you do it like amarok then at least here it keeps working and there is no delay. 
Note that vlc won't be started till the disc is 'mounted' in .gvfs, if you have a delay there due to your drives response nothing to do about that.

Create a text file in home named play2 and paste this in (adjust red to intended drive

```
#!/bin/bash
vlc cdda:///dev/scd[COLOR="Red"]0[/COLOR]
```

In terminal go 
```
chmod +x play2
```

Now in file management -> media ect. and add ./play2  in the custom command box.


Side note

If you want to clean up useless entries in the default player list and by extension in the r.click on icon  then you can carefully edit the proper line in mimeapps.list.

```
gedit ~/.local/share/applications/mimeapps.list
```
Or just browse there
Ex. 
after fooling around with both a copy .desktop method and using the custom command thru ...media the line looks like this

> x-content/audio-cdda=userapp-play2-IXAHLU.desktop;vlc-cd.desktop;amarok-cd.desktop;totem-xine.desktop;userapp-play-0X3TLU.desktop;rhythmbox.desktop;vlc.desktop;brasero-copy-medium.desktop;

(there is no space in brasero - it just keeps getting posted that way - weird

Vlc media player is worthless as is totem-xine and I don't use rhythmbox at all. Amarok works both ways well so I'll keep the copied .desktop. Vlc works best from the userapp and I want to keep brasero as an option.

> x-content/audio-cdda=userapp-play2-IXAHLU.desktop;amarok-cd.desktop;brasero-copy-medium.desktop;

Just don't leave spaces between entries and end with a ;


Or just use your player of choice with no autoplay and start manually.

---

### Post by ziri on 2008-12-10
> 
In the media drop down for cd audio choose 'use another ...' -> 'use a custom command' (adjust red to match your intended drive
```
vlc cdda:///dev/scd[COLOR="Red"]0[/COLOR]
```


If you want to autoplay CD by VLC in whatever drive, you can use the script as described above (for amarok) and modify it slightly. Here it is:

```

#!/bin/bash
CD=/dev/`echo $1|sed -e "s/.*\(scd[0-9]\).*/\\1/"`
vlc cdda://$CD

```

This assumes that your CD drives are called scd0, scd1, etc.

---

### Post by mc4man on 2008-12-10
Thanks ziri, I always figured it could be scripted for 2 drives.
(what I wouldn't give to know how to write scripts other than the kindergarden variety.

I use 8.04 and only use amarok, not vlc. Adjusting the script to below works perfectly with either drive

#!/bin/bash
CD=/dev/`echo $1|sed -e "s/.*\(scd[0-9]\).*/\\1/"`
amarok --cdplay //$CD 

So to set amarok to autoplay on multiple drives in 8.04 (same idea on 8.10 

[http://ubuntuforums.org/showthread.php?p=5459412#post5459412](http://ubuntuforums.org/showthread.php?p=5459412#post5459412)

Edit tested on fresh install of hardy - needed to reboot before script worked with  drives

---

