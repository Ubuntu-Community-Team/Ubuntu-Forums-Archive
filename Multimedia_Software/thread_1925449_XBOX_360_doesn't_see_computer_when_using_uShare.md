---
title: "XBOX 360 doesn't see computer when using uShare"
date: 2012-02-14
forum: Multimedia Software
---

### Post by matbluvenger on 2012-02-14
Hey all, I'm very new to Ubuntu but I'm somewhat familiar with Linux/Unix. However I have a problem and after searching around the only solutions I've found are for much old versions of Ubuntu or solve the firewall problem. Mine is a bit different.

I recently got rid of Windows forever (finally) and switched completely over to Ubuntu 11.10. However, to my dismay, Vuze doesn't connect automatically to my XBOX 360 for streaming videos. So I decided to give uShare a try. After many many attempts and tweaks my XBOX 360 still won't list my computer in the "Videos" section. 

Is there something I'm doing wrong or is there a way to tweak Vuze to get it to work? Thanks in advance for any help!

USHARE_NAME=rafferty-desktop
USHARE_IFACE=wlan0
USHARE_PORT=49200 (I've tried 49153 per suggestion as well)
USHARE_TELNET_PORT=
USHARE_DIR=/home/rafferty/Videos
USHARE_OVERRIDE_ICONV_ERR=
USHARE_ENABLE_WEB=YES
USHARE_ENABLE_TELNET=NO
USHARE_ENABE_XBOX=YES
USHARE_ENABLE_DLNA=NO

---

### Post by Derek Karpinski on 2012-02-14
I think the update Microsoft pushed out to the XBox late last year has pretty much eliminated any sharing with anything but Windows Media Center.
 
I could be wrong though.

---

### Post by matbluvenger on 2012-02-14
> **Derek Karpinski said:**
> I think the update Microsoft pushed out to the XBox late last year has pretty much eliminated any sharing with anything but Windows Media Center.
 
I could be wrong though.

Nah, just two weeks ago I was streaming from Vuze on Windows 7.

---

### Post by matbluvenger on 2012-02-15
*bump* Any suggestions?

---

### Post by matbluvenger on 2012-02-25
*bumpity* Really, nobody has a solution?

---

### Post by mtalexan on 2012-03-11
If you check xbox.com, there's a big to-do over there about whether Xbox stopped support for being a DLNA media renderer (client).  If you've got the newer updates for it, it appears that they did in fact disable that function.  I had the same problem as you, but I also couldn't get my Windows machine based DLNA server to show up either.

---

### Post by Rorke on 2012-04-21
I'm new to Xbox - I was dismayed to receive the 'Microsoft Windows Media' not detected message!
Anny ideas how I can keep M$ out of my home, but still enjoy my Xbox?
I have an Xbox 360 Slim - I am very seriously considering buying an after market HDD and an Xk3y, or similar.
Any thoughts?
Thanks in aadvance

Simon

---

### Post by BigCityCat on 2012-04-21
I was able to get media playing on xbox360 from ubuntu 12.04 by installing rygel and rygel-tracker from synaptic.

Steps I used. 

Turn off Firewall.

run rygel in the terminal once by typing rygel in terminal.

Open file browser right click on your music folder and tag it. 

Then you can add rygle to startup applications by opening startup applications program=rygle command=rygel.

Dont look to see if xbox360 sees pc. It doesn't but just open music or video player with xbox and select media at the bottom.

I can not run any of this with the firewall enabled.

---

### Post by BigCityCat on 2012-04-21
Well it is seeing my pc now.

---

### Post by syerges on 2012-05-06
Mine only works on both XBox 360 and playstation 3 with the following settings exactly...if i change any of them, then it stops working.
USHARE_OVERRIDE_ICONV_ERR=yes
USHARE_ENABLE_WEB=yes
USHARE_ENABLE_TELNET=no
USHARE_ENABLE_XBOX=yes
USHARE_ENABLE_DLNA=no


The enable_dlna really messed me up because it says ps3 won't work without it, but it's wrong. also make sure to look up your xbox and ps3 ip addresses and open up the port to them from your pc.

My computer's IP address was found by right clicking on my internet connection and then clicking on "connection information" and it is 192.168.0.11

My Xbox and PS3's IP addresses were found by going to network settings, they are 192.168.0.10 and 192.168.0.13 so I had to use the following codes in terminal. sorry, don't know how to do that code thing here....

I used the same port as you so you shouldn't have to change that number.

sudo ufw allow proto tcp from 192.168.0.11 to 192.168.0.10 port 49153
sudo ufw allow proto tcp from 192.168.0.11 to 192.168.0.13 port 49153

---

