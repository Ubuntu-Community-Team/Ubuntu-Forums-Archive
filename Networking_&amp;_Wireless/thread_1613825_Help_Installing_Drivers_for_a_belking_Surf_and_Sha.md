---
title: "Help Installing Drivers for a belking Surf and Share wireless Controller/Antenna"
date: 2010-11-04
forum: Networking &amp; Wireless
---

### Post by ubunewbi on 2010-11-04
Hi, I have just installed Ubuntu 10.10 on a pc as a duel boot, On the computer I use a belkin surf and share n speed controller to connect wireless ( pc doesn't have a wireless connection) I have found the correct driver RLT8192SU from realtek and unzipped it and moved the contents to a flash drive. The problem is I am a total noob to Linux based systems and i have no ideal how to install the contents, there is a read me file but it makes no sense to me and i have absolutely no clue how to install the driver so i have no internet. Is there an easier way to install or step by step instructions? Any help will be greatly appreciated and I would like 2 thank you all in advance for your help.

---

### Post by Duplin on 2010-11-04
I'm not running 10.10, now using 10.04, but I had the same problem with my adapter for several days. It uses the same Realtek driver you mentioned. Tonight I installed ndiswrapper and used the Windows XP driver that came on the installation disk, rebooted and it works great now.

---

### Post by dforthman on 2010-11-05
Please note, I have only been able to get this working on 32-bit Ubuntu 10.10. the 64-bit version always threw errors when compiling.
I also did not try ndiswrapper. Why hack a windows driver when there's a linux driver available?

Here's what I did to get it working last night:
```

unzip RTL8191SU_usb_linux_v2.6.0006.20100625.zip
cd rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver
tar zxf rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20100625.tar.gz
cd rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625
sudo su
make && make install
exit

```
Plug in the wireless adapter. It may take a few moments, but it will come on and start searching for access points.

I haven't been able to get the same signal quality I have in Windows, but atleast it works.

---

### Post by ubunewbi on 2010-11-05
I saw the ndiswrapper but there isn't a version for 10.10, How do you install the code (did I mention that I am a total noob who has just started walking in the Linux universe) do I create a folder on the desktop to install the code? I would assume that I can copy and paste the lines of code from the zipped folder.  Thank you guys for trying to help a total noob I am sure with your help we can get this working.

---

### Post by dforthman on 2010-11-05
Put the downloaded .zip file in your Home folder, then just open a terminal and copy/paste what is in the Code section above.
Modify the file names as needed.

---

### Post by chili555 on 2010-11-05
Please note that, in order to compile these drivers, you need the packages *build-essential* and *kernel-headers-generic* installed. They are on the install CD, if I remember correctly, so you can add the CD as a source in System > Administration > Synaptic and search for them.

---

### Post by ubunewbi on 2010-11-05
THANKS, I put the folder in my home folder and and unzipped it, copied and pasted the code in the terminal window, it didn't work so I unplugged the antenna and restarted. after the restart I plugged the antenna back in and it worked great (using it now to post this). Thank you all for the help I was so lost I would have never figured it out on my own.

Props to dforthman for the code 

Again thanks and i owe u a beer :P

---

