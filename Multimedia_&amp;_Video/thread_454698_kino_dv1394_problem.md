---
title: "kino dv1394 problem"
date: 2007-05-25
forum: Multimedia &amp; Video
---

### Post by sirab on 2007-05-25
WARNING:dv1394 kernel module not loaded or failure to read/write /dev/dv1394/0

What am I supposed to do.

Pleeease help.

---

### Post by Matt Yun on 2007-05-25
References:  [HOWTO: DVCamcorder and /dev/raw1394]("http://ubuntuforums.org/showthread.php?t=2792"), [Video Camera and Firewire (IEEE1394)]("http://www.bxlug.be/en/articles/220"), [Ubuntu & Sony Handycam]("http://ubuntuforums.org/showthread.php?t=56468"), [Bug #6290 in kino (Ubuntu)]("https://launchpad.net/ubuntu/+source/kino/+bug/6290")

You need the raw1394 and video1394 modules; dv1394 is apparently deprecated.  To load these manually, do (as root or sudo):

**modprobe raw1394 video1394**

To automatically load these, add **raw1394** and **video1394** to your */etc/modules* file.

Note:  raw1394 will create the /dev/raw1394 device node, that belongs to the 'root' user and 'disk' group.  You need to add your own user account to this group:  as root or sudo, do:

**adduser sirab disk**

---

### Post by sirab on 2007-05-25
i cant save it because it says its a read only file only...

sorry im real new at this

---

### Post by sirab on 2007-05-26
alright so i did what you told me, changed the module file so now it says:

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
sbp2
raw1394
video1394

added the other thing you told me to, but i still get the same error when i open kino

so i thouhgt maybe it didnt get the raw and the video so i went to terminal and tried to get it manually

sirab@sirab-laptop:~$ sudo modprobe raw1394 video1394
sirab@sirab-laptop:~$ sudo modprobe raw1394
sirab@sirab-laptop:~$
sirab@sirab-laptop:~$

yeah so im confused.

---

### Post by sirab on 2007-05-26
come on someone?

anyone?

---

### Post by sirab on 2007-05-26
So I just checked my dev folder. It looks like i only have the video1394 dev if that helps at all.

---

### Post by fenian on 2007-05-26
Try running these commands....

first this
> 
sudo apt-get install  libraw1394-8 libiec61883-0

then run this 

> 
sudo modprobe dv1394
sudo modprobe video1394
sudo modprobe raw1394
sudo modprobe ohci1394

---

### Post by sirab on 2007-05-26
when i run sudo apt-get install.... i get 

sirab@sirab-laptop:~$  sudo apt-get install libraw1394-8 libiec61883-0
Password:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
sirab@sirab-laptop:~$ 

so i run dpkg and  i get 

sirab@sirab-laptop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
sirab@sirab-laptop:~$

---

### Post by sirab on 2007-05-26
wow sorry for being such a noob dont worry about it

---

### Post by sirab on 2007-05-26
alright now that i did something right.

ran the codes you told me to and this is what happened.

> sirab@sirab-laptop:~$ sudo apt-get install libraw1394-8 libiec61883-0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libraw1394-8 is already the newest version.
libiec61883-0 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
sirab@sirab-laptop:~$ sudo modprobe dv1394
sirab@sirab-laptop:~$ sudo modprobe video1394
sirab@sirab-laptop:~$ sudo modprobe raw1394
sirab@sirab-laptop:~$ sudo modprobe ohci1394
sirab@sirab-laptop:~$

---

### Post by sirab on 2007-05-26
I tried to get the raw and dv using terminal but this is what happened
> 
sirab@sirab-laptop:~$ sudo apt-get install raw1394
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package raw1394
sirab@sirab-laptop:~$ sudo apt-get install dv1394
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package dv1394
sirab@sirab-laptop:~$ 
sirab@sirab-laptop:~$ 

---

### Post by eggdeng on 2007-05-26
Some of us have been able to solve similar problems in a fairly simple way. It seems to be that the video capture device is listed as one thing in /dev whereas Kino expects something else.

With the camera connected and turned on, type
```
ls /dev
``` in a console

You should see ```
dv1394-0
``` on the list. 

Go to Kino, Edit->Preferences and on the ieee1394 tab, change dv1394 device to /dev/dv1394-0. This fix is from a post by Mileeta in [http://ubuntuforums.org/showthread.php?t=352441](http://ubuntuforums.org/showthread.php?t=352441).

Post back if the ls command gives you a different output.

---

### Post by sirab on 2007-05-26
i got this output

> dsp        ptyd2  ptyrf  ptywc  sequencer2  ttya1  ttyee  ttyt7  ttyy4
dv1394     ptyd3  ptys0  ptywd  sg0         ttya2  ttyef  ttyt8  ttyy5


---

### Post by sirab on 2007-05-26
When l go in my dev folder there are folder for dv1394 and video1394 and a device-char for raw1394.

If i click on any of the device-chars I get this error message

> Cannot open /dev/raw1394: No application is known for this kind of file.

I don't  know if it is anything significant or not. I wanted to post it just in case.

---

### Post by sirab on 2007-05-26
I really need an answer for this.

In other words "Bump".

---

### Post by meng on 2007-05-26
Try this:
Kino > Preferences > IEEE1394
make sure dv1394 location is:
/dev/raw1394
and then make sure you have access to the device
(in terminal:
sudo chmod 777 /dev/raw1394

alternatively, run kino with superuser privileges
gksu kino
(you still have to have the correct device location though)

---

### Post by sirab on 2007-05-26
I only have two options on my preferences av/c device and dv1394 device.

I changed dv1394 to raw1394 anyway and got the same error message only ending in raw1394.

when l write in the command in terminal i get.

> sirab@sirab-laptop:~$ sudo chmod 777 /dev/raw1394
Password:
sirab@sirab-laptop:~$ 


so nothing happens after i put in my password.

Also I get no notification that I even plug in a ieee card to my laptop when I plug it in and when I remove it and plug it back in my caps button starts blinking and I have to restart my laptop.

Although I see some things come up in terminal when I plug in or take out the card.

---

### Post by meng on 2007-05-26
Nothing else is MEANT to happen after you complete the sudo chown command.
The sequence should be as follows:

put the card in (AND plug in the video capture device!)

sudo modprobe (blah, blah, blah)

sudo chmod 777 /dev/<whatever - could be dv1394 or raw1394>

then run kino
if no joy, run "gksu kino"

Make sure you get the sequence right.

---

### Post by sirab on 2007-05-26
Oh ahaha I'm sorry. I'm not trying to fristrate anyone. I'm just really new at this. I got ubuntu just 3 days ago.

Anyway.... I got kino working without the error showing up now. But it still wont capture. When I click capture it says waiting for dv and has a little countdown and then quits trying.

I have my ieee card in and my camera was on in vcr mode so it should work.

And I might be doing my n00b thing again. But I looked in my root folder and there are no folders in it.

---

### Post by sirab on 2007-05-26
I can control the camera by pressing the control buttons and when i press capture it starts playing the tape in my camera but it does that count down thing and i cant see whats on my camera's lcd on the screen above the controls in kino.

---

### Post by sirab on 2007-05-27
bump

---

### Post by fenian on 2007-05-27
If your controlling the camera through kino you should be able to capture.Follow the instructions [in this tutorial]("http://www.robfisher.net/video/kino.html").

---

### Post by sirab on 2007-05-27
I don't know. I'm gonna start a new thread and see if anyone can help me with this new issue and if I can't fix it im gonna try adn find an alternative.

---

### Post by Selcal on 2007-09-30
> **fenian said:**
> Try running these commands....

first this


then run this


well that did it.  I am not too sure what i did. but it did fix my problem.  Mucho Thankso Van duder.

---

### Post by SammyBoy247 on 2007-10-28
I found this thread really usefull

Someone (smarter than me) should convert this and some other posts in to a definative guide.

---

