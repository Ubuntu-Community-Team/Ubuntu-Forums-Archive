---
title: "Ubuntu 12.04 on Toshiba C850-I0011 with AR8162 Ethernet and Realtek 8723 wireless"
date: 2012-11-24
forum: Networking &amp; Wireless
---

### Post by prajan on 2012-11-24
Toshiba C850-I0011 - Core i3 Laptop with Atheros AR8162 Ethernet card and Realtek 8723 wireless card - both need to be compiled to install them. Without Internet it is a difficult task to compile and install drivers. I had to use DVD repositories to install the build essentials and linux headers to bring up ethernet interface. My how-to to bring up ubuntu 12.04 on Toshiba C850-I0011 as a dual boot with Windows.

1.Download the compatible driver for Atheros AR8162 from some other computer with an internet connection as given in the forum below
[http://ubuntuforums.org/showthread.php?t=2050126](http://ubuntuforums.org/showthread.php?t=2050126)

Download compatible wireless package from 
[www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.5/compat-wireless-3.5.1-1-snpc.tar.bz2]("http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.5/compat-wireless-3.5.1-1-snpc.tar.bz2")
Copy this into an usb drive that can be mounted on the ubuntu computer.

2. Install only the base version of ubuntu - no additional software (samba nearly killed me with unresolvable dependencies). To reinstall, delete the linux partition from windows, install again using the free partition. The installer creates a fresh partition and creates grub boot loader again in the master boot record.

3. Update cdrom to be the repository
sudo vi /etc/apt/sources.list
Comment all the internet repository URLs.
insert the repository dvd into the drive and type
sudo apt-cdrom get
Give an alias name for each DVD and this is stored into the stores.list.
sudo umount /media/cdrom <- Unmount the DVD
Repeat the above to create a map of all the 12 DVD repositories.

sudo lshw -C network -> Gives the list of network hardware

Install build-essential and linux-header-`uname -r` using commands

sudo apt-get install build-essential
sudo apt-get -f install <- To fix any dependency issues. Continue doing this till build essentials is complete
sudo apt-get linux-headers-`uname -r`

4. Mount the USB drive on ubutu server.
sudo blkid <-- Gives you the unique id for your usb device
Create a mount point /mnt/ddrive and make yourself owner of this folder. Create an entry into /etc/fstab
UUID=<your usb device id> /mnt/drive ntfs users,defaults 0 0

Reboot and you should be able to access the downloaded compat-wireless package files at /mnt/ddrive. To install 
tar -xf compat-wireless-3.5.1-1-snpc.tar.bz2
cd compat-wireless-3.5.1-1-snpc
./scripts/driver-select alx
sudo make
sudo make install
sudo modprobe alx

Restart and voila - you should have your ethernet interface up and running.

Change back your repository sources by commenting your cdrom entries and uncommenting the earlier commented out ubuntu repositories on the internet. 
sudo vi /etc/apt/sources.list

Update the packages
sudo apt-get update

Install whatever desktop xubuntu, kubuntu etc.

To install Wireless Realtek 8723 - As given,
[http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized](http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized)
Download unofficial driver from 
dl.dropbox.com/u/57056576/DRIVERS/REALTEK/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012.tar.gz

sudo make
sudo make install
sudo modprobe rtl8723e

reboot and your network manager should detect your wireless card and ask for the security key to be able to connect to your access point.

---

### Post by menonrudhin on 2013-01-20
Thankyou very much Prajan, I appreciate your work. It worked for my atheros ethernet.:KS

Unfortunately the WIRELESS one is not working:(, can you help me on this ?

lspci shows this:

02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8723

Thank you in advance :)

---

