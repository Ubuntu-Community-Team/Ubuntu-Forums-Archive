---
title: "nVidia Driver Problems"
date: 2007-09-30
forum: Multimedia &amp; Video
---

### Post by maplestar on 2007-09-30
I've just recently got ubuntu for my computer.  I finally solved my internet problem and can connect wirelessly.  I want to continue to compiz-fusion, but I need to connect my nVidia card to ubuntu.

I have a Geforce 8600 GTS nVidia card.  When I find new drivers, i find a new driver for Linux.

I download the file, and it's NVIDIA-Linux-x86-100.14.19-pkg1.run.

I'm stuck on how to download it.  I open terminal and type "sh NVIDIA-Linux-x86-100.14.19-pkg1.run"

I get an error that ubuntu can't open the file.  Double clicking the file on the desktop tells me that ubuntu can't detect what character code to use to open it. 

What am I doing wrong and how do I download this driver?

---

### Post by Waappu on 2007-09-30
Hi

Try Envy. It will install lates driver for you
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by maplestar on 2007-09-30
Ok, I installed the Envy package, but when downloading I'm told that Dependancy is not satisfiable: build-essential.  So I can't install it...help?

---

### Post by Waappu on 2007-09-30
Hi

Type in terminal
```
sudo aptitude install build-essential
```
and try again

---

### Post by blackfire on 2007-09-30
Go for a 
```
sudo apt-get install -f 
```

it should do the trick.
Anyway, about your original problem: try with a chmod +x NVIDIA-Linux-x86-100.14.19-pkg1.run
then ./NVIDIA-Linux-x86-100.14.19-pkg1.run

---

### Post by maplestar on 2007-09-30
ok, it seems to work, i downloaded something when i typed:

supo aptitude install build-essential in terminal with my cd inside.

Now I get a different error:

Dependency is not satisfiable: xserver-xorg-dev.

I'm a noob at this so sorry for my complaints.

EDIT:  I tried the chmod +x thing, but I get an error saying that my NVIDIA package cannot be found and that there is no such directory...  Am i supposed to place my programs in a certain folder because they're all on the desktop right now.

Btw, how do I sign in as ROOT?  I'm reading through a couple of guides and this part stumped me.

---

### Post by maplestar on 2007-09-30
bump

someone please help.

---

### Post by nick_h on 2007-10-01
Don't login as root use sudo instead.

Resolve the new dependency as you did with the last one:
```
sudo aptitude install xserver-xorg-dev
```
(or use apt-get)

If using the nvidia script rather than Envy - change to the directory where you have downloaded the script and then type:
```
sudo chmod a+x NVIDIA-Linux-x86-100.14.19-pkg1.run
```
(use TAB completion to get the filename right - e.g. just type NVIDIA and then tab and the filename should complete for you.)

Log out of the GUI then CTL-ALT-F1 to get to a terminal and login. Then stop the GUI by typing:
```
sudo /etc/init.d/gdm stop
```
Then run the script by typing:
```
sudo sh NVIDIA-Linux-x86-100.14.19-pkg1.run
```
Then start the GUI again by typing:
```
sudo /etc/init.d/gdm start
```

---

### Post by Miru on 2007-11-21
I had the same problem, only when I checked the box then it did the (first) error. But when I type in "sudo aptitude install build-essential" It says "Media Change: Please insert the disc labeled 'Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)' in the drive '/cdrom/' and press [Enter].". I dont have the disc I used to install Ubuntu any more,


Also I have a 64 bit comp, but I hear 32 bit is much easier and only slightly slower to use. My motherboard is the P5N32E-SLI Plus and it comes with a whole bunch of features on a disc I want to install. The disc has a Linux folder on it. I also have the disc that came with my graphics card, but it doesn't have a Linux drivers folder. What can I do?

If it would help I'm switching from windows and I know only a little of command prompt. My computer is:
P5N32E-SLI Plus
GeForce 8600 GT
2 GB of PC6400
Intel Core 2 Duo E6850 (3Ghz, 64 bit)
A Sata hard drive and a sound car that came with my mobo (but not onboard).

---

### Post by chaquira on 2007-11-22
check this..
[http://ubuntuforums.org/showthread.php?t=57368&highlight=latest+nvidia+drives](http://ubuntuforums.org/showthread.php?t=57368&highlight=latest+nvidia+drives)

---

