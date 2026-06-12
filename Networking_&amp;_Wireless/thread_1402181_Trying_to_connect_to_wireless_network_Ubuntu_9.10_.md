---
title: "Trying to connect to wireless network Ubuntu 9.10 ERROR"
date: 2010-02-08
forum: Networking &amp; Wireless
---

### Post by EzzyTech on 2010-02-08
Hello,
I have just installed Ubuntu and am absolutely new to it.
As expected, I would like to connect to the internet.
I have done some research and came across these instructions for the command line:
> WEP Connection

You must have either your 64bit or 128 bit HEX Key or the ASCII Equivalent of your HEX Key.

sudo ifconfig [interface] down
sudo dhclient -r [interface]
sudo ifconfig [interface] up
sudo iwconfig [interface] essid “ESSID_IN_QUOTES”
sudo iwconfig [interface] key HEX_KEY <<<-------- If using ASCII Equivalent, this is s:ASCII_KEY (please make note of the prefix s:)
****Additional Comand that may be needed -- sudo iwconfig [interface] key open <<<----See note below
sudo iwconfig [interface] mode Managed
sudo dhclient [interface]

***The security mode may be open or restricted, and its meaning depends on the card used. With most cards, in open mode no authentication is used and the card may also accept non-encrypted sessions, whereas in restricted mode only encrypted sessions are accepted and the card will use authentication if available.

But when I get to "sudo iwconfig [interface] essid “ESSID_IN_QUOTES”"
Which in my case is "sudo iwconfig eth0 essid "5BG03"...
I get the following error:
Error for wireless request "Set ESSID: (8BlA) :
SET failed on device eth0 ; Operation not supported.

Please guide me toward a solution or even propose a whole new process cause as I said I'm clueless with Ubuntu.
Thanks for your time,
- Ezzy

---

### Post by chili555 on 2010-02-09
> sudo iwconfig eth0 essid "5BG03"Typically, eth0 is a wired, ethernet interface, not wireless. It requires no ESSID.

In a system with Network Manager running, manual configuration almost never works. The system wants just one pair of hands on the steering wheel: NM!

Please look for the Network Manager icon at the top right of your desktop, click it, look for networks and click yours. Supply any WEP or WPA details and connect.

Please see attached. (I have relocated the system tray to the bottom because it suits my old eyes better.)

---

### Post by EzzyTech on 2010-02-09
Hey thanks for replying.
The problem is.. The Network Manager isn't showing any wireless network. I have tried going under the Wireless Tab and clicking "Add", but I haven't successfully connected to my network.
And I have the Dell Wireless 1395 WLAN Mini-Card

Any propositions to what I might be able to do?
Thanks

---

### Post by chili555 on 2010-02-09
> Any propositions to what I might be able to do?Sure. Verify that you have a working wireless interface. Open a terminal and do:```
iwconfig
```Do you see an interface with things like this?> IEEE 802.11abg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point:    
          Bit Rate=54 Mb/s   Tx-Power=15 dBm Or, do all the interfaces say, 'no wireless extensions'?

If the latter (we suspect), please post:```
lspci -nn | grep Network
```If you have a USB wirless device, instead, post:```
lsusb
```Thanks.

---

### Post by EzzyTech on 2010-02-09
Hey these were the outputs:
```
ezzy@ezzy-laptop:~$ iwconfig 
lo        no wireless extensions. 
 
eth0      no wireless extensions. 
 
pan0      no wireless extensions. 
```

```
ezzy@ezzy-laptop:~$ lspci -nn | grep Network 
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01) 

```

---

### Post by chili555 on 2010-02-09
Please see: [http://ubuntuforums.org/showthread.php?t=1288865](http://ubuntuforums.org/showthread.php?t=1288865)

---

### Post by EzzyTech on 2010-02-09
Hey,
I did what it told me to.
And now I have an "Enable Wireless" Checkbox/Option under my Networking Icon.
Now what?

---

### Post by chili555 on 2010-02-09
Enable it! Then left-click the icon and see if you see your network, like the attachment I posted above. Click it and, hopefully, connect.

---

### Post by EzzyTech on 2010-02-09
Wow! Yes it work!
Thank you very much!
We need more people like you in this world =)

---

### Post by Jefferythewind on 2010-02-09
Chili555, great advice on the lspci, i hope that fixes it.

---

### Post by chili555 on 2010-02-09
Thank you for your kind comments. You, too, can be people like me. Learn a little bit about Ubuntu, Broadcom wireless, for example, and drop by the forum once in a while and help the nest new Ubuntian get it going. We'll appreciate your help.

Now, if you *really* want to be people like me, grow old, don't shave, watch CNBC and sip brandy laced coffee at mid-morning!

---

