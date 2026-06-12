---
title: "Installing Software Offline"
date: 2011-06-24
forum: Multimedia Software
---

### Post by Ashkwil on 2011-06-24
Hi I have an offline Ubuntu 10.10 install at another house, i cannot bring it to this house to install the software I need.

I would like to install a program which can convert a CD to MP3 files.

Can anyone tell me how i cant get this software onto a USB and then how i can install it when I take it to the other computer?

Thanks a lot :)

EDIT: The computer with internet acccess is Windows 7 not Ubuntu!

---

### Post by icp on 2011-06-24
Hi! I think you could do that whit rhythmbox (pre-installed) if I'm wrong you should try [sound juicer]("http://burtonini.com/blog/computers/sound-juicer"), if you don't have internet on the ubuntu pc you have to download the .deb package and pass it on the ubuntu pc whit an USB key.. If this program tell you that can't do this maybe you must install ubuntu-restricted-extras (sure download the .deb file and pass it whit USB).
Cheers!

---

### Post by Rubi1200 on 2011-06-24
Take a look at whether APTonCD would suit your needs:
[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

It is available via the Ubuntu Software Center.

---

### Post by kvarley on 2011-06-24
Hit Alt + F2 on your machine with internet and enter the following and hit enter:

> gksudo nautilus /var/cache/apt/archives/

The filemanager that opens with have sudo permissions so be careful! However, delete all the files within this directory.

In terminal do:

> sudo apt-get -d install sound-juicer gstreamer0.10-plugins-ugly

This won't install anything on your system but it will download the packages required. In the nautilus window you will see the debs appear for sound juicer and the gstreamer ugly codecs. This is what you will copy to your removable media and transfer them to the computer without internet access.

Once done close the nautilus window which has sudo permissions. :)

---

### Post by Ashkwil on 2011-06-24
Hi forgot to mention the online computer i am downloading it on is Windows 7  not Ubuntu!

Sorry i forgot to mention that! And thanks for quick reply

---

### Post by Ashkwil on 2011-06-25
BUMP, any ideas anyone?

---

### Post by kostkon on 2011-06-25
> **Ashkwil said:**
> Hi forgot to mention the online computer i am downloading it on is Windows 7  not Ubuntu!

Sorry i forgot to mention that! And thanks for quick reply
Check [keryx]("http://keryxproject.org/").

---

### Post by Ashkwil on 2011-06-25
I have tried but havent been successful in getting it to work it just hangs on  loading screen on my Win7.

Isnt there any other way then? Can i not download the package to a USB and then install it on the ubuntu, i take it tis much more complicated than that!

---

### Post by Ashkwil on 2011-06-25
Actually i think i may have got it working ill let you guys know

---

