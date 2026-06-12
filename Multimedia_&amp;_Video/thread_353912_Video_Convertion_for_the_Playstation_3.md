---
title: "Video Convertion for the Playstation 3"
date: 2007-02-05
forum: Multimedia &amp; Video
---

### Post by hanexar on 2007-02-05
I'd like to know how to convert different video file to the Playstation 3 format. There's already a few converter on windows, but I bored to switch back there only for converting files, and I'm pretty sure mencoder can do the job, I'm just not sure how.

Here's the file format the PS3 can read. 
[B]
H.264/MPEG-4 AVC Main Profile (AAC LC)[/B]

Actually, it is also supporting this one, but never got it to work...

**MPEG-4 SP (AAC LC)**

Any idea to do the job?

---

### Post by hanexar on 2007-02-12
Bumping this up in case someone with the answer miss the thread ;)

---

### Post by Ciego on 2007-02-14
Are you trying to play videos from the XMB or from within Linux on the PS3?

---

### Post by hanexar on 2007-02-14
I'm trying to play then from the game OS. I've been using PS3 Converter or something like that on Windows, but it bugs me to turn windows on only to convert movies when I'm pretty sure that mencoder can do the job. I just can't find how.

---

### Post by Ciego on 2007-02-14
I have not found any converters for the PS3 specifically but I have a hunch that the PSP converters will work for the PS3.  I will have to look into that.

---

### Post by hanexar on 2007-02-14
I think it is the same file format, but PS3 support higher definition. 

Btw, nice HowTo. I'll try to install ubuntu on the PS3 when time will permit it. I currently have YellowDog, but I'm not satisfied at all... Especially because I can't get my pppoe to work so it is quite pointless. I hope I won't have the same problem with Ubuntu ;)

---

### Post by Ciego on 2007-02-15
> **hanexar said:**
> I think it is the same file format, but PS3 support higher definition. 

Yeah ... I used to mess around with the PSP before I got my PS3 so I will have to try one of those programs.  Maybe one of them will let you change the resolution.
> 
Btw, nice HowTo.
Thanks ... I hope it helps you with your installation.

---

### Post by hanexar on 2007-02-15
> **Ciego said:**
> Yeah ... I used to mess around with the PSP before I got my PS3 so I will have to try one of those programs.  Maybe one of them will let you change the resolution.

If you point me to some of those converter for PSP, I'll make some test too.

---

### Post by Ciego on 2007-02-15
I pulled this straight off of the PS3 wiki at qj.net (very good site for PSP/PS3 hacking)


Here is a link to the wiki 
[[INDENT][COLOR="DarkOrange"]http://ps3wiki.qj.net/index.php/Main_Page[/COLOR][/INDENT]]("http://ps3wiki.qj.net/index.php/Main_Page")
 Linux Users

[I]> pspvc and why you should install it

The best tool I have found for converting videos for play on the PSP easily is called pspvc. It is an open source, GTK-based GUI program for converting video for the PSP; you can download it here: [http://pspvc.sourceforge.net/](http://pspvc.sourceforge.net/)

The problem with pspvc for converting video for the PS3 is that pspvc assumes you want the screen resolution of the PSP. Unfortunately, this means that while you *can* use pspvc to convert videos for the PS3, the resolution is really low.

A great side-effect of installing pspvc is that it installs a version of ffmpeg that is able to convert video for the PS3 as well. Normally, this is a really painful and complicated process. Installing pspvc does this for you. One catch, though, is that the install scripts for pspvc are a little screwy and end up installing ffmpeg in a really weird path (they probably meant for it to install in /usr/share or...):

```
/share/pspvc/bin/ffmpeg 
```

Whether or not you choose to install pspvc or build ffmpeg yourself, the instructions below should allow you to convert video for playback on your psp3!

Converting video for use on a Standard Resolution (480i) TV

Source video is standard resolution

This is an easy conversion. Assuming the pspvc install path of ffmpeg, here's an example:

```
 /share/pspvc/bin/ffmpeg -y -i InputVideoFile.avi -title "Title Of Your Choosing Here" -bitexact    
 -vcodec xvid -s 640x480 -r 29.97 -b 1500 -aspect 4:3 -acodec aac -ac 2 -ar 24000 -ab 64 -muxvb 768
 OutputFileNameOfYourChoosingHere.mp4

```

Source video is in widescreen aspect ratio

If you use the example above on an input video that has a widescreen (16:9) aspect ratio rather than the standard aspect ratio (4:3) on the PS3, the video will appear stretched vertically and you won't be able to resize it using the display options on the PS3. The solution in the example below is to size the widescreen video down to 640x360 and adding 120 pixels of padding (60 top, 60 bottom) so the resulting video is 640x480 with letterboxing. Your video then will not be stretched! Again, assuming the pspvc install path of ffmpeg:

```
 /share/pspvc/bin/ffmpeg -y -i InputVideoFile.avi
 -title "Title of Your Choosing Here" -bitexact -vcodec xvid -s 640x360 -r 29.97 -b 1500 -aspect 16:9
 -padtop 60 -padbottom 60 -acodec aac -ac 2 -ar 24000 -ab 64 -muxvb 768
 OutputFileNameOfYourChoosingHere.mp4
```

Converting video for use on a High Definition TV

I don't actually have a High Definition TV or display, so I can't test out different ffmpeg settings. Hopefully someone who has one will fill this space in. :)[/I]

I have not been able to verify that this works yet but when/if i do, I will put a post up about it at PSUbuntu.com

---

### Post by hanexar on 2007-02-15
Just tried this, but the install script doesn't seem to do the job.

Just also tried to compile ffmpeg myself with a x264 support, without anymore success.

I'll check tomorrow for other Howto for PSP format conversion.

---

### Post by Marsolin on 2007-02-15
There are some Linux options available.  [PlayStation Portable Video Converter]("http://linuxappfinder.com/package/pspvc") and [Handbrake]("http://linuxappfinder.com/package/handbrake") are two that I'm aware of.

---

### Post by drews_blunted on 2007-03-07
has anyone found a good way to do this yet? The above did not work for me. And i am still looking for a way to convert my avi files to mp4

---

### Post by drews_blunted on 2007-03-09
Does anyone know if their will be a handbrake package made for ubuntu any time soon?

---

### Post by drews_blunted on 2007-03-19
just bumping this thread to see if anyone new in the community has any solutions to this problem, still looking for a way to convert my movies to mp4 or something playable on PS3.

---

### Post by Tridion2000 on 2007-05-03
Another bump to see if there is a solution for us Linux users.

---

### Post by Ciego on 2007-05-03
The new handbrake beta now supports PS3 video.

[http://psubuntu.com/2007/04/23/handbrake-085b1-released/](http://psubuntu.com/2007/04/23/handbrake-085b1-released/)

---

### Post by hanexar on 2007-05-03
There's the new version of handbrake that's supposed to do the job, but you need to compile it from source...  I haven't tried it yet... I kept booting my windows partition to convert video during the night :(

EDIT: ohhh Ciego beat me on that one... :(  Great site btw !

---

### Post by hanexar on 2007-05-03
Ciego, have you tried the beta version of handbrake? If so, what command did you use for converting video to PS3 format?

---

### Post by Ciego on 2007-05-03
> **hanexar said:**
> Ciego, have you tried the beta version of handbrake? If so, what command did you use for converting video to PS3 format?

I have not tried it yet ... haven't even booted up Ubuntu on the PS3 since Oblivion came out.  :)

---

### Post by Tridion2000 on 2007-05-03
But handbrake is only for converting DVDs. What about converting Divx etc.

---

### Post by 454redhawk on 2007-05-07
> **drews_blunted said:**
> has anyone found a good way to do this yet? The above did not work for me. And i am still looking for a way to convert my avi files to mp4


Avi2iPod

[http://www.kde-apps.org/content/show.php/Avi+2+iPod+%28mp4%29?content=56915](http://www.kde-apps.org/content/show.php/Avi+2+iPod+%28mp4%29?content=56915)

Requires kommander and ffmpeg

ffmpeg must be compiled with xvid support

If you need kommander
sudo apt-get install kommander

---

