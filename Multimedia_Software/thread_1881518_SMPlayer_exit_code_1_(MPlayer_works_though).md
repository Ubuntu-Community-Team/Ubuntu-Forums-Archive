---
title: "SMPlayer exit code 1 (MPlayer works though)"
date: 2011-11-15
forum: Multimedia Software
---

### Post by Braindigger on 2011-11-15
While I can play all movie formats in MPlayer, since updating to 11.10 I cannot use SMPlayer.

I searched for hours before posting so I hope this is not redundant.

In SMPlayer, I get the following error when I try to open any movie from either internal hardrdrive:

MPlayer has finished unexpectedly. Exit Code: 1

 p, li { white-space: pre-wrap; }  /usr/bin/mplayer -noquiet -nofs -nomouseinput -vc ffh264vdpau,ffmpeg12vdpau,ffwmv3vdpau,ffvc1vdpau,ffodivxvdpau, -lavdopts threads=2 -sub-fuzziness 1 -identify -slave -vo vdpau -ao pulse -nokeepaspect -framedrop -autosync 100 -mc 0 -nodr -double -input nodefault-bindings:conf=/dev/null -stop-xscreensaver -wid 58720642 -monitorpixelaspect 1 -subcp enca:en:ISO-8859-1 -subcc -forcedsubsonly -vid 0 -aid 0 -subpos 100 -volume 100 -cache 2000 -osdlevel 0 -slices -channels 2 -af scaletempo,equalizer=0:0:0:0:0:0:0:0:0:0 /home/david/Videos/My Videos/30 Days of Night (2007).mkv
 
 /usr/bin/mplayer: Symbol `ff_codec_bmp_tags' has different size in shared object, consider re-linking
 The subcc option must be an integer: -forcedsubsonly
 Error parsing option on the command line: -subcc
 MPlayer SVN-r33713-4.6.1 (C) 2000-2011 MPlayer Team
 ID_EXIT=NONE
 

Thanks in advance for any and all help

---

### Post by andrew.46 on 2011-11-16
I do not really use SMPlayer but there is an error outlined there:

```
**[COLOR="Red"]-subcc [/COLOR]**-forcedsubsonly
```

which should be an integer. Have a look in the SMPlayer options and see if you have enabled: Subtitles --> Enable Closed Caption. Deselect if you have and see if that fixes anything... Perhaps also uncheck 'Remember all settings...' under Preferences --> General --> Media Settings and close and open SMPlayer.

---

### Post by Braindigger on 2011-11-17
> **andrew.46 said:**
> I do not really use SMPlayer but there is an error outlined there:

```
**[COLOR=Red]-subcc [/COLOR]**-forcedsubsonly
```which should be an integer. Have a look in the SMPlayer options and see if you have enabled: Subtitles --> Enable Closed Caption. Deselect if you have and see if that fixes anything... Perhaps also uncheck 'Remember all settings...' under Preferences --> General --> Media Settings and close and open SMPlayer.

Thanks so much. 

I was focused on the "ff_codec_bmp_tags' has different size in shared object, consider re-linking"

Thanks to your message I turned off the subtitling and the closed captioning under the "subtitles tab" (not in preferences) and it now works. Thanks!!!!!! :guitar:

This forum is awesome!

---

### Post by andrew.46 on 2011-11-17
Great news :).

---

