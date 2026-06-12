---
title: "how to connect to encrypted network using terminal"
date: 2010-05-16
forum: Networking &amp; Wireless
---

### Post by zenek89 on 2010-05-16
Hello !
I have lost my** GUI** interface on** Ubuntu 9.10** (by stupid mistake) 
I wanted to** uninstall Cairo dock**, and when I was deleting files on** "synaptic package manager"** I didn't take a look at what was going to be removed :| , so it removed most of packages responsible for my **GUI**.
I'm left just with **Terminal **and wallpaper LOL.

Now I need to install my ubuntu desktop back again... using this code

```
sudo get-apt install ubuntu-desktop
```but to do that I need to connect by Terminal to the internet using my wireless.
The only one network that I can connect too has **encryption: "On"** **(*I know the key*) **but I don't know how to type the key in.

Please help me, I can't stand using Windows anymore... And I can't just reinstall Ubuntu because I have a lot of important files on my ROOT account.

---

### Post by zenek89 on 2010-05-16
please help me guys...

---

### Post by daimaru on 2010-05-16
check at the bottom of the post where it says configure wireless 
you should have to check what your wlan cards adapter is called by using iwconfig and then use your "wlan0 eth1 etc" instead of my ath0. If dhcp is not working for you you will have to set up the connection manually using ifconfig  route add etc
[http://ubuntuforums.org/showthread.php?t=641598](http://ubuntuforums.org/showthread.php?t=641598)

---

### Post by zenek89 on 2010-05-16
thank You, I wish it will help me... I need only one more thing to know.
Do I have to write password inside "**<**....**>**" or without them?? and is it going to work with **WPA-PSK** encryption??

---

### Post by daimaru on 2010-05-16
without the < > if you have spaces in your password or the essid you have to put it in quotes "mykey here" 
I am not sure if this will work with** wpa-psk havent **[B]used it since WEP times :) good luck 

edit: going to try it now on my laptop. will report back afterwards

[/B]

---

### Post by zenek89 on 2010-05-16
It didn't work with **WPA-PSK** 
this error report printed out
```
Error for wireless request **"Set Encode" "(8B2A)"** :
invalid argument "Password"
```

if it says set encode, then isn't there any way to set it up, so would work with **WPA-PSK ?**

---

### Post by daimaru on 2010-05-16
really sorry, it does not seem to work at all with wpa ... damn have to check for a different way to connect. the  iwconfig key thing only accepts ascii encoded stuff and my wpa key is a bunch of different chars jumbled together so its not accepting it at all. even tried a simple phrase but it does not accept the encoding. :(

---

### Post by zenek89 on 2010-05-16
it's all OK... thanks for Your effort.

---

### Post by chili555 on 2010-05-16
Manual configuration is not likely to work with Network Manager running; I have tried, err, failed many times. The only thing that worked was to do:```
sudo /etc/init.d/network-manager stop
sudo gedit /etc/network/interfaces
```Add lines for wlan0, or whatever your interface is, as follows:```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wpa-ssid mylilrouter
wpa-psk coldbeer
```Substitute your details, of course. Then do:```
sudo /etc/init.d/networking restart
```It may work.

If not, you can always remove Network Manager. If you reinstall NM, you will need to remove, or at least comment out the wlan0 lines:```
auto lo
iface lo inet loopback

#auto wlan0
#iface wlan0 inet dhcp
#wpa-ssid mylilrouter
#wpa-psk coldbeer
```

---

### Post by zenek89 on 2010-05-16
thanks Chili, but anyway... I can't open **"gedit" **because I'm missing **GUI** interface... (check my 1st post)

---

### Post by chili555 on 2010-05-16
Oops! Sorry about that! Do you know how to use vim? I wonder if it's installed by default. If so, do:```
sudo vim /etc/network/interfaces
```Press Insert. Use the arrow keys to get to your text. Type it all in and when you are satisfied, press Esc. Then do Shift + :. Type in wq (write and quit) and press Enter.

You might also have nano:```
sudo nano /etc/network/interfaces
```The instructions are pretty much clear when you start it.

---

### Post by zenek89 on 2010-05-17
[FONT=monospace]I don't know why but it** didn't** work for me... 
I just suggest, but when I type in "iwconfig ra0" to check my card, if it says "**Acces point: not-associated**" it means that I'm **not connected** to the network... right? 

I used** nano **to edit the file and I'm not sure about couple of things
[/FONT]```

auto lo                
iface lo inet loopback  ** <-------- these two should be erased **


------------------------------------------------------------------------

auto wlan0                
iface wlan0 inet dhcp  
wpa-ssid mylilrouter    **<-------- and these typed in and saved**
wpa-psk coldbeer       

```where "mylilrouter" is ESSID of the network, and "coldbeer" is a password right?? 

thank's for the time You spend for it but I'm still in the dot.... I need my ubuntu GUI back, maybe if You know some other way to get it back, please just let me know. THX !!

---

### Post by chili555 on 2010-05-17
> if it says "Acces point: not-associated"Correct, you are not connected. When you restarted networking, wasn't there output that suggested that dhclient was trying to connect? For example:> Sending on   LPF/wlan0/99:19:x2:z2:1b:88
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPOFFER of 192.168.1.103 from 192.168.1.254
DHCPREQUEST of 192.168.1.103 on wlan0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.103 from 192.168.1.254
[COLOR="Blue"]bound to 192.168.1.103[/COLOR] -- renewal in 40305 seconds.
 * Stopping the Firestarter firewall...
   ...done.
 * Starting the Firestarter firewall...
   ...fail!
run-parts: /etc/network/if-up.d/50firestarter exited with return code 2
ssh stop/waiting
ssh start/running, process 5136> auto lo                
iface lo inet loopback   <-------- these two should be erased 

No. The lo stanzas should never be disturbed or touched. Linus will be angry with you!

I suggest you try again.

Of course, you could get out your install CD, or burn a new one on another computer, and do:```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install ubuntu-desktop xserver-whomever etc.
reboot
```

---

### Post by zenek89 on 2010-05-17
OK Chilli so.... After I restart networking 

```

Sending on   LPF/wlan0/99:19:x2:z2:1b:88
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4 <---- I'm stuck at this point
**interval # just changes **and prints out about 10 more of these but just with different number
```and some else info prints out but it's quite too long to copy it on a piece of paper and then back on computer.

I'll try to back these two stanzas up and I'll let U know. 

```
wpa-ssid mylilrouter    <-------- isn't it supposed to be **essid**, instead of **ssid**?

```

---

### Post by chili555 on 2010-05-17
> isn't it supposed to be essid, instead of ssid?I can't quote any official documentation, however, it works perfectly for me with wpa-ssid.

Some people are concerned about having a file with the password in clear text, as opposed to a wpa_supplicant.conf file. However, it's in clear text there, too! If someone has access to your machine and a live CD, they can find your password. If your machine is stolen or otherwise compromised, shut down your internet connection and immediately change the password.

---

### Post by zenek89 on 2010-05-17
it's good to know, thanks... I'm about to start working on connecting ubuntu to the internet, I was little busy so I couldn't do it yet.

---

### Post by zenek89 on 2010-05-17
```
listening on LPF/ra0/00:02:6F:5b:du:fa
sending on   LPF/ra0/00:02:6F:5b:du:fa
sending on   Socket/fallback
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping
                                                                                                                                       [OK]
```this is what I'm still getting even after typing in 

```


auto lo                
iface lo inet loopback  

auto ra0               
iface ra0 inet dhcp  
wpa-ssid mynet   
wpa-psk mypass


```inside "/etc/network/interfaces"





Btw I tried to add "**cdrom**" source to "**apt**"
it did add the source, but didn't install anything after I typed 

```

sudo apt-get update
sudo apt-get install ubuntu-desktop

```it came up with the list of apps it was willing to install, and after I agreed,
it was printing errors one by one, with an explanation that it cannot download needed files.

**I'm sorry, for that I'm starting to be annoing and still didn't get it to work but I'm just doing everything exactly as You R explaining me.**

---

### Post by chili555 on 2010-05-17
Not annoying at all. We shall endeavor to persevere.

We expect errors when apt cannot reach the on line repositories; however it ought to get packages from the CD. Maybe we can force it. ```
sudo nano /etc/apt/sources.list
```Comment out *everything *except the CD. Here is an example of a line commented out:```
[COLOR="Red"]#[/COLOR]deb http://archive.canonical.com/ubuntu lucid partner
```Proofread, save and close nano. Now do:```
sudo apt-get update
sudo apt-get install ubuntu-desktop
```Another trick to try is:```
ls /var/cache/apt/archives/ | grep desk
```Is the package in there? You might try to install it from there:```
cd /var/cache/apt/archives/
sudo dpkg -i ubuntu-desktop*
```I have never tried what you are doing, aside from the network part, so I am feeling around in the dark a bit.

If you amend /etc/apt/sources.list, don't forget to change it back after you finish.

---

### Post by chili555 on 2010-05-17
> DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping
When this was happening, was Network manager running?```
ps aux | grep Network
```Is the behavior improved if you do:```
sudo /etc/init.d/network-manager stop
sudo dhclient ra0
```

---

### Post by zenek89 on 2010-05-19
I'm sorry guys but I just gave up... I will just reinstall ubuntu, because we all run out of ideas. And I need my ubuntu back. I'm gonna have to install all my drivers back, one by one again and I'll loose some of important files. But Ubuntu is worth it :)

Do You think that I'm supposed to mark this thread as **Solved?**

---

