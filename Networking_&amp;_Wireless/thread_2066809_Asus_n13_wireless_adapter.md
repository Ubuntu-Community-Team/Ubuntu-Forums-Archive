---
title: "Asus n13 wireless adapter"
date: 2012-10-05
forum: Networking &amp; Wireless
---

### Post by Marthewicked on 2012-10-05
Hello all,

I can not connect to internet and i need help. I already made a post on wireless and networking but i guess im new so i maybe asking beginner stuff, so no help there. I have a desktop and asus n13 wireless adapter and i can not install the driver. The driver instructed me to wrong information by saying linux compatible which is why i bought it to think plug and play. My ubuntu is 11.04 and it is clean  install, only think i have is go programing language.
Please help and i thank you in advance.
Mar

---

### Post by daslinkard on 2012-10-05
Please let me know the output of the following sudo command:
```

lspci
```

---

### Post by Marthewicked on 2012-10-05
> **daslinkard said:**
> Please let me know the output of the following sudo command:
```

lspci
```

Thanks for the reply,

here is the lcpi

  	 	 	 	 	 	   mar@ubuntu:~$ lspci  
 00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)  
 00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)  
 00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02)  
 00:19.0 Ethernet controller: Intel Corporation 82562V-2 10/100 Network Connection (rev 02)  
 00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)  
 00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)  
 00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)  
 00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)  
 00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)  
 00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)  
 00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)  
 00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)  
 00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)  
 00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)  
 00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)  
 00:1f.2 RAID bus controller: Intel Corporation 82801 SATA RAID Controller (rev 02)  
 00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)  
 02:00.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem  
 mar@ubuntu:~$  
  
sorry for the late reply

---

### Post by critin on 2012-10-05
> **Marthewicked said:**
> Hello all,

I can not connect to internet and i need help. I already made a post on wireless and networking but i guess im new so i maybe asking beginner stuff, so no help there. I have a desktop and asus n13 wireless adapter and i can not install the driver. The driver instructed me to wrong information by saying linux compatible which is why i bought it to think plug and play. My ubuntu is 11.04 and it is clean  install, only think i have is go programing language.
Please help and i thank you in advance.
Mar

Get an ethernet wire and wire the laptop to the modem.  You should be able to fix it then.   Using wired internet to install is much better as it can then download drivers as it installs.

---

### Post by mips on 2012-10-05
If your wireless is connected via USB then post the output of **lsusb**

---

### Post by Marthewicked on 2012-10-05
Wireless usb was not connected at the time of code run but i can connect and run it.

---

### Post by Marthewicked on 2012-10-05
I have the drivers on cd if that makes a difference. On the dvd there are mac, windows, and linux drivers. However, i dont know how to install it from disc.
Thank you so much guys.

---

### Post by Marthewicked on 2012-10-05
lscpi 

this is while the usb asus n13 connected

  	 	 	 	 	 	   mar@ubuntu:~$ lspci  
 00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)  
 00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)  
 00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02)  
 00:19.0 Ethernet controller: Intel Corporation 82562V-2 10/100 Network Connection (rev 02)  
 00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)  
 00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)  
 00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)  
 00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)  
 00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)  
 00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)  
 00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)  
 00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)  
 00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)  
 00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)  
 00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)  
 00:1f.2 RAID bus controller: Intel Corporation 82801 SATA RAID Controller (rev 02)  
 00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)  
 02:00.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem  
 mar@ubuntu:~$

---

### Post by Marthewicked on 2012-10-05
corrections......
this is when it was plugged in. I am using copy flash drive on copy and paste from desktop to laptop since laptop is connected to internet.
Thanks,
Mar




mar@ubuntu:~$ sudo lspci  
 00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)  
 00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)  
 00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02)  
 00:19.0 Ethernet controller: Intel Corporation 82562V-2 10/100 Network Connection (rev 02)  
 00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)  
 00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)  
 00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)  
 00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)  
 00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)  
 00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)  
 00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)  
 00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)  
 00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)  
 00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)  
 00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)  
 00:1f.2 RAID bus controller: Intel Corporation 82801 SATA RAID Controller (rev 02)  
 00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)  
 02:00.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem  
 mar@ubuntu:~$

---

### Post by steeldriver on 2012-10-05
The Asus N13 can be tricky iirc because different generations use different chipsets / drivers

Since it's a USB device we will need either

```
lsusb
```

(not lspci) or

```
lshw -C network
```

while the device is plugged in please

---

### Post by Marthewicked on 2012-10-05
ok no problem.....will post in few minutes 3 tops

---

### Post by Marthewicked on 2012-10-05
mar@ubuntu:~$ lsusb  
 Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 006 Device 002: ID 04d9:a01c Holtek Semiconductor, Inc.  
 Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
 Bus 001 Device 011: ID 0b05:17ab ASUSTek Computer, Inc.  
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
 mar@ubuntu:~$

---

### Post by daslinkard on 2012-10-05
I found this on another post and believe this will work for you....
```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms 
wget [http://media.cdn.ubuntu-de.org/forum/attachments/32/20/2844083-rtl8192cu-3.3.23192_dkms.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/32/20/2844083-rtl8192cu-3.3.23192_dkms.tar.gz) 
sudo tar xvf 2844083-rtl8192cu-3.3.23192_dkms.tar.gz -C /usr/src 
sudo dkms add -m rtl8192cu -v 3.3.23192 
sudo dkms build -m rtl8192cu -v 3.3.23192 
sudo dkms install -m rtl8192cu -v 3.3.23192
``````
sudo gedit /etc/rc.local
```Right above exit 0 add these two lines:
     ```
modprobe rtl8192cu
``` ```
 echo "0b05 17ab" > /sys/bus/usb/drivers/rtl8192cu/new_id
```

Found the work around [here]("http://ubuntuforums.org/showthread.php?t=2009075")

---

### Post by Marthewicked on 2012-10-05
> **daslinkard said:**
> I found this on another post and believe this will work for you....
```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms 
wget [http://media.cdn.ubuntu-de.org/forum/attachments/32/20/2844083-rtl8192cu-3.3.23192_dkms.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/32/20/2844083-rtl8192cu-3.3.23192_dkms.tar.gz) 
sudo tar xvf 2844083-rtl8192cu-3.3.23192_dkms.tar.gz -C /usr/src 
sudo dkms add -m rtl8192cu -v 3.3.23192 
sudo dkms build -m rtl8192cu -v 3.3.23192 
sudo dkms install -m rtl8192cu -v 3.3.23192
``````
sudo gedit /etc/rc.local
```Right above exit 0 add these two lines:
     ```
modprobe rtl8192cu
``` ```
 echo "0b05 17ab" > /sys/bus/usb/drivers/rtl8192cu/new_id
```Found the work around [here]("http://ubuntuforums.org/showthread.php?t=2009075")

sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms 
wget [http://media.cdn.ubuntu-de.org/forum/attachments/32/20/2844083-rtl8192cu-3.3.23192_dkms.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/32/20/2844083-rtl8192cu-3.3.23192_dkms.tar.gz) 

That is one code right? Do i have to be connected to internet because im not.

Also, i tried one line at a time or copied all the box and paste and both results are the same ....here

  	 	 	 	 	 	   mar@ubuntu:~$ sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms  
 [sudo] password for mar:  
 Reading package lists... Done  
 Building dependency tree        
 Reading state information... Done  
 0 upgraded, 0 newly installed, 4 reinstalled, 0 to remove and 0 not upgraded.  
 Need to get 915 kB of archives.  
 After this operation, 0 B of additional disk space will be used.  
 Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/main build-essential amd64 11.5ubuntu1  
   Could not resolve 'us.archive.ubuntu.com'  
 Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/main dkms all 2.1.1.2-5ubuntu1  
   Could not resolve 'us.archive.ubuntu.com'  
 Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates/main linux-headers-2.6.38-16-generic amd64 2.6.38-16.67  
   Could not resolve 'us.archive.ubuntu.com'  
 Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) natty-security/main linux-headers-2.6.38-16-generic amd64 2.6.38-16.67  
   Could not resolve 'security.ubuntu.com'  
 Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) natty-security/main linux-headers-generic amd64 2.6.38.16.31  
   Could not resolve 'security.ubuntu.com'  
 Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/b/build-essential/build-essential_11.5ubuntu1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/b/build-essential/build-essential_11.5ubuntu1_amd64.deb)  Could not resolve 'us.archive.ubuntu.com'  
 Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.1.1.2-5ubuntu1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.1.1.2-5ubuntu1_all.deb)  Could not resolve 'us.archive.ubuntu.com'  
 Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.38-16-generic_2.6.38-16.67_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.38-16-generic_2.6.38-16.67_amd64.deb)  Could not resolve 'security.ubuntu.com'  
 Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-headers-generic_2.6.38.16.31_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-headers-generic_2.6.38.16.31_amd64.deb)  Could not resolve 'security.ubuntu.com'  
 E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?  
 mar@ubuntu:~$ run apt-get update  
 No command 'run' found, did you mean:  
  Command 'crun' from package 'ceph' (universe)  
  Command 'zrun' from package 'moreutils' (universe)  
  Command 'runq' from package 'exim4-daemon-heavy' (main)  
  Command 'runq' from package 'exim4-daemon-light' (main)  
  Command 'runq' from package 'sendmail-bin' (universe)  
  Command 'grun' from package 'grun' (universe)  
  Command 'qrun' from package 'torque-client' (universe)  
  Command 'qrun' from package 'torque-client-x11' (universe)  
  Command 'lrun' from package 'lustre-utils' (universe)  
  Command 'rn' from package 'trn' (multiverse)  
  Command 'rn' from package 'trn4' (multiverse)  
  Command 'rup' from package 'rstat-client' (universe)  
  Command 'srun' from package 'slurm-llnl' (universe)  
 run: command not found  
 mar@ubuntu:~$ sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms  
 Reading package lists... Done  
 Building dependency tree        
 Reading state information... Done  
 0 upgraded, 0 newly installed, 4 reinstalled, 0 to remove and 0 not upgraded.  
 Need to get 915 kB of archives.  
 After this operation, 0 B of additional disk space will be used.  
 Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/main build-essential amd64 11.5ubuntu1  
   Could not resolve 'us.archive.ubuntu.com'  
 Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/main dkms all 2.1.1.2-5ubuntu1  
   Could not resolve 'us.archive.ubuntu.com'  
 Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates/main linux-headers-2.6.38-16-generic amd64 2.6.38-16.67  
   Could not resolve 'us.archive.ubuntu.com'  
 Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) natty-security/main linux-headers-2.6.38-16-generic amd64 2.6.38-16.67  
   Could not resolve 'security.ubuntu.com'  
 Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) natty-security/main linux-headers-generic amd64 2.6.38.16.31  
   Could not resolve 'security.ubuntu.com'  
 Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/b/build-essential/build-essential_11.5ubuntu1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/b/build-essential/build-essential_11.5ubuntu1_amd64.deb)  Could not resolve 'us.archive.ubuntu.com'  
 Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.1.1.2-5ubuntu1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.1.1.2-5ubuntu1_all.deb)  Could not resolve 'us.archive.ubuntu.com'  
 Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.38-16-generic_2.6.38-16.67_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.38-16-generic_2.6.38-16.67_amd64.deb)  Could not resolve 'security.ubuntu.com'  
 Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-headers-generic_2.6.38.16.31_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-headers-generic_2.6.38.16.31_amd64.deb)  Could not resolve 'security.ubuntu.com'  
 E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?  
 mar@ubuntu:~$ wget [http://media.cdn.ubuntu-de.org/forum...92_dkms.tar.gz](http://media.cdn.ubuntu-de.org/forum...92_dkms.tar.gz)  
 --2012-10-05 22:00:56--  [http://media.cdn.ubuntu-de.org/forum...92_dkms.tar.gz](http://media.cdn.ubuntu-de.org/forum...92_dkms.tar.gz)  
 Resolving media.cdn.ubuntu-de.org... failed: Name or service not known.  
 wget: unable to resolve host address `media.cdn.ubuntu-de.org'  
 mar@ubuntu:~$ sudo tar xvf 2844083-rtl8192cu-3.3.23192_dkms.tar.gz -C /usr/src  
 tar: 2844083-rtl8192cu-3.3.23192_dkms.tar.gz: Cannot open: No such file or directory  
 tar: Error is not recoverable: exiting now  
 mar@ubuntu:~$ sudo dkms add -m rtl8192cu -v 3.3.23192  
 

 Error! Could not find module source directory.  
 Directory: /usr/src/rtl8192cu-3.3.23192 does not exist.  
 mar@ubuntu:~$ sudo dkms build -m rtl8192cu -v 3.3.23192  
 

 Error! DKMS tree does not contain: rtl8192cu-3.3.23192  
 Build cannot continue without the proper tree.  
 mar@ubuntu:~$ sudo dkms install -m rtl8192cu -v 3.3.23192

---

### Post by daslinkard on 2012-10-05
I do believe you need to be connected to the Internet to be able to get the updates/downloads.

---

### Post by critin on 2012-10-05
> E: Unable to fetch some archives, [COLOR=Blue]maybe run[/COLOR][COLOR=Red] **apt-get update**[/COLOR] or try with[COLOR=Red]** --fix-missing**[/COLOR]?  
 mar@ubuntu:~$ [COLOR=Blue]**run**[/COLOR] **[COLOR=Red]apt-get update[/COLOR]  **
 [COLOR=Blue]No command 'run' found[/COLOR], did you mean:  
  CoDon't copy the word in blue--run--.   The codes are only those in red.

And yes, updates are from the web.  You must be connected.

---

### Post by Marthewicked on 2012-10-06
> **daslinkard said:**
> I do believe you need to be connected to the Internet to be able to get the updates/downloads.

Ok thanks. I will connect through ethernet and try again. Will it make difference if i jave the drivers and such on cd rom?

---

### Post by daslinkard on 2012-10-06
Once you run the commands while connected to the Internet I believe will actually enable you to download the necessary drivers without having to use your CD.  I will be gone for the majority of the day but will check in tonight.  Good luck!

---

### Post by Marthewicked on 2012-10-06
Thanks guys, you guys are the best. Ubuntu is like hate-love, then love-hate relationship with me but i think i think the hate part is disappearing thanks to you guys for that.
Now, i may have tried to update twice where the first time worked but i will give all the codes since connected to the internet.
One more thing, the last part where i supposed to copy the two lines above the exit, well, they have "#" starting from the beginning, should i have added # in front of those two lines? I did not. I just followed instructions but just intuitive thoughts that i should ask after all i don't have all that knowledge on ubuntu yet.
Once again, thank you.

  	 	 	 	 	 	   Sorry, try again.  
 [sudo] password for mar:  
 Sorry, try again.  
 [sudo] password for mar:  
 

 Error! DKMS tree does not contain: rtl8192cu-3.3.23192  
 Build cannot continue without the proper tree.  
 mar@ubuntu:~$ sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms  
 Reading package lists... Done  
 Building dependency tree        
 Reading state information... Done  
 0 upgraded, 0 newly installed, 4 reinstalled, 0 to remove and 0 not upgraded.  
 Need to get 915 kB of archives.  
 After this operation, 0 B of additional disk space will be used.  
 Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/main build-essential amd64 11.5ubuntu1 [5,928 B]  
 Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/main dkms all 2.1.1.2-5ubuntu1 [71.9 kB]  
 Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates/main linux-headers-2.6.38-16-generic amd64 2.6.38-16.67 [835 kB]  
 Get:4 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates/main linux-headers-generic amd64 2.6.38.16.31 [2,682 B]  
 Fetched 915 kB in 0s (1,420 kB/s)                 
 (Reading database ... 144351 files and directories currently installed.)  
 Preparing to replace build-essential 11.5ubuntu1 (using .../build-essential_11.5ubuntu1_amd64.deb) ...  
 Unpacking replacement build-essential ...  
 Preparing to replace dkms 2.1.1.2-5ubuntu1 (using .../dkms_2.1.1.2-5ubuntu1_all.deb) ...  
 Unpacking replacement dkms ...  
 Preparing to replace linux-headers-2.6.38-16-generic 2.6.38-16.67 (using .../linux-headers-2.6.38-16-generic_2.6.38-16.67_amd64.deb) ...  
 Unpacking replacement linux-headers-2.6.38-16-generic ...  
 Preparing to replace linux-headers-generic 2.6.38.16.31 (using .../linux-headers-generic_2.6.38.16.31_amd64.deb) ...  
 Unpacking replacement linux-headers-generic ...  
 Processing triggers for man-db ...  
 Setting up build-essential (11.5ubuntu1) ...  
 Setting up dkms (2.1.1.2-5ubuntu1) ...  
 Setting up linux-headers-2.6.38-16-generic (2.6.38-16.67) ...  
 Examining /etc/kernel/header_postinst.d.  
 run-parts: executing /etc/kernel/header_postinst.d/dkms 2.6.38-16-generic /boot/vmlinuz-2.6.38-16-generic  
  * dkms: running auto installation service for kernel 2.6.38-16-generic                                                                                
  *       virtualbox-ose (4.0.4)...                                  [ OK ]  
  *       fglrx (8.840)...                                           [ OK ]  
 Setting up linux-headers-generic (2.6.38.16.31) ...  
 mar@ubuntu:~$ sudo apt-get update  
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty InRelease  
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates InRelease                   
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release.gpg                         
 Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release.gpg [198 B]       
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release                             
 Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release [39.8 kB]         
 Ign [http://www.geekconnection.org](http://www.geekconnection.org) karmic/ InRelease                        
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Sources                        
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Sources                  
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Sources               
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Sources             
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main amd64 Packages            
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted amd64 Packages      
 Ign [http://archive.canonical.com](http://archive.canonical.com) natty InRelease                      
 Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease               
 Ign [http://www.geekconnection.org](http://www.geekconnection.org) karmic/ Release.gpg                 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe amd64 Packages        
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse amd64 Packages      
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main TranslationIndex          
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse TranslationIndex    
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted TranslationIndex    
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe TranslationIndex      
 Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Sources [173 kB]  
 Ign [http://www.geekconnection.org](http://www.geekconnection.org) karmic/ Release                          
 Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release.gpg                         
 Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg [198 B]        
 Ign [http://www.geekconnection.org](http://www.geekconnection.org) karmic/ Packages/DiffIndex               
 Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release                             
 Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release [39.8 kB]          
 Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Sources [2,116 B]  
 Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Sources [52.2 kB]  
 Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Sources [3,107 B]  
 Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main amd64 Packages [501 kB]  
 Hit [http://archive.canonical.com](http://archive.canonical.com) natty/partner amd64 Packages              
 Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner TranslationIndex            
 Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources [111 kB]     
 Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted amd64 Packages [6,240 B]  
 Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe amd64 Packages [164 kB]  
 Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse amd64 Packages [6,360 B]  
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main TranslationIndex       
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse TranslationIndex  
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted TranslationIndex  
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe TranslationIndex   
 Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources [1,303 B]  
 Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources [30.8 kB]  
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en_US              
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en                 
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en_US  
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en  
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en_US  
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en  
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en_US  
 Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources [1,631 B]  
 Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main amd64 Packages [369 kB]  
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en             
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en_US      
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en         
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en_US  
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en  
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en_US  
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en  
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en_US  
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en  
 Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en_US  
 Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en  
 Hit [http://www.geekconnection.org](http://www.geekconnection.org) karmic/ Packages  
 Ign [http://www.geekconnection.org](http://www.geekconnection.org) karmic/ Translation-en_US  
 Ign [http://www.geekconnection.org](http://www.geekconnection.org) karmic/ Translation-en  
 Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted amd64 Packages [4,778 B]  
 Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe amd64 Packages [103 kB]  
 Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse amd64 Packages [3,546 B]  
 Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main TranslationIndex  
 Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse TranslationIndex  
 Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted TranslationIndex  
 Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe TranslationIndex  
 Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en_US  
 Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en  
 Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en_US  
 Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en  
 Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en_US  
 Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en  
 Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en_US  
 Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en  
 Fetched 1,613 kB in 4s (374 kB/s)  
 Reading package lists... Done  
 mar@ubuntu:~$  
 mar@ubuntu:~$ wget [http://media.cdn.ubuntu-de.org/forum...92_dkms.tar.gz](http://media.cdn.ubuntu-de.org/forum...92_dkms.tar.gz)  
 --2012-10-06 11:10:00--  [http://media.cdn.ubuntu-de.org/forum...92_dkms.tar.gz](http://media.cdn.ubuntu-de.org/forum...92_dkms.tar.gz)  
 Resolving media.cdn.ubuntu-de.org... 213.95.41.13, 2001:780:0:25:206:5bff:fe04:8bcb  
 Connecting to media.cdn.ubuntu-de.org|213.95.41.13|:80... connected.  
 HTTP request sent, awaiting response... 404 Not Found  
 2012-10-06 11:10:00 ERROR 404: Not Found.  
 

 mar@ubuntu:~$ sudo tar xvf 2844083-rtl8192cu-3.3.23192_dkms.tar.gz -C /usr/src  
 tar: 2844083-rtl8192cu-3.3.23192_dkms.tar.gz: Cannot open: No such file or directory  
 tar: Error is not recoverable: exiting now  
 mar@ubuntu:~$ sudo dkms add -m rtl8192cu -v 3.3.23192  
 

 Error! Could not find module source directory.  
 Directory: /usr/src/rtl8192cu-3.3.23192 does not exist.  
 mar@ubuntu:~$ sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms  
 Reading package lists... Done  
 Building dependency tree        
 Reading state information... Done  
 0 upgraded, 0 newly installed, 4 reinstalled, 0 to remove and 8 not upgraded.  
 Need to get 0 B/915 kB of archives.  
 After this operation, 0 B of additional disk space will be used.  
 (Reading database ... 144351 files and directories currently installed.)  
 Preparing to replace build-essential 11.5ubuntu1 (using .../build-essential_11.5ubuntu1_amd64.deb) ...  
 Unpacking replacement build-essential ...  
 Preparing to replace dkms 2.1.1.2-5ubuntu1 (using .../dkms_2.1.1.2-5ubuntu1_all.deb) ...  
 Unpacking replacement dkms ...  
 Preparing to replace linux-headers-2.6.38-16-generic 2.6.38-16.67 (using .../linux-headers-2.6.38-16-generic_2.6.38-16.67_amd64.deb) ...  
 Unpacking replacement linux-headers-2.6.38-16-generic ...  
 Preparing to replace linux-headers-generic 2.6.38.16.31 (using .../linux-headers-generic_2.6.38.16.31_amd64.deb) ...  
 Unpacking replacement linux-headers-generic ...  
 Processing triggers for man-db ...  
 Setting up build-essential (11.5ubuntu1) ...  
 Setting up dkms (2.1.1.2-5ubuntu1) ...  
 Setting up linux-headers-2.6.38-16-generic (2.6.38-16.67) ...  
 Examining /etc/kernel/header_postinst.d.  
 run-parts: executing /etc/kernel/header_postinst.d/dkms 2.6.38-16-generic /boot/vmlinuz-2.6.38-16-generic  
  * dkms: running auto installation service for kernel 2.6.38-16-generic                                                                                
  *       virtualbox-ose (4.0.4)...                                  [ OK ]  
  *       fglrx (8.840)...                                           [ OK ]  
 Setting up linux-headers-generic (2.6.38.16.31) ...  
 mar@ubuntu:~$  
 mar@ubuntu:~$ sudo gedit /etc/rc.local  
 

 mar@ubuntu:~$  
 mar@ubuntu:~$  
 mar@ubuntu:~$ apt-get update  
 E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)  
 E: Unable to lock directory /var/lib/apt/lists/  
 E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)  
 E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?  
 mar@ubuntu:~$

---

### Post by critin on 2012-10-06
> One more thing, the last part where i supposed to copy the **two lines  above the exi**t, well, they have "#" starting from the beginning, should i  have added # in front of those two lines? I did not. I just followed  instructions but just intuitive thoughts that i should ask after all i  don't have all that knowledge on ubuntu yet.
Once again, thank you.

If you copy/paste, copy exactly.  Those "#" hash marks mean the line is information for the user.  It will not be used by terminal.  That means they are 'commented out'.  I don't know which lines you mean though.  There are about four/five sections with ending exits--new logins.

The last lines==
> 
Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)  
 E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?  I see this when I have another install directory open.  Software Center, Synaptic or terminal.     There can be only one running at a time.  If you don't have another open, I don't know else it is.

---

### Post by Marthewicked on 2012-10-06
This is the two line i was referring to,

                                  sudo gedit /etc/rc.local Right above exit 0 add these two lines:
  Code:
 modprobe rtl8192cu Code:
  echo "0b05 17ab" > /sys/bus/usb/drivers/rtl8192cu/new_id  

Oh and i only had the terminal open nothing else. I am still not connected though or don't even see the usb adapter.
Anything im missing out?

---

### Post by Marthewicked on 2012-10-06
I don't get this part, this should be found on directory though yes? Isn't this what i was downloaded? The files for the drivers?

 Error! Could not find module source directory.  
 Directory: /usr/src/rtl8192cu-3.3.23192 does not exist.

---

### Post by steeldriver on 2012-10-06
It looks like your wget failed (maybe because the link got truncated when you copied + pasted it?) try again with

```
wget media.cdn.ubuntu-de.org/forum/attachments/32/20/2844083-rtl8192cu-3.3.23192_dkms.tar.gz
```

> **Marthewicked said:**
> 
 mar@ubuntu:~$ wget [http://media.cdn.ubuntu-de.org/forum...92_dkms.tar.gz](http://media.cdn.ubuntu-de.org/forum...92_dkms.tar.gz)  
 --2012-10-06 11:10:00--  [http://media.cdn.ubuntu-de.org/forum...92_dkms.tar.gz](http://media.cdn.ubuntu-de.org/forum...92_dkms.tar.gz)  
 Resolving media.cdn.ubuntu-de.org... 213.95.41.13, 2001:780:0:25:206:5bff:fe04:8bcb  
 Connecting to media.cdn.ubuntu-de.org|213.95.41.13|:80... connected.  
 [COLOR=Red][B]HTTP request sent, awaiting response... 404 Not Found  
[/B]  [/COLOR]2012-10-06 11:10:00 ERROR 404: Not Found.  
 

 mar@ubuntu:~$ sudo tar xvf 2844083-rtl8192cu-3.3.23192_dkms.tar.gz -C /usr/src  
 [COLOR=Red][B]tar: 2844083-rtl8192cu-3.3.23192_dkms.tar.gz: Cannot open: No such file or directory  
 tar: Error is not recoverable: exiting now  
[/B]  [/COLOR]mar@ubuntu:~$ sudo dkms add -m rtl8192cu -v 3.3.23192  
 

 [B][COLOR=Red]Error! Could not find module source directory.  
 Directory: /usr/src/rtl8192cu-3.3.23192 does not exist.  
[/COLOR][/B]

---

### Post by Marthewicked on 2012-10-06
Ok. Now i have run it again and it downloaded link. I supposed to get update afterwards im only guessing this part. What is next now?


This is getting fun, frustrated but without disappointments you cant appreciate victory right?




mar@ubuntu:~$ wget media.cdn.ubuntu-de.org/forum/attachments/32/20/2844083-rtl8192cu-3.3.23192_dkms.tar.gz 
 --2012-10-06 14:14:28--  [http://media.cdn.ubuntu-de.org/forum/attachments/32/20/2844083-rtl8192cu-3.3.23192_dkms.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/32/20/2844083-rtl8192cu-3.3.23192_dkms.tar.gz) 
 Resolving media.cdn.ubuntu-de.org... 213.95.41.13, 2001:780:0:25:206:5bff:fe04:8bcb  
 Connecting to media.cdn.ubuntu-de.org|213.95.41.13|:80... connected.  
 HTTP request sent, awaiting response... 200 OK  
 Length: 1202618 (1.1M) [application/octet-stream]  
 Saving to: `2844083-rtl8192cu-3.3.23192_dkms.tar.gz'  
 

 100%[=================================>] 1,202,618    562K/s   in 2.1s     
 

 2012-10-06 14:14:30 (562 KB/s) - `2844083-rtl8192cu-3.3.23192_dkms.tar.gz' saved [1202618/1202618]  
 

 mar@ubuntu:~$ get-apt update  
 get-apt: command not found  
 mar@ubuntu:~$ apt-get update  
 E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)  
 E: Unable to lock directory /var/lib/apt/lists/  
 E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)  
 E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?  
 mar@ubuntu:~$

---

### Post by steeldriver on 2012-10-06
Hi, I didn't post the original instructions but since the original wget failed to retrieve the source tar, I think that everything you did after that needs to be done over again, i.e. 

1. unpack the tar archive into the /usr/src directory

```
sudo tar xvf 2844083-rtl8192cu-3.3.23192_dkms.tar.gz -C /usr/src 
```2. add, build, and install the dkms module

```
sudo dkms add -m rtl8192cu -v 3.3.23192 
sudo dkms build -m rtl8192cu -v 3.3.23192 
sudo dkms install -m rtl8192cu -v 3.3.23192

```If that completes successfully (check for error messages this time!) then you can go ahead and modify your rc.local file

Hope this helps

EDIT: also remember you need 'sudo' permission to apt-get things - that is the cause of your most recent error

---

### Post by Marthewicked on 2012-10-06
hehe i figured that. My last post was just not wise post. but like you said i redid the instructions daslinkard gave and here are the posts update

  	 	 	 	 	 	   mar@ubuntu:~$ sudo tar xvf 2844083-rtl8192cu-3.3.23192_dkms.tar.gz -C /usr/src  
 [sudo] password for mar:  
 rtl8192cu-3.3.23192/  
 rtl8192cu-3.3.23192/src/  
 rtl8192cu-3.3.23192/src/os_dep/  
 rtl8192cu-3.3.23192/src/include/  
 rtl8192cu-3.3.23192/src/hal/  
 rtl8192cu-3.3.23192/src/core/  
 rtl8192cu-3.3.23192/src/os_dep/linux/  
 rtl8192cu-3.3.23192/src/include/byteorder/ 
 rtl8192cu-3.3.23192/src/hal/rtl8192d/  
 rtl8192cu-3.3.23192/src/hal/rtl8192c/  
 rtl8192cu-3.3.23192/src/core/efuse/  
 rtl8192cu-3.3.23192/src/hal/rtl8192d/usb/ 
 rtl8192cu-3.3.23192/src/hal/rtl8192c/usb/ 
 rtl8192cu-3.3.23192/Makefile  
 rtl8192cu-3.3.23192/dkms.conf  
 rtl8192cu-3.3.23192/src/wlan0dhcp  
 rtl8192cu-3.3.23192/src/Makefile  
 rtl8192cu-3.3.23192/src/make_drv  
 rtl8192cu-3.3.23192/src/Kconfig  
 rtl8192cu-3.3.23192/src/ifcfg-wlan0  
 rtl8192cu-3.3.23192/src/clean  
 rtl8192cu-3.3.23192/src/autoconf_rtl8192d_usb_linux.h 
 rtl8192cu-3.3.23192/src/autoconf_rtl8192c_usb_linux.h 
 rtl8192cu-3.3.23192/src/os_dep/osdep_service.c 
 rtl8192cu-3.3.23192/src/include/rtw_ioctl.h 
 rtl8192cu-3.3.23192/src/include/rtw_mp.h 
 rtl8192cu-3.3.23192/src/include/rtl8192c_sreset.h 
 rtl8192cu-3.3.23192/src/include/xmit_osdep.h 
 rtl8192cu-3.3.23192/src/include/if_ether.h 
 rtl8192cu-3.3.23192/src/include/rtw_led.h 
 rtl8192cu-3.3.23192/src/include/ip.h  
 rtl8192cu-3.3.23192/src/include/rtl8192c_hal.h 
 rtl8192cu-3.3.23192/src/include/basic_types.h 
 rtl8192cu-3.3.23192/src/include/circ_buf.h 
 rtl8192cu-3.3.23192/src/include/rtw_br_ext.h 
 rtl8192cu-3.3.23192/src/include/Hal8192DPhyReg.h 
 rtl8192cu-3.3.23192/src/include/rtw_io.h 
 rtl8192cu-3.3.23192/src/include/sdio_hal.h 
 rtl8192cu-3.3.23192/src/include/rtw_security.h 
 rtl8192cu-3.3.23192/src/include/autoconf.h 
 rtl8192cu-3.3.23192/src/include/usb_hal.h 
 rtl8192cu-3.3.23192/src/include/rtw_rf.h 
 rtl8192cu-3.3.23192/src/include/rtw_mp_phy_regdef.h 
 rtl8192cu-3.3.23192/src/include/rtw_iol.h 
 rtl8192cu-3.3.23192/src/include/sta_info.h 
 rtl8192cu-3.3.23192/src/include/osdep_intf.h 
 rtl8192cu-3.3.23192/src/include/rtw_debug.h 
 rtl8192cu-3.3.23192/src/include/mlme_osdep.h 
 rtl8192cu-3.3.23192/src/include/rtw_event.h 
 rtl8192cu-3.3.23192/src/include/rtl8192c_cmd.h 
 rtl8192cu-3.3.23192/src/include/pci_ops.h 
 rtl8192cu-3.3.23192/src/include/rtl8192d_rf.h 
 rtl8192cu-3.3.23192/src/include/rtw_cmd.h 
 rtl8192cu-3.3.23192/src/include/pci_osintf.h 
 rtl8192cu-3.3.23192/src/include/h2clbk.h 
 rtl8192cu-3.3.23192/src/include/rtw_ioctl_set.h 
 rtl8192cu-3.3.23192/src/include/rtl8192d_cmd.h 
 rtl8192cu-3.3.23192/src/include/rtw_version.h 
 rtl8192cu-3.3.23192/src/include/rtl8192d_xmit.h 
 rtl8192cu-3.3.23192/src/include/rtw_byteorder.h 
 rtl8192cu-3.3.23192/src/include/drv_types_xp.h 
 rtl8192cu-3.3.23192/src/include/rtw_eeprom.h 
 rtl8192cu-3.3.23192/src/include/rtw_ioctl_query.h 
 rtl8192cu-3.3.23192/src/include/osdep_service.h 
 rtl8192cu-3.3.23192/src/include/usb_vendor_req.h 
 rtl8192cu-3.3.23192/src/include/drv_conf.h 
 rtl8192cu-3.3.23192/src/include/pci_hal.h 
 rtl8192cu-3.3.23192/src/include/rtw_p2p.h 
 rtl8192cu-3.3.23192/src/include/Hal8192CEHWImg.h 
 rtl8192cu-3.3.23192/src/include/sdio_osintf.h 
 rtl8192cu-3.3.23192/src/include/Hal8192DETestHWImg.h 
 rtl8192cu-3.3.23192/src/include/sdio_ops_xp.h 
 rtl8192cu-3.3.23192/src/include/rtw_mp_ioctl.h 
 rtl8192cu-3.3.23192/src/include/rtl8192d_led.h 
 rtl8192cu-3.3.23192/src/include/Hal8192CPhyCfg.h 
 rtl8192cu-3.3.23192/src/include/drv_types_ce.h 
 rtl8192cu-3.3.23192/src/include/ieee80211_ext.h 
 rtl8192cu-3.3.23192/src/include/Hal8192DEHWImg.h 
 rtl8192cu-3.3.23192/src/include/drv_types.h 
 rtl8192cu-3.3.23192/src/include/hal_init.h 
 rtl8192cu-3.3.23192/src/include/rtw_mlme.h 
 rtl8192cu-3.3.23192/src/include/rtl8192c_spec.h 
 rtl8192cu-3.3.23192/src/include/Hal8192DUHWImg.h 
 rtl8192cu-3.3.23192/src/include/sdio_ops_linux.h 
 rtl8192cu-3.3.23192/src/include/rtw_ioctl_rtl.h 
 rtl8192cu-3.3.23192/src/include/mp_custom_oid.h 
 rtl8192cu-3.3.23192/src/include/ethernet.h 
 rtl8192cu-3.3.23192/src/include/rtw_ht.h 
 rtl8192cu-3.3.23192/src/include/usb_ops.h 
 rtl8192cu-3.3.23192/src/include/Hal8192DUTestHWImg.h 
 rtl8192cu-3.3.23192/src/include/sdio_ops_ce.h 
 rtl8192cu-3.3.23192/src/include/Hal8192CUHWImg.h 
 rtl8192cu-3.3.23192/src/include/rtw_efuse.h 
 rtl8192cu-3.3.23192/src/include/drv_types_linux.h 
 rtl8192cu-3.3.23192/src/include/recv_osdep.h 
 rtl8192cu-3.3.23192/src/include/ieee80211.h 
 rtl8192cu-3.3.23192/src/include/sdio_ops.h 
 rtl8192cu-3.3.23192/src/include/osdep_ce_service.h 
 rtl8192cu-3.3.23192/src/include/rtl8192d_spec.h 
 rtl8192cu-3.3.23192/src/include/rtl8192c_xmit.h 
 rtl8192cu-3.3.23192/src/include/rtw_pwrctrl.h 
 rtl8192cu-3.3.23192/src/include/rtw_qos.h 
 rtl8192cu-3.3.23192/src/include/rtl8192c_event.h 
 rtl8192cu-3.3.23192/src/include/rtw_xmit.h 
 rtl8192cu-3.3.23192/src/include/rtl8192d_dm.h 
 rtl8192cu-3.3.23192/src/include/usb_osintf.h 
 rtl8192cu-3.3.23192/src/include/nic_spec.h 
 rtl8192cu-3.3.23192/src/include/rtl8192c_recv.h 
 rtl8192cu-3.3.23192/src/include/rtl8192c_rf.h 
 rtl8192cu-3.3.23192/src/include/rtl8192c_dm.h 
 rtl8192cu-3.3.23192/src/include/rtl8192d_hal.h 
 rtl8192cu-3.3.23192/src/include/Hal8192DPhyCfg.h 
 rtl8192cu-3.3.23192/src/include/Hal8192CPhyReg.h 
 rtl8192cu-3.3.23192/src/include/farray.h 
 rtl8192cu-3.3.23192/src/include/rtl8192d_recv.h 
 rtl8192cu-3.3.23192/src/include/rtl8192c_led.h 
 rtl8192cu-3.3.23192/src/include/wifi.h  
 rtl8192cu-3.3.23192/src/include/rtw_mlme_ext.h 
 rtl8192cu-3.3.23192/src/include/rtw_recv.h 
 rtl8192cu-3.3.23192/src/include/cmd_osdep.h 
 rtl8192cu-3.3.23192/src/include/wlan_bssdef.h 
 rtl8192cu-3.3.23192/src/hal/hal_init.c  
 rtl8192cu-3.3.23192/src/core/rtw_iol.c  
 rtl8192cu-3.3.23192/src/core/rtw_ioctl_set.c 
 rtl8192cu-3.3.23192/src/core/rtw_mp_ioctl.c 
 rtl8192cu-3.3.23192/src/core/rtw_ioctl_rtl.c 
 rtl8192cu-3.3.23192/src/core/rtw_io.c  
 rtl8192cu-3.3.23192/src/core/rtw_mlme_ext.c 
 rtl8192cu-3.3.23192/src/core/rtw_wlan_util.c 
 rtl8192cu-3.3.23192/src/core/rtw_pwrctrl.c 
 rtl8192cu-3.3.23192/src/core/rtw_rf.c  
 rtl8192cu-3.3.23192/src/core/rtw_sta_mgt.c 
 rtl8192cu-3.3.23192/src/core/rtw_mp.c  
 rtl8192cu-3.3.23192/src/core/rtw_mlme.c 
 rtl8192cu-3.3.23192/src/core/rtw_cmd.c  
 rtl8192cu-3.3.23192/src/core/rtw_security.c 
 rtl8192cu-3.3.23192/src/core/rtw_ieee80211.c 
 rtl8192cu-3.3.23192/src/core/rtw_p2p.c  
 rtl8192cu-3.3.23192/src/core/rtw_debug.c 
 rtl8192cu-3.3.23192/src/core/rtw_eeprom.c 
 rtl8192cu-3.3.23192/src/core/rtw_br_ext.c 
 rtl8192cu-3.3.23192/src/core/rtw_recv.c 
 rtl8192cu-3.3.23192/src/core/rtw_ioctl_query.c 
 rtl8192cu-3.3.23192/src/core/rtw_xmit.c 
 rtl8192cu-3.3.23192/src/os_dep/linux/xmit_linux.c 
 rtl8192cu-3.3.23192/src/os_dep/linux/sdio_intf.c 
 rtl8192cu-3.3.23192/src/os_dep/linux/pci_intf.c 
 rtl8192cu-3.3.23192/src/os_dep/linux/mlme_linux.c 
 rtl8192cu-3.3.23192/src/os_dep/linux/usb_intf.c 
 rtl8192cu-3.3.23192/src/os_dep/linux/os_intfs.c 
 rtl8192cu-3.3.23192/src/os_dep/linux/recv_linux.c 
 rtl8192cu-3.3.23192/src/os_dep/linux/ioctl_linux.c 
 rtl8192cu-3.3.23192/src/include/byteorder/generic.h 
 rtl8192cu-3.3.23192/src/include/byteorder/little_endian.h 
 rtl8192cu-3.3.23192/src/include/byteorder/big_endian.h 
 rtl8192cu-3.3.23192/src/include/byteorder/swabb.h 
 rtl8192cu-3.3.23192/src/include/byteorder/swab.h 
 rtl8192cu-3.3.23192/src/hal/rtl8192d/rtl8192d_hal_init.c 
 rtl8192cu-3.3.23192/src/hal/rtl8192d/rtl8192d_rf6052.c 
 rtl8192cu-3.3.23192/src/hal/rtl8192d/rtl8192d_dm.c 
 rtl8192cu-3.3.23192/src/hal/rtl8192d/rtl8192d_mp.c 
 rtl8192cu-3.3.23192/src/hal/rtl8192d/rtl8192d_phycfg.c 
 rtl8192cu-3.3.23192/src/hal/rtl8192d/rtl8192d_cmd.c 
 rtl8192cu-3.3.23192/src/hal/rtl8192d/rtl8192d_rxdesc.c 
 rtl8192cu-3.3.23192/src/hal/rtl8192c/rtl8192c_hal_init.c 
 rtl8192cu-3.3.23192/src/hal/rtl8192c/rtl8192c_sreset.c 
 rtl8192cu-3.3.23192/src/hal/rtl8192c/rtl8192c_rf6052.c 
 rtl8192cu-3.3.23192/src/hal/rtl8192c/rtl8192c_rxdesc.c 
 rtl8192cu-3.3.23192/src/hal/rtl8192c/rtl8192c_mp.c 
 rtl8192cu-3.3.23192/src/hal/rtl8192c/rtl8192c_dm.c 
 rtl8192cu-3.3.23192/src/hal/rtl8192c/rtl8192c_phycfg.c 
 rtl8192cu-3.3.23192/src/hal/rtl8192c/rtl8192c_cmd.c 
 rtl8192cu-3.3.23192/src/core/efuse/rtw_efuse.c 
 rtl8192cu-3.3.23192/src/hal/rtl8192d/usb/usb_ops_linux.c 
 rtl8192cu-3.3.23192/src/hal/rtl8192d/usb/rtl8192du_led.c 
 rtl8192cu-3.3.23192/src/hal/rtl8192d/usb/Hal8192DUHWImg.c 
 rtl8192cu-3.3.23192/src/hal/rtl8192d/usb/rtl8192du_xmit.c 
 rtl8192cu-3.3.23192/src/hal/rtl8192d/usb/usb_halinit.c 
 rtl8192cu-3.3.23192/src/hal/rtl8192d/usb/rtl8192du_recv.c 
 rtl8192cu-3.3.23192/src/hal/rtl8192d/usb/Hal8192DUTestHWImg.c 
 rtl8192cu-3.3.23192/src/hal/rtl8192c/usb/usb_ops_xp.c 
 rtl8192cu-3.3.23192/src/hal/rtl8192c/usb/rtl8192cu_xmit.c 
 rtl8192cu-3.3.23192/src/hal/rtl8192c/usb/usb_ops_linux.c 
 rtl8192cu-3.3.23192/src/hal/rtl8192c/usb/Hal8192CUHWImg.c 
 rtl8192cu-3.3.23192/src/hal/rtl8192c/usb/usb_ops_ce.c 
 rtl8192cu-3.3.23192/src/hal/rtl8192c/usb/rtl8192cu_recv.c 
 rtl8192cu-3.3.23192/src/hal/rtl8192c/usb/usb_halinit.c 
 rtl8192cu-3.3.23192/src/hal/rtl8192c/usb/rtl8192cu_led.c 
 mar@ubuntu:~$ sudo dkms add -m rtl8192cu -v 3.3.23192  
 

 Creating symlink /var/lib/dkms/rtl8192cu/3.3.23192/source ->  
                  /usr/src/rtl8192cu-3.3.23192  
 

 DKMS: add Completed.  
 mar@ubuntu:~$ sudo dkms build -m rtl8192cu -v 3.3.23192  
 

 Kernel preparation unnecessary for this kernel.  Skipping...  
 

 Building module:  
 cleaning build area....  
 'make' -C src/ all................  
 cleaning build area....  
 

 DKMS: build Completed.  
 mar@ubuntu:~$ sudo dkms install -m rtl8192cu -v 3.3.23192  
 

 8192cu.ko:  
 Running module version sanity check.  
  - Original module  
    - No original module exists within this kernel  
  - Installation  
    - Installing to /lib/modules/2.6.38-16-generic/updates/dkms/  
 

 depmod......  
 

 DKMS: install Completed.  
 mar@ubuntu:~$ sudo gedit /etc/rc.local  
 mar@ubuntu:~$

---

### Post by Marthewicked on 2012-10-06
Awesome. I did reboot while the usb was connected and BAM! it automatically connected to my wifi. Awesome! I thank you guys so much!

I have one more quick simple question, can anyone explain it to me what each code means in case i have to download another driver or anything of that sort of thing? I will have to know sooner or later because im not going back to windows, no way! This is fun!

Once again thank you to each and everyone who helped. I promise once i get to learn those specific codes i will pass the help.

---

### Post by Marthewicked on 2012-10-06
One little problem, when i unplug the asus n13 thinking that internet will be disconnected, well the whole screen goes black with white codes filled the whole page. No response unless i turn it off and turn back on. Is this symptom weird or it supposed to do that?
I am not going to unplug again but thought i should ask before i put this question solved.



I also have Tenda wu322u v2.0  and it works with whatever i did with the installation. I can see my network and such but there are few things i have to figure out like

Wireless Network Authentication Required window 
WEB 40/128- bit key....
WEB 128-bit key
LEAP
Dynamic Web 802.1x

I don't this part but i can try it all to see which works but the important thing is that this adapter works and it was not working before that is why i bought the asus thinking it is plug and play and i was wrong.

---

### Post by Marthewicked on 2012-10-06
I cheated the set up from laptop since laptop has ubuntu as well. I have the Tenda w322u v2.0 working as well after setting up and adding the wireless to the desktop. I can unplug and plug back in and like i expected disconnects wireless but does not go crazy like the asus n13. If anyone has any idea about that.

And i mean go crazy, the screen gets no response, black background with white terminal code letters from top of the screen to bottom of the screen. There is no way to get out of it unless i turn it off.

---

### Post by daslinkard on 2012-10-07
> **Marthewicked said:**
> I cheated the set up from laptop since laptop has ubuntu as well. I have the Tenda w322u v2.0 working as well after setting up and adding the wireless to the desktop. I can unplug and plug back in and like i expected disconnects wireless but does not go crazy like the asus n13. If anyone has any idea about that.

And i mean go crazy, the screen gets no response, black background with white terminal code letters from top of the screen to bottom of the screen. There is no way to get out of it unless i turn it off.
I will be following up with this later on today to see if I can get a solution for you!

---

### Post by daslinkard on 2012-10-07
I've been searching Google and various forums trying to find answers but I am drawing a blank....I'm not giving up but if anyone out there has a solution I would love to have it here.  In the mean time I will keep trying...

---

### Post by Marthewicked on 2012-10-07
Thanks. For now i can have it plugged and keep it plugged so i don't have that issue. The main thing was to have the drivers installed and surf. I am surfing now and doing few stunts ;-)
Thank you again.

---

### Post by daslinkard on 2012-10-07
> **Marthewicked said:**
> Thanks. For now i can have it plugged and keep it plugged so i don't have that issue. The main thing was to have the drivers installed and surf. I am surfing now and doing few stunts ;-)
Thank you again.
No worries at all!

---

### Post by Marthewicked on 2012-10-08
> **daslinkard said:**
> No worries at all!
this might be pain the what.  I thought i should upgrade to 11.10 but very not wise idea. Anyway, upgraded and it boots but black screen with the n13 i will post pics on those codes. But boots up fine without the USB n13 asus. ii plug it in and bam same thing. I could not go back to 11.04, i dont know if possible. Long story short i decided to start clean install 12.04 LTS. Now, the driver connects but i have to find my wireless under hidden wireless and create then save but it never connects. It wil keep as king passcode/key and it is all correct but never connect. So once again back to zero again but im connected with my phone tethering thank god.

here is a basic info again.....

lshw

mar@mar-Vostro-200:~$ lshw
WARNING: you should run this program as super-user.
mar-vostro-200            
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 2002MiB
     *-cpu
          product: Intel(R) Pentium(R) Dual  CPU  E2140  @ 1.60GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.15.13
          serial: 0000-06FD-0000-0000-0000-0000
          size: 1200MHz
          capacity: 1200MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm cpufreq
          configuration: id=1
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 64 bits
             capabilities: logical
     *-pci
          description: Host bridge
          product: 82G33/G31/P35/P31 Express DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-pci:0
             description: PCI bridge
             product: 82G33/G31/P35/P31 Express PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:d000(size=4096) memory:fda00000-fdafffff ioport:fdb00000(size=1048576)
        *-display
             description: VGA compatible controller
             product: 82G33/G31 Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:43 memory:fdf00000-fdf7ffff ioport:ff00(size=8) memory:d0000000-dfffffff memory:fdc00000-fdcfffff
        *-network
             description: Ethernet interface
             product: 82562V-2 10/100 Network Connection
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             logical name: eth0
             version: 02
             serial: 00:1a:a0:9e:e1:2e
             capacity: 100Mbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.5.1-k firmware=1.1-2 latency=0 multicast=yes port=twisted pair
             resources: irq:42 memory:fdfc0000-fdfdffff memory:fdfff000-fdffffff ioport:fe00(size=32)
        *-usb:0
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:fd00(size=32)
        *-usb:1
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:fc00(size=32)
        *-usb:2
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #6
             vendor: Intel Corporation
             physical id: 1a.2
             bus info: pci@0000:00:1a.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:fb00(size=32)
        *-usb:3
             description: USB controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:18 memory:fdffe000-fdffe3ff
        *-multimedia
             description: Audio device
             product: 82801I (ICH9 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:44 memory:fdff4000-fdff7fff
        *-usb:4
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:fa00(size=32)
        *-usb:5
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:f900(size=32)
        *-usb:6
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:f800(size=32)
        *-usb:7
             description: USB controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:fdffd000-fdffd3ff
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 92
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: ioport:c000(size=4096) memory:fde00000-fdefffff ioport:fdd00000(size=1048576)
           *-communication UNCLAIMED
                description: Communication controller
                product: HSF 56k Data/Fax Modem
                vendor: Conexant Systems, Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=0
                resources: memory:fdef0000-fdefffff ioport:cf00(size=8)
        *-isa
             description: ISA bridge
             product: 82801IR (ICH9R) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: RAID bus controller
             product: 82801 SATA Controller [RAID mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: storage bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:41 ioport:f700(size=8) ioport:f600(size=4) ioport:f500(size=8) ioport:f400(size=4) ioport:f300(size=32) memory:fdffc000-fdffc7ff
        *-serial UNCLAIMED
             description: SMBus
             product: 82801I (ICH9 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:fdffb000-fdffb0ff ioport:500(size=32)
  *-network:0
       description: Ethernet interface
       physical id: 1
       logical name: usb0
       serial: 02:79:33:34:30:3c
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device ip=192.168.42.43 multicast=yes
  *-network:1
       description: Wireless interface
       physical id: 2
       bus info: usb@2:2
       logical name: wlan0
       serial: c8:60:00:d4:9e:86
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192cu driverversion=3.2.0-29-generic-pae firmware=N/A multicast=yes wireless=IEEE 802.11bgn
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
mar@mar-Vostro-200:~$ modinfo rtl8192cu | grep -e modules -e 17AB
filename:       /lib/modules/3.2.0-29-generic-pae/kernel/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko
alias:          usb:v0B05p17ABd*dc*dsc*dp*ic*isc*ip*
mar@mar-Vostro-200:~$ 

i will post those images after this post

here is lsusb

mar@mar-Vostro-200:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 0b05:17ab ASUSTek Computer, Inc. 
Bus 001 Device 004: ID 04e8:6864 Samsung Electronics Co., Ltd 
Bus 006 Device 002: ID 04d9:a01c Holtek Semiconductor, Inc.

---

### Post by daslinkard on 2012-10-08
Check out this [link]("http://askubuntu.com/questions/186829/wireless-not-working-on-desktop-with-asus-usb-n13-b1-wireless-adapter") and let's see if it can get you headed in the right direction...

---

### Post by daslinkard on 2012-10-08
Also I am wondering about this [link]("http://ubuntuforums.org/showthread.php?t=2032976") primarily with the suggestion of dumping network manager for wicd.

The commands suggested to do this are as follows:
```
sudo apt-get install wicd
``````

sudo apt-get purge network-manager
```

---

### Post by Marthewicked on 2012-10-08
my wireless is not blocked but i ran that anyway and it is running yet still no connection. i did not install drivers since i connected the 12.04, should i do it anyway to see if it works?

mar@mar-Vostro-200:~$ rfkill list all
4: phy4: Wireless LAN
    Soft blocked: no
    Hard blocked: no
mar@mar-Vostro-200:~$ rfkill unblock all
mar@mar-Vostro-200:~$ sudo service network-manager restart
[sudo] password for mar: 
network-manager stop/waiting
network-manager start/running, process 3097
mar@mar-Vostro-200:~$ 

when did this it said connection established i think im still connected to internet with phone though. i will check again after i post without phone connection

---

### Post by Marthewicked on 2012-10-08
> **Marthewicked said:**
> my wireless is not blocked but i ran that anyway and it is running yet still no connection. i did not install drivers since i connected the 12.04, should i do it anyway to see if it works?

mar@mar-Vostro-200:~$ rfkill list all
4: phy4: Wireless LAN
    Soft blocked: no
    Hard blocked: no
mar@mar-Vostro-200:~$ rfkill unblock all
mar@mar-Vostro-200:~$ sudo service network-manager restart
[sudo] password for mar: 
network-manager stop/waiting
network-manager start/running, process 3097
mar@mar-Vostro-200:~$ 

when did this it said connection established i think im still connected to internet with phone though. i will check again after i post without phone connection

Oh just the phone connection disconnected and reconnected. but i will try your codes now.

---

### Post by Marthewicked on 2012-10-08
> **daslinkard said:**
> Also I am wondering about this [link]("http://ubuntuforums.org/showthread.php?t=2032976") primarily with the suggestion of dumping network manager for wicd.

The commands suggested to do this are as follows:
```
sudo apt-get install wicd
``````

sudo apt-get purge network-manager
```

the purge network is MIA it can not locate it.

here

mar@mar-Vostro-200:~$ sudo apt-get install wicd
[sudo] password for mar: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libglade2-0 python-glade2 python-wicd wicd-daemon wicd-gtk
Suggested packages:
  python-gtk2-doc
The following NEW packages will be installed:
  libglade2-0 python-glade2 python-wicd wicd wicd-daemon wicd-gtk
0 upgraded, 6 newly installed, 0 to remove and 138 not upgraded.
Need to get 453 kB of archives.
After this operation, 3,073 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main libglade2-0 i386 1:2.6.4-1ubuntu1.1 [52.6 kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/universe python-wicd all 1.7.2.3-1ubuntu0.1 [39.9 kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/universe wicd-daemon all 1.7.2.3-1ubuntu0.1 [239 kB]
Get:4 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main python-glade2 i386 2.24.0-3 [9,870 B]
Get:5 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/universe wicd-gtk all 1.7.2.3-1ubuntu0.1 [108 kB]
Get:6 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/universe wicd all 1.7.2.3-1ubuntu0.1 [4,434 B]
Fetched 453 kB in 0s (878 kB/s) 
Preconfiguring packages ...
Selecting previously unselected package libglade2-0.
(Reading database ... 141047 files and directories currently installed.)
Unpacking libglade2-0 (from .../libglade2-0_1%3a2.6.4-1ubuntu1.1_i386.deb) ...
Selecting previously unselected package python-wicd.
Unpacking python-wicd (from .../python-wicd_1.7.2.3-1ubuntu0.1_all.deb) ...
Selecting previously unselected package wicd-daemon.
Unpacking wicd-daemon (from .../wicd-daemon_1.7.2.3-1ubuntu0.1_all.deb) ...
Selecting previously unselected package python-glade2.
Unpacking python-glade2 (from .../python-glade2_2.24.0-3_i386.deb) ...
Selecting previously unselected package wicd-gtk.
Unpacking wicd-gtk (from .../wicd-gtk_1.7.2.3-1ubuntu0.1_all.deb) ...
Selecting previously unselected package wicd.
Unpacking wicd (from .../wicd_1.7.2.3-1ubuntu0.1_all.deb) ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for hicolor-icon-theme ...
Setting up libglade2-0 (1:2.6.4-1ubuntu1.1) ...
Setting up python-wicd (1.7.2.3-1ubuntu0.1) ...
Setting up wicd-daemon (1.7.2.3-1ubuntu0.1) ...
 * Starting Network connection manager wicd                              [ OK ] 
Setting up python-glade2 (2.24.0-3) ...
Setting up wicd-gtk (1.7.2.3-1ubuntu0.1) ...
Setting up wicd (1.7.2.3-1ubuntu0.1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
mar@mar-Vostro-200:~$ sudo apt-get purge network manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package network
E: Unable to locate package manager
mar@mar-Vostro-200:~$

---

### Post by daslinkard on 2012-10-08
Try this instead
```
sudo apt-get remove --purge network-manage*
```

---

### Post by Marthewicked on 2012-10-08
[IMG]http:///home/mar/Downloads/20121008_153733.jpg[/IMG]

[IMG]http://ubuntuforums.org/home/mar/Downloads/20121008_153733.jpg[/IMG] This the image that started it all. And when it gets this no response at all, unplug power cord then plug back in. When upgraded to 11.10 it was like this whether i booted or just plugged it after i booted.

---

### Post by Marthewicked on 2012-10-08
> **daslinkard said:**
> Try this instead
```
sudo apt-get remove --purge network-manage*
```

Removed it....

mar@mar-Vostro-200:~$ sudo apt-get remove --purge network-manage*
[sudo] password for mar: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'network-manager-openconnect-gnome' for regex 'network-manage*'
Note, selecting 'network-manager-pptp-gnome' for regex 'network-manage*'
Note, selecting 'network-manager-pptp' for regex 'network-manage*'
Note, selecting 'network-manager' for regex 'network-manage*'
Note, selecting 'network-manager-openconnect' for regex 'network-manage*'
Note, selecting 'network-manager-strongswan-kde' for regex 'network-manage*'
Note, selecting 'network-manager-strongswan' for regex 'network-manage*'
Note, selecting 'network-manager-gnome' for regex 'network-manage*'
Note, selecting 'network-manager-openvpn-gnome' for regex 'network-manage*'
Note, selecting 'network-manager-vpnc' for regex 'network-manage*'
Note, selecting 'network-manager-vpnc-kde' for regex 'network-manage*'
Note, selecting 'network-manager-openvpn-kde' for regex 'network-manage*'
Note, selecting 'network-manager-vpnc-gnome' for regex 'network-manage*'
Note, selecting 'network-manager-pptp-kde' for regex 'network-manage*'
Note, selecting 'network-manager-gnome-dbg' for regex 'network-manage*'
Note, selecting 'network-manager-dbg' for regex 'network-manage*'
Note, selecting 'network-manager-dev' for regex 'network-manage*'
Note, selecting 'network-manager-openvpn' for regex 'network-manage*'
Note, selecting 'network-manager-kde' for regex 'network-manage*'
Package network-manager-gnome-dbg is not installed, so not removed
Package network-manager-kde is not installed, so not removed
Package network-manager-openconnect is not installed, so not removed
Package network-manager-openconnect-gnome is not installed, so not removed
Package network-manager-openvpn is not installed, so not removed
Package network-manager-openvpn-gnome is not installed, so not removed
Package network-manager-strongswan is not installed, so not removed
Package network-manager-vpnc is not installed, so not removed
Package network-manager-vpnc-gnome is not installed, so not removed
Package network-manager-dbg is not installed, so not removed
Package network-manager-dev is not installed, so not removed
The following packages will be REMOVED:
  network-manager* network-manager-gnome* network-manager-pptp*
  network-manager-pptp-gnome*
0 upgraded, 0 newly installed, 4 to remove and 138 not upgraded.
After this operation, 3,665 kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 141310 files and directories currently installed.)
Removing network-manager-gnome ...
Purging configuration files for network-manager-gnome ...
Removing network-manager ...
network-manager stop/waiting
Purging configuration files for network-manager ...
dpkg: warning: while removing network-manager, directory '/etc/NetworkManager/system-connections' not empty so not removed.
Removing network-manager-pptp-gnome ...
Removing network-manager-pptp ...
Purging configuration files for network-manager-pptp ...
dpkg: warning: while removing network-manager-pptp, directory '/etc/NetworkManager' not empty so not removed.
Processing triggers for gconf2 ...
Processing triggers for man-db ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for ureadahead ...
mar@mar-Vostro-200:~$

---

### Post by Marthewicked on 2012-10-08
Thank god im still connected on phone and im still here after waking up this morning clocking over 12 hours for free hehe.  However, i have nothing connected now, i dont even see the wireless symbol by the volume and email link by top right corner, ooooh i have done it now, in big trouble!!

---

### Post by Marthewicked on 2012-10-08
Do this now?

sudo service network-manager restart

or this code is also wrong?

or reinstall the driver again?

---

### Post by daslinkard on 2012-10-08
Let's see what happens

```
 sudo service network-manager restart
```

---

### Post by Marthewicked on 2012-10-08
> **daslinkard said:**
> Let's see what happens

```
 sudo service network-manager restart
```

said, "unrecognized service"

---

### Post by daslinkard on 2012-10-08
> **Marthewicked said:**
> said, "unrecognized service"
 
Hmmm....let's reinstall it....
```

sudo apt-get install network-manager
```

---

### Post by Marthewicked on 2012-10-08
> **daslinkard said:**
> Hmmm....let's reinstall it....
```

sudo apt-get install network-manager
```

ok reinstalled and restarted. then light blue on the usb came back on like it was before i removed and.  Now, asks passcode like before and same thing, enter key for authentication and no connection to internet.  This stomps me and im thinking, is it possible to redownload drivers and start from scratch?

---

### Post by daslinkard on 2012-10-08
I believe you would be able to....try the commands that got this up and running a few pages back and go from there.....I'm here for you though!

---

### Post by Marthewicked on 2012-10-08
There is something weird going on here though, when i discoonect phone tether, it disconnects from web. When i connect tether on then i can see my wireless connection and it looks like it is connected as long as i have the phone tether plugged.  Does this make sense?

---

### Post by daslinkard on 2012-10-08
I'm thinking this is a hardware/driver conflict...

---

### Post by steeldriver on 2012-10-08
i think in general if you are relying on driver modules that you built from source then you are going to need to rebuild them pretty much any time you update the kernel - starting with the new kernel headers i.e.

```
sudo apt-get install linux-headers-$(uname -r)
```

then the dkms add / build / install commands

---

### Post by Marthewicked on 2012-10-08
> **daslinkard said:**
> I believe you would be able to....try the commands that got this up and running a few pages back and go from there.....I'm here for you though!

on this page ....
on the 6th comment where it ends halfway....but it created this ....

 Creating symlink /var/lib/dkms/rtl8192cu/3.3.23192/source ->  
                  /usr/src/rtl8192cu-3.3.23192

before i could continue to dkms because when i ran this code....

 sudo dkms add -m rtl8192cu -v 3.3.23192

i got this error.......

sudo: dkms: command not found
mar@mar-Vostro-200:~$ 

i copied before and after to see....the only difference is this is 12.04 vs the one yesterday for 11.04 if that makes any difference.


rtl8192cu-3.3.23192/src/hal/rtl8192c/usb/usb_ops_ce.c
rtl8192cu-3.3.23192/src/hal/rtl8192c/usb/rtl8192cu_recv.c
rtl8192cu-3.3.23192/src/hal/rtl8192c/usb/usb_halinit.c
rtl8192cu-3.3.23192/src/hal/rtl8192c/usb/rtl8192cu_led.c
mar@mar-Vostro-200:~$ sudo dkms add -m rtl8192cu -v 3.3.23192
sudo: dkms: command not found
mar@mar-Vostro-200:~$

---

### Post by Marthewicked on 2012-10-08
> **steeldriver said:**
> i think in general if you are relying on driver modules that you built from source then you are going to need to rebuild them pretty much any time you update the kernel - starting with the new kernel headers i.e.

```
sudo apt-get install linux-headers-$(uname -r)
```then the dkms add / build / install commands

im confused on this.... sorry i been staring on this computer and this room over 13 hours now maybe brain fried.  I did not update because the USB was crashing the system, like i plug before or after boot and black screen with white letters so i installed clean 12.04 LTS and i have not installed drivers yet but it looked as plug and play though even though it did not connect to the wireless.

Now, sudo apt-get install linux-headers-$(uname-r) what is the parenthesis what goes in the paranthesis or that is the complete code?

thanks in advance im just extremely tired and stubborn to not know how to quit. i did not even eat yet.
whew....breathe breathe.

---

### Post by Marthewicked on 2012-10-08
> **steeldriver said:**
> i think in general if you are relying on driver modules that you built from source then you are going to need to rebuild them pretty much any time you update the kernel - starting with the new kernel headers i.e.

```
sudo apt-get install linux-headers-$(uname -r)
```then the dkms add / build / install commands

if this is what you meant

on extract .....

rtl8192cu-3.3.23192/src/hal/rtl8192c/usb/rtl8192cu_recv.c
rtl8192cu-3.3.23192/src/hal/rtl8192c/usb/usb_halinit.c
rtl8192cu-3.3.23192/src/hal/rtl8192c/usb/rtl8192cu_led.c
mar@mar-Vostro-200:~$ sudo dkms add -m rtl8192cu -v 3.3.23192
sudo: dkms: command not found

tried your option....

mar@mar-Vostro-200:~$ sudo apt-get install linux-headers-$(uname -r)
[sudo] password for mar: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-3.2.0-29-generic-pae is already the newest version.
linux-headers-3.2.0-29-generic-pae set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 137 not upgraded.

seem to check and now it is there

then run this again and no luck...


mar@mar-Vostro-200:~$ sudo dkms add -m rtl8192cu -v 3.3.23192
sudo: dkms: command not found
mar@mar-Vostro-200:~$

---

### Post by Marthewicked on 2012-10-09
> **daslinkard said:**
> I believe you would be able to....try the commands that got this up and running a few pages back and go from there.....I'm here for you though!
appreciated very much for the help.

---

### Post by Marthewicked on 2012-10-09
time to go to sleep i suppose.

Anyway, here is so far what i have done and maybe someone will see where im not getting connected.  Please someone just look it over, when i wake up tomorrow i wil get back at it again.

mar@mar-Vostro-200:~$ sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic
[sudo] password for mar: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  linux-headers-3.2.0-31-generic
The following NEW packages will be installed:
  linux-headers-3.2.0-31-generic linux-headers-generic
0 upgraded, 2 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 1,967 kB of archives.
After this operation, 11.2 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main linux-headers-3.2.0-29-generic-pae i386 3.2.0-29.46 [985 kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main linux-headers-3.2.0-31-generic i386 3.2.0-31.50 [979 kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main linux-headers-generic i386 3.2.0.31.34 [2,596 B]
Fetched 1,967 kB in 1s (1,277 kB/s)             
(Reading database ... 168588 files and directories currently installed.)
Preparing to replace linux-headers-3.2.0-29-generic-pae 3.2.0-29.46 (using .../linux-headers-3.2.0-29-generic-pae_3.2.0-29.46_i386.deb) ...
Unpacking replacement linux-headers-3.2.0-29-generic-pae ...
Selecting previously unselected package linux-headers-3.2.0-31-generic.
Unpacking linux-headers-3.2.0-31-generic (from .../linux-headers-3.2.0-31-generic_3.2.0-31.50_i386.deb) ...
Selecting previously unselected package linux-headers-generic.
Unpacking linux-headers-generic (from .../linux-headers-generic_3.2.0.31.34_i386.deb) ...
Setting up linux-headers-3.2.0-29-generic-pae (3.2.0-29.46) ...
Setting up linux-headers-3.2.0-31-generic (3.2.0-31.50) ...
Setting up linux-headers-generic (3.2.0.31.34) ...


mar@mar-Vostro-200:~$ wget [http://media.cdn.ubuntu-de.org/forum...92_dkms.tar.gz](http://media.cdn.ubuntu-de.org/forum...92_dkms.tar.gz) 
--2012-10-09 01:37:09--  [http://media.cdn.ubuntu-de.org/forum...92_dkms.tar.gz](http://media.cdn.ubuntu-de.org/forum...92_dkms.tar.gz)
Resolving media.cdn.ubuntu-de.org (media.cdn.ubuntu-de.org)... 213.95.41.13, 2001:780:0:25:206:5bff:fe04:8bcb
Connecting to media.cdn.ubuntu-de.org (media.cdn.ubuntu-de.org)|213.95.41.13|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2012-10-09 01:37:09 ERROR 404: Not Found.

mar@mar-Vostro-200:~$ wget media.cdn.ubuntu-de.org/forum/attachments/32/20/2844083-rtl8192cu-3.3.23192_dkms.tar.gz
--2012-10-09 01:38:36--  [http://media.cdn.ubuntu-de.org/forum/attachments/32/20/2844083-rtl8192cu-3.3.23192_dkms.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/32/20/2844083-rtl8192cu-3.3.23192_dkms.tar.gz)
Resolving media.cdn.ubuntu-de.org (media.cdn.ubuntu-de.org)... 213.95.41.13, 2001:780:0:25:206:5bff:fe04:8bcb
Connecting to media.cdn.ubuntu-de.org (media.cdn.ubuntu-de.org)|213.95.41.13|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1202618 (1.1M) [application/octet-stream]
Saving to: `2844083-rtl8192cu-3.3.23192_dkms.tar.gz.1'

100%[======================================>] 1,202,618    568K/s   in 2.1s    

2012-10-09 01:38:39 (568 KB/s) - `2844083-rtl8192cu-3.3.23192_dkms.tar.gz.1' saved [1202618/1202618]



mar@mar-Vostro-200:~$ sudo tar xvf 2844083-rtl8192cu-3.3.23192_dkms.tar.gz -C /usr/src
rtl8192cu-3.3.23192/
rtl8192cu-3.3.23192/src/
rtl8192cu-3.3.23192/src/os_dep/
rtl8192cu-3.3.23192/src/include/
rtl8192cu-3.3.23192/src/hal/
rtl8192cu-3.3.23192/src/core/
rtl8192cu-3.3.23192/src/os_dep/linux/
rtl8192cu-3.3.23192/src/include/byteorder/
rtl8192cu-3.3.23192/src/hal/rtl8192d/
rtl8192cu-3.3.23192/src/hal/rtl8192c/
rtl8192cu-3.3.23192/src/core/efuse/
rtl8192cu-3.3.23192/src/hal/rtl8192d/usb/
rtl8192cu-3.3.23192/src/hal/rtl8192c/usb/
rtl8192cu-3.3.23192/Makefile
rtl8192cu-3.3.23192/dkms.conf
rtl8192cu-3.3.23192/src/wlan0dhcp
rtl8192cu-3.3.23192/src/Makefile
rtl8192cu-3.3.23192/src/make_drv
rtl8192cu-3.3.23192/src/Kconfig
rtl8192cu-3.3.23192/src/ifcfg-wlan0
rtl8192cu-3.3.23192/src/clean
rtl8192cu-3.3.23192/src/autoconf_rtl8192d_usb_linux.h
rtl8192cu-3.3.23192/src/autoconf_rtl8192c_usb_linux.h
rtl8192cu-3.3.23192/src/os_dep/osdep_service.c
rtl8192cu-3.3.23192/src/include/rtw_ioctl.h
rtl8192cu-3.3.23192/src/include/rtw_mp.h
rtl8192cu-3.3.23192/src/include/rtl8192c_sreset.h
rtl8192cu-3.3.23192/src/include/xmit_osdep.h
rtl8192cu-3.3.23192/src/include/if_ether.h
rtl8192cu-3.3.23192/src/include/rtw_led.h
rtl8192cu-3.3.23192/src/include/ip.h
rtl8192cu-3.3.23192/src/include/rtl8192c_hal.h
rtl8192cu-3.3.23192/src/include/basic_types.h
rtl8192cu-3.3.23192/src/include/circ_buf.h
rtl8192cu-3.3.23192/src/include/rtw_br_ext.h
rtl8192cu-3.3.23192/src/include/Hal8192DPhyReg.h
rtl8192cu-3.3.23192/src/include/rtw_io.h
rtl8192cu-3.3.23192/src/include/sdio_hal.h
rtl8192cu-3.3.23192/src/include/rtw_security.h
rtl8192cu-3.3.23192/src/include/autoconf.h
rtl8192cu-3.3.23192/src/include/usb_hal.h
rtl8192cu-3.3.23192/src/include/rtw_rf.h
rtl8192cu-3.3.23192/src/include/rtw_mp_phy_regdef.h
rtl8192cu-3.3.23192/src/include/rtw_iol.h
rtl8192cu-3.3.23192/src/include/sta_info.h
rtl8192cu-3.3.23192/src/include/osdep_intf.h
rtl8192cu-3.3.23192/src/include/rtw_debug.h
rtl8192cu-3.3.23192/src/include/mlme_osdep.h
rtl8192cu-3.3.23192/src/include/rtw_event.h
rtl8192cu-3.3.23192/src/include/rtl8192c_cmd.h
rtl8192cu-3.3.23192/src/include/pci_ops.h
rtl8192cu-3.3.23192/src/include/rtl8192d_rf.h
rtl8192cu-3.3.23192/src/include/rtw_cmd.h
rtl8192cu-3.3.23192/src/include/pci_osintf.h
rtl8192cu-3.3.23192/src/include/h2clbk.h
rtl8192cu-3.3.23192/src/include/rtw_ioctl_set.h
rtl8192cu-3.3.23192/src/include/rtl8192d_cmd.h
rtl8192cu-3.3.23192/src/include/rtw_version.h
rtl8192cu-3.3.23192/src/include/rtl8192d_xmit.h
rtl8192cu-3.3.23192/src/include/rtw_byteorder.h
rtl8192cu-3.3.23192/src/include/drv_types_xp.h
rtl8192cu-3.3.23192/src/include/rtw_eeprom.h
rtl8192cu-3.3.23192/src/include/rtw_ioctl_query.h
rtl8192cu-3.3.23192/src/include/osdep_service.h
rtl8192cu-3.3.23192/src/include/usb_vendor_req.h
rtl8192cu-3.3.23192/src/include/drv_conf.h
rtl8192cu-3.3.23192/src/include/pci_hal.h
rtl8192cu-3.3.23192/src/include/rtw_p2p.h
rtl8192cu-3.3.23192/src/include/Hal8192CEHWImg.h
rtl8192cu-3.3.23192/src/include/sdio_osintf.h
rtl8192cu-3.3.23192/src/include/Hal8192DETestHWImg.h
rtl8192cu-3.3.23192/src/include/sdio_ops_xp.h
rtl8192cu-3.3.23192/src/include/rtw_mp_ioctl.h
rtl8192cu-3.3.23192/src/include/rtl8192d_led.h
rtl8192cu-3.3.23192/src/include/Hal8192CPhyCfg.h
rtl8192cu-3.3.23192/src/include/drv_types_ce.h
rtl8192cu-3.3.23192/src/include/ieee80211_ext.h
rtl8192cu-3.3.23192/src/include/Hal8192DEHWImg.h
rtl8192cu-3.3.23192/src/include/drv_types.h
rtl8192cu-3.3.23192/src/include/hal_init.h
rtl8192cu-3.3.23192/src/include/rtw_mlme.h
rtl8192cu-3.3.23192/src/include/rtl8192c_spec.h
rtl8192cu-3.3.23192/src/include/Hal8192DUHWImg.h
rtl8192cu-3.3.23192/src/include/sdio_ops_linux.h
rtl8192cu-3.3.23192/src/include/rtw_ioctl_rtl.h
rtl8192cu-3.3.23192/src/include/mp_custom_oid.h
rtl8192cu-3.3.23192/src/include/ethernet.h
rtl8192cu-3.3.23192/src/include/rtw_ht.h
rtl8192cu-3.3.23192/src/include/usb_ops.h
rtl8192cu-3.3.23192/src/include/Hal8192DUTestHWImg.h
rtl8192cu-3.3.23192/src/include/sdio_ops_ce.h
rtl8192cu-3.3.23192/src/include/Hal8192CUHWImg.h
rtl8192cu-3.3.23192/src/include/rtw_efuse.h
rtl8192cu-3.3.23192/src/include/drv_types_linux.h
rtl8192cu-3.3.23192/src/include/recv_osdep.h
rtl8192cu-3.3.23192/src/include/ieee80211.h
rtl8192cu-3.3.23192/src/include/sdio_ops.h
rtl8192cu-3.3.23192/src/include/osdep_ce_service.h
rtl8192cu-3.3.23192/src/include/rtl8192d_spec.h
rtl8192cu-3.3.23192/src/include/rtl8192c_xmit.h
rtl8192cu-3.3.23192/src/include/rtw_pwrctrl.h
rtl8192cu-3.3.23192/src/include/rtw_qos.h
rtl8192cu-3.3.23192/src/include/rtl8192c_event.h
rtl8192cu-3.3.23192/src/include/rtw_xmit.h
rtl8192cu-3.3.23192/src/include/rtl8192d_dm.h
rtl8192cu-3.3.23192/src/include/usb_osintf.h
rtl8192cu-3.3.23192/src/include/nic_spec.h
rtl8192cu-3.3.23192/src/include/rtl8192c_recv.h
rtl8192cu-3.3.23192/src/include/rtl8192c_rf.h
rtl8192cu-3.3.23192/src/include/rtl8192c_dm.h
rtl8192cu-3.3.23192/src/include/rtl8192d_hal.h
rtl8192cu-3.3.23192/src/include/Hal8192DPhyCfg.h
rtl8192cu-3.3.23192/src/include/Hal8192CPhyReg.h
rtl8192cu-3.3.23192/src/include/farray.h
rtl8192cu-3.3.23192/src/include/rtl8192d_recv.h
rtl8192cu-3.3.23192/src/include/rtl8192c_led.h
rtl8192cu-3.3.23192/src/include/wifi.h
rtl8192cu-3.3.23192/src/include/rtw_mlme_ext.h
rtl8192cu-3.3.23192/src/include/rtw_recv.h
rtl8192cu-3.3.23192/src/include/cmd_osdep.h
rtl8192cu-3.3.23192/src/include/wlan_bssdef.h
rtl8192cu-3.3.23192/src/hal/hal_init.c
rtl8192cu-3.3.23192/src/core/rtw_iol.c
rtl8192cu-3.3.23192/src/core/rtw_ioctl_set.c
rtl8192cu-3.3.23192/src/core/rtw_mp_ioctl.c
rtl8192cu-3.3.23192/src/core/rtw_ioctl_rtl.c
rtl8192cu-3.3.23192/src/core/rtw_io.c
rtl8192cu-3.3.23192/src/core/rtw_mlme_ext.c
rtl8192cu-3.3.23192/src/core/rtw_wlan_util.c
rtl8192cu-3.3.23192/src/core/rtw_pwrctrl.c
rtl8192cu-3.3.23192/src/core/rtw_rf.c
rtl8192cu-3.3.23192/src/core/rtw_sta_mgt.c
rtl8192cu-3.3.23192/src/core/rtw_mp.c
rtl8192cu-3.3.23192/src/core/rtw_mlme.c
rtl8192cu-3.3.23192/src/core/rtw_cmd.c
rtl8192cu-3.3.23192/src/core/rtw_security.c
rtl8192cu-3.3.23192/src/core/rtw_ieee80211.c
rtl8192cu-3.3.23192/src/core/rtw_p2p.c
rtl8192cu-3.3.23192/src/core/rtw_debug.c
rtl8192cu-3.3.23192/src/core/rtw_eeprom.c
rtl8192cu-3.3.23192/src/core/rtw_br_ext.c
rtl8192cu-3.3.23192/src/core/rtw_recv.c
rtl8192cu-3.3.23192/src/core/rtw_ioctl_query.c
rtl8192cu-3.3.23192/src/core/rtw_xmit.c
rtl8192cu-3.3.23192/src/os_dep/linux/xmit_linux.c
rtl8192cu-3.3.23192/src/os_dep/linux/sdio_intf.c
rtl8192cu-3.3.23192/src/os_dep/linux/pci_intf.c
rtl8192cu-3.3.23192/src/os_dep/linux/mlme_linux.c
rtl8192cu-3.3.23192/src/os_dep/linux/usb_intf.c
rtl8192cu-3.3.23192/src/os_dep/linux/os_intfs.c
rtl8192cu-3.3.23192/src/os_dep/linux/recv_linux.c
rtl8192cu-3.3.23192/src/os_dep/linux/ioctl_linux.c
rtl8192cu-3.3.23192/src/include/byteorder/generic.h
rtl8192cu-3.3.23192/src/include/byteorder/little_endian.h
rtl8192cu-3.3.23192/src/include/byteorder/big_endian.h
rtl8192cu-3.3.23192/src/include/byteorder/swabb.h
rtl8192cu-3.3.23192/src/include/byteorder/swab.h
rtl8192cu-3.3.23192/src/hal/rtl8192d/rtl8192d_hal_init.c
rtl8192cu-3.3.23192/src/hal/rtl8192d/rtl8192d_rf6052.c
rtl8192cu-3.3.23192/src/hal/rtl8192d/rtl8192d_dm.c
rtl8192cu-3.3.23192/src/hal/rtl8192d/rtl8192d_mp.c
rtl8192cu-3.3.23192/src/hal/rtl8192d/rtl8192d_phycfg.c
rtl8192cu-3.3.23192/src/hal/rtl8192d/rtl8192d_cmd.c
rtl8192cu-3.3.23192/src/hal/rtl8192d/rtl8192d_rxdesc.c
rtl8192cu-3.3.23192/src/hal/rtl8192c/rtl8192c_hal_init.c
rtl8192cu-3.3.23192/src/hal/rtl8192c/rtl8192c_sreset.c
rtl8192cu-3.3.23192/src/hal/rtl8192c/rtl8192c_rf6052.c
rtl8192cu-3.3.23192/src/hal/rtl8192c/rtl8192c_rxdesc.c
rtl8192cu-3.3.23192/src/hal/rtl8192c/rtl8192c_mp.c
rtl8192cu-3.3.23192/src/hal/rtl8192c/rtl8192c_dm.c
rtl8192cu-3.3.23192/src/hal/rtl8192c/rtl8192c_phycfg.c
rtl8192cu-3.3.23192/src/hal/rtl8192c/rtl8192c_cmd.c
rtl8192cu-3.3.23192/src/core/efuse/rtw_efuse.c
rtl8192cu-3.3.23192/src/hal/rtl8192d/usb/usb_ops_linux.c
rtl8192cu-3.3.23192/src/hal/rtl8192d/usb/rtl8192du_led.c
rtl8192cu-3.3.23192/src/hal/rtl8192d/usb/Hal8192DUHWImg.c
rtl8192cu-3.3.23192/src/hal/rtl8192d/usb/rtl8192du_xmit.c
rtl8192cu-3.3.23192/src/hal/rtl8192d/usb/usb_halinit.c
rtl8192cu-3.3.23192/src/hal/rtl8192d/usb/rtl8192du_recv.c
rtl8192cu-3.3.23192/src/hal/rtl8192d/usb/Hal8192DUTestHWImg.c
rtl8192cu-3.3.23192/src/hal/rtl8192c/usb/usb_ops_xp.c
rtl8192cu-3.3.23192/src/hal/rtl8192c/usb/rtl8192cu_xmit.c
rtl8192cu-3.3.23192/src/hal/rtl8192c/usb/usb_ops_linux.c
rtl8192cu-3.3.23192/src/hal/rtl8192c/usb/Hal8192CUHWImg.c
rtl8192cu-3.3.23192/src/hal/rtl8192c/usb/usb_ops_ce.c
rtl8192cu-3.3.23192/src/hal/rtl8192c/usb/rtl8192cu_recv.c
rtl8192cu-3.3.23192/src/hal/rtl8192c/usb/usb_halinit.c
rtl8192cu-3.3.23192/src/hal/rtl8192c/usb/rtl8192cu_led.c


mar@mar-Vostro-200:~$ sudo dkms add -m rtl8192cu -v 3.3.23192 
sudo: dkms: command not found
mar@mar-Vostro-200:~$ 

I am stomped right now.

---

### Post by Marthewicked on 2012-10-09
I looked on other alternatives, i was not sure but it made sense because i need to connect to web so bad, here is what i have done and i will post link on the bottom...

mar@mar-Vostro-200:~$ sudo apt-get install linux-headers-`uname -r`
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-3.2.0-31-generic-pae is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

good to hear that i am up to date

and went on with instructions.....


mar@mar-Vostro-200:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dpkg-dev fakeroot g++ g++-4.6 libalgorithm-diff-perl
  libalgorithm-diff-xs-perl libalgorithm-merge-perl libdpkg-perl
  libstdc++6-4.6-dev libtimedate-perl
Suggested packages:
  debian-keyring g++-multilib g++-4.6-multilib gcc-4.6-doc libstdc++6-4.6-dbg
  libstdc++6-4.6-doc
The following NEW packages will be installed:
  build-essential dpkg-dev fakeroot g++ g++-4.6 libalgorithm-diff-perl
  libalgorithm-diff-xs-perl libalgorithm-merge-perl libdpkg-perl
  libstdc++6-4.6-dev libtimedate-perl
0 upgraded, 11 newly installed, 0 to remove and 0 not upgraded.
Need to get 9,249 kB of archives.
After this operation, 27.4 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main libstdc++6-4.6-dev i386 4.6.3-1ubuntu5 [1,643 kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main g++-4.6 i386 4.6.3-1ubuntu5 [6,745 kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main g++ i386 4:4.6.3-1ubuntu5 [1,444 B]
Get:4 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main libtimedate-perl all 1.2000-1 [41.6 kB]
Get:5 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main libdpkg-perl all 1.16.1.2ubuntu7 [181 kB]
Get:6 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main dpkg-dev all 1.16.1.2ubuntu7 [468 kB]
Get:7 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main build-essential i386 11.5ubuntu2.1 [5,796 B]
Get:8 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main fakeroot i386 1.18.2-1 [87.9 kB]
Get:9 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main libalgorithm-diff-perl all 1.19.02-2 [50.7 kB]
Get:10 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main libalgorithm-diff-xs-perl i386 0.04-2build2 [12.9 kB]
Get:11 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main libalgorithm-merge-perl all 0.08-2 [12.7 kB]
Fetched 9,249 kB in 7s (1,215 kB/s)                                            
Selecting previously unselected package libstdc++6-4.6-dev.
(Reading database ... 181415 files and directories currently installed.)
Unpacking libstdc++6-4.6-dev (from .../libstdc++6-4.6-dev_4.6.3-1ubuntu5_i386.deb) ...
Selecting previously unselected package g++-4.6.
Unpacking g++-4.6 (from .../g++-4.6_4.6.3-1ubuntu5_i386.deb) ...
Selecting previously unselected package g++.
Unpacking g++ (from .../g++_4%3a4.6.3-1ubuntu5_i386.deb) ...
Selecting previously unselected package libtimedate-perl.
Unpacking libtimedate-perl (from .../libtimedate-perl_1.2000-1_all.deb) ...
Selecting previously unselected package libdpkg-perl.
Unpacking libdpkg-perl (from .../libdpkg-perl_1.16.1.2ubuntu7_all.deb) ...
Selecting previously unselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.16.1.2ubuntu7_all.deb) ...
Selecting previously unselected package build-essential.
Unpacking build-essential (from .../build-essential_11.5ubuntu2.1_i386.deb) ...
Selecting previously unselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.18.2-1_i386.deb) ...
Selecting previously unselected package libalgorithm-diff-perl.
Unpacking libalgorithm-diff-perl (from .../libalgorithm-diff-perl_1.19.02-2_all.deb) ...
Selecting previously unselected package libalgorithm-diff-xs-perl.
Unpacking libalgorithm-diff-xs-perl (from .../libalgorithm-diff-xs-perl_0.04-2build2_i386.deb) ...
Selecting previously unselected package libalgorithm-merge-perl.
Unpacking libalgorithm-merge-perl (from .../libalgorithm-merge-perl_0.08-2_all.deb) ...
Processing triggers for man-db ...
Setting up libtimedate-perl (1.2000-1) ...
Setting up libdpkg-perl (1.16.1.2ubuntu7) ...
Setting up dpkg-dev (1.16.1.2ubuntu7) ...
Setting up fakeroot (1.18.2-1) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode.
Setting up libalgorithm-diff-perl (1.19.02-2) ...
Setting up libalgorithm-diff-xs-perl (0.04-2build2) ...
Setting up libalgorithm-merge-perl (0.08-2) ...
Setting up libstdc++6-4.6-dev (4.6.3-1ubuntu5) ...
Setting up g++-4.6 (4.6.3-1ubuntu5) ...
Setting up g++ (4:4.6.3-1ubuntu5) ...
update-alternatives: using /usr/bin/g++ to provide /usr/bin/c++ (c++) in auto mode.
Setting up build-essential (11.5ubuntu2.1) ...

mar@mar-Vostro-200:~$  cd ~/Downloads
/RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622

and i get this error and file is there though, how is this possible?

bash: cd: /home/mar/Downloads/RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622: No such file or directory

Here is the link page i followed...the cleanest, understandable link issues with my problem

[http://askubuntu.com/questions/168627/connecting-asus-usb-n13-wireless-adapter](http://askubuntu.com/questions/168627/connecting-asus-usb-n13-wireless-adapter)

i found an error if it makes sense to someone but it doesnt make sense to me......
the link web says this code,   cd ~/Downloads
/RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622

and when i checked my folder i have this, maybe newer or what not....       usb_linux_v3.4.4_4749.20120730.tar.gz 4749 instead of the 4369 and also 20120730  which are different, so i thought change those and im ready to go but still no director at all.

---

### Post by steeldriver on 2012-10-09
Sorry I'm completely lost - are you trying to do a **non**-dkms installation now? if you are still trying to re-do the dkms-based install (which worked on your original system I think?) , then your 'dkms not found' issue can likely be fixed just by (re-)installing the dkms package

```
sudo apt-get install dkms
```

---

### Post by Marthewicked on 2012-10-09
> **steeldriver said:**
> Sorry I'm completely lost - are you trying to do a **non**-dkms installation now? if you are still trying to re-do the dkms-based install (which worked on your original system I think?) , then your 'dkms not found' issue can likely be fixed just by (re-)installing the dkms package

```
sudo apt-get install dkms
```

Thank you so much, im trying pretty much everything, let me try this and see what happens

it feels good to get a reply.

---

### Post by Marthewicked on 2012-10-09
mar@mar-Vostro-200:~$ sudo apt-get install dkms
[sudo] password for mar: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  dkms
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 73.1 kB of archives.
After this operation, 347 kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main dkms all 2.2.0.3-1ubuntu3 [73.1 kB]
Fetched 73.1 kB in 0s (535 kB/s)
Selecting previously unselected package dkms.
(Reading database ... 182585 files and directories currently installed.)
Unpacking dkms (from .../dkms_2.2.0.3-1ubuntu3_all.deb) ...
Processing triggers for man-db ...
Setting up dkms (2.2.0.3-1ubuntu3) ...
mar@mar-Vostro-200:~$ sudo dkms add -m rtl8192cu -v 3.3.23192 

Creating symlink /var/lib/dkms/rtl8192cu/3.3.23192/source ->
                 /usr/src/rtl8192cu-3.3.23192

DKMS: add completed.
mar@mar-Vostro-200:~$ 


Steeldriver thanks alot....im continue to do what i did and reboot after this but im not stuck so far

---

### Post by Marthewicked on 2012-10-09
this s for anyone who followed this post from the beginning, i am posting what i have done and about to reboot. I am not sure if it will work now or not but whoever is following will have the answers.

I have followed so many posts and the person who recieved the help says "oh it worked" and for them but that post is useless who views it later.

mar@mar-Vostro-200:~$ sudo apt-get install dkms
[sudo] password for mar: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  dkms
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 73.1 kB of archives.
After this operation, 347 kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main dkms all 2.2.0.3-1ubuntu3 [73.1 kB]
Fetched 73.1 kB in 0s (535 kB/s)
Selecting previously unselected package dkms.
(Reading database ... 182585 files and directories currently installed.)
Unpacking dkms (from .../dkms_2.2.0.3-1ubuntu3_all.deb) ...
Processing triggers for man-db ...
Setting up dkms (2.2.0.3-1ubuntu3) ...
mar@mar-Vostro-200:~$ sudo dkms add -m rtl8192cu -v 3.3.23192 

Creating symlink /var/lib/dkms/rtl8192cu/3.3.23192/source ->
                 /usr/src/rtl8192cu-3.3.23192

DKMS: add completed.
mar@mar-Vostro-200:~$ 
mar@mar-Vostro-200:~$ sudo dkms build -m rtl8192cu -v 3.3.23192

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
'make' -C src/ all..................
cleaning build area....

DKMS: build completed.
mar@mar-Vostro-200:~$ sudo dkms install -m rtl8192cu -v 3.3.23192

8192cu:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-31-generic-pae/updates/dkms/

depmod........

DKMS: install completed.
mar@mar-Vostro-200:~$ sudo gedit /etc/rc.local

(gedit:11115): GLib-GIO-WARNING **: Missing callback called fullpath = /root/.local/share/recently-used.xbel

after the text editor came out i put these two lines before the exit 0


modprobe rtl8192cu
echo "0b05 17ab" > /sys/bus/usb/drivers/rtl8192cu/new_id

then i will reboot and see what happens. yey or nay

---

### Post by Marthewicked on 2012-10-09
ok rebooted and no connection so i connected my cell phone which is connected to my wireless.  One thing did change though, my wireless network is not on under hidden, it is right there below under wireless connections. I click on it and it asks the key and i enter but im back to square one where it asks the key every other a minute. 
I thank you for the reply and trying Steeldriver.

---

### Post by chili555 on 2012-10-09
So I don't have to read back through 50-60 posts, please post:```
lsb_release -d
lsusb
lsmod | grep 8192
iwconfig
```What are your symptoms?

---

### Post by Marthewicked on 2012-10-09
> **chili555 said:**
> So I don't have to read back through 50-60 posts, please post:```
lsb_release -d
lsusb
lsmod | grep 8192
iwconfig
```What are your symptoms?

mar@mar-Vostro-200:~$ lsb_release -d
Description:    Ubuntu 12.04.1 LTS
mar@mar-Vostro-200:~$ 
mar@mar-Vostro-200:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 0b05:17ab ASUSTek Computer, Inc. 
Bus 006 Device 002: ID 04d9:a01c Holtek Semiconductor, Inc. 
Bus 001 Device 006: ID 04e8:6864 Samsung Electronics Co., Ltd 
mar@mar-Vostro-200:~$ 
mar@mar-Vostro-200:~$ lsmod | grep 8192
rtl8192cu              97722  0 
rtl8192c_common        69519  1 rtl8192cu
rtlwifi                95804  1 rtl8192cu
mac80211              436455  3 rtl8192cu,rtl8192c_common,rtlwifi
mar@mar-Vostro-200:~$ 
mar@mar-Vostro-200:~$ iwconfig
lo        no wireless extensions.

usb0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.

mar@mar-Vostro-200:~$ 


Thank you

Symptoms

I see the network, i can click and choose, asks key/password and i enter but a minute later asks again no connection to internet at all.

---

### Post by chili555 on 2012-10-09
You have a driver loaded and a wireless interface. Let's dig deeper:```
sudo iwlist wlan0 scan
rfkill list all
```

---

### Post by Marthewicked on 2012-10-09
> **chili555 said:**
> You have a driver loaded and a wireless interface. Let's dig deeper:```
sudo iwlist wlan0 scan
rfkill list all
```

im suing my phone tether which is connected to my wireless as well. i can run it without connected to cell just to copy and paste here.  I wanted you to know, i dont know if that makes a difference.


mar@mar-Vostro-200:~$ sudo iwlist wlan0 scan
[sudo] password for mar: 
wlan0     No scan results

mar@mar-Vostro-200:~$ rfkill list all
3: phy3: Wireless LAN
    Soft blocked: no
    Hard blocked: no
mar@mar-Vostro-200:~$

---

### Post by chili555 on 2012-10-09
> $ sudo iwlist wlan0 scan
[sudo] password for mar:
wlan0 [COLOR="Red"]No scan results[/COLOR]Very mysterious. Let's look at:```
dmesg | grep -e rtl -e wlan
```The pipe symbol | is on the right side of my US keyboard on the same key with \.

---

### Post by Marthewicked on 2012-10-09
mar@mar-Vostro-200:~$ dmesg | grep -e rtl -e wlan
[   12.264934] rtl8192cu: MAC address: c8:60:00:d4:9e:86
[   12.264941] rtl8192cu: Board Type 0
[   12.509443] rtlwifi: rx_max_size 15360, rx_urb_num 8, in_ep 1
[   12.517787] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   12.518779] usbcore: registered new interface driver rtl8192cu
[   12.612318] Error: Driver 'rtl8192cu' is already registered, aborting...
[   12.653569] rtl8192cu: MAC auto ON okay!
[   12.699066] rtl8192cu: Tx queue select: 0x05
[   12.699967] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cufw.bin
[   13.146724] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   13.147130] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   20.528324] wlan0: authenticate with 00:18:01:eb:b3:c3 (try 1)
[   20.532338] wlan0: authenticated
[   20.554819] wlan0: associate with 00:18:01:eb:b3:c3 (try 1)
[   20.558216] wlan0: RX AssocResp from 00:18:01:eb:b3:c3 (capab=0x431 status=0 aid=2)
[   20.558221] wlan0: associated
[   20.559329] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   31.360021] wlan0: no IPv6 routers present
[   66.207607] wlan0: deauthenticating from 00:18:01:eb:b3:c3 by local choice (reason=3)
[  235.568036] rtlwifi: reg 0x102, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x83040002
[  235.568046] rtlwifi: reg 0x422, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x0
[  235.568052] rtlwifi: reg 0x542, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x4d5
[  235.568060] rtlwifi: reg 0x608, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x3903f2a
[  235.568080] rtlwifi: reg 0x102, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x3f3f3f3f
[  235.568085] rtlwifi: reg 0x422, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x3f3f3f3f
[  235.568091] rtlwifi: reg 0x542, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x3f3f3f27
[  235.568099] rtlwifi: reg 0x824, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x3f3f3f04
[  235.571080] rtlwifi: reg 0x820, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x3903f00
[  235.571085] rtlwifi: reg 0x8b8, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x83040002
[  235.571093] rtlwifi: reg 0x2, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x0
[  235.571098] rtlwifi: reg 0x2, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x4d5
[  235.571103] rtlwifi: reg 0x2, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x3903f2a
[  235.571109] rtlwifi: reg 0x44, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x3f3f3f3f
[  235.571115] rtlwifi: reg 0x42, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x3f3f3f3f
[  240.883252] rtl8192cu: MAC address: c8:60:00:d4:9e:86
[  240.883261] rtl8192cu: Board Type 0
[  240.888239] rtlwifi: rx_max_size 15360, rx_urb_num 8, in_ep 1
[  240.888703] ieee80211 phy1: Selected rate control algorithm 'rtl_rc'
[  240.927133] rtl8192cu: MAC auto ON okay!
[  240.960139] rtl8192cu: Tx queue select: 0x05
[  240.960893] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cufw.bin
[  241.361757] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  241.362121] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  243.637761] wlan0: authenticate with 00:18:01:eb:b3:c3 (try 1)
[  243.641528] wlan0: authenticated
[  243.664260] wlan0: associate with 00:18:01:eb:b3:c3 (try 1)
[  243.667648] wlan0: RX AssocResp from 00:18:01:eb:b3:c3 (capab=0x431 status=0 aid=2)
[  243.667654] wlan0: associated
[  243.668741] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  254.320039] wlan0: no IPv6 routers present
[  289.209423] wlan0: deauthenticating from 00:18:01:eb:b3:c3 by local choice (reason=3)
[ 5961.988086] rtlwifi: reg 0x102, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x0
[ 5961.988096] rtlwifi: reg 0x422, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x4d5
[ 5961.988102] rtlwifi: reg 0x542, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x3903f2a
[ 5961.988110] rtlwifi: reg 0x608, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x3f3f3f3f
[ 5961.988130] rtlwifi: reg 0x102, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x3f3f3f3f
[ 5961.988136] rtlwifi: reg 0x422, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x3f3f3f27
[ 5961.988142] rtlwifi: reg 0x542, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x5804
[ 5961.988150] rtlwifi: reg 0x824, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x80700
[ 5961.991132] rtlwifi: reg 0x820, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x83040002
[ 5961.991138] rtlwifi: reg 0x8a0, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x0
[ 5961.991146] rtlwifi: reg 0x2, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x4d5
[ 5961.991151] rtlwifi: reg 0x2, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x3903f2a
[ 5961.991157] rtlwifi: reg 0x2, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x3f3f3f3f
[ 5961.991163] rtlwifi: reg 0x44, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x3f3f3f3f
[ 5961.991168] rtlwifi: reg 0x42, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x3f3f3f27
[ 5963.521191] rtl8192cu: MAC address: c8:60:00:d4:9e:86
[ 5963.521200] rtl8192cu: Board Type 0
[ 5963.543443] rtlwifi: rx_max_size 15360, rx_urb_num 8, in_ep 1
[ 5963.543861] ieee80211 phy2: Selected rate control algorithm 'rtl_rc'
[ 5963.755894] rtl8192cu: MAC auto ON okay!
[ 5963.790830] rtl8192cu: Tx queue select: 0x05
[ 5963.791577] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cufw.bin
[ 5964.198474] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5964.199143] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5966.501080] wlan0: authenticate with 00:18:01:eb:b3:c3 (try 1)
[ 5966.504903] wlan0: authenticated
[ 5966.528199] wlan0: associate with 00:18:01:eb:b3:c3 (try 1)
[ 5966.530836] wlan0: RX AssocResp from 00:18:01:eb:b3:c3 (capab=0x431 status=0 aid=2)
[ 5966.530842] wlan0: associated
[ 5966.532084] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 5976.720025] wlan0: no IPv6 routers present
[ 6012.215367] wlan0: deauthenticating from 00:18:01:eb:b3:c3 by local choice (reason=3)
[ 6650.029509] rtl8192cu: MAC auto ON okay!
[ 6650.062897] rtl8192cu: Tx queue select: 0x05
[ 6650.063651] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cufw.bin
[ 6650.468923] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6650.748267] rtl8192cu: MAC auto ON okay!
[ 6650.783408] rtl8192cu: Tx queue select: 0x05
[ 6650.784169] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cufw.bin
[ 6651.208059] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[11651.625978] rtlwifi: reg 0xe08, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x0
[11651.625986] rtlwifi: reg 0x86c, usbctrl_vendorreq TimeOut! status:0xffffffed value=0xd38000
[11651.625992] rtlwifi: reg 0x86c, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x3
[11651.625998] rtlwifi: reg 0x838, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x5881
[11651.635959] rtlwifi: reg 0x603, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x80740
[11651.635967] rtlwifi: reg 0x442, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x8080740
[11651.635973] rtlwifi: reg 0x800, usbctrl_vendorreq TimeOut! status:0xffffffed value=0xd3c000
[11651.635978] rtlwifi: reg 0x900, usbctrl_vendorreq TimeOut! status:0xffffffed value=0xd30000
[11651.635984] rtlwifi: reg 0x884, usbctrl_vendorreq TimeOut! status:0xffffffed value=0xf0002ace
[11651.635995] rtlwifi: reg 0xc50, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x0
[11651.636016] rtlwifi: reg 0xc58, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x0
[11651.636023] rtlwifi: reg 0xe08, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x0
[11651.636030] rtlwifi: reg 0x86c, usbctrl_vendorreq TimeOut! status:0xffffffed value=0xd38000
[11651.636038] rtlwifi: reg 0x86c, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x1
[11651.636046] rtlwifi: reg 0x838, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x5881
[11651.636580] rtlwifi: reg 0x102, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x80740
[11651.636588] rtlwifi: reg 0x422, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x8080740
[11651.636595] rtlwifi: reg 0x542, usbctrl_vendorreq TimeOut! status:0xffffffed value=0xd3c000
[11651.636602] rtlwifi: reg 0x608, usbctrl_vendorreq TimeOut! status:0xffffffed value=0xd30000
[11651.636619] rtlwifi: reg 0x102, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x80390004
[11651.636624] rtlwifi: reg 0x422, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x1000100
[11651.636631] rtlwifi: reg 0x542, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x100010
[11651.636639] rtlwifi: reg 0x824, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x403a0100
[11651.639764] rtlwifi: reg 0x820, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x40080102
[11651.639771] rtlwifi: reg 0x8b8, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x90e1317
[11651.639780] rtlwifi: reg 0x2, usbctrl_vendorreq TimeOut! status:0xffffffed value=0xf0002ace
[11651.639786] rtlwifi: reg 0x2, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x0
[11651.639791] rtlwifi: reg 0x2, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x0
[11651.639797] rtlwifi: reg 0x44, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x0
[11651.639802] rtlwifi: reg 0x42, usbctrl_vendorreq TimeOut! status:0xffffffed value=0xd38000
[11653.573803] rtl8192cu: MAC address: c8:60:00:d4:9e:86
[11653.573813] rtl8192cu: Board Type 0
[11653.578182] rtlwifi: rx_max_size 15360, rx_urb_num 8, in_ep 1
[11653.578888] ieee80211 phy3: Selected rate control algorithm 'rtl_rc'
[11653.617172] rtl8192cu: MAC auto ON okay!
[11653.650566] rtl8192cu: Tx queue select: 0x05
[11653.651320] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cufw.bin
[11654.052490] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[11654.053161] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[11656.360810] wlan0: authenticate with 00:18:01:eb:b3:c3 (try 1)
[11656.362700] wlan0: authenticated
[11656.385689] wlan0: associate with 00:18:01:eb:b3:c3 (try 1)
[11656.389018] wlan0: RX AssocResp from 00:18:01:eb:b3:c3 (capab=0x431 status=0 aid=2)
[11656.389026] wlan0: associated
[11656.393379] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[11666.896023] wlan0: no IPv6 routers present
[11702.212565] wlan0: deauthenticating from 00:18:01:eb:b3:c3 by local choice (reason=3)
[12309.942725] rtl8192cu: MAC auto ON okay!
[12309.983244] rtl8192cu: Tx queue select: 0x05
[12309.983999] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cufw.bin
[12310.390720] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[12310.523982] rtl8192cu: MAC auto ON okay!
[12310.560365] rtl8192cu: Tx queue select: 0x05
[12310.561137] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cufw.bin
[12310.969593] ADDRCONF(NETDEV_UP): wlan0: link is not ready
mar@mar-Vostro-200:~$

---

### Post by chili555 on 2012-10-09
Please try:```
sudo modprobe -r rtl8192cu
sudo modprobe 8192cu
sudo iwlist wlan0 scan
```I love interesting problems!

---

### Post by Marthewicked on 2012-10-09
> **chili555 said:**
> Please try:```
sudo modprobe -r rtl8192cu
sudo modprobe 8192cu
sudo iwlist wlan0 scan
```I love interesting problems!

whew i was working on this couple of days it is not even fair that my computer doesnt want me to be with ubuntu 

200:~$ sudo modprobe -r rtl8192cu
[sudo] password for mar: 
mar@mar-Vostro-200:~$ sudo modprobe -r rtl8192cu
mar@mar-Vostro-200:~$ sudo modprobe 8192cu
mar@mar-Vostro-200:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:18:01:EB:B3:C3
                    ESSID:"MFGT1"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Quality=100/100  Signal level=61/100  
          Cell 02 - Address: 00:1F:90:CF:2D:D4
                    ESSID:"VSTA5"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Quality=12/100  Signal level=26/100  
          Cell 03 - Address: 00:1F:90:B9:81:88
                    ESSID:"8KFU5"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Quality=15/100  Signal level=22/100  

mar@mar-Vostro-200:~$

---

### Post by chili555 on 2012-10-09
> mar@mar-Vostro-200:~$ sudo iwlist wlan0 scan
wlan0 Scan completed :
Cell 01 - Address: 00:18:01:EB:B3:C3
ESSID:"MFGT1"
Protocol:IEEE 802.11bg
Mode:Master
Frequency:2.437 GHz (Channel 6)
Encryption keynAwesome! Now does it connect? Try? Smoke? Spark? Sing???

---

### Post by Marthewicked on 2012-10-09
> **chili555 said:**
> Awesome! Now does it connect? Try? Smoke? Spark? Sing???

No does not connect.

few things that change off topic, there was a blue solid light that is no longer on. There is an LED light that never came on at all.

i can see the networks and i clicked on my network and it asked for code and entered but returned no connection result

---

### Post by Marthewicked on 2012-10-09
boot up first to see if it will connect or that is not necessary?

---

### Post by chili555 on 2012-10-09
> **Marthewicked said:**
> No does not connect.

few things that change off topic, there was a blue solid light that is no longer on. There is an LED light that never came on at all.

i can see the networks and i clicked on my network and it asked for code and entered but returned no connection resultThe presence or absence of an LED is not conclusive. You can see and try to connect to networks; that's more meaningful.

Let's see if there are any clues in the last part of syslog:```
sudo cat /var/log/syslog | grep etwork | tail -n20
```After you post the result, do:```
sudo su
echo "blacklist rtl8192cu" >> /etc/modprobe.d/blacklist.conf
exit
```Reboot.

Any change in behavior?

---

### Post by Marthewicked on 2012-10-09
> **chili555 said:**
> The presence or absence of an LED is not conclusive. You can see and try to connect to networks; that's more meaningful.

Let's see if there are any clues in the last part of syslog:```
sudo cat /var/log/syslog | grep etwork | tail -n20
```After you post the result, do:```
sudo su
echo "blacklist rtl8192cu" >> /etc/modprobe.d/blacklist.conf
exit
```Reboot.

Any change in behavior?

that is true blue light does not matter....it came back on now and flashing but still same issue...

mar@mar-Vostro-200:~$ sudo cat /var/log/syslog | grep etwork | tail -n20
[sudo] password for mar: 
Oct  9 20:28:56 mar-Vostro-200 NetworkManager[738]: <info> Activation (wlan0) Beginning IP6 addrconf.
Oct  9 20:28:56 mar-Vostro-200 NetworkManager[738]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Oct  9 20:28:56 mar-Vostro-200 NetworkManager[738]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Oct  9 20:29:01 mar-Vostro-200 NetworkManager[738]: <info> wpa_supplicant die count reset
Oct  9 20:29:16 mar-Vostro-200 NetworkManager[738]: <info> (wlan0): IP6 addrconf timed out or failed.
Oct  9 20:29:16 mar-Vostro-200 NetworkManager[738]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Oct  9 20:29:16 mar-Vostro-200 NetworkManager[738]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Oct  9 20:29:16 mar-Vostro-200 NetworkManager[738]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Oct  9 20:29:41 mar-Vostro-200 NetworkManager[738]: <warn> (wlan0): DHCPv4 request timed out.
Oct  9 20:29:41 mar-Vostro-200 NetworkManager[738]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 10409
Oct  9 20:29:41 mar-Vostro-200 NetworkManager[738]: <info> Activation (wlan0) Stage 4 of 5 (IPv4 Configure Timeout) scheduled...
Oct  9 20:29:41 mar-Vostro-200 NetworkManager[738]: <info> Activation (wlan0) Stage 4 of 5 (IPv4 Configure Timeout) started...
Oct  9 20:29:41 mar-Vostro-200 NetworkManager[738]: <info> (wlan0): device state change: ip-config -> failed (reason 'ip-config-unavailable') [70 120 5]
Oct  9 20:29:41 mar-Vostro-200 NetworkManager[738]: <warn> Activation (wlan0) failed for access point (MFGT1)
Oct  9 20:29:41 mar-Vostro-200 NetworkManager[738]: <info> Marking connection 'MFGT1 1' invalid.
Oct  9 20:29:41 mar-Vostro-200 NetworkManager[738]: <warn> Activation (wlan0) failed.
Oct  9 20:29:41 mar-Vostro-200 NetworkManager[738]: <info> Activation (wlan0) Stage 4 of 5 (IPv4 Configure Timeout) complete.
Oct  9 20:29:41 mar-Vostro-200 NetworkManager[738]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Oct  9 20:29:41 mar-Vostro-200 NetworkManager[738]: <info> (wlan0): deactivating device (reason 'none') [0]
Oct  9 20:29:41 mar-Vostro-200 NetworkManager[738]: <info> (wlan0): supplicant interface state: completed -> disconnected
mar@mar-Vostro-200:~$

---

### Post by Marthewicked on 2012-10-09
here is the second code....

mar@mar-Vostro-200:~$ sudo su
[sudo] password for mar: 
root@mar-Vostro-200:/home/mar# echo "blacklist rtl8192cu" >> /etc/modprobe.d/blacklist.conf
root@mar-Vostro-200:/home/mar# exit
exit
mar@mar-Vostro-200:~$

---

### Post by Marthewicked on 2012-10-09
No connection yet.

Different symtoms, it searches for the networks. I clicked on the wireless symbol and i see my network i click on it but this time it does not even ask password it just gives up and stops refreshing. This is after reboot.

---

### Post by chili555 on 2012-10-09
> **Marthewicked said:**
> No connection yet.

Different symtoms, it searches for the networks. I clicked on the wireless symbol and i see my network i click on it but this time it does not even ask password it just gives up and stops refreshing. This is after reboot.Have you placed any extra settings in Network Manager? if so, they need to be removed. Normally, NM will do all the setting without assistance, aside from the password. NM should be set as attached.

I assume, from your scan results, that your network is set to WEP encryption. How many characters are in your key?

---

### Post by steeldriver on 2012-10-09
Hi chili I was hoping you would stop by and help out - is it possible that the OP's previous attempts to fix have left some cruft around? The syslog seems to be showing an issue with DHCP and I wondered if that might be a result of a conflict with wicd?

Mar - did you purge wicd when you reinstalled network-manager?

```
sudo apt-get purge wicd
```

---

### Post by Marthewicked on 2012-10-09
> **chili555 said:**
> Have you placed any extra settings in Network Manager? if so, they need to be removed. Normally, NM will do all the setting without assistance, aside from the password. NM should be set as attached.

I assume, from your scan results, that your network is set to WEP encryption. How many characters are in your key?

ten characters, no i have 12.04 clean slate, no adjusting or setting anything up, i never connected to web at all, except tether on phone

---

### Post by Marthewicked on 2012-10-09
> **steeldriver said:**
> Hi chili I was hoping you would stop by and help out - is it possible that the OP's previous attempts to fix have left some cruft around? The syslog seems to be showing an issue with DHCP and I wondered if that might be a result of a conflict with wicd?

Mar - did you purge wicd when you reinstalled network-manager?

```
sudo apt-get purge wicd
```

yes i ran that code when you told me ....i will check when i did it. But im 100% sure i ran this code on termnal

---

### Post by Marthewicked on 2012-10-09
sudo apt-get remove --purge network-manage*

theen it did not work so we did this code


Also I am wondering about this link primarily with the suggestion of dumping network manager for wicd.

The commands suggested to do this are as follows:
Code:

sudo apt-get install wicd

Code:

sudo apt-get purge network-manager

---

### Post by Marthewicked on 2012-10-09
> **Marthewicked said:**
> sudo apt-get remove --purge network-manage*

theen it did not work so we did this code


Also I am wondering about this link primarily with the suggestion of dumping network manager for wicd.

The commands suggested to do this are as follows:
Code:

sudo apt-get install wicd

Code:

sudo apt-get purge network-manager

i am sure i did the code or to my knowledge followed everything.....double checked whenever i entered but im human and possibility is there

i ran now and this is what i got,

mar@mar-Vostro-200:~$ sudo apt-get purge wicd
[sudo] password for mar: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
mar@mar-Vostro-200:~$

---

### Post by steeldriver on 2012-10-09
OK so do you have another package manager open (synaptic or software center)? if so close it then try the sudo apt-get purge wicd again

also can we just check which DHCP client is running (dhclient versus dhcpcd)

```
ps -e|grep dhc
```

---

### Post by Marthewicked on 2012-10-09
> **steeldriver said:**
> OK so do you have another package manager open (synaptic or software center)? if so close it then try the sudo apt-get purge wicd again

also can we just check which DHCP client is running (dhclient versus dhcpcd)

```
ps -e|grep dhc
```

oh yeah there was synaptic manager open my fault

mar@mar-Vostro-200:~$ sudo apt-get purge wicd
[sudo] password for mar: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-wicd wicd-daemon wicd-gtk
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  wicd*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 47.1 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 196115 files and directories currently installed.)
Removing wicd ...
mar@mar-Vostro-200:~$ ps -e | grep dhc
 2042 ?        00:00:00 dhclient
mar@mar-Vostro-200:~$

---

### Post by steeldriver on 2012-10-09
Ok and now if you restart n-m (or go the whole hog and reboot)? Any improvement?

---

### Post by Marthewicked on 2012-10-09
> **steeldriver said:**
> Ok and now if you restart n-m (or go the whole hog and reboot)? Any improvement?
i rebooted and still the same but it does not ask for passcode, just refreshing then says disconnected

---

### Post by chili555 on 2012-10-09
Let's see the syslog again, please:```
sudo cat /var/log/syslog | grep etwork | tail -n20
```It certainly ought to be asking for your key.

---

### Post by Marthewicked on 2012-10-09
> **steeldriver said:**
> The Asus N13 can be tricky iirc because different generations use different chipsets / drivers

Since it's a USB device we will need either

```
lsusb
```(not lspci) or

```
lshw -C network
```while the device is plugged in please
mar@mar-Vostro-200:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0b05:17ab ASUSTek Computer, Inc. 
Bus 006 Device 002: ID 04d9:a01c Holtek Semiconductor, Inc. 
Bus 001 Device 004: ID 04e8:6864 Samsung Electronics Co., Ltd 
mar@mar-Vostro-200:~$ lshw -c network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82562V-2 10/100 Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 02
       serial: 00:1a:a0:9e:e1:2e
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.5.1-k firmware=1.1-2 latency=0 multicast=yes port=twisted pair
       resources: irq:42 memory:fdfc0000-fdfdffff memory:fdfff000-fdffffff ioport:fe00(size=32)
  *-network:0
       description: Ethernet interface
       physical id: 1
       logical name: usb0
       serial: 02:79:33:34:30:3c
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device ip=192.168.42.43 multicast=yes
  *-network:1
       description: Wireless interface
       physical id: 2
       bus info: usb@1:6
       logical name: wlan0
       serial: c8:60:00:d4:9e:86
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192cu multicast=yes wireless=unassociated
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
mar@mar-Vostro-200:~$

---

### Post by chili555 on 2012-10-09
I'm fairly certain it's not going to connect if the cell phone is connected and has an IP address. Also, I am troubled by this:> *-network:1
description: Wireless interface
physical id: 2
bus info: usb@1:6
logical name: wlan0
serial: c8:60:00:d4:9e:86
capabilities: ethernet physical wireless
configuration: broadcast=yes [COLOR="Red"]driver=rtl8192cu[/COLOR] multicast=yes wireless=unassociatedDidn't we blacklist **rtl**8192cu in favor of 8192cu which you downloaded and compiled? Which is loaded?```
lsmod | grep 8192
```

---

### Post by Marthewicked on 2012-10-09
> **chili555 said:**
> I'm fairly certain it's not going to connect if the cell phone is connected and has an IP address. Also, I am troubled by this:Didn't we blacklist **rtl**8192cu in favor of 8192cu which you downloaded and compiled? Which is loaded?```
lsmod | grep 8192
```

no i check wehn i disconnect but to come back on the forum i have to connect to cell phone.  The cell phone is rooted so i can tether whether im connected to wireless or data. This time im connected to the same wireless network im trying to connect on the desktop

---

### Post by Marthewicked on 2012-10-09
mar@mar-Vostro-200:~$ lsmod | grep 8192
rtl8192c_common        69519  0 
mac80211              436455  2 rtl8192c_common,rtlwifi
8192cu                487753  0 
mar@mar-Vostro-200:~$ without cell phone here it is.....
without: command not found
mar@mar-Vostro-200:~$ without cell phone here it is.....
without: command not found
mar@mar-Vostro-200:~$ lsmod | grep 8192
rtl8192c_common        69519  0 
mac80211              436455  2 rtl8192c_common,rtlwifi
8192cu                487753  0 
mar@mar-Vostro-200:~$

---

### Post by Marthewicked on 2012-10-09
Guys,

Thank you so much, i just want to say that. I am sure this is pain, cause im getting frustrated and i cant imagine how you guys feel. I just want to say thank you whether this works or not.
mar

---

### Post by chili555 on 2012-10-09
Please detach the cell phone, try to connect twice and show us:```
sudo cat /var/log/syslog | grep etwork | tail -n20
```> $ lsmod | grep 8192
rtl8192c_common 69519 0
mac80211 436455 2 rtl8192c_common,rtlwifi
[COLOR="Red"]8192cu[/COLOR] 487753 0 Cool! Perfect.

I enjoy helping! I'm not frustrated at all.

---

### Post by Marthewicked on 2012-10-09
mar@mar-Vostro-200:~$ sudo cat /var/log/syslog | grep etwork | tail -n20
[sudo] password for mar: 
Oct  9 22:48:23 mar-Vostro-200 NetworkManager[758]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Oct  9 22:48:23 mar-Vostro-200 NetworkManager[758]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Oct  9 22:48:43 mar-Vostro-200 NetworkManager[758]: <info> (wlan0): IP6 addrconf timed out or failed.
Oct  9 22:48:43 mar-Vostro-200 NetworkManager[758]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Oct  9 22:48:43 mar-Vostro-200 NetworkManager[758]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Oct  9 22:48:43 mar-Vostro-200 NetworkManager[758]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Oct  9 22:49:08 mar-Vostro-200 NetworkManager[758]: <warn> (wlan0): DHCPv4 request timed out.
Oct  9 22:49:08 mar-Vostro-200 NetworkManager[758]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 3619
Oct  9 22:49:08 mar-Vostro-200 NetworkManager[758]: <info> Activation (wlan0) Stage 4 of 5 (IPv4 Configure Timeout) scheduled...
Oct  9 22:49:08 mar-Vostro-200 NetworkManager[758]: <info> Activation (wlan0) Stage 4 of 5 (IPv4 Configure Timeout) started...
Oct  9 22:49:08 mar-Vostro-200 NetworkManager[758]: <info> (wlan0): device state change: ip-config -> failed (reason 'ip-config-unavailable') [70 120 5]
Oct  9 22:49:08 mar-Vostro-200 NetworkManager[758]: <warn> Activation (wlan0) failed for access point (MFGT1)
Oct  9 22:49:08 mar-Vostro-200 NetworkManager[758]: <info> Marking connection 'MFGT1' invalid.
Oct  9 22:49:08 mar-Vostro-200 NetworkManager[758]: <warn> Activation (wlan0) failed.
Oct  9 22:49:08 mar-Vostro-200 NetworkManager[758]: <info> Activation (wlan0) Stage 4 of 5 (IPv4 Configure Timeout) complete.
Oct  9 22:49:08 mar-Vostro-200 NetworkManager[758]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Oct  9 22:49:08 mar-Vostro-200 NetworkManager[758]: <info> (wlan0): deactivating device (reason 'none') [0]
Oct  9 22:49:08 mar-Vostro-200 NetworkManager[758]: <info> Policy set 'Wired connection 2' (usb0) as default for IPv4 routing and DNS.
Oct  9 22:49:08 mar-Vostro-200 NetworkManager[758]: <info> Policy set 'Wired connection 2' (usb0) as default for IPv4 routing and DNS.
Oct  9 22:49:08 mar-Vostro-200 NetworkManager[758]: <info> (wlan0): supplicant interface state: completed -> disconnected
mar@mar-Vostro-200:~$

---

### Post by chili555 on 2012-10-09
I'm still troubled that it doesn't ask for the key. Please post:```
sudo cat /etc/NetworkManager/system-connections/MFGT1  
```It will, hopefully, display your WEP key in clear text. DO NOT POST IT. Obscure it thus:> [802-11-wireless-security]
key-mgmt=none
auth-alg=open
wep-key0=[COLOR="Red"]92xxyyzzwhatever[/COLOR]
wep-key-type=1We are interested in whether it shows and if it's correct. We also hope we see 'infrastructure.'

---

### Post by Marthewicked on 2012-10-09
mar@mar-Vostro-200:~$ sudo cat /etc/NetworkManager/system-connections/MFGT1
[sudo] password for mar: 

[connection]
id=MFGT1
uuid=0e7bce6c-12b4-44f8-a30a-26528794872b
type=802-11-wireless

[802-11-wireless]
ssid=MFGT1
mode=infrastructure
mac-address=C8:60:00:D4:9E:86
security=802-11-wireless-security

[802-11-wireless-security]
key-mgmt=none
wep-key0=529a65xxgh

[ipv4]
method=auto

[ipv6]
method=auto
mar@mar-Vostro-200:~$

---

### Post by chili555 on 2012-10-09
I assume the key is correct under the obscurity. Sorry; retiring for the evening. I'll check in tomorrow.

---

### Post by Marthewicked on 2012-10-09
No problem at all. Thank you so much.
If possible, is it better to clean and clear all settings and drivers and download the drivers on clean slate? 
Thanks,
Mar

---

### Post by daslinkard on 2012-10-10
> **Marthewicked said:**
> Guys,

Thank you so much, i just want to say that. I am sure this is pain, cause im getting frustrated and i cant imagine how you guys feel. I just want to say thank you whether this works or not.
mar
Not frustrated either....but I am determined just like the others trying to help you....I know they, just like me, want to get this resolved for you!

---

### Post by Marthewicked on 2012-10-10
Thank! Is it possible to start clean? To start from scratch driver clean then driver install followed reboot?
Mar

---

### Post by chili555 on 2012-10-10
The first thing I'd try is to delete all your access point-specific settings in NM and reboot. Let NM find MFGT1 fresh and try to connect:```
sudo rm -rf /etc/NetworkManager/system-connections/*
```The command sequence 'rm -rf' removes forcefully and permanently and is dangerous. Proofread carefully, as I am doing, before you press Enter.

Reboot and let us hear your report.

---

### Post by Marthewicked on 2012-10-10
Thanks, will reboot now, sorry i have not looked sooner of the reply, i wish there is  notification.

---

### Post by Marthewicked on 2012-10-10
> **chili555 said:**
> The first thing I'd try is to delete all your access point-specific settings in NM and reboot. Let NM find MFGT1 fresh and try to connect:```
sudo rm -rf /etc/NetworkManager/system-connections/*
```The command sequence 'rm -rf' removes forcefully and permanently and is dangerous. Proofread carefully, as I am doing, before you press Enter.

Reboot and let us hear your report.

After reboot i saw that promising words on top right corner "Wireless Networks Available" and i was thinking this is it we finally got this to surrender.  But refreshed and refreshed and came back to wireless network disconnected you are now offline, bummer!
mar

---

### Post by chili555 on 2012-10-10
And it did or did not ask for your WEP key? It will help me to get details as to the behavior when you reply.>  i wish there is notification. There is; use thread tools at the top to subscribe and get an instant email.

---

### Post by Marthewicked on 2012-10-10
> **chili555 said:**
> And it did or did not ask for your WEP key? It will help me to get details as to the behavior when you reply.There is; use thread tools at the top to subscribe and get an instant email.

Thanks, yes it did ask for web key and the wifi symbol link refreshed and refreshed few times and came back disconnected.

---

### Post by chili555 on 2012-10-10
Is your routers WEP encryption set to Open or Shared? I noticed that your file differed from mine, connected to a WEP access point:```
[connection]
id=qwest4288
uuid=cb140383-dd33-46e5-bfa1-903889f0fc43
type=802-11-wireless
timestamp=1349014646

[802-11-wireless]
ssid=qwest4288
mode=infrastructure
mac-address=xx:94:6B:99:55:xx
security=802-11-wireless-security

[802-11-wireless-security]
key-mgmt=none
[COLOR="Red"]auth-alg=open[/COLOR]
wep-key0=92xxx60xxx
[COLOR="Red"]wep-key-type=1[/COLOR]

[ipv4]
method=auto

[ipv6]
method=ignore

```Your relevant section is, or was:```
[connection]
id=MFGT1
uuid=0e7bce6c-12b4-44f8-a30a-26528794872b
type=802-11-wireless

[802-11-wireless]
ssid=MFGT1
mode=infrastructure
mac-address=C8:60:004:9E:86
security=802-11-wireless-security

[802-11-wireless-security]
key-mgmt=none
wep-key0=529a65xxgh

[ipv4]
method=auto

[ipv6]
method=auto
```How is your router set up?

---

### Post by Marthewicked on 2012-10-10
it is stil the same as you have posted.  Yes it is wep. I checked my laptop which connects to the network and the settings were wep 40/128 bit-key......

---

### Post by Marthewicked on 2012-10-10
How can i delete the driver? Then maybe redownload and start fresh not that it will fix or not but it is worth a try.

---

### Post by chili555 on 2012-10-10
There is no need to delete it. When you install the freshly downloaded driver, the old one will be over-written.

Have you tried with no encryption at all? Even better, with WPA2-PSK?

---

### Post by Marthewicked on 2012-10-10
On the drop down menu i chose none and i clicked on save but nothing happens. I does not refresh or connect.  I click on my wireless or the edit on the bottom and no response . I can click as many times as i want but no response.

---

### Post by Marthewicked on 2012-10-10
Rebooted and now i clicked on the network and it responded/asked the key. I clicked on the edit and to see whether the "none" no key on the wireless security setting still in place and it is still in place yet still asked the key code. Then it refreshed and few seconds later replied with "wireless network disconnected" and it tries again and again with the same response.

---

### Post by Marthewicked on 2012-10-10
No change on wpa/wpa2 personal on settings. When i wanted to set the wpa/wpa2 on enterprise, it would hightlight "Save' button on the bottom right when entered key. No change on leap and dynamic either, even though i dont know what those are.

---

### Post by chili555 on 2012-10-10
> **Marthewicked said:**
> No change on wpa/wpa2 personal on settings. When i wanted to set the wpa/wpa2 on enterprise, it would hightlight "Save' button on the bottom right when entered key. No change on leap and dynamic either, even though i dont know what those are.You certainly don't want Enterprise or LEAP, WPA2-Personal is preferred.

After you make changes, there should be a place to save. Then, I'd delete your old settings and reboot.```
sudo rm -rf /etc/NetworkManager/system-connections/*
```If you can't find a place to save in the router, maybe I can help. What is the make and model of router?

---

### Post by Marthewicked on 2012-10-10
Wait, you were asking me on the desktop  correct?  I am connected to the router through my cell phone then to computer, that is how im coming back online and so forth.  I will delete as you suggest and try on personal then see what happens, for the meantime, i will get router info.

---

### Post by Marthewicked on 2012-10-10
WPA/WPA2 never connected even before, i could have saved that one and it did.  WPA/WPA2 on enterprise would not have saved, or it would not let me.  I ran the code and rebooted no difference.

---

### Post by chili555 on 2012-10-10
In the router, set WPA2-PSK, not WPA/WPA2 if possible. Then, back in the computer, delete the settings, reboot, and try to connect. If you can't, post:```
dmesg | grep -e wlan -e 8192
```

---

### Post by Marthewicked on 2012-10-10
I dont have access to the router :-( long story and i dont want to get into that.  Long story.  However im connected and know it works because i can connect oher stuff, cell phone and other computers.

here is for the code,

mar@mar-Vostro-200:~$ dmesg | grep -e wlan -e 8192
[    0.717333] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[   11.965007] CHIP TYPE: RTL8188C_8192C
[   11.967560] ====> ReadAdapterInfo8192C
[   12.367366] readAdapterInfo_8192CU(): REPLACEMENT = 1
[   12.367369] <==== ReadAdapterInfo8192C in 400 ms
[   12.369651] usbcore: registered new interface driver rtl8192cu
[   13.496710] rtl8192cu_hal_init in 692ms
[   13.507873] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   13.508464] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   14.735205] Error: Driver 'rtl8192cu' is already registered, aborting...
[  181.579446] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  181.587415] rtl8192c_set_FwJoinBssReport_cmd mstatus(1)
[  191.760053] wlan0: no IPv6 routers present
[  227.219506] rtl8192c_set_FwJoinBssReport_cmd mstatus(0)
[  231.175362] rtl8192c_set_FwJoinBssReport_cmd mstatus(1)
[  241.472020] wlan0: no IPv6 routers present
[  276.218773] rtl8192c_set_FwJoinBssReport_cmd mstatus(0)
[  280.254789] rtl8192c_set_FwJoinBssReport_cmd mstatus(1)
[  290.384032] wlan0: no IPv6 routers present
[  326.222672] rtl8192c_set_FwJoinBssReport_cmd mstatus(0)
[  330.252582] rtl8192c_set_FwJoinBssReport_cmd mstatus(1)
[  340.480026] wlan0: no IPv6 routers present
[  375.219565] rtl8192c_set_FwJoinBssReport_cmd mstatus(0)
[  676.214220] rtl8192c_set_FwJoinBssReport_cmd mstatus(1)
[  686.320092] wlan0: no IPv6 routers present
[  721.226135] rtl8192c_set_FwJoinBssReport_cmd mstatus(0)
[  725.247139] rtl8192c_set_FwJoinBssReport_cmd mstatus(1)
[  735.632020] wlan0: no IPv6 routers present
[  771.215786] rtl8192c_set_FwJoinBssReport_cmd mstatus(0)
[  775.217663] rtl8192c_set_FwJoinBssReport_cmd mstatus(1)
[  785.296024] wlan0: no IPv6 routers present
[  820.219814] rtl8192c_set_FwJoinBssReport_cmd mstatus(0)
[  824.269945] rtl8192c_set_FwJoinBssReport_cmd mstatus(1)
[  834.784026] wlan0: no IPv6 routers present
[  870.217474] rtl8192c_set_FwJoinBssReport_cmd mstatus(0)
mar@mar-Vostro-200:~$

---

### Post by chili555 on 2012-10-10
> [ 12.369651] usbcore: registered [COLOR="Red"]new interface driver rtl8192cu[/COLOR]
[ 13.496710] rtl8192cu_hal_init in 692ms
[ 13.507873] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 13.508464] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 14.735205] Error: Driver 'rtl8192cu' is already registered, aborting...May I see:```
lsmod | grep 819
cat /etc/modprobe.d/blacklist.conf | tail -n10
```

---

### Post by Marthewicked on 2012-10-10
Yes sir you may  .....i can run some or same codes to my laptop which i just connected in case you need a control, this ubuntu diagnose might as well be a scientific research

mar@mar-Vostro-200:~$ lsmod | grep 819
rtl8192c_common        69519  0 
mac80211              436455  2 rtl8192c_common,rtlwifi
8192cu                487753  0 
mar@mar-Vostro-200:~$ cat /etc/modprobe.d/blacklist.conf | tail -n10
# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist rtl8192cu
mar@mar-Vostro-200:~$

---

### Post by steeldriver on 2012-10-10
umm did you at some point(around p.3 of the thread) echo "modprobe **rtl**8192cu" to your /etc/rc.local file? maybe that's why we are seeing load attempts despite the blacklist

---

### Post by Marthewicked on 2012-10-10
> **steeldriver said:**
> umm did you at some point(around p.3 of the thread) echo "modprobe **rtl**8192cu" to your /etc/rc.local file? maybe that's why we are seeing load attempts despite the blacklist

Yes, and it worked. But when i started or booted the computer i get black screen with white letters and i have to unplug and boot then when i plug back in same issues.  But sometimes it it did not do that on boot only when plugged back in.  That is why i got 12.04 LTS start clean fresh and redownloaded the driver by following same instructions.

---

### Post by Marthewicked on 2012-10-10
So many codes and things i have done i dont even remember so i dont know if any of codes delted or added or anything, really.

---

### Post by Marthewicked on 2012-10-11
> **steeldriver said:**
> umm did you at some point(around p.3 of the thread) echo "modprobe **rtl**8192cu" to your /etc/rc.local file? maybe that's why we are seeing load attempts despite the blacklist

i went back and redid all...to se how i got to where i am ....

here is how that folder looks like....let me know if it correct or something is wrong....

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

modprobe rtl8192cu
echo "0b05 17ab" > /sys/bus/usb/drivers/rtl8192cu/new_id

exit 0

---

### Post by steeldriver on 2012-10-11
I would comment out those 2 lines (at least while we're debugging) and reboot - but let's see what chili555 has to say about that

```
[COLOR=Red]#[/COLOR] modprobe rtl8192cu
[COLOR=Red]#[/COLOR] echo "0b05 17ab" > /sys/bus/usb/drivers/rtl8192cu/new_id
```

---

### Post by Marthewicked on 2012-10-11
i did that and turned all blue and rebooted but still the same no change.

I had came across something, look this up shouldnt i have Encryption key : xxxxxxxx Security mode : restricted or open or whatever below the line retry off?  I am just curious....

mar@mar-Vostro-200:~$ iwconfig
lo        no wireless extensions.

usb0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"MFGT1"  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:18:01:EB:B3:C3   
          Bit Rate:54 Mb/s   Sensitivity:0/0  
      **   * Retry:off   RTS thr:off   Fragment thr:off***
         i am missing encryption key here and security mode here......can anyne figure this out why? 
         Power Management:off
          Link Quality=100/100  Signal level=59/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

mar@mar-Vostro-200:~$

---

### Post by steeldriver on 2012-10-11
not necessarily I don't think - here is mine (this is also an N13 but it is the other variant with the Ralink chipset)

```
wlan1     IEEE 802.11bgn  ESSID:"NETGEAR68"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: xx:xx:xx:xx:xx:xx   
          Bit Rate=78 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=-29 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:384  Invalid misc:30   Missed beacon:0
```You will get more detailed info including the encryption mode from nm-tool or nmcli:

```
nmcli dev wifi list
```I don't really know what to suggest here (apart from waiting for chili or one of the other wireless gurus to step back in). It wouldn't hurt to reinstall nm since we didn't do that after purging wicd

```
sudo apt-get install --reinstall network-manager
```At some point we could also try creating the connection via /etc/network/interfaces (i.e. the older networking service instead of network-manager)

---

### Post by Marthewicked on 2012-10-11
Never mind my last post i checked on another laptop and the laptop is the same code but somethings are not matching up and i was thinking if anything suspicious.....

  	 	 	 	 	 	   mar@ubuntu:~$ iwconfig  
 lo        no wireless extensions.  
 

 eth0      no wireless extensions.  
 

 wlan0     IEEE 802.11bg  ESSID:"MFGT1"   
           Mode:Managed  Frequency:2.437 GHz  Access Point: 00:18:01:EB:B3:C3    
           Bit Rate=24 Mb/s   Tx-Power=20 dBm    
           Retry  long limit:7   RTS thr:off   Fragment thr:off  
           Power Management:off  
           Link Quality=41/70  Signal level=-69 dBm   
           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0  
           Tx excessive retries:0  Invalid misc:28   Missed beacon:0  
 

 vboxnet0  no wireless extensions.  
 

 mar@ubuntu:~$

---

### Post by chili555 on 2012-10-11
Unfortunately, we have tried everything I know to try unsuccessfully...except one. Here is the salient part of a long thread where the poster and i went through the same agony as you and only got it working with ndiswrapper: [http://ubuntuforums.org/showthread.php?t=2036445&highlight=8192cu&page=5](http://ubuntuforums.org/showthread.php?t=2036445&highlight=8192cu&page=5)

If yours is a 32-bit system, you can use the files I attached there.```
arch [COLOR="Red"]<--32-bit returns 'i686'[/COLOR]
```If you need 64-bit, post back.>  had came across something, look this up shouldnt i have Encryption key : xxxxxxxx Security mode : restricted or open or whatever below the line retry off? I am just curious....
Those details are not revealed to ordinary users; sudo iwconfig won't tell, either, under NM.

---

### Post by Marthewicked on 2012-10-11
> **chili555 said:**
> Unfortunately, we have tried everything I know to try unsuccessfully...except one. Here is the salient part of a long thread where the poster and i went through the same agony as you and only got it working with ndiswrapper: [http://ubuntuforums.org/showthread.php?t=2036445&highlight=8192cu&page=5](http://ubuntuforums.org/showthread.php?t=2036445&highlight=8192cu&page=5)

If yours is a 32-bit system, you can use the files I attached there.```
arch [COLOR=Red]<--32-bit returns 'i686'[/COLOR]
```If you need 64-bit, post back.Those details are not revealed to ordinary users; sudo iwconfig won't tell, either, under NM.

32 bit..  I will try but there are alot of instructions to follow.  Is there a way you can post here from start to finish follow along codes?  If possible.

Also, if i went and installed 11.04 then upgraded to 11.10 then 12.04, is that something that is possible?  I can connect on 11.04 but had problems with the driver being unresponsive when and sometimes after boot.  When it booted it connected to web fine etc.

---

### Post by Marthewicked on 2012-10-11
guys,

I found something weird, i created a wifi hotspot on my phone by connecting to data WPA2 PSK and guess what? it connected with all the bars fully lit up ..... so this is not an issue of a driver or the hardware or equipment.  There is something ging on with the connection between the router and usb .

I mean why would it connect to my cell phone wife and not the router?  Frequency?

---

### Post by Marthewicked on 2012-10-11
mar@mar-Vostro-200:~$ lsmod | grep 819
8192cu                487753  0 
mar@mar-Vostro-200:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"speedracer"  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 98:0C:82:44UD:42   
          Bit Rate:130 Mb/s   Sensitivity:0/0  
          Retry*ff   RTS thr*ff   Fragment thr*ff
          Power Management*ff
          Link Quality=100/100  Signal level=100/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

mar@mar-Vostro-200:~$ haha speedracer is my wifi name and shows there too clearly as you can see the access point is different than wifi since im on mobile data now
No command 'haha' found, did you mean:
 Command 'hacha' from package 'hevea' (main)
 Command 'aha' from package 'aha' (universe)
haha: command not found
mar@mar-Vostro-200:~$ 
mar@mar-Vostro-200:~$ 
mar@mar-Vostro-200:~$ lshw -c network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82562V-2 10/100 Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 02
       serial: 00:1a:a0:9e:e1:2e
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.5.1-k firmware=1.1-2 latency=0 multicast=yes port=twisted pair
       resources: irq:42 memory:fdfc0000-fdfdffff memory:fdfff000-fdffffff ioport:fe00(size=32)
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@2:2
       logical name: wlan0
       serial: c8:60:00:d4:9e:86
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192cu ip=192.168.43.29 multicast=yes wireless=IEEE 802.11bgn
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
mar@mar-Vostro-200:~$ sudo iwlist wlan0 scan
[sudo] password for mar: 
wlan0     Scan completed :
          Cell 01 - Address: 98:0C:82:44*D:42
                    ESSID:"speedracer"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key*n
                    Bit Rates:65 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=100/100  Signal level=100/100  
          Cell 02 - Address: 00:18:01:EB:B3:C3
                    ESSID:"MFGT1"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key*n
                    Bit Rates:54 Mb/s
                    Quality=100/100  Signal level=56/100  
          Cell 03 - Address: 00:1F:90:CF:2D*4
                    ESSID:"VSTA5"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key*n
                    Bit Rates:54 Mb/s
                    Quality=100/100  Signal level=44/100  
          Cell 04 - Address: 00:1F:90:B9:81:88
                    ESSID:"8KFU5"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key*n
                    Bit Rates:54 Mb/s
                    Quality=100/100  Signal level=42/100  

mar@mar-Vostro-200:~$

I really appreciated if anyone can see similarities or differences....Thanks

I appreciated all the time you put in to this ....i can never repay you with any amount of anything!
Thank you guys,
Mar

---

### Post by chili555 on 2012-10-12
So where do you want to go now? ndiswrapper? Or...??

---

### Post by Marthewicked on 2012-10-14
> **chili555 said:**
> So where do you want to go now? ndiswrapper? Or...??

Ndiswrapper gets connection but heard it is not reliable or steady connection, what do you think? You dont see difference between the two wifi? Cell and router?

---

### Post by steeldriver on 2012-10-14
you don't have any kind of MAC filtering enabled on the router by any chance?

---

### Post by chili555 on 2012-10-15
> **Marthewicked said:**
> Ndiswrapper gets connection but heard it is not reliable or steady connection, what do you think? You dont see difference between the two wifi? Cell and router?ndiswrapper works quite well most of the time; not always. However, now you can't connect at all. Isn't it at least worth a try?

I see nothing in your postings above that give me the slightest clue about something we might fix given that you haven't any administration privileges to the router MFGT1.

---

### Post by Marthewicked on 2012-10-15
> **chili555 said:**
> ndiswrapper works quite well most of the time; not always. However, now you can't connect at all. Isn't it at least worth a try?

I see nothing in your postings above that give me the slightest clue about something we might fix given that you haven't any administration privileges to the router MFGT1.

Agree and i thank you so much for the help and i will give it a try. I will have to turn it on. I have not been out here the last couple days because no display and no BIOS just two short beeps and continues. It is dell vestro 200 i will do research and get back to here with the ndiswarapper.
I will pass the help as much as i can and i appreciated it very much.

---

