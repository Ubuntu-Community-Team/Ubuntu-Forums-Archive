---
title: "Install VLC (offline) in Ubuntu 12.04"
date: 2013-03-09
forum: Multimedia Software
---

### Post by ranjanpurbey on 2013-03-09
[SIZE=4]*Note: This guide is only for **Ubuntu 12.04** . But you can try it on other machines. But don't blame me...
VLC is one of the best media players out there - both as a client and as  a streaming server. But due to its long list of dependencies, it's  difficult to install it manuallly . Worse is the case when you have to  install it on a machine without internet. Hope the VideoLan team will  prepare a single VLC package which can be installed directly without  bothering for dependencies. But as of now, it's only a hope...
In the following guide, I will show you how to make this possible.  However you will need one computer connected to internet on which you  will download the files and then transfer them to your offline computer. Follow  these steps:
[/SIZE]
[LIST]
[*][SIZE=4]Download [this script]("https://www.box.com/s/kui4f69p7js922qnoybz") on Internet-connected system .[/SIZE] 
[*][SIZE=4]Save it in a new folder (say VLC).[/SIZE] 
[*][SIZE=4]Make the script executable.[/SIZE] 
[*][SIZE=4]Run it from terminal. (this will download vlc deb package andall other dependency packages. ~26.5 mb).[/SIZE] 
[*][SIZE=4]Now copy this (VLC) folder to home directory of your offline Ubuntu 12.04 system.[/SIZE] 
[*][SIZE=4]Start a terminal and type following : [/SIZE] 
[/LIST]
[INDENT=2][SIZE=4]```
sudo dpkg -iR VLC 
```[/SIZE][/INDENT]
[INDENT][SIZE=4]   Provide the password if prompted.
[/SIZE][/INDENT]
[INDENT][SIZE=4]  ... And you're done. Hope this helps.
[/SIZE][/INDENT]

---

### Post by sershiya on 2013-04-27
Thankyou for the post...!! ):P

---

