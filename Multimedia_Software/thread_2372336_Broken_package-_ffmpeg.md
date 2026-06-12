---
title: "Broken package- ffmpeg?"
date: 2017-09-23
forum: Multimedia Software
---

### Post by net-alexander on 2017-09-23
Excuse my English: D, I have problems with my 'software center' does not install anything, try installing ffmpeg first using:
```
sudo add-apt-repository ppa:jonathonf/ffmpeg-3
sudo apt-get update
sudo apt install ffmpeg libav-tools x264 x265
sudo add-apt-repository ppa:jonathonf/tesseract
```
Then I went to the 'software center' but there were errors saying that I could not install anything and from broken packages, I tried to repair myself but could not, I proceeded to execute:
```
sudo apt-get remove ffmpeg
sudo apt-get remove --auto-remove ffmpeg
sudo apt-get purge ffmpeg
sudo apt-get purge --auto-remove ffmpeg
```
the "software center" still does not work, when trying to repair itself.

This comes to me:
```
InstallArchives() failed: (Reading database ...
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 512471 files and directories currently installed.)
Preparing to unpack .../ffmpeg_7%3a3.3.4-1~14.04.york1_i386.deb ...
Unpacking ffmpeg (7:3.3.4-1~14.04.york1) ...
dpkg: error processing archive /var/cache/apt/archives/ffmpeg_7%3a3.3.4-1~14.04.york1_i386.deb (--unpack):
trying to overwrite '/usr/bin/ffmpeg', which is also in package clipgrab 3.6.4~trusty1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
/var/cache/apt/archives/ffmpeg_7%3a3.3.4-1~14.04.york1_i386.deb
Error in function:
dpkg: dependency problems prevent configuration of libav-tools:
libav-tools depends on ffmpeg; however:
Package ffmpeg is not installed.


dpkg: error processing package libav-tools (--configure):
dependency problems - leaving unconfigured
```
---
help me¡ :(

---

### Post by mc4man on 2017-09-23
You could either - 
Install the .deb with dpkg using a --force-overwrite option 
or 
remove that clipgrab package which installed a symlink named ffmpeg to /usr/bin (it links to avconv, pretty dumb method
The later method is probably your best bet.

---

### Post by deadflowr on 2017-09-23
*Thread moved to **Multimedia Software***

---

### Post by ian-weisser on 2017-09-25
The problem is written in plain language:
> [COLOR=#000000][FONT=&quot]dpkg: error processing archive /var/cache/apt/archives/ffmpeg_7%3a3.3.4-1~14.04.york1_i386.deb (--unpack):
[/FONT][/COLOR][COLOR=#000000][FONT=&quot]trying to overwrite '/usr/bin/ffmpeg', which is also in package clipgrab 3.6.4~trusty1[/FONT][/COLOR]

Each file can be installed by only one package. When two packages try to install the same package, they *conflict*.
You cannot have both packages installed at once. Decide which package you want, and forget about the other. This is the path that mc4man recommended, and I agree.

It's also possible to override to install both, as mc4man mentioned.
However, this path will lead to many, many more apt errors for you to learn and love in the future. If you are not skilled at apt troubleshooting, then I strongly suggest avoiding --force-overwrite.

---

### Post by mc4man on 2017-09-25
What could also work is just to remove the /usr/bin/ffmpeg file (link) that clipgrab installed.
Then your ffmpeg package would install & it's possible clipgrap would still work as it's functions use ffmpeg binary.

What they did for 14.04 which doesn't have ffmpeg is just create a link named ffmpeg to avconv. Otherwise they could have modified their code completely to use avconv directly. Could of been more work than anyone wanted to do..

(- in essence the same as a force, in this case pretty safe as far as package management..

Re-edit:
What a wierdly done app. It needs 'ffmpeg' but uses avconv in 14.04. So it won't encode if ffmpeg binary isn't in your $PATH but then goes ahead with an avconv command to encode.
In use it does not need the symlink itself.

Ex. ( I just extracted the clipgrab binary & put in ~/bin, have ffmpeg installed here & also avconv
> 
apt-cache policy ffmpeg
ffmpeg:
  Installed: 7:3.3.3~trusty2
  Candidate: 7:3.3.3~trusty2
  Version table:
 *** 7:3.3.3~trusty2 0
        500 [http://ppa.launchpad.net/mc3man/trusty-media/ubuntu/](http://ppa.launchpad.net/mc3man/trusty-media/ubuntu/) trusty/main amd64 Packages
        100 /var/lib/dpkg/status
doug@doug-Lenovo-IdeaPad-Y510P:~$ clipgrab
Adding Equifax CA certificate 
Discovered:  "WILL IT BITE?! - BIG CREEPY SPIDER!" 
"WILL IT BITE! - BIG CREEPY SPIDER!" 
Downloading video file: 
blah, blah..
Executing ffmpeg:  "[COLOR="#FF0000"]avconv[/COLOR] -y -i "/tmp/clipgrab-download-Lh3256" -i "/tmp/clipgrab-download-XM3256" -acodec copy -vcodec copy -f mp4 "/tmp/clipgrab-concat--nS3256"" 
"avconv version 11.3-6:11.3-1~ppa1, Copyright (c) 2000-2014 the Libav developers
  built on Jan 27 2017 00:32:07 with gcc 4.8 (Ubuntu 4.8.4-2ubuntu1~14.04.3)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '/tmp/clipgrab-download-Lh3256':
ect., ect.

---

