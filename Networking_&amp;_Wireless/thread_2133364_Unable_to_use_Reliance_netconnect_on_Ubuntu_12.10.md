---
title: "Unable to use Reliance netconnect on Ubuntu 12.10"
date: 2013-04-07
forum: Networking &amp; Wireless
---

### Post by gyanda on 2013-04-07
Hi,

Recently I have installed Ubuntu 12.10 on my laptop, but can't do anything other than login and logout from Ubuntu. I am trying to figure out the way to connect using my datacard (Reliance NetConnect Broadband) but no success. Gone through several posts in last 3 days without luck. 

It seems Ubuntu is useless if you do not have net connection during installation, because you can't install anything. Can't play music, can't do programming stuff until and unless you have net connection as it should load various packages to make this OS useful.

Can anyone help me in fixing this problem? Getting below error message

[COLOR=#000000]WVCONF: /root/.wvdial.conf[/COLOR]
[COLOR=#000000]GNOME PPP: Connecting...[/COLOR]
[COLOR=#000000]GNOME PPP: STDERR: --> WvDial: Internet dialer version 1.60[/COLOR]
[COLOR=#000000]GNOME PPP: STDERR: --> Cannot get information for serial port.[/COLOR]
[COLOR=#000000]GNOME PPP: STDERR: --> Initializing modem.[/COLOR]
[COLOR=#000000]GNOME PPP: STDERR: --> Sending: ATZ[/COLOR]
[COLOR=#000000]GNOME PPP: STDERR: --> Sending: ATQ[/COLOR]
[COLOR=#000000]GNOME PPP: STDERR: --> ReSending: ATZ
[/COLOR][COLOR=#000000]GNOME PPP: STDERR: --> [/COLOR]Modem not responding

Thanks
Gyanda

---

### Post by quarkhirad on 2013-06-07
Hey i tried this and it worked 

[http://ideasareimmortal.blogspot.in/2010/02/getting-reliance-netconnect-usb-modem.html](http://ideasareimmortal.blogspot.in/2010/02/getting-reliance-netconnect-usb-modem.html)

now after installing wvdial and linux-generic i typed dmesg in terminal from which i found my product id and vendor id. I then directly jumpeed to step 4. 


hope this helps

---

### Post by igodspeed on 2013-08-17
Check out what i have done [here]("http://ubuntuforums.org/showthread.php?t=2168403&highlight=reliance+netconnect"). I have has some sucess but i am still looking for a more permanent solution.

---

