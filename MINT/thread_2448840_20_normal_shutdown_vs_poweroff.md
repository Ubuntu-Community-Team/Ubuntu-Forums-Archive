---
title: "20 normal shutdown vs poweroff"
date: 2020-08-14
forum: MINT
---

### Post by Kris_M on 2020-08-14
EDIT - see last post - artifact of "suspend".
-



I am plagued with frequent spontaneous restarts after I choose menu/shutdown.

I have played with some settings but can find no relief.

I started using sudo poweroff instead and so far get no restarts.

Is this safe? It seems a bit more abrupt, but so far linux hasn't complained. Why isn't it always used?

EDIT: this did not work - it's a suspend artifact.

---

### Post by kurt18947 on 2020-08-14
I saw that problem, in my case it was running 18.04 on a newly built Ryzen 2200G based desktop using the integrated video. I tried various fixes but was never able to solve the problem reliably. I kept tinkering until I broke the install. Installing 20.04 fixed the problems; newer kernel, newer ACPI and video firmware. I don't know that your problem has the same basis.

---

### Post by crip720 on 2020-08-14
Some googling seems to be problem for a few people, some have suggested wifi being on is one cause.  Think I had similar problem years ago and had to blacklist a driver.

---

### Post by Kris_M on 2020-08-14
This is actually a brand new build as I gparted wiped my SSD, rebuilt GPT,  and redid win8, win10, and mint 20 to get good efi, mbr and system partitions. I have tried many things.

uplug rj45 before shutdown.

[FONT=Liberation Serif][SIZE=3]sudo ethtool -s enp0s25 wol d - but it just turns it back on.[/SIZE][/FONT]

[FONT=Liberation Serif][SIZE=3]nmcli c modify "Wired connection 1" 802-3-ethernet.wake-on-lan ignore - but makes no difference.

turn off all USB. 

share a fix so I can try it!!!

It still does it 70% of the time. 
EXCEPT when I do sudo poweroff.
[/SIZE][/FONT]

---

### Post by Kris_M on 2020-08-16
EDIT
this is an artifact of "suspend" in Ubuntu base.

go to power mgt and change suspend to something else.

---

