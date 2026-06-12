---
title: "Stuck at Preparing to install Ubuntu"
date: 2011-03-06
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by herdwick on 2011-03-06
I can't get any further trying to install from a USB stick to an Acer Aspire One netbook than the "Preparing to install Ubuntu" screen. This is the same if I try to install from the live edition or if I select install on boot.

Ctrl+Alt+F1 gets me to a working shell prompt, but installation has been sat for an hour.

Natty Alpha 3

Help !

---

### Post by marijus on 2011-03-06
i had the same problem until i found out that one of my partitions (swap) was not "clean".

Probably the partitioning program gives up on the install without any error if any partition it finds is not good...

---

### Post by herdwick on 2011-03-06
> **marijus said:**
> i had the same problem until i found out that one of my partitions (swap) was not "clean".

you may have hit the problem there, I remade the swap partition and it has at least gone into the installer further - thanks !

---

### Post by jerrylamos on 2011-03-06
This is from Aspire one netbook running Natty Alpha 3.  Now I cheated, I installed Natty on a USB hard drive on a desktop and brought the installed Natty over to the Aspire.

I think a netbook Natty install will get stopped at assigning the partitions and setting where grub is to be installed.  There's a big fat wide useless top banner which shoves the grub choices off the bottom of the screen.  The window will not scroll or page up so the button at the bottom of the screen cannot can be selected.

I intend to try plugging an external monitor with a larger screen and trying to do an install that way.

Do note Maverick installed fine as is on the Aspire one netbook since it does not have that same very long partition install window.

Good luck, Jerry

---

### Post by Truin on 2011-03-13
Apparently my swap partition was also unclean.
Ctrl-Alt-F1, ran parted from shell and deleted swap partition (You should try to fix swap 1st, I didn't bother because I was going to do a fresh install anyway)

After that install worked as intended

---

### Post by TunaCanTommy on 2011-03-13
I had this problem installing Natty on my Asus EeePC (701).
I started by choosing to "Run Ubuntu" from a USB built on my Maverick desktop. Then, with Natty running, I opened Gparted and formatted the 4.0 GiB SSD (Ext4) into two partitions - /boot (120MiB) and the rest (3.61GiB) as / (root). Then I formatted a SDHC card (8.0 GiB) in the card reader as /home. I decided to _not_ use a SWAP drive . . . I can add one later if I want.

I shut down and created a new USB with the current Natty "Alternate" version.  I booted using that and the installation went OK - no hangs.

During the installation you have to chose to use the partitions you made - takes a few minutes to input the parameters, but it all went pretty well.

I'm currently up to date and have 87 MiB left on /boot and 1.3 GiB left on / (root). My home directory formatted a 8 GiB SDHC to 7.41 GiB and there is about 7.0 GiB remaining on it after installing Thunderbird and Ubuntu-Tweak.  No data stored on it yet.

---

### Post by sgage on 2011-03-13
This is the third thread on this issue. I started the original one. The fixes and workarounds are being repeated over and over. Don't know if the moderators can consolidate or make a sticky or what, but the "can't get beyond preparing to install" thing is spawning multiple threads.

And people, before you post your problem, do a search!

---

### Post by joshuajon on 2011-03-16
I'm attempting to install alpha 3 in VirtualBox OSE under #! host and I'm stuck at this same spot.  I know that my swap partition is clean because it's virtual... and fresh...

---

### Post by bejayel on 2011-03-24
I am stuck here as well:

3 wd caviar black in raid (windows 7, where grub will go)
1 wd caviar green (where ubuntu will go, fresh)
gigabyte 890fxa-ud5
AMD phenom 2 x6
8 gig g-skill ddr3
11.04 AMD64 daily build for March 23

The installer freezes at "Preparing to install" indefinitely.

This is my first trek back to ubuntu in a LONG time and I haven't been in linux for a good 2 years.

I cannot use 9.x or 10.x as 9.x wont install and 10.x has crazybad problems (crashing my network card till I hard reboot, cant actually click anything as the video seems to just freeze in place for seconds at a time for no reason)

11.04 is my only option at this point as earlier than 9 also wont work for me.

---

### Post by encefalocardia on 2011-03-24
For some reason partition manager does not like partition tables created by other apps or systems. You'll have to erase your entire HD. I learnt that the hard way.

---

### Post by sgage on 2011-03-24
> **encefalocardia said:**
> For some reason partition manager does not like partition tables created by other apps or systems. You'll have to erase your entire HD. I learnt that the hard way.

No, you don't have to erase the entire HD. I dual-boot with Windows. Just delete the non-Windows partitions and create new ones with gparted and you'll be good to go.

---

### Post by bejayel on 2011-03-24
> **sgage said:**
> No, you don't have to erase the entire HD. I dual-boot with Windows. Just delete the non-Windows partitions and create new ones with gparted and you'll be good to go.

It's a fresh hard drive. I can't simply disconnect my others either as windows freaks out. I will fool around in gparted though and see if it helps.

---

### Post by anotherunixguy on 2011-03-28
> **sgage said:**
> This is the third thread on this issue. I started the original one. The fixes and workarounds are being repeated over and over. Don't know if the moderators can consolidate or make a sticky or what, but the "can't get beyond preparing to install" thing is spawning multiple threads.
 
And people, before you post your problem, do a search!
 
Then why not post a link to the relevant posts?
 
I *HAVE* searched, have YOU?  Are people supposed to read hundreds of posts because "The fixes and workarounds are being repeated over and over"?
 
Here's a thought....post a link to post(s) that give some answers!
 
You want ubuntu users, yet when installing, some peoples' machines just hang at "Preparing to install Ubuntu".
 
The recourse you suggest is to "DO A SEARCH".  Well thank you for your helpful response.
 
...and you wonder why linux isn't getting traction....go figure....
 
Thanks for your helpful post.

---

### Post by jerrylamos on 2011-03-28
28 March Natty Daily Build sticks at "Preparing to install Ubuntu" on netbook Acer Aspire one.  Maverick has no such trouble.  I created launchpad bug #744438 because I don't know if the myriad of installations having this same indications are all the same bug or not.  Maybe the additional ubuntu-bug info will be of help maybe not.

The Aspire one has a native 250 GB hard drive split between Maverick and Windoze 7 starter and also a 100 GB sata USB hard drive with Maverick and Natty and a new partition created in hopes of installing today's .iso.  No such luck.

Do note Beta is due 31 March and the image still doesn't fit on a 700 MB CD.  It will fit on a USB stick but I have two test pc's that won't boot from USB.  

Jerry

---

