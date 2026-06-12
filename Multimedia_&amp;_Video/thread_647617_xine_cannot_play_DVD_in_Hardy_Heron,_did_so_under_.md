---
title: "xine cannot play DVD in Hardy Heron, did so under Gutsy Gibbon"
date: 2007-12-22
forum: Multimedia &amp; Video
---

### Post by Robertjm on 2007-12-22
xine 0.99.6 CVS
Ubuntu Hardy Heron Alpha1 w/all available patches installed.

I launch xine from the Applications/Sound & Video menu with a DVD alredy in the tray (there's an icon on my desktop so the system obviously knows its there.

When I click on the DVD button on the menu control an error message pops up:

[COLOR="Blue"]-xine engine error-
There is no input plugin available to handle 'dvd:/".
Maybe MRL syntax is wrong or file/stream source doesn't exist.[/COLOR]

When clicking on "More" I get additional error msgs:
[COLOR="Blue"]
The source can't be read.
Maybe you don't have enough rights for this, or source doesn't
contain  data (e.g: no disk in drive). (/dev/cdrom0)[/COLOR]

Additonally, a window pops up with three tabs (messages, plugin and trace)

Trace has nothing exciting, just two line referring to 2D_Tex and nothing that looks like an error.

Plugin refers to a whole bunch of plugins being found, but no references to plugs not found

The messages screen has seven entries. The third one says:
[COLOR="Blue"]xine: cannot find input plugin for MRL [DVD:/]
[COLOR="Black"]followed by:[/COLOR]
xine: input plugin cannot open MRL [DVD:/][/COLOR]

What's interesting is that if I use Nautilus to explore the DVD, and go to the video folder I can right click on any of the video files and view them through xine just fine.

Already installed libDVDCSS2 for viewing commercial DVDs (editorial note: I did NOT say copying commerical DVDs, just viewing them!!)

This all worked fine under Gutsy Gibbon (except for jittery play which Anita already made suggestions about).

I have a lone CD/DVD writer in the system. The fstab line say:
[COLOR="Blue"]/dev/hdb        /media/cdrom0   auto   rw,user,noauto,exec 0       0[/COLOR]

I've spent several days searching the web for suggestions, most of which revolve around making sure libcss2 is installed and reinstalling xine; both of which I've already done. Still nothing.

When I did the upgrade from Gutsy to Hardy A1 I did a clean install (including reformatting my partitions), except for keeping my /home folder intact.

If I try and use mplayer instead I get an error msg:
[COLOR="Blue"]No Stream found to handle url dvd://1[/COLOR]

Anyone have any other ideas?

Robert

---

### Post by employeeno5 on 2008-04-06
I'm having a similar issue and am getting similar error messages. All of my searching has just led to articles telling you install the packages for xine and libdvdcss2 and all the other normal stuff I already know about getting dvd play back in ubuntu.

My xine error messages are similar to yours. Totem's pop-up error message says that I don't have libdvdcss installed (when I certainly do and have reinstalled several times.

VLC either just crashes or sits idle.

Here are my terminal outputs for my video players when attempting play a commercial dvd with menus:

VLC
------------

```
[00000314] cdda access error: could not read block 001
[00000314] cdda access error: cannot read sector 001
[00000314] cdda access error could not read block 002
[00000314] cdda access error cannot read sector 002
```
etc... those same two messages just keep compiling forever going a number higher each time.


Totem
----------------

```
libdvdnav: Using dvdnav version 1.1.11.1 from http://xine.sf.net
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Attempting to use device /dev/scd0 mounted on /media/cdrom0 for CSS authentication
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/broderick/.dvdnav/.map'
libdvdread: Invalid main menu IFO (VIDEO_TS.IFO).
libdvdnav: vm: faild to read VIDEO_TS.IFO
```

Gxine
-----------------
```
bind: No such file or directory
warning: configuration item media.audio_cd.cddb_cachedir points to a non-existent location /home/broderick/.xine/cddbcache
warning: configuration item media.capture.save_dir points to a non-existent location 
warning: configuration item media.dvd.raw_device points to a non-existent location /dev/rdvd
warning: configuration item media.video4linux.radio_device points to a non-existent location /dev/radio0
warning: configuration item subtitles.separate.font_freetype points to a non-existent location 
lirc: cannot initialise - disabling remote control
lirc: maybe lircd isn't running or you can't connect to the socket?
libdvdnav: Using dvdnav version 1.1.11.1 from http://xine.sf.net
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: YTUMAMA_TAMBIEN_UNRATED
libdvdnav: DVD Serial Number: 2D159641
libdvdnav: DVD Title (Alternative): YTUMAMA_TAMBIEN_UNRATED
libdvdnav: Unable to find map file '/home/broderick/.dvdnav/YTUMAMA_TAMBIEN_UNRATED.map'
libdvdread: Invalid main menu IFO (VIDEO_TS.IFO).
libdvdnav: vm: faild to read VIDEO_TS.IFO
libdvdnav: Using dvdnav version 1.1.11.1 from http://xine.sf.net
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: YTUMAMA_TAMBIEN_UNRATED
libdvdnav: DVD Serial Number: 2D159641
libdvdnav: DVD Title (Alternative): YTUMAMA_TAMBIEN_UNRATED
libdvdnav: Unable to find map file '/home/broderick/.dvdnav/YTUMAMA_TAMBIEN_UNRATED.map'
libdvdread: Invalid main menu IFO (VIDEO_TS.IFO).
libdvdnav: vm: faild to read VIDEO_TS.IFO
xine-lib: error: Read error from::  /dev/dvd
xine-lib: error: The xine engine failed to start.: No input plugin was found.
Maybe the file does not exist or cannot be accessed, or there is an error in the URL.
```

---

### Post by classem2003 on 2008-04-23
Hello, I think the main reason is because it looks for /dev/dvd and it is not
longer present, at least in the version I installed, amd-64. What appears is
/dev/dvd1.

One quick fixed is  symlink /dev/dvd1 to /dev/dvd. To do this code:

cd /dev
sudo ln -s dvd1 dvd


This should fixed the problem, provided that you have libdvdcss2 installed.

---

### Post by cojoco on 2008-04-26
This fixed the problem for me, too, playing DVD in Kaffeine.

The RGBs are a bit mixed up, though, maybe I'll start another thread ... ?

---

### Post by CyDharttha on 2008-05-04
The symlink solution fixed it for me, too. Why is this happening? Will the symlink stay put after a reboot? Anything else I can do to make this problem more transparent for other users?

---

### Post by ScarySquirrel on 2008-05-04
As self-appointed Advocate for the Social Nooblet Radical Party (SNRP, pronounced "snorp"), I second CyDharttha's request for elaboration.  
     "Just compile it with a symbolic link" is about as opaque to the average Nooblet as "just replace the radiator with a metal manifold" sounds to someone not familiar with car repair.

---

### Post by classem2003 on 2008-05-08
> **CyDharttha said:**
> The symlink solution fixed it for me, too. Why is this happening? Will the symlink stay put after a reboot? Anything else I can do to make this problem more transparent for other users?

The thing is I am not an expert. What I know is that people in the ubuntu team decided not put the device dvd in the folder /dev. This is the device
where many applications look for the dvd's by default. The new location for the dvd's is /dev/dvd1. So, we have two options:

1) To indicate to the application where to look for the dvd's (/dev/dvd1 in this case), this can be done through "settings" in the respective application (xine, gxine, mplayer, etc..). I am to lazy to do this kind of things and I do not know how to find the settings dialog or config. files of this programs.

2) Try to mimic /dev/dvd1 and makes it to appear /dev/dvd. So, you "link" /dev/dvd1 to /dev/dvd.  "ln" is for link and -s is to indicate that it is a symbolic association, not a true device. That is why we use:

sudo ln -s /dev/dvd1 /dev/dvd

We are not compiling anything at all.


The other issue is that the change is temporal ("a quick fix"). To make it permanent you need to modify some file to indicate that this link should be created at the beginning when you boot up your computer.

One file can be  "/etc/rc.local". In order to do this you code in a terminal:

[FONT="Courier New"]sudo gedit /etc/rc.local[/FONT]

copy and paste the following line at the end of  the file you just opened, before the line " exit 0".

ln -s /dev/dvd1 /dev/dvd

and save the changes. Next time you boot up your computer the link will be created and every should be all right.

---

### Post by jurgen32 on 2008-05-19
Very good solution!!
This did it for me.
I am really fond of Kubuntu and I often recommand it to others.
But What if a newbee is experience this kind of problems...
I believe that this kind of problems should not apear.
But hey, who am I to complain[-X

Thank's for the solution.

Jurgen

---

### Post by Chuckels550 on 2008-05-21
This solution worked for me, too.  However, it only solved the movie dvd part of the problem.  My DVDRW drive now only plays movies.  It won't play audio CDs, for instance.

---

### Post by jurgen32 on 2008-05-24
Just a wild gues.
If you have this error:
[COLOR="Red"][I]-xine engine error-
There is no input plugin available to handle 'dvd:/".
Maybe MRL syntax is wrong or file/stream source doesn't exist.[/I][/COLOR]
with your homemade dvd's try to play a original dvd.
My experience with homemade dvd's was that I had to burn the *[COLOR="Red"]video_ts & audio_ts[/COLOR]* files not as a data-dvd project but as a video-dvd project.
If you burn it in K3B as a video-dvd project (more actions-new video-dvd project) a little file (few Kb.) is tacked along. 
This little file tells the player that it is a video-dvd.
Dolphin is capable to mount a data-dvd and browse it but a mediaplayer doesn't. 
At home we've got a stand alone dvd-player which plays a dvd, burned as a data-dvd, but on my computer this is a problem. 
I always try my homemade dvd's on the stand alone player and they always played fine... 
So I was suprised that my computer had big problems with it, 
now I know what the problem was/is.

I hope this solves the problems for a few people.

---

### Post by Chuckels550 on 2008-05-29
The following link solved all of my issues with the DVD Writer.[http://ubuntuforums.org/showthread.php?t=801771]("http://ubuntuforums.org/showthread.php?t=801771")

---

### Post by cokehabit on 2008-06-03
linking it solved it for me as well :)

---

### Post by Ghost|BTFH on 2008-06-05
Here's a question...why use a symlink? This is just messy.

The issue is, the source /dev/dvd has been changed to /dev/dvd1.

The program is expecting /dev/dvd, and it's not getting anywhere with that information.

Now, I understand that to many, the logic dictates that we move the source to what the program expects...

However, the source isn't the issue - the issue is the program is looking in the wrong place for what it needs.

Why not simply go into your Media tab inside xine and say, "Hey, instead of looking in /dev/dvd look in /dev/dvd1 please, oh, and for raw access, /dev/rdvd1 works just fine too."

Problem solved, no symlink necessary. No CLI necessary. Just tell the program where you want it to go.

And for the person having an issue with CDs not playing - same solution. It's expecting audio CDs to be loaded as /dev/cdrom and are now most likely /dev/cdrom0 or something of the ilk.

There's an option in the Media tab for that too. And if you don't have a media tab, you need to change your "user experience" setting to a higher level until you get one.

Cheers,
Ghost|BTFH

---

### Post by classem2003 on 2008-06-15
> **Ghost|BTFH said:**
> Here's a question...why use a symlink? This is just messy.

The issue is, the source /dev/dvd has been changed to /dev/dvd1.

The program is expecting /dev/dvd, and it's not getting anywhere with that information.

Now, I understand that to many, the logic dictates that we move the source to what the program expects...

However, the source isn't the issue - the issue is the program is looking in the wrong place for what it needs.

Why not simply go into your Media tab inside xine and say, "Hey, instead of looking in /dev/dvd look in /dev/dvd1 please, oh, and for raw access, /dev/rdvd1 works just fine too."

Problem solved, no symlink necessary. No CLI necessary. Just tell the program where you want it to go.

And for the person having an issue with CDs not playing - same solution. It's expecting audio CDs to be loaded as /dev/cdrom and are now most likely /dev/cdrom0 or something of the ilk.

There's an option in the Media tab for that too. And if you don't have a media tab, you need to change your "user experience" setting to a higher level until you get one.

Cheers,
Ghost|BTFH

Is'n it the beauty of linux? You have choices. I gave you two choices. You have chosen the first one to solve the problem, I chose the second one. The reason is simple: You are graphic interface guy, I am a CLI guy. But there is another reason for me to do it that way: I use several programs to reproduce DVDs, so instead of changing the thing in several places I just changed it in only one place. 

On the other hand, that is also the Karma of linux. This kind of things should not be happening in the first place. How do we suppose to know about this situation if we are  newbies?  Because of that, we are fond in the way it worked  for as. Believe me, you will be amaze of the amount of "messy" solutions to simple problems in the linux forums.

---

### Post by Ghost|BTFH on 2008-06-15
> **classem2003 said:**
> Is'n it the beauty of linux? You have choices. I gave you two choices. You have chosen the first one to solve the problem, I chose the second one. The reason is simple: You are graphic interface guy, I am a CLI guy. But there is another reason for me to do it that way: I use several programs to reproduce DVDs, so instead of changing the thing in several places I just changed it in only one place. 

On the other hand, that is also the Karma of linux. This kind of things should not be happening in the first place. How do we suppose to know about this situation if we are  newbies?  Because of that, we are fond in the way it worked  for as. Believe me, you will be amaze of the amount of "messy" solutions to simple problems in the linux forums.

All true, however, if you think about it, if we were newbies, we'd have installed fresh. In so doing, we wouldn't have this issue. It's a legacy issue caused from upgrading and the packages don't know where to go to find what they knew was in location X earlier.

It is definitely an issue that comes up more than once, and indeed, symlinks can make it easier, but to me, changing one thing (or several) is better than adding to the system, even one thing. I have enough stuff on my system, I don't need more.

But no, I'm not a GUI kinda guy. I'm a "whatever works best for the situation" kinda guy.

Cheers,
Ghost

---

