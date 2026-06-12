---
title: "Ati Radeon Driver wohs"
date: 2010-08-18
forum: Multimedia Software
---

### Post by luckymoonboy1 on 2010-08-18
I made a terrible error, I think. I have a PC with an Ati Radeon 9550. i attempted to install the Ati Radeon Proprietary driver under 10.04. it failed of course and now my graphics are a little lacking. Before my attempt I was running Compiz Desktop effects and games quite well. However after my epic failure I lost all of my desktop effects. My applications that require decent graphics to work no longer do(Including Blender and Quadropassel). I then retreated to the library to try and solve my conundrum and discovered that 10.04 does not support the proprietary driver(or the driver does not support 10.04). now i need to discover how to repair the driver it was running on originally or find a way to download(on a separate computer) and install the open-source Ati driver that i have read about( here: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) ) I was more confused afterwards than before I read it.

I would be eternally thankful to anyone who was able to shine little light on what to do.

---

### Post by KROwen1959 on 2010-08-18
I too had the same identical problem. Before I explain what I did I need to tell you I split my hard drive. I still have windows because there are some things I still can't do with Linux. I too am a newbie. Now, with that being said and can be corrected, I cleared out Linux and reinstalled it from live disk. When it completed, I had to restart the system. After I restarted, I did an update manager. That took about 30-40 min. when all of that was installed, I Restarted my system again. At that point I did a Drivers update and that solved my issues. I anyone feels different feel free to correct me so this person doesn't make a bigger mistake.

---

### Post by Trinity33 on 2010-08-18
> **luckymoonboy1 said:**
> I made a terrible error, I think. I have a PC with an Ati Radeon 9550. i attempted to install the Ati Radeon Proprietary driver under 10.04. it failed of course and now my graphics are a little lacking. Before my attempt I was running Compiz Desktop effects and games quite well. However after my epic failure I lost all of my desktop effects. My applications that require decent graphics to work no longer do(Including Blender and Quadropassel). I then retreated to the library to try and solve my conundrum and discovered that 10.04 does not support the proprietary driver(or the driver does not support 10.04). now i need to discover how to repair the driver it was running on originally or find a way to download(on a separate computer) and install the open-source Ati driver that i have read about( here: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) ) I was more confused afterwards than before I read it.

I would be eternally thankful to anyone who was able to shine little light on what to do.


i have ati hd4850 in my laptop and dont have any problems maybe just one that when i play HD clips the cpu is used in about 30% and it is q9000.

my advice to you install catalyst catalyst do support the new xorg in ubuntu very well i tried in the beginning the open source driver and it didnt work. they dotn have proper support for 3d so i say download catalyst install it and thats all u dont need to do anything else thats how i did and its still working :)

---

### Post by tjones00 on 2010-08-19
The open source radeon driver is installed by default with ubuntu 10.04 and even built into the kernel. It's simply called radeon.

To check if you're running it open a terminal and type.

lsmod

If you see radeon in the output the driver is active.

To purge your system of the failed ati catalyst try following the uninstall instructions on this page.

[https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD)

> Previous or current installations of ATI's  proprietary Catalyst/fglrx drivers are known to interfere with the  installation of the open-source drivers. If you have installed proprietary drivers downloaded from ATI/AMD's website: ```
sudo sh /usr/share/ati/fglrx-uninstall.sh
```> If you've installed the proprietary drivers through Ubuntu (i.e. Synaptic or Jockey/Restricted Hardware Drivers): ```
sudo apt-get purge xorg-driver-fglrx fglrx-amdcccle fglrx-kernel-source xorg-driver-fglrx-dev
```After doing the above open a terminal and delete any xorg.conf that might be present. Ubuntu 10.04 and the radeon driver do not need one.

```
sudo rm /etc/X11/xorg.conf
```Then reinstall the radeon driver just for good measure.
```
sudo apt-get --reinstall install xserver-xorg-core xserver-xorg-video-all
```One last step make sure that the ati catalyst driver did not blacklist the radeon driver.

Open a terminal and check /etc/modprobe.d/blacklist.conf
```

sudo nano /etc/modprobe.d/blacklist.conf
```If you see a line stating

blacklist radeon

Delete it then press ctrl-o to save the file and ctrl-x to exit.


Reboot your computer everything should magically setup to use the radeon driver.
To check if the radeon driver is active open a terminal and type lsmod again.

---

### Post by luckymoonboy1 on 2010-08-19
> Then reinstall the radeon driver just for good measure.
```
sudo apt-get --reinstall install xserver-xorg-core xserver-xorg-video-all
```


Does this require Internet access or can the disk be used?

---

### Post by tjones00 on 2010-08-19
It should check both the local CD/DVD and online if you installed from a CD/DVD and have it the drive.

Those packages are part of the standard install CD/DVD.

If you have been online since the system was installed and have done any updating/upgrading it'd be best to use the online repo.

---

### Post by luckymoonboy1 on 2010-08-20
YES!! THANK YOU, tjones00!! I had preformed the un-install of the failed catalyst earlier however there had been no change. The re-installation of the radeon driver fixed it perfectly!!! I am forever grateful to you and your amazingly resourceful knowledge, may they build statues in your honor. And may the Force be with you. ):P

---

