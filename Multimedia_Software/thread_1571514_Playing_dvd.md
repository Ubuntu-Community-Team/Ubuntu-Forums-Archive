---
title: "Playing dvd"
date: 2010-09-09
forum: Multimedia Software
---

### Post by Leshinsky on 2010-09-09
When i go to [https://help.ubuntu.com/7.04/musicvideophotos/C/video.html](https://help.ubuntu.com/7.04/musicvideophotos/C/video.html) and follow the instructions to watch dvds on my computer i reinstall or install 
                 
[LIST]
[*]                                                                     **gxine**                                            
[*]                                                                     **libdvdcss2**                                            
[*]                                                                     **libdvdnav4**                                            
[*]                                                                     **libdvdplay0**                                            
[*]                                                                     **libdvdread3**
[/LIST]

Problem is i can only find libdvdcss2 and libdvdpay4 and gxine.  the rest are not in the synaptic package mananger.  Then when it is downloading the new files it is timing out while waiting for new files to be downloaded.  Any ideas.

---

### Post by Leshinsky on 2010-09-09
When i go to [https://help.ubuntu.com/7.04/musicvideophotos/C/video.html](https://help.ubuntu.com/7.04/musicvideophotos/C/video.html)  and follow the instructions to watch dvds on my computer i reinstall or  install 
                 
[LIST]
[*]                                                                     **gxine**                                            
[*]                                                                     **libdvdcss2**                                            
[*]                                                                     **libdvdnav4**                                            
[*]                                                                     **libdvdplay0**                                            
[*]                                                                     **libdvdread3**
[/LIST]

Problem is i can only find libdvdcss2 and libdvdpay4 and gxine.  the  rest are not in the synaptic package mananger.  Then when it is  downloading the new files it is timing out while waiting for new files  to be downloaded.  Any ideas.

---

### Post by sir_robert007 on 2010-09-09
> **Leshinsky said:**
> When i go to [https://help.ubuntu.com/7.04/musicvideophotos/C/video.html](https://help.ubuntu.com/7.04/musicvideophotos/C/video.html)  and follow the instructions to watch dvds on my computer i reinstall or  install 
                 
[LIST]
[*]                                                                     **gxine**                                            
[*]                                                                     **libdvdcss2**                                            
[*]                                                                     **libdvdnav4**                                            
[*]                                                                     **libdvdplay0**                                            
[*]                                                                     **libdvdread3**
[/LIST]

Problem is i can only find libdvdcss2 and libdvdpay4 and gxine.  the  rest are not in the synaptic package mananger.  Then when it is  downloading the new files it is timing out while waiting for new files  to be downloaded.  Any ideas.


The link you used is for Ubuntu 7.04 and is thus outdated. Heres what I did to get DVD support on my system. First open Synaptic, search for and install ubuntu-restricted-extras if it is not already installed on your system. Then open up a terminal and execute:

sudo /usr/share/doc/libdvdread4/install-css.sh

Be sure to close any media players that are open as errors will occur. If this doesn't work you can add the Medibuntu repository and install libdvdread4, libdvdnav4 and libdvdcss2 from Synaptic.

[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

Here is the link that wil show you how to add the Medibuntu repository. Be sure to press Reload in Synaptic after adding the repository.

Hope this helps

---

### Post by joeaura7 on 2010-09-09
Try to go on the internet and search for those packages and install them (they should be .deb files) and then install the package. There is other software out there that will allow you to watch movies

---

### Post by s.fox on 2010-09-09
Hello,

You are running 7.10 ?   Your profile displays 10.04 :)

[This]("https://help.ubuntu.com/community/RestrictedFormats#Ubuntu%2010.04%20LTS,%209.10,%208.04") should guide you through what you need in order to play the dvd.

Please post back if you have any more queries.

-Silver Fox

---

### Post by andrewthomas on 2010-09-09
**Comprehensive Multimedia & Video Howto**

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by coffeecat on 2010-09-09
> **Leshinsky said:**
> the rest are not in the synaptic package mananger.

That's because you are following a guide for an obsolete and now unsupported version of Ubuntu (7.04 = Feisty Fawn) and you are running 10.04, Lucid Lynx. Packages have changed and the version of libdvdread is now libdvdread4.

You've found libdvdcss2 (presumably from Medibuntu) which you need for decryption of commercial DVDs. For the rest, why not take the easy way and install the pacakage ubuntu-restricted-extras? This will give you a load of multimedia codecs, flash, java and ms core fonts and will ensure you will be able to play DVDs. The Totem Movie Player (Applications > Sound and Video) will play them OK, but while you're installing stuff, try VLC, the best all-round multimedia player there is, and it will play DVDs for you.

As far as your timing out is concerned, this sounds like a separate issue. It may be trouble with the repository server which will resolve itself in a few hours, or you may need to check your internet connection.

---

### Post by Leshinsky on 2010-09-09
When i tried the first guys idea i went into the package mgr and it would not let me in kept saying to go to terminal and do other prompt.  when i did that it would time out again waiting on downloading something.  Now it says that the package mgr is locked by another program.  so i used his terminal prompt from that post and got this error message.

matthew@ubuntu:~$ sudo /usr/share/doc/libdvdread4/install-css.sh
[sudo] password for matthew: 
--2010-09-09 16:18:13--  [http://packages.medibuntu.org/dists/lucid/free/binary-amd64/Packages](http://packages.medibuntu.org/dists/lucid/free/binary-amd64/Packages)
Resolving packages.medibuntu.org... 88.191.82.11
Connecting to packages.medibuntu.org|88.191.82.11|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 8080 (7.9K) [application/octet-stream]
Saving to: `/tmp/dvdcss-ChKUSU/Packages'

100%[======================================>] 8,080       51.5K/s   in 0.2s    

2010-09-09 16:18:14 (51.5 KB/s) - `/tmp/dvdcss-ChKUSU/Packages' saved [8080/8080]

--2010-09-09 16:18:14--  [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_amd64.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_amd64.deb)
Resolving packages.medibuntu.org... 88.191.82.11
Connecting to packages.medibuntu.org|88.191.82.11|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 38080 (37K) [application/octet-stream]
Saving to: `/tmp/dvdcss-ChKUSU/libdvdcss.deb'

100%[======================================>] 38,080      80.6K/s   in 0.5s    

2010-09-09 16:18:15 (80.6 KB/s) - `/tmp/dvdcss-ChKUSU/libdvdcss.deb' saved [38080/38080]

dpkg: status database area is locked by another process
Dynamic fetch failed; Falling back to static fetch
--2010-09-09 16:18:15--  [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.2medibuntu1_amd64.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.2medibuntu1_amd64.deb)
Resolving packages.medibuntu.org... 88.191.82.11
Connecting to packages.medibuntu.org|88.191.82.11|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 37252 (36K) [application/x-debian-package]
Saving to: `/tmp/dvdcss-ChKUSU/libdvdcss.deb'

100%[======================================>] 37,252      78.7K/s   in 0.5s    

2010-09-09 16:18:16 (78.7 KB/s) - `/tmp/dvdcss-ChKUSU/libdvdcss.deb' saved [37252/37252]

dpkg: status database area is locked by another process
matthew@ubuntu:~$ 


Any ideas and what other programs can i just download right now to watch dvds that i dont have to be messing with this crap.

Thank you for your help.

---

### Post by FinalShot on 2010-09-09
> **andrewthomas said:**
> **Comprehensive Multimedia & Video Howto**

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
This worked for me, on 10.04.

---

### Post by cariboo on 2010-09-09
Please don't create multiple threads on the same subject, I have merged your two threads.

---

### Post by Leshinsky on 2010-09-09
Thanks guys got it figured out.  THis issue is closed.

---

### Post by sir_robert007 on 2010-09-09
> **Leshinsky said:**
> 
dpkg: status database area is locked by another process


Did you close all media players that were open? I got this error the first time I tried it. So then I closed all open media players, ran it again and it installed correctly.

---

### Post by Leshinsky on 2010-09-09
I figured it out.  Now next item is my WIFI card.  I have a sony vaio.  any ideas.

---

