---
title: "Issues playing video files, really need help!"
date: 2009-07-27
forum: Multimedia Software
---

### Post by alfoldem on 2009-07-27
Over the last couple of months i have encountered this problem more and more and it seems to be happening on almost every media / video file i try and play.
If anyone can help me work out why these files are not playing it would be greatly appreciated.

The files seem to be standard .avi files that i have downloaded from the web.

If i try and open the file with MPlayer i get the message
"Cannot find codec for audio format 0X56444152"
I know there are various results if i google that error code but none of them seem to help me.

If i try and open the file with Movie Player (GStreamer) i get the message
"Unable to determine type of stream"

If i try and use Movie Player (Xine) i get the message
"There is no plug in to handle this movie"

And trusty old VLC just wont play it at all - although since i updated VLC i have been having various problems with it.

i have tried updating codecs etc etc but nothing seems to work.
For the last 6 months i havent had any problems downloading and playing any files but now all of a sudden i seem to be having problems with every other file!!
Currently running 9.04.

Is there any way i can get more detail on why these files wont play?

---

### Post by martinbaselier on 2009-07-27
2 suggestions: try the command file in a terminal on it, to determine the exact type:
Check the multimedia guide in my signature.

---

### Post by alfoldem on 2009-07-27
thanks for replying, i have noticed people talk about using the command line for this type of thing, what exactly do i need to type?

p.s i have been through the multimedia guide in your sig - thanks

---

### Post by vinutux on 2009-07-27
what type of codec used for video file ?...check that first......right click file > Properties > Audio/vodio tab .......

---

### Post by martinbaselier on 2009-07-27
sorry, forgot the command
file
example:
file Van.Vlees.en.Bloed.S01E01.DTV.XviD.avi
Van.Vlees.en.Bloed.S01E01.DTV.XviD.avi: RIFF (little-endian) data, AVI, 624 x 352, 25.00 fps, video: XviD, audio: MPEG-1 Layer 3 (stereo, 48000 Hz)

and use tab to complete filenames (or commands or directory names)

---

### Post by alfoldem on 2009-07-27
> **vinutux said:**
> what type of codec used for video file ?...check that first......right click file > Properties > Audio/vodio tab .......

Audio codec = "N/a"

Basic details  "AVI video (video/x-msvideo)"

---

### Post by vinutux on 2009-07-27
> **alfoldem said:**
> Audio codec = "N/a"

Basic details  "AVI video (video/[COLOR="Red"]x-msvideo[/COLOR])"

X-msvideo codec problem......
[URL="http://www.moviecodec.com/topics/19184p1.html"]
http://www.moviecodec.com/topics/19184p1.html[/URL]

---

### Post by alfoldem on 2009-07-28
Thanks for the posts,

I cant find any "easy" way of solving X-msvideo codec problem......
I have all the restricted extra's etc etc installed and cant find anything straightforward about how to resolve this.

When i put the file name into the terminal i get a message telling me permission denied.

Could this be related to my recent upgrade to 9.04?
I dont seem to recall having these problems prior to upgrading.
The files i am attempting to open are fairly common / popular torrent files - all of which have had comments posted against them and none mentioning that the files are dodgy.

Any guidance would be appreciated.:confused:

---

### Post by vinutux on 2009-07-28
If you are install pakages from thirdparty repos make prob when upgrades

Check your gsreamer versions from official repos or third parties Rightclick gstreamer pakages in synaptic>properties>Version

if there is more than one version you need to force to official versions Pakeges>force

or

un tick all un-official repos from System>administration>softwaresources

Then reintsall plugins (ubuntu-restricted-extras)

---

### Post by alfoldem on 2009-07-28
> **vinutux said:**
> 
Check your gsreamer versions from official repos or third parties Rightclick gstreamer pakages in synaptic>properties>Version

if there is more than one version you need to force to official versions Pakeges>force



Vinutux, i must say THANKS A LOT, despite not being entirely sure what i was doing i "forced" the versions for gstreamer via synaptic and everything works fine now. :D:D:D:D:D:D
Im guessing this has happened due to 3rd party repo's?

---

### Post by vinutux on 2009-07-28
> **alfoldem said:**
> Vinutux, i must say THANKS A LOT, despite not being entirely sure what i was doing i "forced" the versions for gstreamer via synaptic and everything works fine now. :D:D:D:D:D:D
Im guessing this has happened due to 3rd party repo's?

yeh..there is third party repos in your software-sources (like mediubuntu..)

The gstreamer version number of third party repos may higher than official .....so if you upgrade system third party gstreamer replace to official one...third party versions not well integrated to ubuntu............So please inactivate third party repos just after install appropriate apps.

---

