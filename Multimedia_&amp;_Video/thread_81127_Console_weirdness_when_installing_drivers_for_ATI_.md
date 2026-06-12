---
title: "Console weirdness when installing drivers for ATI Mobility Radeon 9700"
date: 2005-10-23
forum: Multimedia &amp; Video
---

### Post by moerl on 2005-10-23
I was using the Ubuntu guide, accessible via the life-saver icon on top by default, to install ATI 3D acceleration on my Breezy. That guide says to install the "xorg-driver-fglrx" package first, then execute the following in the terminal: 

echo fglrx | sudo tee -a /etc/modules
sudo depmod -a ; sudo modprobe fglrx
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup 
sudo sed -i -e 's/"ati"/"fglrx"/' /etc/X11/xorg.conf

After just pasting it and not having hit any keys on the keyboard, I get this:

ismar@ISMARubuntu:~$ echo fglrx | sudo tee -a /etc/modules
Password:
fglrx
ismar@ISMARubuntu:~$ echo fglrx | sudo tee -a /etc/modules
fglrx
ismar@ISMARubuntu:~$ sudo depmod -a ; sudo modprobe fglrx
FATAL: Module fglrx not found.
ismar@ISMARubuntu:~$ sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
ismar@ISMARubuntu:~$ sudo sed -i -e 's/"ati"/"fglrx"/' /etc/X11/xorg.conf

First of all, it looks odd that when I paste this block of commands that should take up four lines, the prefix "ismar@ISMARubuntu:~$" always shows up before every line. I expected it to look like this:

ismar@ISMARubuntu:~$ echo fglrx | sudo tee -a /etc/modules
sudo depmod -a ; sudo modprobe fglrx
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup 
sudo sed -i -e 's/"ati"/"fglrx"/' /etc/X11/xorg.conf

or, even nicer, this:

ismar@ISMARubuntu:~$
echo fglrx | sudo tee -a /etc/modules
sudo depmod -a ; sudo modprobe fglrx
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup 
sudo sed -i -e 's/"ati"/"fglrx"/' /etc/X11/xorg.conf

but well, it does not.

Can anyone help me get this to work? The weird thing is that the required package DOES seem to be installed on my system. At least Synaptic thinks so, listing the "xorg-driver-fglrx" package under INSTALLED, with a green box next to it.

What gives?

---

### Post by Rychek on 2006-10-06
> **moerl said:**
> I was using the Ubuntu guide, accessible via the life-saver icon on top by default, to install ATI 3D acceleration on my Breezy. That guide says to install the "xorg-driver-fglrx" package first, then execute the following in the terminal: 

echo fglrx | sudo tee -a /etc/modules
sudo depmod -a ; sudo modprobe fglrx
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup 
sudo sed -i -e 's/"ati"/"fglrx"/' /etc/X11/xorg.conf

After just pasting it and not having hit any keys on the keyboard, I get this:

ismar@ISMARubuntu:~$ echo fglrx | sudo tee -a /etc/modules
Password:
fglrx
ismar@ISMARubuntu:~$ echo fglrx | sudo tee -a /etc/modules
fglrx
ismar@ISMARubuntu:~$ sudo depmod -a ; sudo modprobe fglrx
FATAL: Module fglrx not found.
ismar@ISMARubuntu:~$ sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
ismar@ISMARubuntu:~$ sudo sed -i -e 's/"ati"/"fglrx"/' /etc/X11/xorg.conf

First of all, it looks odd that when I paste this block of commands that should take up four lines, the prefix "ismar@ISMARubuntu:~$" always shows up before every line. I expected it to look like this:

ismar@ISMARubuntu:~$ echo fglrx | sudo tee -a /etc/modules
sudo depmod -a ; sudo modprobe fglrx
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup 
sudo sed -i -e 's/"ati"/"fglrx"/' /etc/X11/xorg.conf

or, even nicer, this:

ismar@ISMARubuntu:~$
echo fglrx | sudo tee -a /etc/modules
sudo depmod -a ; sudo modprobe fglrx
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup 
sudo sed -i -e 's/"ati"/"fglrx"/' /etc/X11/xorg.conf

but well, it does not.

Can anyone help me get this to work? The weird thing is that the required package DOES seem to be installed on my system. At least Synaptic thinks so, listing the "xorg-driver-fglrx" package under INSTALLED, with a green box next to it.

What gives?

This looks normal to me.  When you copied the block and pasted it in the terminal, you pasted the carriage returns as well.  The terminal executed all but the last line automatically, hence the prompt before each command.

Try copying and pasting each line individually.

---

