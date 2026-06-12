---
title: "Force a screen res'"
date: 2010-03-22
forum: Multimedia Software
---

### Post by BigSteve_G on 2010-03-22
I've just dumped Windows completely in favour of Linux Mint (based on Ubuntu) & have got it running very nicely indeed - however - while I was testing it on a dual boot setup I had a few display problems (firefox images colors all wrong & screen gets garbled & crashes the system) so when I installed this time I used 'Compatibility' mode to start the live CD & install Linux Mint a trick that worked on my Laptop with a radion mobile.

The system is now sorted (no crashes, images all present & correct) but when the login screen pops up its the 1024x768 I want - login & it sticks, but when I then logout (about 98% of the time) it changes to 800x640 & when I login it sticks at that & cant be changed. 

I've tried changing a line in grub.cfg to try & force it but that only changes the grub splash images. All & any help you be appreciated. - please help! (my eyes cant take it :-)

---

### Post by gordintoronto on 2010-03-22
What is your video controller?  Do you have proprietary hardware drivers installed? Was the grub change "nomodeset"? Is it Mint 8? (i.e. grub 2?) If it's grub 2, did you remember to run:
sudo update-grub

---

