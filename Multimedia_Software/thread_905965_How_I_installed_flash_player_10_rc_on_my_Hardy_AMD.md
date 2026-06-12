---
title: "How I installed flash player 10 rc on my Hardy AMD64 box!"
date: 2008-08-30
forum: Multimedia Software
---

### Post by tooferson5 on 2008-08-30
Hey all,

If some of you like me are having massive headaches trying to install the newest flash on your 64 machines, this is how I finally got it to work.

Used steps 1, 2, and 3 from [http://www.myscienceisbetter.info/2008/05/install-adobe-flash-player-10-on-ubuntu-using-nspluginwrapper.html]("http://www.myscienceisbetter.info/2008/05/install-adobe-flash-player-10-on-ubuntu-using-nspluginwrapper.html")

Then on the same page scroll all the way down to the comments and install the 32bit libs you need.


> 
By Nate on August 20, 2008 10:18 PM

I got it working now... there may be more recent instructions out there, but yours worked with the latest Flash Player 10 RC. As for the missing 32-bit libraries, I just got them manually from Ubuntu's archives.

Unpack the libs from each of these packages to /usr/lib32/:
libnss3-1d
libnspr4-0d
libcurl3

Get them from:
[http://us.archive.ubuntu.com/ubuntu/pool/main/n/nss/libnss3-1d_3.12.0.3-0ubuntu5_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/n/nss/libnss3-1d_3.12.0.3-0ubuntu5_i386.deb)
[http://us.archive.ubuntu.com/ubuntu/pool/main/n/nspr/libnspr4-0d_4.7.1+1.9-0ubuntu0.8.04.5_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/n/nspr/libnspr4-0d_4.7.1+1.9-0ubuntu0.8.04.5_i386.deb)
[http://us.archive.ubuntu.com/ubuntu/pool/main/c/curl/libcurl3_7.18.2-1ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/curl/libcurl3_7.18.2-1ubuntu1_i386.deb)

(Just extract them, don't try to install directly. Look in the data.tar.gz tarball for the actual libs, unpack to /usr/lib32/)

And of course the latest Flash download URL from Adobe:
[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)


You can then download the .deb from the link above and continue with your install.  You can also do it by following the instructions on [http://meandubuntu.wordpress.com/2008/08/20/flash-10-rc-on-ubuntu-amd64/]("http://meandubuntu.wordpress.com/2008/08/20/flash-10-rc-on-ubuntu-amd64/").  You can skip step involving getlibs since we already have them in our lib32 folder.  Note I did not run the script.  Just copy and pasted the lines into the terminal.

Now, flash 10 is supposed to have flawless fullscreen playback but mine absolutley sucked.  Could not find and answer so I figured I'd update my graphics driver.  Running Ati X1100. I followed the METHOD #2, THE MANUAL WAY instructions on  [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide")

A note on doing this is that when it says you have to edit the /etc/X11/xorg.conf, remember to delete the old information about your graphics card or copy over it.  I left both new and old information in my file and my screen went to the ugly 600x400 when I restarted my computer because there was a conflict.  Retraced my steps and it fixed the issue and now I have the latest version of flash 10 and ATI driver installed on my Hardy 64 box and fullscreen flash looks amazing.

Enjoy!

---

