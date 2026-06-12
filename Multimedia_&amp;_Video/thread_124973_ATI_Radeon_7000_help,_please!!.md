---
title: "ATI Radeon 7000 help, please!!"
date: 2006-02-02
forum: Multimedia &amp; Video
---

### Post by muckluck on 2006-02-02
Hi, I've installed ubuntu about a week ago, and I know enough to get around in linux. My computer has a intergraded video card (some intel chipset thing) and an Ati Radeon 7000. The problem is, during setup, the xorg.conf is set to use the Intel card, and i want it to use the Radeon, but i simply can't find out how to switch the cards. Please tell me how to switch them!!! Thank you for you time.

---

### Post by DoorGunner on 2006-02-02
[http://ubuntuforums.org/showpost.php?p=423584](http://ubuntuforums.org/showpost.php?p=423584)

These are possibley the best set of instructions for ati drivers....have a try with these and it should get you going. :)

---

### Post by janitor_jones on 2006-02-02
these are the instructions for removing the fglrx driver

sudo apt-get remove xorg-driver-fglrx
sudo apt-get remove fglrx-control
sudo apt-get remove linux-restricted-modules-$(uname -r)
sudo dpkg-reconfigure xserver-xorg #Select the ATI driver

in regards to the line:
sudo apt-get remove linux-restricted-modules-$(uname -r)

i type in 
sude apt-get remove linux-restricted-modules-$USER

but it tells me it can't find the files
am i using the right syntax?
what should I put in place of -$(uname -r)
i assume i have to be root

also if I just installed a new copy of ubuntu do i have to remove the fglrx driver or can simply download the new ATI driver and install it

my card is a ATI 9250 HCI PCI 128MB

Thanks

---

### Post by tripleee on 2006-02-20
No, type what it says. The uname command returns the version of the kernel you are running; the name of the package to remove depends on which kernel you have.

In response to DoorGunner's suggestion, I don't think those instructions will work for an ATI 7000 which is what the original poster has.

---

### Post by tripleee on 2006-02-20
See if you can get it to work simply by running dpkg-reconfigure xserver-xorg and selecting the ati driver instead of the intel one. With lspci, you should be able to figure out which PCI card is which, and fill it in when dpkg-reconcigure asks you. In principle, I believe you can even have both cards active at the same time, but that's an advanced topic.

Good luck with getting the 7000 configured for a reasonable resolution, though. I'm just about to give up and run it with the good ole retro vesa driver.

---

### Post by secular on 2006-02-24
Thanks, tripleee. I did a news install with an ATI 7000 AGP card, and it defaulted to 640x480. And I couldn't fit it until I followed your suggestion to use the dpkg-reconfigure xserver-xorg command.

I read all the prompts, and all of the choices I would make were already pre-selected. So, this would probably work well for noobs newer than I am.

Thanks again.

---

