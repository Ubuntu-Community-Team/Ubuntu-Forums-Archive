---
title: "sound juicer question"
date: 2008-12-29
forum: Multimedia Software
---

### Post by willfriedwald on 2008-12-29
for some reason I can't find a usable CD audio extractor program for Ubuntu -

am trying to extract CDs into AAC format, at the highest bitrate I can get (320 stereo / 160 mono).

I tried extracting a track in sound juicer at "CD quality AAC" and the resulting file will NOT play in iTunes.

any suggestions?

w

willfriedwald

---

### Post by wolfen69 on 2008-12-29
try ripperx. it worked good for me. you can find it in synaptic.

---

### Post by mc4man on 2008-12-29
Use anything that doesn't use the gstreamer acc profile (main

Ex. 
doesn't work in itunes (used sound-juicer
> Encoded_application : Lavf1d.51.10.0 
Audio #0 
Codec : AAC Main 
Codec/Family : AAC 
Codec/Info : AAC Main Profile 
PlayTime : 5mn 38s 
Bit rate mode : VBR 
Bit rate : 128 Kbps 

Does play (used NeroAac, though faac works also
> Encoded_application : Nero AAC codec / Aug 6 2007 
Audio #0 
Codec : AAC LC 
Codec/Family : AAC 
Codec/Info : AAC Low Complexity 
PlayTime : 5mn 37s 
Bit rate mode : VBR 
Bit rate : 302 Kbps 
Maximum bit rate : 338 Kbps 

---

### Post by willfriedwald on 2008-12-31
I tried ripper X - thanks for the suggestion - but am having a very basic problem, it does NOT find the CD that's in the drive!  I turn on the program and it keeps telling me that there's no disc in the drive.

sound juicer finds it, but I have other problems with sound juicer...

thanks!

willfriedwald

---

### Post by mc4man on 2008-12-31
You could try grip, while i use rubyripper with NeroAac I still have grip installed, screen shows last settings I used for faac.

By default I believe it uses something like -b %b which isn't what your after.
I wouldn't bother with -b  anything, you'll get better quality and control using a -q setting. (faac is vbr

As I remember there were several ways to set a q, I must have settled on -q xxx for faac in grip
Also there were no logical increments in xxx, -q 340 seemed quite enough. (maybe higher than needed, though you can push it higher

 Grip will default to saving in ~/ogg, you can change that.
 
 Grip doesn't number the tracks so I changed that parameter so it would.

```
-q 340 -o %m -w --artist %a --title %n --genre %G --album %d --track %t/%N --year %y %w
```

```
~/Music/%A/%d/%t- %n.%x
``` (added %t- and a space to default to number the tracks

---

### Post by willfriedwald on 2009-01-01
thanks - the info & screenshot are very helpful.

question: the screenshot - that was from Grip?  or was it soundjuicer or ripperX?

thanks!  will try.

happy new year

willfriedwald

---

### Post by Vryko Lakas on 2009-01-01
I recognize that screenshot as Grip. I use it to rip CDs that have some scratches and tend to skip when played. It's pretty good at correcting for those sorts of things.

---

### Post by willfriedwald on 2009-01-03
I was about to try GRIP (thanks very much for that string of code to encode)...

however, it doesn't seem to find the CD in the drive, or recognize my CD drive.

I had this problem with ripperX as well.  For some reason, sound juicer finds the CD in the drive, but ripperX and GRIP do not.

I don't know why this is happening.  Clearly, the Ubuntu OS recognizes the drive.  The disc shows up perfectly mounted on the desktop.

Any suggestions?

w

---

### Post by willfriedwald on 2009-01-06
question for mc4man - 

Okay - I did exactly what you said (the lines of encoder code) and I DID get it to work - I ripped a CD track into an M4A file - one that iTunes recognizes & plays as an M4A file.  thanks!

my question: the resultant file was ripped at 127 kbps - how do I get it to rip at 320 kbps (for optimum sound quality)

(my next question will be: how do I get it to rip in Mono - but one thing at a time!)

thanks for getting me to this point!

w

---

### Post by mc4man on 2009-01-07
I only used grip for a day or so, I remember there where a couple of ways to input quality. for some reason I settled on the method I see now in it's settings. So a few encodes of the same track show this...

As reported by mediainfo (blue is what I had
faac in grip
```
-q [COLOR="Red"]340[/COLOR] -o %m -w --artist %a --title %n --genre %G --album %d --track %t/%N --year %y %w
```

Default  - 127kbs  - max 183
[COLOR="Blue"]-q 340[/COLOR]  - 264kbs  - max 330
-q 540  - 301kbs  - max 370k   (max under faac with this input method

Using NeroAac in grip ( I guess I didn't find way to use -q
```

-if %w -of %m -br [COLOR="Red"]320000[/COLOR] -2pass
```

[COLOR="Blue"]-br 320000 -2pass[/COLOR] - 316  -max 356
-br 520000 -2pass - 494kbs  -max 525  (again max


I use NeroAac in rubyripper which accepts standard -q values ( 0.37 is about 128
```
neroAacEnc -q 0.65 -if %i -of "%o.m4a"
```

Or Nero can be run by itself (probably better to rip to .wav, then run, example of directly off of the drive

> ./neroAacEnc -if "/home/doug/.gvfs/cdda mount on scd0/Track 9.wav" -of "/home/doug/Desktop/nero75.m4a" -q 0.75


[COLOR="Blue"]-q 0.55[/COLOR] - 216kbs - max 245
[COLOR="Blue"]-q 0.65[/COLOR] - 264kbs - max 303
-q 0.75 - 336kbs - max 372


So just fool around with the numbers, I wouldn't get to hung up on br.,I actually think the ones in blue are more than enough.

---

### Post by willfriedwald on 2009-01-07
thank you for all the helpful info -

one more GRIP conundrum (there will be others...)

I still can't get GRIP to find the CDROM drive -

don't know why, because
1 - it is plainly mounted on the desktop
2 - soundJuicer finds it immediately.

I get the error message from GRIP:

error: unable to initialize [/dev/cdrom]

thanks!

w

---

### Post by mc4man on 2009-01-07
run this to ck. on drive /dev links
```

sudo lshw -C disk
```

---

### Post by willfriedwald on 2009-01-07
tried it - does this tell you anything (need to know why GRIP can't see the CD in the CD ROM drive...) - thanks!

will@supermatrix:~$ sudo lshw -C disk
[sudo] password for will: 
  *-disk:0                
       description: ATA Disk
       product: WDC WD10EACS-00D
       vendor: Western Digital
       physical id: 0
       bus info: scsi@12:0.0.0
       logical name: /dev/sde
       version: 01.0
       serial: WD-WCAU41096134
       size: 931GiB (1TB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5
  *-disk:1
       description: ATA Disk
       product: WDC WD10EACS-00D
       vendor: Western Digital
       physical id: 1
       bus info: scsi@13:0.0.0
       logical name: /dev/sdf
       version: 01.0
       serial: WD-WCAU41096122
       size: 931GiB (1TB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5
  *-cdrom
       description: DVD-RAM writer
       product: DVD A  DH20A4P
       vendor: ATAPI
       physical id: 0.1.0
       bus info: scsi@6:0.1.0
       logical name: /dev/cdrom1
       logical name: /dev/dvd1
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 9P59
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom1
  *-disk:0
       description: ATA Disk
       product: Maxtor 6L300S0
       vendor: Maxtor
       physical id: 0
       bus info: scsi@8:0.0.0
       logical name: /dev/sda
       version: BACE
       serial: L62Q9PVG
       size: 279GiB (300GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=000bf74b
  *-disk:1
       description: ATA Disk
       product: WDC WD10EACS-00D
       vendor: Western Digital
       physical id: 1
       bus info: scsi@9:0.0.0
       logical name: /dev/sdb
       version: 01.0
       serial: WD-WCAU41091984
       size: 931GiB (1TB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=d316d317
  *-disk:0
       description: ATA Disk
       product: WDC WD10EACS-00D
       vendor: Western Digital
       physical id: 0
       bus info: scsi@10:0.0.0
       logical name: /dev/sdc
       version: 01.0
       serial: WD-WCAU41091490
       size: 931GiB (1TB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=d316d316
  *-disk:1
       description: ATA Disk
       product: WDC WD10EACS-00D
       vendor: Western Digital
       physical id: 1
       bus info: scsi@11:0.0.0
       logical name: /dev/sdd
       version: 01.0
       serial: WD-WCAU41240394
       size: 931GiB (1TB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=d316d318
  *-disk:0
       description: SCSI Disk
       product: nuvi Flash
       vendor: Garmin
       physical id: 0.0.0
       bus info: scsi@16:0.0.0
       logical name: /dev/sdg
       logical name: /media/GARMIN
       version: 1.00
       size: 1438MiB (1508MB)
       capabilities: removable
       configuration: ansiversion=5 mount.fstype=vfat mount.options=rw,nosuid,nodev,relatime,uid=1000,fmask=0077,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,utf8 state=mounted
  *-disk:1
       description: SCSI Disk
       product: nuvi SD Card
       vendor: Garmin
       physical id: 0.0.1
       bus info: scsi@16:0.0.1
       logical name: /dev/sdh
       version: 1.00
       capabilities: removable
       configuration: ansiversion=5
     *-medium
          physical id: 0
          logical name: /dev/sdh
will@supermatrix:~$

---

### Post by mc4man on 2009-01-07
Your drive is /dev/cdrom1

In grip go Config -> CD and change there. Close grip and reopen, you should be good.

If any players have a problem with cd's or dvd's then their default is probably /dev/cdrom and or /dev/dvd, adjust in their settings to /dev/cdrom1 and /dev/dvd1

---

### Post by willfriedwald on 2009-01-07
man!  you are the expert!

yes, by changing it to cdrom1, grip was able to find it thanks!

next question:

in the encode settings :

if I set it to "q 540" the resulting soundfile is 267 kbps

if I sent it to "q 640" (a number I just picked at random)the resulting soundfile is 252 kbps.

I was thinking the higher the q number setting, the greater the kbps output - but apparently not!

would like to get it up to 320 kbps, but I guess I can settle for 267 if I have to.

(and at a certain point will shoot for mono, but one issue at a time...)

thanks!

w

---

### Post by willfriedwald on 2009-01-07
man!  you are the expert!

yes, by changing it to cdrom1, grip was able to find it thanks!

next question:

in the encode settings :

if I set it to "q 540" the resulting soundfile is 267 kbps

if I sent it to "q 640" (a number I just picked at random)the resulting soundfile is 252 kbps.

I was thinking the higher the q number setting, the greater the kbps output - but apparently not!

would like to get it up to 320 kbps, but I guess I can settle for 267 if I have to.

(and at a certain point will shoot for mono, but one issue at a time...)

thanks!

w

PS: one more question - GRIP encodes & saves files with titles like this :
02- where_or_when.m4a

those underscore marks also occur in the artist name & the album title, in addition to the song title (as_you_can_see)

how can I get rid of them?  fix it so that it does note encode with underscore marks, I mean?

thanks again!

w

---

### Post by mc4man on 2009-01-07
As I mentioned ( not as clearly as I should) with *that input method* using faac 540 or 5xx in general is the maximum. You may actually get 'better' sound at lower values.
There was another way I think to input for faac in grip, I really didn't spend much time on it. (grip in general

-q works differently than setting a bitrate, again don't get too hung up on reported numbers.

If you want to try NeroAac as an encoder let me know, extremely simple to set up.

---

### Post by willfriedwald on 2009-01-08
thanks...

NeroAac is a separate program?  Or it's an encoder that works within GRIP or another program?

anyhow, will check it out - thanks!

w

---

### Post by willfriedwald on 2009-01-08
giving this a shot -
I downloaded the neroAAC thing...
then I should put the three linux executables in the usr/bin folder?
(the system won't let me do this - permission denied...)
then tell grip to use the new encoder,which is supposed to be in the usr/bin folder?

am sure I must be doing something wrong - help!

w

---

### Post by wolfen69 on 2009-01-08
you need to be superuser to have permission. do
```
gksudo nautilus
``` then you can copy the files where you want.

---

### Post by mc4man on 2009-01-08
You only need the neroAacEnc file, for grip it doesn't matter where you put it, loose in your home folder is fine (you just give it the correct path. 
 If you where to use rubyripper it has to be in /usr/bin.

The more important thing is to make the file executable.

If it was loose in your home folder just go in a terminal ```
chmod +x neroAacEnc
```

Or right click -> properties and ck. the box to make executable.

At that point just leave it there and set in grip -> config -> encode -> 'other', /home/username/neroAacEnc

Or use gksudo nautilus as suggested and then move it to /usr/bin

If you want to try as a standalone to encode

if it's loose in home start command with ./neroAacEnc

if it's in /usr/bin start command with neroAacEnc

---

### Post by mc4man on 2009-01-08
forum

---

### Post by mc4man on 2009-01-08
forum...

---

### Post by mc4man on 2009-01-08
forum error

---

### Post by willfriedwald on 2009-01-09
will@supermatrix:~$ gksudo nautilus 
Initializing nautilus-share extension 
 
** (nautilus:16801): WARNING **: Unable to add monitor: Operation not supported 
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSS
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSS
SSSSSSSSSSSSSS 
 
I got the message above - and I still can't copy into /bin... I must still be 
doing something wrong...

---

### Post by willfriedwald on 2009-01-09
thanks - okay will try tom'w!

thanks again for all the help!

(got this one now - there were some errors on the forum this afternoon...)

---

### Post by mc4man on 2009-01-09
To some extent that 'error' message is normal, did you get a pop up 'root file browser'? (if so go file system -> usr -> bin

Or just stick it in your home folder and set grip to look there.

---

### Post by willfriedwald on 2009-01-09
hey - I just discovered the thanking button.  sorry for not thanking you sooner!

okay - here's the latest -

I think I did everything right, and I do NOT get an error message, but there is no m4a file in the folder, even though there is a WAV file and, according to the status window, the WAV should have been properly encoded into an M4A.  what to do?

I have two hopefully helpful screenshots (PNG files) I can show you - am not sure how to post them here...

(I see there's a tool for inserting an image, but it has to be on an html somewhere, which I don't got..)

maybe I can try to convey it in text

encoder: other
executable: /home/will/neroaac/neroAacEnc
encoder command line; -q 340 -o %m -w --artist %a --title %n --genre %G --album %d --track %t/%N --year %y %w
extension: m4a
file format: ~/Music/%A/%d/%t- %n.%x

the last three are exactly as you gave 'em to me...

executable: /home/will/neroaac/neroAacEnc
is exactly where it should be, and the file is checked (in permissions) as executable...

am still doing something wrong!  thanks for your continued help!

w

---

### Post by mc4man on 2009-01-09
Yeah, pretty simple, your using the the faac input command for grip with neroAac. **None** of those commands are interchangeable.

Nero in grip use this format(from post 10

> Using NeroAac in grip ( I guess I didn't find way to use -q

```
-if %w -of %m -br [COLOR="Red"]320000[/COLOR] -2pass
```

red can be adjusted

---

### Post by willfriedwald on 2009-01-09
okay:

so this should be


encoder: other

or this 

encoder: faac
?


and should this go as follows :

encoder command line: -if %w -of %m -br 320000 -2pass
?

(am not sure where I should put that line, the "-if %w -of %m -br 320000 -2pass")

thanks yet again ... more pineapples for you!

w

---

### Post by mc4man on 2009-01-09
I've edited post 10 for you. The first 2 code boxes are the encoder settings for grip. (red can be adjusted

Grip can only encode using 1 encoder at a time, the one you pick in 'config' -> 'encode'

The settings are only entered once (you can change the red to suit at any time

Code box 1 is  the encoder command for faac, see screen 1

Code box 2 is the encoder setting for other (in this case neroAac), see screen 2

Note : it's usually a good idea to close and reopen grip after making changes

Edit : if you need to copy the commands use post 10, screens are just a visual aid and screen 1 (faac) doesn't show complete command. Anyway I think you already entered that command previously

---

### Post by willfriedwald on 2009-01-10
it still doesn't appear to be encoding the files from WAV to M4A; the WAV files are where they should be, but there are no M4A files in the folder...

here's are some screen shots are that are hopefully helpful:

[http://picasaweb.google.com/lh/photo/QPuAoqBUOVftl83Zun9LUQ?feat=directlink](http://picasaweb.google.com/lh/photo/QPuAoqBUOVftl83Zun9LUQ?feat=directlink)

[http://picasaweb.google.com/lh/photo/2sW5FoM2ddTSZTcbbXjWRQ?feat=directlink](http://picasaweb.google.com/lh/photo/2sW5FoM2ddTSZTcbbXjWRQ?feat=directlink)

[http://picasaweb.google.com/lh/photo/SnzUaidw2bqFgKhVZ3DyRA?feat=directlink](http://picasaweb.google.com/lh/photo/SnzUaidw2bqFgKhVZ3DyRA?feat=directlink)

W

---

### Post by willfriedwald on 2009-01-10
let me try this another way:

[IMG]http://picasaweb.google.com/lh/photo/SnzUaidw2bqFgKhVZ3DyRA?feat=directlink[/IMG]

[IMG]http://picasaweb.google.com/lh/photo/2sW5FoM2ddTSZTcbbXjWRQ?feat=directlink[/IMG]

[IMG]http://picasaweb.google.com/lh/photo/QPuAoqBUOVftl83Zun9LUQ?feat=directlink[/IMG]

<table style="width:auto;"><tr><td><a href="http://picasaweb.google.com/lh/photo/QPuAoqBUOVftl83Zun9LUQ?feat=embedwebsite"><img src="http://lh5.ggpht.com/_KmvmwLTjDSk/SWjoL2sBZRI/AAAAAAAAAEg/kD1CBbsGWhM/s144/GRIP%20ENCODE%20CONFIG%204.png" /></a></td></tr><tr><td style="font-family:arial,sans-serif; font-size:11px; text-align:right">From <a href="http://picasaweb.google.com/wfriedwald/Linux?feat=embedwebsite">linux</a></td></tr></table>





maybe this will work - maybe not, I barely know what I'm doing when it comes to music, and I know much less when it comes to images, and what to do with them!

w

PS: forget it - I can't figure out how to embed the images - hopefully those links above will work!

---

### Post by phenest on 2009-01-17
If it's of any help, I've spent a whole day trying work out how to rip CD's to high quality aac/m4a files. I have discovered that you do not use bitrates, as aac is really meant to be a vbr format, and using cbr reduces the quality. So you need to set the quantizer setting which is between 10 and 500(max). I also discovered that gstreamer and faac produce very horrible sounding files whereas ffmpeg gives excellent results even at high settings. So I've written a bash script:
```
#!/bin/bash

# CD rip to m4a

cdparanoia -B 1-

for i in *.wav; do ffmpeg -y -i $i -acodec libfaac -aq 200 `basename $i .cdda.wav`.m4a; rm $i; done

exit 0
```
Change the 200 to whatever you want (500 max) but I have no idea why you want such high bit rates. 500 should give approx 320kb/s.

---

### Post by phenest on 2009-01-17
> **willfriedwald said:**
> PS: forget it - I can't figure out how to embed the images - hopefully those links above will work!

You can't use html on this forum. Try adding the image as an attachment.

---

### Post by willfriedwald on 2009-01-27
thank you for that script --

I haven't used a script before; am not sure how it works - these are all terminal commands?

thanks - will give it a try - sorry for not seeing it until now (I thought that everyone was done responding to this thread...

thanks again!

w

---

### Post by willfriedwald on 2009-01-28
thanks for the helpful info!

I tried it - it worked as you said.

it converted a CD into a bunch of wav files, but am not sure where it put them! at one point, they were in my home folder along with the script itself, but then when the script finished, they disappeared.

I had the impression that it was supposed to convert the WAV files into AACs and then delete the WAVs, but am not sure what it actually did - the only thing I could swear to is that it did create some WAVs and ultimately deleted them - more I can not tell you!

thanks - have been searching high & low for a means to get high quality AAC files from a CD, and hope to find it eventually... if only there were iTunes for Ubuntu!

one other thing: while I was lookinng at the WAV files (before they disappeared) they all had generic titles, ie "song 1," is there a way to get the script to TAG the song names from the CDDB or something first?

w

---

### Post by kitashi on 2009-02-20
(in reply to the original question #1)
> **willfriedwald said:**
> 
I tried extracting a track in sound juicer at "CD quality AAC" and the resulting file will NOT play in iTunes.


As mc4man said in #3,  "AAC-LC" works in itunes but "AAC MAIN" doesn't.

> **mc4man said:**
> 
Use anything that doesn't use the gstreamer acc profile (main


To make AAC-LC with GStreamer, give "profile=2" option to "faac" in the pipeline.

e.g. in sound-juicer (Edit > Preferences > Edit Profiles > Edit "CD Quality, AAC" > GStreamer pipeline)
```
audio/x-raw-int,rate=44100,channels=2 ! faac [COLOR="Red"]**profile=2**[/COLOR] ! ffmux_mp4
```

hope it works;)

---

