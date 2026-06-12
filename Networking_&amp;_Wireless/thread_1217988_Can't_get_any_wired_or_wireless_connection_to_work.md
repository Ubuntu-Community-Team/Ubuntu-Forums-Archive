---
title: "Can't get any wired or wireless connection to work"
date: 2009-07-20
forum: Networking &amp; Wireless
---

### Post by EntropicalVeda on 2009-07-20
Hi, I'm relatively new to trying out linux and computing. I installed Kubuntu on an old Dell Inspirion 5100 and am trying to figure out how to get ANY connection working. I tried troubleshooting with 
[https://help.ubuntu.com/9.04/internet/C/troubleshooting-wireless.html](https://help.ubuntu.com/9.04/internet/C/troubleshooting-wireless.html)
[https://help.ubuntu.com/9.04/internet/C/troubleshooting-lan.html](https://help.ubuntu.com/9.04/internet/C/troubleshooting-lan.html)
and by reading through the other Kubuntu no network connection but still have no success. 
when i try entering " sudo lshw -C network" in terminal. I see that both of my connections are disabled. 
I'm using another computer to access the forum so i can't paste easily...

---

### Post by Stormrider83 on 2009-07-20
Have you installed ndiswrapper?

---

### Post by EntropicalVeda on 2009-07-20
No i haven't. Is it somewhere on a CD or do i have to install it via a USB? What does it do?

---

### Post by komputes on 2009-07-20
Any better luck with a GNOME Ubuntu LiveCD?

---

### Post by Stormrider83 on 2009-07-20
It allows you to use the windows drivers for the wireless card you are using.
 
Go to the website of the maker of your laptop. Search for drivers. Download the windows driver for the wireless card.
 
Next go here:
 
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
 
and follow the instructions.
 
Any problems post back.

---

### Post by EntropicalVeda on 2009-07-21
I tried installing the files for ndiswrapper but i always seem to get an error that says sorry an error occurred. im not sure if this helps but it says that both network:0 and network:1 are disabled and when i tried lshw network i could see that there were no drivers installed so i'm at a loss... should i reinstall windows with the gnome desktop like what komputes says?

---

