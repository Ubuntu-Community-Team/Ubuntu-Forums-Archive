---
title: "wireless still not working ..help!"
date: 2011-04-04
forum: Networking &amp; Wireless
---

### Post by jojomini on 2011-04-04
hey everybody

I am traveling with my dell 10-1018 and can not access wifi after update anymore.

tried to get help by a shop but they messed it up.(no wired, no wirelss worked anymore- they got back to wired only..)

i am a newbie to Linux and cant get the wireless working anymore... need urgent help as I am traveling and only find wireless connections and rarely wired...

here my infos please someone help..

                     p { margin-bottom: 0.08in; }  **Ubuntu 10.04.2 LTS**
 

 

 **shanghai@mini:~$ ifconfig **
 eth0      Link encap:Ethernet  HWaddr 5c:26:0a:28:f3:51   
           UP BROADCAST MULTICAST  MTU:1500  Metric:1 
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
           Interrupt:28 Base address:0xe000  
  
 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0 
           inet6 addr: ::1/128 Scope:Host 
           UP LOOPBACK RUNNING  MTU:16436  Metric:1 
           RX packets:50 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:50 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:0  
           RX bytes:3412 (3.4 KB)  TX bytes:3412 (3.4 KB)
 

 **shanghai@mini:~$ iwconfig **
 lo        no wireless extensions. 
  
 eth0      no wireless extensions. 
 

 **shanghai@mini:~$ sudo lshw -C network** 
 [sudo] password for shanghai:  
   *-network                
        description: Ethernet interface 
        product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller 
        vendor: Realtek Semiconductor Co., Ltd. 
        physical id: 0 
        bus info: pci@0000:05:00.0 
        logical name: eth0 
        version: 05 
        serial: 5c:26:0a:28:f3:51 
        size: 10MB/s 
        capacity: 100MB/s 
        width: 64 bits 
        clock: 33MHz 
        capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
        configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s 
        resources: irq:28 ioport:2000(size=256) memory:f0f2c000-f0f2cfff(prefetchable) memory:f0f18000-f0f1bfff(prefetchable) 
   *-network UNCLAIMED 
        description: Network controller 
        product: Realtek Semiconductor Co., Ltd. 
        vendor: Realtek Semiconductor Co., Ltd. 
        physical id: 0 
        bus info: pci@0000:07:00.0 
        version: 01 
        width: 64 bits 
        clock: 33MHz 
        capabilities: pm msi pciexpress bus_master cap_list 
        configuration: latency=0 
        resources: ioport:3000(size=256) memory:f0100000-f0103fff
 

 

 **hardware drivers:**
  Linux driver for Realtek RTL819x wifi cards
 “driver is activated but currently not in use”




 **no windows driver installed**
 

thats all I got till now. please let me know what info u need.

best 

Jo

---

### Post by matt_symes on 2011-04-04
Hi

```
*-network UNCLAIMED 
description: Network controller 
product: Realtek Semiconductor Co., Ltd. 
vendor: Realtek Semiconductor Co., Ltd. 
physical id: 0 
bus info: pci@0000:07:00.0 
version: 01 
width: 64 bits 
clock: 33MHz 
capabilities: pm msi pciexpress bus_master cap_list 
configuration: latency=0 
resources: ioport:3000(size=256) memory:f0100000-f0103fff
```

This is your problem. '*-network UNCLAIMED' means that Ubuntu can detect your wireless card but has not loaded a driver for it. 

This can happen for a number of reasons. The wrong driver is loaded and needs to be blacklisted or an incorrect driver is installed etc.

```
Linux driver for Realtek RTL819x wifi cards
&#8220;driver is activated but currently not in use&#8221;
```

Wherever you got that piece of information would tend to back that up.

Open a terminal and type (Case sensitive)

```
lspci -nnk | grep -A3 Network
``` 

Please post between post tags to make it easier to read. To do this copy and paste the text form the terminal into your reply post. Highlight the text in the post and hit the # button just above where you are typing.

This will tell us more about the card. I will not be able to look at this until tomorrow though so if anybody else fancies taking over, please be my guest.

Kind regards.

---

### Post by Funklink on 2011-04-04
I believe you installed the wrong drivers or haven't installed the needed drivers period. Try this:

```
 lspci -nnk | grep -A3 Network
```


Also, see this SOLVED thread with some of the same issues, it might help:

[http://ubuntuforums.org/showthread.php?t=1721524](http://ubuntuforums.org/showthread.php?t=1721524)

---

### Post by jojomini on 2011-04-05
he matt, 
thanks for helping here what i got 

#
[B]shanghai@mini:~$ lspci -nnk | grep -A3 Network
07:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8176] (rev 01)
    Kernel modules: r8192ce_pci[/B]

not sure if I posted it right the right way

  Regards Jo



> **matt_symes said:**
> Hi

```
*-network UNCLAIMED 
description: Network controller 
product: Realtek Semiconductor Co., Ltd. 
vendor: Realtek Semiconductor Co., Ltd. 
physical id: 0 
bus info: pci@0000:07:00.0 
version: 01 
width: 64 bits 
clock: 33MHz 
capabilities: pm msi pciexpress bus_master cap_list 
configuration: latency=0 
resources: ioport:3000(size=256) memory:f0100000-f0103fff
```This is your problem. '*-network UNCLAIMED' means that Ubuntu can detect your wireless card but has not loaded a driver for it. 

This can happen for a number of reasons. The wrong driver is loaded and needs to be blacklisted or an incorrect driver is installed etc.

```
Linux driver for Realtek RTL819x wifi cards
“driver is activated but currently not in use”
```Wherever you got that piece of information would tend to back that up.

Open a terminal and type (Case sensitive)

```
lspci -nnk | grep -A3 Network
```Please post between post tags to make it easier to read. To do this copy and paste the text form the terminal into your reply post. Highlight the text in the post and hit the # button just above where you are typing.

This will tell us more about the card. I will not be able to look at this until tomorrow though so if anybody else fancies taking over, please be my guest.

Kind regards.

---

### Post by jojomini on 2011-04-05
hey Funklink

I looked at the SOLVED you also linked..

As I do not understand it 100% I dont want to mess up by trying. Hope you guys can still help me.

I am still traveling and looking for wired internetcafes to do what you guys suggest!


Best Jo

---

### Post by matt_symes on 2011-04-05
Hi

After a bit of research i believe you need to install a different driver for your chipset than the one you are using.

The driver you want is RTL8192CE-VA4 and is available here.

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#2782](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#2782)

Kind regards

---

### Post by jojomini on 2011-04-08
> **matt_symes said:**
> Hi

After a bit of research i believe you need to install a different driver for your chipset than the one you are using.

The driver you want is RTL8192CE-VA4 and is available here.

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#2782](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#2782)

Kind regards


hey Matt I downloaded and tried to install as described on:
[http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/64958-how-install-software-linux.html](http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/64958-how-install-software-linux.html) 

here what I did


#
root@mini:/home/shanghai/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011#  make install

outcome:

make -C /lib/modules/2.6.32-30-generic/build M=/home/shanghai/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-30-generic'
  CC [M]  /home/shanghai/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/base.o
In file included from /home/shanghai/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/base.c:31:
/home/shanghai/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/wifi.h: In function ‘rtl_find_sta’:
/home/shanghai/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/wifi.h:1967: warning: unused variable ‘mac’
In file included from /home/shanghai/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/base.c:33:
/home/shanghai/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/base.h: At top level:
/home/shanghai/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/base.h:139:  warning: ‘enum ieee80211_smps_mode’ declared inside parameter list
/home/shanghai/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/base.h:139:  warning: its scope is only this definition or declaration, which is  probably not what you want
/home/shanghai/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/base.c: In function ‘rtl_tx_agg_start’:
/home/shanghai/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/base.c:951: warning: unused variable ‘mac’
/home/shanghai/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/base.c: In function ‘rtl_tx_agg_stop’:
/home/shanghai/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/base.c:988: warning: unused variable ‘mac’
/home/shanghai/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/base.c: At top level:
/home/shanghai/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/base.c:1275:  warning: ‘enum ieee80211_smps_mode’ declared inside parameter list
/home/shanghai/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/base.c:1275:  error: parameter 2 (‘smps’) has incomplete type
/home/shanghai/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/base.c: In function ‘rtl_make_smps_action’:
/home/shanghai/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/base.c:1295:  error: ‘union <anonymous>’ has no member named ‘ht_smps’
/home/shanghai/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/base.c:1295:  error: ‘WLAN_HT_ACTION_SMPS’ undeclared (first use in this function)
/home/shanghai/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/base.c:1295:  error: (Each undeclared identifier is reported only once
/home/shanghai/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/base.c:1295: error: for each function it appears in.)
/home/shanghai/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/base.c:1297:  error: ‘IEEE80211_SMPS_AUTOMATIC’ undeclared (first use in this  function)
/home/shanghai/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/base.c:1298:  error: ‘IEEE80211_SMPS_NUM_MODES’ undeclared (first use in this  function)
/home/shanghai/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/base.c:1300:  error: ‘IEEE80211_SMPS_OFF’ undeclared (first use in this function)
/home/shanghai/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/base.c:1301:  error: ‘union <anonymous>’ has no member named ‘ht_smps’
/home/shanghai/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/base.c:1302:  error: ‘WLAN_HT_SMPS_CONTROL_DISABLED’ undeclared (first use in this  function)
/home/shanghai/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/base.c:1304:  error: ‘IEEE80211_SMPS_STATIC’ undeclared (first use in this function)
/home/shanghai/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/base.c:1305:  error: ‘union <anonymous>’ has no member named ‘ht_smps’
/home/shanghai/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/base.c:1306:  error: ‘WLAN_HT_SMPS_CONTROL_STATIC’ undeclared (first use in this  function)
/home/shanghai/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/base.c:1308:  error: ‘IEEE80211_SMPS_DYNAMIC’ undeclared (first use in this function)
/home/shanghai/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/base.c:1309:  error: ‘union <anonymous>’ has no member named ‘ht_smps’
/home/shanghai/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/base.c:1310:  error: ‘WLAN_HT_SMPS_CONTROL_DYNAMIC’ undeclared (first use in this  function)
/home/shanghai/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/base.c: At top level:
/home/shanghai/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/base.c:1319:  warning: ‘enum ieee80211_smps_mode’ declared inside parameter list
/home/shanghai/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/base.c:1319:  error: parameter 3 (‘smps’) has incomplete type
/home/shanghai/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/base.c: In function ‘rtl_send_smps_action’:
/home/shanghai/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/base.c:1347:  error: type of formal parameter 2 is incomplete
make[2]: *** [/home/shanghai/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/base.o] Error 1
make[1]: *** [_module_/home/shanghai/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-30-generic'
make: *** [all] Error 2
root@mini:/home/shanghai/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011# 




can you help me I am lost .. :(
I even tried to add load the windows driver and it did not work. any ideas?

Jo

---

### Post by Cortbssguitar on 2011-04-08
I also have a 10inch Dell Inspiron mini 1018! :D
It's realy easy to install the driver for wifi. Simply copy these commands into the terminal:

sudo -E make clean modules 
 sudo make install 
 sudo depmod -a
 blacklist r8169
 sudo update-initramfs -u


sudo add-apt-repository ppa:lexical/hwe-wireless
sudo apt-get update
sudo apt-get install rtl8192ce-dkms


Keep the PPA in the softwaresources. Then you have not to reinstall it! ;)

Have fun!

Sincerely,
 Mark

---

### Post by jojomini on 2011-04-08
> **Cortbssguitar said:**
> I also have a 10inch Dell Inspiron mini 1018! :D
It's realy easy to install the driver for wifi. Simply copy these commands into the terminal:

sudo -E make clean modules 
 sudo make install 
 sudo depmod -a
 blacklist r8169
 sudo update-initramfs -u


sudo add-apt-repository ppa:lexical/hwe-wireless
sudo apt-get update
sudo apt-get install rtl8192ce-dkms


Keep the PPA in the softwaresources. Then you have not to reinstall it! ;)

Have fun!

Sincerely,
 Mark

hey Mark,
thanks for the reply!

still something wrong here you know what?
best Regards
Jo

here what I did:

#
**shanghai@mini:~$ sudo -E make clean modules **
make: *** No rule to make target `clean'.  Stop.

**shanghai@mini:~$ sudo su**

**root@mini:/home/shanghai# sudo -E make clean modules **
make: *** No rule to make target `clean'.  Stop.

**root@mini:/home/shanghai# -E make clean modules **
-E: command not found

**root@mini:/home/shanghai# -E make clean modules **
-E: command not found

**root@mini:/home/shanghai# make install **
make: *** No rule to make target `install'.  Stop.

**root@mini:/home/shanghai# depmod -a**

**root@mini:/home/shanghai# blacklist r8169**
blacklist: command not found

**root@mini:/home/shanghai# update-initramfs -u**
update-initramfs: Generating /boot/initrd.img-2.6.32-30-generic

root@mini:/home/shanghai# 
**root@mini:/home/shanghai# add-apt-repository ppa:lexical/hwe-wireless**
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 88B3CE2CE934D5F973CC26C80C5CE27EA088FF1E
gpg: requesting key A088FF1E from hkp server keyserver.ubuntu.com
gpg: key A088FF1E: "Launchpad Keng-Yu's PAA" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1

**root@mini:/home/shanghai# apt-get update**
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg [316B]                                                                     
Get:2 [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg [198B]                                                                 
Ign [http://ppa.launchpad.net/lexical/hwe-wireless/ubuntu/](http://ppa.launchpad.net/lexical/hwe-wireless/ubuntu/) lucid/main Translation-en_US                                      
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release.gpg [189B]                                                                    
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US                                                    
Get:4 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release [57.3kB]                                                                       
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg [198B]                                                          
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US                                                          
Get:6 [http://archive.canonical.com](http://archive.canonical.com) lucid Release [8,215B]                                                                   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US                                          
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US                                                    
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US                                                
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US                                          
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US                                                      
Get:7 [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages [12.5kB]                                                          
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US                                                    
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US                                            
Ign [http://dl.google.com/linux/earth/deb/](http://dl.google.com/linux/earth/deb/) stable/main Translation-en_US                                                     
Get:8 [http://dl.google.com](http://dl.google.com) stable Release.gpg                                                                               
Get:9 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages [655B]                                                                   
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release.gpg [198B]                                                           
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release [44.7kB]                                                           
Get:12 [http://dl.google.com](http://dl.google.com) stable Release [1,338B]                                                                         
Get:13 [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources [6,040B]                                                          
Err [http://dl.google.com](http://dl.google.com) stable Release                                                                                     
  
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US                                                  
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US                                            
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US                                              
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages [14B]                                            
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US                                            
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages [173kB]                                                      
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release [57.2kB]                                                                     
Get:17 [http://e8ce82f219d3feb9799a94d83349f8cfdfa00b50.inspiron.dell.archive.canonical.com](http://e8ce82f219d3feb9799a94d83349f8cfdfa00b50.inspiron.dell.archive.canonical.com) lucid-dell Release.gpg [280B]    
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release [44.7kB]                                                             
Ign [http://e8ce82f219d3feb9799a94d83349f8cfdfa00b50.inspiron.dell.archive.canonical.com/updates/](http://e8ce82f219d3feb9799a94d83349f8cfdfa00b50.inspiron.dell.archive.canonical.com/updates/) lucid-dell/public Translation-en_US
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages [4,559B]                                               
Get:20 [http://e8ce82f219d3feb9799a94d83349f8cfdfa00b50.inspiron.dell.archive.canonical.com](http://e8ce82f219d3feb9799a94d83349f8cfdfa00b50.inspiron.dell.archive.canonical.com) lucid-dell Release [4,171B]      
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages [66.7kB]                                                 
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Packages [1,386kB]                                                              
Get:23 [http://e8ce82f219d3feb9799a94d83349f8cfdfa00b50.inspiron.dell.archive.canonical.com](http://e8ce82f219d3feb9799a94d83349f8cfdfa00b50.inspiron.dell.archive.canonical.com) lucid-dell/public Packages [14B] 
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Packages [6,208B]                                                         
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Sources [659kB]                                                                 
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Sources [3,775B]                                                          
Get:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Packages [5,448kB]                                                          
Get:28 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Sources [3,165kB]                                                           
Get:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Packages [180kB]                                                          
Get:30 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Sources [119kB]                                                           
Get:31 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Packages [468kB]                                                        
Get:32 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Packages [3,240B]                                                 
Get:33 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Sources [184kB]                                                         
Get:34 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Sources [1,443B]                                                  
Get:35 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/universe Packages [195kB]                                                    
Get:36 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/universe Sources [72.2kB]                                                    
Get:37 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/multiverse Packages [10.5kB]                                                 
Get:38 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/multiverse Sources [5,066B]                                                  
Fetched 12.4MB in 1min 54s (108kB/s)                                                                                        
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://dl.google.com](http://dl.google.com) stable Release: The following signatures were invalid: NODATA 1 NODATA 2

W: Failed to fetch [http://dl.google.com/linux/earth/deb/dists/stable/Release](http://dl.google.com/linux/earth/deb/dists/stable/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.

**root@mini:/home/shanghai# apt-get install rtl8192ce-dkms**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
rtl8192ce-dkms is already the newest version.
The following packages were automatically installed and are no longer required:
  libdmraid1.0.0.rc16 python-pyicu libdebian-installer4 user-setup cryptsetup libecryptfs0 reiserfsprogs rdate
  localechooser-data ecryptfs-utils libdebconfclient0 dmraid keyutils
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
root@mini:/home/shanghai#

---

### Post by matt_symes on 2011-04-08
Hi

If there is a ppa avaliable and the drivers works then pick that ;)

In case you are interested

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false)

Kind regards

---

