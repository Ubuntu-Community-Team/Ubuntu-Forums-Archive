---
title: "Agh! How do I install ATI drivers?"
date: 2006-06-23
forum: Multimedia &amp; Video
---

### Post by Albi on 2006-06-23
I went to the ATI site, downloaded the driver file, opened it, and selected the first option (Install Driver 8.25.18 on X.org 7.0.x), and went on with the installation, but then I realized that the second option to install distribution specific packages was more appropriate.  The only problem is that this generates a VERY long list, and I can't fit the thing on my screen to click Ok and go on with the installation (screenshot included).
Is there another way to install my ATI RADEON 9600 Pro drivers or perhaps fix this problem (btw my max resolution is 1280x1024, I can't fit it).

---

### Post by tommohawk on 2006-06-23
Open a terminal window and cd to the directory where you downloaded the ati driver file.

Type the following:

```
sudo ./ati-driver-installer-8.25.18-x86.run --buildpkg Ubuntu/dapper
```

That should build the packages for you the same as using the graphical version does.  You can then install them.  It is not always necessary to do it this way. The normal install method does work with some (but not all) ATI cards.

Check this link..

[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

---

### Post by strabes on 2006-06-23
The first method in the wiki that tommohawk posted worked quite nicely. I am now up to 1440x900 but only 60hz. However, I would still like both of those to be increased, as even my old Radeon 7200 on my old 1.5ghz computer could run 75hz with 1600x1200.

---

