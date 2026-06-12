---
title: "MythArchive configuration"
date: 2009-11-16
forum: Mythbuntu
---

### Post by brian_hayward on 2009-11-16
I just installed Mythbuntu 9.04 and i am using a separate partition to store recordings and other media on the same hard drive.  I'm also going to use this same partition as the Mytharchive temp directory.  I went through all the settings that would pertain to Mytharchive and changed them accordingly.  When i want to create a DVD from a recording, i get these error messages;

ERROR: Failed while running ffmpeg to re-encode video.
Command was ffmpeg -v 1 -i "/MythMedia/tivo/Modern Family - 2009-10-14 - 08:00 PM Wednesday.avi" -r ntsc -target dvd -b 4771k -s 720x480 -acodec ac3 -ab 192k -ac 2 -copyts -aspect 4:3 "/MythMedia/mytharchive/work/1/newfile2.mpg" -map 0:0 -map 0:1 
************************************************************

chmod: changing permissions of `/MythMedia/mytharchive/': Operation not permitted
Terminated

Any ideas as to why these errors are showing up would be greatly appreciated.  thanks.

---

### Post by seeker5528 on 2009-11-16
Did you install the updates?

Looks like there was a bug about this against Karmic before they decided to use 0.22: 

[https://bugs.launchpad.net/mythbuntu/+bug/251353](https://bugs.launchpad.net/mythbuntu/+bug/251353)

> I downloaded and installed Mythbuntu on July 15th. It was a fresh machine. There was a temp directory specified in in the settings (/var/lib/mytharchive/temp/), but the directory did not actually exist and I had to create it before MythArchive would work.

Later, Seeker

---

### Post by brian_hayward on 2009-11-17
Ok since my last post i figured out my permissions problem...apparently the solution was too obvious for me to figure it out...i changed the group permissions and everything worked fine.  


I also fixed the ffmpeg re-encoding error.  I copied the code that Mytharchive was trying to execute:
> 
ERROR: Failed while running [COLOR="Red"]ffmpeg to re-encode video.
Command was ffmpeg -v 1 -i "/MythMedia/tivo/<MyVideoHere>.avi" -r ntsc -target dvd -b 4771k -s 720x480 -acodec ac3 -ab 192k -ac 2 -copyts -aspect 4:3 "/MythMedia/mytharchive/work/1/newfile2.mpg" -map 0:0 -map 0:1[/COLOR]

I pasted that command into a terminal and got the following error:

> Seems stream 0 codec frame rate differs from container frame rate: 30000.00 (30000/1) -> 29.97 (30000/1001)
Input #0, avi, from '/MythMedia/tivo/<MyVideoHere>.avi':
  Duration: 00:30:00.98, start: 0.000000, bitrate: 979 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 640x480 [PAR 1:1 DAR 4:3], 29.97 tbr, 29.97 tbn, 30k tbc
    Stream #0.1: Audio: mp2, 48000 Hz, stereo, s16, 192 kb/s
Assuming NTSC for target.
Unknown encoder 'mpeg2video'

I did a quick search using the Google for [COLOR="Red"]Unknown encoder 'mpeg2video'[/COLOR] and i found a few threads in a Medibuntu bug tracking forum ([https://bugs.launchpad.net/medibuntu/+bug/269997]("https://bugs.launchpad.net/medibuntu/+bug/269997")).  There was talk of installing some unstripped libraries (libavcodec-unstripped-51, libavdevice-unstripped-52, and others), i did a search for the libraries in the synaptic package manager i and installed them and now it seems to work.

---

### Post by brian_hayward on 2009-11-18
Update #2:

Since my last post, i tried to create a dvd with a recorded show and i got this error message:

> drivestatus = ioctl(f,CDROM.CDROM_DRIVE_STATUS, 0)
IOError: [Errno 25] Inappropriate ioctl for device

any ideas?

---

