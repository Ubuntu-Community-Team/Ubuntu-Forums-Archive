---
title: "Gnuradio failed"
date: 2015-03-21
forum: Multimedia Software
---

### Post by numeric2 on 2015-03-21
Hello,

wget [http://www.sbrac.org/files/build-gnuradio](http://www.sbrac.org/files/build-gnuradio) && chmod a+x ./build-gnuradio && ./build-gnuradio

This command successfully installed gnuradio, just a few months ago, on two older computers. My new Dell computer, with latest Ubuntu updates, has not been successful to install gnuradio. Ubuntu is installed on a 1TB USB 3 hard drive with a UEFI boot partition. No problems now booting to Ubuntu. Also installed Ubuntu on a 64 GB USB 3 thumb drive with a UEFI partition. No problems no booting to Ubuntu. 

The above command gets the script "build-gnuradio" from [www.sbrac.org/files/build-gnuradio]("http://www.sbrac.org/files/build-gnuradio"). It is suppose install all required prerequisites and install UHD library and gnuradio. However it fails find "git". If I install git from the ubuntu software installer it installs git ok, but then fails to find cmake. It fails with the next item on the list, till finally it fails totally. The resultant gnuradio is a mess. Probably I failed to choose the correct version of whatever I tried to install. At this point I re-installed Ubuntu and started all over again. Again, The first error is still "git". :-(


The following is the verbose output of the process. Only the end few lines are shown:

[COLOR=#0000ff]Checking for package cmake
Checking for package git-core
Checking for package wget
Checking for package libxi-dev
Checking for package python-docutils
Checking for package gtk2-engines-pixbuf
Checking for package r-base-dev
Checking for package python-tk
Checking for package liborc-0.4-0
Checking for package liborc-0.4-dev
Checking for package libasound2-dev
Checking for package python-gtk2
Checking for package libzmq
Checking for package libzmq-dev
Done checking packages
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libzmq
Failed to find just-installed command 'git' after pre-requisite installation.
This very likely indicates that the pre-requisite installation failed
to install one or more critical pre-requisites for Gnu Radio/UHD[/COLOR]

Suggestions are greatly appreciated.

---

### Post by ajgreeny on 2015-03-21
Why not use the repository version of gnuradio?

Do you need a more recent version than that in the repos?  Mind you, I don't know anything about either of them, nor even what versions they both are.

---

### Post by mc4man on 2015-03-21
The script is using wrong package name of libzmq, it's now libzmq1 ( & only the dev really needs to be named as installing libzmq-dev will install libzmq1
So open your script, go to line 524 & remove libzmq entry ( or if desired rename it libzmq1
Then it's possible it may run though if on a fresh 14.04.2 install you may need to enable the -proposed repo in Software Sources > Updates first, then run script..

---

### Post by numeric2 on 2015-03-21
Thank you for your reply. The last time I checked the repository ot did not have gnuradio. It was there a few months ago. I just checked and found it listed again. Unfortuniately, there were  "[COLOR=#ff0000]Package dependencies cannot be resolved" errors.[/COLOR] "[COLOR=#0000ff]This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time[/COLOR].".
It seems recient package name changes may have broken the install. It did work without problems in the past.

---

### Post by numeric2 on 2015-03-21
> **mc4man said:**
> The script is using wrong package name of libzmq, it's now libzmq1.


Still get errors. It looks like I need to do a re-install of Ubuntu 14.04.2 LTE. 
Thank you for your reply.

---

### Post by mc4man on 2015-03-21
> **numeric2 said:**
> Still get errors. It looks like I need to do a re-install of Ubuntu 14.04.2 LTE. 
Thank you for your reply.
If your errors are with package installs then as mentioned you'll need to either wait a bit or enable the proposed repo with a recent 14.04.2 (HWE) install as libsdl1.2-dev is not installable without the  newer mesa packages (10.1.3-0ubuntu0.4

---

### Post by numeric2 on 2015-03-26
> **mc4man said:**
>  libsdl1.2-dev is not installable without the  newer mesa packages (10.1.3-0ubuntu0.4

[FONT=&amp]Thank you for your reply. 
I have successfully built gnuradio from source; however some of the components are missing for QT based items. For example QT sinks. The QT sinks are listed in the GRC; but, an error is generated, when run. Error: missing QT stuff. Something about Q..4, Q..5, do not remember details.

I looked at 10.1.3-0ubuntu0.4; but, have no clue how to install it. Same is true for [gnuradio-3.7.5.tar.gz]("http://gnuradio.org/redmine/attachments/download/792/gnuradio-3.7.5.tar.gz") the most recent binary I have found. My build from source is newer, but with the above problems. 
This script works, but is an older version[/FONT][FONT=&amp]:  [COLOR=#4472C4]$ sudo apt-get install gnuradio[/COLOR][/FONT]

Part of the problem is that I am not familiar with the installation tools and terms. Such as "out-of-tree", Python, python scripts, sudo, apt-get and many other commands. Much of my time is spend on looking for examples; however many of the references are circular. Kind like catch 22. Never used Python. I am far more familiar with C, C++, Delphi and Windows API even dos and dos bat files. I have a long way to go.

 At the least, Ubuntu 14.04.2 LTE is missing GIT and cmake . Installing git and cmake is simple, just type git and the reply will tell how to install git; the same for cmake. The rest is far more difficult. Some of the example script references out of date.
  Again, thank you for your suggestions.

---

### Post by Geoffrey_Arndt on 2015-03-26
For what it's worth, Gnuradio seems to install fine from Ubuntu Utopic (14.10) standard repo.  No errors reported.   Likely 15.04 should work the same.

---

### Post by numeric2 on 2015-03-29
> **Geoffrey_Arndt said:**
> For what it's worth, Gnuradio seems to install fine from Ubuntu Utopic (14.10) standard repo.  No errors reported.   Likely 15.04 should work the same.

Thank you for the information. I did try Ubuntu 14.10 and found the same gnuradio prerequisites missing as Ubuntu 14.04.2 LTE. I suspect the problem may be computer sensitive. My Dell Inspiron 7000  series with the 5th generation Intel i7 processor has the problem with  gnuradio. By contrast, I successfully installed gnuradio on another computer (an ASUS motherboard with 64 bit AMD cpu) using Ubuntu 14.01 without problems. Regardless, the sample size of two computers is too small to draw any computer sensitivity conclusions.

---

### Post by mpr2 on 2016-02-07
Hello i have the same problems when i try to install GNURadio on a HDMI PC-Stick (Atom CPU). 
Now i am shocked to read it can depend on the computer hardware - so my question - is this really possible? 
Where can i find more information or somebody who can help me?

---

### Post by Bucky Ball on 2016-02-07
*Thread moved to **Multimedia Software**.*

What you need to do is uninstall the version you installed in the first place then install the version from the repos.

---

### Post by mpr2 on 2016-02-10
thank you. i did install the binary of Ubuntu 14.04. and i had GNURadio 3.7.1. But i need a version > 3.7.3 
So i deleted everything and installed Ubuntu 14.10 ( binary GNURadio 3.7.5) now i am running into other problems. Somehow the adresses of servers are wrong. i can't apt update nor i can install gnuradio binary. I am getting 404^^ anyway... 
couldn't i install the newer binary (3.7.5) on Ubuntu 14.04? how can i force a installation?

---

### Post by steeldriver on 2016-02-10
Ubuntu 14.10 has reached EOL and the repositories are no longer maintained - that's not going to be a viable route unfortunately

---

### Post by Bucky Ball on 2016-02-10
> **steeldriver said:**
> Ubuntu 14.10 has reached EOL and the repositories are no longer maintained - that's not going to be a viable route unfortunately

^^^
This. 

Forget 14.10. You want 14.04 LTS or 15.10. Or wait for 16.04 LTS in late April.

---

### Post by mpr2 on 2016-03-16
Thank you all for your help. After a longer break from this problem i am motivated to keep trying... 

I have to use a 14.04.03 version because that is the only Linux OS that is running on my Intel PC Stick (Intel Atom Z3735F Quad-Core, 32 GB HDD and 2GB RAM). And it is not the official Ubuntu - there are extra drivers for WIFI and Bluetooth. 
That makes it complicated but not impossible (i think) 
 
So I found another (newer) binary for Ubuntu 14.04.03 ([http://files.ettus.com/binaries/gnuradio/gnuradio_v3.7.3/](http://files.ettus.com/binaries/gnuradio/gnuradio_v3.7.3/)) 
I installed it and run into "cannot import gnuradio" when i open a .grc file. 
It asks "Is the python path environment variable set correctly? and 
"Is the library path env. set correctly" 

how can i check this? is there some kind of batch script that can fix this problem?
And.. how can that happen when it is a binary for exactly this Ubuntu?

---

