---
title: "Mythvideo DVD ISO Playback"
date: 2008-01-29
forum: Mythbuntu
---

### Post by jpgscca on 2008-01-29
Hi all,
I've searched the forums and the web for this and have seen similar issues but nothing conclusive. I recently upgraded from feisty to gutsy (mythbuntu) and have managed to get everything working except for dvd iso playback. I cannot get dvd iso playback to work in mythbuntu/gutsy whatsoever. When I shutdown the frontend, I can watch the videos just fine in VLC, but when mythfrontend is running the video is garbled. I've tried changing the default player from mplayer to VLC and get the same results. I'm starting to think this is some funky driver/resolution problem.

When I check the logs I can see playback starting and I get error the follow error messages:

[FONT="Lucida Console"]
[INDENT]
Playing /content/mythtv/videos/BABEL.iso.
MPEG-PS file format detected.
VIDEO:  MPEG2  720x480  (aspect 2)  29.970 fps  4587.2 kbps (573.4 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 480 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed : (
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
a52: CRC check failed!
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 448.0 kbit/29.17% (ratio: 56000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
a52: error at resampling
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 720x480 => 720x540 Planar YV12  [fs] [zoom]
a52: CRC check failed!
a52: error at resampling
a52: CRC check failed!
a52: error at resampling
a52: CRC check failed!
a52: CRC check failed!
a52: error at resampling
a52: CRC check failed!
a52: error at resampling
a52: CRC check failed!
a52: error at resampling[/INDENT][/FONT]

Am I reading this correctly and this is a resolution problem or something else? I

I have a geforce 7300 based card and  have tried the restricted drivers and have grabbed the latest drivers from nVidia and neither have solved this problem. If anybody can give me some ideas or point me in the right direction, it would be really appreciated.

--jpgscca

---

### Post by stdPikachu on 2008-01-29
The errors about A52 are probably a red herring, that's just the audio. Have you tried mounting the ISO and trying to play it through mplayer or xine? I think Kaffeine migh tbe able to play ISO's as well.
mount /path/to/image.iso /mnt/iso -t auto -o loop
That should get you the VIDEO_TS file visible in /mnt/iso.

What's the command line you use to launch VLC in MythVideo? And are you able to provide a screenshot of the garbledness?

---

### Post by jpgscca on 2008-01-29
Thanks for the response.

Right now I'm using the default mplayer settings that mythvideo uses: mplayer -fs -zoom -quiet -vo xv %s. I've seen posts talking about using gl versus xv and neither work for me. I did a little mplayer RTFM this morning and and will try the spp, scale stuff as the error message states.

I haven't tried to play the ISO from a mount, but I'll try that when I get home tonight, although I can mount the image and the filesystem looks okay (i.e. VIDEO_TS). I'll also try to get a screenshot and try kaffeine tonight.

---

### Post by newlinux on 2008-01-29
Have you tried using the Internal player to play ISOs?

---

### Post by gsrcrxsi on 2008-01-29
something that has messed me up a few times before (and recently) was not having the proprietary codecs installled. open up mythbuntu control center and make sure they are installed. 

you also might play around with your nvidia settings and playback settings in mythtv. the sync to VBlank and XvMC options have played havoc with my dvd iso playback in the past.

---

### Post by stdPikachu on 2008-01-29
> **jpgscca said:**
> Right now I'm using the default mplayer settings that mythvideo uses: mplayer -fs -zoom -quiet -vo xv %s. I've seen posts talking about using gl versus xv and neither work for me. I did a little mplayer RTFM this morning and and will try the spp, scale stuff as the error message states.

Not sure what mplayer calls it, but you might wanna try the XShm driver in xine/kaffeine, it's my usual fallback for when xv b0rks:

xine -pfhq --no-splash --video-driver xshm dvd:/%s

(IIRC, don't think I've ever played an ISO)

If that doesn't work I'd say it's definitely something more fundamental going wrong - since mplayer, xine and VLC all use different decoder backends, the problem can't be in the decoder. Unless you've had the most unlikely hard drive corruption ever ;)

---

### Post by jpgscca on 2008-01-29
stdPikachu, you are not going to believe this... things have just gone from bad to worse. Got home from work and there was a power failure. Hard drive corruption! Now mythfrontend just core dumps as does kaffeine. Seems like anything that starts with the letter k core dumps.... 

I'm going to have to put this on hold for a bit. Sorry guys and thanks for all the suggestions. I'll update the DVD ISO stuff when I figure out what got corrupted. re-installing is beginning to sound good.

---

### Post by stdPikachu on 2008-01-29
I swear I didn't mean to jinx it...!

It's possible, if you live somewhere with dodgy power, that you can get hard disk corruption (incidentally, this is why I don't like using XFS, I've found it quite intolerant of power failure in the past). Another possibility is bad RAM, which can always cause bizarre and unpredictable problems - before you try anything too drastic, try booting the memtest option in GRUB and let it loop through for a good few hours.

---

### Post by jpgscca on 2008-01-30
Great news! :biggrin: After discovering that Qtlib got hosed in the power failure and re-installing it, I'm back to normal. Anyway, we have a pretty good power company but I guess today wasn't my day. Anyway, now for the better news... I found the solution after doing one more search. From the archives there was a good example with mplayer and DVD ISOs: [http://ubuntuforums.org/archive/index.php/t-512698.html]("http://ubuntuforums.org/archive/index.php/t-512698.html")


[INDENT][FONT="Lucida Console"]mplayer dvd://1 -dvd-device /path/to/your/DVD/image.iso[/FONT][/INDENT]

From that example I was able to come up with this:
[INDENT]
[FONT="Lucida Console"]mplayer -fs -zoom -quiet -vo xv dvd://1 -dvd-device %s[/FONT][/INDENT]

I then went to the File Type settings under Video Settings and used this for ISO images. Also deselected "Use defatult player".

This did the trick. Now I can watch DVD ISOs. Go figure... I never had to configure this in Feisty so this really threw me for a loop when it didn't work in Gusty. Now I have to figure out why the Remote is not working when watching videos... but I'll spare everyone.

Thanks a lot for the advice and I hope this will help somebody else.

BTW... how do I mark this thread as answered? or do the modmins do that?

---

### Post by knipknup on 2010-10-23
alright, I know this is responding to an old post, but time is relative when addressing techno-geekery... :)

Anyway, I have several iso files (not vob) that I want to watch and am wondering if installing mythbuntu is the solution.  The iso files reside on an external HD running ubuntu and I'm happy to change the installation if it allows playback of the isos.  However, it is working well as a server now and don't want to dork it if it is a hopeless endeavor.

Thanks for all the help!

---

### Post by tgm4883 on 2010-10-23
> **knipknup said:**
> alright, I know this is responding to an old post, but time is relative when addressing techno-geekery... :)

Anyway, I have several iso files (not vob) that I want to watch and am wondering if installing mythbuntu is the solution.  The iso files reside on an external HD running ubuntu and I'm happy to change the installation if it allows playback of the isos.  However, it is working well as a server now and don't want to dork it if it is a hopeless endeavor.

Thanks for all the help!

Post a new thread. This doesn't have anything to do with the OP

---

### Post by murchball on 2010-10-24
ISOs work fine as long as you aren't using storage groups. This was fixed in .24. However, if you're not recording tv, something like XBMC might be a better solution.

---

### Post by sdredwingsfan on 2011-03-05
i know its an old thread but i'm on 10.10 w/nfs storage groups and cant play isos  doest that problem still exist?  is there any other work around?  I've already tried smb/cifs mounts, there's just too much data not to use a high capacity nas?  Thanks!

---

### Post by tgm4883 on 2011-03-05
> **sdredwingsfan said:**
> i know its an old thread but i'm on 10.10 w/nfs storage groups and cant play isos  doest that problem still exist?  is there any other work around?  I've already tried smb/cifs mounts, there's just too much data not to use a high capacity nas?  Thanks!

What issue?

---

