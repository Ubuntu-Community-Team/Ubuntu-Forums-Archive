---
title: "playback  of avi abends after loading from DVD or HD"
date: 2010-10-13
forum: Multimedia Software
---

### Post by eltonw on 2010-10-13
I installed Meetkat on Sunday, Oct. 10. Meerkat created the  default partitions on my
ASUS EEE 1000 PC.

So far, I have been able to play all AVI files, [COLOR="DarkGreen"]except for these described below[/COLOR]. Movie Player stops _with error messages_ in the following scenario:

The [COLOR="DarkRed"]video files[/COLOR] were [COLOR="DarkRed"]burnt on a DL DVD+R[/COLOR] disk (8.5 gb) on a Msc Powerbook. They playback without any problems on the Mac, directly from the laser disk.

The Asus netbook has an external SAMSUNG slim drive, from which the same DVD disk is read.

:-(When I try to play any of these AVI files from the DVD, [COLOR="DarkGreen"]they start the first few seconds then Movie Player stops with the current image on screen[/COLOR]. The same happens if I copy the file to the hard drive on the netbook.:-(

The 4 popup **error dialogs** are consistent, and consistently *in the same order* as follows: (topmost error dialog first):

1) An error occurred
Disconnected: Connection terminated 

2) An error occurred
pa_stream_cork() failed: Connection terminated

3) An error occurred
Disconnected: Connection terminated

4) An error occurred
pa_stream_writable_size() failed: Connection terminated

...any guidance  or assistance would be appreciated...

---

### Post by davec64 on 2010-10-14
HI,

I've been having the same problem. There are several bug reports relating to this but I couldn't find a solution.

I did find one option and that was to install VLC and run your films through that. This has worked for me and I can now play all my films correctly.

The bug reports seemed to blame pulseaudio but I don't know what VLC does to interact with it differently!

Hope that helps!  :P

EDIT:
If you're using Unity, you'll want to set VLC as the default player before trying to play a file as double clicking will open it in the default player and you don't get the right click menu for "Open With".

---

### Post by eltonw on 2010-10-14
***[SIZE="2"]Thank you![/SIZE]*** 

I have not been following the beta testing of Meerkat, so I was unaware of this bug, I've installed VLC and now it's the default player for AVI and WMV files on my netbook. I even use it on my Macbook. as the preferred video player for all formats. 

IMVHO, [COLOR="Olive"][FONT="Georgia"]VLC is the best media player around[/FONT][/COLOR]. No worries ](*,)about finding codecs. It just does what it is supposed to do!:biggrin:

I don't know why Ubuntu didn't set the Videolan player as the default app.:confused:

---

### Post by davec64 on 2010-10-15
Yep, I prefer VLC too, it just plays everything you throw at it!

---

### Post by tushantin on 2010-10-18
Yeah, Totem's giving me the same problem, but not with VLC. 

*except...*

When I try to run Sintel (I downloaded the highest quality; DivX / MP4 I suppose?) the video doesn't seem to go well, not even with VLC.

---

### Post by eltonw on 2010-10-31
[SIZE="3"]I have [COLOR="Red"]the same problem with **Movie Player[/COLOR]**.[/SIZE] 
:frown:No matter *what* DVD I load, ... either purchased movie disks, or ones that I have burned from an ISO ... it *_STILL_* throws up the same six dialog boxes one on top of the other. 

[FONT="Trebuchet MS"][COLOR="Sienna"]The most recent updates [TODAY:  31 OCT. 2010 16:28 EST] do not seem to fix it either.[/COLOR][/FONT]:-(

I wonder if I am among a minority of users seeing this problem?:confused:

---

### Post by davec64 on 2010-11-01
I tried an M4V and an AVI file in totem and both work for me now since the latest updates. Could it be something else causing the problems?

---

### Post by eltonw on 2010-11-02
> **davec64 said:**
> I tried an M4V and an AVI file in totem and both work for me now since the latest updates. Could it be something else causing the problems?
Have these (YOUR) files been loaded from the hard drive? ... or from a DVD disk? Are you using the desktop flavour of Meerkat, or tne **[COLOR="DarkRed"]notebook[/COLOR]** one?

The IMPORTANT PART of this (**my**) problem is that the files are being loaded from an external DVD drive. It appears that Meerkat Netbook Remix has a problem loading the drive since I see an error message when booting. I have connected the DVD burner to my Macbook and there is no problem playing the disks (DVD movies, or AVI files).

... in the meantime, I have _**[COLOR="DarkRed"]added a comment to this bug report[/COLOR]**_ [FONT="Verdana"][Bug #534340][/FONT] at **Launchpad**:
[https://bugs.launchpad.net/ubuntu/+source/totem/+bug/534340]("https://bugs.launchpad.net/ubuntu/+source/totem/+bug/534340")

I guess I'll just have to define VLC as the default media player and either remove Totem, or keep it pending a fix.

Thank you for your response, anyway.

---

### Post by davec64 on 2010-11-02
Hi Elton,

This all relates to Netbook Edition (on an Aspire A150) and these are files stored on the hard drive.
Do you get the same problem if you play a file from the hard disk?
The only think i can think of doing is perhaps totally remove Totem and its config files and reinstall, but looking at the nature of the bugs reported I doubt this will fix it.

Best of luck

---

### Post by r_mano on 2010-11-08
See [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/644644](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/644644)

For me, doing a

```
 cd ~ ; rm -rf .pulse
``` 

fixes it, at least till the next reboot.

---

