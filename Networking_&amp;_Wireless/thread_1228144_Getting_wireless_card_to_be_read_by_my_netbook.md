---
title: "Getting wireless card to be read by my netbook"
date: 2009-07-31
forum: Networking &amp; Wireless
---

### Post by buckleyboy on 2009-07-31
Hello, 
I am new to ubuntu and am having some difficulties with getting my new netbook to read my wireless and wired internet cards.  I have done several steps to try and get it up and running.  I don't have a wifi usb that is supported by ububuntu so i have to do this without access to internet through my netbook.  I was able to somehow get the internet to work for about an hour and when i went to restart it to finalize the downloads that it found i went back to the same problem. so any help would be much appreciated.  I would like to have this netbook for school by the 17th of August so i can actually use the internet so i hopping to get something accoomplished by then.
 
Here are the specs of my Netbook:
 
Model and Brand: ASUS 1005HA
Wireless Brand :  Atheros Communications Inc. AR9285 Wireless network Adapter (PCI-Express) (rev 01)
Interface: lo Local Loopback; lo no wireless extensions. pan0 No wireless extensions
Wireless Module: There appears to be no wireless module that i can tell i get nothing when imputting the code lsmod | grep "wlan_mdoule_name"
Kernal Messages: again same as before there appears to be no kernal messages
Network Configuration: Network Unclaimed and Network Dissabled 
Scan for Networks: lo interface doesn't support scanning , pan0 interface doesn't support scanning.
Ubuntu Version: 9.04
Kernel / Architecture: 2.6.28-14 generic i686
Restarting the Network: code came back as [OK]
 
 
I hope someone can help much appreciated

---

### Post by t0mppa on 2009-07-31
Check [this]("http://ubuntuforums.org/showthread.php?t=894177") thread for info. Note that the first few posts are one year old, so they likely have old info, but the later ones are up to date. And pytheas is helping a lot of others with their problems too, so you can just reply there, if you still can't get it to work after trying the things suggested there.

---

### Post by buckleyboy on 2009-08-02
Thanks for the feedback, however, neither one of those suggestions helped me i have been trying to get that to work for 2 days and i am not getting any further with my issue.

---

### Post by Crafty Kisses on 2009-08-02
Try loading the ath9k module, you can do this by running as root:
```
modprobe ath9k
```
You also need to read this. [http://wireless.kernel.org/en/users/Drivers/ath9k#ath9k](http://wireless.kernel.org/en/users/Drivers/ath9k#ath9k).

---

### Post by buckleyboy on 2009-08-03
This is what i get when doning modprobe ath9k:
 
james@james-laptop:~$ modprobe ath9k 
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release. 
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release. 
WARNING: Error inserting cfg80211 (/lib/modules/2.6.28-14-generic/kernel/net/wireless/cfg80211.ko): Operation not permitted 
WARNING: Error inserting mac80211 (/lib/modules/2.6.28-14-generic/kernel/net/mac80211/mac80211.ko): Operation not permitted 
FATAL: Error inserting ath9k (/lib/modules/2.6.28-14-generic/kernel/drivers/net/wireless/ath9k/ath9k.ko): Operation not permitted
 
 
So i am not sure what to do at this point.

---

### Post by Crafty Kisses on 2009-08-03
Run it as root, so run:
```
sudo modprobe ath9k
```

---

### Post by careyrn on 2009-08-03
I'm having the same problem on my new netbook.  Same model, same specs.  I've looked EVERYWHERE and tried so many things but i just can't get any sort of internet connection.  I click on the wirless signal bars and it says "No Network devices available."

I tried all these suggestions getting the same error messages.

When I typed "sudo modprobe ath9k"
it gave me

WARNING:  All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.

---

### Post by buckleyboy on 2009-08-04
I also get the same warning when i run sudo modprobe ath9k

---

### Post by Crafty Kisses on 2009-08-04
Login as root by running the following:
```
sudo -i
```
Once you're root, try running:
```
cat /etc/modprobe.d/ndiswrapper >> /etc/modprobe.d/ndiswrapper.conf && rm /etc/modprobe.d/ndiswrapper
cat /etc/modprobe.d/blacklist >> /etc/modprobe.d/blacklist.conf && rm /etc/modprobe.d/blacklist
```
Close the terminal out so you're not logged in as root anymore, this should do the trick.

---

### Post by brhokla on 2009-08-04
will this work with no internet access?

---

### Post by MadHatter21 on 2009-08-04
Hey i had the same problem with my atheros card. Go to (Rplace the xx with tt) hxxp://linuxwireless.org/en/users/Download and download the compat-wireless-2.6.30 and run 

make
sudo make install
sudo make unload

see how that works and get back to me.

---

### Post by buckleyboy on 2009-08-05
so when i downloaded the driver to my flash drive from my other laptop how should i go about putting onto my netbook?

---

### Post by MadHatter21 on 2009-08-05
Yeah just put it on a cd, usb or any other means.

---

### Post by buckleyboy on 2009-08-05
when i did that and put it into my netbook and tried to run those codes u stated to run it wasn't finding any thing to make or install or unload so i don't know if i did something wrong or what?

---

### Post by Crafty Kisses on 2009-08-05
Alright, I'll give you step by step instructions, first in a Terminal run:
```
wget http://www.orbit-lab.org/kernel/compat-wireless-2.6-stable/v2.6.30/compat-wireless-2.6.30.tar.bz2
```
Once you have done that you need to untar the archive, so run the following:
```
tar xvjf compat-wireless-2.6-stable/v2.6.30/compat-wireless-2.6.30.tar.bz2
```
Once you have done that, make sure you have build-essential installed, that's to actually build and compile the driver, so run as root:
```
apt-get install build-essential
```
Once you have that package, navigate to the driver directory you recently untarred by running:
```
cd /home/username/Desktop/compat-wireless-2.6-stable/v2.6.30/compat-wireless-2.6.30
```
That of course assuming you saved it to your desktop and replace username with your actual username, remember it's case sensitive, now you can run:
```
make
sudo make install
```
If you have a problem with the driver, you can always run:
```
make unload
```
As stated in this thread, if you're having loading the ath9k modules, run:
```
cat /etc/modprobe.d/ndiswrapper >> /etc/modprobe.d/ndiswrapper.conf && rm /etc/modprobe.d/ndiswrapper
cat /etc/modprobe.d/blacklist >> /etc/modprobe.d/blacklist.conf && rm /etc/modprobe.d/blacklist
```
That should get you up and running.

---

### Post by buckleyboy on 2009-08-05
can all of this be done without the internet because my netbook's wired connection doesn't work either?

---

### Post by MadHatter21 on 2009-08-05
No, 
Do you have a ethernet rj-45 cable that you can use for the time being? Mainly the downloading the file (wget) and the apt-get will require internet. Did you unzip the file that i told you to download and then go into the directory before you ran the commands i told you?

---

### Post by buckleyboy on 2009-08-05
i do have an ethernet cable however like i stated my wired connection doesn't work on my net book so no ican't download anything on my net book via the internet.

---

### Post by MadHatter21 on 2009-08-05
> **MadHatter21 said:**
> No, 
 Did you unzip the file that i told you to download and then go into the directory before you ran the commands i told you?

Try opening up the ziped file and copying it to your desktop. I.E. for me it was compat-wireless-2.6.30 so i did

cd /Desktop/Compat...........
then i ran the command
make
sudo make install
sudo make unload

Let Me know

---

### Post by buckleyboy on 2009-08-05
ok so for me i had downloaded the file to my flash drive and unzipped the file on my net book on my flash drive so now do i copy it to netbook?

---

### Post by MadHatter21 on 2009-08-05
yes copy the unziped directory to the netbook. Then run the commands from the last post.

Update me

MadHatter21

---

### Post by buckleyboy on 2009-08-05
ok i have to appologize because i just maybe that unlucky but i still am getting the same error code that i have been getting and that is that there isn't a make file found and i copy and unzipped the folder and everything so i don't know

---

### Post by MadHatter21 on 2009-08-05
Im not entirely positive but i think it might be because of netbook remix. I have desktop version running on my netbook and it works fine. It might be something over my head then if its not supported for net remix.

---

### Post by buckleyboy on 2009-08-05
do you think that maybe i should try installing the desktop version onto my netbook instead or not?

---

### Post by Crafty Kisses on 2009-08-05
First, what are the results of this command?
```
uname -r
```
You might be using the array kernel. Secondly, you need the build-essential package if you want to build anything from source, from my knowledge if you don't have an Internet connection you can still obtain certain packages. So in order for this **symlink** to actually work, you need to run:
```
sudo mount -o loop cd.iso /mnt/image
sudo rm /cdrom
sudo ln -s /mnt/image /cdrom
sudo apt-cdrom -**m** add
sudo apt-cdrom add
```
Then once you have ran those commands in order, you need to run:
```
sudo aptitude update
sudo aptitude install build-essential
```
Now I'm guessing since you're on a netbook, you don't have a CD rom drive. So you could grab one of the versions of build-essential from **[here.]("http://ftp.debian.org/debian/pool/main/b/build-essential/")** Then from there mount your USB drive, if you're not sure how to do that, it's simple just run:
```
mount /dev/sdb1
```
The sdb part will vary depending on what type of drive you're using. The only issue I see with this is, I'm almost certain this will not come with all the dependencies, so this is a little tricky situation, I'm not sure what you could do here. So I've taken the liberty of hunting down the dependencies you need to get this to work. So here they are:
[LIST]
[B][*]binutils_2.18.1~cvs20080103-0ubuntu1_i386.deb
[*]perl-modules_5.8.8-12_all.deb
[*]build-essential_11.3ubuntu1_i386.deb
[*]bzip2_1.0.4-2ubuntu4_i386.deb
[*]cpio_2.9-6ubuntu1_i386.deb
[*]cpp_4.2.3-1ubuntu3_i386.deb
[*]cpp-4.2_4.2.3-2ubuntu7_i386.deb
[*]dpkg-dev_1.14.16.6ubuntu3_all.deb
[*]g++_4.2.3-1ubuntu3_i386.deb
[*]g++-4.2_4.2.3-2ubuntu7_i386.deb
[*]gcc-4.2_4.2.3-2ubuntu7_i386.deb
[*]gcc-4.2-base_4.2.3-2ubuntu7_i386.deb
[*]libbz2-1.0_1.0.4-2ubuntu4_i386.deb
[*]libc6_2.7-10ubuntu3_i386.deb
[*]libc6-dev_2.7-10ubuntu3_i386.deb
[*]libgcc1_4.2.3-2ubuntu7_i386.deb
[*]libgomp1_4.2.3-2ubuntu7_i386.deb
[*]libstdc++6-4.2-dev_4.2.3-2ubuntu7_i386.deb
[*]libtimedate-perl_1.1600-9_all.deb
[*]linux-libc-dev_2.6.24-19.36_i386.deb
[*]lzma_4.43-12ubuntu1_i386.deb
[*]make_3.81-3build1_i386.deb
[*]patch_2.5.9-4_i386.deb
[/LIST]
[/B]You need to install all those packages one by one. Then once you have all those packages installed, make sure you have unintstalled or at least uninstall what you have attempted to compile by going into the driver directory and running:
```
sudo make unload
```
Once you have done that, reboot by running the following:
```
sudo shutdown -r now
```
Then try the driver compile/install again.

---

### Post by buckleyboy on 2009-08-05
ok so i am currently running on a 2.6.28-14 generic kernal so i don't know if this is supposed to work with certain kernals but the codes are not working that you gave me.  Should i try to just load the desktop version of linux onto my netbook and see if that changes things or is it going to be the same issue?

---

### Post by Keith Fox on 2009-11-28
@ Crafty Kisses:  your commands in this forum post have helped me with a few problems, errors in terminal regarding ndiswrapper and sudo errors, and also "Hardware device could not be recognised" error in Network-settings.  But I am still having one major problem.  I have a PCI network adapter that seems to override my USB adapters in any case.  I tried shutting down and removing the PCI adapter and trying that and still can't get my USB network devices to work.  They are gettings recognised in network-settings, but the Link light on my WUSB54G adapter does not light up or blink, no network activity is going on unless I only use a PCI adapter.  This device says it comes with driver already installed in Linux and is working, but some reason my Wicd doesn't connect with it to any network.  I also use RutilIT and Wifi-Radar.  still nothing from USB network adapters. thanks for your help though with those commanding errors.:)

---

