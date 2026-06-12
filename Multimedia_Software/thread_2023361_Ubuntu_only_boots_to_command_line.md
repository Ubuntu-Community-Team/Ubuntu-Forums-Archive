---
title: "Ubuntu only boots to command line"
date: 2012-07-12
forum: Multimedia Software
---

### Post by Capetownlad on 2012-07-12
Hi
As above, my Ubuntu 10.04 will only boot to command line. I have spent a lot of time searching for solutions but without success and now I really need some help please.
It was a working system and it all started when my Nvidia card went faulty and I removed the drivers via synaptic. I now have a new Nvidia card and have tried re-installing Nvidia drivers via command line but without success and still cant get to the gui.
I have been using Ubuntu for some time but must admit I am not very good at using the CLI (or forums for that matter!) so patience would also be appreciated.

If anybody would care to help I would be very grateful.

Thanks in advance
Capetownlad

---

### Post by Whovian on 2012-07-12
Are you installing the drivers you previously used for the old card? What was the model of the new card you used?(sometimes the hardware may not work depending on the model you have). If the install is successful we will have test out Xorg. I am still a novice myself but I'll try my best to help you out.

Article that may help(it is debian but it will ubuntu is debian based):
[http://wiki.debian.org/NvidiaGraphicsDrivers/](http://wiki.debian.org/NvidiaGraphicsDrivers/)

---

### Post by Capetownlad on 2012-07-13
> **Whovian said:**
> Are you installing the drivers you previously used for the old card? What was the model of the new card you used?(sometimes the hardware may not work depending on the model you have). If the install is successful we will have test out Xorg. I am still a novice myself but I'll try my best to help you out.

Article that may help(it is debian but it will ubuntu is debian based):
[http://wiki.debian.org/NvidiaGraphicsDrivers/](http://wiki.debian.org/NvidiaGraphicsDrivers/)

Hi
Thanks for your reply.
Update: I must have done something right because I tried the old faulty card again and I can get to the desktop. The new card is a Geforce 210 which still wont get me to the gui.

---

### Post by Whovian on 2012-07-14
No problem glad that the old one is working again an the new card you have could be missing some driver support so here is the website to try and download it an see if it will work. Update what happens an sorry in advance if my replies are slow.
[link]("http://www.nvidia.com/object/linux_display_ia32_190.42.html")

---

### Post by Capetownlad on 2012-07-15
Sorry again but I don't seem to get an email to let me know there is a reply?
Anyhow, I have downloaded the file but it is a .run file and have no idea how to change to the download directory to run the file.

---

### Post by Capetownlad on 2012-07-15
> **Capetownlad said:**
> Sorry again but I don't seem to get an email to let me know there is a reply?
Anyhow, I have downloaded the file but it is a .run file and have no idea how to change to the download directory to run the file.

Update - I downloaded the file to the Desktop, changed directory to the desktop (cd ~/desktop)then tried (chmod +x NVIDIA-Linux-x86-190.42-pkg1.run) but nothing happens. What do you think I am doing wrong?

---

### Post by jmfal on 2012-07-15
Double click on it and double click on read-me, should have instructions there.

---

### Post by Whovian on 2012-07-15
Alright for the driver download problem I found a previous post that had the same problem [here]("http://ubuntuforums.org/showthread.php?t=1311241")  (look here first)

Summary:
Alt+Ctrl+F2 = this will bring up the terminal for you 

next type in:

```
[B]sudo /etc/init.d/gdm stop
[/B] **cd /home/user/Desktop/ **
```
(reason I changed it from the post is because that is where the driver is located on your machine)

Answer with a yes

Next type reboot an should work 

Let us know the progress :)

---

### Post by Capetownlad on 2012-07-16
> **jmfal said:**
> Double click on it and double click on read-me, should have instructions there.

Thanks jmfal but I know have it working

---

### Post by Capetownlad on 2012-07-16
> **Whovian said:**
> Alright for the driver download problem I found a previous post that had the same problem [here]("http://ubuntuforums.org/showthread.php?t=1311241")  (look here first)

Summary:
Alt+Ctrl+F2 = this will bring up the terminal for you 

next type in:

```
[B]sudo /etc/init.d/gdm stop
[/B] **cd /home/user/Desktop/ **
```
(reason I changed it from the post is because that is where the driver is located on your machine)

Answer with a yes

Next type reboot an should work 

Let us know the progress :)


Thank you very much for trying to help me but I have managed to get the card working with a simple solution. I don't know why I didn't think of trying it before. Maybe because I was happy with the behaviour of the driver I never thought to change it.
Anyway, what I did was to fit my old and faulty card and boot. (I had to be quick because it plays up when it gets hot) I then used System - Admin - Hardware drivers to download and update to the version current - recommended driver. Then shut down and change cards and reboot. The new card Geforce 210 now works. Wey hey! I am also using the DVI out rather than the VGA I tried previously so don't know if that was an issue or not but happy to carry on as is.
So after all those hours of frustration and trying command line  scripts, it was an easy fix.
Thanks so much to all on here who offered to help.
Cheers

---

### Post by Whovian on 2012-07-18
I'm glad it is working now an happy to help as much as the community can :)

---

