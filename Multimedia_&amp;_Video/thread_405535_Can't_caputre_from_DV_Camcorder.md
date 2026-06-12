---
title: "Can't caputre from DV Camcorder"
date: 2007-04-09
forum: Multimedia &amp; Video
---

### Post by scott_g on 2007-04-09
Hi,

I'm trying to capture video from my Sony Handycam Mini DV camcorder (DCR-HC21 NTSC), using Kino (or another program if suggested).  I think I have all the correct libraries etc installed.  Kino tries to capture, but times out when it does not get any input from the camcorder.  I've tried to play the device through vlc, yet it does not recognize the device either.  I have also tried dvgrab directly, and it says:

```

Error: no camera exists

```

lsmod | grep 1394 says:
```

dv1394                 22104  0 
raw1394                30584  0 
video1394              20184  0 
ohci1394               37040  2 dv1394,video1394
ieee1394              306104  5 sbp2,dv1394,raw1394,video1394,ohci1394

```

Anyone have any other ideas?

Thanks a lot in advance,
Scott G

---

### Post by scott_g on 2007-04-10
D'oh!!!!

Problem solved.  Firewire cable had come unplugged on the back of the computer.

Sorry for the wasted post.

Scott G.

---

### Post by nim278 on 2007-04-12
Same problem, but the cable is definitely connected. Any ideas?

---

### Post by zerosystem on 2007-04-13
Faulty cable? Device not mounted?

---

### Post by cd-r80 on 2007-04-13
Automatic kernel-image update made problems for me. I went back to orig. installed & everything  started to work. Try other port? Using Kino now.

---

### Post by nim278 on 2007-04-13
I tried another cable and same problem..

What do you mean by "Device not mounted?" .. the modules are loaded, camcorder plugged in and turned on.. what else would I need to do? How do I mount the device?

My motherboard only has one Firewire port so I cannot try another, though it appears to be working fine based on any other way I have to tell (e.g. 'lspci', etc.)

---

### Post by Gruelius on 2007-04-17
Ive got the same issue kinda. I had to change the raw1394 group from disk to video which creates security issues however it fixed the problem for me. It would detect and controll my camera however i couldnt preview or capture any video, i just saw blank.

Anyone else got ideas?

---

### Post by bayvista on 2007-04-30
I have a Canon MV630i camcorder. Kino does not recognize and says " No AV/C compliant camera connected or not switched on"

Any ideas on this one?

---

### Post by McIntoshMXLuver on 2007-05-09
Perhaps your capture card is not compatoble with the PC or with the video cam. Have it double checked.



_________________
Cali
[McIntosh MX135 Audio/Video Control Center](http://www.who-sells-it.com/cy/mcintosh-laboratory-inc-1500/mx135-audio-video-control-center-5967.html)  -  Download the MX135 Audio/Video Control Center Catalog by McIntosh Laboratory, Inc.

---

### Post by bayvista on 2007-05-10
Thanks,

I'm using a standard Firewire card.

---

### Post by alex789 on 2007-05-10
this may not work on ubuntu, but did for kino problems on a pretty pure debian machine at work. 

chmod 666 /dev/raw1394

being new to ubuntu, i guess that this would probably need to be prefaced by sudo.

If this works, you then need to change the ownership of the group with 

addgroup user disk

and that should fix the problem

---

### Post by sebos69 on 2007-07-02
Hi,

I have the same problem with a panasonic digital camcorder. The modules are loaded correctly, but no device is detected, neither by kino nor dvgrab.

is there a way to see if the camcorder was detected by the kernel? dmesg didn't show anything.


Thanks

---

### Post by SeattleUser on 2007-07-02
Did you press the play button on the camera?  Kino also tells me that I have no compliant camcorder attached, but it does capture 1394 input when I press the play button manually.  Kino can control some camcorders directly, but not all of them.  I have a Sharp camcoder.

---

### Post by sebos69 on 2007-07-02
> **SeattleUser said:**
> Did you press the play button on the camera?  Kino also tells me that I have no compliant camcorder attached, but it does capture 1394 input when I press the play button manually.  Kino can control some camcorders directly, but not all of them.  I have a Sharp camcoder.


yep, I did all of this. I also tried gscanbus to scan for IEEE1394 devices. It keeps writing this message : 
Error while reading from IEEE1394: : Resource temporarily unavailable
Error while reading from IEEE1394: : Resource temporarily unavailable
Error while reading from IEEE1394: : Resource temporarily unavailable
Error while reading from IEEE1394: : Resource temporarily unavailable

when I activate the connection on the camcorder.

---

### Post by Gruelius on 2007-07-02
From memory you have to change the access rights of raw1394 and add yourself to the disk group which is a security vulnerability but the only way to do it atm i think.

---

### Post by SeattleUser on 2007-07-02
I just checked out my system.  I see /dev/dv1394/0 is in group video and I belong to that group as a regular user.  Is that what you're referring to?  I have no problem reading or writing to the 1394 connection.

---

### Post by Brian96 on 2007-07-04
> **SeattleUser said:**
> I just checked out my system.  I see /dev/dv1394/0 is in group video and I belong to that group as a regular user.  Is that what you're referring to?  I have no problem reading or writing to the 1394 connection.

I have the same problem described above. However, my 1394 shows root and disk having r/w access. I am a member of the video group, but video is not listed with 1394. Based on what you are saying it should work if I add video (and/or remove disk?) to the 1394 permissions? What is the safest way to do this? (I've run into trouble changing permissions before.)

---

### Post by Brian96 on 2007-07-04
Apparently this is largely a "cosmetic" problem. I just captured by clicking "capture" and manually pushing play on my DV camera. Everything seems to work so far, except no real preview.

I found advice on another thread to start kino with the command "gksu kino" to run as root. That method does allow for the AV/C controls to be enabled, but it also seems to save the capture file with root privileges. I'm not sure this will be a problem in the future, but I don't want to run the risk. So I am running kino without root privileges and just starting the capture manually.

---

### Post by SeattleUser on 2007-07-04
Your post got me to thinking.  I hooked up my camcorder and turned it on.  Sure enough dv1394 and raw1394 showed up in /dev.  dv1394 was group video and raw1394 was group disk.  I ran the chgrp command as root to change raw1394 to video and now I can control the camera from Kino!

The exact command is
sudo chgrp video /dev/raw1394

---

### Post by steevc on 2007-07-07
I've just got my camera working. I had a /dev/raw1394, but the camera was not recognised in kino until I did a chmod 666 on it. I could still not control the camera or capture until I ran kino with kdesu. I tried the chgrp to video, of which I am a member, but could still not capture when running as me.

I'm running a test capture now. Kino is creating lots of files in various sizes. The video is not showing in Kino, but I find that it refreshes the current frame when I switch back to it from Firefox.

I shall experiment further. I have loads of DV tapes that need editing. My aim is to get them onto DVD, although I may settle for Divx to keep the number of disks down as my DVD player can handle it. It's only home movies.

---

### Post by Brian96 on 2007-07-07
> **steevc said:**
> I've just got my camera working. I had a /dev/raw1394, but the camera was not recognised in kino until I did a chmod 666 on it. I could still not control the camera or capture until I ran kino with kdesu. I tried the chgrp to video, of which I am a member, but could still not capture when running as me.

I'm running a test capture now. Kino is creating lots of files in various sizes. The video is not showing in Kino, but I find that it refreshes the current frame when I switch back to it from Firefox.

I shall experiment further. I have loads of DV tapes that need editing. My aim is to get them onto DVD, although I may settle for Divx to keep the number of disks down as my DVD player can handle it. It's only home movies.

As for the files Kino creates: I think the defaults have it auto-split files, so you may want to check those settings. Also, I think it defaults to not show preview during capture.

I got it working okay without changing permissions. The only problem I have is that the mpeg it exported is more than 1/3 smaller than the mpeg created by Sonic (I captured the same DV tape twice, once in WinXP/Sonic, once in Kino). I'm assuming that there is also a commensurate loss in quality. Anybody know why the two programs would encode the mpeg2 files so differently?

---

### Post by steevc on 2007-07-07
> **Brian96 said:**
> As for the files Kino creates: I think the defaults have it auto-split files, so you may want to check those settings. Also, I think it defaults to not show preview during capture.

I got it working okay without changing permissions. The only problem I have is that the mpeg it exported is more than 1/3 smaller than the mpeg created by Sonic (I captured the same DV tape twice, once in WinXP/Sonic, once in Kino). I'm assuming that there is also a commensurate loss in quality. Anybody know why the two programs would encode the mpeg2 files so differently?

I worked out that it was splitting by scene. Not sure if I need it to split or not.

I ended up with 3GB for about 15 minutes of PAL video. That's in the RAW format. How many minutes/GB did you get?

Next issue is that I have run an export in Xvid/High Quality. It runs for about 8 minutes, but I can't see that it has generated any file. There is none where I told it to export.

---

### Post by Brian96 on 2007-07-07
> **steevc said:**
> I worked out that it was splitting by scene. Not sure if I need it to split or not.

I ended up with 3GB for about 15 minutes of PAL video. That's in the RAW format. How many minutes/GB did you get?

Next issue is that I have run an export in Xvid/High Quality. It runs for about 8 minutes, but I can't see that it has generated any file. There is none where I told it to export.

The original capture created about 12.3GB for 62 minutes. When I exported to qdvdauthor DVD format it created a 2.3GB "mpeg" file. When I captured the same DV tape in Sonic and then exported to "high quality mpeg" it created a 3.6GB ".mpg" file (NTSC).

I've been playing around with several apps in both Windows and Ubuntu. The easiest to use is an old oem copy of Ulead DVD Movie Factory 2.0, but it won't let me create Chinese menus. Sonic MyDVD (also oem) is also pretty easy to use, but it won't let me auto-create 5:00 chapters (it only wants to use time stamps or scene changes or both, so I end up with like 30 scenes instead of 12 like in Ulead). Also, Sonic adds a "SONIC" graphic to the DVD, 

Kino and qdvdauthor are very powerful, but I wonder about the quality of the mpeg file Kino creates and qdvdauthor crashes every time I try to do anything (even after upgrading to 1.0.0). Also, Kino takes FOREVER to encode from Raw DV to mpeg. DVDStyler 1.5 is stable and simple to use, but I can't figure out how to do everything I want in it.

Sorry for the long post. That is where I am at. I don't mind switching back and forth. For example, I am currently messing around with creating a DVD in Ubuntu from the mpg file created in Sonic in Windows. I just wish I could get everything in I want in one spot (more or less). I think that qdvdauthor may be that "one spot," but it is SOOO unstable (at least for me).

---

### Post by steevc on 2007-07-09
I still wish I could get any output at all. I've run Xvid exports to various locations, but never get a file. I can see that kino is running

```
mencoder - -quiet -cache 8192 -aspect 4:3 -xy 640 -zoom -vf harddup,pp=ci,scale -ovc xvid -oac mp3lame -lameopts preset=standard -xvidencopts fixed_quant=2:qpel -o /data/video/yy.avi
```

That's the right output file, and it runs for a few minutes, but checking with lsof shows no file of that name being open.

Any ideas?

Update:Running kino from the command line I see the same sort of messages as this person

[http://ubuntuforums.org/showpost.php?p=2855440&postcount=3](http://ubuntuforums.org/showpost.php?p=2855440&postcount=3)

---

