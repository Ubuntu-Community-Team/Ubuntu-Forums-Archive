---
title: "Kdenlive 0.5 released!"
date: 2007-08-12
forum: Multimedia Production
---

### Post by UbuWu on 2007-08-12
From their [website]("http://www.kdenlive.org/"):
After 8 months of hard work, we are glad to announce the release of Kdenlive 0.5. Kdenlive is a non linear video editor for the KDE environnment. Improved stability and many new features have been added since Kdenlive 0.4.

Being based on the the MLT video framework and the FFMPEG project, Kdenlive can work with image, audio and video files of various formats. All these formats can be mixed in your project on an unlimited number of audio and video tracks. Thanks to the MLT framework, Kdenlive 0.5 now supports HDV editing as well as DV and more.

New features include:

    * New image formats
      Added support for gimp xcf and exr.
      Other supported formats are: png, jpeg, gif (non animated), xcf, exr, tiff, svg, mp3, vorbis, wav, flash, mpeg, avi, dv, wmv,... You can even insert another Kdenlive project in the timeline!
    * Effects and Transitions
      Many fixes, and effects and transitions can now be copied from a clip to another.
    * Export formats
      Theora export is now available if FFMPEG was compiled with theora support.
    * Timeline
      Improved markers, allow insertion of of several clips in one operation, added "remove empty space" feature, multi clip selection tool
    * Metadata
      Kdenlive can now read and write metadata in video and audio files
    * Video preview
      Overlay project timecode on the video preview. Click in monitor to play / pause, mouse wheel to seek, multi track view (monitor is split in 4 zones, each one showing a different track),
    * Project management
      User can define a frame that will be used as thumbnail for each video clip in the project
    * General
      Many fixes to the undo / redo system, lots of ui fixes and enhancements 

For more information:

Kdenlive web site: [http://kdenlive.org](http://kdenlive.org)

---

### Post by UbuWu on 2007-08-12
And [someone is working on getting it in the Gutsy repo's]("https://bugs.launchpad.net/ubuntu/+source/mlt/+bug/131341")! :KS

---

### Post by Adler on 2007-08-12
UbuWu,

Hey, thanks for that. I've been doing some YouTube Desktop Vid captures, and see that I'll be able to edit them. Cool!

Any repos out there already?

Adler

---

### Post by amonsul on 2007-08-12
here

[http://3v1n0.tuxfamily.org/dists/feisty/3v1n0/index.html](http://3v1n0.tuxfamily.org/dists/feisty/3v1n0/index.html)

Look for MLT, MLT++ and Kdenlive!

---

### Post by UbuWu on 2007-08-12
For Feisty, this is probably the best place to get deb's for kdenlive, it has one of the latest svn versions which is pretty much the same as the 0.5 release:

[http://3v1n0.tuxfamily.org/dists/feisty/3v1n0/index.html](http://3v1n0.tuxfamily.org/dists/feisty/3v1n0/index.html)

---

### Post by Adler on 2007-08-12
UbuWu / amonsul

Thanks -- that was fast.

Adler

---

### Post by bluenova on 2007-08-12
It asks me to start a new project or open an existing one, then crashes with no output.

---

### Post by amonsul on 2007-08-12
do you have inserted the right path for mlt???

---

### Post by linux_rocks on 2007-08-14
Hi! How do I install Kdenlive 0.5 in my Ubuntu Studio system? :confused:

I downloaded the file from the [FAQ Install ]("http://kdenlive.sourceforge.net/wiki/index.php?title=Faq_Install#Ubuntu") but it has 6 files...and the FAQ page said it was for "Ubuntu Edgy Eft 6.10"

[[IMG]http://s2.supload.com/thumbs/default/Screenshot-20070814203846.png[/IMG]](http://s2.supload.com/free/Screenshot-20070814203846.png/view/)

I'm sorry if this is a dumb question :???: but I dont want to mess up my system, it works so nicely.

---

### Post by linux_rocks on 2007-08-14
Okay I found this[ here]("http://66.249.91.104/translate_c?hl=en&sl=pt&u=http://ubuntupedia.info/index.php/Kdenlive&prev=/search%3Fq%3Dhttp://ubuntupedia.info/index.php/Kdenlive%26hl%3Den%26client%3Dfirefox-a%26rls%3Dcom.ubuntu:en-US:official%26hs%3DtWS"):
>  To install the Kdenlive

The Kdenlive does not exist in the repositories of Ubuntu 7,04, for what the installation procedure is the following one:


1º - To add to the repository that the Kdenlive ace its sources of applications

Note: In the menu of the Gnome to go the System > Administration > Canals of software. Later seleccionar the border “Applications of third” and pressuring the button “Add”. To add the following line:

deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty 3v1n0 


2º - To open one consoles and to bring up to date the list of packages with the command:

$ sudo apt-get update


3º - In it consoles to add the digital signatures of the programmer

$ gpg --to keyserver subkeys.pgp.net --recv 2D6CFB44DD800CD9

$ gpg --export --sudo armor 2D6CFB44DD800CD9 | apt-key add -


4º - In it consoles to install kdenlive

sudo apt-get install kdenlive


5º - To run the program through the menu of the Gnome:

Applications > Sound and video > Kdenlive 

could someone explain the steps 2, 3 and 4? Thank you! :)

---

### Post by swisscow on 2007-08-15
This sounds like a translation done with an online tool!

Ok what 2, 3 and 4 are just commands to paste into the terminal and run one at a time. Once you've added the repositories to your sources.list (step 1), step 2 updates apt-get so it knows what software is available, step 3 adds keys so you can get it and step 4 installs kdenlive.

---

### Post by flawedprefect on 2007-08-15
I'd never thought I'd say this but... WOW. I come from a mac environment, and when at home, I need to boot into WIndows, and the closest thing I got to edit in is a copy of Premiere elements. I tried CInelarra - HATED IT. PiTiVi and the other one that merely digitizes I just don't get how each is half a program... THis little gem does what I need it to: easily import video and audio, trim files, splice clips, drag clips from various timelines, do basic effects and transitions, and then render out to a number of formats. In retrospect, I wanted to scream "is that so much to ask!?" Kdenlive answered my prayers. I shall be checking this out further.

---

### Post by Corbelius on 2007-08-15
@ Feisty Fawn **AMD64**

Kdenlive 0.5 "stable" find to upure64 repository ;)

[http://ubuntuforums.org/showthread.php?t=196093](http://ubuntuforums.org/showthread.php?t=196093)

---

### Post by dad311 on 2007-08-15
> **Corbelius said:**
> @ Feisty Fawn **AMD64**

Kdenlive 0.5 "stable" find to upure64 repository ;)

[http://ubuntuforums.org/showthread.php?t=196093](http://ubuntuforums.org/showthread.php?t=196093)


Downloaded and installed from upure64 respository, seems to work well.

---

### Post by dabl on 2007-08-15
I'm getting unresolved dependencies complaints from Synaptic for mlt --

 " Depends: libc6 (>=2.6-1) but 2.5-0ubuntu14 is to be installed
 Depends: libmlt0.2.4 but it is not going to be installed"

There are more if I try to mark Kdenlive, but I know I need mlt first anyway, so might as well deal with that one.

??? I'm running Feisty 2.6.20-16-lowlatency.  What am I missing?  :confused:

---

### Post by linux_rocks on 2007-08-17
Okay thans for your help!

I do step 1 and 2 and get this in the terminal:

> W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2D6CFB44DD800CD9
W: You may want to run apt-get update to correct these problems


then pasting this in the terminal (step 3)
```
gpg --to keyserver subkeys.pgp.net --recv 2D6CFB44DD800CD9
```

gets this:
> :~$ gpg --to keyserver subkeys.pgp.net --recv 2D6CFB44DD800CD9
gpg: Invalid option "--to"

anyway am i doing it all wrong or what...i heard great things about kdenlive about how it could be the iMovie of linux.

---

### Post by UbuWu on 2007-09-02
Kdenlive has been added to the gutsy repo's!!! :guitar:

---

### Post by mjakennedy on 2007-10-07
inux_rocks - Did yuou get an offline reply i am getting the same problems as you:
thanks for your help..........

[I][COLOR="DarkOrange"]I do step 1 and 2 and get this in the terminal:

Quote:
W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2D6CFB44DD800CD9
W: You may want to run apt-get update to correct these problems

then pasting this in the terminal (step 3)
Code:

gpg --to keyserver subkeys.pgp.net --recv 2D6CFB44DD800CD9

gets this:
Quote:
:~$ gpg --to keyserver subkeys.pgp.net --recv 2D6CFB44DD800CD9
gpg: Invalid option "--to"
anyway am i doing it all wrong or what...i heard great things about kdenlive about how it could be the iMovie of linux.[/COLOR][/I]

---

### Post by Dave M G on 2007-10-07
I have installed the Trevino Ubuntu Repository. However, when I attempt to install Kdenlive, it returns this error:

```
sudo apt-get install kdenlive
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  kdenlive: Depends: libfreetype6 (>= 2.3.5) but 2.2.1-5ubuntu1.1 is to be installed
E: Broken packages

```

Is anyone else getting this error?

Is there a way around it?

---

### Post by styrofoam cup on 2007-10-08
I was getting the same error

> kdenlive:
  Depends: libfreetype6 (>=2.3.5) but 2.2.1-5ubuntu1.1 is to be installed


what I did, and if you do it is UP TO YOU !!!

added a gutsy main to my sources list (currently using fiesty 4.07) and reload the package list. a new libfree6 was there. I installed it and some other files came with it too. about 9MB. I then removed the gutsy main and reload packages again. Then install kdenlive. It is working, I just have to work out how to use it right.

Hope this is some help to you.

If I have done something really, really bad please post here so someone does not follow my mistakes.


:KS

---

### Post by Dave M G on 2007-10-08
Styrofoam Cup,

Nice suggestion! I added the Gutsy repository, got the libfreetype6 package and its dependencies, then installed Kdenlive with no problems. Thanks for that.

Oddly enough, in the "About Kdenlive" interface, it says version 0.6svn. Is that what it says for you? I thought the version in the repositories was 0.5.

---

### Post by styrofoam cup on 2007-10-09
I dont have the other computer with kdenlive here to check but I did see the splash screen also shows 0.6svn. I got my kdenlive from [http://download.tuxfamily.org](http://download.tuxfamily.org). only libfree6 from gutsy.

I'm glad its working for you.

Just as a side note I did find that the render timeline would cut the output file short when saving to xvid and mpeg4 and something else too (in th medium quality tab). The only render option that worked properly was high quality tab or render to dvd.
Are you getting the same problem ???

Cheers,

:KS :KS :KS

---

### Post by Dave M G on 2007-10-09
I might be having a similar problem. I tried rendering an MPEG-2 video, but it only rendered from a point about 45 seconds to a minute in the timeline.

So the timeline is not fully rendering, although of course I can't say for sure if the causes or results are the same as what you're seeing.

Right now my biggest issue with Kdenlive is that it does not seem to be possible to make custom specifications for project settings. I'm asking about it on the Kdenlive forum:
[http://www.kdenlive.org/bbforum/viewtopic.php?f=11&t=288]("http://www.kdenlive.org/bbforum/viewtopic.php?f=11&t=288")

I recommend going to the Kdenlive forum, by the way. The main developer is active there and very responsive and friendly.
[Kdenlive Forum]("http://www.kdenlive.org/bbforum/")

---

### Post by styrofoam cup on 2007-10-09
Thanks for the tip,
might see you over in the forums!

cheers.
:KS :KS :KS

---

