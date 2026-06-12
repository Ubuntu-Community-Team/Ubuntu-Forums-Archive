---
title: "Need help installing the newest BroadCom STA Driver (begginner)"
date: 2010-11-28
forum: Networking &amp; Wireless
---

### Post by Emmanuel Alvarado on 2010-11-28
Hello, 
i am new to Ubuntu 10.10, i just recently recieved a Mini CQ10-525DX with a Broadcom 4313 wlan card. when loading ubuntu i notice it says that it supports 4311 4312, so i looked on the broadcom website and they have a newer update with 4313 coverage. I downloaded it but do not know how to install it. If someone could help me i would be very grateful, and if possible make it as simple as possible since i am beginning to learn the OS.
Thank You

---

### Post by uncaspi on 2010-11-28
Open a terminal and rename existing wl driver.
sudo mv /lib/modules/$(uname -r)/kernel/drivers/net/wireless/wl.ko <space>/lib/modules/$(uname -r)/kernel/drivers/net/wireless/wl.original.ko
Your tarball file are probably hybrid-portsrc_x86-32_v5.60.246.6.tar.gz
Make a new directory  mkdir driver  and cp hybrid-portsrc_x86-32_v5.60.246.6.tar.gz ./driver
then issue cd driver

Unpack the file tar zxvf hybrid-portsrc_x86-32_v5.60.246.6.tar.gz

sudo make
sudo make install
sudo depmod -a
sudo modprobe wl


and thats it. Connect via network-manager

---

### Post by Emmanuel Alvarado on 2010-11-28
I am not completely sure what im suppose to do so, i open terminal then the first thing i do is type:
sudo mv /lib/modules/$(uname -r)/kernel/drivers/net/wireless/wl.ko <space>/lib/modules/$(uname -r)/kernel/drivers/net/wireless/wl.original.ko <== exactly like that? or does uname mean my computer name which is emmanuel? and is <space> required? i know it sounds silly but i have little knowledge on open source programming but i would love to learn

Then my Tarbil file is  hybrid-portsrc_x86-32_v5.60.246.6.tar.gz

To make a new directory do i have to use Terminal also and insert: mkdir driver, and cp hybrid-portsrc_x86-32_v5.60.246.6.tar.gz ./driver respectively? 

when i do the following, Sudo Make, Sudo Make Install, Sudo Depmod -a etc. do i need to also type the directory?

Thanks, i know its alot but i would appreciate it so much

---

### Post by uncaspi on 2010-11-28
<space> means to press the spacebar.$(uname -r) is your kernel version. Type it like I said. Yes you use the terminal for the rest of the commands. Linux is case sensitive so its like I typed it. After the cp command type
sudo make
sudo make install
sudo depmod -a
sudo modprobe wl

as I said

---

### Post by Emmanuel Alvarado on 2010-11-28
Alright so i did what you said and i got the following.
For the renaming part it said :
cannot stat: mv '/lib/modules/$(uname -r)/kernal/drivers/net/wireless/wl.ko No such file or directory

for the making directory it says:
mkdir: cannot create directory 'driver' File exists (so i would assume that means the directory has been made)

for the CP part:
cp: cannot stat 'hybrid-portsrc_x86_5.60.246.6.tar.gz ./driver no such file or directory. (is this because this file is not inside the directory? if so how could i move it there, as right now its in the downloads folder) 

This is were i stopped since i did not seem to know if anything was happening. Thanks

---

### Post by uncaspi on 2010-11-28
there was an spelling error for kernel in the path. It should be
sudo mv /lib/modules/$(uname -r)/kernel/drivers/net/wireless/wl.ko wl.orig.ko

Try mkdir mydir and copy the tarball hyb... to this as I said.
You must copy it from your download folder to /home/emmanuel or whatever it is. You see the name of the folder when you open the terminal.

---

### Post by Emmanuel Alvarado on 2010-11-28
okay so after some manual searching i went into the wireless directory and there is no file for Wl.ko to rename is this an issue?

i moved the tarbill into the drivers folder that is /driver.

so from here
what exactly do i type into the cp command?

is it still:cp hybrid-portsrc_x86-32_v5.60.246.6.tar.gz ./driver
exactly like above, what does cp do? 
When i type above it says there is no directory so i must be doing something wrong there, 'cp: cannot stat 'hybrid-portsrc_x86-32_v5.60.246.6.tar.gz ./driver'

after this i unpack it in the same folder? the driver directory, and itll become hyrbid-portsrc_x86-32_v5.60.246.6 directory. 

Then when i do the Sudo commands do i have to put that directory each time? if so would it be like:
sudo make hybrid-portsrc_x86-32_v5.60.246.6
sudo make install hybrid-portsrc_x86-32_v5.60.246.6
sudo depmod -a hybrid-portsrc_x86-32_v5.60.246.6
sudo modprobe wl hybrid-portsrc_x86-32_v5.60.246.6?

Once again i apologize i really just dont know whats going on, all i need is wifi to work on this thing then ill be content as i dont need to do anything else advanced

---

### Post by uncaspi on 2010-11-28
/driver is your root folder. You should cp to your /home folder.
Do this. cd /home
ls
Find your username and do cd username

---

### Post by Emmanuel Alvarado on 2010-11-28
okay im getting some progress here i was able to cp the hybrid-portsrc_x86-32_v5.60.246.6.tar.gz.

so now do i do the sudo commands while driver directory is my root
or do i make the hybrid-portsrc_x86-32_v5.60.246.6 my root now?

---

### Post by uncaspi on 2010-11-28
/   is your root folder.
/home is your home folder
/home/put your username here, and you have your /home/user  folder and to this folder you should cp hybrid.....gz

---

### Post by Emmanuel Alvarado on 2010-11-28
i give up... im just not getting it.. it says i have the sta driver installed but it doesnt connect to anything, i can create a wireless network but it isnt connecting to anything in my house... when it works fully does it show the networks? or you have to type it in manually

---

### Post by uncaspi on 2010-11-28
If it works it should show your networks in the area around you.

---

### Post by 1337hippo on 2010-12-04
> **uncaspi said:**
> Open a terminal and rename existing wl driver.
sudo mv /lib/modules/$(uname -r)/kernel/drivers/net/wireless/wl.ko <space>/lib/modules/$(uname -r)/kernel/drivers/net/wireless/wl.original.ko
Your tarball file are probably hybrid-portsrc_x86-32_v5.60.246.6.tar.gz
Make a new directory  mkdir driver  and cp hybrid-portsrc_x86-32_v5.60.246.6.tar.gz ./driver
then issue cd driver

Unpack the file tar zxvf hybrid-portsrc_x86-32_v5.60.246.6.tar.gz

sudo make
sudo make install
sudo depmod -a
sudo modprobe wl


and thats it. Connect via network-manager

I followed these instructions and was successful, however, at the last step I got this:

> $ sudo modprobe wl
WARNING: All config files need .conf: /etc/modprobe.d/aliases, it will be ignored in a future release.


is that OK?

---

