---
title: "Ubuntu and Windows Networking"
date: 2011-09-13
forum: Networking &amp; Wireless
---

### Post by adam.gla on 2011-09-13
I have ubuntu 11.04 and i have a windows 7 touchsmart computer that I want to put ubuntu on.  I also have a laptop that belongs to my sister that has ubuntu 11.04 and windows 7 and another desktop that has windows xp on it.  Is there any possible way I can network these computers together? When I am on the windows side, all these computers can see each other fine and can access files on each other, when im on ubuntu i can't see the other computers or the files, I would like to see them both, and access the printer that is connected via usb to the hp touchsmart computer thanks!

---

### Post by garvinrick4 on 2011-09-13
It is all part of the "windows workgroup" as long as you have all your window shares
set up will work in Ubuntu out of box.
If you want to see Ubuntu just need to set up "samba shares". You can install "system-config-samba" I believe it is, look in your Ubuntu software center. 
Is a GUI package to set up what you want to share.
Have to use your path to set up share, such as /home/rick will set up all in /home/rick
or you can set up /home/rick/Public as a share. What ever you want to share, can make your
own directory to share sudo mkdir /home/rick/Shared and then set that up as a Samba share. 
#The printer will work when you set up printer look under printer to network printer to samba using workgroup I believe, you will see it. Make sure you share printer in Windows.
#Nothing will work while is in sleep mode and Windows machine will not sleep if you share media I do believe it overrides the sleep setting.
It will all show up in the bottom of samba config file.
```
gedit /etc/samba/smb.conf
```You will then see what your samba shares look like.
Below is how I change my directory to my name as permissions that I have made.
Just wanted to give you this incase you come across a directory you need permissions, rick is username of course use your own.
```
sudo chown -R rick:rick /home/rick/Shared
```
## Windows folder=Linux directory
Enjoy your Ubuntu, ask all the questions you want lots of users here to help.

---

