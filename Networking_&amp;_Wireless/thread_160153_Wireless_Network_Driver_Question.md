---
title: "Wireless Network Driver Question"
date: 2006-04-14
forum: Networking &amp; Wireless
---

### Post by Mr_Welfare on 2006-04-14
Hi Everyone,

I have just recently downloaded and installed Ubuntu and am very new to the Linux OS.

I am looking for a way to use my "D-Link DWL-G122" USB Wireless adapter with Linux. Unfortunatly, D-Link does not have any Linux drivers for download. What other methods (and how would I go about doing them) are avaliable for installing wireless network drivers?

Thanks,

Mr_Welfare

---

### Post by x5452 on 2006-04-14
search here for your card, drivers should be linked:
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)
Follow this wiki guide, make sure to dl diswrapper and ndisgtk
[https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper](https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper)

---

### Post by Mr_Welfare on 2006-04-14
[QUOTE=x5452]make sure to dl diswrapper and ndisgtk
[/QUOTE]

What do you mean by this? 

I have followed the Howto, (using the graphical interface instead of the prompts) installed ndiswrapper and installed the windows driver off of the D-Link CD (just like the list of surrpoted cards says to do). I still can't seem to get an internet connection though. My System>Admin>Networking shows that my wlan0 is active, but whenever I try to go to Google or Yahoo on Mozilla, I still get a message saying that the site cannot be found. :confused:

---

### Post by pkslot on 2006-04-15
How about the configuration of your wlan, is it set on your "essid" and is the password right?

---

### Post by Mr_Welfare on 2006-04-15
Yes, I think what the problem is, is that I'm using a 128 bit WEP encryption code. I've heard that Ubuntu doesn't readily support 128 bit encryption. Later on today, I'm going to set the encryption code to a 64 bit and see wat happens.

---

### Post by pkslot on 2006-04-15
Well, be sure to let us know how it turns out ;) 

To be honest, i just got my wlan working too, by followin the links above, but i have a few problems my self. It seems that i can't save my settings, so everytime i turn on the pc, i have to set it again, for wlan0 and not eth0 (or something like that ;) )

The WEP encryption is the least of my problems, cause i live a couple of miles away from the nearest neighbour, but still, it's always nice to know!

---

### Post by Mr_Welfare on 2006-04-15
Well, I still haven't managed to get it working yet. My USB adpater's light still just flashes on and off, but I still can't get a connection going. I've heard that you need to put dashes between every fourth character, but that doesn't do anything for me. :-? I've also been mesing around with

```
sudo nano /etc/network/interfaces
```

and editing the text there. (As [this]("https://wiki.ubuntu.com/WiFiHowto") guid said to do. See the title: "Adding it to /etc/network/interfaces") Now I just hope I haven't messed up my kernel somehow (as I foolishly didn't backup the file before editing.)

I'm not really sure what I'm going to do yet as I have looked through and followed (to the best of my knowledge) most of the guids listed [here]("https://wiki.ubuntu.com/WifiDocs"). I know that the Wifi works fine without an encryption on, but since I live close to three or four other Wifi users, I like to keep an encryption on as much as possible. 

If anyone else has any other information regarding using a 64 bit WEP encryption in Ubuntu, it would be appreciated.

---

### Post by Mr_Welfare on 2006-04-16
I am now thinking of using NetworkManager to try to get my wireless interent connection working. Unfortnatly, I have had some problems installing the certain packages required to install NetworkManager. The install says to enable the universe repository, but ecause I don't have an internet connection on my Ubuntu PC, I'm not sure how to go about doing this. Instead of enabling the universe repository, I tried to download and install the packages I needed off of the packages section of the Ubuntu site. When trying to install the package libdbus1-2, however, I go an output saying that libdbus conflicted with the dbus package that was already installed. I need libdbus installed because the next package, I don't have the nam in front of me right now... I think it was something like dch__) requires lidbus1-2 to be installed. I was wondering if **anyone** could post what their

```
sudo nano /etc/network/interfaces
```

looks like by default. I have changedthis file and I think that doing so might have caused a problem. If anyone has any information regarding my Wifi problem, it would be appreicated.

Mr_Welfare

---

### Post by el duderino on 2006-04-16
> I was wondering if anyone could post what their

Code:

sudo nano /etc/network/interfaces

Here's mine...my wlan0 is not installed/working right though...

>   GNU nano 1.3.8                        File: /etc/network/interfaces

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

iface ra0 inet dhcp
wireless-essid different
wireless-key ###your key here###

iface eth0 inet dhcp



auto eth0

auto ra0

I'm trying to get my wifi up and running with 128 encryption no joy yet. I worked for live cd and then just after install. I'm investigating...

---

