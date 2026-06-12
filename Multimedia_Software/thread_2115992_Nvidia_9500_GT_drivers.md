---
title: "Nvidia 9500 GT drivers"
date: 2013-02-14
forum: Multimedia Software
---

### Post by abhayadevs on 2013-02-14
Hey, i am stuck by nit getting the proper driver for 9500 GT. How did you guys managed to get the driver in Ubuntu 12.04 LTS for the nvidia card? which version of driver is been used? pls share the source. everytime i do install something i can see it in the lsmod but the nvidia-setting is saying that it is not in us and i need to run nvidia-xconfig. if i run this command nothing happens but the resolution is getting dropped and i had to eventually remove the xorg.cfg to get the display alright.

any help is highly appreciated as i am stuck with this for days.

end of the day i need to intall the ubuntu studio 12.04 lts version.

---

### Post by oldos2er on 2013-02-14
Post moved to its own thread.

---

### Post by oldfred on 2013-02-14
Re: How To Install Nvidia Drivers [v8.1.2.12 by Bogan]. post 1126
[http://ubuntuforums.org/showthread.php?t=1743535&page=113](http://ubuntuforums.org/showthread.php?t=1743535&page=113)
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
[http://ubuntuforums.org/showthread.php?t=2081649](http://ubuntuforums.org/showthread.php?t=2081649)

    
I have the 9600GT and have had to use nomodeset to boot liveCD and on first boot. But then I install the nVidia drivers from Ubuntu not from nVidia.
Ubuntu now has several choices. 

       # You may need headers - meta package for 12.10 version:
sudo apt-get install linux-headers-generic
# only reason to purge is there are several versions, if you know you have different nVidia use that:
#To see available  versions:
dpkg -l | grep -i nvidia*
apt-cache search nvidia-sett*
# Houseclean out all old versions to avoid issues
sudo apt-get remove --purge < nvidiadriverpackagename>
 # [ using the correct names] for each driver, before running: 
sudo apt-get purge nvidia*
# I used nvidia-current-updates & nvidia-settings-updates, example below is just nvidia-current, use version you prefer
sudo apt-get install nvidia-current
sudo apt-get install nvidia-settings
sudo dpkg-reconfigure nvidia-current
sudo nvidia-xconfig
sudo reboot
May want nvidia-current, nvidia-current-updates or nvidia-current-experimental-XXX for most recent testing version.
apt-cache search nvidia-sett*

---

### Post by gordintoronto on 2013-02-14
Indeed. With my 9400 GT, I needed:
linux-headers-generic
nvidia-current

All done.

---

### Post by abhayadevs on 2013-02-15
> **oldfred said:**
> Re: How To Install Nvidia Drivers [v8.1.2.12 by Bogan]. post 1126
[http://ubuntuforums.org/showthread.php?t=1743535&page=113](http://ubuntuforums.org/showthread.php?t=1743535&page=113)
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
[http://ubuntuforums.org/showthread.php?t=2081649](http://ubuntuforums.org/showthread.php?t=2081649)

    
I have the 9600GT and have had to use nomodeset to boot liveCD and on first boot. But then I install the nVidia drivers from Ubuntu not from nVidia.
Ubuntu now has several choices. 

       # You may need headers - meta package for 12.10 version:
sudo apt-get install linux-headers-generic
# only reason to purge is there are several versions, if you know you have different nVidia use that:
#To see available  versions:
dpkg -l | grep -i nvidia*
apt-cache search nvidia-sett*
# Houseclean out all old versions to avoid issues
sudo apt-get remove --purge < nvidiadriverpackagename>
 # [ using the correct names] for each driver, before running: 
sudo apt-get purge nvidia*
# I used nvidia-current-updates & nvidia-settings-updates, example below is just nvidia-current, use version you prefer
sudo apt-get install nvidia-current
sudo apt-get install nvidia-settings
sudo dpkg-reconfigure nvidia-current
sudo nvidia-xconfig
sudo reboot
May want nvidia-current, nvidia-current-updates or nvidia-current-experimental-XXX for most recent testing version.
apt-cache search nvidia-sett*

i am gonna tray a fresh instalation with UbuntuStudio 12.10.
so what i would do is like,
1. Install from DVD
2. Apply online updates if any
3. Remove Jockey
4. sudo apt-get remove --purge < nvidiadriverpackagename> to remove all/any available nvidia* drivers
5. get the linux headers (lowlatency)
6. sudo apt-get install nvidia-current
7. sudo apt-get install nvidia-settings
8. sudo dpkg-reconfigure nvidia-current
9. sudo nvidia-xconfig
10.sudo reboot

I might start the installation by 9PM IST. Before that if anything i should know, please let me know.

Thanks a lot for the detials and i really appreciate the support.

Wishing good luck to myself and hoping to come bcak with a good news :)

---

### Post by abhayadevs on 2013-02-15
sadly it failed ! :mad:

Now the display is at 720x400 !

Is there anything i need to do with the /etc/modprobe.d/nvidia* ?

i have attached the typescipt file... please help me...

thanks,
abhayadev s

---

### Post by abhayadevs on 2013-02-15
> **abhayadevs said:**
> sadly it failed ! :mad:

Now the display is at 720x400 !

Is there anything i need to do with the /etc/modprobe.d/nvidia* ?

i have attached the typescipt file... please help me...

thanks,
abhayadev s

cananybody tell me at what conditions it tells me that "you do not appear to be using the NVIDIA X driver.. Please edit your X configuration file...."

i dont have any other driver other than the nvidia-current and the xconfig is updated also....

---

### Post by abhayadevs on 2013-02-26
> **abhayadevs said:**
> cananybody tell me at what conditions it tells me that "you do not appear to be using the NVIDIA X driver.. Please edit your X configuration file...."

i dont have any other driver other than the nvidia-current and the xconfig is updated also....


Its fixed.. the issue was that the on-board gfx was enabled and the ubuntu was initialising it and was not caring of the gfx card. once i disabled the onboard gfx (intel) the nvidia is now online...

thanks for all you support...

---

### Post by tlotr on 2013-07-11
Hi All,

I am having this problem with the fonts looking all fuzzy. I installed Ubuntu 12.04 LTS yesterday and updated it with all the updates there was. After updating I installed the n-Vidia drivers from the 4 options that I received and I selected the (Recommended) one. After the drivers got downloaded and installed. I rebooted the system once. After the system got started the fonts all became fuzzy before that it was all sharp and clear. Also when I check system settings and click on Details and click the last option "Graphics" it shows that the card is unknown and doesn't shows that its n-Vidia. 

Please help. 

Did I do something wrong.

---

### Post by tlotr on 2013-07-11
Hi All,

This is resolved, I uninstalled the nvidia drivers which I had installed through the Additional drivers and now everthing is back to normal. The fonts are the way it was before.

---

