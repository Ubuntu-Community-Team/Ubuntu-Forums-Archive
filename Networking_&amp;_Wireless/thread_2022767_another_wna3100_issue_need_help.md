---
title: "another wna3100 issue need help"
date: 2012-07-11
forum: Networking &amp; Wireless
---

### Post by garver21 on 2012-07-11
ok i have been working on trying to get my internet to work.. it is a custom computer .. i have been reading an searching for a weeks now i have gotten to were it shows up in networks an i can connect to internet but says sites cant be reached.. i have temp internet through a wired connection but cant use it as a permante soultion... an help will be apprecited. 

p.s. sry for bad grammer

---

### Post by garver21 on 2012-07-11
[FONT=monospace]i get the following
[/FONT]sudo modprobe ndiswrapper

returns nothing
[FONT=monospace]
[/FONT]ndiswrapper -l
bcmn43xx64 : driver installed 
        device (0846:9020) present

dmesg | grep ndis
[15.127623] ndiswrapper version 1.57 loaded (smp=yes, preempt=no)
[15.800471] ndiswrapper: driver bcmn43 (,08/26/2009, 5.10.79.30)loaded
[16.315654] usbcore: registered new interface driver ndiswrapper

---

### Post by garver21 on 2012-07-11
iwconfig returns

 iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"belkin.462"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 08:86:3B:AE:04:62   
          Bit Rate=104 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management-ff
          Link Quality:100/100  Signal level:-18 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:8  Invalid misc:126   Missed beacon:0

eth0      no wireless extensions.

---

### Post by garver21 on 2012-07-12
Anybody

---

### Post by madvinegar on 2012-07-12
What version of ubuntu are you using?
Try this:

1) First go to ubuntu software center and download ndiswrapper.

2) Install "wine" from software center.
 
2) Then go here: [http://sourceforge.net/projects/ndiswrapper/files/stable/](http://sourceforge.net/projects/ndiswrapper/files/stable/)    and download the latest stable version (i.e. ndiswrapper-1.57.tar.gz)

Go to your Downloads folder, find the ndiswrapper-1.57.tar.gz file, right-click it and select "extract here".

Then open terminal and navigate to the extracted folder and install ndiswrapper as follows:

```
cd /Downloads/ndiswrapper-1.57
sudo make
sudo make install
```

3) Insert your wna3100 cd with the win drivers and install the win driver/program with wine.

4) Navigate to /home/yourusername/.wine/drive_c/windows/inf/wna3100
(.wine will be hidden so press ctrl+H to reveal it)
Inside this file you will hopefully find a file called something like wna3000.inf (it must be a .inf file).

5) Open ndiswrapper, choose to add driver, navigate to /home/yourusername/.wine/drive_c/windows/inf/wna3100 and select the wna3000.inf file. Install it and hopefully your wireless will get working.

PS.Don't ask why you should install ndiswrapper twice. This is the only way I managed to get a netgear adapter working... :)

---

### Post by garver21 on 2012-07-12
im using 12.04 thinkin about going back to a older version or back to windows

---

### Post by garver21 on 2012-07-12
tired an i get bash "command" no such file or directory

---

