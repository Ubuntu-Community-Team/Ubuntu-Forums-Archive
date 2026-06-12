---
title: "NVIDIA drivers updates"
date: 2010-09-02
forum: Multimedia Software
---

### Post by ccc2007chaos on 2010-09-02
Hi,
I have installed the restricted drivers for NVIDIA graphics card and has  not been updated. I'm stuck with the version 195.36.24 while for linux  and specific my graphics card driver version has reached 256.44 released  on 2010.08.02. Is there going to be any update from the Ubuntu updates?  Do we have to wait for update from Ubuntu or there is no reason to not  update by downloading the drivers from the NVIDIA site?

Thanks for any information.

---

### Post by tripmix on 2010-09-02
Download the driver, it's a major improvement. It's easy just download it then run```
sudo apt-get install module-assistant
sudo module-assistant update
sudo module-assistant prepare
```
Then you need to exit to console by pressing ctrl+alt+f1 then
```
cd /where/you/downladed/driver
sudo /etc/init.d/gdm stop
sudo sh NVIDIA*
sudo /etc/init.d/gdm start
```

---

### Post by ccc2007chaos on 2010-09-02
> **tripmix said:**
> Download the driver, it's a major improvement. It's easy just download it then run```
sudo apt-get install module-assistant
sudo module-assistant update
sudo module-assistant prepare
```Then you need to exit to console by pressing ctrl+alt+f1 then
```
cd /where/you/downladed/driver
sudo /etc/init.d/gdm stop
sudo sh NVIDIA*
sudo /etc/init.d/gdm start
```


and then how do i exit from console?

---

### Post by DeMus on 2010-09-02
> **tripmix said:**
> Download the driver, it's a major improvement. It's easy just download it then run```
sudo apt-get install module-assistant
sudo module-assistant update
sudo module-assistant prepare
```
Then you need to exit to console by pressing ctrl+alt+f1 then
```
cd /where/you/downladed/driver
sudo /etc/init.d/gdm stop
sudo sh NVIDIA*
sudo /etc/init.d/gdm start
```

**sudo /etc/init.d/gdm stop (or start)** is valid for older version sof Ubuntu. For 10.04 (Lucid) it is:
**```
sudo service gdm stop (or start)
```**

---

### Post by ccc2007chaos on 2010-09-02
"The distribution-provided pre-installed script failed. Continue  installation anyway?" Yes/No. What should i choose? If choose no it just  does not install anything but if i install will be any problem  occurred?

---

### Post by tripmix on 2010-09-02
Thats OK, it just means it didn't find a precompiled driver for ubuntu, thats normal. Just choose yes and accept on everything except the last one after it's finished installing that asks if you want it to auto edit xorg.conf. I just press enter all the way through as it normally automatically selects the choices you want.

---

### Post by ccc2007chaos on 2010-09-02
Well, got some troubles with this.

I did what you (both) said :
Download the driver,
```
sudo apt-get install module-assistant
sudo module-assistant update
sudo module-assistant prepare
```Ctrl+Alt+F1
i logged in
```
sudo service gdm stop // (sudo /etc/init.d/gdm stop also worked in first attempt)
sudo sh NVIDIA-Linux-x86-256.53.run
// Hit yes/accept/etc to everything even to make xorg.conf
// (back to console)
sudo service gdm start
```Everything seemed ok, but when i restarted a window appeared that said "Ubuntu runs on low resolution" or something like that. It had some options then to choose such as Restart X, Reconfigure hardware and some more. I tried some of the options and logged in low resolution ( i think 800x600 ) and tried to find out. The nvidia-settings couldn't find the driver and said to try "sudo nvidia-xconfig" to make a configuration file automatically. I tried sometimes more with restarts and other but nothing. So i boot ubuntu from usb to see how the files are configured there. Well, there was no /etc/X11/xorg.conf in the filesystem of ubuntu ( in the usb ), so i though it would be good to deleted so i renamed in the ubuntu partition the /etc/X11/xorg.conf to something else just to not be found by the os.
I reboot to Ubuntu ( hard drive ) and the graphics where good. but no graphics card driver of nvidia was in use. so i uninstalled ( remove ) from the restricted drivers the activated driver and i restarted. i reinstalled the 256.53 driver with the method described in the beginning, restarted and here i am in the logon screen. i login and again low graphics. i opened nvidia-settings and i could configure successfully the graphic card. i saved the conf file and restarted. but the resolution after the login screen were again not fixed in 1280x800 as i saved in xorg.conf!
Well the thing is that i used a button never used before and the resolution changed magically! Fn+F7! It's a special function button that has an (LCD/display out) icon. I don't know how it came to me, but it needs to be pressed after every login.
Do you know something about that? It happens to you too?

---

### Post by Linuxforall on 2010-09-02
Easist and safest way to update to latest nvidia, ati and Intel is via x-swat ppa

sudo add-apt-repositor ppa:ubuntu-x-swat/x-updates 

sudo apt-get update

sudo apt-get upgrade

At this point, your pre-existing nvidia or intel or ati would be automatically updated and if you install via hardware applet, you will have latest driver for your card.

---

### Post by ccc2007chaos on 2010-09-02
> **Linuxforall said:**
> Easist and safest way to update to latest nvidia, ati and Intel is via x-swat ppa

sudo add-apt-repository* ppa:ubuntu-x-swat/x-updates 

sudo apt-get update

sudo apt-get upgrade

At this point, your pre-existing nvidia or intel or ati would be automatically updated and if you install via hardware applet, you will have latest driver for your card.

So i have to reinstall the drivers from "Hardware Drivers" ? :-k

*(add the 'y'  for no one to get confused)

---

### Post by NoNameWill on 2010-09-02
I have never had the nvidia driver "stick" with installing through the repository. It would fail after a few restarts.  
 Today I had to install them again after a update. The way described by tripmix. The only command I didn't use was
```
sudo service gdm stop
```but that is because I am still learning.

Thanks for sharing. Now I know how to get to tty from terminal.

---

### Post by Linuxforall on 2010-09-03
> **ccc2007chaos said:**
> So i have to reinstall the drivers from "Hardware Drivers" ? :-k

*(add the 'y'  for no one to get confused)

If its already installed, then no need, they will be updated to latest.

---

### Post by ccc2007chaos on 2010-09-03
> **Linuxforall said:**
> If its already installed, then no need, they will be updated to latest.

No, i downloaded from nvidia site the drivers and had them installed. That was what i asking, if i have to install from the "Hardware Drivers" to have the updates. Sorry for my bad english. I currently have the site's drivers.

---

### Post by keypox on 2010-09-03
x swat still not updated to newest. [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

---

### Post by RemmyNumber7 on 2010-09-03
I have Ubuntu Linux 9.10    1 gig of ram and a 80 gig hard drive.    	MSI motherboard I have a Ge Force 6600 ddr 256mb AGP that I want to install. I am running now on a ATI  AGP  but it is too old to get it installed, besides no driver for it. 

How do I Install that Ge Force 6600 ddr 256mb AGP card.?????   I'm a little new at Linux too. I already downloaded the Driver from Nvidia it is on my desktop now. Can I install the driver first then shut down the computer Unplug it. Put in the Video Card.  How dose this process of adding a video driver work????

---

