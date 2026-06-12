---
title: "HOWTO: Install ATI Sapphire Radeon X1950"
date: 2008-09-23
forum: Multimedia Software
---

### Post by Nettoyer on 2008-09-23
I recently reformatted to test the authenticity to make sure I did this right:

These are the steps I took to get this installed "correctly" the first time.

Pre: Installed Ubuntu 8.04 Hardy, downloaded the 100+ updates, then rebooted.


1. install fglrx: ```
sudo apt-get install xorg-driver-fglrx
```
2. Went to ati site and downloaded the linux driver for my card
     ```
http://ati.amd.com/support/driver.html
```
3. Ran the install from the terminal instead of a gui: 
      ```
sudo sh ./ati-driver-installer-8-9-x86.x86_64.run
```
4. Followed the step-by-step directions in the terminal.  After it finished, it returned me to the terminal alerting me to reboot.
5. Reboot.
-
This allowed me to setup my card perfectly the first time! If I Right Click -> Properties -> Permissions -> "Allow executing file as a program"
then run the install via the gui, it messes up and **doesn't work correctly**!

I know next-to-nothing about linux (I've been using it less than a week) but I hope this can help you.
-Nett
:popcorn:

---

