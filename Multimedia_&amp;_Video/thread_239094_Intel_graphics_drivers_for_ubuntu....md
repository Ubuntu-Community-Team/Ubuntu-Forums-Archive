---
title: "Intel graphics drivers for ubuntu...?"
date: 2006-08-18
forum: Multimedia &amp; Video
---

### Post by TH3W1R3D on 2006-08-18
I have intel® 82852/82855 Graphics and am having a problem where I cannot display the resolution at what it should be (its too low). I HAVE looked all over the forum and tried many things with no luck.  ](*,)Does anyone know if the intel drivers for linux work on Ubuntu? They work on Red Hat and thats all I know. [http://downloadfinder.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=922&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21](http://downloadfinder.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=922&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21)

Another thing how do I install these? I am very new with Linux so I dont know much about tar.gz and how to install um.

---

### Post by abijah on 2006-08-18
I really hope u find out b/c i been having the same problem!

I've been working a few days on this and i just can't get it to work.

I too shed tears

---

### Post by skattman83 on 2006-08-18
Actually, someone correct me if I'm wrong, but you dont need drivers.  Intel graphics don't offer 3d acceleration in linux, but you get 2d out of the box.  All you need to do for a different resolution is to edit your xorg configuration file.  Do a ```
sudo gedit /etc/Xll/xorg.conf
``` I'm not sure offhand, but there's a section that lists a bunch of resolutions.  At the top of that section it says what diplay depth is default.  You probably want to set that to 16 or 24, if its not already.  Then go to that section and it'll probably have a bunch of stuff like ```
"1024x768" "800x600"
``` and so on.  Just add the resolution you want in front of those, like if you wanted 1280 by 1024, change that line to ```
"1280x1024" "1024x768" "800x600"
```  You can find a lot more information on editing that config file if you search the forums for xorg.conf or xorg.  Good luck though!

---

### Post by givré on 2006-08-18
I have the same card and i can say that it provide 3D acceleration (i'm running compiz with aiglx at this moment :D )
For your resolution problem, you may have a look there:
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)
especily the part about 855 / 865 / 915 Intel graphic chipset

---

### Post by TH3W1R3D on 2006-08-18
@Skattman83 I have tried and that method does not work for me.
@givre I could really use more help from you since you seem pretty experienced. Check your PMs.

---

