---
title: "Install/patch Edimax EW-7138USG"
date: 2009-12-08
forum: Networking &amp; Wireless
---

### Post by KingNeil on 2009-12-08
I have Ubuntu 9.04 and the Edimax EW-7138USG. It is a USB dongle for Wifi.

I don't know what the name of the driver (?) is, whether it's ralink rt73, or rt73usb or what (I've heard two drivers were released for this very device, so I don't know if mine is the old or new). I need to know how to get this working on Ubuntu 9.04. I've read various guides, but none seem to work.

Can somebody help?

This is where I bought it: [http://www.play.com/PC/PCs/-/660/867/-/3477978/Edimax-EW-7318USG-WiFi-USB-Turbo-Wireless-Adaptor-4Dbi/Product.html?searchtype=genre](http://www.play.com/PC/PCs/-/660/867/-/3477978/Edimax-EW-7318USG-WiFi-USB-Turbo-Wireless-Adaptor-4Dbi/Product.html?searchtype=genre)

---

### Post by chili555 on 2009-12-08
Please check here: [http://ubuntuforums.org/showpost.php?p=7716964&postcount=8](http://ubuntuforums.org/showpost.php?p=7716964&postcount=8)

You might try the built-in driver. Open a terminal and do:```
sudo modprobe rt73usb
iwconfig
```Do you now have a wireless interface? Can you click the Network Manager icon and connect?

---

### Post by KingNeil on 2009-12-08
No, this is what iwconfig returns:

```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g  Mode:Managed  Frequency=2.422 GHz  
          Access Point: Not-Associated   Bit Rate:11 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```

wlan0 is my computer's regular built-in Wifi, I think.

I don't even know if rt73usb is actually the name of the driver... Can anyone confirm what the name is? This is very annoying.

---

### Post by chili555 on 2009-12-08
Plug the device in and do:```
sudo modprobe rt73usb
lsusb -v
dmesg > dmesg.txt
zip dmesg.zip dmesg.txt
```Please post the *lsusb* result and attach the dmesg.zip file that you will find in your home directory. Thanks.

---

### Post by KingNeil on 2009-12-08
Here is the ZIP file.

---

### Post by KingNeil on 2009-12-08
Any idea of what the problem is?

---

### Post by chili555 on 2009-12-08
No ideas yet. Please post:```
lsusb -v
lsmod | grep rt
```Thanks.

---

### Post by KingNeil on 2009-12-08
Do I run that with the dongle plugged in?

---

### Post by chili555 on 2009-12-08
Yes, please.

---

### Post by KingNeil on 2009-12-09
It doesn't exactly all fit in the terminal window. How do I show you the output?

EDIT: Also see the info on the next post.

---

### Post by KingNeil on 2009-12-09
By the way, I have a screenshot for you. This is my network manager, popped down from the top bar in Gnome.

As you can see, my internal Wifi pops up with a list of networks, but the USB adapter is set as "disconnected". In fact, that may be my RJ45... sigh

[[IMG]http://i.imgur.com/GIFBg.png[/IMG]]("http://i.imgur.com/GIFBg.png")

Is it possible that I have to disable the internal Wifi first, or, if not, does this screenshot help you in any way?

---

### Post by chili555 on 2009-12-09
> It doesn't exactly all fit in the terminal window. How do I show you the output?You can use the process we used for dmesg; that is, convert the terminal output to a text file and copy and paste it, or, if it's more than 10 or so lines, attach it to your reply.```
lsusb -v > lsusb.txt
lsmod | grep rt > lsmod.txt
```

---

### Post by KingNeil on 2009-12-09
OK, here we go. Attached.

---

### Post by chili555 on 2009-12-09
> Is it possible that I have to disable the internal Wifi firstIt is certainly worth a try. Can it be disabled in the BIOS? Please do so. You may also try:```
sudo ifdown wlan0
```If this is a laptop, you may also have a key combination to turn off the internal wireless.

This all begs the question: if you have a working wireless, why are we struggling with the Edimax?

---

### Post by KingNeil on 2009-12-09
It says 

```

ifdown: interface wlan0 not configured

```

The answer is because I need the Edimax to work. It has the ability to be used for packet injection, legally, of course.

But I really just need it to work..

---

### Post by KingNeil on 2009-12-09
What do you make of the output I attached? I mean, how much of an expert would you say you are in all this?

---

### Post by chili555 on 2009-12-09
> What do you make of the output I attached?I can see that rt73usb and its dependencies are not included in the loaded modules, maybe because you rebooted and did not modprobe again. That tells me the insertion of the device does not alert the system of its need for specific drivers. Sometimes, you can wake it up by modprobing the correct module; sometimes not.> I mean, how much of an expert would you say you are in all this? In terms of the Edimax and rt73usb? None at all. In terms of Linux networking generally, I started in Linux in 2001 and have been through several distributions and several network cards, wired, wireless and HomePNA, all of which, with the help of forums and Google, I could get working. I try to learn something new about networking every day. 

After all these years, if you look closely, you can see I answer the simpler posts about common devices. I have no 3G experience and I got my built-in phone-line modem working just to see if I could. I use neither. I know little about samba because Windows machines are not allowed in my house. I can file-share without it amongst Ubuntu machines. I can set up a networked printer.

End curriculum vitae.

---

### Post by chili555 on 2009-12-09
Please insert the device, and do:```
sudo modprobe rt73usb
lsmod | grep rt > lsmod.txt
sudo ifdown wlan0
iwconfig > iwconfig.txt
```Please post the text. Thanks.

---

### Post by KingNeil on 2009-12-09
This is the terminal of what I just did:

```
ubuntu@ubuntu:~$ sudo modprobe rt73usb
ubuntu@ubuntu:~$ lsmod | grep rt > lsmod.txt
ubuntu@ubuntu:~$ sudo ifdown wlan0
ifdown: interface wlan0 not configured
ubuntu@ubuntu:~$ iwconfig > iwconfig.txt
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

ubuntu@ubuntu:~$ 

```

The ZIP file with both text files is attached, too.

Two things I should add: 

(1) I'm using the Live CD. That shouldn't make a difference though, right?

(2) I've been told to download the following driver from the Edimax support, but I don't know how to install it. I've tried the readme but can't understand it. [http://www.edimax.co.uk/images/Image/Driver_Utility/Wireless/NIC/2009/2008_0506_RT73_Linux_STA_Drv1.1.0.1.tar.zip](http://www.edimax.co.uk/images/Image/Driver_Utility/Wireless/NIC/2009/2008_0506_RT73_Linux_STA_Drv1.1.0.1.tar.zip)

---

### Post by chili555 on 2009-12-09
> I'm using the Live CD. That shouldn't make a difference though, right?None, except that things you compile or add to configuration files, etc. will not persist on reboot. You can either install permanently, if and after we get this working, or keep notes so you can recreate the steps each time you boot up. Of course, you can just leave your computer running indefinitely.> I've been told to download the following driver from the Edimax support,I do know how to install it, and it fails. I suspect it is not up-to-date with respect to kernel 2.6.31-x. Maybe Edimax needs to update it. 

I think part of the problem is that you are shutting down *wlan0* and Network Manager is restarting it! Let's try:```
sudo /etc/init.d/network-manager stop
```That will probably break your network connection. Be sure the Edimax is inserted.```
sudo rmmod -f rt73usb
sudo modprobe rt73usb
iwconfig
```*Now* do you see a new wireless interface? You can get wlan0 started again by removing the Edimax and doing:```
sudo /etc/init.d/network-manager start
```

---

### Post by KingNeil on 2009-12-09
Big prob on the first instruction.

```

ubuntu@ubuntu:~$ sudo /etc/init.d/network-manager stop
sudo: /etc/init.d/network-manager: command not found

```

---

### Post by chili555 on 2009-12-09
On my computer running 9.10, and not 9.04 as you indicate, it's 'network-manager.' Please do:```
ls /etc/init.d
```See if it's 'NetworkManager' or 'networkmangler' or whatever. Then adjust the command, stop it and continue the remaining commands. Thanks!

---

### Post by KingNeil on 2009-12-09
Adjusted it. Ran it. Iwconfig gave me:

```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g  Mode:Managed  Access Point: Not-Associated   
          Bit Rate:11 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```

NetworkManager shows the same as it did before.... sigh.

---

### Post by chili555 on 2009-12-09
I am low on ideas. I will be back later.

---

