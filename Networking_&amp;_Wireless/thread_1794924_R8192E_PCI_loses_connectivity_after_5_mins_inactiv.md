---
title: "R8192E_PCI loses connectivity after 5 mins inactivity on Natty (Samsung N130)"
date: 2011-07-01
forum: Networking &amp; Wireless
---

### Post by dsluser on 2011-07-01
Hi all, 

Firstly I'm still pretty new to linux so please bear with me. 

I have a fresh install of 11.04 natty running on my N130. 

lsmod shows


~$ lsmod | grep r81
r8192e_pci            251260  0 
r8192se_pci           482505  0 
cfg80211              156212  1 r8192se_pci

However the se driver doesn't do anything, I usually just modprobe -r it and the cfg 80211 goes with it.

After about 5 mins inactivity I cannot ping the router(and obviously anything beyond this). 127.0.0.1 works fine.

I can rmmod r8192e_pci and then modprobe r8192e_pci and it works again until the next timeout but this is extremely annoying. When it drops I'm still showing as connected and iwconfig shows no changes.

I've tried blacklisting the se driver and the lan driver in case they were interfering but with no success.

For completion lspci and modprobe -l | grep r81 shown below

~$ lspci | grep Realtek
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8192E Wireless LAN Controller (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

~$ modprobe -l | grep r81
kernel/drivers/net/r8169.ko
kernel/drivers/staging/rtl8187se/r8187se.ko
kernel/drivers/staging/rtl8192u/r8192u_usb.ko
kernel/drivers/staging/rtl8192e/r8192e_pci.ko
kernel/ubuntu/rtl8192se/r8192se_pci.ko

Any help or suggestions would be greatly appreciated

*EDIT*
sudo network-manager stop produces the same symptoms, can somebody maybe talk me through going around network manager to see if this solves the issue? I've tried adding auto wlan0 and iface wlan0 inet dhcp with the wpa ssid and passphrase and doing ifup wlan0 but it tells me it's already up and I can't connect.

*EDIT2* dhclient wlan0 does not renew ip address after stopping network manager. I have set the essid using iwconfig but cannot add the wpa2 key, can anyone tell me how to do this via command line? ifconfig only shows loopback interface when network manager is stopped, I assume this is because I haven't managed to add the wpa key.

---

### Post by dsluser on 2011-07-02
So it also happens when network manager is stopped but I can instantly reconnect by doing

ifdown wlan0
ifup wlan0

This leads me to believe it could be caused by some power saving option or similiar that's enabled by default in Natty. 

Any linux gurus able to suggest a command to force my wireless to maintain a connection when it's not active?

---

### Post by moaoci on 2011-07-03
I am no Linux guru but I know the rtl8192e driver.  And I am surprised you could get anything out of your  install !  

The driver provided by Ubuntu  (staging driver from Linux) is not working (out of the box).  Some people were able to make it work but I never was.   Realtek provides a driver that works. For Ubuntu 11.04, the driver is this one rtl8192e_linux_2.6.0015.1013.2010 . I could not include it here because of it's size, 1.7M.

You can get it by writing to [EMAIL="wlanfoe@realtek.com"]wlanfae@realtek.com[/EMAIL] specifying what machine and Ubuntu version you are using. I could also sent it to you if you send me your e-mail address by private message. 

Once you get the realtek driver, the first thing to do is delete the staging driver, and also the rtl8192se driver.  rtl8192se driver shares most of the same code as rtl8192e but it doesn't work for rtl8192e.

To delete: 
run the "terminal" application,
type: sudo nautilus
This will open a desktop directory with privileges.  Navigate to File system => lib => modules => (your linux kernel number, most likely the only file in modules) => kernel => drivers => staging
Find the rtl8192e directory and delete it (press DEL)

Do the same for ...  kernel => Ubuntu => rtl8192se

Then quit the directory and close terminal application.

Unzip (extract) the driver to the desktop, creating the driver directory  rtl8192e_linux_2.6.0015.1013.2010
Now you can compile the Realtek driver: (You will have to recompile at each linux kernel number change)

Open the terminal application
type:  sudo su
This will identify yourself as super user with all privileges, 
type: cd Desktop
type: cd rtl8192e_linux_2.6.0015.1013.2010
type: make clean
type: make
type: make install

reboot now

This should be all !

---

### Post by dsluser on 2011-09-20
Thanks for the advice, turns out my router was at fault. After weeks troubleshooting I swapped it out and everything worked perfectly with my initial setup :guitar:

---

