---
title: "Trouble with WLAN PCI card"
date: 2010-03-17
forum: Networking &amp; Wireless
---

### Post by QuaGon on 2010-03-17
Hello,
In the last few days I decided to jump in and switched from Windows XP to kubuntu. Only problem is, my wireless just doesn't seem to work. When I click "Manage Connections" from the network manager, I can see a wires tab, a VPN tab and a DSL tab, but the wireless tab is greyed out. My wireless PCI card is, origo WLAN 22mbps PCI... model number WLL-2300. I cant find drivers for it, but to be honest I dont know whether im wasting my time with this card as it may not be compatable as its fairly old now! Do i have a chance making it work with kubuntu or not? thanks

---

### Post by QuaGon on 2010-03-17
i have found drivers for windows, but of course the CD doesn't auto run. will the windows drivers be compatable with kubuntu ( i doubt it somehow :))

---

### Post by chili555 on 2010-03-17
> will the windows drivers be compatable with kubuntu ( i doubt it somehow )Shockingly enough, they can be.

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

You will need the XP .inf file and possibly one or two .sys files. Can you unzip the files on the CD? Try right-clicking and select Extract Here.

---

### Post by QuaGon on 2010-03-18
i have the .inf and the .sys files in my documents. just reading up about ndiswrapper...

any advice before i blow up my pc :))))

thanks

---

### Post by chili555 on 2010-03-18
Follow instructions carefully and fully and post back if you get stuck.

---

### Post by QuaGon on 2010-03-18
I followed the instructions here([https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)) to set up my WLAN. it all works now :) 


thank you for your help

---

### Post by QuaGon on 2010-03-18
just rebooted and it didnt save my wireless settings. had to open the terminal and type a few commands to re establish a connection. it says at the end of that guide how to make the settings load at start up but when i type in the command, i get a message that the command is not found... 

kdesu kate /etc/ndiswrapper

surely kdesu is a spelling error... and what is kate lol... sorry for being a noob

---

### Post by cariboo on 2010-03-18
kdesu is the equivalant to gksu in gnome it a graphical sudo command. Kate is a text editor that is installed by default with KDE. to get the command to work press Alt-F2 and type it in the text box.

---

### Post by chili555 on 2010-03-18
> surely kdesu is a spelling error... and what is kate lol... sorry for being a noobUghh! Sometimes people who write these things get a bit difficult. Just use:```
sudo nano whatever_file
```Nano and kate are text editors. They allow you to write or edit files and save the changes. Kate is a bit harder than nano and not installed by default.

I think they meant kdesudo, which is also not installed by default as far as I know. Way to be user-friendly, tutorial writers!

Your changes will not be saved in nano until you WriteOut. Nano has its commands listed at the bottom. Post back if you get stuck.

---

### Post by QuaGon on 2010-03-18
i did alt f2

and typed

kdesu kate /etc/modules

and i got an error message... i tryed again and a small windows shows for about half a second saying error.... then nothing

---

### Post by chili555 on 2010-03-18
Open a terminal and do:```
sudo nano /etc/modules
```

---

### Post by QuaGon on 2010-03-19
ok all done :)

thanks for your help its much appreciated.

---

