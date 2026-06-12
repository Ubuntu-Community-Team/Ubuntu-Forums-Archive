---
title: "Help me install patched driver for AWUS036H, Ubuntu 10.10"
date: 2011-03-08
forum: Networking &amp; Wireless
---

### Post by Torp3x on 2011-03-08
I have scoured the web for every bit of information I can find regarding installing the ieee80211 patched driver for the realtek rtl8187, to use an Alfa AWUS036H for packet injection. Error after error after error, I have had no success, and all I can find is other people with the same setup having the same problems.

Assume I have installed Ubuntu 10.10 straight out the box, so no updates have yet been made. Is someone in the know willing to post some step by steps on how to download, install and patch the necessary driver and install necessary software, including precise info on how to blacklist or remove mac80211 version rtl8187.ko in order to replace it with the patched ieee80211 version?

I know there's a tutorial on here somewhere for installing rtl8187 in an older version of Ubuntu, and in that thread, the people with Ubuntu 10.10 all seem to be having the same problems.

---

### Post by MasonX on 2011-07-10
I would really appreciate it if someone would step up and be the only Person in cyberspace with a working copy of instructions on   How-to install and patch drivers for the Alfa awus036h 1000mw usb Wireless Network Adapter in backtrack4 or ubuntu 10.10 .  I know its asking alot but if your not a pro with linux its extremely hard to do, and for beginners its next to impossible. Thank you to anyone who is willing to take the time to do so. Im sure there will be thousands of Thank yous out there just waiting.  Please help.

---

### Post by atomicben on 2011-07-15
I have done this a bunch of times; most recently (last week) on my laptop.

There is a great tut by Jano over at the Aircrack Forum. Here's a link:
[http://forum.aircrack-ng.org/index.php?topic=5755.0](http://forum.aircrack-ng.org/index.php?topic=5755.0)

Don't let all that info overwhelm you. I'm going to summarize it for you. This is (mostly a C/P) from the section
"Installing Compact-Wireless patched for Ubuntu Maverick or Lucid with Kernel 2.6.35 to 2.6.37"
However, I have added steps and fixed a few broken ones.

Ok, the first thing you should know is that your AWUS036H will work out of the box on 10.10, but if you are looking to aircrack, then you need patched drivers.

Getting the drivers and patching them can be a wicked pain in the a** so a nice guy (Jano) over at aircrack has already PRE-patched the drivers for you!  YAY  (ok, the fragmentation attack patches are NOT included but I've never needed them so who cares)

**BEFORE WE BEGIN:** Do you even have the stuff installed to compile stuff?  If not, scroll down and find those instructions - you need to do them first.


**Getting and Installing:**
First get the package from Jano's site:
Click this link to download:
[Compat-wireless-aircrack-maverick-patched]("http://www.janoweb.net/drivers-patch/compat-wireless-aircrack-maverick-patched.tar.bz2")                                                  30-Oct-2010  2.5M
Download it to Downloads.

(If that link doesn't work for you go to [http://www.janoweb.net/drivers-patch.html](http://www.janoweb.net/drivers-patch.html)
go about half way down and find it)


Open a terminal and:

cd ~/Downloads
sudo rmmod rtl8187 zd1211rw mac80211
sudo mkdir /usr/src/drivers
sudo cp compat-wireless-aircrack-maverick-patched.tar.bz2 /usr/src/drivers
cd /usr/src/drivers
sudo tar jxvf compat-wireless-aircrack-maverick-patched.tar.bz2
cd compat-wireless-aircrack-lucid-maverick.patched
sudo make                                       
sudo make install
sudo make unload
sudo reboot

Description of steps above:
1. change into the downloads folder when you saved the compressed drivers from Jano.
2. unload rtl8187 zd1211rw mac80211 from memory so they don't cause a problem when compiling/installing.  This will kill (probably) your internet if you are only connected via wireless.  If you are wired, who cares, if you are reading this via wireless connection you can probably skip this step.
3. make a new directory where we will extract the source code
4. copy our compressed file to the new directory
5. change into our new folder
6. un-compress Jano's file (this creates a new directory)
7. change into the new directory where the files were un-compressed
8. compile the drivers (this will take a while)
9. install our new drivers
10. reboot your system


**Getting the stuff you need to compile:**
To get the stuff you need to compile do this:

sudo dpkg --configure -a && sudo apt-get install -f && sudo apt-get update

sudo apt-get install linux-headers-$(uname -r) build-essential make patch gcc gettext autoconf python-psyco subversion tcl8.5 openssl zlib1g zlib1g-dev libssh2-1-dev libssl-dev libnl1 libnl-dev libpcap0.8 libpcap0.8-dev python-scapy cracklib-runtime macchanger-gtk tshark


**Additional Information about r8187 and RTL8187:**
ALSO NOTE:
If you reboot and start either just networking or trying to aircrack and things aren't doing what they should it's probably because the r8187 driver has taken over.  I had this happen to me.  There are plenty of people out there that say that one driver should be used for Internet and the other for aircrack.  I have paid no attention to any of that.  I want RTL8187 NOT the r8187.  RTL8187 works great for me.  So, if you need to do this open a terminal and:


sudo cp /etc/modprobe.d/blacklist.conf /etc/modprobe.d/blacklist.original.conf
echo "blacklist r8187" | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo reboot

Explained:
1. make a backup of your current (original) /etc/modprobe.d/blacklist.conf file and call it blacklist.original.conf
2. adds "blacklist r8187" to the blacklist.conf file.  This prevents Ubuntu from loading that lousy driver.

If you ever need to GO BACK to the original then:
sudo rm /etc/modprobe.d/blacklist.conf
sudo cp /etc/it blacklist.original.conf /etc/modprobe.d/blacklist.conf

---

