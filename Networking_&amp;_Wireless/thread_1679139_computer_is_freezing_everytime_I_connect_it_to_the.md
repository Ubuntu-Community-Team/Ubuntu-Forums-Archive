---
title: "computer is freezing everytime I connect it to the router"
date: 2011-01-31
forum: Networking &amp; Wireless
---

### Post by accoustika on 2011-01-31
hello, I'm using ubuntu studio 10.04, I'm trying to connect to the internet but everytime I connect the network card to my Linksys WRT54GS router, everything totally freezes leaving me with no option but to press the reset button and unplug the internet cable so that it can reboot. as long as the cable is plugged in, the computer remains frozen. this started happening after i installed the Network Manager from the ubuntu studio CD image. before i had installed it, no crash would occur but again, nothing wld happen so i wasn't able to connect to the internet. I googled the issue and I found that I should install the Network Manager. So i did this and resulted in the issue mentioned above.

any help would be most appreciated. thanks!

---

### Post by accoustika on 2011-02-04
Help anyone????

---

### Post by dmizer on 2011-02-04
How did you configure your network before you installed network-manager?

---

### Post by accoustika on 2011-02-04
i didn't configure anything, i just plugged the cable but nothing would happen. im really new to ubuntu so i'm pretty much clueless to it all. i think the problem is that my connection type is static IP while ubuntu uses DHCP. but the thing is that if i switch it to DHCP it won't work anymore. it's a never ending cycle!

---

### Post by accoustika on 2011-02-06
Hello, I need to connect to the internet using ethernet cable on my router. I'm using Ubuntu Studio 10.04, my router is Linksys WRT54GS. I need simple guidelines because I'm having problems when I connect the router to the network card, everything is freezing. I've already installed the network manager from the cd image and ever since I did so, I've been having these problems. But prior to that, nothing would happen when I used to plug in the cable.

---

### Post by dmizer on 2011-02-06
Do you have any ability to try a different network card?

Can you post the output of:
```
lspci
```

---

### Post by accoustika on 2011-02-06
well i only have one network card so i can't really try another one. but i'll try the code u gave me and see what the output is and i'll get back to u on that.
i've been told i need to patch my network drivers. does that make sense to u? do u know how i can do that?

---

### Post by registered2-5-2011 on 2011-02-06
is the router running dhcp server? most do by default, check all yout connections, make sure you have the routers WAN port connected to your modem or wherever your getting your internet connection from. and connect the pc to one of the LAN ports. when you plug it up it should automatically connect with network manager, or at least try (if it is not even attempting then you may have a bad cable) you can also connect to a dhcp server manually with...

```
dhclient eth0
```

---

### Post by accoustika on 2011-02-06
the WAN connection is static IP, if i switch it to Automatic Configuration -  DHCP it won't work anymore on my laptop on which I connect wirelessly. But my router has a DHCP server and it is enabled. I already have connected my network card to the router through one of the LAN ports but the second I do that my system freezes and I know it's not a cable problem because the cable is brand new. However when I once switched the connection type to DHCP in the router settings, the freeze stopped and the connection was recognized on my PC, BUT I couldn't connect anymore to the internet because the connection type from my ISP is Static IP based not DHCP. So what do you suggest I do?

---

### Post by registered2-5-2011 on 2011-02-06
When you enable dhcp server in the router it should only affect the LAN side of things. there is also a setting in there for your WAN side (where you can choose from pppoe, dynamic or static) but that should be set to whatever WAN connection type you have with your ISP. When you plug your nic in with dhcp enabled on your router you get an IP address but cannot surf or ping? If so then do this again and show me the output of ```
ifconfig
``` and also ```
netstat -r
``` and also ```
cat /etc/resolv.conf
``` then try connecting with the router set at static and do a ```
sudo ifconfig eth0 192.168.0.20 netmask 255.255.255.0
``` and ```
/sbin/route add default gw 192.168.0.1
``` and then edit the /etc/resolv.conf file to have this line ```
nameserver 4.2.2.1
``` good luck... if the whole box freezes when plugging the cable in then you may want to check out the hardware (reseat the card or whatever)

remember to adjust the ip's to match your routers e.g. set it to 192.168.1.20 if your routers ip is set to 192.168.1.1( and obviously set the gw in the same manner)

---

### Post by dmizer on 2011-02-06
> **accoustika said:**
> well i only have one network card so i can't really try another one. but i'll try the code u gave me and see what the output is and i'll get back to u on that.
i've been told i need to patch my network drivers. does that make sense to u? do u know how i can do that?

It's hard to say what needs to be done unless we know what kind of network card you have. The command I gave you earlier will tell us that information.

---

### Post by accoustika on 2011-02-07
My ethernet controller is: Realtek Semiconductor Co.,  RTL-8139/8139C/8139C+ (rev 10)

---

### Post by accoustika on 2011-02-07
in order for these settings to take effect, don't I need to be connected to the router? I already tried these codes without being connected but i wasn't allowed to change the gateway and the name server. the first ones i was able to change. but u have to understand that the second i plug the ethernet cable my system freezes. if it helps, my network card is Realtek RTL-8139/8139C/8139C+ and my router is Linksys WRT54GS. Thanks for your time.

---

### Post by registered2-5-2011 on 2011-02-07
> but u have to understand that the second i plug the ethernet cable my system freezes.

this looks loke a hardware issue. If you are able, power the machine off and unplug it from the wall. Then remove the network card(assuming that it is not an onboard nic) and reseat it blowing any dust or whatever out of the slot then power the machine back up and plug it into the router and try those settings. Note that those are two different situations in the settings, one is when the router has dhcpd enabled and the other is with no dhcpd. If your card is onboard(soldered on the motherboard) then you may have a faulty mobo. If still no luck after any of that, you should the box on a live cd in there and see if you are getting the same results.

---

### Post by dmizer on 2011-02-07
> **registered2-5-2011 said:**
> this looks loke a hardware issue. If you are able, power the machine off and unplug it from the wall. Then remove the network card(assuming that it is not an onboard nic) and reseat it blowing any dust or whatever out of the slot then power the machine back up and plug it into the router and try those settings. Note that those are two different situations in the settings, one is when the router has dhcpd enabled and the other is with no dhcpd. If your card is onboard(soldered on the motherboard) then you may have a faulty mobo. If still no luck after any of that, you should the box on a live cd in there and see if you are getting the same results.

I agree with the above. Your card is not an unusual card and should not be causing this problem. It is most likely a defective card.

Also, I merged your two threads. Please do not create multiple threads for the same problem as it causes you and others to do more work than necessary.

---

### Post by accoustika on 2011-02-07
if it is so a hardware issue as u said, then why did the freeze stop when i switched the WAN connection type on the router from static IP to automatic configuration - DHCP?? (however i couldn't connect to the internet anymore on my windows based laptop when i did so)

---

### Post by accoustika on 2011-02-07
IT WORKED!!! I dusted off the network card and switched it to another slot on the motherboard and now the internet is running!! :D I'm so happy you have no idea how long i've been trying to fix this issue! THANKS YOU GUYS, you're awesome!!

---

