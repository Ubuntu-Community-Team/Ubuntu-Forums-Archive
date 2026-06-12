---
title: "A Real Puzzler"
date: 2009-11-22
forum: Multimedia Software
---

### Post by davidbw1 on 2009-11-22
I've got myself into a bit of a strange situation.  After running Computer Janitor, I suddenly stopped being able to watch DVDs.  
Here's the thing:  The DVD still shows up when I insert it.  I can still see its file contents.  If I mount the ISO of a DVD I copied onto my hard drive, that plays just fine.  When I try to open the DVD with VLC or Movie Player, the disk spins up, and then stops.  Nothing gets displayed.  Also: everything works hunky dory when I boot into windows.

I don't know what to do next.
Help?

---

### Post by andrew.46 on 2009-11-23
Hi davidbwl,

> **davidbw1 said:**
>   When I try to open the DVD with VLC or Movie Player, the disk spins up, and then stops.  Nothing gets displayed.

Could you play the dvd from the commandline as follows:

```
cvlc -v dvd://
```

and post the full command and full terminal output? This will give an indication if the problem has to do with encryption, video output etc.

All the best,

Andrew

---

### Post by davidbw1 on 2009-11-23
Andrew,
Thanks for the assistance!  VLC player opened, some strange boxes green and staticy boxes flashed on the screen and here's what I got on the terminal:

david@r-daneel:~$ cvlc -v dvd://
VLC media player 1.0.2 Goldeneye
[0x8167470] main demux warning: no access_demux module matching "file" could be loaded
[0x817b348] main interface error: no interface module matched "globalhotkeys,none"
[0x817b348] main interface error: no suitable interface module
[0x80d1140] main libvlc error: interface "globalhotkeys,none" initialization failed
[0x817b388] dummy interface: using the dummy interface module...
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Encrypted DVD support unavailable.
************************************************
**                                            **
**  No css library available. See             **
**  /usr/share/doc/libdvdread4/README.Debian  **
**  for more information.                     **
**                                            **
************************************************
libdvdnav: DVD Title: STARDUST_WS_AC
libdvdnav: DVD Serial Number: 373B92D2
libdvdnav: DVD Title (Alternative): STARDUST_WS_AC
libdvdnav: Unable to find map file '/home/david/.dvdnav/STARDUST_WS_AC.map'
libdvdnav: DVD disk reports itself with Region mask 0x00f60000. Regions: 1 4
[0x817c660] main input error: ES_OUT_RESET_PCR called
[0x817c660] main input error: ES_OUT_RESET_PCR called
[0x81bb380] main decoder warning: dts != current_pts (-151543)
[0x81bb380] main decoder warning: backward_pts != current_pts (-33367)
[0x81bb380] main decoder warning: dts != current_pts (-200204)
[0x81bb380] main decoder warning: backward_pts != current_pts (-50045)
[0x81d76f8] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000
[0x82aeb20] pulse audio output: No. of Audio Channels: 2
[0x82b9210] scaletempo audio filter warning: bad input or output format
[0x82b9210] main audio filter warning: no audio filter module matching "scaletempo" could be loaded
[0x82aeb20] main audio output warning: audio drift is too big (-128000), clearing out
[0x82aeb20] main audio output warning: mixer start isn't output start (-53760)
[0x81bb380] main decoder warning: backward_pts != current_pts (-33362)
[0x82aeb20] main audio output warning: audio drift is too big (-192000), clearing out
[0x82aeb20] main audio output warning: mixer start isn't output start (-76800)
[0x82aeb20] main audio output warning: buffer is 96000 in advance, triggering downsampling
[0x81bb380] main decoder warning: dts != current_pts (-200210)
[0x82aeb20] main audio output warning: audio drift is too big (-288146), clearing out
[0x82aeb20] main audio output warning: timing screwed, stopping resampling
[0x82aeb20] main audio output warning: mixer start isn't output start (-112128)
[0x82aeb20] main audio output warning: buffer is 95834 in advance, triggering downsampling
[0x81bb380] main decoder warning: dts != current_pts (-183520)
[0x817d900] dvdnav demux warning: cannot get next block (Error reading from DVD.)
[0x817c660] main input error: ES_OUT_RESET_PCR called
[0x817c660] main input error: ES_OUT_RESET_PCR called
[0x82d0e70] main decoder warning: dts != current_pts (-171999)
[0x82d0e70] main decoder warning: backward_pts != current_pts (-33366)
[0x82be900] a52 decoder: A/52 channels:6 samplerate:48000 bitrate:448000
[0x82aeb20] pulse audio output: No. of Audio Channels: 6
[0x82d0e70] libmpeg2 decoder error: invalid picture encountered
[0x82d0e70] main decoder warning: decoder synchro warning: pts != current_date (-250248)
[0x82d0e70] main decoder warning: dts != current_pts (-33373)
[0x81aab08] scaletempo audio filter warning: bad input or output format
[0x81aab08] main audio filter warning: no audio filter module matching "scaletempo" could be loaded
[0x82d0e70] main decoder warning: backward_pts != current_pts (16686)
[0x82d0e70] libmpeg2 decoder error: invalid picture encountered
[0x82aeb20] main audio output warning: audio drift is too big (-160000), clearing out
[0x82aeb20] main audio output warning: mixer start isn't output start (-198144)
[0x82d0e70] main decoder warning: backward_pts != current_pts (50053)
[0x82d0e70] libmpeg2 decoder error: invalid picture encountered
[0x82d0e70] libmpeg2 decoder error: invalid picture encountered
[0x82d0e70] libmpeg2 decoder error: invalid picture encountered
[0x82d0e70] libmpeg2 decoder error: invalid picture encountered
[0x82d0e70] libmpeg2 decoder error: invalid picture encountered
[0x82d0e70] libmpeg2 decoder error: invalid picture encountered
[0x82d0e70] libmpeg2 decoder error: invalid picture encountered
[0x82d0e70] libmpeg2 decoder error: invalid picture encountered
[0x82d0e70] libmpeg2 decoder error: invalid picture encountered
[0x82d0e70] libmpeg2 decoder error: invalid picture encountered
[0x82d0e70] libmpeg2 decoder error: invalid picture encountered
[0x82d0e70] libmpeg2 decoder error: invalid picture encountered
[0x82d0e70] libmpeg2 decoder error: invalid picture encountered
[0x82d0e70] libmpeg2 decoder error: invalid picture encountered
[0x82d0e70] libmpeg2 decoder error: invalid picture encountered
[0x82d0e70] libmpeg2 decoder error: invalid picture encountered
[0x82d0e70] libmpeg2 decoder error: invalid picture encountered
[0x82d0e70] libmpeg2 decoder error: invalid picture encountered
[0x82d0e70] libmpeg2 decoder error: invalid picture encountered
[0x82d0e70] libmpeg2 decoder error: invalid picture encountered
[0x82d0e70] libmpeg2 decoder error: invalid picture encountered
[0x82d0e70] libmpeg2 decoder error: invalid picture encountered
[0x82d0e70] libmpeg2 decoder error: invalid picture encountered
[0x82d0e70] libmpeg2 decoder error: invalid picture encountered
[0x82d0e70] libmpeg2 decoder error: invalid picture encountered
[0x82d0e70] libmpeg2 decoder error: invalid picture encountered
[0x82d0e70] libmpeg2 decoder error: invalid picture encountered
[0x82d0e70] libmpeg2 decoder error: invalid picture encountered
[0x82d0e70] libmpeg2 decoder error: invalid picture encountered
[0x82d0e70] libmpeg2 decoder error: invalid picture encountered
[0x82d0e70] libmpeg2 decoder error: invalid picture encountered
[0x82d0e70] libmpeg2 decoder error: invalid picture encountered
[0x82d0e70] libmpeg2 decoder error: invalid picture encountered
[0x82d0e70] libmpeg2 decoder error: invalid picture encountered
[0x82d0e70] libmpeg2 decoder error: invalid picture encountered
[0x82d0e70] libmpeg2 decoder error: invalid picture encountered
[0x82d0e70] libmpeg2 decoder error: invalid picture encountered
[0x82d0e70] libmpeg2 decoder error: invalid picture encountered
[0x82d0e70] libmpeg2 decoder error: invalid picture encountered
[0x82d0e70] libmpeg2 decoder error: invalid picture encountered
[0x82d0e70] libmpeg2 decoder error: invalid picture encountered
[0x82d0e70] libmpeg2 decoder error: invalid picture encountered
[0x82d0e70] libmpeg2 decoder error: invalid picture encountered
[0x82d0e70] libmpeg2 decoder error: invalid picture encountered
[0x82d0e70] libmpeg2 decoder error: invalid picture encountered
[0x82d0e70] libmpeg2 decoder error: invalid picture encountered
[0x82d0e70] libmpeg2 decoder error: invalid picture encountered
[0x82d0e70] libmpeg2 decoder error: invalid picture encountered
[0x82d0e70] libmpeg2 decoder error: invalid picture encountered
[0x82d0e70] libmpeg2 decoder error: invalid picture encountered
[0x82d0e70] libmpeg2 decoder error: invalid picture encountered
[0x82d0e70] libmpeg2 decoder error: invalid picture encountered
[0x82d0e70] libmpeg2 decoder error: invalid picture encountered
[0x82d0e70] libmpeg2 decoder error: invalid picture encountered
[0x82d0e70] libmpeg2 decoder error: invalid picture encountered
[0x81d8720] main video output warning: late picture skipped (2802173 > -567)
[0x82d0e70] main decoder warning: dts != current_pts (-216885)
[0x817d900] dvdnav demux warning: cannot get next block (Error reading from DVD.)

---

### Post by davidbw1 on 2009-11-23
...and this is what I get when I do the same with a DVD ISO I've mounted (it plays normally):

david@r-daneel:~$ cvlc -v /media/cdrom0
VLC media player 1.0.2 Goldeneye
[0x8655470] main demux warning: no access_demux module matching "file" could be loaded
[0x8669348] main interface error: no interface module matched "globalhotkeys,none"
[0x8669348] main interface error: no suitable interface module
[0x85bf140] main libvlc error: interface "globalhotkeys,none" initialization failed
[0x86693b0] dummy interface: using the dummy interface module...
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Encrypted DVD support unavailable.
************************************************
**                                            **
**  No css library available. See             **
**  /usr/share/doc/libdvdread4/README.Debian  **
**  for more information.                     **
**                                            **
************************************************
libdvdread: Attempting to use device /dev/loop0 mounted on /media/cdrom0 for CSS authentication
libdvdread: Could not open input: Permission denied
libdvdread: Can't open /dev/loop0 for reading
libdvdread: Device /dev/loop0 inaccessible, CSS authentication not available.
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/david/.dvdnav/.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
[0xb7400710] main input error: ES_OUT_RESET_PCR called
[0xb7400710] main input error: ES_OUT_RESET_PCR called
[0x86c6178] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000
[0x8681290] main decoder warning: dts != current_pts (-247265)
[0x8681290] main decoder warning: backward_pts != current_pts (-33368)
[0x879d490] pulse audio output: No. of Audio Channels: 2
[0x879e660] scaletempo audio filter warning: bad input or output format
[0x879e660] main audio filter warning: no audio filter module matching "scaletempo" could be loaded
^C[0x86652c8] signals interface error: Caught Interrupt signal, exiting...
[0x86c6fd8] main video output warning: late picture skipped (3456 > -462)
[0x8681290] main decoder warning: can't get output picture
[0x8681290] main decoder warning: can't get output picture

---

### Post by andrew.46 on 2009-11-23
Hi davidbw,

I suspect that this may be the problem:

```
libdvdread: Encrypted DVD support unavailable.
```

Could you try installing libdvdcss2 and then retrying? There are several ways of doing this but perhaps the easiest is to add the [Medibuntu Repository]("https://help.ubuntu.com/community/Medibuntu"):

```

sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get -q update && sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring && sudo apt-get -q update

```

and then install libdvdcss2:

```
sudo apt-get install libdvdcss2
```

and try the command again, hopefully this will kickstart your dvd :).

Andrew

---

### Post by davidbw1 on 2009-11-23
It worked perfectly.  Thanks Andrew!

---

### Post by andrew.46 on 2009-11-24
Hi davidbw1,

> **davidbw1 said:**
> It worked perfectly.  Thanks Andrew!

Excellent news :). There is also a script installed with libdvdread that downloads and installs libdvdcss2 but Medibuntu has a few extras that make it worthwhile to do it this way I think. Enjoy your movie!

Andrew

---

