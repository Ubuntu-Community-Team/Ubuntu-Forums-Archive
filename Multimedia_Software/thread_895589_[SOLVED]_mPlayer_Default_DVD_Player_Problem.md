---
title: "[SOLVED] mPlayer Default DVD Player Problem"
date: 2008-08-20
forum: Multimedia Software
---

### Post by Prosis on 2008-08-20
Hello Everyone

I've just set mPlayer as my default DVD movie player so that when I insert a DVD, it starts and plays the movie.  But what happens now is that, mPlayer starts and I get a "Seek Failed" error.  So I have to manually open the DVD in mPlayer.

Now before Hardy, I used to go to System -> Preferences -> Removable Media (or something along those lines) and for DVD reading "mplayer dvd:// %m".  But that doesn't exist anymore in Hardy.

So how can I make it so, mPlayer opens and reads the movie?

Thank you! :)

---

### Post by Prosis on 2008-08-20
Come on no one in French or English forums can help me? ](*,)

---

### Post by mc4man on 2008-08-20
If you have just 1 dvd drive (or 1 you'll use for dvd playback ), then it's relatively simple to set mplayer (gui ver. or smplayer) as default and have it open properly.

Haven't found a launch command that will direct it to device that 'called' it.

So you'll need to set default device in preferences or mplayer .config to match drive you'll use (ie. /dev/dvd, /dev/dvd1 , ect.

If you could get a proper launch comm. or maybe a script that had mplayer ck. /dev/dvd and if no dvd is found then ck. /dev/dvd1 it would be easy to tie the script to 'autoplay ' on dvd insertion. ( and work properly with 2 drives

---

### Post by Prosis on 2008-08-20
Weird it's already set that way...:(

---

### Post by mc4man on 2008-08-20
How did you set it (mplayer) up to be default dvd player?


Edit: If you want there is an quick,safe and easily reverted way to set mplayer(gui ver.) to autoplay dvds upon insertion. Should only take a min. or two. Let me know

---

### Post by Prosis on 2008-08-20
Oh great!  Let me know ! :)

What I did is that I opened  /etc/gnome/defaults.list in gEdit, went to the line starting by ```
x-content/video-dvd
``` and replaced totem.desktop by mplayer.desktop

That's the only way I found.

---

### Post by mc4man on 2008-08-21
> and replaced totem.desktop by mplayer.desktop
I actually prefer to use defaults.list to add vlc which works fine from there and even better by changing the default launch comm to vlc %f.

[http://ubuntuforums.org/showthread.php?p=4986640#post4986640](http://ubuntuforums.org/showthread.php?p=4986640#post4986640)

Otherwise i like to either make copies of .desktops and use mimeapps.list or the quick method.  You can also use the launch commands of apps that are automatically added to the default choice menu to run either other apps or scripts. 
The main thing is to match the launch command to how your using the app

Also note - any app set as a default choice will also become available in the r. click 'open with' menu on the appropriate icon (dvd or cd, ect.

Some Ex.
autoplay audio cd with amarok - copy .desktop with custom Exec=
banshee-1 - atm used to run script to autostart and autoconnect amarok with ipod, am going to use for a cd rip script
gxine - used to run script to run vobcopy to rip dvds from any drive or two at once
gmplayer - copy .desktop with custom Exec= 
cd audio extractor - launch command changed to ruby ripper cli
smplayer - copy.desktop
mplayer dvdnav version - copy.desktop with custom command as Exec=
gthumb - copy.desktop with custom Exec=
vlc 0.9.x - copy .desktop
xine - copy.desktop with custom Exec=
totem-xine - copy.desktop
etc., etc.



**note; holding down shift button when inserting media will bring up a list of available choices, very handy**

**copy .desktop method**

Ex. of mplayer (gmplayer) 
theory holds true for other apps, (except kde apps, you have to look elsewhhere to find the .desktop), for media other than dvd use a **different x-content line** , for lines that are available to use look in /etc/gnome/defaults.list

first browse to home dir. -> .local -> share and see if there is a folder named applications and if so,  is there a file - mimeapps.list inside. If so good, **if not** you can create the **folder** if needed
```
mkdir ~/.local/share/applications 
``` 

then run

```
cp /usr/share/applications/mplayer.desktop ~/.local/share/applications/mplayer-dvd.desktop
```

Then run
 ```
gedit ~/.local/share/applications/mimeapps.list
```
 If it's **empty** then paste this in 

```
[Added Associations]
   x-content/video-dvd=mplayer-dvd.desktop;totem.desktop;

```
If it's **not **then paste just this line in
```
x-content/video-dvd=mplayer-dvd.desktop;totem.desktop;

```
if the **line exists** then just add
```
mplayer-dvd.desktop;
```

Be careful to keep formatting - no space between entries and end with a ;

then
 ```
gedit ~/.local/share/applications/mplayer-dvd.desktop

```
find the line - Exec=gmplayer %F and change to Exec=gmplayer dvd://
find the line - Name=MPlayer Movie Player and change to Name=MPlayer1 Movie Player

For comparison -  setting smplayer as default

Smplayer needs and uses a default dvd device like gmplayer but when set as the default player will work even if you have 2 drives
So with smplayer the default command is fine.

assuming the applications folder and mimeapps.list exist and the x-content/video-dvd= line all exist

Just 

```
cp /usr/share/applications/smplayer.desktop ~/.local/share/applications/smplayer.desktop
```

Then 

```
gedit ~/.local/share/applications/mimeapps.list
```

and add to end of the x-content/video-dvd= line 

```
smplayer.desktop;
```

Then choose smplayer in preferences -> media -> dvd video

**Very quick method for some apps**

If there is an existing default choice for default 'anything' (all categories) that you don't want to use as a default then you can try this

Ex.
Want to have audio cd insertion open grip

Set cd audio extractor as default (preferences -> file management -> media or places -> home folder -> edit -> preferences -> media

r. click aplications -> edit menus -> sound & video, on right side r. click on cd audio extractor -> properties. 

Change the launch command from sound-juicer to grip.

Now when inserting a audio cd grip will open

You can find the launch command of app your changing to from edit menus - > properties of the app, or gedit it's .desktop (gedit /usr/share/applications/[COLOR="Red"]appname[/COLOR].desktop

In some cases you can add additional parameters to launch command ( see <app> --help  or <app> --longhelp


To use sound-juicer just make a desktop launcher pointing to it (/usr/bin/sound-juicer

Above methods can be used for all apps (the quick may or may not work with kde apps, some times using a script as a launch command is only way for proper use.

Ex. for xine-ui (same as mplayer
[http://ubuntuforums.org/showthread.php?t=914043](http://ubuntuforums.org/showthread.php?t=914043)

on using scripts, ect.

[http://ubuntuforums.org/showthread.php?p=5562637#post5562637](http://ubuntuforums.org/showthread.php?p=5562637#post5562637)
related, amarok and ipod
[http://ubuntuforums.org/showthread.php?p=6092069#post6092069](http://ubuntuforums.org/showthread.php?p=6092069#post6092069)

on using scripts, ect.
[http://ubuntuforums.org/showthread.php?p=5456622#post5456622](http://ubuntuforums.org/showthread.php?p=5456622#post5456622)


setting amarok as default audio cd player ( 2 methods
[http://ubuntuforums.org/showthread.php?p=5459412#post5459412](http://ubuntuforums.org/showthread.php?p=5459412#post5459412)

an ex. of mimeapps - to see formatting - don't copy!screen1
how extensive the .list can get - screen 2

you can also create **custom** file associations with custom names to create more possibilities - screen 3 for ex. (blue diamonds


Edit 
to add totem-xine as a default choice while keeping totem-gstreamer as default totem player simply add this to the end of the 'x-content/video-dvd=' line

```
totem-xine.desktop;
```


Non traditional uses of auto run events

run script when flash drive is inserted

[http://ubuntuforums.org/showthread.php?p=6215968#post6215968](http://ubuntuforums.org/showthread.php?p=6215968#post6215968)

set rubyripper to autorip in background

[http://ubuntuforums.org/showthread.php?p=5708646#post5708646](http://ubuntuforums.org/showthread.php?p=5708646#post5708646)

Auto rip dvds with vobcopy with 1 or more drives

[http://ubuntuforums.org/showthread.php?p=5883353#post5883353](http://ubuntuforums.org/showthread.php?p=5883353#post5883353)

media cards

[http://ubuntuforums.org/showthread.php?p=5862576#post5862576](http://ubuntuforums.org/showthread.php?p=5862576#post5862576)

---

### Post by Prosis on 2008-08-21
Wow thanks

I changed a bit your way of doing it but could have never done it without you.

What I did is create a copy of mplayer.desktop named mplayerDVD.desktop

In mplayerDVD.desktop I changed the name (so I can tell which is which) and changed the command from gmplayer %F to gmplayer dvd:// 

Then I set DVD in defaults.list to mplayerDVD.desktop leaving the others as they were.

All works well now!  Thank you! :)

---

### Post by llawwehttam on 2009-10-13
Woah there is a much easier way. Go to your file browser and go to edit>preferences>Media and edit what you want.

---

### Post by mc4man on 2009-10-13
> Go to your file browser and go to edit>preferences>Media a........

did you happen to notice the date of this thread, about 14 months ago.

Mainly specific to hardy where is was/is no 'use a custom command', nor were several apps registered  as players for certain mimetypes.

Still though,  for some things, even on karmic, I still prefer to use copies of .desktops rather than userapp.desktops for some specific app launchers. ( though most normal things can be done from file management

---

