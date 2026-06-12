---
title: "My 9600GT and low graphics mode"
date: 2008-05-24
forum: Multimedia Software
---

### Post by Mortosa on 2008-05-24
Let me start by saying I just recently switched from Kubuntu to Ubuntu and I couldnt be happier. Gnome has gotten a lot nicer since I used it last 2 or 3 years ago.

My machine has a 9600GT in it. I love it when I game, its a great card. But when I wanted to get drivers installed in Nix I had issues. I got the 173.08 beta drivers installed with no problems. The issue I did have was that when I went to reboot I would get a low graphics mode window with lousy resolution. So I did a lot of readying here at the forums and here is what I did to get it fixed for me. I have rebooted 5 or 6 times and I am still doing good. 

1. Downloaded the 64bit beta drivers
2. Opened a terminal window and ran the command;
   sudo apt-get install build-essential linux-headers-$(uname -r)
3. Hit ctrl + alt + F1
4. Logged in
5. Changed to the director that the beta driver was located at. In my case it was /home/jeff/Desktop
6. Ran the command /etc/init.d/gdm stop
7. Ran the command sudo sh NVIDIA-Linux-x86_64-173.08-pkg2.run
8. Ran the command /etc/init.d/gdm start
9. Logged back in
10. Opened a terminal and typed sudo gedit /etc/default/linux-restricted-modules-common
11. Scrolled down to where it says DISABLED_MODULES="" and changed it to DISABLED_MODULES="nv". I then saved it.

After that I have rebooted randomly and not had any more issues and I am able to watch my movies, etc.

I hope this helps someone else. My apologies if the thread title is misleading.

---

### Post by smarks on 2008-05-24
Hey,

I am haveing a problem with my 9600GT card. I have been trying to solve this for days and can't find any help. I have 8.04 installed. when I try to run the file in F1 all i get back is:
sh: Can't open /nvidia-linux-x86-173.08-pkg1.run

I disabled gnome, idk if im missing something. the file is saved to my desktop.
 Please HELLP!!

---

### Post by Mortosa on 2008-05-24
Did you install the linux-headers and build essentials?

You can also try opening a terminal window to where the NVidia driver is downloaded to and running the command;
chmod +x nvidia-linux-x86-173.08-pkg1.run

then drop to ctrl+alt+f1 and see what happens

---

### Post by blastus on 2008-06-07
> **Mortosa said:**
> Let me start by saying I just recently switched from Kubuntu to Ubuntu and I couldnt be happier. Gnome has gotten a lot nicer since I used it last 2 or 3 years ago.

My machine has a 9600GT in it. I love it when I game, its a great card. But when I wanted to get drivers installed in Nix I had issues. I got the 173.08 beta drivers installed with no problems. The issue I did have was that when I went to reboot I would get a low graphics mode window with lousy resolution. So I did a lot of readying here at the forums and here is what I did to get it fixed for me. I have rebooted 5 or 6 times and I am still doing good. 

1. Downloaded the 64bit beta drivers
2. Opened a terminal window and ran the command;
   sudo apt-get install build-essential linux-headers-$(uname -r)
3. Hit ctrl + alt + F1
4. Logged in
5. Changed to the director that the beta driver was located at. In my case it was /home/jeff/Desktop
6. Ran the command /etc/init.d/gdm stop
7. Ran the command sudo sh NVIDIA-Linux-x86_64-173.08-pkg2.run
8. Ran the command /etc/init.d/gdm start
9. Logged back in
10. Opened a terminal and typed sudo gedit /etc/default/linux-restricted-modules-common
11. Scrolled down to where it says DISABLED_MODULES="" and changed it to DISABLED_MODULES="nv". I then saved it.

After that I have rebooted randomly and not had any more issues and I am able to watch my movies, etc.

I hope this helps someone else. My apologies if the thread title is misleading.

Thanks Mortosa. 

It seems steps #10-11 are not required for the installation of the 32bit driver but are for the 64bit driver. I was about to give up on 64bit until I found your post and did steps #10-11 :) BTW I installed build-essential only (I did not install linux-headers*.)

---

