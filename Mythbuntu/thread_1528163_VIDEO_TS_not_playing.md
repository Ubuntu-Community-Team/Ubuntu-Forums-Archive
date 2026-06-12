---
title: "VIDEO_TS not playing"
date: 2010-07-10
forum: Mythbuntu
---

### Post by larsolav on 2010-07-10
Good morning,
My kids this morning wanted to watch our Smurfs DVD which I have in a VIDEO_TS folder. This used to work quite well in 10.04 (0.23 Autobuilds enabled and fully updated). But today I get this error in the frontend log(I still get the error after the latest updates):
> libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Couldn't find device name.
libdvdnav:DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdnav: Using dvdnav version svnR1169
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/husebo/.dvdnav/.map'
libdvdnav: vm: failed to read VIDEO_TS.IFO
2010-07-10 08:06:20.903 Failed to open DVD device at /var/lib/mythtv/disk1/isos/SMURFS_S1_VOL1_DISC1

I also tried other films I have stored in VIDEO_TS format. They do not work. ISOs work fine (at least the least pesky ones). So, VIDEO_TS does not work, but ISO does. I do not use storage groups for videos, of course.

Any ideas?

Thanks!

Lars

---

### Post by thebigob on 2010-07-10
Which application are you using to view these?

---

### Post by larsolav on 2010-07-10
> **thebigob said:**
> Which application are you using to view these?

Hi thebigob!
Internal, hadn't installed anything else.

---

### Post by jlagrone on 2010-07-10
Are you using storage groups?  A number of file types -- iso, video_ts, and bdmv do not currently work with storage groups.  Perhaps that is the problem?  [http://www.mythtv.org/wiki/MythVideo#Disadvantages](http://www.mythtv.org/wiki/MythVideo#Disadvantages)

---

### Post by larsolav on 2010-07-10
> **jlagrone said:**
> Are you using storage groups?  A number of file types -- iso, video_ts, and bdmv do not currently work with storage groups.  Perhaps that is the problem?  [http://www.mythtv.org/wiki/MythVideo#Disadvantages](http://www.mythtv.org/wiki/MythVideo#Disadvantages)

Hi jlagrone,
Nope, not using storage groups for my ISOs and video_ts. I have ISOs working (they are in the same directory as my video_ts folders). I also had video_ts working in 9.10, I guess it stopped working after I made a fresh install of 10.04

---

### Post by larsolav on 2010-08-27
I still haven't gotten it to work.I used to play the video_ts folders fine in 9.10. ISOS play fine. I even upgraded today to 10.04/0.23.1, and it is still the same: ISOs work fine, video_ts do not...

Anyone know why?

Frontend log again:
> 2010-08-27 22:13:13.256 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/video-ui.xml
2010-08-27 22:13:14.339 TV: Attempting to change from None to WatchingDVD
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Couldn't find device name.
libdvdnav:DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdnav: Using dvdnav version svnR1169
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/husebo/.dvdnav/.map'
libdvdnav: vm: failed to read VIDEO_TS.IFO
2010-08-27 22:13:14.340 Failed to open DVD device at /var/lib/mythtv/disk1/isos/The_Many_Adventures_of_Winnie_the_Pooh

---

### Post by larsolav on 2010-08-29
Solved the symptom, but not the underlying problem: Converted the videos to ISO files using genisoimage. 
Cheers!

---

### Post by Rocko262c on 2010-08-30
LarsoLav,

I am having similar troubles, but with a plain DVD from the DVD drive. 

Mythbuntu 9.10 played everything with no problems.  

I upgraded to 10.04, installed updates, and even installed libdvdread4 package ([https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)), but I have trouble playing DVD's.  Some DVD&#8217;s won't play at all and those that do play returns back to the "Optical Disk" directory when I try to fast-forward.

Any advice/recommendations?

Cheers,
Rocko262c

---

### Post by larsolav on 2010-08-30
Rocko,
Do you have Autobuilds enabled as well?
If not, then enable it in mcc or at [http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds) , it fixes some of the player issues.
If you have, then I have no idea what is wrong...

---

### Post by Rocko262c on 2010-12-01
Larslav,

I finally enabled Autobuilds by the following:
1.0 Go to [http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds)
2.0 Click on "Install the Mythbuntu-repos package"
3.0 Opening the deb package and then following the instructions
4.0 Reopen Update Manager and then installing the updates

This did fix the DVD player, but it still has lots of errors.

The video player has the following errors:
     -Freezes when fast forwarding or skipping chapters, then exits out of the Mythbuntu Frontend to the desktop or gives an error that says "Video frame buffering failed too many times"
     -Can't properly display the Disk Menu when disk is in play and selecting the menu, then selecting "Navigate", then selecting "DVD Root Menu".  The menu is flashing and seems to be stretched and displayed twice over itself.

Anyways, I am much happier that I finally took the time to enable the Autobuilds.

Cheers,
Rocko262c

---

### Post by Rocko262c on 2011-10-02
Dear Everyone,

The fix I have above only worked for about a day and I really didn't like the Autobuilds as I encountered numerous errors and constant change in my system. The internal player on Mythbuntu/Mythtv I found isn't so great.  Here is a much much much much much better solution:

1. Install Xine by going to the terminal and typing "xine". There will be a message and it will tell you to install "xine-ui". Maybe as time goes on, the message might say something else. Just follow the directions in the future according to the output.
2. Go to Synaptic Package Manager and search and mark "xine-ui" and mark the other files required for installation, apply (install)
3. Go to MythFrontEnd and then go to Utilities/Setup->Setup->Media Settings->Player Settings and edit the following entries:
     DVD Player:  xine -f dvd://
     DVD Drive:   /media/cdrom0     (that is a zero and not an O)

I didn't even have to reboot!

Hope it helps, I really enjoy my Mythbuntu/Mythtv much better now.

Cheers,
Rocko262c

---

### Post by nickrout on 2011-10-02
> **Rocko262c said:**
> 
I didn't even have to reboot!



What a strange thing to say, why would this change, or anything like it, ever need a reboot?

You'll find that before long your fix will not work because support for external players is largely disappearing.

---

### Post by Rocko262c on 2011-10-02
> **nickrout said:**
> What a strange thing to say, why would this change, or anything like it, ever need a reboot?
HAHAHAHAHAHAHAHAHAHAHAHA!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!! You have to constantly reboot Ubuntu, MythTV/Mythbuntu, and other versions of Linux for many installations or modifications to work. I am not sure if you are joking, but you are funny. For instance, please read EVERY Linux forum about "RestrictedFormats/PlayingDVDs" and you will see that you need to reboot. I can give you more examples if you wish.



> **nickrout said:**
> You'll find that before long your fix will not work because support for external players is largely disappearing.
Wow, it was Dec 2010 when I posted my last comment till now Oct 2011 and the Xine fix has continued to work till now for almost 1 year. Sorry, but I should have posed my fix a long time ago.

---

### Post by nickrout on 2011-10-02
> **Rocko262c said:**
> HAHAHAHAHAHAHAHAHAHAHAHA!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!! You have to constantly reboot Ubuntu, MythTV/Mythbuntu, and other versions of Linux for many installations or modifications to work. I am not sure if you are joking, but you are funny. For instance, please read EVERY Linux forum about "RestrictedFormats/PlayingDVDs" and you will see that you need to reboot. I can give you more examples if you wish.

Umm no, about the only time you need to reboot is to update a kernel.

---

