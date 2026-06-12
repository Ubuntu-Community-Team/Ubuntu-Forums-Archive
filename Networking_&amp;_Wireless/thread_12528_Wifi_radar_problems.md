---
title: "Wifi radar problems"
date: 2005-01-25
forum: Networking &amp; Wireless
---

### Post by albersag on 2005-01-25
Im trying to get working my wifi on ubuntu (smc 2835).

It works and iwlist eth1 scan gave me what i expected to, but wii radar (scan option) does not return me any wifi.

Thanks in advance

I have configured as it must , so a wifi-radar configuration problem i dont think it is.

Output:

eth1      Scan completed :
          Cell 01 - Address: 00
                    ESSID:"xxxxxxx"
                    Mode:Master
                    Encryption key: off
                    Channel:11
                    Quality:37/0  Signal level:-49 dBm  Noise level:-86 dBm


Wifi_radar Screen is empty always, ( i press scan and nothing appears to work)

---

### Post by ming0 on 2005-02-03
You might try the top of the 2nd page--I had to do a bit of messing around to get wifi radar working:

[http://ubuntuforums.org/showthread.php?t=10046&page=2&pp=10&highlight=wifi+radar](http://ubuntuforums.org/showthread.php?t=10046&page=2&pp=10&highlight=wifi+radar)

---

### Post by kermy on 2005-04-09
I just tried wifi-radar, but it doesn't support wpa.. :( I hope we will get great wifi support in breezy!

---

### Post by lonetree on 2005-07-10
I am trying my best to convert my notebook to run with ubuntu. I have almost get all my desktop PC to run with ubuntu, a simple reason, I like ubunut though the name doesn't sound appealing but, I find that this is so far the best linux distro I have encounter (still waiting for someone to solve the timestamp proble though), I have encourage a lot of my friends to switch to using ubuntu.

The only reason why I'm still not ready for my notebook is mainly the wireless issue, I have to work remotely a times, and the wireless thing is killing me. Have tried with a number of wireless adapter but lots of it don't work natively. I have to use ndiswrapper to compile with the windows driver and the security part is a pain. Not taking into account of WPA or rather WPA-PSK, WEP is already a pain. Though wifi-radar could do the job,but it still fails. Although it could display a list of wireless netrwork within the range, it seems that the native ubuntu network configurator is taking control all the time. And when in cases where there is WEP protecting the wireless network, I have to issue the iwconfig key xxxx-xxxx command in console mode and then use the ubuntu network configurator to activate the wireless connection.

Have I done anything wrong here? Is there anyway that I could let wifi-radar full control?

I am still new to linux, about 2 years of exposure but seriously concentration on linux distro start last year November when ubuntu exist and when I really settle down on ubuntu.

I hope I could learn more and help more people in the future.

[www.ubuntuguide.org](www.ubuntuguide.org) (by Chua Wen Kiat) has help me a lot. Thanks Wen Kiat.

Regards,

---

### Post by ssck on 2005-07-20
[QUOTE=lonetree]I am trying my best to convert my notebook to run with ubuntu. I have almost get all my desktop PC to run with ubuntu, a simple reason, I like ubunut though the name doesn't sound appealing but, I find that this is so far the best linux distro I have encounter (still waiting for someone to solve the timestamp proble though), I have encourage a lot of my friends to switch to using ubuntu.

The only reason why I'm still not ready for my notebook is mainly the wireless issue, I have to work remotely a times, and the wireless thing is killing me. Have tried with a number of wireless adapter but lots of it don't work natively. I have to use ndiswrapper to compile with the windows driver and the security part is a pain. Not taking into account of WPA or rather WPA-PSK, WEP is already a pain. Though wifi-radar could do the job,but it still fails. Although it could display a list of wireless netrwork within the range, it seems that the native ubuntu network configurator is taking control all the time. And when in cases where there is WEP protecting the wireless network, I have to issue the iwconfig key xxxx-xxxx command in console mode and then use the ubuntu network configurator to activate the wireless connection.

Have I done anything wrong here? Is there anyway that I could let wifi-radar full control?

I am still new to linux, about 2 years of exposure but seriously concentration on linux distro start last year November when ubuntu exist and when I really settle down on ubuntu.

I hope I could learn more and help more people in the future.

[www.ubuntuguide.org](www.ubuntuguide.org) (by Chua Wen Kiat) has help me a lot. Thanks Wen Kiat.

Regards,[/QUOTE]


have you tried gtkwifi 1.08.1 ? it is great but doesn't support wpa yet

you can get the link here : [http://ubuntuforums.org/showthread.php?t=49148&page=1](http://ubuntuforums.org/showthread.php?t=49148&page=1)

---

### Post by lonetree on 2005-07-21
Thanks.

I will go take a look and try it out. Will post my result after trying.

:-)

Oh Btw, I just broke my notebook 4 days ago, very upset about it. The pcmcia card punctured the whole slot and afftected the display chip.

:-(

---

### Post by lonetree on 2005-07-24
ok I'm back. Installed the gtkwifi, .deb file. Everything successful, but can run. Perhaps, please explain how to start up. 

And also, do I have to configure the networking part? How do I set the WEP key? How do I specify which key to use?

Thanks

---

### Post by ssck on 2005-07-28
[QUOTE=lonetree]ok I'm back. Installed the gtkwifi, .deb file. Everything successful, but can run. Perhaps, please explain how to start up. 

And also, do I have to configure the networking part? How do I set the WEP key? How do I specify which key to use?

Thanks[/QUOTE]

sorry for the late reply.you can run it using this command from the terminal :- 
gtkwifi run-in-window

or you could create a launcher and put in the above command

---

### Post by lonetree on 2005-07-28
[QUOTE=ssck]sorry for the late reply.you can run it using this command from the terminal :- 
gtkwifi run-in-window

or you could create a launcher and put in the above command[/QUOTE]

Hi.

Thanks for the reply, have got it work after posting the message with a few search and tries. However, I am still face with some troubles with the WEP settings. I have set and assign the AP to use key #4  as the default key. each time, I will have to issue the command in console to assign the key to be used. 

Also, how do I disable the gnome network manager to not start the wireless device at startup, so that gtkwifi could see the wireless network.

I have also found one very strange behavior, although it shows that I am connected to my wireless network, but when I issue the command "iwconfig" I saw that I am connected to another wireless network. The essid in iwconfig and the gtkwifi status are totally different. Strange, isn't it?

Have I done anything wrong with this? Or is this a common bug?

Thanks.

Side note:

Although this is a totally different technical issue, I just like to ask around. Has anyone of you face with timestamp problem over network share? For example, the modified time of the file changed to 1980 01 01 Tues 08:00am. This always happened when I copy a file from my ubuntu box to another windows share folder.

:-(

Regards,

---

### Post by ssck on 2005-07-29
[QUOTE=lonetree]Hi.

Thanks for the reply, have got it work after posting the message with a few search and tries. However, I am still face with some troubles with the WEP settings. I have set and assign the AP to use key #4  as the default key. each time, I will have to issue the command in console to assign the key to be used. 

Also, how do I disable the gnome network manager to not start the wireless device at startup, so that gtkwifi could see the wireless network.

I have also found one very strange behavior, although it shows that I am connected to my wireless network, but when I issue the command "iwconfig" I saw that I am connected to another wireless network. The essid in iwconfig and the gtkwifi status are totally different. Strange, isn't it?

Have I done anything wrong with this? Or is this a common bug?

Thanks.

Side note:

Although this is a totally different technical issue, I just like to ask around. Has anyone of you face with timestamp problem over network share? For example, the modified time of the file changed to 1980 01 01 Tues 08:00am. This always happened when I copy a file from my ubuntu box to another windows share folder.

:-(

Regards,[/QUOTE]


could you paste the details of the interfaces file here ?

you can get the file from : /etc/network

---

### Post by lonetree on 2005-07-29
[QUOTE=ssck]could you paste the details of the interfaces file here ?

you can get the file from : /etc/network[/QUOTE]

Hi ssck,

are you refering to the interfaces file in etc/network ?

thanks

regards,

---

### Post by ssck on 2005-07-29
[QUOTE=lonetree]Hi ssck,

are you refering to the interfaces file in etc/network ?

thanks

regards,[/QUOTE]

yes.please paste the results here.

thanks

---

### Post by lonetree on 2005-07-29
[QUOTE=ssck]yes.please paste the results here.

thanks[/QUOTE]

Thanks again. Below is the results from /etc/network/interfaces. One think strange, I don't get to see wlan0 (which is my wireless interface). Hope you could help solve this. Let me know how I should go about adding the specific WEP key.

----------------- begin ------------------------
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

# The primary network interface




iface eth0 inet dhcp


---------------end-----------------------


Regards,

---

### Post by ssck on 2005-07-30
[QUOTE=lonetree]Thanks again. Below is the results from /etc/network/interfaces. One think strange, I don't get to see wlan0 (which is my wireless interface). Hope you could help solve this. Let me know how I should go about adding the specific WEP key.

----------------- begin ------------------------
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

# The primary network interface




iface eth0 inet dhcp


---------------end-----------------------


Regards,[/QUOTE]


hi,

this is my interfaces file :

# They will be activated automatically by the hotplug subsystem.

mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet dhcp

iface wlan0 inet dhcp
wireless-essid HHH
wireless-mode managed
wireless-keymode restricted
wireless-key 1234-5678-90

auto wlan0

auto eth0


---------------------

you could use it as a sample for your interfaces file.just change the wireless-essid to your own access point and change the wireless-key to your according to the one set in your access point.

btw, when you start up gtkwifi, what do u get ? as far as i know, gtkwifi doesn't read the interfaces file.

---

### Post by lonetree on 2005-07-30
[QUOTE=ssck]hi,

this is my interfaces file :

# They will be activated automatically by the hotplug subsystem.

mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet dhcp

iface wlan0 inet dhcp
wireless-essid HHH
wireless-mode managed
wireless-keymode restricted
wireless-key 1234-5678-90

auto wlan0

auto eth0


---------------------

you could use it as a sample for your interfaces file.just change the wireless-essid to your own access point and change the wireless-key to your according to the one set in your access point.

btw, when you start up gtkwifi, what do u get ? as far as i know, gtkwifi doesn't read the interfaces file.[/QUOTE]

Hi ssck,

thanks so much for the info. But do you need to specify the key use? Anyway, I will give it a try and if there is anything, please help me.

Thanks a zillion.

Regards,

---

### Post by valnar on 2005-08-19
The person who comes up with a usable WPA Radius or WPA-PSK program will make a lot of Linux users happy.  I still can't use ubuntu (or any Linux distro) for my work, nor recommend it to any colleagues, until this glaring omission is fixed.

Is there not a single developer in all of GNU-land working on WPA, in any application?  ](*,) 

-Robert

---

