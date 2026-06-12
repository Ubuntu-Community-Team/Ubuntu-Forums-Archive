---
title: "Desktop 10.04 No wireless connections?  HP Pavilion  Broadcom AF1 ver2"
date: 2010-08-25
forum: Networking &amp; Wireless
---

### Post by Sxynerd on 2010-08-25
So I gave up on trying to figure out the wireless on the Studio Version...  Now I'm trying to figure it out on Desktop 10.04 and I'm meeting with the same issues.  Although this time, I have a cute little Icon in the upper right corner to try and manipulate.  But I am having no luck at all.   I can try and create my own Wireless connection through the drop down menu.  But it does not actually connect to anything.

Is there a walk-through for setting up wireless on these silly OS's?


Under the Icon the menu lists
Wireless Networks (Not click-able)
Disconnected  (Not click-able)
VPN Connections  (click-able)
Connect to Hidden Wireless Network  (click-able)
Create New Wireless Network...  (click-able)


Solved

HERE IS THE FIX:
> Step one, getting the wireless to work.
[http://ubuntuforums.org/showthread.php?t=1560567](http://ubuntuforums.org/showthread.php?t=1560567)

You need b43-fwcutter from here: [http://packages.ubuntu.com/maverick/b43-fwcutter](http://packages.ubuntu.com/maverick/b43-fwcutter)

From the website referenced, you need this: [http://downloads.openwrt.org/sources...0.10.5.tar.bz2](http://downloads.openwrt.org/sources...0.10.5.tar.bz2)




Did you also download the firmware file and transfer it on a USB drive? Where is it? On your desktop? Please open a terminal and do:
Code:
cd Desktop
Now, let's unpack the firmware file:
Code:
tar xjf broadcom-wl-4.150.10.5.tar.bz2

The tar command should result in a new folder called broadcom-wl-4.150.10.5, within which is a folder called driver. We need the firmware files in the driver folder, so let's change directories there:
Code:
cd broadcom-wl-4.150.10.5/driver

Now, we will use b43-fwcutter to cut out the firmware and place it in the file on your Ubuntu installation where the b43 wireless driver expects to find it:

Code:
sudo b43-fwcutter -w /lib/firmware/ wl_apsta_mimo.o

Now, a reboot should have your wireless working.

---

### Post by anonomo on 2010-08-25
hi no answers here!
just asking why you gave up on figuring out wireless in Studio 10.04?

because i've just installed it, and the cute little wireless icon in the corner is missing, as is the connections tab in network administration tool window.

was that your problem too or just me?

---

### Post by dineshs on 2010-08-25
deleted

---

### Post by dineshs on 2010-08-25
anonomo,
> because i've just installed it, and the cute little wireless icon in the corner is missing, as is the connections tab in network administration tool windowUbuntu Studio does not have Network-Manager installed
[http://ubuntuforums.org/showthread.php?t=1479788](http://ubuntuforums.org/showthread.php?t=1479788)
Sxynerd,
Kindly post  the results of the following terminal(applications-accessories-terminal)commands
```
sudo lshw -C network
```
```
iwconfig
```
so that experts in the forum can help

---

### Post by Sxynerd on 2010-08-25
> **dineshs said:**
> 
```
sudo lshw -C network
```

```
iwconfig
```

so that experts in the forum can help

[COLOR="Red"]michael@michael-desktop:~$ sudo lshw -c network
  *-network               
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 6
       bus info: pci@0000:01:06.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:18 memory:ef8fc000-ef8fdfff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:22:75:19:6d:51
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
michael@michael-desktop:~$ [/COLOR]



[COLOR="Red"]michael@michael-desktop:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
michael@michael-desktop:~$ [/COLOR]
Thank you...  I'm going nuts here.  For the life of me I can't understand why developers would make things so hard?  I now see why windows controls the market.

---

### Post by dineshs on 2010-08-25
Did you try this
1)Rightclick NM icon and tick Enable wireless
2)Rightclick NM icon -edit connections-wireless-select device and see Available to all users is ticked

---

### Post by anonomo on 2010-08-25
@dineshs
thanks heaps for your questions)))
i'll post the response to 
[http://ubuntuforums.org/showthread.php?p=9763372#post9763372](http://ubuntuforums.org/showthread.php?p=9763372#post9763372)
just so not make mess of 

@everyone 
these forums are awesome thanks 4 the help

p.s no i didn't try that hang on i'll switch OS and give it a go

---

### Post by Sxynerd on 2010-08-25
> **dineshs said:**
> Did you try this
1)Rightclick NM icon and tick Enable wireless
2)Rightclick NM icon -edit connections-wireless-select device and see Available to all users is ticked


Yes and all three of these are click-able and Check marked enabled.
Enable Networking
Enable Wireless
Enable Notifications

I also have "Edit connections" and "about"   Here is a screenshot.  If you notice the "Wifi" signal bars up top; they never change.  It is not really connecting to anything.  In fact, after I edit my "Mike_Jess" wireless network, it still says "Never" for being connected.

---

### Post by dineshs on 2010-08-25
Pl see if post #14 in this link can help
[http://ubuntuforums.org/showthread.php?p=9680300#post9680300](http://ubuntuforums.org/showthread.php?p=9680300#post9680300)
Pl also post what is in  */var/lib/NetworkManager/NetworkManager.state*
```
gksudo gedit /var/lib/NetworkManager/NetworkManager.state
```

---

### Post by Sxynerd on 2010-08-25
I have tried it with wpa, wpa2 and mixed with restarts in between and it has not affected it in any way.



EDIT:  (the GKGUDO results)
[COLOR="Red"]
[main]
NetworkEnabled=true
WirelessEnabled=True
WWANEnabled=true[/COLOR]

---

### Post by dineshs on 2010-08-25
I think chili555 can help you.Please try to send a private message

---

### Post by Sxynerd on 2010-08-25
> **dineshs said:**
> I think chili555 can help you.Please try to send a private message

PM sent, thanks for you help anyway.

---

### Post by chili555 on 2010-08-25
I am going to be out for a few hours but I will help you when I return.

Do you also have a USB wireless device? If so, please post:```
lsusb
dmesg | grep firmware
```See you in a while.

---

### Post by zdenal on 2010-08-25
I'm not sure if your broadcom card is using the bcmwl-kernel-source driver, but if yes, then try this howto:

[http://polach.cc/howto-fix-broadcom-wifi-adapter-wpa-network-access-on-ubuntu-10-04-lucid-lynx](http://polach.cc/howto-fix-broadcom-wifi-adapter-wpa-network-access-on-ubuntu-10-04-lucid-lynx)

---

### Post by Sxynerd on 2010-08-25
> **chili555 said:**
> I am going to be out for a few hours but I will help you when I return.

Do you also have a USB wireless device? If so, please post:```
lsusb
dmesg | grep firmware
```See you in a while.

Thank you for your help.  No, I don't have any USB devices.

---

### Post by chili555 on 2010-08-25
Your Broadcom is undoubtedly not working because it requires proprietary firmware. These, along with certain fonts, audio-video codecs, et al, are not included in a default install because they are proprietary and don't meet the spirit and the letter of open source. If you want to install them anyway, you certainly may.

I believe your card uses the native b43 driver plus firmware and not the bcmwl-kernel-source driver. Are you able to temporarily connect to an ethernet cable and try to grab the firmware with System > Administration > Hardware Drivers?

---

### Post by Sxynerd on 2010-08-25
> **chili555 said:**
> Your Broadcom is undoubtedly not working because it requires proprietary firmware. These, along with certain fonts, audio-video codecs, et al, are not included in a default install because they are proprietary and don't meet the spirit and the letter of open source. If you want to install them anyway, you certainly may.

I believe your card uses the native b43 driver plus firmware and not the bcmwl-kernel-source driver. Are you able to temporarily connect to an ethernet cable and try to grab the firmware with System > Administration > Hardware Drivers?

No, I can't.  I don't even think my on board LAN is working either.  Here is where I'm at right now.  I don't know how to get it to work or even if I'm heading in the right direction.

---

### Post by chili555 on 2010-08-26
You *are* headed in the right direction! To activate the driver, meaning download and install the firmware, an active internet connection is needed. > No, I can't. I don't even think my on board LAN is working either.Do you mean you can't get the ethernet working (you are hooked up but there is no connection) or do you mean no ethernet connection is available at all (you can't get to your neighbor's/internet cafe's/university's router)?

If you can hook up an ethernet cable, does the Network Manager icon at the top right show an available wired connection? If you run the terminal command:```
ifconfig
```Does it show an ethernet interface, eth0, perhaps? If you have an eth0 interface, your on board LAN is probably working well.

---

### Post by Sxynerd on 2010-08-28
> **chili555 said:**
> You *are* headed in the right direction! To activate the driver, meaning download and install the firmware, an active internet connection is needed. Do you mean you can't get the ethernet working (you are hooked up but there is no connection) or do you mean no ethernet connection is available at all (you can't get to your neighbor's/internet cafe's/university's router)?

If you can hook up an ethernet cable, does the Network Manager icon at the top right show an available wired connection? If you run the terminal command:```
ifconfig
```Does it show an ethernet interface, eth0, perhaps? If you have an eth0 interface, your on board LAN is probably working well.

Sorry to be delayed on the reply, I've been on Holiday with the family.:popcorn:

I am unable to connect to net at all.  The onboard lan is not even working.  (both did work with windows)

IF config comes back with.

michael@michael-desktop:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:384 errors:0 dropped:0 overruns:0 frame:0
          TX packets:384 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:29392 (29.3 KB)  TX bytes:29392 (29.3 KB)

---

### Post by chili555 on 2010-08-29
If you can grab a couple of files on another machine and transfer those files with a USB drive, post #6 here shows how to get going:

[http://ubuntuforums.org/showthread.php?t=1419368](http://ubuntuforums.org/showthread.php?t=1419368)

---

### Post by bkratz on 2010-08-29
> **chili555 said:**
> If you can grab a couple of files on another machine and transfer those files with a USB drive, post #6 here shows how to get going:

[http://ubuntuforums.org/showthread.php?t=1419368](http://ubuntuforums.org/showthread.php?t=1419368)


@Chili555
Sorry to interrupt--but if it makes a difference (probably not) the op is using 10.04 and the thread mentions the Karmic version of cutter.  The Lucid version is at 

[http://packages.ubuntu.com/lucid/b43-fwcutter](http://packages.ubuntu.com/lucid/b43-fwcutter)

and it does have a slightly different number on it it says build 1.

Sorry if this was worthless!

---

### Post by chili555 on 2010-08-29
Good catch! Yessir, please use the Lucid version. Thanks!

---

### Post by Sxynerd on 2010-08-30
OK, I'm really confused.  

I have tried to install the b43-fwcutter_012-1build1_amd64.deb.  (I have 64bit) Well, at least the stock Vista OS it had on it before was 64bit.

[IMG]http://i44.photobucket.com/albums/f33/wolvee123/Failedtointall.png[/IMG]

---

### Post by chili555 on 2010-08-30
I think b43-fwcutter gets stuck when it can't go on line to grab the firmware files. Kind of silly, isn't it? If we could go on line, we wouldn't need the firmware!!!

I suggest you just run the second command to force b43-fwcutter to use the file you downloaded:```
tar xjf broadcom-wl-4.150.10.5.tar.bz2
cd broadcom-wl-4.150.10.5/driver
sudo b43-fwcutter -w /lib/firmware/ wl_apsta_mimo.o
```Post back if it doesn't work as expected.

---

### Post by Sxynerd on 2010-08-30
OK, I'm still lost.  You said to run the second command.  What is the second command?  I tried pasting in all of your "code" as a whole and as individual lines and I'm getting back nothing but garbage from the terminal.

Can you type it out so I can tell exactly what I need to do at every step?  Thanks.

---

### Post by chili555 on 2010-08-30
Did you also download the firmware file and transfer it on a USB drive? Where is it? On your desktop? Please open a terminal and do:```
cd Desktop
```Now, let's unpack the firmware file:```
tar xjf broadcom-wl-4.150.10.5.tar.bz2
```The tar command should result in a new folder called *broadcom-wl-4.150.10.5*, within which is a folder called *driver*. We need the firmware files in the *driver* folder, so let's change directories there:```
cd broadcom-wl-4.150.10.5/driver
```Now, we will use b43-fwcutter to cut out the firmware and place it in the file on your Ubuntu installation where the b43 wireless driver expects to find it:```
sudo b43-fwcutter -w /lib/firmware/ wl_apsta_mimo.o
```Now, a reboot should have your wireless working.

Post back if you are still stuck.

---

### Post by Sxynerd on 2010-08-30
ok before I went any further, I thought I would post a screen shot to make sure everything was in order on the terminal.  Rebooting now...

thanks

[img]http://i44.photobucket.com/albums/f33/wolvee123/Lastdirrectiongs.png[/img]

---

### Post by Sxynerd on 2010-08-30
SUCCESS!!!  Thank you for all your help!  Now, it's time to back track and realize everything I had to do to get it to work and to completely learn a new OS.

Thank you everyone for having patience with me.

---

### Post by chili555 on 2010-08-30
Glad it's working! Good work.

---

### Post by Sxynerd on 2010-08-30
Now it's time to figure out how to install flash. Any ideas?  I've got a bunch of options.

---

### Post by bkratz on 2010-08-30
> **Sxynerd said:**
> Now it's time to figure out how to install flash. Any ideas?  I've got a bunch of options.

You might look here

[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

---

### Post by Sxynerd on 2010-08-30
Ahk, I figured it out right after I posted.  Reminds me to use my own brain before I run off and enlist using the brains of other people.  I'm sure it can get annoying.  

Peace love and hair grease.
:popcorn:

---

### Post by bkratz on 2010-08-30
Two for Two not a bad day--eh!

Glad you got your wireless working

---

### Post by Sxynerd on 2011-05-24
I'm bringing my thread back from the dead.  I now have 10.10 installed, now what do I do?

---

