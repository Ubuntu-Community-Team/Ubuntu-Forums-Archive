---
title: "Unable to play DVD -"
date: 2011-10-09
forum: Multimedia Software
---

### Post by blasptor on 2011-10-09
Hello everyone,

I am brand new to Ubuntu and have been only using it for less than two weeks.

About 2 days ago I tried to watch a DVD on my computer, but I was met with this message:

Could not read DVD. This may be because the DVD is encrypted and a DVD decryption library is not installed.

After some googling I found that I had to install a couple of things, so this is what I have done so far:

sudo apt-get install ubuntu-restricted-extras
sudo /usr/share/doc/libdvdread4/install-css.sh

wget -c [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb) sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_i386.deb
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list 
http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && 
sudo apt-get --quiet update && sudo apt-get --yes --quiet 
--allow-unauthenticated install medibuntu-keyring && 
sudo apt-get --quiet update

sudo apt-get --yes install app-install-data-medibuntu apport-hooks-medibuntu

And probably others, but I have been unable to actually play a DVD.
I have restarted my computer (MacbookPro 5.5) with Ubuntu 11.04, but I keep getting
the error above every time.

And I really have no idea what else to do.

Any help is greatly appreciated!

---

### Post by WasMeHere on 2011-10-09
In general, I recommend that you try this thread: [_**[COLOR="Red"]Comprehensive Multimedia & Video Howto[/COLOR]**_]("http://ubuntuforums.org/showthread.php?t=766683")
It may take some time, but the result is very good, you will get a solid multimedia system.

Have fun
Olle

---

