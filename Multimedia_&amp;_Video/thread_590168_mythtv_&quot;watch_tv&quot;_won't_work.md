---
title: "mythtv &quot;watch tv&quot; won't work"
date: 2007-10-24
forum: Multimedia &amp; Video
---

### Post by Robocoastie on 2007-10-24
Hi all, perhaps some of you could help. I've been trying to get MythTV to work to little avail.
Ubuntu Gutsy (7.10) x64, Hauppage PVR-150, I've run tests that confirm the tv card is working.
Intent: desktop/frontend/backend so I installed mythbuntu per the documentation site but it does nothing. clicking on mythbuntu-setup under System-Admin also does nothing.
2 SATA drives. /home is on the second drive (500GB). I want to record on /home/robocoastie/shared/Videos so any recordings can be shared with other pc's including my windows ones (the first hard disk is 80gb so I want recordings on the second one).


------------------Update---------------
Ok well I have it all working now except "watch tv." I no longer get the SQL error, and mythbuntu control centre works now thanks to a thread a found elsewhere that said the problem has to do with a bug in it when it comes to 64bit proc's. So when I installed the version that thread mentioned it worked. But now I get a blank screen when I try "Watch TV." 

Doing this: vlc pvr:// :pvr-device="/dev/video0" gets me a screen (Dr. Phil to be specific at this time) but no audio. So it sees the card at least. Any thoughts before I just give up and put the tv card in my windows box for recording on it instead of vice versa? (wanted to get away from the evil .dvr-ms).
---Update------
It's all working!!!!
How I solved this for anyone that runs into it as well:

1) followed steps in the wiki for troubleshooting which completely deleted mythtv, sql, and mythbuntu
2) reinstalled mythbuntu using the 64 bit version which fixes a bug in the version that's in the repo's currently (search forum for mythbuntu 64)
3) under capture card had to use mpeg2 capture card instead of vlc
4) had to set to us-cable instead of us-bdcast.

after those 4 changes it all works! I've noticed the quality is poor compared to Windows MCE 2005 and Vista MCE, probably Nvidia driver and PVR150 driver related as they've been optimized for MCE. But I don't care because I'd rather a recorder that records in anything but that proprietary dvr-ms!

---

### Post by Robocoastie on 2007-10-28
now it's not working again. exact error as before "can't connect to server" and before that it was working sometimes, then other times through up blue,white, and black snow screens, just completely unusable. I'm ready to pay someone to make it work seriously - anyone in Nebraska? anyone? -- edit/update--- now I have audio but video is all garbled in colored bands.

---

### Post by mwc on 2007-10-29
Are you running Compiz? in my experience compiz plays havoc with playback in Mythtv. I turn compiz off and all is good in the world of Mythtv again........Cheers

---

### Post by Robocoastie on 2007-10-29
aha! indeed I am. Bummer, so no 3d desktop then if I want to use the front-end?
--update---
Well disabling compiz let it work for a few minutes. Then another attempt to view tv or even play video resulted in an even worse garbled screen and no audio either. I give up, *nix is simply still junk for multimedia.

---

### Post by mwc on 2007-10-29
After switching off Compiz you need to reboot and Myth will playback fine, that's what worked for me and I've had no problems since on any of my machines. 

It was stupid to enable a technology like Compiz by default, it still has far too many issues with various app's creating problems where none need be. 

Linux distro's do themselves nothing but harm by doing this in main stream releases, if they want new users things need to work out of the box, no exceptions or conflicts. I don't have any Windows machines so i need to work through these things but I can see how someone coming from Windows may head straight back after encountering silly problems like this.

Linux does not have any problems with multimedia, some developers and packagers  just have no common sense.....rant over!

---

### Post by Robocoastie on 2007-10-30
yea you're right. It's just frustrating. Maybe I didn't turn compiz off properly anyway. What I did was went to System-Pref-Advanced Desktop Effects-Preferences- then unchecked "Enable integration into the desktop."

Maybe that's not how to disable compiz?

---

### Post by tiachopvutru on 2007-10-30
I'm not really sure if that is a wrong way or not, but I disable mine by going to System -> Preference -> Appearance -> Visual Effect Tab and select None. Both of them may be the right ways though.

---

### Post by Robocoastie on 2007-10-30
that worked! And it's simple to turn it back on or off (didn't have to restart). 

thanks so much!

Rob

---

### Post by mwc on 2007-10-30
I'm glad you got it sorted out, in my house the Mythtv box is king as far as my wife and 7 year old son are concerned, any problems are more than my life's worth, god forbid the little guy missed an episode of Ben10 or something!

---

### Post by Robocoastie on 2007-10-30
yea i hear ya there. We have pvr's from our cable company but I like to make cartoon compilations sometimes plus its nice to have another tuner/recorder. My daughter watches so many of her toons from the PVRs that she tries to fast-foreward commercials in livetv and gets frustrated when she realizes it doesn't work. That is until the commercial has some cool toy in it - which is why I to see how good its commercial detection and cutting is :)

thanks again! I think your tip here should be added to the troubleshooting section of the mythbuntu wiki.

Rob

---

### Post by Robocoastie on 2007-11-17
Ok, I've now turned the box I was going to use as a frontend only into back/front since I don't want to depart from compiz on my mainbox. (turned out that yes I had to restart whenever I switched compiz on/off which makes it impossible to use as a backend/desktop).

My question is that I've noticed video quality to well, to be frank suck compared to Win. Media Center. I don't expect it to match perfectly what that other app. with a MSFT million dollar budget but certainly it can do better than this. Is there any myth tweaks I'm missing by chance to improve it?

thanks!

Rig it's running on:
256MB Nvidia 6600 AGP/Haup. PVR-150 MCE tv capture card.
P4. 2 Ghz HT CPU Mythbuntu 7.10 32bit

---

### Post by mwc on 2007-11-17
My set up is very much like yours, after upgrading to Gutsy I turned of compiz and downgraded the Nvidia driver from 100.14.23 to 100.14.11 and have had no video issues since, there are know problems with driver 100.14.19 and they are not fixed in the current Beta.

In terms of video quality in what way is it bad? tearing and such or something else. My setup feeds a  32 inch 720p panel over DVI and the quality is superb. I use the following settings.

Deinterlace playback Algorithm = Kernel

Mpeg2 decoder = Libmpeg2

enable real time priority threads in /etc/security/limits.conf by adding the following to the bottom of the file:

*                     -       rtprio     0
*                     -       nice       0
@audio          -       rtprio     50
@audio          -       nice       0

---

### Post by Robocoastie on 2007-11-18
Didn't have to adjust the nvidia driver. I didn't find the Deinterlace at first so did the other steps which I couldn't tell any difference but then I looked again for the Deinterlace setting and found it, I also found the mpeg2 decoder was set to the default, whichever uses ffmepg. Anyway after I changed that to libmeg2 and set Deinterlace and chose kernel video cleaned up much better. It now looks the same as Windows Media Center, not perfect since both setups used direct cable rather than taking over my digital box and thus robbing me of its recording ability but its far better than it was!

Before I was getting grainy horizontal bars. Kind of like you get with rabbit ears instead of cable or a good tall antenna tower.

thanks! Now I just need to learn how to use all the features of mythtv like transcoding, burning a recording to disc, and making a divx or theora out of a recording and so on. Just going to pick up a mythtv book for that because the howto guide is pretty cryptic.

---

### Post by mwc on 2007-11-18
That's great the video is sorted out, as for learning about everything else Myth has to offer, I started with it about 3 years ago and I'm still finding new tweaks and twists. I should qualify my comment on the Nvidia driver, I only had problems on the master backend/frontend which is 64 bit gutsy, on the other machines, one slave backend / frontend and one frontend only 32 bit installs I had no issue with 100.14.19 driver.

Some where on the Myth website it says the project is by developers for developers, they are not kidding!

Cheers,

Mark

---

### Post by Robocoastie on 2007-11-23
I'm trying another approach now. Now I'd like to try again the big rig as a backend only and the other as frontend. I'm having problems getting the frontend to see the back though and I think perhaps I'm using the wrong ip.

when I set my backend up I assume I am to replace "localhost" with the actual ip number instead, then punch that into the frontend also. But which is my ip? When I do ifconfig on the backend I get:

> robocoastie@dell5100:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:12:3F:88:21:7F  
          inet addr:192.168.2.4  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::212:3fff:fe88:217f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1446 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1352 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1143036 (1.0 MB)  TX bytes:210124 (205.1 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:66 errors:0 dropped:0 overruns:0 frame:0
          TX packets:66 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5104 (4.9 KB)  TX bytes:5104 (4.9 KB)

robocoastie@dell5100:~$ 

is the one I use the "inet addr" or the "Bcast?"

Note that aside from my router I'm not running a firewall because it just gets in the way of samba sharing so I know that's not the problem. One way or another I'm going to figure this all out because the limitations and restrictions in microsofts media center is maddening. You know what else is hilarious is the rig I want to use as a frontend I tried to use Vista Media Center with and it turns out the via chipset won't work with the PVR-150 card and makes the computer restart over and over, yet it runs mythtv just fine.

---

