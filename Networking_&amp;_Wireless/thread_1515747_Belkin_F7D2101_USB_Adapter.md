---
title: "Belkin F7D2101 USB Adapter"
date: 2010-06-22
forum: Networking &amp; Wireless
---

### Post by Jaxzen on 2010-06-22
I'm extremely new to Linux and just built a machine for its sole use and decided to go with a USB adapter for internet. I bought a Belkin F7D2101 and it just will not install.

I've looked around, seen some kind of application to let you run Windows drives on Linux but I have no idea how to install anything. Nothing seems to work and if I double click any .exe files it fails. I honestly have no idea what I'm doing and feel overly-ambitious. 

Is it even possible to use this adapter with Ubunutu? If so, how do I get this thing working? I've stared and tinkered for two hours now :S

---

### Post by eteq on 2010-08-24
I managed to get this adapter working under Ubuntu (lucid 64).  Pretty straightforward actually... I got most of this from [http://ubuntuforums.org/showthread.php?t=1522815](http://ubuntuforums.org/showthread.php?t=1522815) , although it required a some slight changes. Hopefully this will also work for you:

Run this command:
```
sudo gedit /etc/udev/rules.d/network_drivers.rules 
```

And add this line to the file (which may be empty) and save:

```
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="050d", ATTR{idProduct}=="845a", RUN+="/sbin/modprobe -qba r8192s_usb"
```

Then run this command:
```
sudo gedit /etc/modprobe.d/network_drivers.conf 
```

And add this file (and save)
```
install r8192s_usb /sbin/modprobe --ignore-install r8192s_usb $CMDLINE_OPTS; /bin/echo "050d 845a" > /sys/bus/usb/drivers/rtl819xU/new_id
```

Finally, download this file:
[http://svn.debian.org/wsvn/kernel/dists/trunk/firmware-nonfree/realtek/RTL8192SU/rtl8192sfw.bin](http://svn.debian.org/wsvn/kernel/dists/trunk/firmware-nonfree/realtek/RTL8192SU/rtl8192sfw.bin)

and copy it to the directory ```
/lib/firmware/RTL8192SU/ 
```

To summarize, the first two commands tell linux to load the correct driver when that particular USB device is plugged in (which I figured out with the lsusb command), and the firmware is used to load the information the wireless chip needs to run.

---

### Post by majormar on 2010-09-08
Thanks for the instructions. This worked for me first time I tried it. I just had to create the directory to put the firmware file with this command ...```
sudo mkdir /lib/firmware/RTL8192SU
```before I copied the file there since it didn't already exist for me.

Then I unplugged and re-plugged the usb adaptor and it worked like a champ!

---

### Post by ahanssen on 2010-09-28
Thank you for this! I hadn't registered or commented even though I've been using these forums for weeks. Thank you for something that really works!

---

### Post by florenceit on 2010-10-13
thank you so much etec, this works like a charm on Linux Mint!

---

### Post by dforthman on 2010-11-03
I haven't been able to get this to work on Ubuntu 10.10. 
10.04, all I had to do was use ndiswrapper and it worked.

---

### Post by abooks on 2010-11-28
I'm having a problem: I'm not sure if rtl8192sfw.bin is really in the directory. when I type in "ls" it shows rtl8192sfw.bin in green letters. when I type in "ls l" it says "total 72" then -rwxr-xr-x 1 root root 68368" then the date and time and rtl8192sfw.bin in green again. Bottom line is it still doesn't work. Since I can't get online with my Ubuntu 10.4 machine, I downloaded the file from debian and transferred it to the Home Folder. Are there other alternatives?

---

### Post by Gawler on 2011-01-07
I've not been able to get the Belkin F7D2101 to work with Ubuntu 10.10  No signs of life from the indicator light during powerup or thereafter.  Has anyone had success with this adaptor since moving to 10.10?

---

### Post by monkkeydragon on 2011-02-22
Thanks eteq!!! This guide worked great!!!

-Running on Ubuntu 10.04 LTS

:KS:KS:KS:KS:KS

---

### Post by david_a_moore on 2011-02-25
.

---

### Post by Shallator on 2011-03-18
tried this,on lucid32, but when i plugged in the device it recognized it as a wireless device, but said "device not ready"

---

### Post by Malibyte on 2011-04-06
Just installed on Lucid 32-bit, works great!  Thanks very much for posting this solution.

---

### Post by eeaggie on 2011-04-07
I was able to get this working on my desktop running Ubuntu 10.10 but I haven't been able to get it running on a beagle board running Ubuntu 10.10 for omap. Can anyone help me with this?

---

### Post by Embegrant on 2011-04-08
Thanks for the tip. I got this to work on an HP Pavilion dv6000 laptop with Ubuntu 10.10. Worked the first time.

---

### Post by calande on 2011-05-26
It worked, thanks! I hope Ubuntu makes it work by default!

---

### Post by calande on 2011-05-27
However...When I start my computer, I have tu unplug and plug back in my dongle several times until it shows up in the network applet icon. Do you also have the recognition problem? This looks strange to me.
Thanks,

---

### Post by calande on 2011-05-28
Does anyone have the same problem?

---

### Post by calande on 2011-05-31
From my first tests, it looks like it's due to overheating :(

---

### Post by bindaaz on 2011-06-21
For those who have connect/disconnect problem, see my last 2 posts in the thread - [http://ubuntuforums.org/showthread.php?p=10964226#post10964226](http://ubuntuforums.org/showthread.php?p=10964226#post10964226)

---

### Post by neutrinod on 2011-10-20
Hi,
I tried all the things mentioned above. I had tried to install some of the drivers using ndiswrapper. However didnt work.
The usb was recognised but i couldn't connect, however after trying out a few things, i dnt get a green light when i plug in the device. Also lsusb doesn't give the device id just says 'Belkin component'.
Is the problem because of some of the old files still remaining? 
I am running 11.04. updating to 11.10 to see if the problem persists. 

Any ideas people ?

---

