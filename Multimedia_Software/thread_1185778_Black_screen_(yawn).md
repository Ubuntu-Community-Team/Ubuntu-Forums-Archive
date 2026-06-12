---
title: "Black screen (**yawn**)"
date: 2009-06-12
forum: Multimedia Software
---

### Post by Jannes. on 2009-06-12
Hello everyone, i'm noob in ubuntu.

I just installed ubuntu 9.04. What i would do was
Install my Enemy-Territory...
But first i had to install Nvidia drivers. So i took from an ubuntu site ([http://ubuntuforums.org/showthread.php?t=5246](http://ubuntuforums.org/showthread.php?t=5246)) the info how to install ET. There they said i had to go to hard drivers. And install the ones who arent installed yet. After two or tree errors i could install it. After reboot i got a black screen.
Tried so many options, read all topics bout this but i understand anything... 

Please help me, i need my pc next week...

grtz

---

### Post by gradinaruvasile on 2009-06-12
What is that you did exactly? What video card u have?

---

### Post by Jannes. on 2009-06-12
I just activated one of the two nvidia drivers i got by hard drivers...

then i had to reboot, i did and now i got blackscreen...(can see my mouse and move it etc)
It fails when i try to boot in safe mode, it fails when i normally reboot... and i dont want to lose my files :(

NVIDIA GEFORCE FX 5200

---

### Post by gradinaruvasile on 2009-06-12
Which version drivers did u try?
I suppose u installed them from system->administration->hardware drivers
To restore your graphical interface,boot with recovery mode, choose xfix and then continue boot normally. This will disable the installed drivers though.
Post the driver version.

---

### Post by Jannes. on 2009-06-12
i think it was something with 170...

Mhm can u repeat that all and explain it in steps...

Im beginner xD

---

### Post by Jannes. on 2009-06-13
Maybe solutions are, Reinstall older driver of nvidia, delete the newest one...

BUT HOW?

---

### Post by ItaniKnight on 2009-06-14
The official Nvidia install instructions are here: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

> 1. Switch to the console (Try using ctrl+alt+F1, or reboot and select recovery mode from the GRUB menu.)
2. Use your text editor to open /etc/X11/xorg.conf. (try "sudo nano /etc/X11/xorg.conf")
3. Find the line that says Section "Screen"
4. Insert a new line that says Option "UseDisplayDevice" "DFP".
5. Save the file. If you had to restart into recovery mode, type reboot, otherwise restart your display using sudo /etc/init.d/gdm restart.

May or may not work. I have exactly this problem and this solution does nothing for me, but apparently it works for everyone else.

---

### Post by gradinaruvasile on 2009-06-14
> **Jannes. said:**
> Maybe solutions are, Reinstall older driver of nvidia, delete the newest one...

BUT HOW?

open a terminal and type

sudo apt-get remove --purge nvidia-*

sudo dpkg-reconfigure xserver-xorg

reboot

go to the system->administration->Hardware Drivers

select the recommended driver and activate it 
reboot

---

### Post by Jannes. on 2009-06-14
mhm in the paper i found they said

the old trick from
sudo dpkg-reconfigure xserver-xorg
isnt anymore for ubuntu 9.04


Im going to try all ur options now.

This paper i found on internet today --> [http://sites.google.com/site/computertip/geenbeeld](http://sites.google.com/site/computertip/geenbeeld)

its in dutch...

Lets try your options

---

### Post by gradinaruvasile on 2009-06-14
That command helped me alot. Maybe the xfix option does the same, but i have more confidence in stuff i type... It creates a new configuration for the X server from ground up.

---

### Post by Jannes. on 2009-06-14
> **gradinaruvasile said:**
> That command helped me alot. Maybe the xfix option does the same, but i have more confidence in stuff i type... It creates a new configuration for the X server from ground up.

still the black screen with my mouse...

---

### Post by Jannes. on 2009-06-14
> **ItaniKnight said:**
> The official Nvidia install instructions are here: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)



May or may not work. I have exactly this problem and this solution does nothing for me, but apparently it works for everyone else.

this doesnt work because in the sudo nano /etc/x11/xorg.conf there is nothing inside it

---

### Post by gradinaruvasile on 2009-06-14
> **Jannes. said:**
> this doesnt work because in the sudo nano /etc/x11/xorg.conf there is nothing inside it

Thats x should be uppercase:
```
sudo nano /etc/[COLOR="Red"]X[/COLOR]11/xorg.conf
```

What did u do exactly?

---

### Post by Jannes. on 2009-06-14
how do u mean


I did what the other guy posted

Ive got screen again something bout low graphix mode

there was something bout there is already something in use...
yes or no, i did yes and i see my black screen again...

---

### Post by gradinaruvasile on 2009-06-14
Before going on, did u install drivers downloaded from the Nvidia site? Cause those are removed differently.

If not, do the following exactly:

From the beginning:

Step 1

Reboot, chose recovery mode.
Select root terminal.
When u are at the command prompt type:
```
dpkg-reconfigure xserver-xorg
apt-get remove nvidia*
```
press ctrl-d
select resume booting

Step 2

Login
go to the System->Administration->Hardware Tabs

U should have a possibility to chose a driver. Select the recommended one. Click activate.
Reboot.

---

### Post by Jannes. on 2009-06-14
> **gradinaruvasile said:**
> Before going on, did u install drivers downloaded from the Nvidia site? Cause those are removed differently.

If not, do the following exactly:

From the beginning:

Step 1

Reboot, chose recovery mode.
Select root terminal.
When u are at the command prompt type:
```
dpkg-reconfigure xserver-xorg
apt-get remove nvidia*
```
press ctrl-d
select resume booting



there it finishes...
after resume booting i got my black screen with only the mouse again...

---

### Post by Jannes. on 2009-06-15
Oke what i did was

-> go on the live CD of ubuntu
-> Backup all my files to my external HDD
-> Reinstall ubuntu

And now im on my fresh new ubuntu.

After every update im going to reboot so i can see where the problem is.

U will hear me later with moooree problems...

Thanx for the help and see you later

grtzz

---

