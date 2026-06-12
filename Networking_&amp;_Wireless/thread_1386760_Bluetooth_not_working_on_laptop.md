---
title: "Bluetooth not working on laptop"
date: 2010-01-21
forum: Networking &amp; Wireless
---

### Post by timb_nz on 2010-01-21
Hi,

I have a problem very similar to the one described in this thread:
[http://ubuntuforums.org/showthread.php?t=671552](http://ubuntuforums.org/showthread.php?t=671552)

I have a Toshiba Satellite L500, and I am running Ubuntu 9.10 64 bit.
When I try to open the Bluetooth Preferences it says "Your computer does not appear to have any Bluetooth adapters plugged in"

My laptop says it has a BTU1030 Bluetooth module in it.

I do not have Windows on this laptop (anymore), so I cannot use it to switch the Bluetooth module on.

Does anyone have any suggestions for how to activate Bluetooth on my laptop?
I have tried looking in the BIOS, but I didn't see anything that looked like it controlled the Bluetooth module.

Thanks,
Tim

---

### Post by timb_nz on 2010-01-22
Is there a way to easily switch on/off Bluetooth and Wifi when you're running Ubuntu?

---

### Post by al.zatv on 2010-07-11
here (but in Russian)
[http://al-zatv.livejournal.com/166582.html](http://al-zatv.livejournal.com/166582.html)

In short, for ubuntu 10.04 open the Terminal and try commands:

sudo sh
modprobe omnibook ectype=14
echo 1 > /proc/omnibook/bluetooth
###

to turn it on, and after that
sudo sh
echo 0 > /proc/omnibook/bluetooth
###

to turn it off.

---

### Post by dkstoney on 2010-08-04
You forgot to tell him to install omnibook first. Here's a tutorial:[http://ubuntuforums.org/showthread.php?t=316358&highlight=omnibookIf](http://ubuntuforums.org/showthread.php?t=316358&highlight=omnibookIf) your BIOS is Toshiba or Phoenix you'll have no problems. If, however, you have a UEFI BIOS such as Insyde H20, like me, well then I'm sure we'll be seeing more of each other.Did you ever get your bluetooth working?

---

### Post by Kixtosh on 2010-08-31
Allright, dagnabbit! Maybe I can be of some help here!

I've been trying out the Live CD for Xubuntu, and with a search came across this thread. It worked to get my bluetooth working on a Toshiba Portégé R205, so here's how I did it:

I opened a terminal, then:```
sudo apt-get install bluez && sudo apt-get install bluez-utils
```Then:```
sudo /etc/init.d/bluetooth restart
```Then:```
sudo hciconfig hci0 reset
```Then: ```
sudo hciconfig hci0 inqmode 0
```Then: ```
sudo hcitool scan
```At this stage, if you get a bluetooth mouse MAC address, you are almost there. 

I then tried: ```
sudo hidd --connect 00:11:22:3a:44:5b
```But got a message "hidd: command not found". So I then entered: ```
sudo root@ubuntu:/home/ubuntu# # echo 1 > bluetooth
```Followed by: ```
sudo apt-get install bluez-compat
```And finally, at long last: ```
sudo hidd --connect 00:11:22:3a:44:5b
```That did it (with a fake MAC address in this post): bluetooth mouse workiing in Live CD mode!

I'm not exactly sure what I did, or exactly why, since I was using suggestions from different sources (here in the Ubuntu forums and documentation area), but it did work perfectly!

I hope this might help another Toshiba user. If anyone has any questions, I could try to replicate this procedure better from another Live CD session.

---

### Post by kriebel on 2010-09-16
Had the same problem on a toshiba A200 after an update on 9.10 (to kernel 2.6.31.22). What worked for me was booting the old kernel (2.6.31.21), use the bluetooth device and boot again to the new kernel. Everything was back to normal. ](*,) Hope this helps for someone.

---

### Post by Kixtosh on 2010-09-16
Following my post above, I ended up installing Ubuntu 10.04 (not Xubuntu), and I don't think I had to do anything to get bluetooth working with my Toshiba Portégé R205, other than pair the device (System Menu, then Preferences, then choose Bluetooth).

It's working great. There are several distros that have Bluetooth included and working for this laptop (Peppermint, Lubuntu ...).

---

