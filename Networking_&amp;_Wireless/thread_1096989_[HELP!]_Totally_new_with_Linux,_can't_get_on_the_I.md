---
title: "[HELP!] Totally new with Linux, can't get on the Internet with it"
date: 2009-03-15
forum: Networking &amp; Wireless
---

### Post by SNTC on 2009-03-15
Hi, I am TOTALLY new with Ubuntu, or any other Linux stuff.
I was tired of my Windows XP keep crashing, so i decided to
try this. Alright, so i downloaded Ubuntu 8.10, Image burned
it on CD, installed, etc. Now, my 1st step is getting internet
on my pc. I use this Sitecom USB Wireless stick 54g WL-169 to
connect to my router. Since I haven't found ANY drivers for
Linux, I've done some research & found that this "ndiswrapper"
can help me out, as soon as i started to follow the tutorial on how to run it, I got stuck. There was this /etc/modprobe.d/blacklist thing, where i have to blacklist b43, ssd, etc.
when I try to save it, it says that i don't have the permisson
for it. I rlly don't get the tutorial made by the site ppl.
Could anyone help me, to find what i'm looking for? What to do?
Or anything else?

thank you

the ubuntu noob

---

### Post by inobe on 2009-03-15
welcome to the forums

the very first thing you should do is connect wired to get all your updates !

if you get the card working prior to the updates' the card configuration may get borked .......

so plug into the router and run all updates first if you haven't done so already :)

---

### Post by Kevbert on 2009-03-15
Easiest way is to make sure ndiswrapper is installed first and the Wifi adapter plugged in. Then with the install disk browse to /pool/main/n/ndisgtk folder using nautilus filemanager (which will open when you insert the CD, just press cancel at the prompt). In the folder you will find one file called ndisgtk...deb. Just double click on the file to install it.
Copy the Windows **XP** .sys and .inf driver files to your desktop.
Now go to System-Administration-Windows Wireless Drivers (this is what you've just installed) and click on Install New Driver and point it to the .inf file on your Desktop by clicking on the folder icon and selecting the Desktop Folder. The driver should then install and you'll be able to set up a wireless connection.

---

