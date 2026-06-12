---
title: "ffmpeg conversion quality"
date: 2009-04-28
forum: Multimedia Software
---

### Post by Geffers on 2009-04-28
I have a .mov file which I would like to do a partial extraction from.

The video details are H.264/AVC

I issued the command ffmpeg -i wd.mov -ss 114 -t 588 output.mov

I ended up with the correct portion of movie file but the quality was degraded and shows as MPEG-4 video, I thought with the same extansion that it would extract the segment like for like, obviously I am wrong so what would I need to do?

I tried using WinFF which I have used previously but for any DVD type conversion I kept getting the error 'Unable to parse option value "trell" undefined constant or missing (  Invalid value '+trell' for options 'flags'.

Done a search for trell and no luck.

Geffers

---

### Post by lovinglinux on 2009-04-28
You could go to WinFF profile editor and copy the command for the profile you need and run it in the terminal.

---

### Post by Geffers on 2009-04-28
> **lovinglinux said:**
> You could go to WinFF profile editor and copy the command for the profile you need and run it in the terminal.

Tried that and got exactly the same error message re +trell

Bit puzzled as to why you thought this may work, I was under the impression WinFF was just a GUI for ffmpeg but I may be wrong.

Geffers

---

### Post by Geffers on 2009-04-28
> **Geffers said:**
> I have a .mov file which I would like to do a partial extraction from.

The video details are H.264/AVC

I issued the command ffmpeg -i wd.mov -ss 114 -t 588 output.mov

I ended up with the correct portion of movie file but the quality was degraded and shows as MPEG-4 video, I thought with the same extansion that it would extract the segment like for like, obviously I am wrong so what would I need to do?

I tried using WinFF which I have used previously but for any DVD type conversion I kept getting the error 'Unable to parse option value "trell" undefined constant or missing (  Invalid value '+trell' for options 'flags'.

Done a search for trell and no luck.

Geffers

Not sure what +trell is but read a wee bit more of the MAN pages and found that if I just output as -target dvd then I get good video quality.

I'm assuming then that DVD is best quality followed by DV and VCD.

Geffers

---

### Post by FakeOutdoorsman on 2009-04-28
Try this:
```
ffmpeg -ss 114 -t 588 -i wd.mov -acodec copy -vcodec copy output.mov
```
I changed *-t* and *-ss* to input file options so it seeks before decoding the input.  The *-acodec copy* and *-vcodec copy* options will copy the audio and video streams.  This prevents any need to re-encode.  It should create a usable H.264 file and works for me with mplayer, but I haven't tested any other players.  I'm not sure how they will handle a truncated H.264 video.

---

### Post by paul.gevers on 2009-04-29
> **Geffers said:**
> I tried using WinFF which I have used previously but for any DVD type conversion I kept getting the error 'Unable to parse option value "trell" undefined constant or missing (  Invalid value '+trell' for options 'flags'.

This means that the presets you are using are for an older version of ffmpeg. How did you install winff? Did you use the same version as your OS? 

From the upsteam [wiki:]("http://code.google.com/p/winff/wiki/InstallPresetsxml")

Unfortunately different versions of ffmpeg have different parameters (see the [forum]("http://www.biggmatt.com/forums/index.php?topic=49.0") for an explanation). Therefore you can find several versions of the presets.xml file in the [download]("http://http://code.google.com/p/winff/downloads/list") section. Here is what to do with the new file.

Be aware that the procedure described here deletes your customized presets, so if you have added or edited the presets, you have to merge the new file manually.

If you just want to install for the current user, unzip/untar the downloaded file and copy the new presets.xml file to /home/user/.winff/

If you want to change the system wide presets.xml file, unzip/untar the downloaded file and copy the new presets.xml to /usr/share/winff/presets.xml. If you install to the system each user must delete /home/user/.winff/presets.xml for the new presets to take effect. This last procedure might prevent successful updates of later if you are using standard Debian/Ubuntu updates.

---

