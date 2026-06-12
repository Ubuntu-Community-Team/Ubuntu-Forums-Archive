---
title: "[SOLVED] Kworld ASTC 115 setup"
date: 2008-07-04
forum: Multimedia Software
---

### Post by jiggygent on 2008-07-04
Hello all,

I am new to Linux, but very excited about learning more. Currently, I am trying to setup my Kworld ATSC TV Tuner to use with MythTV.  I've searched the forums, and reviewed the howto wiki for setting up the card, but I can't even get past the first command..

According to the wiki, to download the firmware, you must first type:

sudo apt-get install linux-doc-[kernel version]

My kernel version is 2.6.24-19-generic

When I type, sudo apt-get install linux-doc-2.6.24-19-generic or just sudo apt-get install linux-doc-2.6.24-19, I get the following response:

E: Couldn't find package linux-doc-2.6.24-19-generic or E: Couldn't find package linux-doc-2.6.24-19

I must be doing something wrong.. please help! :confused:

---

### Post by xc3RnbFO8P on 2008-07-04
It should be:
> sudo apt-get install linux-doc
or
> sudo apt-get install linux-doc-2.6.24
or install it from Synaptic Package Manager.

---

### Post by jiggygent on 2008-07-04
Thank you so much.  That worked.. Now since my source is 2.6.24.19-generic, during the next command it says to use your kernel source directory, so does that mean 2.6.24.19-generic, or just 2.6.24.19 considering that is what I used to get the linux-doc... and regardless of either one, I checked my /usr/src/all kernel folders  and I do not have a /dvb directory.. Is there any easier way to download and install the nxt2004 firmware??

---

### Post by jiggygent on 2008-07-04
OK, I ran a search for DVB and found the directory. It was actually located in: /usr/src/linux-headers-2.6.24-19-generic/drivers/media/dvb

But when I type the next command: sudo gzip -d get_dvb_firmware.gz , I get gzip: get_dvb_firmware.gz: No such file or directory

It is frustrating when the commands on the howto's do not work.. but I know it's just going to take some getting use to. I'm determined to learn about this stuff and become a regular linux user..  Is there an alternative command that I can type go get dvd_firmware.gz?

---

### Post by xc3RnbFO8P on 2008-07-04
You should do this:
> cd /usr/scr/linux-headers-2.6.24-19-generic/Documentation/dvb/
> sudo perl get_dvb_firmware nxt2004

---

### Post by jiggygent on 2008-07-05
Thats the thing, I do not have a /dvb in that directory.. all I have is:

aoe  cdrom  DocBook  lguest  s390

---

### Post by jiggygent on 2008-07-05
I just ran locate get_dvb_firmware.gz and I found it here:

/usr/share/doc/linux-doc-2.6.24/Documentation/dvb/get_dvb_firmware.gz


Is it ok to run the command in this directory?

---

### Post by xc3RnbFO8P on 2008-07-05
yes use **sudo gzip -d get_dvb_firmware.gz**

---

### Post by jiggygent on 2008-07-05
OK! That worked.. now I want to edit my /etc/modules, the wiki says that saa1734 should already exist and to put saa7134-dvb under it.. I do not have saa7134 in my modules.. should I add that as well? or can I just put saa7134-dvb and save?  

p.s. I tried searching the forums for saa1734 and I googled it as well.. but could not find anything about if I should add it etc.. I feel like a child with this stuff.. lol.  Once I get this successfully installed, I plan on posting the instructions that worked for me just in case others might have similar problems.

---

### Post by xc3RnbFO8P on 2008-07-05
When you do **dmesg**
do you see these lines:
> nxt200x: NXT2004 Detected
DVB: registering new adapter (saa7133[0]).
DVB: registering frontend 0 (Nextwave NXT200X VSB/QAM frontend)..
no need to post it here.

---

### Post by Cresho on 2008-07-05
You should of done a search before posting.  It is solved and there is no problems.

[http://ubuntuforums.org/showthread.php?t=734867&highlight=kworld](http://ubuntuforums.org/showthread.php?t=734867&highlight=kworld)

this is my tutorial and it works fine.

---

### Post by jiggygent on 2008-07-05
As I stated in my previous post, I did search the forums, as well as Google.  I was searching specifically for saa1734 since what I was trying to figure out why saa1734 is not listed under /etc/modules and according to the ATSC 115 wiki, it should be. After reviewing your tutorial, does it apply if I am trying to setup MythTV?? That is why I am following the ATSC Wiki, because it is specifically for MythTV which is what I would like to install.. I did add the dependencies listed in your tutorial, and rebooted, ran dmesg and do see the correct response, but when I type ls -1 /dev/dvb/adapter0 , I only see:

demux0
dvr0
frontend0
net0

I'm not sure if that is correct, considering it is not identical to what you say it should be.. but secondly, even still.. I do not see saa1734 in my /etc/modules.. so back to my original question, am I suppose to add it? or can I continue forward in adding saa7134-dvb?

---

### Post by Cresho on 2008-07-05
Your card is working and in perfect order.  NOW!  you need to get myth tv to work with it.  are you going to be using your system as a dedicated multimedia system?  make a new post about getting the kworld 115 with mythtv  working since you already completed the kworld astc 115 setup.

This thread should be labeled as solved. :popcorn:

or if you want to see how me tv works? you can view the third pic and that is how me-tv looks on a regular desktop. [http://www.gnome-look.org/content/show.php/E17+Liquid+Mythril?content=82939](http://www.gnome-look.org/content/show.php/E17+Liquid+Mythril?content=82939)  ohh and incase you think your card is not running, just run that same line "ls -1 /dev/dvb/adapter0" and should say that. my setup says the exact same thing.  I don't understand why you would want to run mythtv unless it is a dedicated box on a hdtv.  If you run a desktop, I'd recommend you try using me-tv first for a desktop.  I have 2-4 television tuners on my desktop running either one at a time or 2 at the same time depending on what my liking is.  mythtv is a fullscreen application from what I gather and you cannot do other things while myth is running am I wrong?

---

### Post by jiggygent on 2008-07-06
OK, I've never heard of me-tv.. I do plan on using it just for my desktop.. I'm going to have to try me-tv first I suppose. :) Thank you guys so much for the help setting this up!

---

### Post by Cresho on 2008-07-06
my tutorial shows you how to install.  please read it

---

