---
title: "Wireless Issues with Ubuntu 10.04"
date: 2012-09-25
forum: Networking &amp; Wireless
---

### Post by dkb12 on 2012-09-25
I downloaded the Broadcom Driver and activated it. It will detect my wireless but wont connect. Im running Ubuntu 10.04 on Compaq Presario 2100.

---

### Post by josephmills on 2012-09-25
can you please connect the computer with a cat5 (ethernet cable) and run these commands(one by one) and paste the output here. 

```

lspci -vnn | grep 14e4

```
```

apt-cache policy b43-fwcutter broadcom-sta-* firmware-b43-*

```
```

rfkill list all 

```

```

lsmod | grep b43  && lsmod | grep wl

```


Thanks

---

### Post by dkb12 on 2012-09-25
> **josephmills said:**
> can you please connect the computer with a cat5 (ethernet cable) and run these commands(one by one) and paste the output here. 

```

lspci -vnn | grep 14e4

``````

apt-cache policy b43-fwcutter broadcom-sta-* firmware-b43-*

``````

rfkill list all 

``````

lsmod | grep b43  && lsmod | grep wl

```
Thanks

heres what I got.. thanks 

donna@donna-laptop:~$ lspci -vnn | grep 14e4
00:09.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 02)

onna@donna-laptop:~$ apt-cache policy b43-fwcutter broadcom-sta-* firmware-b43-*
b43-fwcutter:
  Installed: 1:012-1build1
  Candidate: 1:012-1build1
  Version table:
 *** 1:012-1build1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Packages
        100 /var/lib/dpkg/status
W: Unable to locate package broadcom-sta-*
W: Unable to locate package firmware-b43-*

onna@donna-laptop:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

donna@donna-laptop:~$ lsmod | grep b43  && lsmod | grep wl
b43legacy             115152  0 
mac80211              205434  1 b43legacy
cfg80211              126528  2 b43legacy,mac80211
led_class               2864  1 b43legacy
ssb                    38934  1 b43legacy

---

### Post by josephmills on 2012-09-25
Ok last two questions 
```

uname -r 

```

and then 

```

awk '/deb/' /etc/apt/sources.list 

```

Thanks

---

### Post by dkb12 on 2012-09-25
ere> **josephmills said:**
> Ok last two questions 
```

uname -r 

```and then 

```

awk '/deb/' /etc/apt/sources.list 

```Thanks

here ya go

donna@donna-laptop:~$ uname -r
2.6.32-43-generic

donna@donna-laptop:~$ awk '/deb/' /etc/apt/sources.list
#deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse

---

### Post by josephmills on 2012-09-25
Thanks again and I think that I see the troubles that you are running into. You have to Enable Backports. 

from your paste's 

```

# deb http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu lucid partner

```

The # means that the [Repository ](https://help.ubuntu.com/community/Repositories/Ubuntu) Is not enabled and must be. 

This is a simple task 

open Ubuntu software Center  

and go to 

Edit-->Software Sources(attachment 1)

Then make sure that You are have 3rd party clicked Then go to the Other Software TAB and make sure that they are all clicked also. 
(attachments 2 & 3 )
Then Close Software Center and Open a terminal
time to update the software that is coming from the new repo's 
```
sudo apt-get update
```

Then Install the firmware for your wireless card 

```
 sudo apt-get install firmware-b43legacy-installer
```

Then restart your Wireless card 

If you have a switch you can use that If not you can put this into the terminal 
too shut down and remove the mod (driver)
```
sudo rmmod b43legacy
```

Then to start again 
```
sudo modprobe b43legacy
```

Or you can just restart the computer the choice is yours :)

---

### Post by dkb12 on 2012-09-25
> **josephmills said:**
> Thanks again and I think that I see the troubles that you are running into. You have to Enable Backports. 

from your paste's 

```

# deb http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu lucid partner

```The # means that the [Repository ]("https://help.ubuntu.com/community/Repositories/Ubuntu") Is not enabled and must be. 

This is a simple task 

open Ubuntu software Center  

and go to 

Edit-->Software Sources(attachment 1)

Then make sure that You are have 3rd party clicked Then go to the Other Software TAB and make sure that they are all clicked also. 
(attachments 2 & 3 )
Then Close Software Center and Open a terminal
time to update the software that is coming from the new repo's 
```
sudo apt-get update
```Then Install the firmware for your wireless card 

```
 sudo apt-get install firmware-b43legacy-installer
```Then restart your Wireless card 

If you have a switch you can use that If not you can put this into the terminal 
too shut down and remove the mod (driver)
```
sudo rmmod b43legacy
```Then to start again 
```
sudo modprobe b43legacy
```Or you can just restart the computer the choice is yours :)


I didnt see any third party to check and I went ahead and put the update in the terminal and this is what I got. 
onna@donna-laptop:~$ sudo apt-get update
[sudo] password for donna: 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg [198B]
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg [198B]   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release                       
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release [58.3kB]              
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release [57.3kB]               
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                        
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages [646kB]
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages [451kB]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages [2,867B]   
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources [130kB]           
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources [1,267B]    
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages [135kB]     
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources [42.0kB]     
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages [5,372B]  
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources [2,321B]   
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages [4,630B] 
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources [229kB]         
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources [2,196B]  
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages [278kB]    
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources [103kB]     
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages [11.5kB] 
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources [5,821B]  
Fetched 2,166kB in 20s (105kB/s)                                               
Reading package lists... Done

and this for the b43 legacy 
donna@donna-laptop:~$ sudo apt-get install firmware-b43legacy-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package firmware-b43legacy-installer

I didnt put in the other commands. I didnt know if I needed to or see what you said. thanks

---

### Post by josephmills on 2012-09-25
Huh it is still not geting packages from backport try this 
open terminal enter in 
[COLOR="Red"]TYPE CAREFUL AND DOUBLE CHECK 
[/COLOR]```
 sudo sed -i 's|\#\ deb\ http|deb http|g'  /etc/apt/sources.list
```

then 
```
sudo apt-get update 
```

then 
```
sudo apt-get install firmware-b43legacy-installer
```

see if it sees installs If not open terminal and enter in 

```
apt-cache search b43
```

and post that back here 
Thanks

---

### Post by dkb12 on 2012-09-25
I dont think this work either. I hope we can figure it out.

donna@donna-laptop:~$ sudo sed -i 's|\#\ deb\ http|deb http|g'  /etc/apt/sources.list

donna@donna-laptop:~$ sudo apt-get update
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg                      
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg                   
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                   
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg [198B]  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release                
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports Release.gpg         
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release 
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release [58.3kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages                    
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports Release               
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages [646kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages [4,630B]  
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources [229kB]          
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources [2,196B]   
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages [278kB]     
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources [103kB]      
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages [11.5kB]  
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources [5,821B]  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/main Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/restricted Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/universe Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/multiverse Packages           
Fetched 1,338kB in 28s (47.4kB/s)                                              
Reading package lists... Done
donna@donna-laptop:~$ sudo apt-get install firmware-b43legacy-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package firmware-b43legacy-installer

---

### Post by dkb12 on 2012-09-25
heres the other command 

donna@donna-laptop:~$ apt-cache search b43
b43-fwcutter - Utility for extracting Broadcom 43xx firmware
donna@donna-laptop:~$

---

