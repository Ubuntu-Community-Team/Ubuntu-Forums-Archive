---
title: "Accessing NAS drive"
date: 2011-01-18
forum: Networking &amp; Wireless
---

### Post by teamdebo on 2011-01-18
Hello, 
I'm kind of new to Linux. I have done some work with Fedora, some shell scripting some perl scripting and some C development but I still consider myself new to Linux since there is so much to learn.

Anyways my question is:

I have a NAS drive attached to my network. I can access it by mounting the drive with the gui interface. I enter the ip address, select Windows Share (since it's shared among windows, Mac and linux pc's ) and it connects using samba.

Now I have a question how do I access the files on this drive from the terminal? I can see and open the files and save files from the NAS drive using the GUI but when it comes to terminal I am lost.

I need to write a script which backs up some files onto the NAS and I can't seem to figure out how to access the drive from the shell or from perl.

I understand it's probably a very simple solution except I tried googling it and I cant seem to find the answer.

thanks.

---

### Post by thinkinhurtz on 2011-01-18
Try this I hope it helps:
First create the directory that you want to mount the files from the NAS drive into. Then bust this command into your terminal.
sudo mount -t cifs //192.168.1.100/NASdrive /media/NASdrive

Use your IP address and change the directories to reflect your system. Then navigate to the new folder from the command line.
Good luck.

---

### Post by kaiseris on 2011-03-18
I have a different problem with my Buffalo NAS on my home network. I can access the NAS through file manager. I browse through home network, find windows workgroup ant find my NAS there, then it mounts as Samba share. I can then copy, delete files etc. through file manager. But for example if I want download some files through Jdownloader and save them straight to my NAS I can't see it in the dialog window. Other example: I want to put some new music to my iPod with help of special software. I can upload music from internal drive, but again NAS won't show up in dialog window when choosing folder to upload music from. In other words I can access NAS through file manager but most of other apps won't see it.
How can I change that?
Thanks in advance.

---

