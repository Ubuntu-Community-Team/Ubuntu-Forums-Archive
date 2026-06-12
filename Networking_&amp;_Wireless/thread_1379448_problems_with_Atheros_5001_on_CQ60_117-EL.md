---
title: "problems with Atheros 5001 on CQ60 117-EL"
date: 2010-01-12
forum: Networking &amp; Wireless
---

### Post by giovanni420 on 2010-01-12
Hello everybody, I have a problem with my Compaq CQ60 117EL. I can not connect with the wifi, I tried in different ways and have not had results. Using Kubuntu 9.10 and the wifi card is an Atheros AR5001.
sorry for my bad English.:(

---

### Post by Crafty Kisses on 2010-01-12
First I need to know which ways have you tried getting the card to work? Have you tried using ndiswrapper? If you haven't you first need to get the .inf for your card. Now if I recall the 5001 uses the net5211.inf, so you can get that at the following link:

**[http://www.netgate.com/support/Drivers/](http://www.netgate.com/support/Drivers/)**

Get your .inf, then you need to install the .inf via ndiswrapper, and remember if you don't have ndiswrapper installed you can run the following:
```
sudo apt-get install ndiswrapper-common
```
Then that should install what you need to use ndiswrapper, but once you have the .inf and ndiswrapper installed, you now need to install the .inf, so you need to run the following:
```
ndiswrapper -i net5211
ndiswrapper -m
```
Then once you have done that, make sure ndiswrapper has installed the driver properly. You can do that by running:
```
ndiswrapper -l
```
If all is well, it should give you results similar to this:
```
Installed ndis drivers
driver present, hardware present
```
So now if you didn't have any problems installing ndiswrapper and installing the .inf file you now need to load the ndiswrapper module so run the following:
```
sudo modprobe ndiswrapper
```
Then you can run the following to bring your wireless up:
```
ifconfig wlan0 up
```
If that doesn't work, you might need to reboot so run the following:
```
sudo shutdown -r now
```

---

### Post by giovanni420 on 2010-01-12
I followed all the steps well, but the result is this:

giovanni@Compaq:~$ sudo ndiswrapper -i net5211
install argument must be .inf file

giovanni@Compaq:~$ sudo ndiswrapper -m
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper ...

giovanni@Compaq:~$ sudo ndiswrapper -l
giovanni@Compaq:~$

not been installed correctly? no notification is not written like the one you said!

thanks for the help!!

---

### Post by Crafty Kisses on 2010-01-13
Try running these commands:
```
cat /etc/modprobe.d/ndiswrapper >> /etc/modprobe.d/ndiswrapper.conf && rm /etc/modprobe.d/ndiswrapper
cat /etc/modprobe.d/blacklist >> /etc/modprobe.d/blacklist.conf && rm /etc/modprobe.d/blacklist
```
Then try the above steps again.

---

### Post by giovanni420 on 2010-01-13
> **Crafty Kisses said:**
> Try running these commands:
```
cat /etc/modprobe.d/ndiswrapper >> /etc/modprobe.d/ndiswrapper.conf && rm /etc/modprobe.d/ndiswrapper
cat /etc/modprobe.d/blacklist >> /etc/modprobe.d/blacklist.conf && rm /etc/modprobe.d/blacklist
```Then try the above steps again.

[IMG]http://www.google.it/images/cleardot.gif[/IMG]
it did not help, because I tried to continue with the procedure you suggested and restart the wifi was turned on and connected automatically!
now I have another problem with the Nvidia drivers, I will open a tread in the right section.
Thanks very much I just hope that does not stop working suddenly as the last time. But I never tried it with ndiswrapper. Hello, thanks again!

---

### Post by giovanni420 on 2010-01-23
> **Crafty Kisses said:**
> Try running these commands:
```
cat /etc/modprobe.d/ndiswrapper >> /etc/modprobe.d/ndiswrapper.conf && rm /etc/modprobe.d/ndiswrapper
cat /etc/modprobe.d/blacklist >> /etc/modprobe.d/blacklist.conf && rm /etc/modprobe.d/blacklist
```
Then try the above steps again.

hello, I take this tread because I had to format the pc because of problems with the video card.And now I can not install the drivers with the procedure that I have recommended.What should I do?I miss some package to install with sipnaptic?
This is the result of the proceedings:

giovanni@kubuntu:~$ sudo ndiswrapper -m
[sudo] password for giovanni:
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
module configuration already contains alias directive

giovanni@kubuntu:~$ sudo ndiswrapper -l
net5211 : invalid driver!
giovanni@kubuntu:~$

---

### Post by giovanni420 on 2010-01-25
no one can explain to me why this error? if I try to delete the file. inf tells me that it is impossible to eliminate / etc/ndiswrapper/net5211.inf: No such file or directory.:(

---

