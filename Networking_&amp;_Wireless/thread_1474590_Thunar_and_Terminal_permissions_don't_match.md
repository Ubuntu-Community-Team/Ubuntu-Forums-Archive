---
title: "Thunar and Terminal permissions don't match"
date: 2010-05-06
forum: Networking &amp; Wireless
---

### Post by tootlet on 2010-05-06
Greetings,
I just upgraded my laptop to Xubuntu 10.4. I have a nfs server I connected to with my old Xubuntu 9.10 set up. I loaded portmap and nfs-common then made a mount point. I chowned and chmodded the mount point in the terminal to my user name. But Thunar (the file manager for Xubuntu) won't let me open subdirectories. So I went back to the terminal and chowned and chmodded again with a -R. In the terminal I can read and write as user. Thunar (as user) says I don't have permissions to see the subfolders. When I start Thunar as root it assigns the permissions to my user name but not when I start Thunar as user. When I start it as user and browse to the folder and select properties it says the owner is root. What the frak? How do I get Thunar to see the permissions I set in terminal as sudo? Or better yet, how can I set the permissions for my mount point so that I can access and write to directories and files on my nfs share. I have no problems with my other computers with this server's shares. Hints are very welcome. Thanks.

---

### Post by tootlet on 2010-05-08
Greetings,
Since I haven't gotten any replies to my first post I thought I would talk about what I've tried.

I had a desktop with Xubuntu 10.4 loaded on to it. I did the following commands:
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install portmap nfs-common

Made a mount point I named titania
sudo mkdir /titania
sudo chown -cR tootlet /titania
sudo chmod -cR 775 /titania
sudo mount -t nfs -o rw 192.168.1.6:/titania /titania
no error messages. In the terminal of the desktop I can change to subfolders in /titania and read, write and execute. 

When I go to Thunar I can open /titania and see the directories in it but can't open them or add a new file or directory. Same as my laptop. 

Ubuntu 9.04, Xubuntu 9.04, Kubuntu 9.04, openSUSE 11.2 and Mint 8 can all access these shares on the server. 

Is this a bug? Anyone getting Thunar to work on an nfs share? Most likely operator error. I hate that! I'll keep playing with it.

T

---

### Post by tootlet on 2010-05-09
Work around.

This problem only occurs in Thunar's detailed list view. In icon view or compact list it works fine. Now I'm really thinking bug. I prefer the detailed list view but can work around this. 

Hope this helps someone else.

T

---

