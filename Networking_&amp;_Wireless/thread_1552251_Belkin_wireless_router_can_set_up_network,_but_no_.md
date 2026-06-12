---
title: "Belkin wireless router: can set up network, but no internet!"
date: 2010-08-13
forum: Networking &amp; Wireless
---

### Post by FreedomOverdose on 2010-08-13
Hello, 

I've been trying for a long time to set up a WLAN network at my home. I have a belkin wireless router, and I get my internet to my PC through a dsl modem. Instead of plugging the network cable from my modem to my PC, I've plugged it on my belkin router (to the uplink port) and using another cable, I've connected one of the belkin ports to my pc (since it doesn't have any wireless cards).

I can connect to the router, but not the internet! I can even see a WLAN network from my laptop, and I can connect to it, but I can't connect to the internet!

Any ideas?

Thanks

---

### Post by Kerubu on 2010-08-13
It's possible that your DSL modem cannot be used directly with your router but I could be wrong.

Post the model of your router and the modem and I'll google them.

---

### Post by FreedomOverdose on 2010-08-13
> **Kerubu said:**
> It's possible that your DSL modem cannot be used directly with your router but I could be wrong.

Post the model of your router and the modem and I'll google them.
Thanks for the reply. My modem is: speedtouch st536v6
and the wireless router: Belkin F5D6231

Thanks :D

---

### Post by Kerubu on 2010-08-13
I could be wrong, but looking for the Belkin router model you gave, isn't it a DSL modem as well ? i.e. configure the belkin router with your internet provider details and there is no need for the speedtouch modem (which I can't find a manual for on the internet)

Is this the belkin model ? :
[http://en-us-support.belkin.com/app/product/detail/p/422]("http://en-us-support.belkin.com/app/product/detail/p/422")

---

### Post by FreedomOverdose on 2010-08-13
> **Kerubu said:**
> I could be wrong, but looking for the Belkin router model you gave, isn't it a DSL modem as well ? i.e. configure the belkin router with your internet provider details and there is no need for the speedtouch modem (which I can't find a manual for on the internet)

Is this the belkin model ? :
[http://en-us-support.belkin.com/app/product/detail/p/422](http://en-us-support.belkin.com/app/product/detail/p/422)
I thought about that, but I can't plug in the cable from my isp directly into my belkin router, as the isp cable is kinda smaller (like phone cables)

---

### Post by Kerubu on 2010-08-13
Actually no, I've got that wrong. Your Belkin router is not a Modem as well.. (that's typical of Belkin.. rubbish descriptions of their products.. I'm not a fan of any of their products).

I can't really find a setup manual for your speed touch modem. Is there one on the CD that came with it ? (probably a pdy file)

Both your modem and router have the capability to run a DHCP server but you need only one on your network. It could be that both are enabled which you shouldn't have.

---

### Post by Kerubu on 2010-08-13
I found the manuals for your router and modem now.

It looks as though they use different subnets.. provided you haven't altered the defaults. If they are both acting as DHCP servers then they won't see each other either. You'll have to disable one DHCP server .. I'd suggest you disable your Belkin DHCP.. you'll have to read the manual to do this and you're best assigning it a fixed IP on your network that fits in with the subnet your MODEM provides.. which is 192.168.1.X (your Belkin works on 192.168.2.X)...You could assign a fixed IP of 192.168.1.71 to your Belkin so that you know what it is and get back into it should things go pear-shaped

---

### Post by FreedomOverdose on 2010-08-14
> **Kerubu said:**
> I found the manuals for your router and modem now.

It looks as though they use different subnets.. provided you haven't altered the defaults. If they are both acting as DHCP servers then they won't see each other either. You'll have to disable one DHCP server .. I'd suggest you disable your Belkin DHCP.. you'll have to read the manual to do this and you're best assigning it a fixed IP on your network that fits in with the subnet your MODEM provides.. which is 192.168.1.X (your Belkin works on 192.168.2.X)...You could assign a fixed IP of 192.168.1.71 to your Belkin so that you know what it is and get back into it should things go pear-shaped

Hey there

After debugging the modem's page javascript with firebug (as it wouldn't apply my configuration, javascript parsing errors -_-), I was able to change the DHCP status to off. After that, I changed the IP to something like 192.168.1.X. Then, not only I didn't have internet, but I couldn't open my router's page, even with the new IP!! I tried restarting both devices. Any ideas?

Thanks

---

### Post by smiles on 2010-08-14
> **FreedomOverdose said:**
> Hey there

After debugging the modem's page javascript with firebug (as it wouldn't apply my configuration, javascript parsing errors -_-), I was able to change the DHCP status to off. After that, I changed the IP to something like 192.168.1.X. Then, not only I didn't have internet, but I couldn't open my router's page, even with the new IP!! I tried restarting both devices. Any ideas?

Thanks

I've had this very same problem (different models - but same problem) just last night.

You may have to do a hard reset of one or both devices (there's usually a reset button that you need a paper clip or toothpick to push). This resets the device back to manufacturer defaults. Worst case scenario, you may even have to uninstall/reinstall your ethernet devices as well (I had to do this in Windows XP). 

Sometimes the modem doesn't have a reset button and so the power cord needs unplugged and the battery backup (if any) taken out for a minute or two. 

Also a reboot is sometimes needed as well in order to fully reconfigure the devices. You can usually escape the reboot, but if you've tried everything and it still isn't working, try rebooting and check again. 

Hope this helps!

~smiles

---

### Post by FreedomOverdose on 2010-08-14
> **smiles said:**
> I've had this very same problem (different models - but same problem) just last night.

You may have to do a hard reset of one or both devices (there's usually a reset button that you need a paper clip or toothpick to push). This resets the device back to manufacturer defaults. Worst case scenario, you may even have to uninstall/reinstall your ethernet devices as well (I had to do this in Windows XP). 

Sometimes the modem doesn't have a reset button and so the power cord needs unplugged and the battery backup (if any) taken out for a minute or two. 

Also a reboot is sometimes needed as well in order to fully reconfigure the devices. You can usually escape the reboot, but if you've tried everything and it still isn't working, try rebooting and check again. 

Hope this helps!

~smiles
Hey there

Thanks for the reply :)

I'm afraid I already tried all the above... :(. 

What in the world is possibly going on? :(

---

### Post by Kerubu on 2010-08-14
> **FreedomOverdose said:**
> Hey there

After debugging the modem's page javascript with firebug (as it wouldn't apply my configuration, javascript parsing errors -_-), I was able to change the DHCP status to off. After that, I changed the IP to something like 192.168.1.X. Then, not only I didn't have internet, but I couldn't open my router's page, even with the new IP!! I tried restarting both devices. Any ideas?

Thanks

OK if your not getting access to your modem's configuration page then the reset should bring it back to the default (this may mean having to set up your internet provider again using windows software)

 from what you've said it looks like you disabled your modem's DHCP and want to use your Belkin router as your DHCP server. In this case you need to comply with your Belkin network (which is 192.168.**2**.XXX). NOT 192.168.1.X

Whichever DHCP server you disable you need to fix the IP of the device with the disabled DHCP server to the subnetwork of the ACTIVE DHCP server OR if it has a setting to allow it to be assigned an IP by another DHCP server.

I suggested you disable your ROUTER DHCP server because you're not fiddling with something that will interrupt your internet connect (and access to help !)

---

### Post by FreedomOverdose on 2010-08-14
actually no. You've either misread, or I've miswritten anything. I've disabled the **router's** DHCP, and cannot access the **router**!

edit: and yes, I reset the router, but still, I've no internet... it dissapears when changing the ip... :(

---

### Post by Kerubu on 2010-08-14
Can you now access the router's config page and your modem's config page?

---

### Post by FreedomOverdose on 2010-08-14
yes for the router as I reset, and maybe for the modem (don't remember the pass -_-)

---

### Post by Kerubu on 2010-08-14
So you're back to your original setup... that is a local wireless network through your router but no internet? If you've reset your Modem you'll have to set it up again for your internet provider.

---

### Post by FreedomOverdose on 2010-08-14
yep, back to my original setup... that's why i dont wanna reset the modem, cause I have to reconf :(

---

### Post by Kerubu on 2010-08-15
I'm afraid I can't help you any more without seeing your setup. Unfortunately some of your information conflicts so I'm not entirely clear exactly what you did or tried. I can only suggest you read the manuals carefully and to learn a bit about networking etc and DHCP servers. There is no reason why you can't have the setup you want.

The alternative is to buy a combined modem/wireless/ethernet hub. 

One box.

---

### Post by FreedomOverdose on 2010-08-15
Ok, thanks for your help :)

I'll try my best, and I'll let you guys know how (if at all) I fixed the problem :)1

---

### Post by FreedomOverdose on 2010-08-17
right now I've managed to change DHCP to off on the belkin wireless router, and the IP to the modem's subnet BUT out of it's DHCP range. I can access the belkin wireless router (no internet though!), but I can't access my modem(btw, who's password I recovered)!!!

---

### Post by FreedomOverdose on 2010-08-18
FIXED!!

I should have selected PPPOE instead of dynamic connection, in the wireless router's config. However, if I turn DHCP off and assign an IP address in the same subnet as the modem, only one computer at a time will be able to be connected to the network! (or at least, maybe because I put them the same internal IP in the manual config). However, with the native settings (different subnet, dhcp on) everything works just fine :)

EDIT: **However**, my belkin router seems to support WEP encryption only?! WTF?! Isn't that really old and reeally unsafe?! It takes just a few minutes to crack with aircrack... :(

---

