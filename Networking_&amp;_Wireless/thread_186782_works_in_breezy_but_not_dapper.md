---
title: "works in breezy but not dapper?"
date: 2006-06-02
forum: Networking &amp; Wireless
---

### Post by medz on 2006-06-02
hi i have a us robotics pci wifi card with texas instrument acx111 chipset....from fresh install of breezy it works sraight out of the box, perfectly. i downloaded and installed a fresh install of dapper and the wifi card doesnt work...it is detected on network manager and device manage and says active and i configured it but doesnt seem to be connecting.

damn i prefer the old installation method in breezy where everything is configured text


some one help please

---

### Post by geoizo on 2006-06-02
Got the same problem with same card, i configure everything but it seems not to be working. Any idea what to do?

---

### Post by robert114 on 2006-06-02
We'll i'm in the same situatiation with my US Robotics

My dmesg is full of errors like:
 wlan0: warning: peer 00:00:FF:FF:FF:FF is on channel 0 outside of channel range of current regulatory domain - couldn't join even if other settings match. You might want to adapt your config

i also noticed this in my dmesg:
[4294699.051000] acx: firmware 'Rev 2.3.1.31' does not work well with this driver
[4294699.051000] acx: form factor 0x01 ((mini-)PCI / CardBus), radio type 0x16 (Radia), EEPROM version 0x05, uploaded firmwar$[4294699.051000] acx v0.3.21: net device wlan0, driver compiled against wireless extensions 19 and Linux 2.6.15-23-k7

I've also found information about this bug here:
[https://launchpad.net/distros/ubuntu/+source/linux/+bug/26703](https://launchpad.net/distros/ubuntu/+source/linux/+bug/26703) but i don't understand it so if somebody could explain it. that would be very nice

---

### Post by robert114 on 2006-06-02
WEll ive got my card working with the use of this post

[http://www.ubuntuforums.org/showthread.php?t=183031&highlight=acx111+dapper]("http://www.ubuntuforums.org/showthread.php?t=183031&highlight=acx111+dapper")

The firmware is on your pc you should make a link in /lib/firmware/2.6.15-23-686/acx/default
to ../1.2.0.34/tiacx111c16 

you've got to use the .34 verion at first the driver didn't work for me but after i replaced my card the link went perfctly up!

succes I'll monitor this forum for further questions or improvements

edit:

I switched to an other version of firmwere because i did receive a lot of tx errors and my card might be to hot!!
the version i now use is 1.2.0.30 

**[COLOR="Red"]what ever you change watch dmesg for errors before you frie you card![/COLOR]**

---

### Post by robert114 on 2006-06-02
well the card still doesn't work when i boot my system but it only works after i reconnect my wireless device... maybe you folks should try this

---

### Post by durableapostle on 2006-06-02
Same problem here.

It seems that it is not a driver issue, as I can scan for networks, etc.  I really have no idea what I'm talking about, but is it possible that the driver is not loading?

My card (linksys WPC54G v2) worked well in Breezy, but was killed D-E-D dead in Dapper.

Any ideas on the driver not loading?

---

### Post by robert114 on 2006-06-03
maybe the driver isn't loading very well... but i'm not sure about this because i've been f*cking around with the driver... 

can the others confirm that reatach the device will make Ubuntu loading the driver?

---

### Post by OizOx on 2006-06-03
still no solution for this?:confused: :confused:

---

### Post by robert114 on 2006-06-04
another link: [http://www.ubuntuforums.org/showthread.php?t=75448&page=3](http://www.ubuntuforums.org/showthread.php?t=75448&page=3) 

This is what (i think worked for me)

1 place this line "options acx firmware_ver=1.2.1.34"in /etc/modprobe.d/options
[PHP]sudo nano /etc/modprobe.d/options
add line: options acx firmware_ver=1.2.1.34
hit ctr x and save the file[/PHP]

2. reboot machine or reload acx module
2.1 reload acx module 
[PHP]sudo rmmod acx
sudo modprobe acx[/PHP]

please report your results here... i'm not sure wheater i have been complete in my small howto because i've messed around!

---

### Post by durableapostle on 2006-06-04
this worked... for now.  let's see what happens after reboot (gulp!)....

---

### Post by durableapostle on 2006-06-04
yeah baby! still works after restarting X.

robert114 you are the bombizzle!

---

### Post by robert114 on 2006-06-05
does your card also work after a reboot, it doesn't here :-k

---

### Post by durableapostle on 2006-06-05
yep. works like a champ... both restarting X and a full system reboot/shutdown--

it's odd that yours is not...  maybe configure so that the changes load at startup?  That's how I had to fix my screen resolution issue...

---

### Post by robert114 on 2006-06-05
well, i'm glad it works for you :wink: 

I've created a script for my mother witch she will use to automaticly reload the acx kernel module

---

### Post by jolzee on 2006-06-11
Fantastic works a treat for me. :-D  Thanks robert114

---

### Post by apoth on 2006-10-07
The options line worked for a Netgear WG311 v2 for me. How the hell anyone's supposed to work out they need that line though is beyond me...

---

### Post by Llewxam on 2006-10-07
> **durableapostle said:**
> Same problem here.

It seems that it is not a driver issue, as I can scan for networks, etc.  I really have no idea what I'm talking about, but is it possible that the driver is not loading?

My card (linksys WPC54G v2) worked well in Breezy, but was killed D-E-D dead in Dapper.

Any ideas on the driver not loading?

same with me. same card except v3. it's really getting on my nerves. i was hoping ndiswrapper would be the last thing to give me trouble](*,)

---

