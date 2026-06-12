---
title: "Install Asus N13-usb adapter on 10.04"
date: 2010-05-05
forum: Networking &amp; Wireless
---

### Post by phuc06 on 2010-05-05
I have a Asus N13-usb adapter and i am running ubuntu 10.04 on my  desktop. I tried all those commands that you have posted but it led me  nowhere. I was wondering if you can help me start off from scratch. I am  new to ubuntu and linux commands. Please let me know if you can help or  recommend me to someone else.

I have typed lsub and it showed the device. 

I followed this thread [http://ubuntuforums.org/showthread.php?t=1444746&page=1](http://ubuntuforums.org/showthread.php?t=1444746&page=1) 
and i did it up the part where you downloaded the driver. but i was not able to go further once i typed in the command :
cd Downloads
tar -xvzf

---

### Post by phuc06 on 2010-05-05
ubuntu@ubuntu-desktop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse
Bus 002 Device 002: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 0b05:1784 ASUSTek Computer, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
ubuntu@ubuntu-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

---

### Post by chili555 on 2010-05-05
Maybe we can find a shortcut. Please open a terminal and do:```
sudo gedit /etc/udev/rules.d/network_drivers.rules
```If you had previously created such a file, we are going to amend it. If not, we are going to write one from scratch. Add just one long line:```
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="0b05", ATTR{idProduct}=="1784", RUN+="/sbin/modprobe -qba rt2870sta"
```Proofread carefully, save and close gedit. If you had previously created such a file, all you need to do, aside from proofreading, is change rt3070sta to rt2870sta.

Now do:```
/etc/modprobe.d/network_drivers.conf
```Add one long line:```
install rt2870sta /sbin/modprobe --ignore-install rt2870sta $CMDLINE_OPTS; /bin/echo "0b05 1784" > /sys/bus/usb/drivers/rt2870/new_id

```Proofread carefully, save and close gedit. If you had previously created such a file, all you need to do, aside from proofreading, is change rt3070sta to rt2870sta in both places.

Now do:```
sudo su
echo rt2870sta >> /etc/modules
modprobe rt2870sta
exit
iwconfig
```Do you now have a wireless interface?

---

### Post by phuc06 on 2010-05-05
it gave me a permission denied when i entered in the second command.


ubuntu@ubuntu-desktop:~$ sudo gedit /etc/udev/rules.d/network_drivers.rules
[sudo] password for ubuntu: 

ubuntu@ubuntu-desktop:~$ 
ubuntu@ubuntu-desktop:~$ /etc/modprobe.d/network_drivers.conf
bash: /etc/modprobe.d/network_drivers.conf: Permission denied

---

### Post by chili555 on 2010-05-05
> $ /etc/modprobe.d/network_drivers.conf
bash: /etc/modprobe.d/network_drivers.conf: Permission deniedSorry abot that! That's what happens when I eat lunch, watch a Blu-Ray and answer a few posts all at the same time. Mistakes...

I meant:```
sudo gedit /etc/modprobe.d/network_drivers.conf
```Please excuse me and try again.

---

### Post by phuc06 on 2010-05-05
It now shows i have a wireless adapter. what do i do now? Thanks.

ubuntu@ubuntu-desktop:~$ sudo su
root@ubuntu-desktop:/home/ubuntu# echo rt2870sta >> /etc/modules
root@ubuntu-desktop:/home/ubuntu# modprobe rt2870sta
root@ubuntu-desktop:/home/ubuntu# exit
exit
ubuntu@ubuntu-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     RTxx70 Wireless  ESSID:""  Nickname:"RT3070STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by chili555 on 2010-05-05
> what do i do now? You click the Network Manager icon, see your network, ask it to connect and enjoy!

---

### Post by phuc06 on 2010-05-05
i see. Thank you very much.

---

### Post by chili555 on 2010-05-05
Does that mean you are now surfing wirelessly? Got your updates? Torrents? Mp3s? Instant messaging with Grandma in Alabama? All dialed in??

---

### Post by phuc06 on 2010-05-06
Hi Man. Sorry to bother you again but i cannot connect to my wireless network. ubuntu recognizes the wireless adapter but it wont connect to my network. i have a latitude d610 and i am running 10.04 also and i can connect to my wireless network with out a problem. can you please help me again.

Thanks.

---

### Post by chili555 on 2010-05-06
> i cannot connect to my wireless network.> i can connect to my wireless network with out a problem.I'm not sure I quite understand. What are your symptoms? Does Network Manager see your network and try to connect? Does it prompt you for your WPA or WEP key? What happens or doesn't happen?

---

### Post by phuc06 on 2010-05-06
Sorry for being unclear. With the Asus wireless adapter that you had helped me with for my desktop, i was not able to connect into my wireless network. However, i also have a laptop that i am running ubuntu 10.04, and i can connect to my wireless network fine. my network is hidden so i manually entered my ssid when i click on the network connection. i have wpa/wpa2 personal for encryption and i am using a pre-shared key. With the desktop, i manually entered in my wireless network SSID and password like i did with my laptop, but it doesn't connect. i get the wireless icon spinning in circle like it's looking for connection.

---

### Post by chili555 on 2010-05-07
Does it help if you do:```
sudo ifconfig wlan0 down
sudo iwconfig wlan0 mode managed
sudo iwconfig wlan0 rate 54M
sudo ifconfig wlan0 up
```Now can you connect? If not, please post:```
dmesg | grep -e rt2 -e wlan
```Thanks.

---

### Post by phuc06 on 2010-05-07
I typed in what you told me to and it connected. But it's only showing 1 bar on the signal bar and i cannot surf the internet. It says problem loading page, server not found. For testing purpose i have my wireless router is right next to it. I also noticed that in the code you put in:

sudo iwconfig wlan0 rate 54M

Is this to set the adapter at that speed rate, which is max speed for G network? my adapter can run on N network and i also have a N wireless router. i dont know if that's has anything to do with it. Also, when i click on the wireless network connection for information, it's showing a different IP address. It's not in the same range as how it should be for my DHCP.

i also typed in the second part of the code and this is the output:

ubuntu@ubuntu-desktop:~$ dmesg | grep -e rt2 -e wlan
[   11.572491] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   11.581227] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   11.592928] usbcore: registered new interface driver rt2870
[   23.560009] wlan0: no IPv6 routers present
[  767.072008] wlan0: no IPv6 routers present

---

### Post by chili555 on 2010-05-07
> Is this to set the adapter at that speed rate, which is max speed for G network? Correct. That was just to get us started.> when i click on the wireless network connection for information, it's showing a different IP address. It's not in the same range as how it should be for my DHCP.May I have specifics? I wonder if you are actually connected to the neighbor's network. ```
ifconfig wlan0
iwconfig wlan0
```

---

### Post by phuc06 on 2010-05-08
ubuntu@ubuntu-desktop:~$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr e0:cb:4e:bd:41:8c  
          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0
          inet6 addr: fe80::e2cb:4eff:febd:418c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:130 errors:0 dropped:0 overruns:0 frame:0
          TX packets:107 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:33607 (33.6 KB)  TX bytes:7452 (7.4 KB)

ubuntu@ubuntu-desktop:~$ iwconfig wlan0
wlan0     RTxx70 Wireless  ESSID:"nhanguyen"  Nickname:"RT3070STA"
          Mode:Ad-Hoc  Frequency=2.462 GHz  Cell: 96:4A:D9:3E:32:F9   
          Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by chili555 on 2010-05-08
> $ iwconfig wlan0
wlan0 RTxx70 Wireless ESSID:"nhanguyen" Nickname:"RT3070STA"
Mode:[COLOR="Red"]Ad-Hoc[/COLOR]Ah, ha! It's trying to negotiate an ad-hoc (computer to computer) connection. Please do:```
sudo ifconfig wlan0 down
sudo iwconfig wlan0 mode managed
sudo iwconfig wlan0 rate 54M
sudo ifconfig wlan0 up
```How about now?

---

### Post by phuc06 on 2010-05-08
nope it didn't work. i noticed the ad-hoc mode too and i went into network connection manager to change it to infrastructure mode and it didnt work. it keeps on looking for connection and the authentication window keeps popping up asking for my password to the network. i also tried to do a scan and it found my wireless network with great strength signal but it's not able to connect, authentication window still pops up. i know the adapter works because i had tried it on a windows XP machine and it worked.

Appreciate all your help and hope we can figure this out.

Thanks.

---

### Post by phuc06 on 2010-05-09
i found this link when looking through the forum. Do you think i should try it?

[http://swiss.ubuntuforums.org/showthread.php?t=1382798](http://swiss.ubuntuforums.org/showthread.php?t=1382798)

it talks about downloading an updated driver version for ralink RT2870usb. i checked out the ralink website and saw that they have an updated one RT3070usb v2.3.0.2. does it matter which one i install? would the lastest one support my wifi adapter?

---

### Post by chili555 on 2010-05-09
It will indeed support your device. I suggest the RT3070USB package. 

Make sure you make any modifications outlined in the readme file before you start. Also make sure you have linux-headers-generic and build-essential installed. Before you do 'make install,' do:```
cp RT2870STA.dat RT3070STA.dat
rm /etc/udev/rules.d/network_drivers.rules
rm /etc/modprobe.d/network_drivers.conf
```Good luck!

---

### Post by phuc06 on 2010-05-09
can you please show me step by step how to install this updated driver since i am completely new to ubuntu. i am going to download it and then run that script that you specified, and then what next?

Thanks.

---

### Post by chili555 on 2010-05-10
> **phuc06 said:**
> can you please show me step by step how to install this updated driver since i am completely new to ubuntu. i am going to download it and then run that script that you specified, and then what next?

Thanks.Please go here: [http://www.ralink.com.tw/support.php?s=2](http://www.ralink.com.tw/support.php?s=2)

Download the package RT3070USB/RT307x to your desktop. Open System > Administration > Synaptic and install *linux-headers-generic* and *build-essential*. 

Open a terminal and do:```
cd Desktop/
tar xvjf DPO_RT3070*
cd DPO_RT3070_LinuxSTA_V2.3.0.2_20100412
gedit os/linux/config.mk
```Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'.

Proofread, save and close gedit. Now do:```
sudo su
cp RT2870STA.dat RT3070STA.dat
rm /etc/udev/rules.d/network_drivers.rules
rm /etc/modprobe.d/network_drivers.conf
make
make install
rmmod -f rt2870sta
modprobe rt3070sta
exit
```Detach the ethernet cable, if any and click the Network Manager icon.

Now is your card working? We may need to tweak RT3070STA.dat, if not.

---

### Post by phuc06 on 2010-05-13
Hi,
 
Sorry i've been busy so didn't get a chance to get back to you as soon as possible. I was able to edit config.mk file but when i started to type to the command
 
cp RT2870STA.dat RT3070STA.dat
 
it gave me this error:
cp: cannot stat 'RT2870STA.dat': so such file or directory

---

### Post by chili555 on 2010-05-13
Are you in the correct directory?```
cd Desktop/
tar xvjf DPO_RT3070*
cd DPO_RT3070_LinuxSTA_V2.3.0.2_20100412

```When you list the contents of the current directory, is there a .dat file there?```
ls
```

---

### Post by phuc06 on 2010-05-16
Thanks for helping. I was messing with it and i deleted some files and i wasn't sure that may have caused for the errors and wireless not working. But i decided to reinstall Ubuntu 10.04 over again. After the installation, i went to Ralink website and downloaded the driver 3070 to my Downloads folder and i did these commands:

cd Downloads/
tar xvjf DPO_RT3070*
cd DPO_RT3070_LinuxSTA_V2.3.0.2_20100412
gedit os/linux/config.mk - changed the setting on WPA

sudo su
cp RT2870STA.dat RT3070STA.dat
make
make install

sudo gedit /etc/udev/rules.d/network_drivers.rules
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="0b05", ATTR{idProduct}=="1784", RUN+="/sbin/modprobe -qba rt3070sta"
sudo gedit /etc/modprobe.d/network_drivers.conf
install rt3070sta /sbin/modprobe --ignore-install rt3070sta $CMDLINE_OPTS; /bin/echo "0b05 1784" > /sys/bus/usb/drivers/rt3070/new_id
sudo su
echo rt3070sta >> /etc/modules
modprobe rt3070sta

I got this error message:

root@ubuntu1:/home/phuc/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.2_20100412# modprobe rt3070sta
FATAL: Error inserting rt3070sta (/lib/modules/2.6.32-22-generic-pae/kernel/drivers/net/wireless/rt3070sta.ko): Unknown symbol in module, or unknown parameter (see dmesg)
sh: cannot create /sys/bus/usb/drivers/rt3070/new_id: Directory nonexistent
FATAL: Error running install command for rt3070sta

---

### Post by chili555 on 2010-05-16
> sudo gedit /etc/udev/rules.d/network_drivers.rules
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="0b05", ATTR{idProduct}=="1784", RUN+="/sbin/modprobe -qba rt3070sta"
sudo gedit /etc/modprobe.d/network_drivers.conf
install rt3070sta /sbin/modprobe --ignore-install rt3070sta $CMDLINE_OPTS; /bin/echo "0b05 1784" > /sys/bus/usb/drivers/rt3070/new_idMy instructions above do not say this; they say to *remove* these files.> rm /etc/udev/rules.d/network_drivers.rules
rm /etc/modprobe.d/network_drivers.conf
However, I don't think this has any real effect on the process. It errors out for me, too. All I can suggest is to email Ralink and ask them about it. Be sure to report what dmesg says:> [31510.419743] rt3070sta: Unknown symbol usb_alloc_urb
[31510.419900] rt3070sta: Unknown symbol usb_free_urb
[31510.420323] rt3070sta: Unknown symbol usb_register_driver
[31510.420639] rt3070sta: Unknown symbol usb_put_dev
[31510.420763] rt3070sta: Unknown symbol usb_get_dev
[31510.420997] rt3070sta: Unknown symbol usb_submit_urb
[31510.421550] rt3070sta: Unknown symbol usb_control_msg
[31510.421939] rt3070sta: Unknown symbol usb_deregister
[31510.422474] rt3070sta: Unknown symbol usb_kill_urb
[31510.422594] rt3070sta: Unknown symbol usb_buffer_free
[31510.423099] rt3070sta: Unknown symbol usb_buffer_allocI am sorry I could not be of more help.

---

### Post by phuc06 on 2010-05-16
The adapter came with a driver CD that also supported Linux. Can i perform those same steps above if i use the files from the CD? Do i need to add anything?

---

### Post by chili555 on 2010-05-16
It's entirely kernel and GCC dependent. If the package was built against kernel version 2.6.28, for example, it probably won't compile against 2.6.31 or -32. The only way to find out is to try.

Before you start, I'd do:```
cd DPO_RT3070_LinuxSTA_V2.3.0.2_20100412
sudo make uninstall
```Then cd to the directory where the driver CD files have been copied and proceed. 

I will look forward to your report.

---

### Post by phuc06 on 2010-05-22
Hi chilli,

I followed this thread and got it working, but i had to disable my wireless security for the adapter to connect. is it because the adapter doesn't support WPA2? can we make some changes to the driver?

[http://ubuntuforums.org/showthread.php?t=1467291&highlight=asus+n13-usb&page=2](http://ubuntuforums.org/showthread.php?t=1467291&highlight=asus+n13-usb&page=2)

---

### Post by phuc06 on 2010-05-22
Ok never mind. it does support WPA2, but for cipher security i picked TKIP instead of AES. I had it on auto before so i dont know it's capable of supporting AES. One more question. It's showing that its running on G network at 54mbps. Can you show me how to change so it can run on N network?
Thanks.

---

### Post by phuc06 on 2010-05-22
I am also having a problem retaining the wireless connection. Every time i reboot, i can't connect. i have to log into my router and disable the wireless security, then i can connect. then i go back into my router and change my wireless setting with security enabled, it has no problem reconnecting once i put in the password. Is there a way to solve this?

Thanks.

---

### Post by chili555 on 2010-05-22
> **phuc06 said:**
> Ok never mind. it does support WPA2, but for cipher security i picked TKIP instead of AES. I had it on auto before so i dont know it's capable of supporting AES. One more question. It's showing that its running on G network at 54mbps. Can you show me how to change so it can run on N network?
Thanks.You might try:```
sudo iwconfig ra0 rate auto
```

---

### Post by motin on 2010-06-15
Seems to be relevant, I posted how to install a working driver for the device with id 07d1:3c0d on [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/546653](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/546653)

Cheers

---

### Post by incec on 2011-01-11
I have bought an Asus N13 wireless USB adapter
 
I have been following instructions posted for other users to install ASUS N13 wireless USB adapter. 
 
when i get as far as the "make" command, I get "permission denied" ,( this is after using two approaches to build ) after i put the pasword  in correctly
 
can anyone help?

---

