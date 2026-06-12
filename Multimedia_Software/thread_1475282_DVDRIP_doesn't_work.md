---
title: "DVDRIP doesn't work"
date: 2010-05-06
forum: Multimedia Software
---

### Post by djmoore85 on 2010-05-06
Hey there, I am trying to back up some DVDs for an upcoming trip, but am having trouble getting dvdrip to work. Ran it in termianl, here is output I am getting: 

```
daniel@daniel-laptop2:~$ sudo dvdrip
[sudo] password for daniel: 
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing dvd://1.
libdvdread: Encrypted DVD support unavailable.
************************************************
**                                            **
**  No css library available. See             **
**  /usr/share/doc/libdvdread4/README.Debian  **
**  for more information.                     **
**                                            **
************************************************
There are 5 titles on this DVD.
There are 1 angles in this DVD title.
audio stream: 0 format: ac3 (stereo) language: en aid: 128.
audio stream: 1 format: ac3 (5.1) language: en aid: 129.
audio stream: 2 format: ac3 (stereo) language: es aid: 130.
audio stream: 3 format: ac3 (stereo) language: pt aid: 131.
audio stream: 4 format: ac3 (stereo) language: en aid: 132.
number of audio channels on disk: 5.
subtitle ( sid ): 0 language: en
subtitle ( sid ): 1 language: es
subtitle ( sid ): 2 language: pt
subtitle ( sid ): 3 language: zh
subtitle ( sid ): 4 language: ko
subtitle ( sid ): 5 language: th
number of subtitles on disk: 6


Exiting... (End of file)
Catched Callbacks Exception: Error executing command execflow tcprobe  -i /home/daniel/dvdrip-data/Pest/vob/001/ && echo EXECFLOW_OK:
EXEC_FLOW_JOB_PID=1677
libdvdread: Encrypted DVD support unavailable.
************************************************
**                                            **
**  No css library available. See             **
**  /usr/share/doc/libdvdread4/README.Debian  **
**  for more information.                     **
**                                            **
************************************************
libdvdread: Couldn't find device name.
libdvdnav:DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
[fileinfo.c] warning: [fileinfo.c:125] file read error: No such file or directory
[probe_ffmpeg.c] critical: unable to open '/home/daniel/dvdrip-data/Pest/vob/001/' (libavformat failure)
[tcprobe] critical: failed to probe source
 at /usr/share/perl5/Video/DVDRip/JobPlanner.pm line 377
daniel@daniel-laptop2:~$ sudo dvdrip
Catched Callbacks Exception: Error executing command execflow tcprobe  -i /home/daniel/dvdrip-data/Pest/vob/001/ && echo EXECFLOW_OK:
EXEC_FLOW_JOB_PID=2326
libdvdread: Encrypted DVD support unavailable.
************************************************
**                                            **
**  No css library available. See             **
**  /usr/share/doc/libdvdread4/README.Debian  **
**  for more information.                     **
**                                            **
************************************************
libdvdread: Couldn't find device name.
libdvdnav:DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
[fileinfo.c] warning: [fileinfo.c:125] file read error: No such file or directory
[probe_ffmpeg.c] critical: unable to open '/home/daniel/dvdrip-data/Pest/vob/001/' (libavformat failure)
[tcprobe] critical: failed to probe source
 at /usr/share/perl5/Video/DVDRip/JobPlanner.pm line 377
daniel@daniel-laptop2:~$ 
```

I know I probably don't need to run as sudo but I was thinkin maybe I didn't have permissions.

---

### Post by MS-Hater on 2010-05-06
you'll need [this]("http://download.videolan.org/pub/libdvdcss/1.2.9/deb/libdvdcss2_1.2.9-1_i386.deb") to break the encryption on the disc and make it readable. Theoretically, you SHOULD be able to pull the DVD as an ISO, mount and decrypt it later when you're ripping the video to a playable file (I know that's what you're trying to do, don't even bother denying it), but I'm yet to see such in ANY OS.

---

### Post by mc4man on 2010-05-06
I'd say it's trying to tell you something..
> 
************************************************
**                                            **
**  No css library available. See             **
**  /usr/share/doc/libdvdread4/README.Debian  **
**  for more information.                     **
**                                  

run this in terminal
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

---

### Post by djmoore85 on 2010-05-07
Thank yall. Yes I am putting them into a playable format. Six month trip ahead of me and it's easier to take a HDD vs DVDs. And doh on my part for not reading the terminal output thoroughly. Once again, thank yall.

---

### Post by PouvoirTriforce on 2011-09-09
Thanks for your message. I was having the same error:
```
[fileinfo.c] warning: [fileinfo.c:125] file read error: No such file or directory
[probe_ffmpeg.c] critical: unable to open '/mnt/usb_disk/dvd-data/invictus/vob/001/' (libavformat failure)
[tcprobe] critical: failed to probe source
 at /usr/share/perl5/Video/DVDRip/JobPlanner.pm line 377
```

I've just installed the CSS decryption as you said, because it was already downloaded on my computer: 
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

Now, I can rip DVD!

Thanks again.

---

### Post by handy on 2011-09-09
There certainly would be a lot less posts in this sub-forum if new users read the two stickies at the beginning of it. #-o

I know, it takes a while to learn how to use a forum.

---

