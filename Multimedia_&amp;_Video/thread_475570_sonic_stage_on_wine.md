---
title: "sonic stage on wine"
date: 2007-06-16
forum: Multimedia &amp; Video
---

### Post by dcalvani on 2007-06-16
After downloading Wine I tried to install SonicStage 3.4 (on Ubuntu) in an attempt to have my Sony minidisc player MZ-RH1 "communicate" with my computer. 

The installation seemed to be ok. Two icons (Sonicstage and MDburner) appeared on the desktop. When I clicked on them, though, I got the following message:

"Before you can use the program, you must restart your computer. After start the computer, please log on as an Administrator". 

This is my computer, and I'm the only user. Am I the Administrator? I thought so. Anyway, rebooting my machine didn't help. When I try to start Sonicstage (or MDburner) I keep getting the above message. 

I tried to start it through Terminal by typing 

sudo env WINEPREFIX="/home/daniele/.wine" wine "C:\Program
Files\Sony\SonicStage\Omgjbox.exe"

and I got exactly the same message. 

Can you please help? If it's not going to work anyway (and I won't be able to use my MD player anyway) can you tell me how to uninstall Sonicstage and MDburner?

Thank you!

---

### Post by 9170 on 2007-07-08
Hello dcalvani

Try this side! 

[http://frankscorner.org/index.php?p=qa](http://frankscorner.org/index.php?p=qa)


christian

---

### Post by Chronos6 on 2007-09-11
Hy!
I want to handle my NetMD player, but i cant connect it to VirtualBox XP. I got the following mesaage:
[ 7368.694719] usb 2-3: new full speed USB device using ohci_hcd and address 2
[ 7368.886600] usb 2-3: device descriptor read/64, error -62
[ 7369.174234] usb 2-3: device descriptor read/64, error -62
[ 7369.457969] usb 2-3: new full speed USB device using ohci_hcd and address 3
[ 7369.641771] usb 2-3: device descriptor read/64, error -62
[ 7369.930554] usb 2-3: device descriptor read/64, error -62
[ 7370.213201] usb 2-3: new full speed USB device using ohci_hcd and address 4
[ 7370.628773] usb 2-3: device not accepting address 4, error -62
[ 7370.804671] usb 2-3: new full speed USB device using ohci_hcd and address 5
[ 7371.220182] usb 2-3: device not accepting address 5, error -62

Can anybody help me? I just need Linux kernel to handle the usb part. Thanx

---

