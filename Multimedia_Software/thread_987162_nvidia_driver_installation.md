---
title: "nvidia driver installation"
date: 2008-11-19
forum: Multimedia Software
---

### Post by no1zaman on 2008-11-19
i am in a serious trouble after i bought nvedia 9800gt graphics card its driver is creating lot of trouble.can uppl plz tell me how to install nvidia driver for my pc
my configuratio is:
intel dual core 2.5 ghz
1gb ram
nvidia 9800gt 512 mb
it is working fine in windows but not on ubuntu 8.04 which i am using right now.plz help me:confused::confused::confused:

---

### Post by sadiqdude on 2008-11-19
8A)hi installing nvidia driver is easy and it wll hardly take few minutes just follow these instructions:
note:u should have nvidia driver for linx(can be downloaded from nvidia site  [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)) and your hardy heroin (8.04) ubuntu disk..here is the procedure
STEP 1:
Backup xorg.conf by typing following command
		$ sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
STEP 2:
Install Build Essential
	Insert your &#8220;ubuntu&#8221; cd in cd-rom drive if necessary and in terminal type:
	$ sudo apt-cdrom add (will ask for Gusty Gibbon cd, click yes)
	$ sudo apt-get update
	$ sudo apt-get install build-essential 
STEP 3:
Remove Default Ubuntu nVidia Driver/Settings
	in the terminal type following command:
	$ sudo apt-get --purge remove linux-restricted-modules-`uname -r` linux-restricted-modules-common nvidia-glx nvidia-settings nvidia-kernel-common
IT WILL ASK U TO REMOVW SEVERAL FILES ANSWER YES
remove file manually by typing following command in terminal:
	$ sudo rm /etc/init.d/nvidia-*
dont worry if the system displays file cannot be removed
STEP 4:
Install nVidia Driver/Settings
NOTE::This action is to be performed in text mode so it is advisable to note down all the steps if you can't remember them.Copy your downloaded driver to desktop. The file name is something like this &#8220;NVIDIA-Linux-x86-169.07.pkg1.run&#8221;. To install it you have to type &#8220; sudo sh NVIDIA-Linux-x86-169.07.pkg1.run &#8221;. No need to type whole file name just type first latter(in this case capital N) and press TAB to autocomplete the file name.
Let us come to actual installtion steps
Press CTRL-ALT-F1 (so as to get to the command line, not a windowed terminal, but out of the graphical interface GUI)
login with your username and password (if required) and type:
	$ sudo /etc/init.d/gdm stop (To stop &#8220;Graphics Device Manager&#8221;)
	$ cd /home/sadiq/Desktop (Navigate to Desktop i.e. nvidia driver location)
NOTE:replace "sadiq" with ur user name in the above commaand
STEP 5:
start nvidia installer by typing following command:
	$ sudo sh NVIDIA-Linux-x86-169.07.pkg1.run

NOTE::File name may not be same as written above
Agree to license terms. Then it'll prompt you to search for &#8220;Precompiled Headers&#8221;. Choose no. It'll then compile the kernel.At last it'll ask you to configure your driver using nvidia-xconfig utility. Again choose yes.
STEP 6:
Restart the login manager by typing:
	$ sudo /etc/init.d/gdm restart
voila u have installed ur nvidia graphics driver
NOTE::if anything goes wrong and you have problems with the xserver (i.e. if it doesn't start) you can type:
	$ sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf

---

### Post by Serpher on 2008-11-20
Confirming this. I'm a Linux noob and I'm setting up my first system and this worked **WONDERFULLY**.

---

### Post by nicoladimaria on 2008-11-22
Does this videocard work flawlessly in intrepid ?

---

### Post by sadiqdude on 2008-11-23
it should work for intipid too...i have not yet tested............:):):)

---

### Post by SirJYK on 2008-12-09
I tried with no luck.  This is very frustrating.  This same reason stopped me with version 6.1, ie. I could not get my vid card working properly.

---

### Post by warlog on 2009-02-12
i managed to install the graphic card but the problem occured after that. After installation i reboot my notebook. The login screen comes in perfect resolution but after providing my login credentials [COLOR="DarkRed"]the TFT goes off[/COLOR]. If you have any solution then please post it here.

---

