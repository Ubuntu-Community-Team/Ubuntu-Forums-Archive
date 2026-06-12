---
title: "ISO stalls after upgrade to 8.04"
date: 2008-10-18
forum: Mythbuntu
---

### Post by larsolav on 2008-10-18
Hello,
I finally took the plunge and upgraded from 7.10 to 8.04 three days ago. I have an ISO of a ripped DVD that played OK before the upgrade, but now stalls on the FBI warning screen (somewhat ironic?). The system responds to no remote control keys. I have to reboot from an other shell. Other DVD ISOs play just fine after the warning screen.

Here is the Frontend log for the process:
> 2008-10-18 08:50:31.362 XMLParse::LoadTheme using /usr/share/mythtv/themes/Mythbuntu/video-ui.xml
2008-10-18 08:50:37.285 XMLParse::LoadTheme using /usr/share/mythtv/themes/Mythbuntu/video-ui.xml
2008-10-18 08:50:39.061 TV: Attempting to change from None to WatchingPreRecorded
libdvdread: Using libdvdcss version 1.2.9 for DVD access

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000145
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x0000021c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000017eb
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x000ac49b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x000ac4a6
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x000ac591
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x000ac59c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x000ad0a7
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x000ad0b2
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x000b071d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x000b0728
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x000b21f1
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x000b21fc
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x000c40c5
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x000c40d0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x000d479a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x000d47a5
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_0.VOB at 0x000d4c4b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_1.VOB at 0x000d4c56
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_0.VOB at 0x000d5158
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_1.VOB at 0x000d5163
libdvdread: Elapsed time 0
libdvdread: Found 10 VTS's
libdvdread: Elapsed time 0
libdvdnav: Using dvdnav version 0.1.10-xine from [http://xine.sf.net](http://xine.sf.net)
libdvdnav: DVD Title: BABY_MOZART
libdvdnav: DVD Serial Number: 2f9e125a
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/xxx/.dvdnav/BABY MOZART.map'
libdvdnav: DVD disk reports itself with Region mask 0x00000000. Regions: 1 2 3 4 5 6 7 8
2008-10-18 08:50:39.694 Opened DVD device at /var/lib/mythtv/videos/BABY_MOZART.ISO
2008-10-18 08:50:39.695 There are 16 titles on the disk
2008-10-18 08:50:39.695 Title 0 has 0 parts.
2008-10-18 08:50:39.695 Title 1 has 8 parts.
2008-10-18 08:50:39.695 Title 2 has 1 parts.
2008-10-18 08:50:39.695 Title 3 has 3 parts.
2008-10-18 08:50:39.695 Title 4 has 2 parts.
2008-10-18 08:50:39.695 Title 5 has 2 parts.
2008-10-18 08:50:39.695 Title 6 has 3 parts.
2008-10-18 08:50:39.695 Title 7 has 2 parts.
2008-10-18 08:50:39.695 Title 8 has 2 parts.
2008-10-18 08:50:39.695 Title 9 has 2 parts.
2008-10-18 08:50:39.695 Title 10 has 2 parts.
2008-10-18 08:50:39.695 Title 11 has 2 parts.
2008-10-18 08:50:39.696 Title 12 has 1 parts.
2008-10-18 08:50:39.696 Title 13 has 5 parts.
2008-10-18 08:50:39.696 Title 14 has 20 parts.
2008-10-18 08:50:39.696 Title 15 has 45 parts.
2008-10-18 08:50:39.713 AFD: Opened codec 0x8327fd0, id(MPEG2VIDEO) type(Video)
2008-10-18 08:50:39.713 NVP: Disabling Audio, params(-1,-1,-1)
2008-10-18 08:50:39.731 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2008-10-18 08:50:39.760 OSD Theme Dimensions W: 640 H: 480
2008-10-18 08:50:39.764 DPMS Deactivated 
2008-10-18 08:50:40.105 TV: Changing from None to WatchingPreRecorded
greedyhdeint: size changed from 0 x 0 -> 720 x 480
greedyhdeint: size changed from 0 x 0 -> 720 x 480
2008-10-18 08:50:40.212 Video timing method: USleep with busy wait
greedyhdeint: size changed from 0 x 0 -> 720 x 480
2008-10-18 08:50:40.365 DPMS Reactivated.
2008-10-18 08:50:40.448 AFD: Warning, video codec 0x8327fd0 id(MPEG2VIDEO) type (Video) already open.
greedyhdeint: size changed from 0 x 0 -> 720 x 480
2008-10-18 08:50:40.465 DPMS Deactivated 
2008-10-18 08:50:40.466 DPMS Reactivated.
2008-10-18 08:50:40.606 AFD: codec AC3 has 0 channels
2008-10-18 08:50:40.607 AFD: Opened codec 0xa66ff300, id(AC3) type(Audio)
2008-10-18 08:50:40.609 Opening audio device 'digital'. ch 2(2) sr 48000
2008-10-18 08:50:40.609 Opening ALSA audio device 'iec958:{ AES0 0x02 }'.
2008-10-18 08:50:40.625 NVP: Enabling Audio
2008-10-18 08:50:40.644 Opening audio device 'digital'. ch 2(2) sr 48000
2008-10-18 08:50:40.644 Opening ALSA audio device 'iec958:{ AES0 0x02 }'.
2008-10-18 08:50:40.666 DPMS Deactivated 
2008-10-18 08:50:40.766 DPMS Reactivated.
libdvdnav: RANDOM or SHUFFLE titles are NOT handled yet.
2008-10-18 08:50:43.263 NVP: Disabling Audio, params(-1,-1,-1)
2008-10-18 08:50:43.270 DPMS Deactivated 
2008-10-18 08:50:43.270 DPMS Reactivated.
greedyhdeint: size changed from 0 x 0 -> 720 x 480
2008-10-18 08:50:43.443 AFD: Warning, video codec 0x8327fd0 id(MPEG2VIDEO) type (Video) already open.
greedyhdeint: size changed from 0 x 0 -> 720 x 480
2008-10-18 08:50:43.600 AFD: codec AC3 has 0 channels
2008-10-18 08:50:43.601 AFD: Opened codec 0xa66aae90, id(AC3) type(Audio)
2008-10-18 08:50:43.604 Opening audio device 'digital'. ch 2(2) sr 48000
2008-10-18 08:50:43.604 Opening ALSA audio device 'iec958:{ AES0 0x02 }'.
2008-10-18 08:50:43.620 NVP: Enabling Audio
2008-10-18 08:50:43.636 Opening audio device 'digital'. ch 2(2) sr 48000
2008-10-18 08:50:43.636 Opening ALSA audio device 'iec958:{ AES0 0x02 }'.
libdvdnav: RANDOM or SHUFFLE titles are NOT handled yet.
2008-10-18 08:50:43.671 DPMS Deactivated 
2008-10-18 08:50:43.671 DPMS Reactivated.
2008-10-18 08:51:08.425 TV: Attempting to change from WatchingPreRecorded to None
mythfrontend.real: Fatal IO error: client killed
mythfrontend.real: Fatal IO error: client killed
Starting mythfrontend.real..

My myth version:
> ~$ apt-cache policy mythtv-common
mythtv-common:
  Installed: 0.21.0+fixes18207-0ubuntu4~hardy1
  Candidate: 0.21.0+fixes18207-0ubuntu4~hardy1
  Version table:
 *** 0.21.0+fixes18207-0ubuntu4~hardy1 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/multiverse Packages
        100 /var/lib/dpkg/status
     0.21.0+fixes16838-0ubuntu3.1 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Packages
     0.21.0+fixes16838-0ubuntu3 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Packages


Does anyone know why it is stalling now when it was working fine in 7.10? My son really wants his baby mozart...

My system (if at all relevant):
Foxconn 955X7AA motherboard, Intel Pentium D 820 Smithfield 2.8GHz CPU, 1 GB RAM, 1.2 TB LVM var/lib, 2 AirStar-HD5000-PCI tuners, eVGA GeForce 7300GS GPU, Streamzap PC remote control.

---

### Post by larsolav on 2008-10-19
Just want to add that last night while watching a Netflix DVD, "Forgetting Sarah Marshall", the menus were all screwed up on the Mythtv box, but on a XP machine they looked fine. Anyone know what is going on?

Cheers!

---

### Post by larsolav on 2008-10-21
No one has seen something like this before? Is it just my player?
newlinux suggested in this post, [http://ubuntuforums.org/showthread.php?t=954584](http://ubuntuforums.org/showthread.php?t=954584), to use xine or vlc instead of the internal player. Can I do that with an ISO as well? And how do I do that. Can I select the video in the Myth frontend video screen with all my ripped DVDs and select one and have it played by for example xine? 
Thanks again and Cheers!

---

### Post by larsolav on 2008-10-26
Hi there,
So no one has seen anything like this? My wife had to reboot after staring to play the iso of Toy story. It also stopped at the same spot. I uninstalled mythvideo and reinstalled it. It did not help.
Any one know why iso's that worked before under 7.10 stalls when played in 8.04??????????

Anyone?

---

### Post by larsolav on 2008-10-28
I feel so alone!
[Ah, there is at least one more person who has experienced this!]("http://www.mythtv.org/pipermail/mythtv-users/2008-July/229359.html")

 Not so alone anymore, but still don't know what to do.

How do I have myth open ISOs with Xine? Will that help?

Cheers!

---

### Post by newlinux on 2008-10-28
Hello, sorry no one has helped. I hope you get this figured out soon.


As far as opening isos with a separate application you have a couple of ways:

1. You can set all isos to open with an external player. To do this you go into your setup->media settings->video settings->file types (or something like that, not at my machine now) and then go to the iso type, and for player put in xine (you may want to add some command line options for making it full screen, using a certain filter, etc. If you search around I'm sure you'll get some good examples). This will make all isos open up with xine.

2. You can also set it on a per file basis. so if you only have a couple that are giving you problems, you go can go into Video manager, select the title that is giving you problems, and then enter in xine (again with the command line switches you want) as the player. I do this for a couple files that give me problems using mplayer.

I should note that if you have a remote, you'll want to make sure lirc is configured for xine as well. Before going through all this, you should make sure the isos play fine with xine outside of myth, and maybe play around with some command line options.

I hope this helps.

---

### Post by larsolav on 2008-10-29
Thanks Newlinux! 
You gave Baby Einstein back to my 1.5 year old and Toy Story to my 4 year old! Happy happy happy time!

I now have set myth to run all ISOs using Xine. I found the command line options you mentioned here: [http://www.mythtv.org/wiki/index.php/Configuring_Xine](http://www.mythtv.org/wiki/index.php/Configuring_Xine)
Xine opens and plays my ISOs without any problem at all! It is not as fancy as the internal player when it comes to remote control configuration (e.g. the arrow keys only work for navigating the DVD menus but not for skipping while playing a film), but at least it plays the ISOs without a hitch.
It is funny, the wiki page referenced above says this: > As of 0.21, the use of Xine for videos and DVDs is deprecated in favour of using the Internal player which is integrated into MythTV

But for ISOs with every upgrade something funky has happened: I started out OK with original 7.10 distro, ISOs worked fine. Then I upgraded in 7.10 to myth 0.21 and some ISOs would not play the sound unless I selected "chapters" (or the like) and selected to start the film under the second chapter and then skip back to the first chapter. I saw some posts here about it, but I don't recall any solution other than the chapter thing.

And then, when I upgraded to 8.04 a couple of weeks ago some ISOs don't play at all with Myth, and hence my post. Strange....

---

### Post by larsolav on 2008-10-29
Okay, so as I was writing the last post, I clicked [the link for "Internal player"]("http://www.mythtv.org/wiki/index.php/Internal_player") in [the wiki for configuring Xine for Myth]("http://www.mythtv.org/wiki/index.php/Configuring_Xine")I noticed it says:
> In order to use the Internal Player in MythDVD or MythVideo set the player to "Internal" (capital I) and ensure that the Default Player option is not selected. 
Okay, when I set up myth to change the default player to Xine, I do believe that before the default player was set to mplayer with some letter salad behind. Should it have instead said "Internal"? Could this be the answer to my problem? I can't test for an other 12 hours or so until I get back from work and taking the kids to the park! Is the "Internal" player different from mplayer? Ooooh, I hope, I hope!

Thanks again for all you guys's support and help!

Cheers!

---

### Post by newlinux on 2008-10-29
Yes, the internal player is different from mplayer. If you want to use the internal player can swap out xine for Internal per my instructions above for mythvideo. You can also set the default player to Internal in the setup for all videos.

i use the internal player for almost everything unless a file has a problem. Then my onscreen menus and playback options and bookmarking and remote all work just like they do with TV recording playback. If you haven't tried the Internal player, give that a shot. At least you already know for problem isos you can just set them to xine. Some files just work better in different players than others - this is why it is nice you can actually set up different players for different files.

---

### Post by larsolav on 2008-10-29
Thanks again newlinux!

So I tried with setting up the default player as "Internal," and have ISOs tagged to use the default player. Tried the Baby EInstein video and it freezes on the warning screen again. When I press the menu button I get the familiar semi transparent menu on on the upper left corner I used to get (which looks very much like the menu that pops up when playing recorded content and selecting menu). So I guess I was originally opening ISOs with the internal player anyway..... 

Bummer, because when it works the internal player is so much more convenient than Xine (I haven't figured  out how to skip previews in Xine etc). I also set up the default player to be mplayer and tagged ISOs to the default player, and it doesn't seem to do DVD menus... I'd like to have my internal player work again...

Wonder why my Internal plaer is having this problem with select ISOs after the upgrade to 8.04 ? Is this worthy of filing a bug? and if so how does one go about doing it?

---

