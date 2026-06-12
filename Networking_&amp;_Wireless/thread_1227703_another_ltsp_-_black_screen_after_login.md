---
title: "another ltsp - black screen after login"
date: 2009-07-31
forum: Networking &amp; Wireless
---

### Post by trinitycsi on 2009-07-31
Loaded Juanty on a  ltsp server build. I have the exact issues that have been posted before. client login and then black screen and mouse cursor.

I tried a different client PC and the screen came up but it was mirrored and the boxes/text were also upside down. really weird.

Anyway I need to get the older PCs working. they have the ITOX G4V620-B-G  motherboard in them: [http://www.itox.com/pages/products/mothers/revcontrol/g4v620-b-g.php](http://www.itox.com/pages/products/mothers/revcontrol/g4v620-b-g.php)

The ltsp server hardware is a Gigabyte GA-P43-ES3G board with an Nvidia 8400GS card in it. I was really wanting to load the 64-bit Juanty so that I could use 8 GB of ram. I went down to the 32 bit version making sure that was not the problem, but still had issues. 

downgraded to 8.10 for good measure but same issue. I've tried to look at the logs but I'm not really sure what I'm exactly looking at. I'm a strong windows guy but a weak to mid linux guy so I need a little hand holding.

Any help would be greatly appreciated. This is for a school computer lab and school starts Monday.

Thanks

Andy

---

### Post by trinitycsi on 2009-08-02
ok, will this work?

I used a client PC and a temp LTSP server. loaded it up etc. the other client boots normally. Can I copy the /opt/ltsp folder to the rea; server and get it to work?

If so how do I copy the LTSP image file and the i386 folder?

Thanks

---

### Post by trinitycsi on 2009-08-03
OK I'm an idiot. I figured out my issue. I reloaded the server with the 64 bit version. found this in the ltsp quick install acticle linked below:

[IMG]https://help.ubuntu.com/htdocs/ubuntunew/img/alert.png[/IMG] **If you are on a 64-bit system** but your clients have another architecture use the --arch option eg. sudo ltsp-build-client --arch i386 


[https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall](https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall)

did that and let 9.04 build an i386 image then bam everything worked like it should have last tuseday when I started down this windy road. Seeing that the school year starts in about 8 hours I guess it was just in the nick of time.

---

### Post by iskibinski on 2009-09-13
I have this exact problem.  The server does have a 64bit processor but has the i386 distribution of ubuntu (9.04) installed.  Nonetheless I tried rebuilding the client with --arch i386 to no avail (exact same problem occurs as before).

Any ideas what else could be causing this?

---

