---
title: "presario v2000 wifi light off"
date: 2010-03-29
forum: Networking &amp; Wireless
---

### Post by jdsloan on 2010-03-29
Installed UBUNTU 2 days ago, have tried ALL posts to resolve my problems.  The WI-FI light above the keyboard is off, I assume the OS does not see WI-FI adapter - Broadcom 4318.  I have tried windows driver with this and that.  I have typed more gobble-de-goop into the "terminal", and seen more error messages, I am at wits end.
I am a NEWBIE who wants to learn at 50, is there anyone out there that speaks idiot, and can put it all in real simple terms for me.
MANY thanks to anyone with a LOT of patience!!!

---

### Post by chili555 on 2010-03-29
I have a fair amount of patience. I'll be glad to help. The fastest and easiest way to find out what's going on under the hood is the terminal. Let's find out if you have a working wireless interface. In a terminal, do:```
iwconfig
```Do you see a wireless interface, wlan0, perhaps? If not, please run and post:```
sudo lshw -C network
```That will list the networking hardware on your system and give us some clues as to how to proceed.

If you do have a wireless interface, click the Network Manager icon and see if you can connect. Be sure the wireless switch and Fn keys are toggled appropriately. You can get an idea of the correct position by running:```
rfkill list
```If the wireless is blocked, manipulate the switches again and run rfkill again. Reach a point where the wireless is neither hard- or soft-blocked.

The wireless LED is usually, but not always an indicator of the health of your wireless.

---

### Post by jdsloan on 2010-03-29
ran iwconfig
   wlan0  IEEE 802/11bg   ESSID:""                                                                                                                                           
   Mode"Managed Frequescy:2.412 GHz  Access Point: Not-Associated
   Tx-Power=0 dBm
    Retry long limit:7      RTS thr:off    Fragment thr:off
    Power Management:off
    Link Quality:0  Signal level:0-   Noise level:0
    Rx Invalid nwid:0  Rx Invalid crypt:0  Rx Invalid frag:0
    Tx excessive retries:0 Invalid misc:0 Missed beacon:0

rfkill list

0: phy:0 Wireless LAN
      Soft blocked: no
      Hard blocked: no



In my first post I failed to mention the wifi light over the keyboard is a button you press to activate the wifi, when pressed within UBUNTU nothing happens.
When I go to System > Administration > Hardware Drivers
  I see Broadcom B43 wireless driver, but when I push activate it says it is downloading, but because that little stupid button over the keyboard will not come on, it can never really activate.
Thank you again for your response, you are brave!!!

---

### Post by chili555 on 2010-03-29
> I see Broadcom B43 wireless driver, but when I push activate it says it is downloading, but because that little stupid button over the keyboard will not come on, it can never really activate.That really has nothing to do with it. It wants internet access, usually from an ethernet connection, in order to get the needed firmware. However, you do have a wireless interface, wlan0! Perhaps the Windows wireless drivers are properly in place. Let's try two tests. First, let's see if any kernel messages say anything useful about the firmware:```
dmesg | grep -e firm -e b43 -e ndis
```Let's see if your card will see networks:```
sudo iwlist wlan0 scan
```We are getting very close!

---

### Post by jdsloan on 2010-03-29
dmesg | grep -e firm -e b43 -e ndis

gave me a whole page of stuff and most lines have ERROR : Firmware file "b43........"etc"

sudo iwlist wlan0 scan

gave me   wlan0    Interface doesn't support scanning : Network is down

---

### Post by chili555 on 2010-03-29
> ERROR : Firmware file "b43That's all we need to see. That means the driver needs but lacks essential firmware and so won't operate correctly. Is this a computer that you can walk over to the router, hook up an ethernet cable and activate the hardware driver? If not, do you have a USB key so we can transfer files?

---

### Post by chili555 on 2010-03-29
If you need to use a USB key, here is the process: [http://ubuntuforums.org/showpost.php?p=9028167&postcount=17](http://ubuntuforums.org/showpost.php?p=9028167&postcount=17)

---

### Post by jdsloan on 2010-03-29
have a flash drive plugged in and ready

---

### Post by jdsloan on 2010-03-29
I "grabbed" the package on a flash selected extract here and when I try to drag to lib/firmware it gives me the error 'you do not have permissions to create it in the destination'

---

### Post by jdsloan on 2010-03-29
post count 18 
mkdir b43
sudo cp /lib/firmware/b43/* b43
returns error - cp: cannot stat '/lib/firmware/b43/*'; No such file or directory

---

### Post by bkratz on 2010-03-29
> **jdsloan said:**
> post count 18 
mkdir b43
sudo cp /lib/firmware/b43/* b43
returns error - cp: cannot stat '/lib/firmware/b43/*'; No such file or directory

Chili555 must be getting coffee now! Here is a similar post where he did the same thing recently, I'll butt out now, but i hope this helps, if not just post where you put it!

[http://ubuntuforums.org/showpost.php?p=9029728&postcount=23](http://ubuntuforums.org/showpost.php?p=9029728&postcount=23)

---

### Post by chili555 on 2010-03-29
I did have to run into the city for a little appointment. You cannot drag any files into any place in /etc because they are owned by root and not writable by ordinary users. I know, you and I are hardly ordinary!

May I assume you dragged the files off of the USB key to your desktop and extracted them there? If so, let's first create a missing directory and then move the files. We will precede our commands with 'sudo' so we temporarily have the priveleges of root, also known as Super User. 

(sudo = Super User DO, get it?)```
sudo mkdir /lib/firmware/b43
cd Desktop
ls
```Do you see the file you extracted, called b43-firmware-1.1? Good! Now do:```
sudo cp b43-firmware-1.1/firmware/b43/* /lib/firmware/b43
```Any complaints or errors? No? Great!

Let's make sure permissions and ownership are correct:```
sudo chmod 755 /lib/firmware/b43/*
sudo chown root:root /lib/firmware/b43/*
```The wildcard * means, roughly, do everything there is to do.

Now, we will need to unload and reload the *b43* module and see if it grabs the firmware:```
sudo rmmod -f b43
sudo modprobe b43
sudo iwlist wlan0 scan
```Does your wireless interface now see networks? Can you click the Network Manager icon and connect?

Any signs of life from the wireless light?

---

### Post by jdsloan on 2010-04-03
thank you for your time, I apologize for not responding, I work a lot of OT.  
your help was priceless, worked like a charm, once I began to understand what
you were trying to get me to do.  I took Basic programming 200 years ago 
and there was a moment of AH HA.  everything is working great, think I am
ready to do a clean sweep and install JUST UBUNTU, I had partitioned.
once again thank you for your time and patience..

---

### Post by chili555 on 2010-04-03
Excellent! Glad it's working! Before you do a reinstall, save those firmware files on a USB key or a CD and save yourself a bit of work.

Enjoy!

---

