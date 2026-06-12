---
title: "AdHoc woes - USB Wifi dongle"
date: 2011-06-03
forum: Networking &amp; Wireless
---

### Post by Daminator on 2011-06-03
Hello all,

I'm trying to set up AdHoc wifi from my media centre machine so that I can connect my mobile phone to the internet.

My house has several machines, but no wifi. All connected with LAN cable hubs and switches.

I bought a "LogicPro 802.11g High Speed Linux / Ubuntu Wireless Internet USB Adapter Wifi Dongle"
[http://www.amazon.co.uk/gp/product/B003YURCG8/ref=oss_product](http://www.amazon.co.uk/gp/product/B003YURCG8/ref=oss_product)

I have tried plugging it in and following AdHoc ubuntu guides online, but it's not working.

My feeling is that that whatever driver gets 'auto detected' and used can use the wifi dongle 'normally', but can not put it into AdHoc mode.

There's a file on the disk that comes with the dongle called "rtl8187B_linux_24.6.1025.tar.gz", but I have no idea what to do with that. I was thinking of trying to set it up assuming it's a Linux driver, but just read somewhere that if you try to load a driver when another driver is already in place then you can get lock up problems etc.

Can anyone help me with this? I really don't want to use a wifi router if possible. I just want to plug this thing in when I want wifi and unplug it when I don't.

Thanks
Damian

---

### Post by Daminator on 2011-06-04
A bit more information ..

I'm running the latest version of Ubuntu with all updates regularly in place. Here's the output from a few commands:

```
$ lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 05af:0408 Jing-Mold Enterprise Co., Ltd 
Bus 001 Device 003: ID 0bda:8189 Realtek Semiconductor Corp. RTL8187B Wireless 802.11g 54Mbps Network Adapter
Bus 001 Device 002: ID 0409:0058 NEC Corp. HighSpeed Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

```
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"UbuntuAdhoc"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm                                                                                        
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
vboxnet0  no wireless extensions.
```


```
$ sudo iwconfig wlan0
wlan0     IEEE 802.11bg  ESSID:"UbuntuAdhoc"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
```

```
$ sudo iwconfig wlan0 mode ad-hoc
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Operation not supported.
```

Does this help at all?

Can I get an Ad-hoc wifi network with this dongle?

Would installing the supplied "rtl8187B_linux_24.6.1025.tar.gz" driver give better results? If so, can anyone talk me though doing that? Do I need to turn off the current driver somehow first?

Thanks
Damian

---

### Post by spiky001 on 2011-06-04
Hi if you click on network manager dose it show any wireless networks?

---

### Post by chili555 on 2011-06-04
> My feeling is that that whatever driver gets 'auto detected' and used can use the wifi dongle 'normally', but can not put it into AdHoc mode.The usual driver is rtl8187. I think it's very probable that you are correct; that it doesn't do ad-hoc.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/97322](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/97322)> Would installing the supplied "rtl8187B_linux_24.6.1025.tar.gz" driver give better results?I'm not quite sure anyone on this forum knows for sure. You could sure try it and if it doesn't, it's very easy to uninstall. I wonder how old this driver is, but I might try compat-wireless first.

[http://wireless.kernel.org/en/users/Download](http://wireless.kernel.org/en/users/Download)

Neither task is very hard if you go slowly and follow directions carefully.

Which do you prefer?

---

### Post by dragonclan1tnt on 2011-07-11
try disabling the linux driver, by blacklisting it and using ndiswrapper to install the windows driver for the card


well that work for me any way:)



for the the past week or so i was trying to get Ad-hoc mode on my Advantek USB WiFi dongle (AWN-USB-54R) so i can do some testing and expanding of my mesh network

and i finally came across the answer

i disable the linux drivers by add it to the blacklist and install ndiswrapper, use the windows drivers and i got Ad-hoc working 

sudo rmmod rtl8187

sudo gedit /etc/modprobe.d/blacklist
add "blacklist rtl8187"

after that, download and install the window driver via ndisgtk:grin:

---

### Post by gingertom5005 on 2011-09-03
LogicPro 802.11g High Speed Linux / Ubuntu Wireless Internet USB Adapter Wifi Dongle

I bought one of these from Amazon for £9.99 and it works fine with Ubuntu (and Windows) and does everything the reviews say.

Amazon are now advertising it at £99.00.

I'm waiting to hear back from the seller.

---

