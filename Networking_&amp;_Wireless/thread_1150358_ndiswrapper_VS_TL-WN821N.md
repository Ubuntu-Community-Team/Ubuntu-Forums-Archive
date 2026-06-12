---
title: "ndiswrapper VS TL-WN821N"
date: 2009-05-06
forum: Networking &amp; Wireless
---

### Post by julian_mintz on 2009-05-06
I just installed 9.04 on my PC. But I can not make my Wireless USB work!
I try to use ndiswrapper, download and install 1.54 ndiswrapper. And I used windows driver in ndiswrapper. Nothing error prompts.
But when I use "ndiswrapper -l" to see the result, it just prompts:
arusb_lh : driver installed
I can not find "device (0CF3:1002) present" message. But I am sure that the wireless adapter is connected.
And I use "lsusb", the adapter is in the USB list.
How could I make it work? Anyone could help?

---

### Post by julian_mintz on 2009-05-06
Could anyone help me on this?:popcorn:

---

### Post by julian_mintz on 2009-05-06
I am still waiting for answers...

---

### Post by flash63 on 2009-05-08
Hy,
i build a driver-package for atheros ar9170 based USB-Dongles.

See [http://ubuntuforums.org/showthread.php?t=1150835](http://ubuntuforums.org/showthread.php?t=1150835)
and
[http://ubuntuforums.org/showthread.php?t=1052619&page=2](http://ubuntuforums.org/showthread.php?t=1052619&page=2)
for details.

---

### Post by Sistereliz on 2010-12-06
Hi! I am very new to Ubuntu 10.04 and I have just been through a mammoth process of getting my tl-wn821n adaptor to work, so I can use my new pocket wifi. But I am so glad that I have come through it all, I want to share it. I hope I can remember the steps.

I installed ndiswrapper
[http://www.ubuntu1501.com/2007/11/wireless-in-gutsy-gibbon-with.html](http://www.ubuntu1501.com/2007/11/wireless-in-gutsy-gibbon-with.html)
(It just so happens I have a Dell Inspiron 1501, but I think this would work fine with others).
I had to follow instruction 4 twice.
Step 6 did not work.

I downloaded the driver needed: ar9170
[http://linuxwireless.org/en/users/Drivers/ar9170](http://linuxwireless.org/en/users/Drivers/ar9170)
Under 'Official firmware devices', 'One stage', I clicked on ar9170 and opened the folder. Then I extracted it into my Desktop.

I downloaded compat-wireless
[http://www.orbit-lab.org/kernel/compat-wireless-2.6-stable/v2.6.32/compat-wireless-2.6.32.3.tar.bz2](http://www.orbit-lab.org/kernel/compat-wireless-2.6-stable/v2.6.32/compat-wireless-2.6.32.3.tar.bz2)

I opened the terminal and typed in
tar -xf /root/compat-wireless-2.6.32.3.tar.bz2
cd compat-wireless-2.6.32.3

I installed aircrack-ng by typing in the terminal
sudo apt-get install build-essential

sudo apt-get install aircrack-ng

Then wrote in terminal
airmon-ng
and found where my wireless adapter was (wlan2 in my case)

I then wrote in terminal 
airmon-ng start wlan2

Then in terminal
cd /home/username/Desktop/compat-wireless-2.6.32.3.bz2
(This finally worked, as my instructions didn't have /home/[my username, you use yours]/Desktop)

Then in terminal
make install

Then
make unload

Finally, after all of this
sudo reboot

And it restarted and everything worked! I went to the icon at the top right of the screen
clicked on my pocket wifi, which was finally there, and entered my key number.

And it worked! And now it is 2:00am and I need to get to bed, but I thought
I'd try to note all this down before I forgot. I am sure I have missed some steps, and
maybe not all of it is essential, but this might help someone.

Thank you, Ubuntu community!!!!

God bless you all :)

---

### Post by Sistereliz on 2010-12-06
PS. You must also extract compat-wireless into your Desktop, I forgot to do that the first time and many more wasted minutes.

---

### Post by masque7 on 2011-07-14
For anyone still having difficulties, I have got the device works with ndiswrapper without having to compile any software. All that is needed are simple GUI tools.
[http://ubuntuforums.org/showthread.php?p=11046879#post11046879](http://ubuntuforums.org/showthread.php?p=11046879#post11046879)

---

