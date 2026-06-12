---
title: "pc to tv connection thru dvi"
date: 2007-12-28
forum: Mythbuntu
---

### Post by lime4x4 on 2007-12-28
Trying to setup a mythubuntu box. Current graphic card is a ati 9550 radeon with dvi output. I have it hooked up to my tv. I can get into the bios and see everything but when i start the install i get the mythubuntu logo racing across the screen non stop then nothing but a blank screen

---

### Post by theacoustician on 2007-12-29
> **lime4x4 said:**
> Trying to setup a mythubuntu box. Current graphic card is a ati 9550 radeon with dvi output. I have it hooked up to my tv. I can get into the bios and see everything but when i start the install i get the mythubuntu logo racing across the screen non stop then nothing but a blank screen

-What TV do you have?
-How is the TV connected to the computer (DVI to DVI)?
-What resolution are you trying to run?

For myself, I find that you have to dump out to the command line at startup, install the fglrx driver manually, then restart the computer.  To do this...

Once you've dumped to command line at startup, you need to make sure you have network connectivity.  Do this by editing /etc/network/interfaces
> 
sudo pico /etc/network/interfaces

Edit as follows
> 
auto eth0
iface eth0 inet dhcp

Then save and close the document.  Restart networking services by typing this at the command line
> 
sudo /etc/init.d/networking restart

Now you have a network connection at the command line.  Time to get the restricted drivers.
> 
sudo apt-get update 
sudo apt-get install xorg-driver-fglrx

Now set module dependencies so it works right when you configure it
> 
sudo depmod -a

Configure the driver
> 
sudo aticonfig --initial 

And restart the machine
> 
sudo reboot

It should start up perfectly now.

---

### Post by lime4x4 on 2007-12-29
It's a 51 inch widescreen about 5 years old. I'm connecting the pc to the tv from dvi to dvi

---

### Post by Chuckels550 on 2008-01-09
You might want to check the setup menus on your TV.  I have a Sharp LCD TV.  If I connect my PC DVI to DVI, the TV has to be configured through its menus to accept the connection as either digital or analog.  If what I select doesn't match what the PC is sending, then I get a blank screen.

---

