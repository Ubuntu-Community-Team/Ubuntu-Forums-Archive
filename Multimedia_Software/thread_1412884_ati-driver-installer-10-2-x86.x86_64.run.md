---
title: "ati-driver-installer-10-2-x86.x86_64.run"
date: 2010-02-21
forum: Multimedia Software
---

### Post by aparolin on 2010-02-21
greetings,
i installed a new ati radeon 4350 driver in pcie slot.  (pulled old card out) adjusted bios to video pcie, then installed 9.04 on a clean hdd.  no probs.

fglrx driver is not activated 
now i thought to install video driver (catalyst)(ati-driver-installer-10-2-x86.x86_64.run)
downloaded and is showing on my desktop screen (81.7mb)

is this the terminal command???
aparolin@aparolin-desktop:~$ sh ./ati-driver-installer-10-2-x86.x86_64.run
sh: Can't open ./ati-driver-installer-10-2-x86.x86_64.run

am i mistaken??
or should i leave the system as is???

thanx for ur input
:)

---

### Post by me13221 on 2010-02-21
Do you need to run as root (i.e. sudo)?

---

### Post by aparolin on 2010-02-21
tried as sudo sh ./ati-driver-installer-10-2-x86.x86_64.run

command asked for password; entered; and i got same result...

---

### Post by karrank% on 2010-02-21
I had this prob, and markbuntu, bless his soul, helped solve:
[http://ubuntuforums.org/showthread.php?t=1405957](http://ubuntuforums.org/showthread.php?t=1405957)

---

### Post by Yellow Pasque on 2010-02-22
You're in your home (~/) dir, not your /home/Desktop (~/Desktop)....

---

### Post by aparolin on 2010-02-22
1)
i thought this was my desktop.  (aparolin@aparolin-desktop)

(ati-driver-installer-10-2-x86.x86_64.run) is on my 'brown colored ubuntu' desktop screen.

i am confused.  then how do i switch???

2)
also tried to remove fglrx as suggested before installing proprietary ati driver:

aparolin@aparolin-desktop:~$ sudo sh /usr/share/ati/fglrx-uninstall.sh
[sudo] password for aparolin: 
sh: Can't open /usr/share/ati/fglrx-uninstall.sh

as u can see im still pretty green.  srry

---

### Post by Yellow Pasque on 2010-02-22
cd Desktop
sudo sh ...

---

### Post by aparolin on 2010-02-22
ok figured out to do 
1)
change directory to desktop:
cd Desktop

now about question 2)
???

---

### Post by aparolin on 2010-02-22
just a note:

my system, admin, hardware driver notes that the ati/fglrx driver is not activated...

should i still remove it before installing the  proprietary ati driver???

and how???

---

### Post by Yellow Pasque on 2010-02-22
What?

---

### Post by aparolin on 2010-02-22
thanx for info tem:

karrank% noted in a reply that i should goto this website.  it has some hints for installing 
ati drivers.  it notes to remove the ati/fglrx driver that comes with ubuntu9.04, before installing  a proprietary ati driver
[http://ubuntuforums.org/showthread.php?t=1405957](http://ubuntuforums.org/showthread.php?t=1405957)


i downloaded the ati/catalyst/10.2 driver for linux and hoping i would get the max out of my new ati radian 4350 card.

---

### Post by Yellow Pasque on 2010-02-22
If you haven't installed a driver previously, then skip that step...

---

### Post by karrank% on 2010-02-23
> **aparolin said:**
> thanx for info tem:

karrank% noted in a reply that i should goto this website.  it has some hints for installing 
ati drivers.  it notes to remove the ati/fglrx driver that comes with ubuntu9.04, before installing  a proprietary ati driver
[http://ubuntuforums.org/showthread.php?t=1405957](http://ubuntuforums.org/showthread.php?t=1405957)


i downloaded the ati/catalyst/10.2 driver for linux and hoping i would get the max out of my new ati radian 4350 card.

I'm happy with my 4350 EXCEPT for no sound over HDMI port which has yet to be solved. Let me know how your experience plays out. 

thanks.

---

### Post by vinan on 2010-03-09
Krank

just installed my 4350 with proprietary ati drive, sound worked perfectly.



the issue i have is no matter how i tries to set my VGA screen as prim. and HDMI as secound it fails. 

any body have a clue:KS

---

### Post by ls420 on 2010-03-11
Help I have tried everything posted in every thread. Catalyst tells me no driver installed after I installed 10-2-x86 and ran aticonfig. tried removing all previous drivers and reinstalling also. Please help.

---

### Post by Yellow Pasque on 2010-03-11
> **ls420 said:**
> Help I have tried everything posted in every thread. Catalyst tells me no driver installed after I installed 10-2-x86 and ran aticonfig. tried removing all previous drivers and reinstalling also. Please help.
[http://ubuntuforums.org/showpost.php?p=8821885&postcount=2](http://ubuntuforums.org/showpost.php?p=8821885&postcount=2)
What video card do you have? If it's Radeon X1k or older, then Catalyst 10-2 isn't going to work..

---

### Post by doas777 on 2010-03-11
> **karrank% said:**
> I'm happy with my 4350 EXCEPT for no sound over HDMI port which has yet to be solved. Let me know how your experience plays out. 

thanks.

i had to do some monkying with alsa and pulse to get it going on my 4200, but should work. toward teh end I had it working but didn't realize it since I had to change my stereo head to PCM surround.

---

