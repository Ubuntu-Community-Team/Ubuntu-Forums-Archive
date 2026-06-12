---
title: "Has my wifi card been recognized?"
date: 2011-10-30
forum: Networking &amp; Wireless
---

### Post by GiH on 2011-10-30
Hi everyone!
I really need your help, I tried to RTFM a lot without finding what I need! :(
I'm using XBMC Live (installed on my hdd), based on ubuntu 10.04 (according to *lsb_release -a***). In this distribution, not every ubuntu package is available, and (especially)** the only way to modify every hardware-localized problem is the shell-way.
So here it is: I own the broadcom BCM4311 (found my wifi card model with *sudo lspci*), and I have to associate it to my AP, which uses WPA-TKIP codification. This is what I obtain with *sudo iwconfig* :
> lo      no wireless extensions
eth0    no wireless extensions
wlan0   IEEE 802.11bg ESSID: off/any
        Mode: Managed Access Point: Not-Associated Tx-Power=0 dBm
        Retry long limit:7 RTS thr: off   Fragment thr: off
        Encryption key: off
        Power management: off
I tried previosly to associate to my AP, with *sudo iwconfig wlan0 essd *, no problems, but with *sudo iwconfig wlan0 key* (or *key:s* or *key"s:"*) i obtained the *"Error for wireless request "Set Encode" (8B2A) etc etc"*.

So, has my card been recognized or I need to install a driver? what I can do now? Without GUI & especially without internet connection...if the solution is to install some packages (like ndiswrapper to install the driver) how can install them from my usb pen drive? Please be very precise with your indications..._**t**_**hank you very much for your attention and your help!!! **_**:)**_

---

### Post by wildmanne39 on 2011-10-30
Hi, welcome to the forum! you have to install driver and firmware.

This should work based on the information
you gave.
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```
after it is finished unplug your wired connection and reboot.
Thank you

---

### Post by GiH on 2011-10-30
> **wildmanne39 said:**
> Hi, welcome to the forum! you have to install driver and firmware.

This should work based on the information
you gave.
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```
after it is finished unplug your wired connection and reboot.
Thank you
Hi wildmanne, thank you very much for you reply!
Unfortunately I can't manage to make my ethernet card to work, too :( sigh... how can I install these packages without a internet connection?

---

### Post by wildmanne39 on 2011-10-30
Hi,

Download the b43 zip file to a flash drive from a computer with internet access then drag and drop the file to your ubuntu desktop. Right-click it and select Extract Here. Open a terminal and do:
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/*  /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```
one line at a time.
Thank you

---

### Post by GiH on 2011-10-30
> **wildmanne39 said:**
> Hi,

Download the b43 zip file to a flash drive from a computer with internet access then drag and drop the file to your ubuntu desktop. Right-click it and select Extract Here. Open a terminal and do:
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/*  /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```
one line at a time.
Thank you
Thank you again wild, but unfortunately I'm using a shell-only distribution so I can't just use the GUI :( how can I relevate and mount my usb pen drive from shell? Thanks!

---

### Post by wildmanne39 on 2011-10-30
Hi, this should do it.
[http://www.codeunit.co.za/2011/04/15/ubuntu-server-how-to-mount-a-usb-flashdrive-from-a-terminal/](http://www.codeunit.co.za/2011/04/15/ubuntu-server-how-to-mount-a-usb-flashdrive-from-a-terminal/)
Thank you

---

### Post by GiH on 2011-10-30
> **wildmanne39 said:**
> Hi, this should do it.
[http://www.codeunit.co.za/2011/04/15/ubuntu-server-how-to-mount-a-usb-flashdrive-from-a-terminal/](http://www.codeunit.co.za/2011/04/15/ubuntu-server-how-to-mount-a-usb-flashdrive-from-a-terminal/)
Thank you

I followed carefully your indications, unfortunately nothing changes (checked with iwconfig...)
PS: what is the command to scan wifi AP? *sudo iwconfig wlan0 scan *doesn't work..
PPS: with the command sudo rmmod b43 I obtained a "no such file or directory" error...

Thank you again!!

---

### Post by wildmanne39 on 2011-10-30
Hi, try this command first:
```
sudo ifconfig wlan0 up
```
If it does not work then
please post the results of:
```
lsmod
```
```
lspci -nnk | grep -iA2 net
```
```
iwconfig
```
```
rfkill list all
```
```
sudo iwlist scan
```
```
sudo cat /var/log/syslog | grep -e b43 -e firmware -e wl -e wlan -e etwork | tail -n45
```
by clicking on new reply and click # and paste the information between the brackets.

You can copy and paste the results to a flash drive then post them here.
Thank you

---

### Post by GiH on 2011-10-31
Oh, something happened, wild! 
the *ifconfig wlan0 up* definitely worked, now the command *sudo iwconfig* returned me 
```
 
lo no wireless extensions 
eth0 no wireless extensions 
wlan0 IEEE 802.11bg ESSID: off/any 
Mode: Managed Access Point: Not-Associated **Tx-Power=20 dBm** 
Retry long limit:7 RTS thr: off Fragment thr: off Encryption key: off 
Power management: off 
``` 
and the *sudo iwlist wlan0 s* command found my Access Point, finally! 
After that, I followed accurately  [this guide]("http://ubuntuforums.org/showthread.php?t=263136")  and, doing everything just as luca_linux said,** i finally managed to  ping my Access Point**!! 
And I can be pinged from other PCs in my network... 
...**BUT**... 
when I try to ping any other website (either ping [www.google.com](www.google.com) or  ping xxx.xxx.xxx.xxx , just to be sure it's not a DNS related problem) i  get an  
```
connect: Network is unreachable
``` 
error.....**what could the problem be?** 

Thank you again very much for your patience with me!

---

### Post by wildmanne39 on 2011-10-31
Hi, I do not know with out seeing the information that I asked you to post here.

Plus add:
```
nm-tool
```
to the other information that I need.
Thank you

---

### Post by GiH on 2011-10-31
Hi wild, here you are (i used attachments for long texts...)

_________________
```
lsmod
```**See attachment 1.zip**
_________________
```
lspci -nnk | grep -iA2 net
```**See attachment 2.zip**
_________________
```
iwconfig
```[B]```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Alice-79149188"  
          Mode:Managed  Frequency:2.432 GHz  Access Point: 00:1D:6A:AD:99:84   
          Bit Rate=5.5 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=63/70  Signal level=-47 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```[/B]
_________________
```
rfkill list all
```[B]```

0: eeepc-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```[/B]
_________________
```
sudo iwlist scan
```**See attachment 5.zip**
_________________
```
sudo cat /var/log/syslog | grep -e b43 -e firmware -e wl -e wlan -e etwork | tail -n45
```[B]
See attachment 6.zip[/B]
_________________
```
nm-tool
```[B]```

nm-tool: No such file or directory
nm-tool died with exit status 1

```
[/B]_________________

Thank you again!! Hope I did everything right :)

---

### Post by wildmanne39 on 2011-10-31
Hi please run this command again, exactly as it is posted and give the results here:
```
sudo cat /var/log/syslog | grep -e b43 -e firmware -e wl -e wlan -e etwork | tail -n45
```

Also 
```
cat /etc/network/interfaces
```

You should take the dash out of your ESSID in your router and network interfaces file.

You do not have network manager installed correct?

I have not worked with anyone that is using a shell only enviroment so this is new territory for me.

The link you used to set up your connection is old you may want to look at this one.
[http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html](http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html)
Thank you

---

### Post by GiH on 2011-10-31
Here you are, wild! Saved the outputs in attachements...hope you will find something in there! :(

Unfortunately, I can't take out the dash from my essid, the router I'm using is telecom branded and nearly anything can be modified...could this be a problem??

I'll try to follow that guide, thank you!

---

### Post by wildmanne39 on 2011-10-31
Hi, it might be, I do not know for sure, that is not a standard character for ESSID's. 

You do not have network manager installed correct?
Thank you

---

### Post by GiH on 2011-10-31
no I don't, but I'd really really like to have some GUI too!
What can I do now? :confused:

---

### Post by wildmanne39 on 2011-10-31
Hi, why did you not install GUI? it would be a lot easier.

I do not see any attachments.
Thank you

---

### Post by GiH on 2011-10-31
I always have the same problem...how can I install GUI & its dependencies without internet? It would take like forever...right? :(
PS I tried to reupload outputs.zip, you should see it down here!

---

### Post by wildmanne39 on 2011-10-31
Hi, go to somewhere with internet and read the directions on the download page of ubuntu then download ubuntu and burn the image to a cd or flash drive it is quick and simple.
[http://www.ubuntu.com/](http://www.ubuntu.com/)
Thank you

---

### Post by wildmanne39 on 2011-10-31
Hi I have been looking over your log files and doing some researching is your ip address set to an address outside of what your router assigns automatically? it needs to be.
Thank you

---

### Post by GiH on 2011-10-31
BIG NEWS! :D
I...kinda :D ...managed it all to work! :D
I just don't really know how...no really.
I just messed up with absolute rage with interfaces and wpa_supplicant.conf. 
I configured them like that:

**/etc/network/interfaces**
```

auto wlan0
iface wlan0 inet static
address 192.168.1.5 
netmask 255.255.255.0 
wireless-essid *my_essid *
gateway 192.168.1.1 
pre-up wpa_supplicant -B -Dwext -iwlan0 -c/etc/wpa_supplicant.conf 
post-down killall -q wpa_supplicant

```

** /etc/wpa_supplicant.conf **
```

ap_scan=1
ctrl_interface=/var/run/wpa_supplicant
network={
ssid="*my_ssid*"        
scan_ssid=0        
proto=WPA        
key_mgmt=WPA-PSK        
psk="*my_router_password_in_plain_ASCII*"
pairwise=TKIP        
group=TKIP        
}

```

after that I executed:
```

sudo ifconfig wlan0 down
sudo dhclient -r wlan0
sudo wpa_supplicant -W -Dwext -iwlan0 -c/etc/wpa_supplicant.conf -dd
sudo ifconfig wlan0 up
sudo iwconfig wlan0 mode Managed
sudo dhclient wlan0

```And I just was online! O_o
As you can see, I did not follow just one guide...but I just messed up two different guides!
And since then when I login to XBMC it automatically connects and everything....
I can't understand though why my other crappy laptop with W7 connects @ 56Mbps and my XBMC connects @ only 18Mbps...it's kinda slow, too. But now I've got internet, so we can surely find a way to solve everything...Thank you for your precious help wild!!

Any other test I can make/pkg I can download to optimize the whole thing?

---

### Post by wildmanne39 on 2011-10-31
Hi, I am glad it is working, I suspected it was in the manual configuration.

I imagine it is because your signal strength is weak, if it get's much weaker it will not connect.
Thank you

---

### Post by GiH on 2011-10-31
Well, it took something like 3 days of work in the shell-only-way, but we made it!
Thank you again wild!!!
[SOLVED] :D

---

### Post by wildmanne39 on 2011-10-31
Hi, your welcome!
Enjoy

---

