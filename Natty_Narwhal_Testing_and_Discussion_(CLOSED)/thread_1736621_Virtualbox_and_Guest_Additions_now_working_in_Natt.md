---
title: "Virtualbox and Guest Additions now working in Natty"
date: 2011-04-22
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by tlcstat on 2011-04-22
Greetings,
The Oracle Virtualbox PPA is now working in Natty.

In terminal
echo "deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) $(lsb_release -sc) contrib" | sudo tee /etc/apt/sources.list.d/virtualbox.list

wget -q [http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc](http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc) -O- | sudo apt-key add -

sudo apt-get update

sudo apt-get install virtualbox-4.0

To install the guest additions that allow you to use your Ubuntu files, usb ports, etc
In terminal
sudo apt-get install dkms (if dkms is not already installed)

Create your virtual machine if not already created and open the virtual machine.
On the top menu bar choose "Devices"/CD-ROM Virtual/ 
Then browse to /usr/share/virtualbox and choose the guest additions iso to load into the virtual cdrom. You can then install the guest additions from inside your vm from the virtual cdrom.

The whole ordeal is a bit techy but I hope this is a help.

---

### Post by teachop on 2011-04-22
> **tlcstat said:**
> Greetings,
The Oracle Virtualbox PPA is now working in Natty.

In terminal
echo "deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) $(lsb_release -sc) contrib" | sudo tee /etc/apt/sources.list.d/virtualbox.list

wget -q [http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc](http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc) -O- | sudo apt-key add -

sudo apt-get update

sudo apt-get install virtualbox-4.0

To install the guest additions that allow you to use your Ubuntu files, usb ports, etc
In terminal
sudo apt-get install dkms (if dkms is not already installed)

Create your virtual machine if not already created and open the virtual machine.
On the top menu bar choose "Devices"/CD-ROM Virtual/ 
Then browse to /usr/share/virtualbox and choose the guest additions iso to load into the virtual cdrom. You can then install the guest additions from inside your vm from the virtual cdrom.

The whole ordeal is a bit techy but I hope this is a help.
Virtualbox has worked for me right on through the betas.  I downloaded from the Oracle website, 4.04 I think, then added the usb extension later.  Have an XP in there with no issues.

---

### Post by xebian on 2011-04-22
VirtualBox 4.0.6 is now available and there is a deb file for Natty.  

DKMS is not a requirement to install vbox guest additions.

---

### Post by andrew.46 on 2011-04-22
> **xebian said:**
> VirtualBox 4.0.6 is now available and there is a deb file for Natty.  

Has this release solved the crashes / freezes seen with Natty + Unity as guest?

---

### Post by Hedgehog1 on 2011-04-23
> **andrew.46 said:**
> Has this release solved the crashes / freezes seen with Natty + Unity as guest?

Finished an install of Natty as guest on 10.10 about 15 minutes ago. Works fine (once guest extensions are loaded and GPU is set to 512mb and 3d).

I can start build my screen shots of Natty installs and common issues now (for the big day next week).

***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-04-23
I am also pleased to report that Vbox also now installs and runs in Natty (although the install complained just a bit):

[IMG]http://img546.imageshack.us/img546/3093/vboxinnatty.png[/IMG]


***The Hedge***

:KS

---

### Post by tlcstat on 2011-04-23
Greetings,
I added this line to my original post "Be sure to remove old versions of Virtualbox first". The line "sudo apt-get install virtualbox-4.0" will install the latest version of Virtualbox released by Oracle for Natty.
Note: You don't have to delete your old .vdi files, they will continue to work.

---

