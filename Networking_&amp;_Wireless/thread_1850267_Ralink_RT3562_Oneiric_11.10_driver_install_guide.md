---
title: "Ralink RT3562 Oneiric 11.10 driver install guide"
date: 2011-09-26
forum: Networking &amp; Wireless
---

### Post by jackoneill87 on 2011-09-26
For anybody looking to install drivers for Ralink Device 3062, I've finally managed to get it working so I thought I'd share.
[Link to source updated; thanks Algorith]

1. Check your wireless controller hardware

> lspci | grep NetworkYou should get the following output
> Network controller: Ralink corp. Device 3062If so, you will need to install Ralink driver 3562. 


2. Download the driver source from the Ralink website
[http://www.ralinktech.com/en/04_support/support.php](http://www.ralinktech.com/en/04_support/support.php)


3. Extract the folder (DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217) to your home directory.


4. Open DPO_RT.../os/linux/config.mk


5. Change line 12 to read HAS_WPA_SUPPLICANT=y
    Change line 15 to read HAS_NATIVE_WPA_SUPPLICANT=y


6. Open a terminal
> cd DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_201012177.
> sudo make8. Install the driver. (Thanks Algorith :p)
> sudo make install9. Next you need to blacklist the conflicting wireless drivers
> sudo gedit /etc/modprobe.d/blacklist.confAdd the following lines
#Wireless drivers conflicting with rt3562sta
blacklist rt2800pci
blacklist rt2x00pci


10. Tell linux to load the correct module on boot
> sudo gedit /etc/modulesAppend the following line
rt3562sta


11. Update the changes
> sudo update-initramfs -u12. Restart your system. You should see a list of available networks in the network manager next time it boots.

If anyone has any problems with this please let me know and I'll try to help!

---

### Post by uconnjl on 2011-11-05
I'm installing a Zonenet ZEW1690 card on 11.10.  It is recognized as RaLink 3062 and uses the 3625 drivers.   Your instructions worked for compiling the driver but not for installing.  

Apparently I also needed to update the firmware which is available on the RaLink website on the same page as the drivers.  I used the instructions in this post to get it to work.

[To update firmware]("http://ubuntuforums.org/showthread.php?t=1608095&highlight=zew1690&page=9")

[To compile and install drivers]("http://ubuntuforums.org/showthread.php?t=1608095&highlight=zew1690")

---

### Post by zenon222 on 2011-12-03
I hacked a similar process together for my HP ProBook 4430s based on the RT3592.

Attached is the code referenced above just in case the files are AWOL from the server.  

The above mentioned code changes need to be applied.

---

### Post by Algorith on 2012-03-04
For me, these instructions needed some modification:

In particular, the link from the OP in step 2 has gone away - the new link is
[http://www.ralinktech.com/en/04_support/support.php](http://www.ralinktech.com/en/04_support/support.php)

Second, in step 8, rather than a simple cp, I needed to do 
> sudo make install
(as per [http://ubuntuforums.org/showthread.php?t=1608095](http://ubuntuforums.org/showthread.php?t=1608095) )

--------
BTW, a WPA supplicant is a daemon that implements key negotiation with a WPA authenticator

---

### Post by JackOConnor on 2012-03-06
I am able to do most of this but am having a problem at step 9. I also had to change step 8 to:
```
 sudo make install
```But anyway at step nine when I enter
```
sudo gedit /etc/modprobe.d/blacklist.conf
```It brings up the file that has to be changed but the terminal says:
```


 (gedit:2092): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.VGSLAW': No such file or directory 

(gedit:2092): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory
 
```I have no idea why this is happening (no surprise, I'm new to linux) but I think that it's the reason that this whole method won't work for me.

I am running ubuntu 11.10 and I'm certain I follwed all of the prior steps correctly, I would greatly appreciate some expert help right now!!!

---

### Post by jackoneill87 on 2012-03-07
> **JackOConnor said:**
> I am able to do most of this but am having a problem at step 9. I also had to change step 8 to:
```
 sudo make install
```But anyway at step nine when I enter
```
sudo gedit /etc/modprobe.d/blacklist.conf
```It brings up the file that has to be changed but the terminal says:
```


 (gedit:2092): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.VGSLAW': No such file or directory 

(gedit:2092): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory
 
```

I'm not at a computer with Linux at the moment so I can't check this out in depth, but it seems like gedit is unable to create a temporary file because the folder it normally creates them in doesn't exist. That might be a bit of a problem in itself, but you might be able to root around the settings in gedit to fix it.

As a work-around for the driver install you can add the lines directly to the file, instead of step 9, backup your file (this is important, I've learned it the hard way) and then try
```
sudo echo 'blacklist rt2800pci' >> /etc/modprobe.d/blacklist.conf
sudo echo 'blacklist rt3562sta' >> /etc/modprobe.d/blacklist.conf
```this will append the lines to the end of the file directly. you can check to make sure it worked by viewing the last few lines of the file from the console
```
 tail /etc/modprobe.d/blacklist.conf 
```Similarly, in step 10 try 
```
sudo echo rt3562sta >> /etc/modules
```Again, check to make sure it's worked using the tail command. If that doesn't work, once you have followed all the steps, please post the results of
```
lsmod | grep rt3562
``` and I'll see if I can help you further.

---

### Post by JackOConnor on 2012-03-07
No its ok I solved it. Didn't fully understand it but this tutorial worked for me.[http://www.squidoo.com/how-to-install-ralink-3062-network-card-on-linux:grin:]("http://www.squidoo.com/how-to-install-ralink-3062-network-card-on-linux")
Thanks anyway though!!!

---

### Post by andreika73 on 2012-03-12
Hi there!

It didn't work! I was using this driver 2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2.zip with all other Ubuntu versions and had no problems. (Here is my public link to the driver just in case: [http://ubuntuone.com/1x62PHTNJdVraviQx7sFmx](http://ubuntuone.com/1x62PHTNJdVraviQx7sFmx))

When trying to install it with Oneiric, I get this following error message: root@ubuntu-HP:/tmp/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2# make
make -C tools
make[1]: Entering directory `/tmp/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/tmp/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/tools'
/tmp/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/tools/bin2h
cp -f os/linux/Makefile.6 /tmp/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/Makefile
make -C /lib/modules/3.2.0-18-generic/build SUBDIRS=/tmp/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-18-generic'
  CC [M]  /tmp/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../os/linux/rt_linux.o
/tmp/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../os/linux/rt_linux.c: In function &#8216;duplicate_pkt&#8217;:
/tmp/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../os/linux/rt_linux.c:550:3: warning: passing argument 1 of &#8216;memmove&#8217; makes pointer from integer without a cast [enabled by default]
/usr/src/linux-headers-3.2.0-18-generic/arch/x86/include/asm/string_64.h:58:7: note: expected &#8216;void *&#8217; but argument is of type &#8216;sk_buff_data_t&#8217;
/tmp/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../os/linux/rt_linux.c:552:3: warning: passing argument 1 of &#8216;memmove&#8217; makes pointer from integer without a cast [enabled by default]
/usr/src/linux-headers-3.2.0-18-generic/arch/x86/include/asm/string_64.h:58:7: note: expected &#8216;void *&#8217; but argument is of type &#8216;sk_buff_data_t&#8217;
/tmp/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../os/linux/rt_linux.c: In function &#8216;ClonePacket&#8217;:
/tmp/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../os/linux/rt_linux.c:654:23: warning: assignment makes integer from pointer without a cast [enabled by default]
/tmp/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../os/linux/rt_linux.c: In function &#8216;update_os_packet_info&#8217;:
/tmp/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../os/linux/rt_linux.c:676:15: warning: assignment makes integer from pointer without a cast [enabled by default]
/tmp/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../os/linux/rt_linux.c: In function &#8216;wlan_802_11_to_802_3_packet&#8217;:
/tmp/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../os/linux/rt_linux.c:697:15: warning: assignment makes integer from pointer without a cast [enabled by default]
/tmp/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../os/linux/rt_linux.c: In function &#8216;send_monitor_packets&#8217;:
/tmp/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../os/linux/rt_linux.c:957:9: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 3 has type &#8216;long unsigned int&#8217; [-Wformat]
/tmp/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../os/linux/rt_linux.c: At top level:
/tmp/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../os/linux/rt_linux.c:1646:10: error: unknown field &#8216;ndo_set_multicast_list&#8217; specified in initializer
make[2]: *** [/tmp/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../os/linux/rt_linux.o] Error 1
make[1]: *** [_module_/tmp/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-18-generic'
make: *** [LINUX] Error 2
root@ubuntu-HP:/tmp/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2# 


When installing using the changes you suggest, I don't get any error messages, but the driver doesn't seem to work, my Network Card doesn't detect any WI-FI.

Do you think you can help? ))

Thank you in advance, 

Andre

---

### Post by jackoneill87 on 2012-03-13
Hey, sorry to hear you're having trouble; I don't have access to my linux machine at the moment so I apologize if there's a mistake in any of the commands :)

You said that the make command seems to work fine when you use some of the changes suggested. Can you try the following?

1. Run the make command as you've been doing before (it might be worth while using sudo to make sure there are no permissions issues)If this runs without any ERROR messages, it's been successful, you might get 'warnings', but generally they're ok.

2. From root directory of your downloaded folder run
```
sudo make install
```

3. Check to see if the driver has been installed
```
ls /lib/modules/$(uname -r)/kernel/drivers/net | grep rt 
```

4. If you get a result along the lines of rt3562sta.ko then all's good so far so proceed to load the driver
```
sudo modprobe rt3562sta
```

5. Check to see if the module has loaded properly
```
lsmod | grep rt 
```

6. Make sure the wireless is enabled
```
sudo ifconfig ra0 up 
```

Any available wireless networks should now be showing up.

If it all seems to go well but the networks aren't showing up double check to make sure your wireless is physically switched on (I had this problem once and it took me hours to figure it out).

If it fails anywhere else along the way just let me know how far you got, and what error messages it's giving you.

p.s. it seems some people had to update firmware as well as installing a driver. Check the following thread
[http://ubuntuforums.org/showthread.php?t=1608095&highlight=zew1690&page=9](http://ubuntuforums.org/showthread.php?t=1608095&highlight=zew1690&page=9) (post #90)

---

### Post by Andrew F in Australia on 2012-04-20
> **jackoneill87 said:**
> 

If anyone has any problems with this please let me know and I'll try to help!

Worked perfectly for me, Jack on the Ralink 3592 chipset in a HP Probook4730s

[One minor change - installed as per your directions, if I disconnect or line drops out, I need to reboot to get it going again, but at least it works now.  Excellent and thanks for the clear advice.]

Instead, I put the following into the 'blacklist' file, copied from here.
[http://www.squidoo.com/how-to-install-ralink-3062-network-card-on-linux](http://www.squidoo.com/how-to-install-ralink-3062-network-card-on-linux)

```
sudo gedit /etc/modprobe.d/blacklist.conf 
(or kwrite, nano, etc...)

Once inside the blacklist.conf file you should append the following lines to the file

blacklist rt2800pci
blacklist rt2800lib
blacklist rt2800usb
blacklist rt2x00pci
blacklist rt2x00lib
blacklist rt2x00usb

```This allows the chipset to rediscover any broadcasting networks when disconnected, allows automatic reconnect.

Can't thank you enough for the clear advice.

Cheers.

AF

EDIT: Just upgraded to 12.04 pangolin and the network adapter wasn't recognised (again). Repeated these steps and it configured OK.

Thanks again Jack

---

### Post by Graham C Williams on 2012-07-03
All Fixed now: See post #14. Many thanks to the good people on this forum.

Good Day all.
[System: 11.10 64bit]
I've followed this guide and the related link ([http://www.squidoo.com/how-to-install-ralink-3062-network-card-on-linux](http://www.squidoo.com/how-to-install-ralink-3062-network-card-on-linux)).

In the initial tests I got these answers:
0d:01.0 Network controller: Ralink corp. Device 3062
0d:01.0 0280: 1814:3062

I downloaded the following:
DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217

make and install with updates as required:
sudo modprobe rt3562sta 
sudo gedit /etc/modprobe.d/blacklist.conf 
blacklist rt2800pci
blacklist rt2800lib
blacklist rt2800usb
blacklist rt2x00pci
blacklist rt2x00lib
blacklist rt2x00usb

After the install and a restart, the Wireless option is completely disappeared and an extra wired has appeared.
I ran these tests as, with the results shown.

:~$ ls /lib/modules/$(uname -r)/kernel/drivers/net | grep rt
virtio_net.ko

:~$ lsmod | grep rt
parport_pc             36962  0 
rt3562sta             986394  1 
parport                46562  3 parport_pc,ppdev,lp

What is virtio_net?
I still have wired connectivity but no sign of wireless.
Can you help? I get the feeling some fundamental mistake has been made!!
Graham.

---

### Post by Graham C Williams on 2012-07-03
In Addition.
I asked the question: iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

ra0       Ralink STA  
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

---

### Post by Graham C Williams on 2012-07-04
> As a work-around for the driver install you can add the lines directly to the file, instead of step 9, backup your file (this is important, I've learned it the hard way) and then try
Code:

sudo echo 'blacklist rt2800pci' >> /etc/modprobe.d/blacklist.conf
sudo echo 'blacklist rt3562sta' >> /etc/modprobe.d/blacklist.conf

this will append the lines to the end of the file directly

Is the second line refering to "rt3562sta" in the above extract incorrect?
I have removed it from my 'Blacklist' because I think it's what we want.

Asking The Question:
lsmod | grep rt3562
gives me
rt3562sta             986394  0 
I don't know what this means but it differs from the last time when I used the general form?

Still I have no referance to wireless, the wireless section being replaced by a second wired as attached.

Graham.

---

### Post by Graham C Williams on 2012-07-04
Fixed & Working; this forum is so good:
Following this link:[http://ubuntuforums.org/showthread.php?t=1806897](http://ubuntuforums.org/showthread.php?t=1806897)
It is similar to this, it's all working.
):P

Graham.

---

### Post by superpink99 on 2012-07-16
wohooooo, a big thanks man. i have been poking my head for this problem. i had a slightly different problem but the procedure was the same. 

oh yeah thanks a lot again.

---

### Post by jackoneill87 on 2012-07-18
> **Graham C Williams said:**
> Is the second line refering to "rt3562sta" in the above extract incorrect?
I have removed it from my 'Blacklist' because I think it's what we want.

Hi Graham, sorry I haven't been on in a while, but glad to hear you got it working. Yes, you're right that is a mistake, we don't want to blacklist the module we're trying to install!  what I should have written is this (thanks to everyone who pointed out the full list)


sudo echo "blacklist rt2800pci" >> /etc/modprobe.d/blacklist.conf 
sudo echo "blacklist rt2800pci" >> /etc/modprobe.d/blacklist.conf
sudo echo "blacklist rt2800usb" >> /etc/modprobe.d/blacklist.conf 
sudo echo "blacklist rt2x00pci" >> /etc/modprobe.d/blacklist.conf 
sudo echo "blacklist rt2x00lib" >> /etc/modprobe.d/blacklist.conf 
sudo echo "blacklist rt2x00usb" >> /etc/modprobe.d/blacklist.conf

---

### Post by alexmoon on 2012-10-05
[On Ubuntu 12.04]

Hi,

I followed the steps given on the first page, with the exception that I downloaded the RT3290 driver from [here]("http://www.ralinktech.com/en/04_support/support.php?sn=501"), and added further drivers to the blacklist as given on [the squidoo page]("http://www.squidoo.com/how-to-install-ralink-3062-network-card-on-linux") mentioned earlier. 

When I click on 'additional drivers' in Settings, it shows that rt3290sta is "activated and currently in use". However, while "Wireless Networks" is now showing up under the connections manager (it didn't before the driver was installed), no wireless networks appear (while they are clearly visible on a laptop sitting next to this one). 

I'm wondering if it may be related to the wireless toggle switch on my keyboard: I have a [Dreambook]("http://pioneercomputers.com.au/products/configure.asp?c1=3&c2=166&id=3399"), and the guy at the store mentioned that this may be an issue.

Any tips for what to try next? Thanks for any help you can offer!

---

### Post by jackoneill87 on 2012-10-08
Hi,

I'm not familiar with the dreambook, but it sounds like the driver's working fine, but your wireless capabilities are just switched off. As far as I know there's a setting to turn off wireless to maximize battery life. Poke around in the settings to see if you can find something to that effect.

If that's not the case, and it's not picking up wireless signals anywhere, it might be a more general software problem. Make sure you're using the latest version of the OS, available here
[ftp://service.pioneer.net.au/Manuals/Update.pdf](ftp://service.pioneer.net.au/Manuals/Update.pdf)
As the updates may fix whatever is causing it.

If this doesn't work, and it picks up some wireless signals, just not yours, it might be something to do with the encryption. Try setting your router up to broadcast with no password, and see if it fixes the problem. If it does, you might need to try to change the encryption settings on your wireless router.

Hope it helps!

---

### Post by alexmoon on 2012-10-08
Thank you so much! I just managed to sort it out and wireless is now working fine. I'm not sure exactly which step helped, but I did install some firmware in addition to the drivers listed here.

---

### Post by ucard on 2013-04-21
Best solution...works like a charm. Thanks a ton.

---

### Post by raudan on 2013-05-31
Hi everyone!
I'm new here ... and for the start I want to tell you that you are doing a very great job by sharing all the knowledge and informations ... Really! Thanks for this! :)

Ok, I have an HP 650 laptop, with an Intel Core i3-2328M processor with an Ubuntu 12.04 LTS OS which has an wireless device: Ralink 3290

And I did what jackoneill87 told in his first post ... and ... it is OK (the wireless is working fine - yeah! :) until Ubuntu updates itself

I think the Ubuntu its rewriting my wireless driver (actually removing for good the wireless device - like doing an disable or something because I don't have wireless at all, just the LAN network) so I don't have wireless at all.

So please help me with this: isn't something that I can do, so after those updates, tell Ubuntu to not do anything with the wireless device? I don't know, just not to reinstall it the wireless again and again!!
How to tell Ubuntu to not do anything with the wireless ...?

Thanks in advance! :)

---

### Post by wildmanne39 on 2013-05-31
Hi, the way you installed the driver it has to be removed and recompiled everytime you have an update to your kernel.
If you remove the driver completely then you can install it using these directions and you will not have to redo it everytime the kernel is updated.
[http://forum.ubuntuusers.de/topic/nach-update-kein-wlan-mehr-433/2/#post-5641297](http://forum.ubuntuusers.de/topic/nach-update-kein-wlan-mehr-433/2/#post-5641297)
The directions are in German but just copy and paste the commands if you want you can use google translate.
Thanks

---

