---
title: "bcm4318 wireless not working"
date: 2009-01-22
forum: Networking &amp; Wireless
---

### Post by _BigWings_ on 2009-01-22
Hey everyone,

I am reconfiguring a laptop of a friend of mine to run ubuntu and everything went fine except for the darn wireless which is not working. For the last three days I have been reading forum posts and found out that this is a common issue. I found several posts with step by step guides to fix the problem and I have tried following them from a clean install (I am aleady on my third clean install) but nothing has worked so far.

Some information:
Laptop: compaq presario v2000
OS: ubuntu 8.10
Wireless: Broadcom BCM4318

I also tried activating the bc43 driver in system->administration->hardware drivers and while that does light up the wireless light after a restart, I still can't connect to any networks.

If any knowledgeable person would be so kind to run me through the steps then that would be great and that would help me to convert someone to ubuntu, which, without wireless, is going to be a tough sell. 

M

---

### Post by Ayuthia on 2009-01-22
Are you able to see any wireless sites and also are you using WEP/WPA?  Can you post the results of:
```
ifconfig
iwconfig
sudo iwlist scan
```

---

### Post by acimmarusti on 2009-01-23
Though it is premature to say, I think you would find this info very useful:

[http://ubuntuforums.org/showthread.php?t=1047297&highlight=4318](http://ubuntuforums.org/showthread.php?t=1047297&highlight=4318)

If you already have installed the newest firmware, I suggest you reinstall ubuntu and use that package I mention in my thread. It's old, but it works well.

---

### Post by _BigWings_ on 2009-01-24
Ayuthia:
I am using wep 64bit on my network. The results of the commands you suggested are as follows:

```
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:36:5b:a8:66  
          inet addr:192.168.0.106  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:36ff:fe5b:a866/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2815 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2509 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2584596 (2.5 MB)  TX bytes:529632 (529.6 KB)
          Interrupt:18 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:14:a5:af:e8:3b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-14-A5-AF-E8-3B-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
```

```
sudo iwlist scan
[sudo] password for courtney: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.
```


acimmarusti:
It is not entirely clear from your post what I should be doing. So you are saying the b43 divers that come with ibex might no be good?

---

### Post by sampbar on 2009-01-24
Hello,

Could i suggest that you tried my guide: [http://www.sampbar.com/2008/11/broadcom-bcm4318-ubuntu-intrepid.html]("http://www.sampbar.com/2008/11/broadcom-bcm4318-ubuntu-intrepid.html")

It uses NDISWrapper and has a high success rate, any problems feel free to email me: samuelbarrett {at} sampbar.com or just reply to this thread.

Samuel

---

### Post by acimmarusti on 2009-01-24
Hey there,

Go here, download the deb package under b43-firmware

[http://ubuntu.cafuego.net/dists/hardy-cafuego/broadcom/](http://ubuntu.cafuego.net/dists/hardy-cafuego/broadcom/)

(I know you are going to say this package is for hardy ubuntu 8.04, but trust me...I've tried the package meant for intrepid and it doesn't work!)

Once you do that, double click on the package to "execute" it. It will probably ask you for your administrator password. When you are done, restart your computer. Your wireless light should turn on after you log back in ubuntu and you should be able to detect wireless connections close to you.

I hope this works for ya. It has worked for me. If it complains saying that you have newer firmware installed, then force the installation.

---

### Post by _BigWings_ on 2009-01-24
Thank for the guide man, it i the most comprehensive I have seen so far, also, it is the first one that use the driver ending in a. So that might work. I tried running though it quickly but hit a few snags. 
I would love to use the shell scripts but it is hard to see what they do and if anything went wrong with them because the terminal window gets closed right after the script finishes.
Anyways, one of the problems I have: I can't copy anything to the init.d folder, I get permission denied.

I'll be gone for the rest of the week, but when I come back I'll definitely try again.

Thanks for the help so far.

---

### Post by sampbar on 2009-01-24
Ok, Drop me an email when your back: samuelbarrett {a} sampbar.com

Also about the permission denied: Type "sudo nautilus" in to a terminal then enter your password. A file browser window will pop up. Then you should be able to just drop the file in the correct folder!

---

### Post by _BigWings_ on 2009-02-02
I am trying to follow sampbars tutorial after a clean install of 8.10

Here is how I fared so far:
step 1) done
step 2) it warns me that there is also a version in the software channel and that it would be better to use that, i used the one from the disc and it installs fine

step 3) Here is what i got after dragging the .sh file into an open terminal window:

```
courtney@courtney-laptop:~$ '/home/courtney/Desktop/BCM4318 Ubuntu Intrepid/step3.sh' 
[sudo] password for courtney: 
blacklist bcm43xx
blacklist wl
```

step 4) Done, i also copied the .sys file to the desktop.

step 5) Here is what I got:

```
courtney@courtney-laptop:~$ '/home/courtney/Desktop/BCM4318 Ubuntu Intrepid/step5.sh' 
sudo: cd: command not found
couldn't open bcmwl5a.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219.
auto lo
iface lo inet loopback

adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper ...

************************************************************************
*
* The update-modules command is deprecated and should not be used!
*
************************************************************************

ndiswrapper
ENABLED=0
```

it seems to me that something went wrong here so I thought i' better stop and ask for directions before proceding.

M

---

### Post by leroy1086 on 2009-02-02
> **acimmarusti said:**
> Hey there,

Go here, download the deb package under b43-firmware

[http://ubuntu.cafuego.net/dists/hardy-cafuego/broadcom/](http://ubuntu.cafuego.net/dists/hardy-cafuego/broadcom/)

(I know you are going to say this package is for hardy ubuntu 8.04, but trust me...I've tried the package meant for intrepid and it doesn't work!)

Once you do that, double click on the package to "execute" it. It will probably ask you for your administrator password. When you are done, restart your computer. Your wireless light should turn on after you log back in ubuntu and you should be able to detect wireless connection for this firmwares close to you.

I hope this works for ya. It has worked for me. If it complains saying that you have newer firmware installed, then force the installation.

First - thank you for this link.  I am a brand new linux user.  I bought the Ubuntu 8.04 from Best Buy - they said they did not have it in stock, but I made them do an inventory search and they had two copies.  They were located with the foreign language courses! lol!  

I installed it on a Dell Inspiron B120.  The wireless did not work - so I looked through the forums and found this thread.  I also have the Broadcom BCM4318 airborne card.  I downloaded this link and installed - rebooted and viola - I am using wireless now on this computer that seems to have a lot more life now!

Second - BigWings - have you tried this?  It took only 5 minutes to do this!

Good Luck,
Leroy

---

### Post by MarblePanther on 2009-02-02
> **leroy1086 said:**
> First - thank you for this link.  I am a brand new linux user.  I bought the Ubuntu 8.04 from Best Buy - they said they did not have it in stock, but I made them do an inventory search and they had two copies.  They were located with the foreign language courses! lol!  

I installed it on a Dell Inspiron B120.  The wireless did not work - so I looked through the forums and found this thread.  I also have the Broadcom BCM4318 airborne card.  I downloaded this link and installed - rebooted and viola - I am using wireless now on this computer that seems to have a lot more life now!

Second - BigWings - have you tried this?  It took only 5 minutes to do this!

Good Luck,
Leroy

Eek, i hope you didn't pay more than $5!

You know Ubuntu is free right?  You can download the .iso from [www.ubuntu.com](www.ubuntu.com) and burn it to a cd.

---

### Post by leroy1086 on 2009-02-02
Yes - I know it is free - but I splurged and spent the 20 bucks to get the rest of the free stuff too!  I am Ok with it since my time was saved.  I also believe in profit for people who organize everything for me.

---

### Post by MarblePanther on 2009-02-02
Ok, that's good.

I was just worried that Best Buy mightve been taking advantage of people. (Well, more than they usually do ;) )

---

### Post by leroy1086 on 2009-02-02
No - it is all good - I am able to get right to work as open office - firefox - etc is all installed at one time.  I just started and am able to open word docs and pdf docs without any problems.

I do have a question - I only have 512 mb ram - should I increase that?

Thanks,
Leroy loving linux thusfar!

---

### Post by _BigWings_ on 2009-02-03
guys, lets keep on topic :)

I haven't tried the other method yet. I don't want to be half way through one method and then try another one because it might screw things up. If what i'm doing right now will not work out then i'll go to the next thing. That said, i'm still having troubles with sams approach. So Sam, if you are around, care to clarify?

---

### Post by _BigWings_ on 2009-02-03
Anyone?

---

### Post by Ayuthia on 2009-02-03
> **_BigWings_ said:**
> Anyone?

You look like you are stuck at step 5.  The problem is that cd does not work in sudo.  Because of this, the script was unable to change to the Desktop.

Try the following:
```
cd ~/Desktop
sudo ndiswrapper -i bcmwl5a.inf
sudo ndiswrapper -l
sudo depmod -a
sudo modprobe ndiswrapper
sudo cp /etc/network/interfaces /etc/network/interfaces.orig
echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
sudo ndiswrapper -m
echo 'ndiswrapper' | sudo tee -a /etc/modules
echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant
```

Or else you can edit the file to remove the sudo in front of "sudo cd ~/Desktop".

---

### Post by _BigWings_ on 2009-02-03
thanks for the reply Ayuthia. I changed the script and it seems to be going though now.

step 5)

```
courtney@courtney-laptop:~$ '/home/courtney/Desktop/BCM4318 Ubuntu Intrepid/step5.sh' 
[sudo] password for courtney: 
installing bcmwl5a ...
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
bcmwl5a : driver installed
	device (14E4:4318) present (alternate driver: ssb)
auto lo
iface lo inet loopback

module configuration already contains alias directive

ndiswrapper
ENABLED=0

```

and step 6)
```
courtney@courtney-laptop:~$ cd /etc/init.d/
courtney@courtney-laptop:/etc/init.d$ sudo update-rc.d wifi.sh defaults
update-rc.d: warning: /etc/init.d/wifi.sh missing LSB style header
 Adding system startup for /etc/init.d/wifi.sh ...
   /etc/rc0.d/K20wifi.sh -> ../init.d/wifi.sh
   /etc/rc1.d/K20wifi.sh -> ../init.d/wifi.sh
   /etc/rc6.d/K20wifi.sh -> ../init.d/wifi.sh
   /etc/rc2.d/S20wifi.sh -> ../init.d/wifi.sh
   /etc/rc3.d/S20wifi.sh -> ../init.d/wifi.sh
   /etc/rc4.d/S20wifi.sh -> ../init.d/wifi.sh
   /etc/rc5.d/S20wifi.sh -> ../init.d/wifi.sh
courtney@courtney-laptop:/etc/init.d$ sudo chmod +x wifi.sh
courtney@courtney-laptop:/etc/init.d$ 

```

step 7)
I am not entirely sure what to do here. Which program do I use and what do I enter? Can't i just get a list of available networks an choose one and then enter a password etc?

---

### Post by Ayuthia on 2009-02-04
> **_BigWings_ said:**
> thanks for the reply Ayuthia. I changed the script and it seems to be going though now.

step 5)

```
courtney@courtney-laptop:~$ '/home/courtney/Desktop/BCM4318 Ubuntu Intrepid/step5.sh' 
[sudo] password for courtney: 
installing bcmwl5a ...
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
bcmwl5a : driver installed
	device (14E4:4318) present (alternate driver: ssb)
auto lo
iface lo inet loopback

module configuration already contains alias directive

ndiswrapper
ENABLED=0

```

and step 6)
```
courtney@courtney-laptop:~$ cd /etc/init.d/
courtney@courtney-laptop:/etc/init.d$ sudo update-rc.d wifi.sh defaults
update-rc.d: warning: /etc/init.d/wifi.sh missing LSB style header
 Adding system startup for /etc/init.d/wifi.sh ...
   /etc/rc0.d/K20wifi.sh -> ../init.d/wifi.sh
   /etc/rc1.d/K20wifi.sh -> ../init.d/wifi.sh
   /etc/rc6.d/K20wifi.sh -> ../init.d/wifi.sh
   /etc/rc2.d/S20wifi.sh -> ../init.d/wifi.sh
   /etc/rc3.d/S20wifi.sh -> ../init.d/wifi.sh
   /etc/rc4.d/S20wifi.sh -> ../init.d/wifi.sh
   /etc/rc5.d/S20wifi.sh -> ../init.d/wifi.sh
courtney@courtney-laptop:/etc/init.d$ sudo chmod +x wifi.sh
courtney@courtney-laptop:/etc/init.d$ 

```

step 7)
I am not entirely sure what to do here. Which program do I use and what do I enter? Can't i just get a list of available networks an choose one and then enter a password etc?

That should be all you have to do.  If you can't see any, please post the results of:
```
lshw -C network
sudo iwlist scan
dmesg|grep ndis
```
The first command will help us see what your wireless card is trying to use for a driver, the second will try to scan for sites, and the third will check to see if the system had any issues with loading ndiswrapper.

---

### Post by _BigWings_ on 2009-02-04
Well look a this. At first when i restarted I didn't see a wireless light and didn't see any wireless networks but it seems that after typing the first command that you suggested: "lshw -C network" the light came on an i can connect to wireless. 
If you guys can read this post then it is because wireless works because i unplugged my ethernet.

Thanks a lot guys! I have been tinkering with this thing for ages! I think it works now because of the bcmwl5a driver instead of the bcmwl5 driver.

---

