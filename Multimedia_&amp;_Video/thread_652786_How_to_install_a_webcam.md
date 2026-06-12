---
title: "How to install a webcam"
date: 2007-12-29
forum: Multimedia &amp; Video
---

### Post by Bruce2 on 2007-12-29
I know you put your webcam into the USB port.... but how do i install the disk that came with it?

It says in the instructions to click the my computer prompt which i dont have. It says to find "setup.exe" which i did. I double clicked on it and its said:

"Cannot open /media/Star-eye PWC-130/Setup.exe: No application suitable for automatic installation is available for handling this kind of file."

Can anybody help me with this please?

Apparently ive already got camorama installed.

---

### Post by forcehack on 2007-12-29
This is a windows file extention and likely a program for windows....do you have wine installed?

if so try opening this file with wine from a terminal
wine ~/Desktop/steam/steam.exe

if not install wine and give it a try...from a terminal
sudo apt-get install wine

Then try step one again.
 
sometimes you would be ask for root password (root privilages) which is your root password (admin password) this only this you can do is to  type "sudo apt-get install wine", it will ask you for YOUR password, type the password you use to login in to your linux machine so you can run the command as root.
When you installed wine, you can either double-click on the .exe file you want to run, or type in a terminal "wine /home/martin/desktop/steam/steam.exe".

Full wine instructions available at : [https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)
Instructions how to use sudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

:)
Regards,
Philip Sega Otoo

---

### Post by Bruce2 on 2007-12-29
OK, I did all of that and its still coming up with this:

Cannot open /home/bruce1/Desktop/Setup.exe: No application suitable for automatic installation is available for handling this kind of file.

---

