---
title: "Broadcom 4312 Not find Wireless connection - Ubuntu 12.10"
date: 2012-10-25
forum: Networking &amp; Wireless
---

### Post by moroccan92 on 2012-10-25
```
sudo modprobe -r b43 ssb wl 
sudo apt-get remove bcmwl-kernel-source
 sudo apt-get install build-essential dkms linux-headers-generic 
sudo  apt-get install bcmwl-kernel-source
```when i do this code , my computer find my wireless connection , but when i restart my computer , it comeback like the first time , he doesn't find any wireless connection
i have broadcom 4312 and Ubuntu 12.10

---

### Post by westie457 on 2012-10-25
Those are not the right drivers for your wifi card.

Remove all of the drivers you have installed. Use 'Synaptic Package Manager' to do this (a GUI interface).

If not already installed do ```
sudo apt-get install synaptic
```

In Synaptic do a search for bcm. all packages with a green box next to them select for complete removal.

Then mark 'firmware-b43-lpphy-installer' for installation and accept the recommended for installation. Finally click on 'Apply'.

If prompted to reboot it is safe to do.

Your wireless should now be working.

Thank you

---

### Post by moroccan92 on 2012-10-25
i do exactly what you say , and it's still don't work

---

### Post by westie457 on 2012-10-25
Okay we will now go through the diagnostic process. 

Open a terminal. Copy and Paste this command - to avoid any typos -```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```

If nothing happens follow the instructions in this post. [http://ubuntuforums.org/showpost.php?p=12317058&postcount=8](http://ubuntuforums.org/showpost.php?p=12317058&postcount=8) to generate the text file.

I have to disappear for a while and will check back later so do not panic if no reply when you really expect one. Got to go to work.

Thank you

---

### Post by moroccan92 on 2012-10-25
any of 2 solutions works :s when i write my password , i don't have any txt file 
in fact , when i use this line 
```
sudo modprobe b43
```
the wireless connection is found again !!!

---

### Post by moroccan92 on 2012-10-25
THIS IS THE SOLUTION ::


Code:    
 ```
sudo apt-get remove bcmwl-kernel-source 
```If the system requires a reboot do not, it can wait a few minutes  until we have finished. Warning - in some cases rebooting now can remove  the wired capability as well.

Next is      Code:
     ```
sudo apt-get install linux-firmware-nonfree 
```After this has installed wait for about 2 minutes and check if  there is any wireless networks available. If none show up then two more  terminal commands     


Code:

```
sudo rmmod ssl  sudo modprobe b43 
```
and finally
```
sudo su 
 echo b43 >> /etc/modules 
 exit

```

---

### Post by westie457 on 2012-10-26
Glad it is now working for you

---

### Post by moroccan92 on 2012-10-26
[westie457]("http://ubuntuforums.org/member.php?u=970779")
thank you.

---

