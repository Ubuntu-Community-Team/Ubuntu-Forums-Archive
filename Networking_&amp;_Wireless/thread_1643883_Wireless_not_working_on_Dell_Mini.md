---
title: "Wireless not working on Dell Mini"
date: 2010-12-12
forum: Networking &amp; Wireless
---

### Post by muddly49 on 2010-12-12
Hello,
I have Ubuntu 10.10 installed on a Dell Inspiron Mini 1018. It has a Realtek wireless chipset and can't get working after a few hours of trying. I installed the realtek drivers from the realtek support website. I installed the build essentials through apt-get then:

sudo su
make
make install
rebooted

wlan didn't show in network connections applet

So I tried:
sudo su
ifconfig wlan0 up

iwconfig shows:
lo no wireless extensions
eth0 no wireless extensions

wlan0     802.11bgn  Nickname:"rtl8192CE"
          Mode:Managed  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:65 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=10/100  Signal level=0 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

In System/Administration/Additional Drivers it shows the driver installed and activated. I think I'm close to getting it working....LOL. Any help would be greatly appreciated.

---

### Post by Mbroadstone on 2011-02-06
Try:
 
sudo add-apt-repository ppa:lexical/hwe-wireless
sudo apt-get update
sudo apt-get install rtl8192ce-dkms
 
It seems to get the right driver for the wirless but it will only work on my mini until I update Ubuntu.  Maybe that won't be a problem for you, but if you find a fix for my update issue please let me know.

---

### Post by Cortbssguitar on 2011-04-08
I also have a 10inch Dell Inspiron mini 1018! :grin:
It's realy easy to install the driver for wifi. Simply copy these commands into the terminal:

sudo -E make clean modules 
 sudo make install 
 sudo depmod -a
 blacklist r8169
 sudo update-initramfs -u


sudo add-apt-repository ppa:lexical/hwe-wireless
sudo apt-get update
sudo apt-get install rtl8192ce-dkms


Keep the PPA in the softwaresources. Then you have not to reinstall it! :wink:

Ps; Mbroadstone You've also found the right driver!

Have fun!

Sincerely,
 Mark

---

