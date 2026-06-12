---
title: "Dell Latitude D600"
date: 2008-12-31
forum: Networking &amp; Wireless
---

### Post by nickabocker on 2008-12-31
Hi,
So i'm alittle new to linux, I got Ubuntu installed after a friend refered me to it. It installed great except on part, NO WIRELESS Internet. I read online that switching from the gnome network manager to WICD it would work tried it, NOTHING. So i started digging alittle deeper and found that my computer says DISABLED after running the command sudo lshw -C network in the terminal. Now it says the same thing with my ethernet port but if i plug my dsl box right into my computer i cna get internet with no problem. Also i checked my bios on my computer for my wireless status and it says it is on. can anyone help?

---

### Post by pytheas22 on 2008-12-31
You may just need to install some extra drivers.  If you could please post the output of the following commands, I'll try to point you in the right direction:
```

lshw -C Network
uname -rm
dmesg | tail -50
sudo iwlist scan
```

Also, while you're plugged into the Internet via your DSL cable, try going to System>Administration>Hardware Drivers and see if there's any option to enable wireless.  If you have a card that requires proprietary firmware (Broadcom cards do, and these tend to be in Dells), this should take care of it.

---

### Post by nickabocker on 2009-01-01
ok first i did the hardware drivers like you suggest first and i was able to enable a driver for my wireless card but i still have an issue it won't connect

posted below are two photos of the terminal and what the output was of the commands you asked me to look into.

[IMG]http://i4.photobucket.com/albums/y139/nickabocker/screenshot1.png[/IMG]
[IMG]http://i4.photobucket.com/albums/y139/nickabocker/Screenshot2.png[/IMG]

thank you again.

nick

---

### Post by pytheas22 on 2009-01-01
hmmm, it looks like your card should work now, but it's not seeing your router for some reason.  Is your router operating in 11g mode or a different mode?  Do you know which channel it's on?

If you open a web browser from a computer that is connected to the router and put 192.168.1.1 in the address bar (if that fails, try 192.168.0.1 or 10.0.0.1) you should be able to configure your router.  Does anything change if you switch it to a different channel (6 is the most reliable) and make sure it's in 11g mode?

I have the exact same wireless card as you in a laptop--Broadcom 4306--and it definitely works with this driver in Ubuntu 8.10.

Also, try running these commands to make sure the firmware is installed:
```

sudo apt-get update
sudo apt-get install b43-fwcutter
```

---

