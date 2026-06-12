---
title: "Smplayer Issue || 11.04"
date: 2011-06-25
forum: Multimedia Software
---

### Post by linuxyogi on 2011-06-25
Hi, 

Problem is when I open any file with Smplayer it won't play 


 ```
/usr/bin/mplayer -noquiet -nofs -nomouseinput -vc ffh264vdpau,ffmpeg12vdpau,ffwmv3vdpau,ffvc1vdpau, -afm hwac3 -sub-fuzziness 1 -identify -msglevel demux=6 -slave -vo vdpau -ao alsa -nokeepaspect -framedrop -nodr -double -input conf=/usr/share/smplayer/input.conf -stop-xscreensaver -wid 41943396 -monitorpixelaspect 1 -*** -embeddedfonts -***-line-spacing 0 -***-font-scale 1 -***-styles /home/user0/.config/smplayer/styles.*** -fontconfig -font Arial -subfont-autoscale 0 -subfont-osd-scale 20 -subfont-text-scale 20 -subcp ISO-8859-1 -subpos 100 -cache 1000 -osdlevel 0 -prefer-ipv4 -slices -channels 2 -softvol -softvol-max 153 -aspect 16:9 file:///home/user0/Videos/New%20HD%20Videos/video.mkv
  MPlayer 1.0rc4-4.5.2 (C) 2000-2010 MPlayer Team
 mplayer: could not connect to socket
 mplayer: No such file or directory
 Failed to open LIRC support. You will not be able to use your remote control.
  Playing file:///home/user0/Videos/New%20HD%20Videos/video.mkv.
 File not found: '/home/user0/Videos/New%20HD%20Videos/video.mkv'
 Failed to open file:///home/user0/Videos/New%20HD%20Videos/video.mkv.
   Exiting... (End of file)
 ID_EXIT=EOF
  
```
But when I drag n drop the same file to the Smplayer window playback starts without any issues.

---

### Post by andrew.46 on 2011-06-26
Is the problem corrected if you remove the spaces from the path to the file? Perhaps rename the offending folder something like:

```
/home/user0/Videos/**[COLOR="Red"]New_HD_Videos[/COLOR]**/video.mkv
```

---

### Post by linuxyogi on 2011-06-26
> **andrew.46 said:**
> Is the problem corrected if you remove the spaces from the path to the file? Perhaps rename the offending folder something like:

```
/home/user0/Videos/**[COLOR=Red]New_HD_Videos[/COLOR]**/video.mkv
```

Nope. Tried that ^. File not found.

---

### Post by andrew.46 on 2011-06-27
> **linuxyogi said:**
> Nope. Tried that ^. File not found.

Hmmm.... seems a little odd. 'File not found' usually means there is an error in the path. The problem you are facing I suspect is that because of the way the SMPlayer desktop files are set up they will often have a problem with spaces in either path to the file and/or in the filename itself. Perhaps drag the file to the Desktop and right-click + open with SMPlayer from this location?

---

### Post by linuxyogi on 2011-06-27
Tried copying the video file to Desktop & playing it from there. 

mplayer log shows different kinds of errors.

Please see attachment.

---

### Post by SeijiSensei on 2011-06-27
> ```
[h264_vdpau @ 0xb67b3e20]AVC: nal size 548161
[h264_vdpau @ 0xb67b3e20]no frame!
Error while decoding frame!
```


Looks like the high-profile H.264 problem that Andrew and I discussed over [here]("http://ubuntuforums.org/showpost.php?p=10848340&postcount=6").  

Also this error looks a bit dicey:

> ```
[format] Sample format big-endian AC3 not yet supported
```

You might not get any audio even if you fix the video problem.

As I suggested in the other thread, one option is to try mplayer2. (Andrew, any pointers to a good mplayer2 PPA?)

One other option might be to try viewing the video with the "xv" driver rather than VDPAU.  The error is thrown by the H.264/VDPAU decoder; maybe using xv or opengl as the video driver might avoid it.

---

### Post by linuxyogi on 2011-06-27
> **SeijiSensei said:**
> Looks like the high-profile H.264 problem that Andrew and I discussed over [here]("http://ubuntuforums.org/showpost.php?p=10848340&postcount=6").  

Also this error looks a bit dicey:



You might not get any audio even if you fix the video problem.

As I suggested in the other thread, one option is to try mplayer2. (Andrew, any pointers to a good mplayer2 PPA?)

One other option might be to try viewing the video with the "xv" driver rather than VDPAU.  The error is thrown by the H.264/VDPAU decoder; maybe using xv or opengl as the video driver might avoid it.

I am playing these files with vlc ATM. 

Let's hope mplayer2 gets included in the Ubuntu repos soon.

But the file permission problem is still a mystery.

---

### Post by andrew.46 on 2011-06-28
> **SeijiSensei said:**
> (Andrew, any pointers to a good mplayer2 PPA?)

I will have to admit that I don't normally use PPAs but I have heard of that a gentleman known as Ripps has a PPA with MPLayer2, but I have not chased this up as yet....

---

### Post by beew on 2011-06-28
> **SeijiSensei said:**
> 

(Andrew, any pointers to a good mplayer2 PPA?)
.

[https://launchpad.net/~ripps818/+archive/coreavc]("https://launchpad.net/%7Eripps818/+archive/coreavc")

or

[https://launchpad.net/~ed10vi86/+archive/tst]("https://launchpad.net/%7Eed10vi86/+archive/tst")

The mplayer (actually mplayer2) from both are the same build by Ripps.

---

### Post by SeijiSensei on 2011-06-28
> **beew said:**
> [https://launchpad.net/~ripps818/+archive/coreavc]("https://launchpad.net/%7Eripps818/+archive/coreavc")

or

[https://launchpad.net/~ed10vi86/+archive/tst]("https://launchpad.net/%7Eed10vi86/+archive/tst")

The mplayer (actually mplayer2) from both are the same build by Ripps.

The first of these requires using CoreAVC through wine.  I wouldn't suggest that to anyone over native mplayer.  A solution that requires running some Windows code in wine isn't a solution for people like me who don't run wine and don't intend to.  (I'd rather just use VirtualBox with a Windows guest.) The second PPA is called "Testing PPA".  While it has an mplayer2 build, I don't know how trustworthy it is.

I wish the mplayer2 devs would maintain their own PPA with a well-tested and well-supported release.  Until then, I'm sticking to building from source.  If you're not deterred from compiling, this is a fine solution with no additional overhead like CoreAVC.

---

### Post by beew on 2011-06-28
> **SeijiSensei said:**
> The first of these requires using CoreAVC through wine.  I wouldn't suggest that to anyone over native mplayer.  A solution that requires running some Windows code in wine isn't a solution for people like me who don't run wine and don't intend to.  (I'd rather just use VirtualBox with a Windows guest.) The second PPA is called "Testing PPA".  While it has an mplayer2 build, I don't know how trustworthy it is.

I wish the mplayer2 devs would maintain their own PPA with a well-tested and well-supported release.  Until then, I'm sticking to building from source.  If you're not deterred from compiling, this is a fine solution with no additional overhead like CoreAVC.

No, it doesn't require coreavc, it just says you *could* install coreavc if you want to but it doesn't say you have to. Installing coreavc would involve some extra work and components. 

I have been using just the mplayer for quite a while without coreavc (I didn't even have WINE) If you don't want coreavc just don't install dishowserver. It is an excellent player, works well with all gui front ends and gets updated regularly. It is a lot better than stock Mplayer. I have never encountered a problem. I think this ppa should really gets more publicity (The MOTU mplayer PPA is rather mediocre, but it has a lot of recommendations)

The second one's mplayer build is exactly the same as the first one, it is from the first ppa. There are some "testing" stuffs but you don't need to install them, I do recommend the gnome-mplayer though if you are using 0.922 in Maverick because it is broken.

The only problem with mplayer2 is with streaming because it has some conflicts with  gnome-mplayer's handling of pausing and starting,--see Mplayer2's FAQ for the explanation. So I actually ended up compiling mplayer2 so I have both mplayer and mplayer2 (with different paths and different names) I use mplayer2 to play local files (with Umplayer as front end) and mplayer for streaming, it turns out to work quite well.

---

### Post by no2498 on 2011-06-28
win ff loads a 264 file type

---

### Post by linuxyogi on 2011-07-07
**(S)mplayer filename ****Issue**** issue solved **

Follow the instructions in this post [COLOR=Red][here]("http://ubuntuforums.org/showpost.php?p=3646653&postcount=3").[/COLOR]

If you are having this issue with  Smplayer, modify the Smplayer desktop configuration (instead of mplayer) 

file at /usr/share/applications.

---

