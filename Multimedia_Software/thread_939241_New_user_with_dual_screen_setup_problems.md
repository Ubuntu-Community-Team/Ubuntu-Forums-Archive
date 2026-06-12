---
title: "New user with dual screen setup problems"
date: 2008-10-05
forum: Multimedia Software
---

### Post by john_mc on 2008-10-05
Hi all,

i wonder if anyone could could offer me some help getting dual screen to work as I ahve spent sometimes looking for ansers on the net but hit a brick wall.

i have ubuntu server 8.04 installed with the x desktop (can't remember the exact name, Gnome I think). I am using a Nvidia 6800GT for which I got the drivers using the command line

sudo apt-get install nvidia-settings

This now allowed me to enable the setting for screen resolution with extra effects etc so I think i have the driver isntall ok for the Nvidia card.

The problem is now i want to connect my panasonic TV to the S-vidwo output of my graphics card. I go to system > administration > nvidia x server settings. I select my TV dispaly and enable but the system would save the x config file. I got around this by reading other psots and found i should be using

gksudo nvidia-setting

I am now able tosave the nvida X server settings but they don't appy. I restart X server and still no display on my TV. In the Nvidia settings i only ever see screen 0. no matter what i do I can get the system to save the changes or get hem to take effect.

Anyone help as i am now banging my head of a wall.

John

---

