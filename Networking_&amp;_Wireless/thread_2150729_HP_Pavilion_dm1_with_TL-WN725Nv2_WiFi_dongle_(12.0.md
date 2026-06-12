---
title: "HP Pavilion dm1 with TL-WN725Nv2 WiFi dongle (12.04)"
date: 2013-06-02
forum: Networking &amp; Wireless
---

### Post by dimvoly on 2013-06-02
Posting this in the hope that someone else doesn't waste as much time as I had. Posting this in these forums since they've been quite helpful to me in the past.

[B]
Specs[/B]
[LIST]
[*]HP Pavilion dm1 netbook
[*]Ubuntu 12.04
[*][FONT=courier new]uname -r[/FONT]
[LIST]
[*]3.5.0-31-generic
[/LIST]

[*]TP-LINK ([http://wikidevi.com/wiki/TP-LINK_TL-WN725N_v2](http://wikidevi.com/wiki/TP-LINK_TL-WN725N_v2))
[LIST]
[*]Driver 8188eu
[*]It is a very small dongle but you get quite a good signal. Perfect for laptops, just leave it plugged in.
[/LIST]

[*][FONT=courier new]lsusb[/FONT]
[LIST]
[*]Bus 002 Device 002: ID 0bda:8179 Realtek Semiconductor Corp.
[/LIST]
[/LIST]

**Why a dongle**
The drivers for the on-board card did not work:
[LIST]
[*]BCM proprietary driver (or even the compiler open source version of the same thing): boots everyone else off of the network. This was hilarious but only for me. For some reason it just interferes so that no one else but me can access the wifi. Also on my enterprise work network it did not log on to the network at all until about 6pm for some reason. Perhaps someone else was interfering. This current set up not tested at work yet.
[*]Some open source driver: low signal strength and terrible speeds. When I moved to my room, the signal was lost completely.
[*]Tried some other drives and nothing worked.
[*]Also, stupid HP put a white list on the netbook so only certain cards are accepted or it won't boot at all! That is, you can't swap out the on board wifi card, even though it is removable.
[/LIST]


**General Instructions for Dongle.**
In the end, I used the instructions found here: [http://burogu.makotoworkshop.org/index.php?post/2013/04/27/TL-WN725N-v2](http://burogu.makotoworkshop.org/index.php?post/2013/04/27/TL-WN725N-v2) (use Google Translate).

[s]Downloading the driver was a pain, since for some reason GitHub does not let you download the folder that the driver is located in. So I ended up downloading the whole 161MB zip file that contains all of the guy's works.[/s] Apparently it is available from the above linked site so just follow those instructions. I originally used a different site, which was a Chinese site and pointed me to GitHub.

After following the above instructions I had to blacklist all the older drivers that I've tried, since they interfered.

```
nano /etc/modprobe.d/blacklist.conf
```

I've added these lines just to be sure:
```
# blacklist the wifi drivers all to hell
# dimvoly 29/5/13
blacklist b43
blacklist wl
blacklist b43legacy
blacklist bcma

```



[B]
Useful Commands Reference
[/B]People normally just jump in with commands when giving answers and when I first encountered them I didn't even know they were meant to go into a terminal, I thought they were for the web browser or file browser.
[LIST]
[*][FONT=courier new]Ctrl+Alt+T[/FONT] - open up terminal
[*][FONT=courier new]sudo -i[/FONT] - run as root user. Use [FONT=courier new]logout[/FONT] to log back out.
[*][FONT=courier new]lshw -C network[/FONT] - shows hardware network interfaces, states driver
[*][FONT=courier new]uname -r[/FONT] - shows the kernel version (this has to be compatible with the stuff you're trying to compile)
[*][FONT=courier new]nano /etc/modprobe.d/blacklist.conf[/FONT] - blacklisted modules, so if you have a bad driver, just blacklist it so it doesn't get in the way
[*][FONT=courier new]nano /etc/modules[/FONT] - I haven't used this but I think it is for loading the module on start up.
[*][FONT=courier new]modprobe -r *MODULE*[/FONT] - unload the module
[*][FONT=courier new]modprobe *MODULE*[/FONT] - load the module
[*][FONT=courier new]iwconfig[/FONT] - shows IP, signal strength. I had 2 wireless interfaces in the end so it showed both of them
[*][FONT=courier new]lsmod | grep brc[/FONT] - shows modules with brc in name (I guess if you're looking for a module)
[*][FONT=courier new]lspci -n | grep 14e4[/FONT] - can't remember what this does.
[/LIST]



This was written quickly so post here if you have troubles. Hopefully I'll save someone somewhere some time.

Do I recommend this dongle? Yes, since the driver works with the kernel. However, I had a hard time finding the driver since it was listed on French/Chinese sites. Google translate really saved me here.

---

### Post by praseodym on 2013-06-02
[http://forum.ubuntuusers.de/topic/problem-mit-usb-adapter-tp-link-tl-wn725n-v2/#post-5536902](http://forum.ubuntuusers.de/topic/problem-mit-usb-adapter-tp-link-tl-wn725n-v2/#post-5536902)

Here are the terminal commands for the installation via git:
```

sudo apt-get install --reinstall build-essential git 
git clone git://github.com/liwei/rpi-rtl8188eu.git
cd ~/rpi-rtl8188eu
make
sudo make install
sudo depmod -a
sudo update-initramfs -u 
sudo modprobe -v 8188eu
```

---

### Post by nathanwilliams2 on 2013-11-26
root@nathan-System-Product-Name:~# cd ~/rpi-rtl8188eu
-bash: cd: /root/rpi-rtl8188eu: No such file or directory
root@nathan-System-Product-Name:~# git clone git://github.com/liwei/rpi-rtl8188eu.git
Cloning into 'rpi-rtl8188eu'...
remote: Counting objects: 278, done.
remote: Compressing objects: 100% (199/199), done.
remote: Total 278 (delta 75), reused 275 (delta 75)
Receiving objects: 100% (278/278), 1.17 MiB | 367 KiB/s, done.
Resolving deltas: 100% (75/75), done.
root@nathan-System-Product-Name:~# cd ~/rpi-rtl8188eu
root@nathan-System-Product-Name:~/rpi-rtl8188eu# make
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/3.8.0-33-generic/build M=/root/rpi-rtl8188eu  modules
make[1]: Entering directory `/usr/src/linux-headers-3.8.0-33-generic'
  CC [M]  /root/rpi-rtl8188eu/core/rtw_cmd.o
In file included from /root/rpi-rtl8188eu/core/rtw_cmd.c:23:0:
/root/rpi-rtl8188eu/include/osdep_service.h: In function ‘thread_enter’:
/root/rpi-rtl8188eu/include/osdep_service.h:1397:2: error: implicit declaration of function ‘daemonize’ [-Werror=implicit-function-declaration]
cc1: some warnings being treated as errors
make[2]: *** [/root/rpi-rtl8188eu/core/rtw_cmd.o] Error 1
make[1]: *** [_module_/root/rpi-rtl8188eu] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.8.0-33-generic'
make: *** [modules] Error 2
root@nathan-System-Product-Name:~/rpi-rtl8188eu# sudo make install
install -p -m 644 8188eu.ko  /lib/modules/3.8.0-33-generic/kernel/drivers/net/wireless/
install: cannot stat `8188eu.ko': No such file or directory
make: *** [install] Error 1

Any ideas as to what I might be doing wrong? Complete noob here. Thought it was going so well until that point.

Spucs:
12.04 LTS
3.9GbRAM
AMD Athlon(tm) II X4 640 Processor × 4 
487.9gb
Doesn't recognise my graphics cards (Rdn 5350, ancient technology) for some reason, have installed the ATI/AMD Propietary FGLRX graphics driver. But that's a different matter.

ANy help greatly appreciated.

---

### Post by chili555 on 2013-11-26
> # git clone git://github.com/liwei/rpi-rtl8188eu.gitHowever, on the page you used, it clearly says:> This repo has been deprecated, please goto [https://github.com/lwfinger/rtl8188eu](https://github.com/lwfinger/rtl8188eu) for future updates.Moreover, you are running as root: #. There is no need to do so. I suggest you open a new terminal as an ordinary user $ and do:```
git clone git://github.com/lwfinger/rtl8188eu.git
cd rtl8188eu
make
sudo make install
sudo modprobe rtl8188eu
``` Post back if you get stuck, there are errors, warnings, smoke, sparks, etc.

---

### Post by harmkuiper on 2014-08-27
Thanks Chili555!  I noticed i had SUPER poor link quality (2/100) for my TP WN725N. I decided to browse around and found this thread. I used the instructions in the post above this one to update the rtl8188eu driver.  After the sudo make install i changed tactics and did the following: sudo depmod -a sudo update-initramfs -u  sudo rmmod r8188eu sudo modprobe -v 8188eu  Now running with 21/100 link quality!  I suggest installing wavemon to monitor link connection

---

