---
title: "Internet not working with WPA"
date: 2010-09-01
forum: Networking &amp; Wireless
---

### Post by wesleybishop on 2010-09-01
For some reason my Ubuntu computer will not connect to the internet when the router uses WPA but is fine with WEP the sooner this is fixed the better because my ubuntu computer is down until this is solved :(. But I know the Ubuntu community and  I am sure we will resolve this in no time so please throw any ideas at me.:D

---

### Post by Tracy177 on 2010-09-01
> **wesleybishop said:**
> For some reason my Ubuntu computer will not connect to the internet when the router uses WPA but is fine with WEP the sooner this is fixed the better because my ubuntu computer is down until this is solved :(. But I know the Ubuntu community and  I am sure we will resolve this in no time so please throw any ideas at me.:D


yes yes yes :)

it depends what card do u have not all work out of the box with wpa and ubuntu 

i had for example rt2870 and it didnt work with sta driver every 1 min internet was disconnected etc . 

buy card that does work or configure your card properly than it may work.

if u have iwl or zd ath rt73 rt2800 they work for sure

---

### Post by bkratz on 2010-09-01
> **wesleybishop said:**
> For some reason my Ubuntu computer will not connect to the internet when the router uses WPA but is fine with WEP the sooner this is fixed the better because my ubuntu computer is down until this is solved :(. But I know the Ubuntu community and  I am sure we will resolve this in no time so please throw any ideas at me.:D

you might also want to look at this

[http://ubuntuforums.org/showpost.php?p=9680300&postcount=14](http://ubuntuforums.org/showpost.php?p=9680300&postcount=14)

---

### Post by wesleybishop on 2010-09-01
I have a Belkin Wireless USB [http://www.productwiki.com/upload/images/belkin_wireless_g_usb_adapter.jpg](http://www.productwiki.com/upload/images/belkin_wireless_g_usb_adapter.jpg)  .

Also I figured out that if I change it to automatic DHCP adn Manual DNS it will not work at all but if I change it to Default which Is Auto DHCP and DNS it will work but soooo slowly that it is unusable.

---

### Post by wesleybishop on 2010-09-01
> **bkratz said:**
> you might also want to look at this

[http://ubuntuforums.org/showpost.php?p=9680300&postcount=14](http://ubuntuforums.org/showpost.php?p=9680300&postcount=14)

Mine is set to WPA-PSK [TKIP]

---

### Post by Baji P. on 2010-09-01
I thought WPA & WPA2 have been available in Ubuntu for a while now, guess not.

In any case, if you cannot find native Ubuntu support for your card, you can go the [NDIS Wrapper route]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper"), where you install the windows driver.

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

hth...-baji.

---

### Post by wesleybishop on 2010-09-01
> **Baji P. said:**
> I thought WPA & WPA2 have been available in Ubuntu for a while now, guess not.

In any case, if you cannot find native Ubuntu support for your card, you can go the [NDIS Wrapper route]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper"), where you install the windows driver.

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

hth...-baji.

My card works fine with Ubuntu I have been using this card for a while now its just they changed the encryption to WPA now it does not work. Thanks for the idea though :) Plus I have no inter net on my Ubuntu desktop computer to download this program.

---

### Post by nightkidz on 2010-09-01
i am installing ubuntu 10.0.4 using laptop msi cr400 , i can not detect the wireless, pls anyone help

---

### Post by wesleybishop on 2010-09-01
> **nightkidz said:**
> i am installing ubuntu 10.0.4 using laptop msi cr400 , i can not detect the wireless, pls anyone help

go to [http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336) then on the top left corner you should see a new thread button click on that and type as detailed information as you can give :D

---

### Post by Baji P. on 2010-09-01
NightKidz...when you started the installation, did you have your laptop connected to the internet using a wired connection ?

A high % of wireless issues would get resolved automatically if people just did the install while connected to the internet with a wired ethernet connection.

This allows the installer to probe your hardware and connect to online package repositories and check for drivers for your hardware. Without a wired connection the installer cannot to the repositories even if a driver were available.

Without that wired connection, if the driver is not on the CD you are out of luck...hth.

---

### Post by jrbjr5 on 2011-04-28
I had a similar problem, but noticed that ubuntu was choosing the IP for my wireless card which was used by my router.  I set up a static IP assigning a different address to my laptop and everything worked.  Maybe this will help someone...

---

### Post by n3140f on 2011-04-29
Marking this solved for the time being . . . .

I decided to re-install using Natty 11.04 while plugged into ethernet.  Didn't really solve the wireless problem, but now I can start fresh.  Thanks.

---

