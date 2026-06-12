---
title: "Reconnecting to a disconnected network share"
date: 2009-11-25
forum: Networking &amp; Wireless
---

### Post by the4thamigo_uk on 2009-11-25
Ive setup a mount point for a share on a NAS drive. However if I restart the NAS while logged into ubuntu, I cannot then reconnect to the share. Is there an easy way to get ubuntu to rediscover the share?

---

### Post by chaanakya_chiraag on 2009-11-25
Do you know the IP address of the share?  An IP address looks like 4 numbers separated by periods, each number consisting of 1-3 numbers.

---

### Post by the4thamigo_uk on 2009-11-25
Yes I know the IP address, and I also have a machine name that resolves via DNS. So I can successfully 'ping MachineName'.

I guess what Im really trying to find out is whether the 'mount' command will automatically reestablish in the situation when the the connection is temporarily lost.

(Thanks for the speedy response by the way!)

---

### Post by chaanakya_chiraag on 2009-11-25
First, click on Places->Home, click on the location button, and type smb://IP address and see if it connects.  No problem!!!

---

### Post by the4thamigo_uk on 2009-11-25
I can reconnect via the GUI menus successfully yes but it does not force a reconnection of my boot time mount point (defined in fstab). In fstab I have a mapping setup to connect /mnt/MachineShareName with //MachineName/Share via CIFS.

Interestingly, when I click on /mnt/MachineShareName in Nautilus it displays no files but when I do 'ls /mnt/MachineShareName' via the command line the files show up...?

Is this a bug in Nautilus I wonder?

---

### Post by chaanakya_chiraag on 2009-11-25
After doing ls in the terminal, try doing ```
sudo nautilus . 
``` and see if the files show up.

---

### Post by the4thamigo_uk on 2009-11-25
No joy. Can you reproduce this? Im on Karmic.

---

### Post by chaanakya_chiraag on 2009-11-25
The thing is, I'm also on Karmic, but I just do ad-hoc connecting, mounting before backing up and unmounting after backing up.  The only thing the drive is used for is to back up stuff.  The question is, do you really NEED to mount it on boot.  Otherwise, I can give you two lines of code that will mount and unmount a NAS.

---

### Post by the4thamigo_uk on 2009-11-25
Well it looks like it is re-mounting when I check via the command line. But Nautilus isnt being refreshed for some reason. Do I NEED it? No I guess, but its very handy to have the NAS share already mounted and authenticated when I boot. I pick media files off it using Rhythmbox and often used to forget to do a manual connection. Its no massive problem but it looks like something is fishy with Nautilus... (excuse the pun)

---

### Post by doas777 on 2009-11-25
I have a simmilar issue. if I reboot the server while a client is connected, I have to reboot the client before it will reconnect. it cannot unmount the original share, and won't create a new mount until the old one is gone. it's really bad if I was watching video in totem during the outtage, as totem often hard locks.

---

### Post by chaanakya_chiraag on 2009-11-25
haha pun excused.  I mean, you COULD mount it in a script that runs when you log in.  If you want, I can tell you how to do that until I figure out what is going on with Nautilus.

1) Open Text Editor (Applications->Accessories->Text Editor) and set the type of the document to .sh (look in the lower right for Plain Text).

2) Copy the following line into the Text Editor: ```
yes "**your password**" | sudo -S smbmount //**IP Address**/**Share location** **mount location** -o username=**user name to access the share**,password=**password to access share**,uid=1000,mask=000;
```

3) Save this as whatever you want.

4) Add this script to your startup applications (System->Preferences->Startup Applications)

Again, I am not sure what is going on and I will look into it and get back to you.  In actuality, I am not sure if the above script will fix your problem :D  It's worth a shot though

---

### Post by chaanakya_chiraag on 2009-11-25
To unmount the share, repeat steps 1-3, but copy this instead:
[CODE]yes "**your password" | sudo -S smbumount [B]mount location**;

This should work!

---

