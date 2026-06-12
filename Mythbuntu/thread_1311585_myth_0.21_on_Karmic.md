---
title: "myth 0.21 on Karmic"
date: 2009-11-02
forum: Mythbuntu
---

### Post by jensk on 2009-11-02
I have tried Karmic on my backend. It has distorted video on my HVR-4000 card - pictures overlaying of not showing at all. I tried with firmware 1.20.xx.x, 1.22.xx and 1.23.xx. Apparently this is a known problem and being worked upon. 

So backend restored back to jaunty and mythtv 0.21 where everything worked with a little help from patches (h.264, he-aac...) the right firmware etc.

My problem is that I would like to run the new intel video drivers for my frontend (a Shuttle x27D )and theese comes with Karmic. With the drivers that comes with Jaunty HDTV stutters and processor utilization by mythfront.real goes above 100% - however that can happen.

So to get HDTV (h.264 he-aac) to work I would try to install Karmic with the good Intel drivers on my frontend and on top of that install mythtv 0.21

If i grab the Jaunty mythtv packages from packages.ubuntu.com/jaunty/graphics and .../libraries and install theese with dpkg could that work or would that break something else?

Any advice would be helpfull
/jk

---

### Post by sk8er3810 on 2009-11-02
I don't see why not.  I was able to install jaunty Boxee on Karmic and it's jaunty dependencies.  You might get lucky.  Its worth a shot though.

---

### Post by technoboi on 2009-11-03
My experience may be of some use to you.
I installed Karmic and MythTV 0.22 as a new install on my Media Centre PC
This was a BIG mistake. 0.22 is so broken it is ridiculous. I spent 2 days trying to fix it. Then I thought, in desperation, missing my MythTV, I would try the latest Mythbuntu. Well, apart from the fact that it didn't work either I couldn't put up with the stripped down desktop - I want to view pix and listen to audio too!
So, I decided to revert to Jaunty, with a difference. I installed Jaunty again but then installed the latest kernel. I then installed MythTV 0.21 via the 'Add/remove programs as well as Mythbuntu control centre. I keep a record of all that I do so I was able to refer to my last install on what i had to do to get it all working.
I have pasted my install log below as you might find it useful. One disadvantage is that I can't use the 0.22 install on my Karmic desktop PC to view my media Centre using 0.21 as the database is incompatible. So now I have to find a way of installing 0.21 on my Karmic desktop. The only problem I am getting now is that when I do a reboot I have to keep reselecting the desktop to Gnome - mythbuntu has taken over!
b.t.w I have Intel 945 CPU.
So here is the log I made of my latest install which was based on previous experience:-
......................................................
Need to do updates to cope with jerky video
[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=7104256](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=7104256)
Found a later version of the Kernel that I can use instead of one in guide
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31.5/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31.5/)

I modified commands to do the latest stable kernel(this is all in one line):-
sudo wget -c [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31.5/linux-headers-2.6.31-02063105-generic_2.6.31-02063105_i386.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31.5/linux-headers-2.6.31-02063105-generic_2.6.31-02063105_i386.deb) [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31.5/linux-headers-2.6.31-02063105_2.6.31-02063105_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31.5/linux-headers-2.6.31-02063105_2.6.31-02063105_all.deb) [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31.5/linux-image-2.6.31-02063105-generic_2.6.31-02063105_i386.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31.5/linux-image-2.6.31-02063105-generic_2.6.31-02063105_i386.deb)

Followed by this (all one line):-
sudo dpkg -i linux-headers-2.6.31-02063105-generic_2.6.31-02063105_i386.deb linux-headers-2.6.31-02063105_2.6.31-02063105_all.deb linux-image-2.6.31-02063105-generic_2.6.31-02063105_i386.deb
.....................................
Problem with missing mythconverg database.
Solved:-
sudo apt-get purge  mythtv-database
sudo apt-get install mythtv-database
......................................
MythTV frontend General (not TV General) settings:-
Sound: Set 'mixer device' and 'audio output' to 'Alsa default' and set 'mixer controls' to 'Master'
Also in Alsa mixer set PCM volume to full. The Frontend settings seem to be influenced by this setting.
................................
Set video tweaks etc. in MythBuntu control and that seemed to improve HD TV. At this point it is watchable but still jerks at regular intervals.
Set Jaunty appearance 'Visual Effects' to none and this got rid of windowing and seemed to improve the video.
..........................

In summary:- There is a bit to go on the HD but the rest is working fine. I will look at other Intel drivers if available. Don't know atm how I'm going to install 0.21 on my Karmic desktop.

---

