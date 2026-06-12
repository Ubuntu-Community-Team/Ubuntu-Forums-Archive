---
title: "WNA1000M not working"
date: 2013-07-05
forum: Networking &amp; Wireless
---

### Post by pimms on 2013-07-05
Hello, 

I'am trying to install internet on my computer with the netgear's key WNA1000M but I don't manage :(
I found a topic with the same problem but it doesn't help me : [http://ubuntuforums.org/showthread.php?t=1806839&highlight=WNA1000M](http://ubuntuforums.org/showthread.php?t=1806839&highlight=WNA1000M)

It doesn't work when I tried to launch the command : sudo apt-get install linux-headers-generic build-essential 
So I have downloaded RTL8192cu here : [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=48&Level=5&Conn=4&ProdID=277&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=48&Level=5&Conn=4&ProdID=277&DownTypeID=3&GetDown=false&Downloads=true)
Then I executed the file install.sh, but without success, I don't know how I can do.


Thanks a lot for your help :)

---

### Post by chili555 on 2013-07-05
Do you have the same device? Please insert the device and run and post:```
lsusb
```The module rtl8192cu is included in later versions of Ubuntu, certainly 12.10 and newer. What version do you have?```
lsb_release -d
```Did you try to simply load the driver and see what happens?```
sudo modprobe rtl8192cu
```If the driver doesn't exist in your earlier Ubuntu version, is there any reason you can't simply download and install 13.04?> It doesn't work
....
without success
....
it doesn't help meIt will be very helpful, as we proceed, to know the details of any error, not just that it didn't work, since the exact error will help us find the solution.

---

### Post by pimms on 2013-07-05
Thank you for your answer.
The result of lsusb :


```
Bus 001 Device 003: ID 0846:9041 NetGear, Inc. WNA1000M 802.11bgn [Realtek RTL8188CUS]
```

The result of lsb_release -d :

```
Debian GNU/Linux 7.1 (wheezy)
```


sudo modprobe rtl8192cu :

```
FATAL : Module rtle8192cu not found.
```

Sorry for my english, I'm french and it's difficult to write for me ^^

---

### Post by chili555 on 2013-07-05
I'm very sorry. I know nearly nothing about wheezy. Aren't you able to get any help on Debian's forums?

---

### Post by pimms on 2013-07-05
I will see on Debian's forums, maybe they could help me.
In any case, now I have a list of the connexions available on my computer, I select my SSID and enter the key but the connection is not possible, maybe there is a conflict between drivers ?

I'am learning this topic : [http://forums.debian.net/viewtopic.php?f=7&t=103044](http://forums.debian.net/viewtopic.php?f=7&t=103044)

---

