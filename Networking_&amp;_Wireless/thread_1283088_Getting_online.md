---
title: "Getting online"
date: 2009-10-05
forum: Networking &amp; Wireless
---

### Post by paulgertie on 2009-10-05
Hello, I am very new to this and have a problem trying to get my wireless USB adapter to work. I have been on absolute beginners and it was suggested I come here. If anyone can help I would ask that your instructions are basic it took me a day to find how to open a terminal window.
Anyway I have installed Ubuntu 9.04 and I am trying to get my Azurewave GU210 adapter to work, I have found and installed the driver for it, but it will not activate. I was advised to run command 1susb and got the result

Bash : 1susb: command not found

I was also advised to run iwconfig and got the following result

paul@paul-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Wlan0 is a Belkin network card and wlan1 is the Azurewave USB.
Now on windows the adapter comes up onscreen and advises that I need to install it, is there an equivalent on Ubuntu, I'm not saying windows is right, I'm asking am I doing something wrong. Is there an equivalent to control panel, so I can see what's what.

Update: When I go windows wireless drivers without it in it shows netrtuw Hardware not present, restart it with it in and it shows present. When I try to install driver it says driver installed. When I try press configure network it says cannot find network configuration tool.
Thanks, Paul

---

### Post by hal10000 on 2009-10-05
> I was advised to run command 1susb
the command is [COLOR="Red"]lsusb[/COLOR] with a lowercase L instead of 1 (one). You may post the output of this command here (You can mark the output with your mouse and paste it with the middle mouse button).

Your usb-adaptor seems to be recognized correctly by your ubuntu-system, so i guess your drivers are already installed.

In gnome i guess on the right side of your taskbar is an icon to set up your network (including wireless, i don't use gnome, so i can't tell you where exactly it can be found, maybe you have to search a little bit in your apps or system menu).
You could also install a special tool like [COLOR="Red"]wicd[/COLOR] or [COLOR="Red"]wifi-radar[/COLOR] to manage your wireless connections.

But in any case you have to know the network-name (essid) and the wireless key for your network and also wether your wireless network is encrypted with WEP or WPA or WPA2.
These informations you have to know unless your wireless network is completely open and unencrypted, which would be a very bad idea. (I guess you don't want to see the police knocking on YOUR door because your neighbour has downloaded the latest hardcore children porn via your wireless net.)

---

### Post by Iowan on 2009-10-05
I'm fond of **lshw -C network** to get information about network devices. Wifi hotspots are a good place to check unsecured wireless connectivity.

Network Manager can manage only one interface at a time, so you may need to disable the "other" one(s).

---

### Post by thecow on 2009-10-05
> **hal10000 said:**
> 
But in any case you have to know the network-name (essid) and the wireless key for your network and also wether your wireless network is encrypted with WEP or WPA or WPA2.
I dont know what you mean, however that is not accurate.  Network Manager will list the networks you can connect to and will tell you what encryption scheme they are using. 

 To OP: In the upper right hand corner you will see a networking icon, click on it and it should list the networks around you.  Click on a network, does it not connect to it?

---

### Post by hal10000 on 2009-10-06
@thecow:

> Network Manager will list the networks you can connect to and will tell you what encryption scheme they are using
So you think that you don't have to care to which network you are connecting to?
Not only that this is usually illegal (if it's not your own network),nevertheless you have to know the wireless key to get connected.

And, btw. what will you do if the network you have to connect to is hidden?

---

