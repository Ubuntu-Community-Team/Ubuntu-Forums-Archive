---
title: "[HELP] Installing NVidia Geforce 4 MX 440 drivers with NO INTERNET CONNECTION"
date: 2008-04-14
forum: Multimedia &amp; Video
---

### Post by SkinnyJeans929 on 2008-04-14
Hi

Gutsy 7.10
P4 1.8GHz / 30GB Ext3 partition / Dualboot with XP / 128mb Nvidia Geforce 4 MX 440 AGP 8x


i need to install drivers for my video card Geforce 4MX 440 AGP 8x. I DONT HAVE AN INTERNET CONNECTION. so in an effort to resolve this myself, here's what i did:

- went to nvidia.com and searched for my card 
- downloaded the driver using another computer and placed in a USB drive
- placed the driver and the readme in my desktop
- followed the readme and did '# sh NVIDIA-Linux-x86-96.43.05-pkg1.run'
- got error message sh: cant open NVIDIA-Linux-x86-96.43.05-pkg1.run


i cant seem to do this without an internet connection. im trying to get this to work because my screen is not the right size as i want it to. as well, i want to get compiz to work as well and cant seem to do so. Could anyone please be kind enough to walk me through configuring compiz so i can have the cube desktop thing and wobbly windows feature? 

thanks in advance.

---

### Post by SkinnyJeans929 on 2008-04-14
still no luck with this

---

### Post by naja on 2008-04-14
Hi
try downloading the Nvidia glx legacy package from the repositories- use synaptics  do download it,then go to /var/cache/apt/archieves -you will find all the downloaded packages there.
thanks

---

### Post by SkinnyJeans929 on 2008-04-15
uhm, yeah .. that could work. IF i had internet connection at home. i'm doing my downloads in the office running windows 2000. aint that a bummer .. 

well i fiddled around with the nvidia installer once more today. i managed to get it running by doing this:

cd /home/usr/Desktop
sudo sh NVIDIA-Linux-x86-93.46.05.pkg1.run

i get the installer gui and it says that i'm running an x server. it says i have to quit the x server to get the installer going. i went back to the readme file, and all it said was that i have to edit something in the /inittab ... and set the session to '3' or something to that effect by editing the line that says:

id:n:something (where N is the session type)

does this sound familiar? how i understand this is that it wants me to boot up to ubuntu with a command prompt instead of the GUI. is that correct? how do i this and how do i go back to the gui if in any case i mess it up all the more? 


thanks!

---

### Post by aeiah on 2008-04-15
first, backup your xorg.conf file, then drop to the shell with alt+ctrl+F1 and stop the gdm with ```
sudo /etc/init.d/gdm stop
```

then run your nvidia.run file

to get the gui back up run ```
sudo /etc/init.d/gdm start
```

make sure you back up your xoooorrrggggg! :p

---

