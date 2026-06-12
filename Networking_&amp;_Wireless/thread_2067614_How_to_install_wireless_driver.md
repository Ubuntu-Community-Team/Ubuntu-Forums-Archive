---
title: "How to install wireless driver :?"
date: 2012-10-07
forum: Networking &amp; Wireless
---

### Post by Fxy on 2012-10-07
HI

Recently I bought a new wireless dongle for my pc.  Unfortunately it does not work out of the box, but the drivers for it are included on a cd. The driver comes in the form of "RTL8188SU_usb_linux_v2.6.0006.20100625.zip" but for the life of me I do not know how to install it !!  Can anyone give me steps on how to install it :?



Thanks in advanced...

---

### Post by mikewhatever on 2012-10-07
Well, .zip is an archive, so the first step would be to right click, and select Extract Here. You should get a folder with included files, sometimes, there is an installation script, install.sh, for example, in which case you just run it.

That said, the date of the archive (2010.06.25) indicates that it's rather old, and I rather doubt it will work well, if at all. Try a more recent version of [RTL8188SU from Realtek]("http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8191SU").

To get that one working, (after extracting), note where the folder is. Mine is in Downloads, so:

```
cd Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405

sudo bash ./install.sh
```

---

### Post by Fxy on 2012-10-07
> **mikewhatever said:**
> Well, .zip is an archive, so the first step would be to right click, and select Extract Here. You should get a folder with included files, sometimes, there is an installation script, install.sh, for example, in which case you just run it.

That said, the date of the archive (2010.06.25) indicates that it's rather old, and I rather doubt it will work well, if at all. Try a more recent version of [RTL8188SU from Realtek]("http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8191SU").

To get that one working, (after extracting), note where the folder is. Mine is in Downloads, so:

```
cd Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405

sudo bash ./install.sh
```

Thanks for the reply :-)

If the one I have is outdated, then I think your mentioned one might be better to use so i'll give it a try.

---

### Post by Fxy on 2012-10-07
Ok so I have downloaded the .zip & extracted it.  Whenever i open it, i'm presented with 3 folders...
```
documents, driver & wpa_supplicant
```

What is the next step from here :?

---

### Post by mikewhatever on 2012-10-07
I am afraid we've not downloaded the same files. After downloading RTL8188SU for Linux, I get the archive named
```
RTL819xSU_usb_linux_v2.6.6.0.20120405.zip
``` 

...and after extracting, there is only one folder named 
```
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405
```

There are lots of different drivers on that page, please varify you've got the right one.

---

### Post by Fxy on 2012-10-07
Ok so i re-downloaded the zip & everythings good this time.

I followed your instructions as below...
```
cd Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405

sudo bash ./install.sh
```
...but it didn't work !!  It looked as if it was working when I ran install.sh but at the bottom/end it gave an error.
```
compile make driver error: 2
please check error mesg
```

---

### Post by mikewhatever on 2012-10-07
Here is a similar thread [http://ubuntuforums.org/showthread.php?t=2055670&highlight=8188su](http://ubuntuforums.org/showthread.php?t=2055670&highlight=8188su). They've tried installing the same driver and also got the same error. Are you also on Lucid (10.04)?

---

### Post by Fxy on 2012-10-07
> **mikewhatever said:**
> Here is a similar thread [http://ubuntuforums.org/showthread.php?t=2055670&highlight=8188su](http://ubuntuforums.org/showthread.php?t=2055670&highlight=8188su). They've tried installing the same driver and also got the same error. Are you also on Lucid (10.04)?

Ok so I went and installed "build-essential" using the cd but I still get the same error message...

...No im not using 10.04. I wanted to go back to my ubuntu roots so i installed 8.04

---

### Post by chili555 on 2012-10-07
Did you also install *linux-headers-generic*?

---

### Post by Fxy on 2012-10-08
> **chili555 said:**
> Did you also install *linux-headers-generic*?

No I didn't install "linux-headers-generic" but when I'm back at the computer later I will install :-)

---

### Post by Parker32 on 2012-10-08
Use a wired network first. Then when you go to Windows Update you will find some wireless network driver listed there (possibly Intel or RealTEK Semi-conductor blah...blah). Select it, and install it. I think that will do!

---

### Post by Fxy on 2012-10-08
> **Parker32 said:**
> Use a wired network first. Then when you go to Windows Update you will find some wireless network driver listed there (possibly Intel or RealTEK Semi-conductor blah...blah). Select it, and install it. I think that will do!

Sorry but I don't have access to a wired connection !!

---

### Post by Marthewicked on 2012-10-08
if you have another computer or laptop, use the internet from that PC. if it is a ubuntu running computer then click on the wireless connection on top right corner or where ever it is on your version and  > click on edit connections on the bottom...>  click echo auto...>  edit...click ip4settings...>  on method choose shared to other computers.  After you do this connect ethernet wire between computers. You will be connected sometimes longer sometimes short but enough to download drivers.  I did that from my laptop to desktop and it works.

---

### Post by Fxy on 2012-10-08
> **Marthewicked said:**
> if you have another computer or laptop, use the internet from that PC. if it is a ubuntu running computer then click on the wireless connection on top right corner or where ever it is on your version and  > click on edit connections on the bottom...>  click echo auto...>  edit...click ip4settings...>  on method choose shared to other computers.  After you do this connect ethernet wire between computers. You will be connected sometimes longer sometimes short but enough to download drivers.  I did that from my laptop to desktop and it works.

Thanks for the advice :-)  I have a MacBook that I can share the Internet from so when I get home from work ill give it a whirl...

---

### Post by Fxy on 2012-10-08
Ok so internet sharing from my macbook doesn't seem to work via ethernet !!  To make sure everything I done was correct, I googled it & followed steps partly from ["here"]("http://outerware.blogspot.co.uk/2011/01/finally-internet-between-mac-and-ubuntu.html")  ...Anyone any ideas :?

---

### Post by Cheesemill on 2012-10-08
If you are trying to use 8.04 then there is no surprise that you can't get things working properly.

8.04 reached end of life about a year and a half ago and as such doesn't have access to the software you need to get this driver working (as well as not being supported and having major security issues which wont ever get fixed).

Also a huge amount of wireless drivers have been added to the kernel in the last 4 years meaning on the latest versions of linux there is a chance that your adapter will work out of the box.

There is no good reason at all to attempt to run 8.04 over 4 years after it was released.

There have been 8 completely new versions of Ubuntu since then. What you're trying to do is like attempting to get drivers for new hardware for Windows 98, it's just not feasible.

---

### Post by Fxy on 2012-10-08
> **Cheesemill said:**
> If you are trying to use 8.04 then there is no surprise that you can't get things working properly.

8.04 reached end of life about a year and a half ago and as such doesn't have access to the software you need to get this driver working (as well as not being supported and having major security issues which wont ever get fixed).

Also a huge amount of wireless drivers have been added to the kernel in the last 4 years meaning on the latest versions of linux there is a chance that your adapter will work out of the box.

There is no good reason at all to attempt to run 8.04 over 4 years after it was released.

There have been 8 completely new versions of Ubuntu since then. What you're trying to do is like attempting to get drivers for new hardware for Windows 98, it's just not feasible.

Ok so the reason i went ahead & installed 8.04 is because i wanted to go back to my ubuntu roots & get my desktop computer looking like it once did !!  Is there no way I can update the kernel in 8.04 to the latest version :? Or is there another os alternative that would work with my connection, but still allows me to install gtk themes from gnome-look ...

---

### Post by Cheesemill on 2012-10-08
Debian Stable still uses Gnome 2 as it's GUI and is likely to be supported for another few years.
Also Ubuntu is based on Debian so they both share the same apt-get commands and have similar repositories.

Downloads are here:
[http://www.debian.org/CD/http-ftp/#stable](http://www.debian.org/CD/http-ftp/#stable)
You just need to download the correct CD-1 for your architecture (either amd64 or i386).

---

### Post by Fxy on 2012-10-08
> **Cheesemill said:**
> Debian Stable still uses Gnome 2 as it's GUI and is likely to be supported for another few years.
Also Ubuntu is based on Debian so they both share the same apt-get commands and have similar repositories.

Downloads are here:
[http://www.debian.org/CD/http-ftp/#stable](http://www.debian.org/CD/http-ftp/#stable)
You just need to download the correct CD-1 for your architecture (either amd64 or i386).

Thanks ill go give it a try & report back if it works ;-)

---

### Post by Fxy on 2012-10-14
Everything worked perfetly with Debian :-) Thanks everybody for the help...

---

