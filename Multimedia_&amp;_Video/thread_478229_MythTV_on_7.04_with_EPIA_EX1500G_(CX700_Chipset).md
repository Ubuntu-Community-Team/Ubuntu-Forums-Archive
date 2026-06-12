---
title: "MythTV on 7.04 with EPIA EX1500G (CX700 Chipset)"
date: 2007-06-19
forum: Multimedia &amp; Video
---

### Post by BillDozer on 2007-06-19
Hi,

Just want to give my two cents back to the ubuntu community.

I wanted to build my HTPC using MythTV and bought the following hardware (for those of you who are interested):
[LIST]
[*]VIA EPIA [EX1500G]("http://www.via.com.tw/en/products/mainboards/motherboards.jsp?motherboard_id=450") motherboard (CX700M2 chipset)
[*]Silverstone [LC-09]("http://www.silverstonetek.com/products/lc09/lc09.html") case
[*]Hauppauge [WinTV-PVR-500 MCE ]("http://www.hauppauge.com/pages/products/data_pvr500mce.html") (including remote with IR receiver/blaster - lirc mce_usb2)
[*]320 Gb Harddisk (SATA)
[*]Slimline DVD writer (IDE)
[*]Microsoft wireless keyboard with mouse (M700 if I recall it correctly).
[/LIST]

The reason I bought the Epia EX motherboard was that I have a Sony 32" LCD TV (32U2000) with an HDMI connector and thought that this motherboard would be perfect for it. VIA also had drivers on their support web site for Linux, so this should be easy-peasy. (At least I thought it would be).

**First things first, the assembly of the hardware...**
I had the package sent to my work and after I checked all the components I found out that the only thing missing was a SATA cable. So on the way home from work I pulled in to the local PC shop and got me a SATA cable (incl. SATA power converter). I read [somewhere]("http://www.virtual-hideout.net/reviews/silverstone_lc09/index.shtml") that it took them 15 minutes to put it all together. So I put the kids in front of the TV, put in Shrek 2 and by the end of the film I was still sweating with the small connectors. I think in all it took me two hours to assemble which I think is pretty ok for a non physical technical guy. ;)
In the end the tuner card was crammed between the harddisk and the DVD drive, but it seems the Hauppauge people had this case in mind when they built the tuner card. Because on the backside there were some rubber nubs(??) so that the back of the card did not get in touch with the metal of the DVD inlay.

**And now to the Ubuntu part...**
To start out I want the machine to be both frontend and backend, but in the future, after we sell our house and move into a new house with a "server room", I want the machine to be diskless frontend.

To install the system I would follow the [combined Backend/frontend guide]("https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend"). So I crossed my fingers, turned on the PC, put in the Alternate Install Disk and it went pretty much OK. :) No problems to install the system, the first "problem" came when I started gdm. I worked remote and could not see anything starting, but once I got over to the TV in the living room I could see the Myth-Setup screen. ;) The only problem was that the resolution was 640x480, to be honest I had this in a couple of days until i found out how to set up the modeline in xorg.conf (I will update this later), but I finished up running in 1280x720.

Because I live in Denmark I had to apt-get the xmltv package to get the grabber to work (this is not described in the guide). The tuner card worked out-of-the-box, increased the resolution on the cards to 720x576 instead of the standard 480x480. The motherboard on the other hand had some problems, no drivers for the audio and no display driver (the system uses the vesa driver which works but does not perform too well).

So now I had a machine that could plan and record programs. But... I could not hear what I recorded and the video was stuttering and really bad to look at. Went to VIA's [support]("http://www.viaarena.com") website and got the drivers for the HD Audio and the display. The display driver had to be compiled and I had never tried this, so I started with the audio driver because this was binary and needed no compilation. I followed the guide from VIA and there was sound. Very optimistic after this successfull installation I started to follow VIA's guide on the compiling/installing of the display driver.

This became my nightmare for the next few weeks. I compiled the driver, there were errors, got some more, more errors, installed the driver. After installing, the fine modeline did not work anymore, the system hanged completely when trying to show a video. I was getting pretty frustrated.

Had also visited the [OpenChrome]("http://www.openchrome.org") site and read that there was no MPEG2 accelleration on the CX700 chipset yet and had dismissed this driver. But after being unable to get the VIA driver to work I decided to give the openchrome driver a try.

I had to use the Experimental branch to get a driver that supported my (new) chipset.
```
svn co http://svn.openchrome.org/svn/branches/experimental_branch
```
And followed the [Ubuntu OpenChrome Compile guide]("https://help.ubuntu.com/community/OpenChrome") and compiled the 2D driver. This was really easy, and fast, compared to VIA's compilation guide. After installing the driver i unfortunately ended up with a garbled screen and thought that I had to wait a long time before I would have a system that would actually work.

**But...**
I read some posts on the openchrome forums and found [this]("http://wiki.openchrome.org/tikiwiki/tiki-view_forum_thread.php?comments_parentId=3598&topics_threshold=0&topics_offset=4&topics_sort_mode=lastPost_desc&topics_find=&forumId=1") one, that guided me in the right direction, I added```
Option "VBEModes" "true"
Option "EnableAGPDMA" "true"
```to the display section, restarted gdm and it showed up like i hoped.

**And...**
Now the video also works with satisfying speed (although I do not think the MPEG2 accelaration is working yet, the machine uses 50% processor power when it is showing video).

I am happy now, although there still are a few things I have to do before I am completely satisfied.
[LIST]
[*]I have a sattelite box, and have to set up the IR blaster to connect to it (but I do not think this is going to be a big issue)
[*]The screen is cut-off on the sides, I'll reckon I have to adjust some of the values on the modeline line in xorg.conf but I am not sure how to do this yet. At the moment this is only irritating when running the configuration screens, the checkboxes do not show when I am trying to change the settings, so I have to guess if they are checked or not ;)
[*]The 3D driver, although I not find this really important on this machine.
[*]Maybe some other things I have forgotten right now...
[/LIST]

**Conclusion**
[LIST]
[*]If you own a VIA EPIA EX1500G (or EX1000G). Do not go with VIA's display driver but use the openchrome experimental one. Eventhough I had trouble getting it to work, I think it is a good motherboard with a lot of potential.
[*]The Silverstone case is really nice and I recommend it to everybody that wants to have good looking case that does not look like a nerdy PC.
[/LIST]

I hope this post can help some of you out there that have the same problems I had with the VIA Epia EX motherboard.

---

### Post by hansoffate on 2007-06-19
Thanks for this detailed post.  I have been thinking about making a new Mythtv box.  Your box must be really quiet.  

How much did this setup cost you?  I want to build a smaller and quieter box to put in my bedroom.  Any suggestions on how to accomplish that?

Thanks,
Hans

---

### Post by BillDozer on 2007-06-20
Hi Hans,

All-in-all (including DVI->HDMI cable and a scart->SVHS) it has cost me about 6.500 DKR (about 1.150 USD). But if I am not mistaken, it looks like you already have another MythTV box, then you can save some money by making it into a thin client that gets everything from the mythtv server. In that case all you need is:
[LIST]
[*]A case
[*]Fanless motherboard (with included network card). I accidentally bought a motherboard with a fan, the EX1000G is fanless but I am not sure whether or not this board will work at the moment.
[*]A remote
[*]USB wireless keyboard/mouse, is only needed for installing the system
[/LIST]
Then you can set your other MythTV box, or even better a server if you have one, up to serve via the TFTP protocol and set the system up to start from the network. That is also what I want in the future, one server and 4-5 frontends around the house. :-) I haven't tried to do this yet, but I most certainly will try it.

If you want to have the system in your bedroom, I would strongly suggest a fanless motherboard and no harddisk in the machine. I have my machine in the living room, the fan is not too noisy here. The thing that makes the most noise is the harddisk when recording! Rule of thumb to make a quiet syste: *"No moving parts!" (Rotating harddisk, fan or DVD/CD).*

So about 3000 DKR/500 USD or even down to 2000 DKR/350 USD if you take another case and motherboard should be able to do the trick. I suggest looking at the [OpenChrome]("www.openchrome.org") for finding out which chipsets will work for you. If you want a nicelooking case check out Silverstone, I am really satisfied with the one I got.

Robert

---

### Post by hansoffate on 2007-06-21
Thanks for all the information.  What do you say about my build here.
[http://ubuntuforums.org/showthread.php?t=478945](http://ubuntuforums.org/showthread.php?t=478945)

 I do have to agree with you though.  Maybe it will be to loud because of the fans it will have and all the moving parts.  

The thing is, I only have about 150 gb's of tv recording storage, and I wanted to buy a 500gb hard drive and make another frontend/backend setup to record TV.

Does my build seem reasonable for this?  If it is too loud, I can just move it to the living room, but I am a heavy sleeper, so I think it will be fine.

Also, could you explain this, DVI->HDMI cable and a scart->SVHS.  I understand the DVI -> HDMI but I don't understand what the other one is.

Also, I have a newbie Mythtv question.  I have been wondering for a very long time now, why the only shows mythtv ever has is futarama, simpsons, and southpark.   I think it has to do with that they are the top 3 in recording priorty.  Just yesterday, I realized what might be happening.  I saw something recording, but after it got recorded, it immediately got deleted, to record south park.  

I was wondering what recording options you guys use.

Thanks,
Hans

---

### Post by BillDozer on 2007-06-22
I'll post the comments on your system in your own thread.

In Europe, where I live, we already had hdmi's "predecessor" called [SCART]("http://en.wikipedia.org/wiki/Scart"). Basically it is just a connector that can carry sound and video in the same cable. I use it because I have a satellite receiver that has a scart outupt. My tuner card has S-VHS input, so I had to convert this ;-) Btw. This does not work yet :-( I only get a black screen.

Maybe you have set a [filter ]("http://www.mythtv.org/wiki/index.php/Frequently_Asked_Questions#Q:_Why_aren.27t_my_new_recordings_showing_up_in_Watch_Recordings.3F")in the watch recordings screen. Or you have set some special rules regarding expiration, I am not so sure how to make these special settings yet, but [MythTV's wiki]("http://www.mythtv.org/wiki/index.php/Main_Page"!) is probably a good place to find an answer for that.

---

### Post by jazzgossen on 2007-06-26
Thanks a lot for your post! I'm planning to do just the same that you have done in a month or two, but with the fanless EX1000 motherboard. I'll be using 2.5" laptop hard drives to keep the disk noise down. I've read other reports about driver problems with the EX series, so I'm really glad that you were able to work it out. Now I feel more confident to get this kind of motherboard. 

One question though: Is it powerful enough to do simultenous recording and playback?

---

### Post by BillDozer on 2007-06-26
That was the intention, I have had a lot of good help just by reading the posts on ubuntuforums, so now I found that is was time to share. :)

Recording and viewing simultaneously depends all on the tuner card you put in the machine. Be sure to put in one that does hardware MPEG2 encoding. The Hauppauge WinTV-PVR-500 MCE that I have does just that (and that with 2 tuners).

In my case, the recording takes almost no processor power, and when the hardware MPEG2 decoding will be activated for the CX700 chipset, this also will drop the processor load a lot.

But right now, without the hardware MPEG2 decoding, the processor load is about 50% on my system when viewing a recorded program (or DVD). And it does not increase much whether or not I record something at the same time. So as an answer to your post, yes it is powerfull enough, which I suspect also will be the case for the EX1000G, but YMMV.

I'm not in reach of the machine right now, but will come with an update with some more exact figures.

---

### Post by majom on 2007-10-04
> **jazzgossen said:**
> Thanks a lot for your post! I'm planning to do just the same that you have done in a month or two, but with the fanless EX1000 motherboard. I'll be using 2.5" laptop hard drives to keep the disk noise down. I've read other reports about driver problems with the EX series, so I'm really glad that you were able to work it out. Now I feel more confident to get this kind of motherboard. 

One question though: Is it powerful enough to do simultenous recording and playback?
Hi JazzGossen

Did you build your HTPC? Did you have some positive or negative experiences with application speed (MythTV) and PC noise? Did you satisfy with your work?
I am interested in your work, because I am decided to choice EX1000G or EX1500G VIA motherboard for my HTPC.
I prepare to build HTPC with system disk as flash P-ATA module. Disk for storing data will be probably SATA disk. But this is a future and my plans could by changed.

---

### Post by jazzgossen on 2007-10-25
I bought the parts and tried running Ubuntu and Slax Linux on them. I'm having trouble getting TV out in Ubuntu, but with Slax it's no problem. I haven't actually tried my TV tuner card yet. I can play all my AVI videos without problems (maybe 15% CPU load with the OpenChrome drivers), and the system is nice and quiet of course. 

Don't expect it to work for HDTV though, or 3D graphics. It just doesn't have enough CPU power, and the linux driver doesn't support 3D acceleration yet. Also, be aware that it only handles low-density RAM (chip configuration 64*8). I bought a high-density 1 GB RAM stick, and it only sees half of it. Otherwise, I'm pretty happy so far. But the day I buy a HDTV, I'll probably regret that I didn't buy something with a faster CPU. 

One more negative aspect is that VIA's support is entirely non-existant. If you have problems, you are on youre own, or left to user forums.

---

### Post by BillDozer on 2007-10-26
> **jazzgossen said:**
> I bought the parts and tried running Ubuntu and Slax Linux on them. I'm having trouble getting TV out in Ubuntu, but with Slax it's no problem. I haven't actually tried my TV tuner card yet. I can play all my AVI videos without problems (maybe 15% CPU load with the OpenChrome drivers), and the system is nice and quiet of course. 

Don't expect it to work for HDTV though, or 3D graphics. It just doesn't have enough CPU power, and the linux driver doesn't support 3D acceleration yet. Also, be aware that it only handles low-density RAM (chip configuration 64*8). I bought a high-density 1 GB RAM stick, and it only sees half of it. Otherwise, I'm pretty happy so far. But the day I buy a HDTV, I'll probably regret that I didn't buy something with a faster CPU. 

One more negative aspect is that VIA's support is entirely non-existant. If you have problems, you are on youre own, or left to user forums.

I'm still using my system and are very happy about it. The only things I have problems with at the moment are:
[LIST]
[*]DVD playback sometimes "hicks" when showing subtitles, but not with every title.
[*]When recording two programs and viewing a third, sometimes the program that you are wathing plays, stops for ½ a sec, plays again, stops for ½ a sec, and so on... But not always, it has been a long time since I noticed this to happen. Now I think of it it is when there are 2 programs recording, 1 watching and 1 commercial flagging. In the future I would like to have a dedicated server to store the data and commercial flagging, so this should not be an issue anymore then.
[*]The screen cut-off at the sides I solved by specifying width in MythTV setup, but I would rather have solved it using modelines in xorg.conf
[/LIST]

Hopefully, HDTV will be supported in the future by the openchrome drivers. There is a special chip on the motherboard that should be able to decode MPEG2, WMV9 and HDTV, but the drivers do not support this at the moment.  I'm not able to receive any HDTV signals at this time, so it is not too important for me right now.

I'm still using the same openchrome driver I installed back in june, there have been updates since, but I am a little scared to start changing the system. My wife really likes it and I don't want to jinx it, "Never change a winning horse" ;-)

---

### Post by morphar on 2008-01-14
Hello,

I have installed Ubuntu on a VIA EX10000EG board, and compiled the openchrome drivers as in the beginning of this thread..

But I can't start op GDM or KDM, when I do my TV (40"" Samsung LCD) just say "Mode not supportet". But when I run startx fro commandline, the desktop fires up nicely, only missing about an incharound the desktop.

Does anyone have any experience with this, and any idea how i can fix gdm?

---

### Post by Mastersi on 2008-01-22
Hey
I have manage to get openchrome to work by using the experimental branch of openchrome.  *But not the video out (RGB, S-Video, Composite) 
[http://wiki.openchrome.org/tikiwiki/tiki-index.php?page=Work%20In%20Progress]("http://wiki.openchrome.org/tikiwiki/tiki-index.php?page=Work%20In%20Progress")

Now my projekt have stand still in some month and my next step will be to try via's new binary install for ubuntu (Released 4 dec. 2007) 
[http://www.viaarena.com/default.aspx?PageID=420&OSID=45&CatID=3220&SubCatID=184]("http://www.viaarena.com/default.aspx?PageID=420&OSID=45&CatID=3220&SubCatID=184")

Are there any, there have manage to get video out working on this board?

---

### Post by jazzgossen on 2008-01-23
I also have the EX10000EG, and I have Ubuntu 7.10 installed. PAL TV out via S-Video has been working great with the vesa driver. On a previous installation, using Ubuntu 7.04 and the then experimental branch of the openchrome driver, TV out worked fine too. But with the recent CVS version (mid-january 2008) of the openchrome trunk (which now supports this chipset as well), TV out only "kind of" works, if I explicitly specify TV out and PAL format in the driver options in xorg.conf. Currently, I get an image on the TV, but it is wildly flickering, as if the refresh rate is wrong, and I haven't found the way to correct it yet.

Also try to look [here]("http://www.kingcot.eclipse.co.uk/unichrome/unichromeTvOut.html") for some other suggestions.

---

### Post by jazzgossen on 2008-01-24
I couldn't find a working mode with the current OpenChrome trunk, but after installing VIA's official driver for Ubuntu 7.10, I\m getting good accelerated TV output. Wee!

---

### Post by Mastersi on 2008-01-28
> I couldn't find a working mode with the current OpenChrome trunk, but after installing VIA's official driver for Ubuntu 7.10, I\m getting good accelerated TV output. Wee!
Then you are using the official driver from Via, do you using VeMP or VeXP to get full accelerated video?

---

### Post by BillDozer on 2008-01-28
> **jazzgossen said:**
> I couldn't find a working mode with the current OpenChrome trunk, but after installing VIA's official driver for Ubuntu 7.10, I\m getting good accelerated TV output. Wee!
Sounds nice to get accellerated output. How hard was it to install this? I gave up last year, because the documentation was not good enough. If it is not too hard I am considering to install it too.

---

### Post by jazzgossen on 2008-01-29
With the current driver, installation was completely painless for me. Just run the installation script and restart X (but as always, be sure to back up your xorg.conf first). 

However, I just read something on the openchrome mailing list about security flaws in the closed-source driver. And when I play videos in MythTV with the via driver, the image is green and oddly scaled, although the same files play fine in Totem.

---

### Post by jazzgossen on 2008-02-05
> **Mastersi said:**
> Then you are using the official driver from Via, do you using VeMP or VeXP to get full accelerated video?
I don't know. I just use the default settings. However, now I've found that MythTV won't play videos when I use the via driver, but it works in other movie players, and if I run the same command line as specified in MythTV from the command line. So I'd like to try the openchrome driver again, though it seems more tricky to get it working correctly with the current trunk than with the previous experimental branch. Oh well...

---

### Post by aidan_curtis on 2008-03-23
Ive built a box using a xubuntu 7.10 a Via EX10000eg mother board and a hvr 4000 heres how 
1.  insert disk and boot pick default install option
2.  when Xserver fails type <CTRL>+<ALT>+<F4>
3.  at the $ prompt type startx<ENTER>
4.  follow the install proceedure
5.  Reboot
6.  when Xserver fails type <CTRL>+<ALT>+<F4>
7.  log in to the console using the username and password setup during the install
8.  at the $ prompt type startx<ENTER>
9.  do the system updates
10. reboot
11. when Xserver fails type <CTRL>+<ALT>+<F4>
12. log in to the console using the username and password setup during the install
13. at the $ prompt type startx<ENTER>
14. Add the restricted multivers and universe and backports and package lists to the distribution using Applications\System\Software Sources
15. run Applications\System\Update Manager, Install any updates
16. reboot.
17. when Xserver fails type <CTRL>+<ALT>+<F4>
18. log in to the console using the username and password setup during the install
19. at the $ prompt type startx<ENTER>
20. using Applications\System\Synaptic Package Manager add the libgl-mesa-dri package 
21. it might be wise to try removing xserver-xorg-video-via
22. sudo apt-get build-dep xserver-xorg-video-via
23. Create a directory src in your home directory
24. download and extract [http://www.viaarena.com/Driver/via_ubuntu710_unichrome-v40072d-kernel-bin-_v0.80.zip](http://www.viaarena.com/Driver/via_ubuntu710_unichrome-v40072d-kernel-bin-_v0.80.zip) to the src directory
25. open a terminal type cd src <ENTER>
26. type chmod 755 VIA_U710_UniChrome-GFX-v40072d.run <ENTER>
27. type sudo ./VIA_U710_UniChrome-GFX-v40072d.run <ENTER> and pick option 1.install
28  reboot and determine display resolution and set it using S3utility and Applications\Settings\Screens and Graplics
29. move the task list, show desktop and trash items from the pannel along the bottom of the screen to the panel at the top
30. remove everything else of the pannel bar along the bottom
31. change the number of workspaces to one using Applications\Settings\Workspace Settings
32. Set the pannel at the top of the screen to a width of 30 and set it's location to the bottom center of the screen using Applications\Settings\Panel Manager
33. reboot.
33a. using Applications\System\Software Sources remove backports
34. Install Filezilla,dvb-utils, rtorrent, mplayer, mplayer-doc, mplayer-fonts & mplayer-skins using using Applications\System\Synaptic Package Manager
35. sudo apt-get install mercurial.
36. hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)
37. cd v4l-dvb
38. wget [http://dev.kewl.org/hauppauge/v4l-dvb-hg-sfe-latest.diff](http://dev.kewl.org/hauppauge/v4l-dvb-hg-sfe-latest.diff)
39. patch -p1 < v4l-dvb-hg-sfe-latest.diff
40. edit and fix any problems from previous act. look at the output you'll see which files didnt diff
41. make
42. sudo make install
43. wget [ftp://167.206.143.11/outgoing/Oxford/88x_2_119_25023_WHQL.zip](ftp://167.206.143.11/outgoing/Oxford/88x_2_119_25023_WHQL.zip)
44. decompress what's needed : "unzip -jo 88x_2_119_25023_WHQL.zip Driver88/hcw88bda.sys"
45. sudo dd if=hcw88bda.sys of=dvb-fe-cx24116.fw skip=81768 bs=1 count=32522
46. copy dvb-fe-cx24116.fw to /lib/firmware/2.6.22-14-generic
47. reboot
48. make sure that the xorg.conf is correct i.e. set keyboard to "ie" and Load	"dri" alernatively copy the xorg.conf from src.
49. to test tune mkdir .szap
50. scan /usr/share/doc/dvb-utils/examples/scan/dvb-s/Astra-28.2E > ./.szap/channels.conf
51. run mplayer
52  cp ./.szap/channels.conf ./.mplayer/channels.conf
53. mplayer dvb://UTV
54. firefox to [http://www.mythbuntu.org/existing-ubuntu](http://www.mythbuntu.org/existing-ubuntu)
55. click install mythbuntu and select install packages /select haugauge nova t 500 as the lirc
56. reboot
57. run Applications\System\Mythbuntu Control Centre
58. click system roles
59. setup as primary backend and as frontend
60. reboot
61. run Applications\System\Mythbuntu Control Centre
62. click mythtv configuration
63. launch mythtv setup
64. answer yes to adding user to mythtv group and restart 
65. run Applications\System\Mythbuntu Control Centre
66. click mythtv configuration
67. launch mythtv setup setup inputs do channel scans etc
68. reboot
69. [http://www.nabble.com/MythTV-won't-run-with-VIA-CX700M2-chipset-td15040477s15552.html](http://www.nabble.com/MythTV-won't-run-with-VIA-CX700M2-chipset-td15040477s15552.html)
70. sudo apt-get install build-essential
71. sudo apt-get build-dep mythtv
72. cd src
73. apt-get source mythtv
74. In libs/mythtv/vsync.cpp, comment out the following line in VideoSyn::BestMethod (line 95): //TESTVIDEOSYNC(DRMVideoSync);
75. In libs/mythtv/videoout_xv.cpp, uncomment line 67: #define USE_ATI_PROPRIETARY_DRIVER_XVIDEO_HACK
76. ./configure --enable-dvb --enable-proc-opt --prefix=/usr --enable-xvmc --enable-xvmc-pro --enable-xvmc-vld
77.  qmake mythtv.pro
78. make
79. sudo make install
80. Applications\System\run myth-setup and after that try to run the frontend and reboot
81. run Applications\System\Mythbuntu Control Centre
82. click system roles
83. remove as primary backend and as frontend
84. run Applications\System\Mythbuntu Control Centre
85. click system roles
86. setup as primary backend and as frontend
87. launch frontend
88. reboot if required and relaunch frontend
89. setup settings (notice lack of skins)
90. run Applications\System\Mythbuntu Control Centre
91. click applications & plugins add em all.
92. reboot
93. run Applications\System\Mythbuntu Control Centre
94. click proprietary codecs enable medibuntu proprietary codec support apply
95. it appears that the changes dont finish just run the update manager beside the clock when you get sick waiting.
96. reboot
97. run Applications\System\Mythbuntu Control Centre
98. click proprietary codecs all the available codecs
99. Install the mythtv-themes using Applications\System\Synaptic Package Manager do a search you'll find them.
100. reboot
101. rerun frontend and pick the right theme you will probably have to rerun it a couple of times
102. run Applications\System\Mythbuntu Control Centre
103. click system services enable mysql service and apply
104. click system services enable vnc service , set password and apply
105. click system services enable ssh services and apply
106. reboot
107. run Applications\System\Mythbuntu Control Centre
108. click artwork and login behavour, enable automatic login 
109. reboot 
110. you may  have to edit xorg.conf again.
111. there are are some problems with mythbuntu the links in /www/mythweb/data/ they are pointing to the wrong places fix as follows
112. cd /var/www/mythweb/data
113. sudo rm ./video_covers
114. sudo rm ./video
115. sudo ln -s /var/lib/mythtv/videos ./video
116. sudo ln -s /var/lib/mythtv/videos ./video_covers
117. cd /var/www/mythweb
118. sudo chown root:www-data ./data
119. sudo chmod +t /usr/share/mythtv/mythweb/data (thanks Gary Parker "http://www.parker1.co.uk/mythtv_0.20.php")
120. add www-data to the mythtv group in /etc/group.
120. Install Webmin its a damm good way of managing the box. (personal opinion)
121. the remote control needs some work  again one should have a look at [http://www.parker1.co.uk/mythtv_tips.php](http://www.parker1.co.uk/mythtv_tips.php)
122. use this to back up the disk [http://ping.windowsdream.com/](http://ping.windowsdream.com/)

Thanks to all at the ubuntu forums, lytke, Billdozer, Darron Broad, Menthol, Garry Parker, Eugene Gargan and lots of others
Hope this helps someone else.
Aidan

---

