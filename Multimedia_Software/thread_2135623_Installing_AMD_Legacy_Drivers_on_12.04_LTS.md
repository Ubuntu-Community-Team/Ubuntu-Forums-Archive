---
title: "Installing AMD Legacy Drivers on 12.04 LTS"
date: 2013-04-14
forum: Multimedia Software
---

### Post by mclark87 on 2013-04-14
I've tried doing this repeatedly, and I give up doing it through my own research. Every other page shows a different process and the one's I've tried haven't worked out. Don't know what I'm doing wrong. I reformatted my drive, had 12.1 installed, and installed 12.04 so I could use this driver, or so I thought. My Gateway nv52 uses the Radeon 3200 card so I need the legacy driver. I've been trying to use the newer 13.1 version. So far I've broke something a handful of times and just reinstalled ubuntu to start fresh. Main reason I want to get away from the open source driver is the boot/sleep problem and the only game I play one my computer, World of Tanks, runs at single digit frames per second with the open source card even with a low res pack installed. So, is there a definitive guide somewhere or where may I be screwing up? Thanks in advance.

---

### Post by mclark87 on 2013-04-15
Bump...

I googled how to find out my xserver version and my kernel version. I am running 1.13 which I know is a problem. I thought 12.04 came with 1.12? Is it safe to downgrade to 1.12 and not cause problems later on? I had read that hacking ubuntu 12.10 into using xserver 1.12 may cause issues down the line which is why I uninstalled 12.10 and installed 12.04 instead. My kernel is 3.5.0. I haven't found out if that is compatible or not. Still working finding an answer for xserver.

---

### Post by Mark Phelps on 2013-04-15
I believe 12.04.02 comes with X-server 1.13, as does 12.10. 

It's not simple to downgrade to X-server 1.12 and will carry lots of problems with it even if you do that.

---

### Post by mclark87 on 2013-04-16
So I found out how to find out for sure what I got. The system screen says 12.04 LTS so I thought that's what it was, not 12.04.02. Did the 'lsb_release -a' command and it says 12.04.02. Damn, guess I gotta figure out how to get regular 12.04. I knew 12.1 and 12.04.02 came with xserver 1.13, just thought I had 12.04

---

### Post by Cheesemill on 2013-04-16
You can download 12.04.1 which still uses X server 1.12 from here...

[http://old-releases.ubuntu.com/releases/12.04.1/](http://old-releases.ubuntu.com/releases/12.04.1/)

---

### Post by mclark87 on 2013-04-16
Thanks, downloading it now. Is there anything I need to watch for with updates? Like is the system going to try to update itself to the next version with x-server 1.13 at any time? And what is the definite guide for installing the legacy driver? I had tried a couple different ones that used different commands, of course now I know why they didn't work. Just want to get this driver installed and working so I can get my other programs installed. Not going to mess with putting them on again until after I know this works incase I need to reinstall ubuntu again and start over.

---

### Post by mclark87 on 2013-04-21
Finally got around to getting 12.04.01 installed and now that is done. Before I try to install the 13.1 Legacy driver again I want to be sure I get the right commands. There is sooo many different sets of commands you should enter floating around online. Most of the one's I've been finding now involve downgrading x-server. Whole reason I installed 12.04.01 is so that I won't have to do that. There is a fglrx driver under Additional Drivers but it doesn't say which version it is or if it is a legacy type driver. Help?

---

### Post by Mark Phelps on 2013-04-21
> **mclark87 said:**
> Finally got around to getting 12.04.01 installed and now that is done. Before I try to install the 13.1 Legacy driver again  want to be sure I get the right commands. There is sooo many different sets of commands you should enter floating around online. Most of the one's I've been finding now involve downgrading x-server. Whole reason I installed 12.04.01 is so that I won't have to do that. There is a fglrx driver under Additional Drivers but it doesn't say which version it is or if it is a legacy type driver. Help?

The one under additional drivers would be the version that was distributed with 12.4 -- probably a Catalys 10.x or 12.x version.

The 13.1 Linux legacy driver will work with your card and Ubuntu 12.04 -- but make sure it says Legacy Driver in the web page -- as the standard 13.1 driver will not work with your card.

---

### Post by mclark87 on 2013-04-21
Yeah, I downloaded the 13.1 legacy driver from their site. Do I just extract the .zip file and click the .run file inside to run it like that? Just want to make sure it works this time, thanks. I figured I was looking for some commands to enter into the terminal.

---

### Post by Yellow Pasque on 2013-04-22
You should build .deb packages. If you need to remove the driver for some reason, that will make it a lot easier.

```
sudo apt-get install build-essential cdbs dh-make dkms execstack dh-modaliases fakeroot libqtgui4 linux-headers-generic
cd ~/
wget http://www2.ati.com/drivers/legacy/amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.zip
unzip amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.zip
chmod +x amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.zip
sh ./amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.zip --buildpkg Ubuntu/precise
sudo dpkg -i fglrx*.deb
sudo amdconfig --initial -f
```

---

### Post by Yellow Pasque on 2013-04-22
> **Mark Phelps said:**
> I believe 12.04.02 comes with X-server 1.13, as does 12.10. 
It's not simple to downgrade to X-server 1.12 and will carry lots of problems with it even if you do that.

In 12.04.2, it is fairly easy to go back to the original 1.11.4 Xserver that 12.04 originally came with:
```
sudo apt-get install xserver-xorg-lts-precise
```

---

### Post by mclark87 on 2013-04-27
> **Temüjin said:**
> You should build .deb packages. If you need to remove the driver for some reason, that will make it a lot easier.

```
sudo apt-get install build-essential cdbs dh-make dkms execstack dh-modaliases fakeroot libqtgui4 linux-headers-generic
cd ~/
wget http://www2.ati.com/drivers/legacy/amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.zip
unzip amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.zip
chmod +x amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.zip
sh ./amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.zip --buildpkg Ubuntu/precise
sudo dpkg -i fglrx*.deb
sudo amdconfig --initial -f
```

I am unable to get this coding to work. After the first line "sudo........cd ~/" is entered I get

Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
E: Unable to locate package cd
E: Unable to locate package /home/matt

Why is it so hard to find something that works for something that should be common to do?

---

### Post by Yellow Pasque on 2013-04-27
cd ~/ is its own command. If it was part of the first command, it wouldn't be on the second line.
> Why is it so hard to find something that works for something that should be common to do?
Copying/pasting should not be difficult..

---

### Post by mclark87 on 2013-04-27
OK, it didn't do anything when I tried them separate so I tried the two lines as one and got that.

Now, this is what I am getting...

matt@matt-NV52-Series:~$ sudo apt-get install build-essential cdbs dh-make dkms execstack dh-modaliases fakeroot libqtgui4 linux-headers-generic
[sudo] password for matt: 
Sorry, try again.
[sudo] password for matt: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
cdbs is already the newest version.
dh-make is already the newest version.
execstack is already the newest version.
fakeroot is already the newest version.
build-essential is already the newest version.
dh-modaliases is already the newest version.
dkms is already the newest version.
libqtgui4 is already the newest version.
linux-headers-generic is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-29 linux-headers-3.2.0-29-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 360 not upgraded.
matt@matt-NV52-Series:~$ cd ~/
matt@matt-NV52-Series:~$ wget [http://www2.ati.com/drivers/legacy/amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.zip](http://www2.ati.com/drivers/legacy/amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.zip)
--2013-04-27 11:55:34--  [http://www2.ati.com/drivers/legacy/amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.zip](http://www2.ati.com/drivers/legacy/amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.zip)
Resolving www2.ati.com (www2.ati.com)... 12.120.114.146
Connecting to www2.ati.com (www2.ati.com)|12.120.114.146|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 106908508 (102M) [application/zip]
Saving to: `amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.zip'


100%[======================================>] 106,908,508 1.71M/s   in 71s     


2013-04-27 11:56:50 (1.43 MB/s) - `amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.zip' saved [106908508/106908508]


matt@matt-NV52-Series:~$ unzip amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.zip
Archive:  amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.zip
  inflating: amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.run 
matt@matt-NV52-Series:~$ chmod +x amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.zip
matt@matt-NV52-Series:~$ sh ./amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.zip --buildpkg Ubuntu/precise
./amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.zip: 1: ./amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.zip: Syntax error: ";;" unexpected
matt@matt-NV52-Series:~$ sudo dpkg -i fglrx*.deb
dpkg: error processing fglrx*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 fglrx*.deb
matt@matt-NV52-Series:~$ sudo amdconfig --initial -f

I do appreciate the help. Just after trying multiple things and it seems it's fighting me the whole it's getting frustrating. And, I'm getting tired of having to hard reset my laptop every time I go to use it because of the boot/sleep issue with the open source driver.

---

### Post by mclark87 on 2013-04-29
bump

---

### Post by Arpage on 2013-12-18
> **Temüjin said:**
> You should build .deb packages. If you need to remove the driver for some reason, that will make it a lot easier.

```
sudo apt-get install build-essential cdbs dh-make dkms execstack dh-modaliases fakeroot libqtgui4 linux-headers-generic
cd ~/
wget http://www2.ati.com/drivers/legacy/amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.zip
unzip amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.zip
chmod +x amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.zip
sh ./amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.zip --buildpkg Ubuntu/precise
sudo dpkg -i fglrx*.deb
sudo amdconfig --initial -f
```

Sorry for opening an old thread but I was bumping my head against the wall with my HD3470 and Ubuntu 12.10, 13.04 and 13.10 the past MONTH or so. Finally, today I came across this post!! Thank you for this!!

OP: I hope you got it sorted in the meantime and shame noone came back to the thread to help you. Temujin's code here is correct except for ONE line, which gave you the syntax error.

So for anyone else that may come across this post in the future, the correct steps are:

> -Fresh install of Ubuntu 12.04.1 downloaded from [http://old-releases.ubuntu.com/releases/12.04.1/](http://old-releases.ubuntu.com/releases/12.04.1/)
-```
X -version
``` which should show you're on X.Org X Server 1.11.3, Build Operating System: Linux 2.6.42-26-generic i686 Ubuntu, Current Operating System: Linux [your machine name here] 3.2.0-29-generic-pae #46-Ubuntu
-manually download the AMD 13,1 legacy driver from [http://www2.ati.com/drivers/legacy/a...x86.x86_64.zip]("http://www2.ati.com/drivers/legacy/amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.zip") (it should save to your home/[your username]/Downloads directory) I advise this step so you can always find the original .zip and .deb file for just incase.

Now it's time to build the .deb package as Temujin suggested...
```
sudo apt-get install build-essential cdbs dh-make dkms execstack dh-modaliases fakeroot libqtgui4 linux-headers-generic
cd /home/[your username here]/Downloads
unzip amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.zip
chmod +x amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.run
```

**THIS IS THE LINE OF CODE THAT IS WRONG SO DO NOT USE THIS:**
```
sh ./amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.zip --buildpkg Ubuntu/precise
```

[B]REPLACE ABOVE CODE WITH:
[/B]```
sh ./amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.run --buildpkg Ubuntu/precise
```

Because the wrong line of code is commanding an execute of the .zip file and not the .run file. You want to execute the .run file.
After that, the rest of the codes are correct:
```
sudo dpkg -i fglrx*.deb
sudo amdconfig --initial -f
```

And now, reboot your pc.

Yes, you will have to be VERY carefull which updates you install after installing the Legacy driver as any X-server version above 1.12 and any kernel version above 3.4 are not supported. Perhaps there is a way to upgrade X-server to 1.12 and the kernel version to 3.4 and then HOLD both of them so they don't get updated anymore?

Anyhow, hope anyone else in need of these instructions finds them in time :)

---

### Post by Yellow Pasque on 2013-12-18
Yeah, copy/paste error. Good catch.

---

