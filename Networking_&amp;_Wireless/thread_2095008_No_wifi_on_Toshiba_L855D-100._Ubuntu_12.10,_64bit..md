---
title: "No wifi on Toshiba L855D-100. Ubuntu 12.10, 64bit."
date: 2012-12-15
forum: Networking &amp; Wireless
---

### Post by Kjeks on 2012-12-15
Hi
I have recently installed Ubuntu 12.10 on my Toshiba Satellite L855D-100 laptop.
The wireless card is not recognized, and I have no idea where to start to get it working.
I have also tried to install Linux Mint, but have the same problem there.

Is wifi not supported on the L855D-100?

---

### Post by chili555 on 2012-12-15
Let's figure out what wireless card you have first. Please open a terminal and run and post:```
lspci -nn | grep 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by Kjeks on 2012-12-15
Thanks for the reply, chili555.

The output is as follows:
```
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8723]
```

---

### Post by chili555 on 2012-12-15
This is a relatively new device that requires that you compile a driver. Please see here: [http://ubuntuforums.org/showpost.php?p=12164850&postcount=6](http://ubuntuforums.org/showpost.php?p=12164850&postcount=6)

Please post back if you get stuck.

---

### Post by Kjeks on 2012-12-15
Thanks for the info!
I'll try that when I get access to a wired network (I live in a boat with only wireless network).

Have a good day :KS

---

### Post by Kjeks on 2012-12-16
Hi again.
Today I took my laptop to work, where we have wired LAN. It appears the wired network card isn't recognized either! It worked in Windows, but not in Ubuntu or Linux Mint. eth0 = no device found.

Is there any other way I can install the wifi driver without Internet access? I have a USB stick I can use to transfer files from Windows to Ubuntu...

---

### Post by chili555 on 2012-12-16
If you can download the packages to your Windows partition and then transfer them on a USB key, CD or similar, then we can get the job done. First, let's get build-essential: [http://packages.ubuntu.com/precise/build-essential](http://packages.ubuntu.com/precise/build-essential)

Download the package as appropriate to your architecture; either i386 (32-bit) or amd64 (64-bit). Find out which you have with this command:

```
arch
```

32-bit will report as i686 and 64-bit as x86_64.

The red dots indicate that the package build-essential depends on dpkg-dev, g++, gcc, libc6-dev or libc-dev and make. Download those packages also.

Now for linux-headers: [http://packages.ubuntu.com/search?ke...se&section=all](http://packages.ubuntu.com/search?ke...se&section=all) 
This package depends on the headers matching your running kernel. That means that, in addition to the 'generic' package, you'll also need linux-headers for your kernel. Find out your running kernel version with:```
uname -r
```For example, if the uname -r command shows that you are running 3.5.0-19-generic, you will need linux-headers-3.5.0-19-generic.

Once you have all these on a USB key or CD, drag and drop these on to the desktop of your Ubuntu installation. Open a terminal and do:
```
cd Desktop
sudo dpkg -i *.deb
```

The wildcard * means to install every .deb package on your desktop. We hope there are no missing dependencies, but if so, go here, download and install them, too: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Then go back to the link I gave you and proceed. Obviously, post back if there is any question or you get stuck.

---

### Post by Kjeks on 2012-12-17
Yes! It worked!
It was a bit of a hassle to copy all the *.deb-files over, because of a lot of unexpected dependencies. At one point I even had to force a package installation (g++), because the -dev-package was depending on the main package and the other way around. But eventually it worked.
The driver compiled and installed, and I'm now writing this on a wifi-connection :-)

Now back to PHP programming!

Thank you very much for your help, chili! :guitar:

---

### Post by chili555 on 2012-12-17
Awesome! Now that you are connected, I suggest you do:```
sudo apt-get update && sudo apt-get -y upgrade
```You will probably get a later kernel version. When you reboot into the later kernel, recompile the driver:```
cd Desktop/Driver_file_wherever
sudo su
make clean
make
make install
modprobe rtl8723e
exit
```Repeat each time a newer kernel is installed or until the driver is included in the mainline kernel.

I wish there was an easier way but I'm glad you persevered!

---

### Post by Kjeks on 2012-12-18
Hi again.
I did as you said in the last post, and it worked OK.

But then today Ubuntu found some new updates (including kernel), and I installed them and rebooted.
Now the wifi is broken again!
I tried to make clean; make; make install and modprobe, as I've done before, but this time modprobe fails..

This is what happens:
```
root@kjeks-SATELLITE-L855D:~/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012# modprobe rtl8723e
FATAL: Error inserting rtl8723e (/lib/modules/3.5.0-19-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723e/rtl8723e.ko): Invalid argument
```

Any idea on what to do?

---

### Post by chili555 on 2012-12-18
Please try again and show us the resultant output for each command. I wonder if there is an error.

---

### Post by Kjeks on 2012-12-18
***NOTE: ***I think I know what's wrong (but not how to fix it):

After the kernel upgrade, the module would not compile because of missing "*build*" in /lib/modules/3.5.0-19-generic/. The "*build*"-file did however exist in /lib/modules/3.5.0-17-generic/.
I therefore made a symlink in the *19-generic directory pointing to the build in the *17-generic directory.
Then it compiled.

But modprobe fails.

Here's a link to the complete output log: [https://dl.dropbox.com/u/457972/error_log.txt](https://dl.dropbox.com/u/457972/error_log.txt)

---

### Post by chili555 on 2012-12-18
Because of the symlink, you effectively built the module for 3.5.0-17. Modprobe looks for the module in the currently running kernel, 3.5.0-19. There is none. The symlink is an error. This:>  missing "build" in /lib/modules/3.5.0-19-generic/. ...usually means you don't have linux-headers installed or at least installed correctly. We may have a mess to fix. Please try:```
sudo apt-get install --reinstall linux-headers-generic
sudo apt-get install --reinstall linux-headers-`uname -r`
```Those backticks are on the left side of my US keyboard on the same key with ~.

Then compile again, preceded by make clean.

---

