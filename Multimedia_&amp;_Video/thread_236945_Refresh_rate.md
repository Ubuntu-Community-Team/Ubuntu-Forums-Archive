---
title: "Refresh rate"
date: 2006-08-15
forum: Multimedia &amp; Video
---

### Post by ssmokn on 2006-08-15
Hi,

I'm a recent convert to Linux and Ubuntu.  I tried out 6.06 a few weeks ago on a spare machine and liked it so much that I rebuilt my primary system with 6.06.1 a day or so ago. 

I built the system with one monitor and later decided to trade up to my better monitor (since this is really going to be my primary system from now on).

The new monitor is a Samsung SyncMaster 204T.  After installing the new monitor I ran the following commands to update /etc/X11/xorg.conf

sudo /etc/init.d gdm stop
sudo dpkg-reconfigure xserver-xorg

The reconfigure was successful and all the settings were properly identified.  During the reconfigure I selected 1600x1200 at 60Hz the resolution/refresh that I need.

Restarted the system and my monitor has a popup (not Ubuntu but my Samsung monitor) stating that I'm not running at optimal which is 1600x1200 at 60Hz.

When checking screen resolution in GNOME I see 1600x1200 at 65Hz.

I've run the reconfigure about a dozen time trying different things and I cannot get this to work (plus when I take all the defaults everything is recognized properly).

I've searched on Ubuntu forms and google looking for tips on how to configure this.   The most promising was adding _60 to my xorg.conf file (that is changing the appropriate config setting from "1600x1200" to 1600x1200_60").  Once I did that I didn't even have 1600x1200 as an option.

This is annoying because I'm not running the appropriate refresh and I get a popup from my monitor every time I boot that I must acknowledge with one of the monitor buttons to get rid of it.

I'm running an MSI motherboard using the Intel i810

Output from lspci | grep VGA follows:
0000:00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)

I even tried booting from the install CD again and I got the same monitor popup.  It seems like dpkg-reconfigure is getting everything right BUT for some reason when gdm starts I end up with 65Hz instead of 60Hz.

Any tips or pointers to information on how to configure this properly would be greatly appreciated.

Ubuntu is an awesome piece of work!  Kudos to everyone involved in creating and supporting this wonderful product.

---

### Post by tseliot on 2006-08-15
Try this guide:
[http://doc.gwos.org/index.php/ChangeResolution](http://doc.gwos.org/index.php/ChangeResolution)


OR this one (read where it says "Getting the Right Mode for an LCD monitor"):
[https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration](https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration)

---

### Post by ssmokn on 2006-08-15
I looked at both links you provided (thanks) but still no joy.

My "Monitor section started out like this as configured by dpkg-reconfigure (and they are accurate):

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
        HorizSync	30-81
        VertRefresh	56-75
EndSection

Per the instructions in the second link I did the following:

gtf 1600 1200 60 which generated the following Modeline:

Modeline "1600x1200_60.00"  160.96  1600 1704 1880 2160  1200 1201 1204 1242 -HSync +Vsync

I added that to the "Monitor section along with the other parameters (option, HorzSync and VertRefresh) and later without them.

This did not work.  I lost 1600x1200 all together and the monitor would only do 1280x1024 in GDM (1600x1200 didn't even show up anymore)


Section "Monitor"
	Identifier	"SyncMaster"
        Option		"DPMS"
        HorizSync	30-81
        VertRefresh	56-75
        Modeline "1600x1200_60.00"  160.96  1600 1704 1880 2160  1200 1201 1204 1242 -HSync +Vsync
EndSection

Then I tried the info using the first link you provide and created the Modeline statement from the website using.  This generated a Modeline of 

Modeline "1600x1200" 170.89  1600 1688 1896 2288  1200 1200 1203 1244 	

I replaced the previous modeline with this one.

Again my screen went to 1280x1024 but in Gnome I had a 1600x1200 option (out of order from the others).  When selected my screen was desktop appeared to be 1600x1200 on 1280x1024 so this really didn't work either. 

Am I missing something?  I'd really like to "fix" this.  Thanks again.

---

### Post by tseliot on 2006-08-15
Since yours is an Intel card I think that you should do:
```
sudo apt-get install 915resolution
```

then run that application

---

