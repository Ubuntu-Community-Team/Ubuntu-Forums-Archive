---
title: "MP3 player doesn't mount"
date: 2007-07-21
forum: Multimedia &amp; Video
---

### Post by claus on 2007-07-21
Hi,

after purchasing a new MP3 player, Ubuntu "Breezy" doesn't mount the new player (Maxfield Blackline, 512 MB), whereas the old one (no-name from Hongkong) was mounted automatically. What do I have to do to get the new player mounted as well? I checked all of the options in 'Preferences > Removable drives and media', but to no avail. Do I have to edit '/etc/fstab'?

Thanks,

claus

---

### Post by Martje_001 on 2007-07-21
Can you mount it via Computer --> Audioplayer?

---

### Post by zero244 on 2007-10-19
Try this...........open a terminal window and copy and paste this.

sudo rmmod ehci_hcd

It will then ask you for your passwork.
Password:

Then try and mount your player. This goes away on reboot. I made a launcher on my desktop, so I just double click it when I want to mount my mp3 players.
This works with Edgy and Feisty.......I havent tried it with Gutsy yet.
It seems some mp3 players are seen as scusi drives instead of plain ole flash drives.
This command has worked on all my mp3 players that wouldn't mount before.
Good Luck.

---

### Post by mrClean on 2007-10-20
I was having trouble with mounting my iaudio x5 under gutsy... it worked fine with fiesty. Anyways tried your command: 

sudo rmmod ehci_hcd

and it worked perfectly. Thanks

---

### Post by insane_v on 2008-02-26
Hi everybody ! 
I'm sorry for the stupid questions (maybe), but what is "terminal window" and how to open one ?

I also have similar problems with my MP3 player (Canyon &#1057;N-MP3SOF 1GB). Everything seems fine with the player and "Ready" is written at the display, but the computer do not recognize it. It is written that there are no drivers for this device. Earlier it used to work without any drivers as it was detected as a "Mass storage device".

---

