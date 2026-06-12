---
title: "Noob installing ndiswrapper with no connection"
date: 2006-06-01
forum: Networking &amp; Wireless
---

### Post by mulder416 on 2006-06-01
I have installed breezy badger on my dell laptop, and have a usb drive with the ndiswrapper deb package, my card's drivers. Nothing else, no other internet connection. I can't even install ndis because there is no option in the package manager to just open the package, it insists on having to download it. I've looked at several help pages, forums, etc, and I haven't seen any that go any more in depth than "Step 2: Install ndiswrapper.", or are way too in depth to be of any use to me. What do I need to do to get this package installed? I can still dual boot to windows and download additional packages if needed, but can't compile anything from source because I can't do it with the default settings, unless there is an easy way that I totally missed.

---

### Post by pelle.k on 2006-06-01
First of all, i take it you can't see this network device at all?
Second, Dapper drake is the current version released today. This is the dapper support forums, but anyway - can you right click your usb device and NOTE which device it mouted as (sda1, hda1, hdb, or whatever). When it's mounted, run this command in a 
terminal;
cd /media/<whatere device it is mouted under>/<whatever catalog the .deb is in>/
sudo dpkg -i <whatever it's name is>

if there are no error reports, then you have successfully installed that .deb

then;
cd /media/<whatere device it is mouted under>/<whatever catalog the driver .inf is in>/
sudo ndiswrapper -i <driver .inf name>
sudo ndiswrapper -m

restart your computer and see if your card is detected...

if not;
sudo ifconfig wlan0 up

now it should be visible.

---

### Post by Titus A Duxass on 2006-06-01
why don't you use the ndiswrapper that's on the CD?

---

### Post by mulder416 on 2006-06-01
Awesome, that's all I needed. I can figure out the drivers bit on my own, thanks!

---

