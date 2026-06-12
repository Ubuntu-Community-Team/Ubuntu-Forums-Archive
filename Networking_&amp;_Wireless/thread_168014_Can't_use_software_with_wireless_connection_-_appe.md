---
title: "Can't use software with wireless connection - appears to be connected. PLEASE HELP!"
date: 2006-04-29
forum: Networking &amp; Wireless
---

### Post by brickhead20 on 2006-04-29
I am using a Safecom SWMULZ-5400 USB Wireless adapter that uses a Zydas ZD1211b chipset. I have installed the latest driver (lsmod shows a zd1211b module running and it is recognized in the device manager), and have managed to get to a point where it appears to be connected to my router when i type "sudo iwconfig wlan0" into the terminal. In fact it returns this:

wlan0     802.11b/g NIC  ESSID: "SWAMRU-54108"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:50:18:47:BD:CC
          Bit Rate: 54 Mb/s
          Retry: off   RTS thr=2432 B   Fragment thr: off
          Encryption key:****-****-****-****-****-****-**   Security mode: open
          Power Management: off
          Link Quality=96/100  Signal level=-155 dBm  Noise level=-256 dBm
          Rx invalid nwid: 0  Rx invalid crypt: 0  Rx invalid frag: 0
          Tx excessive retries: 105  Invalid misc: 0   Missed beacon: 0

Which is the correct network (ESSID is set to ANY, so it must have picked up the ESSID). However, when I load up firefox or a messanger program that requires an internet connection, it doesnt work. I'v been hammering at it gradually wearing down the problems for about a week now but this ones got me stumped. ](*,) Loving Ubuntu though...any help with this would be VERY much apprecitated. Notice "Tx excessive retries" is up to 105, as it fails to send packages.

The WEP is set to hexidecimal, which was the source of one of the first problems as I had it set to ASCII :rolleyes: . Also previously "iwlist wlan0 scan" wouldnt work, but that was fixed with compiling and installing a newer driver.

Any help would be very much appreciated, any more information that is required I will do my very best to get.  Thanks ;) 

Rich

---

### Post by brickhead20 on 2006-04-30
Anyone?

---

### Post by el duderino on 2006-04-30
You have tried turning off your WEP just for troubleshooting right?

---

### Post by brickhead20 on 2006-04-30
Thanks, Ok I tried that and it worked! YESSSS! I can connect to the router without encryption. Thats great and all, but if I want to enable WEP encryption how do I go about that? Any help again, would be much appreicated

EDIT: Actually I searched the forums and figured it out myself. I installed wpasupplicant and set the WEP key using the terminal, and miraculously it now works. Thanks for the help!

---

### Post by brickhead20 on 2006-05-02
However, it is still a bit unreliable in connecting to the Router. I can get it connected by bashing around in the terminal (no pun intended), but it can take a while to connect. Does anyone know any tricks to make it faster and more reliable. 

Moreover, is the new release (Dapper Drake) going to have some friggin' proper wireless support, and a network manager that works?

---

