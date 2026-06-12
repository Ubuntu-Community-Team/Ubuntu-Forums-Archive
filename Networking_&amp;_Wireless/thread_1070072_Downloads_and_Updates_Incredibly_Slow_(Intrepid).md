---
title: "Downloads and Updates Incredibly Slow (Intrepid)"
date: 2009-02-14
forum: Networking &amp; Wireless
---

### Post by millerwiller on 2009-02-14
Sorry to add to the already copious amounts of "help my downloads are slow!" threads, but I just can not seem to figure this out. 

I am running Intrepid Ibex 8.10 on a Toshiba A205-S477 with an Intel PRO/Wireless 4965 AG Wireless card.

If there is any extra information you need to know please tell me. I am not sure what would be helpful.

I have already disabled IPv6 and have attempted to install the Realtek 8187b Wireless Lan Driver via Ndiswrapper which I think was successful, but of little help. 

Regular downloads from Mozilla as well as while running synaptic are usually under 1kb/s. However, when I use a wired connection I achieve normal download speed. Internet Browsing speed is normal.

---

### Post by darco on 2009-02-14
run this in a terminal:

```
iwconfig
```

and give us the output

darco

---

### Post by millerwiller on 2009-02-14
wil@wil-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"room901"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:30:BD:C7:24:36   
          Bit Rate=11 Mb/s   Tx-Power=14 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=100/100  Signal level:-36 dBm  Noise level=-88 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.

---

### Post by darco on 2009-02-14
Your wl card is running at 11mbt (Bit Rate=11 Mb). If its capable of running at 54mb,try:

```
sudo /etc/init.d/networking restart
sudo iwconfig wlan0 rate 54M
```

darco

---

### Post by millerwiller on 2009-02-14
Thanks for your help!

I did as you requested, and when I attempted a download and a synaptic install the results were mostly the same. For the synaptic I was pleased that it at least showed a download rate of 32 kb/s at times at least, but dropped down below 1kb/s again. The download was reported to take 8 hours for just a 500 MB file...

Anything else you can do for me is appreciated!!!

---

### Post by darco on 2009-02-15
Check out this link....

[http://ubuntuforums.org/showthread.php?t=251509](http://ubuntuforums.org/showthread.php?t=251509)

Also run this command to see if you have ipv6 disabled: ip a | grep inet6
If disabled, you wont see a response in the terminal.

darco

---

### Post by Dr.Suave on 2009-02-16
Hi - I'm having a slow internet problem as well. I've fiddled with MTU to no avail and disabled ipv6. When I do your command I get this:

```
wlan0     IEEE 802.11bg  ESSID:"LindaHome"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:09:5B:6D:52:F6   
          Bit Rate=1 Mb/s   Tx-Power=26 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=72/100  Signal level:-45 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

harry@WAZ5000:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Ignoring unknown interface wlan0=wlan0.
                                                                         [ OK ]
harry@WAZ5000:~$ sudo iwconfig wlan0 rate 32m
Error for wireless request "Set Bit Rate" (8B20) :
    SET failed on device wlan0 ; Invalid argument.
harry@WAZ5000:~$ 
```

I would guess the fact that my bit rate is set at 1mb is the cause of my troubles, but something goes wrong when I try to change it. Can anyone set me straight?

Thanks a lot
Wilf

---

### Post by Dr.Suave on 2009-02-16
sorry, spotted my mistake - very tired right now, keep typong things wrong :)

---

### Post by Dr.Suave on 2009-02-16
Oh lordy - just set it to 54M, this fast internet business is wonderful, thanks so much for the post.

---

### Post by millerwiller on 2009-02-16
Thanks for all your help!

Turns out Ndiswrapper wasn't installed properly after all.

I found the correct driver and then reinstalled and now all is well. 


Thanks!

---

