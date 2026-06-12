---
title: "Need help right of the bat."
date: 2013-08-27
forum: Networking &amp; Wireless
---

### Post by cory3 on 2013-08-27
Hi there,

So I am brand new to linux, I just installed it as a second OS on my MBP with rEFIt. The install went fine (or at least I think it did), and I was then promped to restart. Then the computer restarted, and I was met with a purple background with a bunch of flashing pixels across the screen. After that, it booted up and I was shown the desktop, and I opened Additional Drivers to see what was needed to be installed. At the top of the list, I saw "Broadcom STA wireless driver." Which I assumed was to add WiFi capability.

I was quickly met with an error saying: 

"Sorry, installation of this driver failed.

Please have a look at the log file for details: /var/log/jockey.log"

I've tried googling my problem, but everything seemed to either not apply to my issue or be too hard for me to understand. Without the driver there is no option to connect to a wireless network, which is a huge inconvenience seeing that I am on a laptop. 

I am a complete newbie to Ubuntu, so I had no idea where to look for this file. Any help pointing me in the right direction would be *greatly* appreciated.


Thanks,
-Cory

---

### Post by lah7 on 2013-08-27
**Hello, welcome to the world of Ubuntu! **Wireless networking in general can be a pain sometimes. The file **jockey.log** will contain useful technical information for diagnosing what went wrong.

_**To get this file:**_ Open the file manager and press **CTRL+L** which brings up the address bar. Type */var/log* and press ENTER. This will take you to the folder where it's located. Scroll down or begin typing 'jockey.log' to find it within the folder.

Someone knowledgeable with installation issues will be able to read this log and be able to understand exactly what went wrong. Since you're not yet connected, you may wish to transfer this log to another PC with a USB drive and share it in this thread. If this isn't an option for you, we'll be stuck for suggestions.

Please could you also help provide us with some specs of your laptop? It'll help us identify other possible causes.

---

### Post by wildmanne39 on 2013-08-27
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz) in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by wildmanne39 on 2013-08-27
*Thread moved to **Networking & Wireless**.*

---

### Post by cory3 on 2013-08-27
Alrighty, so I just uploaded the file. It's compressed to a .zip, since it was over the upload size. The file seems a bit big, so if anything needs narrowing down I'd be happy to assist.

Some specs on the computer itself:

MacBook Pro (mid-2010)
Intel Core 2 Duo 2.4GHz processor
4GB of RAM
NVIDIA GeForce 320M GPU

Let me know if you need anything else!

-Cory

---

### Post by Quackers on 2013-08-27
You may need to load the firmware for your wifi device (I did on a MBP 10,1). Have a look in your MBP's specs and see what your wifi device is.

---

### Post by wildmanne39 on 2013-08-27
Please do what I ask in post 3 that way we can see exactly the condition of your wireless.
Thanks

---

### Post by cory3 on 2013-08-27
Here you go, the 'wireless-info' file

---

### Post by wildmanne39 on 2013-08-27
Let's try this:
```
sudo apt-get install --reinstall linux-headers-generic linux-headers-$(uname -r) build-essential dkms
```
```
sudo apt-get install --reinstall bcmwl-kernel-source
```

```
sudo modprobe wl
```
watch for errors.
Thanks

---

### Post by cory3 on 2013-08-27
After entering the first line of code, everything was installing and then an error came up:

"Sorry, a problem occurred whole installing software.

Package: bcmwl-kernel-source"

I see that the second line appears to reinstall this, so should I go through with the other lines?

-Cory

---

### Post by wildmanne39 on 2013-08-27
Please post the errors here.
Thanks

---

