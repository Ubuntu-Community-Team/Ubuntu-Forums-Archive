---
title: "wireless network driving me mad"
date: 2009-01-18
forum: Networking &amp; Wireless
---

### Post by dezy on 2009-01-18
I moved over to ubuntu recently after mandrivas new release ( I didn't like it)

Very impressed , setup my mobile as a modem no problem , love the look and feel of ubuntu.  How ever I had trouble with conecting to the wireless with my atheros AR2425 wifi (built in to samsung nc10)

I then follow these instuctions to the letter ..

> 
    sudo su
    echo “blacklist ath_pci” >> /etc/modprobe.d/blacklist
    echo “blacklist ath_hal” >> /etc/modprobe.d/blacklist
    exit

Now for both Fedora and Ubuntu, download the latest development driver here (tested on compat-wireless-2009-01-06.tar.bz2).
Now run:

    tar -jxf compat-wireless*.bz2
    cd compat-wireless*
    sudo make install
    sudo make unload
    sudo make load
[quote]

wo hoo i have wireless .. yay ! ... set up email etc and go to bed happy :)  
Start up in the morning .. nothing but it can detaect my network but won't log in.

so I redo the last comands , sudo make unload , sudo make load
takes a while to conect but it does connect.  happy again 

restart and get nothing !

Google gets more abuse , and i find theses instructions ..[https://help.ubuntu.com/community/NC10](https://help.ubuntu.com/community/NC10) 
I follow them to the letter and still nothing 


dmesg =

[quote]
dmesg

[   36.097838] sky2 eth0: enabling interface
[   36.467759] ath5k phy0: gain calibration timeout (2412MHz)
[   36.467785] ath5k phy0: can't reset hardware (-11)
[   36.829468] ath5k phy0: gain calibration timeout (2412MHz)
[   36.829487] ath5k phy0: can't reset hardware (-11)
[   36.830275] [drm] Initialized drm 1.1.0 20060810
[   36.844842] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low IRQ 16
[   36.844868] pci 0000:00:02.0: setting latency timer to 64
[   36.845271] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   37.097988] NET: Registered protocol family 17

iwconfig wlan0
> 
dezy@Netbook:~$ iwconfig wlan0
wlan0     IEEE 802.11bg  ESSID:"" 
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated  
          Tx-Power=0 dBm  
          Retry min limit:7   RTS thr ff   Fragment thr=2352 B  
          Power Management ff
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

dezy@Netbook:~$



Any help gratefully recieved

---

