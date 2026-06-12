---
title: "audio CDs not playing"
date: 2010-11-08
forum: Multimedia Software
---

### Post by steveredshaw on 2010-11-08
:guitar:
I have just installed 10.10 on my Sony Vaio laptop, but an audio CD inserted into the drive is not recognised, it does not show up in the file manager or in RhythmBox and therefore cannot be played

this is the error I get from VLC when I try to open the disc

p, li { white-space: pre-wrap; } [COLOR=#FF0000]Your input can't be opened:[/COLOR]
 [COLOR=#000000]VLC is unable to open the MRL 'dvd:///dev/dvd'. Check the log for details.[/COLOR]
[COLOR=#000000](I don't know where the log is!)
[/COLOR]

how can I sort this out please?

---

### Post by cchhrriiss121212 on 2010-11-08
Is the drive recognising other discs? DVDs etc.

VLC is trying to open the default DVD location which seems to be empty. You should be able to find the CD in /media as cdrom0 or something.

---

### Post by mc4man on 2010-11-08
while it may not make any difference, (if you have some other issue) the relevant part of this is the blue
> VLC is unable to open the MRL '[COLOR="Blue"]dvd:[/COLOR]///dev/dvd'

The /dev link used, if accurate, to the drive is irrelevant.
So from vlc interface - media -> open disk -> click on "Audio Cd"

Or from a terminal 
```
vlc cdda:///dev/dvd
```
or (all really the same

vlc cdda:///dev/cdrom
vlc cdda:///dev/sr0

I'd run this to make sure of the device node (sr[COLOR="Blue"]X[/COLOR]) or /dev links (/dev/dvd, /dev/cdrom, ect)  first, you may be /dev/dvd1, /dev/cdrom1, ect. Look for the *-cdrom section
```
sudo lshw -C disk
```
> 
(I don't know where the log is!
There is no log unless logging is enabled, in any event pretty much the same as seen when running vlc from a terminal

After an audio cd is inserted, if recognised, the files (.wav's) can be seen in ~/.gvfs/cdda mount on sr[COLOR="Blue"]X[/COLOR]
(home folder - view show hidden files - .gvfs, ect.

---

### Post by steveredshaw on 2010-11-08
> You should be able to find the CD in /media as cdrom0 or something.found this in VLC, I was trying to get it to open a DVD - my mistake, so I did get VLC to play the CD, so far so good...however

after this an Audio CD listing appeared in the places pane of Nautilus, clicking on this displayed the tracks and at the top appeared a button to launch RhythmBox

having done this the CD also played in RythmBox

however nothing appears in the DVD VR folder in media and I cannot eject the CD from Nautilus or RhythmBox

> Unable to eject Audio Disc
/dev/sr0 is mountedand I cannot open the Audio CD palce from the Places drop down menu of the top task bar - I get the following error

> Could not open location 'cdda://s0/'
Failed to execute child process "sound-juicer" (No such file or directory)____________________________________________________________________

from

> sudo lshw -C diskI get

>   *-disk                  
       description: ATA Disk
       product: TOSHIBA MK8032GS
       vendor: Toshiba
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: AS11
       serial: X5SM4222S
       size: 74GiB (80GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=1e08c2a3don't know what this signifies if anything!!

I would say that my computer is not mounting the disc properly, although I have been able to play it and extract tracks to library - thanks for your help so far...

---

### Post by mc4man on 2010-11-08
> I cannot open the Audio CD palce from the Places drop down menu
The default for that remains sound-juicer which is no longer installed by default
To change the places icon to a player of choice 
in terminal
```
gconf-editor
```
scroll down and expand - desktop/gnome/url-handlers/cdda and for command r. click -edit  - enter command of choice
see screen ( in this case I'm using vlccd which is a script so vlc opens the cd properly with cddb info from multiple drives

You could  try using the  vlc cd command, if you just use vlc it will only open as .wav's
vlc cdda:///dev/dvd

(in lshw you need to look for the *-cdrom section, what you posted was *-disk - your harddrive

> however nothing appears in the DVD VR folder
Not sure what you mean, if referring to an audio cd then it's not mounted, only accessed/seen at the location mentioned

---

### Post by steveredshaw on 2010-11-09
I feel we are nearly there now!!

thanks mc4man, audio CD now recognised by RhythmBox, but still cannot eject it, so the Audio CD icon remains on my desktop and in the places pane of Nautilus even when I have taken the CD out of the drive

error from RhythmBox or Nautilus when I click eject is

> Unable to eject
/dev/sr0 is mountedI cannot find /sr0 in the dev folder and there is nothing in the media folder either

---

### Post by mc4man on 2010-11-09
Maybe try to eject in 'stages' to see where the issue may lie.
Do a restart to clear, then insert an audio cd and hold down the shift button till you get a pop up.
Try the 'eject' button in the pop up
If it works then re-insert the cd, hold down the shift, this time click 'cancel'.
Then r. click on the desktop audio cd icon -> eject, does this work?

If either of the above didn't work then open a terminal and run this command and post

```
eject -v
```

---

### Post by steveredshaw on 2010-11-10
:)

Well, this is puzzling - my Ubuntu seems to have knuckled down to dealing with CDs and DVDs and is doing everything correctly!

I have been trying out some operations - transferring files to a DVD, listening to and ripping from CDs and burning tracks onto a CD

I can eject from RhythmBox, Nautilus and the desktop icon - no problems

perhaps someone can surmise why it all works now? but thanks for your help and advice, much appreciated

---

### Post by Tonyr63 on 2011-03-07
Hi

I run vlc cdda:///dev/sr0 from the terminal and VLC started and played the CD fine, however within VLC if I chose Media, Open Disk with an Audio disk loaded i get the error message 

p, li { white-space: pre-wrap; } [COLOR=#FF0000]Your input can't be opened:[/COLOR]
 [COLOR=#000000]VLC is unable to open the MRL 'cdda://0w&#65533;	&#65533;t&#65533;	Pr&#65533;	&#65533;o&#65533;	&#65533;m&#65533;	8k&#65533;	&#65533;h&#65533;	Hf&#65533;	8'. Check the log for details.[/COLOR]

[COLOR=#000000][/COLOR]
[COLOR=#000000]Rythembox will not play an audio disk showing the error message widely reported however no remedy is provided by the Ubuntu community.  Places will not open the Audio disk which is mounted in front of you on the desktop.  This is very flaky and bug ridden.[/COLOR]

[COLOR=#000000][/COLOR]
[COLOR=#000000]This means that Ubuntu still cannot reliably play a simple Audio disk compiled with a file format that is more than 20 years old even though the device is mounted in the file system![/COLOR]

[COLOR=#000000][/COLOR]
[COLOR=#000000]I have experienced problems over the years with various versions of Ubuntu not properly supporting audio disks.  Can it really be that hard to stabilize the O/S to fix this?
[/COLOR]

---

### Post by edwardoclese on 2011-11-21
I had similar problems and solved them by installing [FONT=Courier New]gvfs-backends.[/FONT]

---

### Post by beew on 2011-11-21
Try this and see if it works.

```
sudo ln -s /dev/sr0 /dev/cdrom
```

---

### Post by lagerratrobe on 2011-11-29
Agreed, this is pretty ridiculous.  I have a seemingly random chance of my 10.10 machine recognizing an audio CD.  Sometimes the same disk is read fine on the 1st try, other times I reboot 7 times and scratch my stomach, then it reads the disc.

What is equally frustrating is that it seems the quality of the posts on the Ubuntu forums from the development team seem to have slid downhill in the past 5 years as well.  I see many, many instances of this bug mentioned by people from all over the place, and also many frankly stupid suggestions coming from people who should know better.

Lame, lame, lame and for the 1st time in a VERY long time, I'm considering whether it is time to find another Linux distro to use.

---

