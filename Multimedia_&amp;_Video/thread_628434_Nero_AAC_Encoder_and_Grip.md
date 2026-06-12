---
title: "Nero AAC Encoder and Grip"
date: 2007-12-01
forum: Multimedia &amp; Video
---

### Post by dj_penguin on 2007-12-01
I'm attemping to use Grip and the Nero AAC encoder to rip music from my CD collection.  I downloaded the latest Nero AAC encoders from Nero's website and saved them to my **/usr/bin** directory.  At first grip would rip the tracks and encode them, but these tracks were unplayable on both totem and Amarok, both said that the tracks were encoded incorrectly.  However, now grip won't even encode the tracks, it creates the directories but there are no files in them.  I would be greatful if anyone could help me get this working.  My grip settings are as follows;

**Encoder Executable:** /usr/bin/neroAacEnc
**Command Line:** -if %w -of %m -br 44100 -2pass
**File extension:** m4a
**File format:** /home/daniel/Music/%a/%d/%A-%d-%t-%n.%x

And in case you're wondering why I'm using AAC instead of Vorbis, it's because I have a 6th gen iPod.

Thanks in advance for any help.

---

### Post by hugmenot on 2007-12-01
What's the -br 44100 doing there? This is for the bitrate, and 44kb/s sounds a little low.

---

### Post by fenian on 2007-12-01
Did you make the nero files executable before you moed them to /usr/bin?
For the command line entry I use this and get really good quality but larger file sizes...
-if %w -of %m -br 256000 -2pass

---

### Post by hugmenot on 2007-12-01
now proposing using 256kbps with a good AAC encoder seems like overkill on the other hand, doesn't it?

---

### Post by dj_penguin on 2007-12-02
> **fenian said:**
> Did you make the nero files executable before you moed them to /usr/bin?
This was my problem, thanks a lot, that fixed all my problems.
> **hugmenot said:**
> What's the -br 44100 doing there? This is for the bitrate, and 44kb/s sounds a little low.
I just chucked some numbers in while I was getting it working, I'm now encoding at a target bit rate of 193000 that gives me an output bit rate of 192 kbps.  Thanks again guys :)

---

### Post by rootkit on 2007-12-04
I have this linux AAC+ encoder: [http://teknoraver.net/software/mp4tools/](http://teknoraver.net/software/mp4tools/)

Give it a try.

Packages are in this repository:

deb [http://ppa.launchpad.net/teknoraver/ubuntu](http://ppa.launchpad.net/teknoraver/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/teknoraver/ubuntu](http://ppa.launchpad.net/teknoraver/ubuntu) hardy main

---

### Post by rootkit on 2007-12-13
i have updated it and fixed a few bugs, please have a look

---

### Post by zietbukuel on 2007-12-19
> **rootkit said:**
> I have this linux AAC+ encoder: [http://teknoraver.campuslife.it/software/mp4tools/](http://teknoraver.campuslife.it/software/mp4tools/)

Give it a try.

Packages are in this repository:

deb [http://ppa.launchpad.net/teknoraver/ubuntu](http://ppa.launchpad.net/teknoraver/ubuntu) gutsy main
deb-src [http://ppa.launchpad.net/teknoraver/ubuntu](http://ppa.launchpad.net/teknoraver/ubuntu) gutsy main
I have AMD64 and I can't use these programs, it says it doesn't support Stereo for my Arch... :(

---

### Post by rootkit on 2007-12-20
> **zietbukuel said:**
> I have AMD64 and I can't use these programs, it says it doesn't support Stereo for my Arch... :(
yes, that's bad..
But if you compile it statically for i386 it will work for you too

---

### Post by ron999 on 2007-12-21
Hi

I've visited the mp4tools website and listened to the demonstration audio track (Time :guitar:).
It's encoded at 32Kbps but the sound quality is good.
(If I encode music at 32Kbps using  neroAacEnc it sounds terrible).

Please can you help me to install mp4tools on my system - Ubuntu 7.04 Feisty Fawn.

So far I've downloaded the three tar.gz archives from the website and unzipped them.
Now I have got three folders on my desktop:-
mp4tools-0.5.3
aaplusenc-0.12
amrenc

What do I have to do next?

---

### Post by rootkit on 2007-12-21
> **ron999 said:**
> Hi

I've visited the mp4tools website and listened to the demonstration audio track (Time :guitar:).
It's encoded at 32Kbps but the sound quality is good.
(If I encode music at 32Kbps using  neroAacEnc it sounds terrible).

Please can you help me to install mp4tools on my system - Ubuntu 7.04 Feisty Fawn.

So far I've downloaded the three tar.gz archives from the website and unzipped them.
Now I have got three folders on my desktop:-
mp4tools-0.5.3
aaplusenc-0.12
amrenc

What do I have to do next?
Why don't you install the ubuntu packages?

---

### Post by ron999 on 2007-12-21
Hi
Thanks for your reply.
The links that you gave in the earlier post say 'gutsy main'.
I'm running Feisty Fawn.
How do I install the Ubuntu packages?

---

### Post by rootkit on 2007-12-21
> **ron999 said:**
> Hi
Thanks for your reply.
The links that you gave in the earlier post say 'gutsy main'.
I'm running Feisty Fawn.
How do I install the Ubuntu packages?
download them by hand, then

```

dpkg -i aacplusenc*.deb mp4tools*.deb amrenc*.deb

```
then if you have dependency errors fix them with
```

apt-get -f install

```

---

### Post by ron999 on 2007-12-21
This is what happens:-
> ron@ron-desktop:~$ sudo dpkg -i aacplusenc*.deb mp4tools*.deb amrenc*.deb
dpkg: error processing aacplusenc*.deb (--install):
 cannot access archive: No such file or directory
dpkg: error processing mp4tools*.deb (--install):
 cannot access archive: No such file or directory
dpkg: error processing amrenc*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 aacplusenc*.deb
 mp4tools*.deb
 amrenc*.deb


---

### Post by rootkit on 2007-12-21
> **ron999 said:**
> This is what happens:-
Have you dowloaded those files?

[http://ppa.launchpad.net/teknoraver/ubuntu/pool/main/m/mp4tools/mp4tools_0.5.3_all.deb](http://ppa.launchpad.net/teknoraver/ubuntu/pool/main/m/mp4tools/mp4tools_0.5.3_all.deb)
[http://ppa.launchpad.net/teknoraver/ubuntu/pool/main/a/aacplusenc/aacplusenc_0.12_i386.deb](http://ppa.launchpad.net/teknoraver/ubuntu/pool/main/a/aacplusenc/aacplusenc_0.12_i386.deb)
[http://ppa.launchpad.net/teknoraver/ubuntu/pool/main/a/amrenc/amrenc_0.5_i386.deb](http://ppa.launchpad.net/teknoraver/ubuntu/pool/main/a/amrenc/amrenc_0.5_i386.deb)

---

### Post by ron999 on 2007-12-21
oK
I've just downloaded and run those 3 debs.
For mp4tools it says Error dependency not satisfiable amrenc
For the other two it says Error dependency not satisfiable libc6
(I've checked with Synaptic, 'libc6 GNU C Library:Shared libraries' is installed)

---

### Post by rootkit on 2007-12-21
> **ron999 said:**
> oK
I've just downloaded and run those 3 debs.
For mp4tools it says Error dependency not satisfiable amrenc
For the other two it says Error dependency not satisfiable libc6
(I've checked with Synaptic, 'libc6 GNU C Library:Shared libraries' is installed)
try this:
```

dpkg -i --force-all dpkg -i aacplusenc*.deb amrenc*.deb mp4tools*.deb
apt-get -f install

```

---

### Post by ron999 on 2007-12-21
This is the output when I enter the first line of your code:-
> ron@ron-desktop:~$ sudo dpkg -i --force-all dpkg -i aacplusenc*.deb amrenc*.deb mp4tools*.deb
dpkg: error processing dpkg (--install):
 cannot access archive: No such file or directory
dpkg: error processing -i (--install):
 cannot access archive: No such file or directory
dpkg: error processing aacplusenc*.deb (--install):
 cannot access archive: No such file or directory
dpkg: error processing amrenc*.deb (--install):
 cannot access archive: No such file or directory
dpkg: error processing mp4tools*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 dpkg
 -i
 aacplusenc*.deb
 amrenc*.deb
 mp4tools*.deb
ron@ron-desktop:~$ 


---

### Post by rootkit on 2007-12-21
> **ron999 said:**
> This is the output when I enter the first line of your code:-
sudo dpkg -i --force-all dpkg -i

"dpkg -i" given twice

also, you need the .deb files.
dpkg: error processing mp4tools*.deb (--install):
 cannot access archive: No such file or directory
If you don't have the archive what do you install???

---

### Post by ron999 on 2007-12-21
Hi
I don't understand what you mean.
Maybe I ought to wait until I have updated to Gutsy then try again.
Thanks

---

### Post by rootkit on 2007-12-21
> **ron999 said:**
> Hi
I don't understand what you mean.
Maybe I ought to wait until I have updated to Gutsy then try again.
Thanks
how can you install a .deb file without having it?
you do dpkg-i whatever.deb without having wathever.deb in your current dir

---

### Post by ron999 on 2007-12-21
Hi
I still don't understand you.
Those 3 debs are on my desktop.
What am I supposed to do with them?

---

### Post by rootkit on 2007-12-21
> **ron999 said:**
> Hi
I still don't understand you.
Those 3 debs are on my desktop.
What am I supposed to do with them?
```

cd ~/Desktop
sudo dpkg -i aacplusenc*.deb mp4tools*.deb amrenc*.deb
sudo apt-get -f install

```

you forgot to change dir

---

### Post by ron999 on 2007-12-21
Hi
I've done what you said.
But it's telling me that my libc6 is version 2.5 and needs to be >= 2.6-1 to install aacplusenc. And fftw3 isn't installed.
And it won't install mp4tools because aacplusenc isn't installed.
i've attached a printout.

---

### Post by rootkit on 2007-12-21
> **ron999 said:**
> Hi
I've done what you said.
But it's telling me that my libc6 is version 2.5 and needs to be >= 2.6-1 to install aacplusenc. And fftw3 isn't installed.
And it won't install mp4tools because aacplusenc isn't installed.
i've attached a printout.
mm. so you should consider upgrading to gutsy first

---

### Post by ron999 on 2007-12-21
> **rootkit said:**
> mm. so you should consider upgrading to gutsy first
Yes, OK, I'll leave it until then.
That 32Kbps audio track was very impressive though. Is it because your encoder is better than the nero one?

---

### Post by rootkit on 2007-12-21
> **ron999 said:**
> Yes, OK, I'll leave it until then.
That 32Kbps audio track was very impressive though. Is it because your encoder is better than the nero one?
Dunno, but i don't think so. I never compared it with nero, but nero is a professional encoder,
mine was taken from reference sources.
BTW quality is ever subjective so...

---

### Post by hugmenot on 2007-12-24
Why don't you just upload to Feisty too, then?

---

### Post by rootkit on 2007-12-24
> **hugmenot said:**
> Why don't you just upload to Feisty too, then?
There are still so many feisty users?

---

### Post by hugmenot on 2007-12-24
No, just to ease ron's dependency problems.

---

### Post by rootkit on 2007-12-24
> **hugmenot said:**
> No, just to ease ron's dependency problems.
the following is valid for every debian package:

```

wget http://ppa.launchpad.net/teknoraver/ubuntu/pool/main/a/aacplusenc/aacplusenc_0.12.{tar.gz,dsc}
dpkg-source -x aacplusenc_0.12.dsc
cd aacplusenc-0.12
dpkg-buildpackage -rfakeroot

```

and you will magically have the .deb package.

---

### Post by ron999 on 2007-12-24
Hi
Thanks for that rootkit.

I ran those lines of code.
The last one told me I hadn't got **fftw3-dev** installed. So I used Synaptic to install it.
When I ran the line again it was OK.
So now (I think) I have aacplusenc installed.

How do I use that encoder?
Do I use the command-line?
Is there a 'help' for the bitrate options?

---

### Post by ron999 on 2007-12-24
Ha, I've found the answer.
*************************************************************
* Enhanced aacPlus Encoder
* Build Dec 24 2007, 17:22:47
* Matteo Croce <rootkit85@yahoo.it>
*************************************************************


Usage:   /home/ron/aacplusenc-0.12/aacplusenc <source.wav> <destination.aac> <bitrate>

Use - as filename for stdin and/or stdout.

Example: /home/ron/aacplusenc-0.12/aacplusenc song.wav song.aac 32

:lolflag:

---

### Post by ron999 on 2007-12-24
Hi
I've got aacplusenc working now and I've made some comparisons.

At 32Kbps neroAacEnc is just tinny and squeaky, not listenable.
At 32Kbps aacplusenc is better than neroAacEnc at 64Kbps and is similar to lame mp3 at 128Kbps.

As you said, the quality is subjective. But I think that the 32Kbps aacplusenc is at least good enough for portable players and will need only a quarter of the storage space of 128Kbps mp3.

By the way, aacplusenc seems to only encode at 32Kbps, it won't accept bitrate settings of 64Kbps or 128Kbps. 
:guitar:

---

### Post by rootkit on 2007-12-24
> **ron999 said:**
> Hi
I've got aacplusenc working now and I've made some comparisons.

At 32Kbps neroAacEnc is just tinny and squeaky, not listenable.
At 32Kbps aacplusenc is better than neroAacEnc at 64Kbps and is similar to lame mp3 at 128Kbps.

As you said, the quality is subjective. But I think that the 32Kbps aacplusenc is at least good enough for portable players and will need only a quarter of the storage space of 128Kbps mp3.

By the way, aacplusenc seems to only encode at 32Kbps, it won't accept bitrate settings of 64Kbps or 128Kbps. 
:guitar:
AAC+ in general encodes from about 16 to 51kbit. This is valid for every AAC+ encoder, not only aacplusenc. For higher bitrates plain AAC is better and preferred

---

### Post by ron999 on 2007-12-24
OK, I understand what you say. The aac+ is deliberately used for low bitrates. Otherwise ordinary aac is used for higher bitrates. So when we tell aacplusenc 32, we are suggesting a VBR target.

One last thing - when the aac file is shown in the nautilus file browser it shows as an icon of a document (like a text file) and the description is given as 'aac document'. Why does Ubuntu not show it as a music file icon and give it a suitable description?

---

### Post by hugmenot on 2007-12-25
You have to wrap the .acc into a .mp4 (or .m4a)  container. Keeping them as .aac is not a good idea.

---

### Post by ron999 on 2007-12-25
> **hugmenot said:**
> You have to wrap the .acc into a .mp4 (or .m4a)  container..

How do I do that?
If I just rename them m4a or mp4 then the icon does change but VLC won't play them any more.

---

### Post by hugmenot on 2007-12-25
No, you have to wrap them with MP4Box or something.

---

### Post by ron999 on 2007-12-25
> **hugmenot said:**
> No, you have to wrap them with MP4Box or something.

Hi
I have MP4Box installed, but I don't know how to use it.
Does anyone know a command for MP4Box that will wrap an aac+ file in an mp4 wrapper?

VLC will do the job, but I would like to use a CL instruction instead of one-at-a-time with the VLC GUI.

8)

Edit I've got it now.
The command for MP4Box is:-
**MP4Box -add <audio.acc> <audio.mp4>**
:guitar:8):guitar:

---

### Post by rootkit on 2007-12-26
> **ron999 said:**
> 
Edit I've got it now.
The command for MP4Box is:-
**MP4Box -add <audio.acc> <audio.mp4>**
:guitar:8):guitar:
No that's the command for plain AAC.
for AAC+ you do:

MP4Box **-sbrx** -add <audio.aac> <audio.mp4>

and, you may want to don't include extra **** in mp4, so:

MP4Box **-new -sbrx -no-sys** -add <audio.aac> <audio.mp4>

---

### Post by rootkit on 2007-12-26
> **ron999 said:**
> OK, I understand what you say. The aac+ is deliberately used for low bitrates. Otherwise ordinary aac is used for higher bitrates.
True, you got it.

> **ron999 said:**
> 
So when we tell aacplusenc 32, we are suggesting a VBR target.

No, aacplusenc is always CBR

> **ron999 said:**
> 
One last thing - when the aac file is shown in the nautilus file browser it shows as an icon of a document (like a text file) and the description is given as 'aac document'. Why does Ubuntu not show it as a music file icon and give it a suitable description?
It's a gnome issue, just add a filetype association.
BTW wrapping AAC+ in MP4 is preferrable

---

### Post by ron999 on 2007-12-26
Thanks again rootkit

I've made the changes to my MP4Box command as you suggested. The files are slightly smaller now, I suppose that's the **-no-sys** option.

The results with this encoder are good, Nero can't touch it.

When I (eventually) upgrade to Gutsy I'll install the whole mp4tools package, but just the aac+ encoder is fine for now.
:):)

---

### Post by rootkit on 2007-12-26
```

#!/bin/sh
aacplusenc "$1" /tmp/$$.aac "$3"
MP4Box -new -no-sys -sbrx -add /tmp/$$.aac "$2"
rm -f /tmp/$$.aac

```

save this as /**usr/local/bin/mkaacplus** and you don't have to care.
If you want extra volume then do:
```

#!/bin/sh
normalize-audio --peak "$1"
aacplusenc "$1" /tmp/$$.aac "$3"
MP4Box -new -no-sys -sbrx -add /tmp/$$.aac "$2"
rm -f /tmp/$$.aac

```

---

### Post by ron999 on 2007-12-26
HI
That's convenient, doing the two jobs in one (encode and wrap).
When I save mkaacplus to the usr/local/bin folder, how do I use it?
How do I tell it which file to encode and wrap?

---

### Post by rootkit on 2007-12-26
> **ron999 said:**
> HI
When I save mkaacplus to the usr/local/bin folder, how do I use it?
How do I tell it which file to encode and wrap?
Sorry, it was:
```

#!/bin/sh
normalize-audio --peak "$1"
aacplusenc "$1" /tmp/$$.aac "$3"
MP4Box -new -no-sys -sbrx -add /tmp/$$.aac "$2"
rm -f /tmp/$$.aac

```
and the command is **mkaacplus input.wav output.mp4 32**

---

### Post by ron999 on 2007-12-26
> **rootkit said:**
> 
and the command is **mkaacplus input.wav output.mp4 32**

That's working great. I've added the command to 'ConvertIT' gui that I use.
:):)

---

### Post by ron999 on 2007-12-27
Hi
When I encode and wrap an audio file it ends up with it's MIME type as video/mp4 and Nautilus shows an icon for a movie reel and the description is MPEG-4 video.
Is there a way during the operation to set it's MIME type to audio/mp4 so that a music icon shows and the description is given as MPEG-4 audio instead?
I've read the man page for MP4Box and there is mention of 'Meta handling options'. 
Could one of these options be used here to do the job?

---

### Post by rootkit on 2007-12-27
> **ron999 said:**
> Hi
When I encode and wrap an audio file it ends up with it's MIME type as video/mp4 and Nautilus shows an icon for a movie reel and the description is MPEG-4 video.
Is there a way during the operation to set it's MIME type to audio/mp4 so that a music icon shows and the description is given as MPEG-4 audio instead?
I've read the man page for MP4Box and there is mention of 'Meta handling options'. 
Could one of these options be used here to do the job?
simple, use .mp4 for video and .m4a for audio

---

### Post by ron999 on 2007-12-27
Yes, that's done it.
The command now is:-
**mkaacplus input.wav output.m4a 32**
:cool::D

So, is that because Gnome has been told originally that if it sees mp4 then assume it's mp4/video, and if it sees m4a assume it's mp4/audio?

---

### Post by rootkit on 2007-12-28
> **ron999 said:**
> Yes, that's done it.
The command now is:-
**mkaacplus input.wav output.m4a 32**
:cool::D

So, is that because Gnome has been told originally that if it sees mp4 then assume it's mp4/video, and if it sees m4a assume it's mp4/audio?
> **ron999 said:**
> Yes, that's done it.
The command now is:-
**mkaacplus input.wav output.m4a 32**
:cool::D

So, is that because Gnome has been told originally that if it sees mp4 then assume it's mp4/video, and if it sees m4a assume it's mp4/audio?
This because ISO defined only extensions for MP4, that are MP4 for PC movies and 3GP for mobile ones.

So we, (apple users, gnome users, kde users, etc.) uses this hack to distinguish them.
Some stupid people (apple, sony) uses .m4a for audio and .m4v for video, ignoring that .m4v is the extension for "RAW MPEG4 ASP video frames (eg. DivX or XviD)"

Cheers,
Matteo

---

