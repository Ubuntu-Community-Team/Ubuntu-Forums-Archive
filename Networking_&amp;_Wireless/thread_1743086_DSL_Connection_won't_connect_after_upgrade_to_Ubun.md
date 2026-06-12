---
title: "DSL Connection won't connect after upgrade to Ubuntu 11.04"
date: 2011-04-29
forum: Networking &amp; Wireless
---

### Post by rereradu on 2011-04-29
Hey guys. Just updated to 11.04 Natty Narwhal on my Dell Inspiron 1501 this morning and I bumped into a problem. The DSL connection I used to connect to before the update doesn't work anymore. When I was running 10.10 I had this DSL connection set up via Network Manager (right-click on the network notification area=>edit connection=>add new, using PPPoE method and user name and pass from the ISP). Now I still get the AutoEth1 connection that is created (automatically), but when I try to connect to the DSL connection, it just doesn't connect. I tried deleting the connection and creating a new one, then rebooting, but still cannot connect. Another problem is that first time I ran 11.04, after beeing prompted to reboot at the end of the upgrade, I had my wireless on and while I was trying to get the DSL connection to work I switched it off (Fn+F2). Now if I try to turn it on again, it won't start. The network manager applet is looking also different now, wheter I left-click or right-click on it is the same (used to be different in previous releases), and this makes me even more confused. 
I know I probably shouldn't have rushed into upgrading without getting aquainted with the changes and the possible issues, but to be honest I wouldn't want to downgrade now to 10.10 (unity looks kind of interesting and I am looking forward to see it improved in the future) and I really need to fix this DSL connection problem on my laptop (using my desktop now) so, any help, guide or hint as to what to do next would be really appreciated. 
Best regards, Radu

---

### Post by fenolftaleina on 2011-04-29
I had the same problem at first, here's what I did:
I deleted all existing wired and DSL connections.
I created a new DSL connection, entered the username and password, and left the "Service" box blank.
I ticked both "Connect automatically" and "Available to all users".

I don't know if/how many of these details are relevant, but after doing this my DSL connection worked again, it's worth a try.

---

### Post by rereradu on 2011-04-30
Thanks. I already managed to connect using *ppoeconf*,and now the network manager says the device is not managed, so will stick to this solution. Anyway, I will keep your in mind. Again, many thanks.

---

### Post by seventeenth_sunrise on 2011-04-30
[QUOTE=rereradu;10742481]Thanks. I already managed to connect using *ppoeconf*,and now the network manager says the device is not managed, so will stick to this solution. Anyway, I will keep your in mind. Again, many thanks.[/QUO


Identical problem here! HELP! First off it was not connecting to DSL then when run pppoeconf; it has started showing in the indicator saying "Wired Networks, device not managed"

Heres my output to ifconfig eth1:

eth1    Link encap:Ethernet  HWaddr 00:1c:c0:19:af:fa  
          inet6 addr: fe80::21c:c0ff:fe19:affa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:384783 errors:0 dropped:30 overruns:0 frame:0
          TX packets:13541 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:34816299 (34.8 MB)  TX bytes:1218848 (1.2 MB)
          Interrupt:20 Memory:90380000-903a0000

---

### Post by rereradu on 2011-04-30
did you manage to connect to the Internet using *pppoeconf*? I am using this option and now the connection is automatically on after boot, although in the network manager applet I get the disconnected sign and the same "Device not managed" message. I guess it has something to do with the network interface configuration file or the network manger configuration. Found this resources, hope it will help:

I don't know if this works also for a wired connection, but you can try this: [http://www.accretionlogistics.com/2011/04/ubuntu-11-04-fix-the-wireless-device-not-managed/](http://www.accretionlogistics.com/2011/04/ubuntu-11-04-fix-the-wireless-device-not-managed/)

Some similar issue, but for 9.04 release, here: [http://www.craigmayhew.com/blog/2009/06/ubuntu-904-wired-network-device-not-managed/](http://www.craigmayhew.com/blog/2009/06/ubuntu-904-wired-network-device-not-managed/)

Hope this helps in any way.
Best regards,
Radu

---

### Post by seventeenth_sunrise on 2011-04-30
Hey thanks man!

Changing ifdown=TRUE in the /etc/NetworkManager/NetworkManager.conf does establish my Lan connection again but yet I can't connect to DSL. I heard there are other alternatives to Network Manager, but they aren't termed as a better solution in the forums.

Might purging the network manager and reinstalling it again help? Does it has a chance to break my distro?

---

### Post by rereradu on 2011-05-01
it's way out of my league. :P
if *pppoeconf  *doesn't work, and if you also tried fenolftaleina's solution:

> I had the same problem at first, here's what I did:
I deleted all existing wired and DSL connections.
I created a new DSL connection, entered the username and password, and left the "Service" box blank.
I ticked both "Connect automatically" and "Available to all users".

I don't know if/how many of these details are relevant, but after doing this my DSL connection worked again, it's worth a try. 	

and it still doesn't work, I at least am out of solutions.

---

### Post by mrinkus on 2011-05-02
Having a similar problem, but I wasn't using PPPoE before the update, I had been using a wireless connection.  For some reason I can't turn wireless back on for my laptop, and when I go to the networking tab it simply shows "wired connections" and "disconnected."  I can't switch back to using wireless.  Any ideas?  Tried hooking an ethernet cable up from the DSL box to my laptop but couldn't get anything to work there, I'm not too savvy with networking.

---

### Post by rereradu on 2011-05-02
I am also not so good with networking. What brand and model is your laptop? I am using a Dell Inspiron 1501 with a Broadcom wireless card and I used this solution:
[http://askubuntu.com/questions/36905/no-wireless-with-dell-inspiron-1501](http://askubuntu.com/questions/36905/no-wireless-with-dell-inspiron-1501) to fix my wireless problem. If you are using a BCM43XX type wirless card, this should do it for you. Basically you need to remove the STA driver from Additional Drivers (if it is activated) and install firmware-b43-installer from Synaptics Package Manager (I also have installed b43-fwcutter, you should make sure that one is selected to, I guess). After a restart I was able to turn on my wirleess using the keyboard combination (Fn+F2 for Dell). The only "glitch" is that I need to manually turn on my wireless each time I boot.
Hope this helps in anyway.

Best regards,
Radu

---

### Post by mrinkus on 2011-05-02
Looked through Synaptics and found the firmware, but when I tried installing them the Manager tried connecting to the internet to download necessary files (which it couldn't do).  Grabbed an ethernet cable and connected to my DSL box and tried the first solution (wiping wired/DSL network connections and creating a new DSL connection).  Still wouldn't connect to the internet (but an option for Wireless Connections has now appeared on the drop down menu, still can't connect wirelessly though, it says firmware needs to be installed, which I am assuming is the b43).

Any ideas on if I can get the necessary files on my desktop and put them on the laptop with a flash drive or something?  I feel like the problem will be solved as soon as that firmware is installed....

Thanks for all your help!

---

### Post by rereradu on 2011-05-03
Here it is:
[http://packages.debian.org/sid/firmware-b43-installer](http://packages.debian.org/sid/firmware-b43-installer)

Just click on the "all" button under architecture. When installing the package, if any dependencies aren't met, download the depending packages (marked with a red dot).

As for the wired connection....As far as I know, if you have a DSL box (which is actually a modem, and works like a router I think) you don't need to create a DSL connection on your Ubuntu laptop, as the modem creates the connection itself, or you need to create a connection using the modem firmware via your browser (this is usually how it's done in my country, at least). If your desktop is connected to the DSL box and it connects automatically to the Internet (this means your DSL box connects to the Internet through its firmware), then what you should normally do for your laptop is just to plug the ethernet cable in (without creating a DSL connection yourself). If your desktop is connected to your DSL box and has Internet connection, but your laptop doesn't, you should check some of the settings.
only thing I can think about now is:
open a terminal and run: ```
  sudo gedit /etc/network/interfaces
```a new text editor window will appear. it should (only) contain these lines
```
auto lo 
iface lo inet loopback
```I've seen on different threads on networking people post the output of different commands to give more info about the networking settings, devices, etc...
If any of the things above don't help, post the output of *ifconfig* and  *lspci *(just run the commands in a terminal and copy paste the output).

---

### Post by creontu on 2011-05-25
Removing the Service name in dsl settings did the trick for me. Did not recreate any connection settings.:)

---

### Post by valerauko on 2011-06-16
For me it works fine, though time to time it doesn't connect, but a reboot solves that. The "device not managed" message is very annoying, considering it worked perfectly fine in lucid.

---

