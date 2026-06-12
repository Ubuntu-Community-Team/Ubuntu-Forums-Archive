---
title: "Troubleshooting - Ubuntu LTS Shared Drive with Macbook OSX"
date: 2010-07-22
forum: Networking &amp; Wireless
---

### Post by Marzipan_D on 2010-07-22
This is what I am trying to do. I have a Ubuntu 10.04 LTS as my primary desktop computer. It has 2 hard drives, which are both currently mounted correctly. 

The first drive is my OS/Ubuntu drive (150GB). The second drive is a 500GB hard drive where all my files are stored. 

I want to be able to share my second drive (500GB) to my macbook. 

I orignally found this article: [http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/](http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/)

Although I really wasn't trying to do a backup with time machine, i thought it might be a start. This article got me going ok with "Netatalk", but then instead of replacing the default values in step 2, i replaced the whole config file (/etc/default/netatalk), Oops. I tried reinstalling that dang Netatalk, but no dice. There was still no new config file (/etc/default/netatalk).

At this point, i ditched these instructions and went to these instructions. [http://ubuntuforums.org/showthread.php?t=410274](http://ubuntuforums.org/showthread.php?t=410274)

These worked really well. I went to my mac and hit Control-K, added the IP to my Ubuntu desktop, and presto! I could see my hard drive.

The only issue now is, I can't see the second hardrive (500GB), only the primary hard drive (150GB). I installed Samaba, and shared the drive out (by right clicking the drive in the file manager, and selecting "Sharing Options"). Per other forum posts, I selected all the check boxes available, and selected "yes" to auto change permissions when that dialog box appeared. 

I reconnected in my Macbook OS 10.5.8, and I can still only see the primary hard drive (150GB). 

Any thoughts, on how I might see the second drive (500GB)?

Thank in advance :-)

---

