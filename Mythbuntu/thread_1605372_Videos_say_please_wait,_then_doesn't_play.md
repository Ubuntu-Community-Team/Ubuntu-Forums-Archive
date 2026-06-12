---
title: "Videos say please wait, then doesn't play"
date: 2010-10-25
forum: Mythbuntu
---

### Post by CrusaderAD on 2010-10-25
I have avi files loaded and MythVideo successfully scanned and found them. When I play them on the front end, they go to a Please Wait... screen and then go back to the previous screen. Any ideas?

Also, will Mythbuntu automatically load artwork like elisa does?

---

### Post by LowSky on 2010-10-25
open a terminal type ```
mythfrontend
```
try to play an AVI.
exit when it fails. check the terminal for output on the failure.

for artwork and such
[http://www.mythtv.org/wiki/MythVideo#Metadata_Lookup](http://www.mythtv.org/wiki/MythVideo#Metadata_Lookup)

---

### Post by CrusaderAD on 2010-10-25
Ok, this is what terminal gave me:

> 2010-10-25 13:41:36.630 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/default-wide/video-ui.xml
2010-10-25 13:41:37.632 TV: Attempting to change from None to WatchingVideo
2010-10-25 13:41:38.173 RingBuf(myth://Videos@127.0.0.1:6543/Test video.avi) Warning: Peek() requested 2048 bytes, but only returning 0
2010-10-25 13:41:38.173 NVP::OpenFile(): Error, couldn't read file: myth://Videos@127.0.0.1:6543/Test video.avi
2010-10-25 13:41:47.381 Deleting UPnP client...


Any ideas?

---

### Post by tgm4883 on 2010-10-25
> **CerealCypher said:**
> Ok, this is what terminal gave me:



Any ideas?

Permissions maybe? Is the video located on your frontend? What directory is the video stored in? It might help to get backend logs from the same time.

---

### Post by LowSky on 2010-10-25
try changing the name of the frontend

> MythTV: Utilities / Setup; Setup; General; Database Configuration 2/2: "Use custom identifier for frontend preferences" is *not* a "friendly" name, it's more like a hostname. So *don't* use something stupid like "JP's Office" in that field!!!

[http://lists.netisland.net/archives/plug/plug-2007-10/msg00321.html](http://lists.netisland.net/archives/plug/plug-2007-10/msg00321.html)

---

### Post by CrusaderAD on 2010-10-25
@tgm4883 - Yep, it's on the front end. I tried both the /var/lib/mythtv/videos directory and /home/user/Videos directory, neither works... same result.

@LowSky - I'll give that a shot... hopefully it is that easy but it would shock me if a clean install had this sort of problem from the get go.

Maybe it has something to do with this "Videos@127.0.0.1:6543"? The dhcp ip leasing on my router doesn't use the 127.*.*.* variation... maybe that's it?

---

### Post by LowSky on 2010-10-25
> **CerealCypher said:**
> 
Maybe it has something to do with this "Videos@127.0.0.1:6543"? The dhcp ip leasing on my router doesn't use the 127.*.*.* variation... maybe that's it?

make sure the frontend uses the correct address to the backend. that most certainly could be the issue

---

### Post by CrusaderAD on 2010-10-25
Hm, I switched it to localhost and it still doesn't work.

---

### Post by tgm4883 on 2010-10-25
> **CerealCypher said:**
> Hm, I switched it to localhost and it still doesn't work.

Switch it to the actual machine IP of your private network. Not localhost/127.0.0.1

---

### Post by CrusaderAD on 2010-10-25
Tried that, not working. Here's what the backend log says:

#
2010-10-25 18:22:22.866 RingBuf(/home/myth/Videos//test.avi) Error: File exists but is not readable by MythTV!
#
2010-10-25 18:22:23.025 RingBuf(/home/myth/Videos//test.avi) Error: Invalid file descriptor in 'safe_read()'

---

### Post by LowSky on 2010-10-25
it might just be a simple codec issue.

log out of mythtv and if you using mythbuntu go to the mythbuntu control centre.. go to codecs and make sure its checked. if yes, try playing the video from VLC or another player like totem or mplayer.

---

### Post by CrusaderAD on 2010-10-25
Never mind guys. I'm throwing in the towel. I thought I could simply stream video files with myth but this is turning into too much of a chore. Moovida is extremely easy to install and use. Maybe I'll try it again in the future when the default settings in myth actually work. Thanks for the help!

---

### Post by chipppy on 2010-10-25
Good Morning

I had a similar problem in 10.04 with .vob file.  Would put up "please wait" then drop back to the selection page with a buffering error.  Found out this was a problem with the internal player.  Set to use mplayer instead (with all codecs loaded) and no problem.
I didnt have any problem with .avi in 10.04 though.
Out of interest upgraded to 10.10 now and using internal player again with both .avi, and .vob, and no problems.

cheers chipppy

---

### Post by tim_m99 on 2011-02-06
I solved this issue by changing the file permissions (to read & write) or ownership (to mythtv). I think 10.04 needs open permissions, sounds like this might be fixed in 10.10.

---

