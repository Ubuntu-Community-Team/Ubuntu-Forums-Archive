---
title: "Video seems to work, but blank screen"
date: 2006-06-17
forum: Multimedia &amp; Video
---

### Post by drippy on 2006-06-17
I have a strange problem where when I try to play a video, all I get is a blank screen.  There doesn't seem to be any noticeable errors.  I know I have the right codecs, I've tried playing multiple file types (mpg, avi, wmv) on multiple programs (mplayer, totem, gxine).  In all cases sound works fine, and the players don't report any errors but the video is blank.  
Also, when I view the files in the file browser, the "preview" thumbnail shows the files correctly:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=11349&stc=1&d=1150526476[/IMG]

I have a Radeon R200 QM [Radeon 9100], and I recently installed the fglrx driver, but then decided I didn't need it and rolled back to the Xorg driver.  I don't know if that has anything to do with it.  I've never tried playing video before now, so I can't say if that's what caused it.

I'm pretty new to linux, so any help is appreciated!

---

### Post by x64Jimbo on 2006-06-17
Check the player's options to see if it's trying to render through a nonexistent video driver. In Kaffeine, this is under Settings -> xine Engine Parameters

---

### Post by drippy on 2006-06-17
Ah, that did the trick.  Thanks a bunch!  I never would have thought of that..

---

### Post by pkunal on 2006-06-19
I have installed the Win32 codecs from the suggested web page of Mplayer's website.

I followed the instructions to install the codecs completely. After that I installed the Mplayer and Mencoder like Ubuntu Wiki suggested.

Now I can hear the audio of the WMV files but no Video.

I looked at this thread and suggestion is to adjust the Video Codec.

I chose: Win32* codecs and tried out but still no video.

Driver Chosen: xv
Codec Chosen: Win32/VfW & Win32/VfwEx none of these worked.

Restarted the player too. I am trying to see online WMV files.

Please help.

Thanks,
pkunal

---

