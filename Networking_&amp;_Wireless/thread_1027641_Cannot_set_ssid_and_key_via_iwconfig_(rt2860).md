---
title: "Cannot set ssid and key via iwconfig (rt2860)"
date: 2009-01-01
forum: Networking &amp; Wireless
---

### Post by pitris on 2009-01-01
Hello,
on Eee 1000H with rt2860 I'm normally using network manager and gnome nm applet to connect to wifi networks - works just fine. But now I want to set essid via iwconfig and it's silently ignored. The same with setting a key.
```

luc@fifinka:~$ sudo iwconfig ra0 
ra0       RT2860 Wireless  ESSID:""  Nickname:"RT2860STA"
          Mode:Auto  Frequency=2.432 GHz  Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

luc@fifinka:~$ sudo iwconfig ra0 essid DEZO
luc@fifinka:~$ echo $?
0
luc@fifinka:~$ sudo iwconfig ra0 
ra0       RT2860 Wireless  ESSID:""  Nickname:"RT2860STA"
          Mode:Auto  Frequency=2.432 GHz  Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

luc@fifinka:~$ 

```

What's wrong? Thanks for any suggestions.

---

### Post by oblidor on 2009-04-22
I have the same problem and same computer.

Did you find out anything since you posted the question?

---

### Post by killabytenow on 2009-05-02
I discovered that if you kill NetworkManager (/etc/init.d/NetworkManager stop), you can partially manage the asus-eee rt2860 wireless connection.

I have connected succesfully to Open Wireless network (wihout wep/wap protection). But when I try to connect to WEP AP's it does not work... Now I'm trying to configure the wireless interface via iwpriv, but I have no success :(

Somebody with the same problem? I hate Network managers, big window managers and such, so it is very important for me to configure manually everything in my Linux box.

Thanks in advance.

---

### Post by chili555 on 2009-05-02
I don't believe the ESSID and encryption key will appear until you actually associate:```
sudo iwconfig ra0 essid DEZO
sudo iwconfig ra0 key 0123456789
sudo dhclient ra0
```If you connect, then the details will appear in:```
sudo iwconfig ra0
```

---

### Post by killabytenow on 2009-05-02
I'm sorry chili555, but this hasn't work for me. I'm  using an Asus EEE 901, with Easy Peasy based in Ubuntu Intrepid, and I don't know wthat is exactly happening but it is perhaps the oddest wifi case I have seen in my life x"DDD

But I have found a solution, I copy'n'paste it here. Perhaps it could be useful for other users :D

```

# stop one of the main source of problems
sudo /etc/init.d/NetworkManager stop

# enable the wireless device
sudo ifconfig ra0 up

# configure the WEP wireless connection
sudo iwpriv set EncryptType=WEP
sudo iwpriv set Key1=CACACACACACACACAFE0CACAFE0
sudo iwpriv set DefaultKeyID=1
sudo iwpriv set SSID=*****

# catch your Ip and run
dhclient ra0

```I don't know if it is a problem of Easy Peasy or Ubuntu Intrepid :( sorry

But this works :D

---

### Post by sprince09 on 2009-05-05
I am also having this problem with an EEE 901 with Ubuntu Netbook Remix/Jaunty. Even trying to connect to an open network fails. Network manager works without any problems however.... just when I try to bring up the network manually do I have problems.

This is what I've been running (as root):

ifconfig ra0 down
dhclient -r ra0
ifconfig ra0 up

iwconfig ra0 ap xx:xx:xx:xx
dhclient ra0

This doesn't connect to the the access point given. It changes the AP listed when I run iwconfig ra0 with no parameters, but doesn't update the ESSID. Also, I noticed this output from dmesg after running ifconfig ra0 up:

--> Error 2 opening /etc/Wirelss/RT2860STA/RT2860STA.dat

This directory/file doesn't exist, and adding a blank one at that location doesn't help.

---

