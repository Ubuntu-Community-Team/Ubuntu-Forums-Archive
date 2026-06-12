---
title: "no wireless networks available"
date: 2009-02-19
forum: Networking &amp; Wireless
---

### Post by sileconsoul on 2009-02-19
ive got a compaq presario r4000
with a broadcom bcm4318 rev 02 
im running ubuntu 8.04.2, updated.
ive been using [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Step%201:%20All%20BCM43xx%20-%20Install%20NDISWrapper%20and%20Blacklist%20Native%20Driver]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Step%201:%20All%20BCM43xx%20-%20Install%20NDISWrapper%20and%20Blacklist%20Native%20Driver")
to try to fix it myself

i did have the hardy ssb module bug
but i fixed it and now lshw gives me this..

module=ndiswrapper driver=ndiswrapper+bcmwl5

i also compiled ndiswrapper from source


iwconfig gives me this..

iee:802.11g essid: off/any
mode:managed frequency 2.462 ghz access-point: not-associated
bit rate:52 mb/s  tx-power: 32 dbm
rts thr: 2347b  fragement thr: 2346 b
power management: off
link quality:0 signal level:0 noise level:0
rx invalid nwid:0 rv invalid crypt:0 rx invalid frag:0 
tx excessive retries:0 invaled misc:0 missed beacon:0

 Kernel/architecture (including 32 vs. 64 bit): 2.6.24-23-generic  i686

any ideas?
oh yeah, the wireless runs with my xp pro desktop and my gf can connect wirelessly with her dell laptop.
also, its my first time using ubuntu on a regular basis. so im fairly new at this.

---

### Post by theDaveTheRave on 2009-02-19
sileconsoul

it sounds as though you are having a problem that was remarkably similar to mine, although I was using an atheros chip.

Is this version of Hardy you are using a new install?? if not try logging into another kernel from the grub menu.

When I had this problem I suddenly found out that the switch on the front of the laptop, that had previously never worked, now had mutliple levels of funcionality.

if you get a good response from the following command

```

ifconfig
iwlist scan
lshw -C network
dmesg | grep -e <name of your network interface>

```

you can determine the <name of your network interface> in the output of <ifconfig> here is mine, with the network interface in blue, so you know what you are looking for.

```

davem@Dartagnon:~$ ifconfig -a
[COLOR="Navy"]ath0[/COLOR]      Link encap:Ethernet  HWaddr 00:19:7d:40:b8:c0  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1474 (1.4 KB)  TX bytes:4289 (4.2 KB)

eth0      Link encap:Ethernet  HWaddr 00:16:36:c8:51:d3  
          inet addr:192.168.1.120  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:36ff:fec8:51d3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19754 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16609 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:22749671 (22.7 MB)  TX bytes:2652015 (2.6 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 B)  TX bytes:100 (100.0 B)

pan0      Link encap:Ethernet  HWaddr b6:34:fd:44:d0:b4  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

[COLOR="Navy"]wifi0[/COLOR]     Link encap:UNSPEC  HWaddr 00-19-7D-40-B8-C0-00-00-00-00-00-00-00-00-00-00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:9214 errors:0 dropped:0 overruns:0 frame:17236
          TX packets:328 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:2192843 (2.1 MB)  TX bytes:21666 (21.6 KB)
          Interrupt:18 

davem@Dartagnon:~$ 

```

you will notcie that the hardware address is the same for each, just one of them is a "pseudonym" for the other (it wraps it up in the functionality - at least that is how I understand it too work?)

if you still have problems check out the installed kernel modues with 
```

lsmod

```
and see if there are any potential conflicts. If so you may need to remove the "nasty" ones and re-install the "good" ones, I'm not the person to ask on this though... I'm sure that someone else has had problems with the same device as yours, and I'm sure you will find someone else who has been able to get it working somehow.

if you still don't have any joy, send the responses from those commands and I'll see if I can help out.

David

---

### Post by sileconsoul on 2009-02-19
[[IMG]http://img407.imageshack.us/img407/170/screenshotfe4.th.png[/IMG]](http://img407.imageshack.us/my.php?image=screenshotfe4.png)

[[IMG]http://img407.imageshack.us/img407/4538/screenshot1da6.th.png[/IMG]](http://img407.imageshack.us/my.php?image=screenshot1da6.png)

[[IMG]http://img8.imageshack.us/img8/2777/screenshot2hb2.th.png[/IMG]](http://img8.imageshack.us/my.php?image=screenshot2hb2.png)

[[IMG]http://img518.imageshack.us/img518/5663/screenshot3lx8.th.png[/IMG]](http://img518.imageshack.us/my.php?image=screenshot3lx8.png)

no clue what to do now. again, sorry, i'm new at this.

---

### Post by Crafty Kisses on 2009-02-20
Hey there! Let's see if we can't get this card up and running with ndiswrapper, first off, you need to install ndiswrapper, so run the following command:
```
sudo apt-get install ndiswrapper-common
```
Once you have ndiswrapper installed you need to grab the XP driver for your Broadcom wireless card, which you can get right [here.]("http://ubuntuforums.org/attachment.php?attachmentid=11584&d=1150897000") So when you have the XP driver, save it to your desktop or wherever you like, then run the following:
```
sudo ndiswrapper -i bcm4318.inf
```
The driver would be named different probably so substitute the real driver name, so once you have done that, run the following:
```
sudo ndiswrapper -l
```
If the drivers are installed correctly, you will get results similar to this:
```
Installed ndis drivers:
bcmwl5a driver present, hardware present
```
You're almost done, you then need to load the ndiswrapper module, so run the following:
```
sudo modprobe ndiswrapper
```
So the module is loaded, now you need to make sure it loads on every start:
```
sudo ndiswrapper -m
```
Once you have done that, reboot and your wireless card should be working.

---

### Post by sileconsoul on 2009-02-20
step 1 ndiswrapper was already installed
step 2 i get stuck at     ```
sudo ndiswrapper -i bcm4318.inf
```
       when i did try to do the command, i got "couldnt open bcm4318.inf: no such file         or directory at /usr.sbin.ndiswrapper line 219

i also extracted the drivers from bcm4318.tar.gz that you linked me, the driver inside is the same i am currently running, when i did (wifidriver in bcm4318.tar.gz)```
sudo ndiswrapper -i bcmwl5.inf 
```

step 3 when doing ```
sudo ndiswrapper -l

bcmwl5: driver installed
device (14e4:4318) present (alternate driver: bcm43xx
```

---

### Post by Crafty Kisses on 2009-02-20
Well it appears the drivers are present, it gave you these results:
```
bcmwl5: driver installed
device (14e4:4318) present (alternate driver: bcm43xx
```
So try rebooting, then right click on the NetworkManager and select Enable Wireless, and see if that works.

---

### Post by sileconsoul on 2009-02-20
ok, wireless is enabled.
but i still dont have internet access.

also my internet is secured with wpa personal type password.
dont know if that makes a difference

thanks for your time. i noticed you help alot of people out, its really appreciated.

---

### Post by Crafty Kisses on 2009-02-20
Hey there once again! Let's try something else, run the following:
```
sudo gedit /etc/modprobe.d/blacklist
```
Add the following line to the text-file:
```
blacklist bcm43xx
```
Once you have done that, run the following:
```
sudo rmmod bcm43xx
```
Then reboot, and see if that doesn't get the card up and running.

---

### Post by sileconsoul on 2009-02-21
its already blacklisted , i checked the actual mousepad file and

```
sudo rmmod bcm43xx
ERROR: module bcm43xx does not exist in /prov/modules
```

---

### Post by Crafty Kisses on 2009-02-21
Try running the following:
```
sudo gedit /etc/modprobe.d/ndiswrapper
```
Then try changing the following line:
```
alias wlan0 ndiswrapper
```
To the following:
```
alias eth1 ndiswrapper
```
See if that doesn't work.

---

### Post by sileconsoul on 2009-02-21
gedit dosnt work```
sudo: gedit: command not found
```

---

### Post by Crafty Kisses on 2009-02-21
Just copy and paste the command I gave you. It's more accurate that way.

---

### Post by sileconsoul on 2009-02-22
i copy pasted your commands exactly.
still the error gedit command not found.


while doing the ssb work around, and making it permanent, i managed to add some code to /etc/modprobe.d/ndiswrapper. by using

```
echo -e '#Hardy ssb/ndiswrapper workaround, added' `date` '\ninstall ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;' | sudo tee -a /etc/modprobe.d/ndiswrapper
```

gedit, does not work for me. but that did. both should edit the ndiswrapper file, if i understand correctly. i dont exactly know what part of the code above allowed me to edit /etc/modprobe.d/ndiswrapper, but i do know it worked but gedit does not.

sorry for all the trouble.

---

### Post by Crafty Kisses on 2009-02-22
That's weird gedit isn't installed, here try installing gedit by running the following:
```
sudo apt-get install gedit-common
```
Then once it's installed, try this command again:
```
sudo gedit /etc/modprobe.d/ndiswrapper
```
If you're still getting the error, try nano, you can do that by running the following:
```
sudo nano /etc/modprobe.d/ndiswrapper
```

---

### Post by sileconsoul on 2009-02-22
i had to use nano, even after gedit isntallion and reboot, it didnt work.

i did manage to range wlan0 to eth1.
but i still dont have access.
i have a wireless light or whatever. and the only time it ever turned on is when the module was being run by ssb.

---

### Post by Crafty Kisses on 2009-02-22
Here's what we're going to do, we are going to start from fresh and try again, if this doesn't work I may have a solution, but let's try this once again. I have a different driver for you this time, download it right [here.]("http://ubuntuforums.org/attachment.php?attachmentid=48087&d=1193544558") Once you have downloaded that, you need to remove your old driver, so run the following:
```
sudo ndiswrapper -e <drivername>
```
Once it's removed, we can repeat the same steps to install the new driver, so run the following:
```
sudo ndiswrapper -i <drivername>
```
Once it's installed, remember make sure it's there:
```
sudo ndiswrapper -l
```
If it's there, you should get results similar to this:
```
bcmwl5, driver installed, 
hardware present
```
Try that, and get back to me.

---

### Post by sileconsoul on 2009-02-22
ok i want to make this clear, so im not making any mistakes.
the driver you gave me a link for. bcm4318.all , where do i put it and what do i do with it? do i simply extract it to the desktop and then run
```
sudo ndiswrapper -i bcmwl5
```

---

### Post by Crafty Kisses on 2009-02-22
So for example you extract the folder to your desktop and it's called "bcm4318" and the folder that the .inf file is called "WinXPdriver", you would want to do the following:
```
cd /home/username/Desktop/bcm4318/WinXPdriver
```
Then once you're in the directory where the .inf is, you can run the following:
```
sudo ndiswrapper -i <drivername>
```
Where "drivername" is, rename it with the .inf file.

---

### Post by sileconsoul on 2009-02-22
ok i get it. uninstalled old driver.
installed new one. still the same name bcmwl5.inf

check with ndiswrapper -l

driver is installed, device is present.
still no wireless

---

### Post by Crafty Kisses on 2009-02-22
Ok, here's what I want you to do, remove the driver by running the following:
```
sudo ndiswrapper -e <drivername>
```
Then install the following package:
```
sudo apt-get install ndisgtk
```
Once you have that package installed, run the following:
```
sudo ndisgtk
```
Once the window is open, click "Install new drivers" once you have done that, open the bcmwl5 driver, and click "Install" then see if that works.

---

### Post by sileconsoul on 2009-02-22
ok,uninstalled my driver, installed ndisgtk, installed the driver thru ndisgtk , and then i hit 'configure network' and while i did that..
this popped up in my terminal
```
(network-admin:6250): Gtk-WARNING **: Unknown property: GtkComboBox.items


** (network-admin:6250): CRITICAL **: Unable to lookup session information for process '6250'

```

---

### Post by Crafty Kisses on 2009-02-22
Did it actually let you access the configure network option? I wouldn't really worry about the Terminal outputs while your using ndisgtk, just see if you can access it.

---

### Post by sileconsoul on 2009-02-22
yes i accessed the configuration menu, i tried roaming and setting the specific network name and password
but on the plus side. my wireless light is always on now.

---

### Post by Crafty Kisses on 2009-02-22
Try rebooting and see if you can connect. What are the results of this command?
```
ping google.com
```

---

### Post by sileconsoul on 2009-02-23
```
ping: unkown host google.com
```

---

### Post by Crafty Kisses on 2009-02-23
Alright, let's make sure those bcm modules are out of the kernel, so run the following:
```
sudo modprobe -r bcm43xx
```
Once you have done that, run the following:
```
sudo ifdown wlan0
sudo ifup wlan0
```
If that doesn't work, remove the driver once again, and navigate to the driver folder, and let's try a manual installation, but this time, I want you to run this after you have confirmed you installed the driver, so for example, you would run:
```
sudo ndiswrapper -i <drivername>
sudo ndiswrapper -l
```
Once it says "The driver is present", I want you to run the following:
```
sudo depmod -a
sudo modprobe ndiswrapper
```
Then try and manually connect, you can do the following:
```
iwconfig eth1 essid <your_accesspoint_essid_here>
```
If you have an encryption on your router, you can alternatively run the following:
```
iwconfig eth1 key <your_key_here>
```
Then once you have done that, you can run the following:
```
dhclient eth1
```
Essentially this should work, but if it doesn't post back, and I'll help you further.

---

### Post by sileconsoul on 2009-02-23
got half way until i was trying to connect. then i got this. would it be better if i upgraded to 8.10?
```
iwconfig eth1 essid Alyssas Network 3
error for wireless request 'set essid" (8B1A) :
SET failed on device eth1; operation not permitted
```
```
iwconfig eth1 key <********>
error for wireless request 'set Encode" (8B2A) :
SET failed on device eth1; operation not permitted
```

---

### Post by Crafty Kisses on 2009-02-23
Try putting "sudo" in front of that command, so for example:
```
sudo iwconfig eth1 essid <your_accesspoint_essid_here>
```

---

### Post by sileconsoul on 2009-02-23
all the commands worked once i put sudo.
except for ```
sudo dhclient eth 1
```
[[IMG]http://img240.imageshack.us/img240/5999/screenshot999.th.png[/IMG]](http://img240.imageshack.us/my.php?image=screenshot999.png)

---

### Post by Crafty Kisses on 2009-02-23
Alright, reboot and see if you can connect by running the following:
```
sudo iwconfig eth1 key <your_key_here>
```

---

### Post by sileconsoul on 2009-02-23
no go, im trying to understand as we're doing this. i understand we're trying to connect to the router but is the router refusing or is the laptop not working? what are we trying to figure out?

[[IMG]http://img4.imageshack.us/img4/8232/screenshot111.th.png[/IMG]](http://img4.imageshack.us/my.php?image=screenshot111.png)

---

### Post by Crafty Kisses on 2009-02-23
Alright my friend, that's fine, here's what were are going to do. We are going to try a different driver again. So you can grab that driver right [here.]("ftp://ftp.linksys.com/pub/network/wusb11_v28_dr.zip") Now we want to remove the old drivers, so run these commands:
```
sudo ndiswrapper -e <drivername>
```
Once you have removed the current driver, make sure you have this module blacklisted:
```
blacklist bcm43xx
```
So just make sure, then once you have done that run these following commands in order:
```
rmmod bcm43xx 
rmmod ndiswrapper 
sudo modprobe ndiswrapper
```
If you have any permission issues, just put "sudo" in front of those commands, then you want to navigate to the driver and install it, so run these commands:
```
cd /home/username/Drivers
ndiswrapper -i WMP54GS.inf
ndiswrapper -l
ndiswrapper -m
```
Then restart your computer, then once your back into Xubuntu, run these commands:
```
iwconfig
sudo iwconfig wlan0
sudo iwconfig wlan0 channel
sudo ifconfig wlan0 up
sudo dhclient
```
Then you should be set my friend.

---

### Post by sileconsoul on 2009-02-23
```
blacklist bcm43xx
bash:blacklist: command not found
```

but i did go check in /etc/modprobe.d/blacklist , and the following are blacklisted (well.. just writen in the file i guess) bcm 43xx, wl , bcm43xx, wl

---

### Post by Crafty Kisses on 2009-02-23
Oh when you blacklist the module, you want to run this first:
```
sudo gedit /etc/modprobe.d/blacklist
```
Then you can add the blacklist at the end of the file.

---

### Post by sileconsoul on 2009-02-23
gedit still dosnt work
but i did do nano and i found out i had these drivers blacklisted, which i think i did on my own while i was trying to fix it myself.

( bcm 43xx, wl , bcm43xx, wl )


so on we go to the next step...

i want to navigate to the drivers 
```
cd  /home/joel/drivers
no such file or directory
```

now those drivers that i just downloaded , i extracted it, and its an exe inside and i know exe's dont work like they should in ubuntu, but i dont know what to do with it

---

### Post by Crafty Kisses on 2009-02-24
Go to **System->Administration->Synaptic Package Manager** and search for the program called WINE. Once you have installed WINE, open the driver which is in .exe format and extract it with WINE.

---

### Post by sileconsoul on 2009-02-24
ok extracted, had to manualy open the terminal from where it was extracted because for some reason the terminal didnt read the directory changes. it was there, but i couldnt cd to it.

so right click open terminal here.
```
ndiswrapper -i WMP54GS.inf 
couldnt open WMP54GS.inf: no such file or directory at /usr/sbin/ndiswrapper line 219
```

---

### Post by Crafty Kisses on 2009-02-24
Actually what you can do, is once you have the .exe on your desktop, right click and extract here, then you will get the .inf file.

---

### Post by sileconsoul on 2009-02-24
getting the same error, so i double checked and the only .inf file in the drivers folder is NETUSB.INF

---

### Post by Crafty Kisses on 2009-02-24
That should be the correct one. Anyway I got a PM from TripWire7 and he said maybe this link could help you: [http://ubuntuforums.org/showthread.php?t=958011&highlight=broadcom+bcm+4318+rev+02](http://ubuntuforums.org/showthread.php?t=958011&highlight=broadcom+bcm+4318+rev+02). Take a look at that link, and if that doesn't help you, then let me know and I can help you further.

---

### Post by sileconsoul on 2009-02-24
ok i tried that. didnt do much. in fact my wireless light is no longer on, and when i do iwlist scan , eth1 does not scan says```
 interface dosnt support scanning: no such device
```


i checked with lshw -c network and my driver and module are now bcm43xx instead of ndiswrapper + bcmwl5.inf

---

### Post by Crafty Kisses on 2009-02-24
Just to confirm that we are working with the card that I think I'm working on what are the results of these commands?
```
sudo lshw -C network
lspci
```

---

### Post by sileconsoul on 2009-02-24
[[IMG]http://img23.imageshack.us/img23/5537/screenshot22.th.png[/IMG]](http://img23.imageshack.us/my.php?image=screenshot22.png)

[[IMG]http://img24.imageshack.us/img24/6823/screenshot33.th.png[/IMG]](http://img24.imageshack.us/my.php?image=screenshot33.png)

---

### Post by Crafty Kisses on 2009-02-24
Ok, so have you checked **System->Administration->Hardware Drivers** and see if anything comes up for you card?

---

### Post by sileconsoul on 2009-02-24
yeah when i updated from 7 to hardy, i downloaded the drivers directly after that

---

### Post by Crafty Kisses on 2009-02-24
So you rebooted once you installed those, and still no dice? Also did you ever uninstall those drivers when you installed them.

---

### Post by sileconsoul on 2009-02-24
the only time i've ever seen any signs of life from the wireless card, is with the ssb module and our most recent setup of ndiswrapper+bcmwl5.inf.

installing and putting the drivers in use when i first upgraded to hardy didnt do  much, not sure what you mean 'did you ever uninstall those drivers when you installed them'

---

### Post by Crafty Kisses on 2009-02-24
Go to System->Administration->Hardware Drivers and make sure those drivers are uninstalled.

---

### Post by sileconsoul on 2009-02-24
i dont quite remember which one it was, but the only two options are ati accelerated graphics driver and software modem. so i disabled software modem, will that do?

---

### Post by Crafty Kisses on 2009-02-24
Hmmm, I don't think that would be it. Are you using 64-bit or 32-bit Xubuntu?

---

### Post by sileconsoul on 2009-02-24
i686 - 32 bit

the driver that i did install when i upgraded, was a broadcom, possibly bcm43xx , i cant remember tho. its no longer in hardware drivers

---

### Post by Crafty Kisses on 2009-02-24
What are the results of this command?
```
lsmod | grep ndiswrapper
```

---

### Post by sileconsoul on 2009-02-24
nothing

---

### Post by Crafty Kisses on 2009-02-24
That means there is no ndiswrapper module, try running the following:
```
sudo modprobe ndiswrapper
```
Then run this command again:
```
lsmod | grep ndiswrapper
```
Then see if anything comes up, this MIGHT be the problem.

---

### Post by sileconsoul on 2009-02-24
```
ndiswrapper   192920  0
      usbcore       146412  4 ndiswrapper,ehci_hcd, ohci_hcd
```

---

### Post by Crafty Kisses on 2009-02-24
That's really weird the modules are not loading at start, if you have a current driver installed run the following:
```
sudo ndiswrapper -m
```
That should make the module load at every start, so once you've done that reboot and see if the module is there. I'd also like to point you out to this new thread about your wireless card, follow his instructions, maybe you will have different results: [http://ubuntuforums.org/showthread.php?t=1079617](http://ubuntuforums.org/showthread.php?t=1079617).

---

### Post by sileconsoul on 2009-02-25
the link you gave me didnt do much, other then updating ndiswrapper.
but i did discover this [http://www.ing.unibs.it/openfwwf/]("http://www.ing.unibs.it/openfwwf/")

and im trying to try it, but for some reason i cant copy the b43-tools```
/usr/bin/git-clone: 374: curl: not found
```

do you know anything about git? or possibly something else to try?

---

### Post by Crafty Kisses on 2009-02-25
This was the link I was actually looking for, if this doesn't work let me know and I'll attempt to help you further. [http://linuxfans.betaserver.org/](http://linuxfans.betaserver.org/).

---

### Post by sileconsoul on 2009-02-25
i cant get past step 2
```
git clone http://git.bu3sch.de/git/b43-tools.git
/usr/bin/git-clone: 374: curl: not found
```

---

### Post by Crafty Kisses on 2009-02-25
Try installing "git", do the following:
```
sudo apt-get install git
```

---

### Post by sileconsoul on 2009-02-25
still the same issue
```
initialized empty git repository in /home/joel/b43-tools.git/
 /usr/bin/git-clone: 374:curl : not found 
```

---

### Post by Crafty Kisses on 2009-02-25
You said you had ndiswrapper compiled from source, so I'm guessing you have build-essential installed, but if you don't run the following command and it will install it for you, in order for you to compile drivers, you need this:
```
sudo apt-get install build-essential
```
Anyway, I think this link is your solution here, [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43). If that doesn't work I'll try and help you further, my methods in essence should have worked but for some reason failed. The root of the problem I think lies within the modules, I remember when I asked you to grep the ndiswrapper module nothing came up for the ndiswrapper module. So it could be a module issue here too, but follow that tutorial and if that doesn't work I'll try and see if I can help you further.

---

