---
title: "can find SSID, but cant access it"
date: 2009-06-16
forum: Networking &amp; Wireless
---

### Post by Mark Straatman on 2009-06-16
Hi,

I´ve got a wireless network at home which I want to connect to. the only problem is that I can recive it, but it wont connect to it.

I´ve tried to connect through a cable but it gave me the same problem.
i´ve tried to install samba, but neither did that work cuz of the internet connection.
tried to figure out if samba was already installed, but if I run 
```
sudo nano/etc/samba/smb.conf
```it says command not found
any help is apreciated ;)
thanks

by the way, the network isnt protected. I tried to do so by putting a WPA PSK on it, but that didnt work.

---

### Post by puppywhacker on 2009-06-16
you need to put a space after the command "nano" and the file that you want to edit.
```
sudo nano /etc/samba/smb.conf
```

but that is not the answer to your problems.

post the output of iwconfig and ifconfig. (you can put XXX in the place of the ip-address)

I'm guessing here that the SSID will be filled in properly for the wireless interface (wlan0) but that the AP says not-associated. In that case you can connect to the access point with

```
sudo iwconfig wlan0 ap 00:11:22:33:44:55
```

---

### Post by Mark Straatman on 2009-06-16
iwconfig wlan0:
```
IEEE 802.11abg ESSID:"Straatman"
Mode:Managed Frequency:2.462 GHz Access Point: Not-Associated
Tx-Power=15 dBm
Retry min limit:7 RTS thr:off Fragment thr=2352 B
Power Management:off
Link Quality:0 Signal level:0 Noise Level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

```

ifconfig
```
Link encap:Ethernet  HWaddr 00:19:d2:cf:cd:68
inet6 addr: fe80::219:d2ff:fecf:cd68/64 Scope:link
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:22 errors:0 dropped:0 overruns:0 frame:0
TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:1320 (1.3 KB) TX bytes:1908 (1.9 KB)

```

---

### Post by superprash2003 on 2009-06-16
post output of **sudo iwlist scanning**

---

### Post by Mark Straatman on 2009-06-16
```
    mark@mark-laptop:~$ sudo iwlist scanning
  
  [sudo] password for mark: 
  
  lo        Interface doesn't support scanning.
  
      eth0      Interface doesn't support scanning.
  
      wmaster0  Interface doesn't support scanning.
  
      wlan0     Scan completed :
  
            Cell 01 - Address: 00:18:4D:D5:1C:D9
  
                      ESSID:"Straatman"
  
                      Mode:Master
  
                      Channel:11
  
                      Frequency:2.462 GHz (Channel 11)
  
                      Quality=90/100  Signal level:-41 dBm  Noise level=-127 dBm
  
                      Encryption key:off
  
                      IE: Unknown: 00095374726161746D616E
  
                      IE: Unknown: 010882848B962430486C
  
                      IE: Unknown: 03010B
  
                      IE: Unknown: 2A0104
  
                      IE: Unknown: 2F0104
  
                      IE: Unknown: 32040C121860
  
                      IE: Unknown: DD060010180200F0
  
                      Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
  
                                24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
  
                                12 Mb/s; 48 Mb/s
  
                      Extra:tsf=000000544f89f186
  
                      Extra: Last beacon: 68ms ago
  
            Cell 02 - Address: 00:80:48:41:50:7A
  
                      ESSID:""
  
                      Mode:Master
  
                      Channel:9
  
                      Frequency:2.452 GHz (Channel 9)
  
                      Quality=30/100  Signal level:-91 dBm  Noise level=-127 dBm
  
                      Encryption key:on
  
                      IE: Unknown: 0000
  
                      IE: Unknown: 010482040B16
  
                      IE: Unknown: 030109
  
                      IE: Unknown: 050400010000
  
                      IE: Unknown: DF20011E0000000005660902FF0F3030383034383431353037410000000000000000
  
                      Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
  
                      Extra:tsf=000001c31a611184
  
                      Extra: Last beacon: 2104ms ago
  
      pan0      Interface doesn't support scanning.
```

could it be possible that my intel PRO/wireless driver isnt installed?
Ive downloaded a .tgz file, but I´m not really familliar with installations in linux...

---

### Post by puppywhacker on 2009-06-16
your interface found the essid, it didn't associate it for some reason, so the driver (or better module) is loaded and the radio part seems to be working, it just didn't associate. you can force it by 

```
sudo iwconfig wlan0 ap 00:18:4D:D5:1C:D9

```

once the wireless link is established you can restart the network, that should trigger DHCP to receive an ip address from your accesspoint or your internet provider.

```
sudo /etc/init.d/network restart
```

If you have connected once using these commands, chances are it will work without messing around in the future since previous connections are remembered.

---

### Post by Mark Straatman on 2009-06-17
the first command worked, but I couldnt restart the /ect/init.d/network. it says that the file or directory couldnt be found.
I tried to log in as root (sudo su) and navigating to the first directory (dont know the exact work, but the highest map) and tried it than. that didnt work either...

tricky case isnt it? :P

---

### Post by puppywhacker on 2009-06-17
my bad, should be networking.

```
sudo /etc/init.d/networking restart
```

you can hit [tab] while you are typing, so you don't have to finish the whole commands, so when you type sud[tab] it will finish it to sudo, the same goes for the network script. type /et[tab]ini[tab]netw[tab] and the  it will find the complete path for you. tab completion is my frend =)

also execute the commands again
```
sudo iwconfig wlan0
sudo ifconfig wlan0
```
you should see an AP associated for iwconfig and an ip-address at ifconfig.

---

### Post by Mark Straatman on 2009-06-17
I'm sorry to dissappoint, but it didnt work (the command did work, but no connection)

I ran the three commands, and on the last two the AP was still not-associated and there was no IP in the ifconfig section.

I dont know why, in linux 7 and 8 I never had problems with it :S

---

### Post by Mark Straatman on 2009-06-19
Guy's, never mind. I dont know how, but I do know where the problem was, and it was my AP. not that there was something wrong with it, I just think that ubuntu didnt connect to it right.

I had a wireless router at home, one that I used before, but not anymore. I connected the WR, and with another cable I connected the AP. after that I could connect sucessfully with the AP and with the WR.

Dont know how, but the problem is solved ;)

thanks everybody who replied ;)

---

