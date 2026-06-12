---
title: "Videos problem"
date: 2009-12-11
forum: Mythbuntu
---

### Post by Ryan-M- on 2009-12-11
Hi, im having issues with the videos section of 9.10. 
I have my videos stored on a separate drive to the OS and have linked the videos folder to /var/lib/mythtv/videos ,i am not using storage groups for videos. All the videos show up ok and play fine initially, fanart etc but for reasons unknown to me it seems to "forget" where they are stored after a while, usually after disturbing the folder in some way. 
The result is im unable to play any video file until I remove the original path and then enter it again, all the fanart etc has to then be downloaded again !
Looking at the mythbacked I see,

 ERROR: LocalFilePath unable to find local path for 'holiday.avi
 RingBuffer::RingBuffer(): Failed to open remote file ()
 RingBuf() Error: Invalid file descriptor in 'safe_read()

The frontend shows,

 TV: StartPlayer(0, Watching Video, main) -- begin
 RingBuf(myth://Videos@127.0.0.1:6543//var/lib/mythtv/videos/holiday.avi) Warning: Peek() requested 2048 bytes, but only returning 0
 NVP::OpenFile(): Error, couldn't read file: myth://Videos@127.0.0.1:6543//var/lib/mythtv/videos/holiday.avi
 TV: StartPlayer(0, Watching Video, main) -- end error
 ScreenSaverX11Private: DPMS Deactivated 1

Any ideas ? Ive set the permissions of the folders to mythtv grp and user but this made no difference it looks like its not seeing the file size correctly and failing ?
Thanks all for a great distro, its just this is driving me up the wall, well this and something else but thats another post for another day !

Cheers,

Ryan

---

### Post by nickrout on 2009-12-11
> **Ryan-M- said:**
> 
 TV: StartPlayer(0, Watching Video, main) -- begin
 RingBuf(myth://Videos@127.0.0.1:6543//var/lib/mythtv/videos/holiday.avi) Warning: Peek() requested 2048 bytes, but only returning 0
 NVP::OpenFile(): Error, couldn't read file: myth://Videos@127.0.0.1:6543//var/lib/mythtv/videos/holiday.avi
 

this indicates you ARE using storage groups.

---

### Post by Ryan-M- on 2009-12-11
No im not using it for videos, initially I did but had problems playing back certain file types so I removed that storage group. Perhaps the database needs telling this ? 
You know the next question ! ;)

---

### Post by nickrout on 2009-12-11
myth certsinly thinks you are as it is trying to access the file through the myth:// protocol. Rescan your videos. Search the mythtvusers mailing list archive, this problem was dealt with there IIRC.

---

### Post by williammanda on 2009-12-11
I can say that using jamu that you will get errors that seem to show that you are using storage groups for videos when you are not. So ...just because you get a certain output in the frontend log doesn't mean you are.
I got the same output and I wasn't using storage groups...see this post...

[http://ubuntuforums.org/showthread.php?t=1318635]("http://ubuntuforums.org/showthread.php?t=1318635")

I have new problems where I need to use the same solution. Everyday my fanart disappears and I resolve it by using this solution. Even after re-installing mythtv for the second time.

---

### Post by Ryan-M- on 2009-12-12
Thanks for all your help, I'll try a few things and hopefully get it sorted. Might start by storing the video images etc on the same drive as the videos, as its sym linked at the moment.
Might try the 9.10 fixes too.

Cheers

---

