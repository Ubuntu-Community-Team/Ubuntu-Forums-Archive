---
title: "VPN Help!!"
date: 2012-12-10
forum: Networking &amp; Wireless
---

### Post by robn30 on 2012-12-10
Ok so I am no Network Guru and this VPN stuff is really kicking my butt.  I do some travel abroad and want to be able to VPN into my home network and use its internet connection.  So far I have searched Google for a comprehensive guide to setting up a VPN and some of the stuff seems ok but I need a for dummies version that will work with Ubuntu 12.04.  I have seen a lot of stuff for OpenVPN and it seems the way to go but seems to be a bit of a pain to configure.  Maybe its just me but all the explanations seem to be a little complex.  Is this a difficult thing to do?  Or am I just getting overwhelmed and need to be shown a simpler way.  I know I need to setup a VPN Server and a Client.  I know that keys need to be generated to make the handshaking work.  The configuration of the whole thing is what is killing me.  I found this PDF [http://madisonlinux.org/InstallingOpenVPNOnUbuntu10.04?action=AttachFile&do=view&target=install_open_vpn_on_ubuntu.pdf](http://madisonlinux.org/InstallingOpenVPNOnUbuntu10.04?action=AttachFile&do=view&target=install_open_vpn_on_ubuntu.pdf) that seems to be a good guide but there is something wrong with the vars configuration that is messing me up.  Something about the openssl.cnf not pointing to the right location.  So if someone can help me I would greatly appreciate it.  I have spent way too much time trying to figure this out.  Thanks in advance.

---

### Post by alfa16vjtd on 2012-12-10
You could also use SSH port forwarding to your PC at home if that's a solution.

---

### Post by ZippyUbu on 2012-12-10
Hi,

Most VPN solutions are complex to setup and configure in my experience. If you choose OpenVPN then you should use public and private keys which make this setup more complex. Especially if you're not familiar with a lot of the terminology and processes.

Another solution is to use a different VPN that might be a little easier to configure; albeit not as secure as OpenVPN. Have a look at this post: [How to PPTP VPN]("http://silverlinux.blogspot.co.uk/2012/05/how-to-pptp-vpn-on-ubuntu-1204-pptpd.html")

Your modem/router might also support VPN connections that you may be able to use. You'll also need to make sure that you either have a static IP address or some sort of dynamic mapping in place in-case your IP changes when your away...

EDIT: You can use network manager in Ubuntu 12.04 to connect to a PPTP VPN Server.

--
Zu

---

### Post by robn30 on 2012-12-10
> **alfa16vjtd said:**
> You could also use SSH port forwarding to your PC at home if that's a solution.

I already have an SSH Tunnel setup that allows me to connect to my machine for remote desktop.  I don't think this will allow me to connect my remote machine to the internet will it?  If so I would need some information on that.  Normally I just SSH Tunnel then VNC for remote desktop connections.  I am looking to be able to connect from abroad to get around the outside the US IP issue.  I know VPN can do this but the setup is way more difficult than SSH.  SSH is totally easy.

---

### Post by alfa16vjtd on 2012-12-10
> **robn30 said:**
> I already have an SSH Tunnel setup that allows me to connect to my machine for remote desktop.  I don't think this will allow me to connect my remote machine to the internet will it?  If so I would need some information on that.  Normally I just SSH Tunnel then VNC for remote desktop connections.  I am looking to be able to connect from abroad to get around the outside the US IP issue.  I know VPN can do this but the setup is way more difficult than SSH.  SSH is totally easy.

With VPN there is not much that you can do more then with SSH. Do you wan't to forward your browser over the internet? Or do you wan't to use the local browser to use your internet connection at home?

---

### Post by robn30 on 2012-12-10
> **ZippyUbu said:**
> Hi,

Most VPN solutions are complex to setup and configure in my experience. If you choose OpenVPN then you should use public and private keys which make this setup more complex. Especially if you're not familiar with a lot of the terminology and processes.

Another solution is to use a different VPN that might be a little easier to configure; albeit not as secure as OpenVPN. Have a look at this post: [How to PPTP VPN]("http://silverlinux.blogspot.co.uk/2012/05/how-to-pptp-vpn-on-ubuntu-1204-pptpd.html")

Your modem/router might also support VPN connections that you may be able to use. You'll also need to make sure that you either have a static IP address or some sort of dynamic mapping in place in-case your IP changes when your away...

EDIT: You can use network manager in Ubuntu 12.04 to connect to a PPTP VPN Server.

--
Zu
So I tried the link and followed the directions but it doesn't take you all the way through from the client prospective.  I used the instructions to setup the pptpd server side but how do I connect.  I am hotspoting my phone to give it as shot and using my laptop as the client.  I would assume I use the Network Manager and select pptp connection under the VPN tab.  What do I put in the boxes to make the connection.  For example what do I put for Gateway? Also under the Advanced tab do I change anything? Lastly on my pptp server do I need to run anything to get it started after a reboot?  Thanks for any help, I would love to get this working.

---

### Post by robn30 on 2012-12-10
> **alfa16vjtd said:**
> With VPN there is not much that you can do more then with SSH. Do you wan't to forward your browser over the internet? Or do you wan't to use the local browser to use your internet connection at home?

I guess I would want to forward the browser, whatever is going to provide me the best experience.  Do I need to VNC to use my internet connection at home?  As I said that is what I do to help my folks with tech assist and to access my machines desktop.  I am still new to all this, so if SSH can do way more then I am not aware of all it can do.  So I am looking for the method that would provide me the best user experience from the client prospective as I may be in another country when using this service.

---

### Post by alfa16vjtd on 2012-12-10
> **robn30 said:**
> I guess I would want to forward the browser, whatever is going to provide me the best experience.  Do I need to VNC to use my internet connection at home?  As I said that is what I do to help my folks with tech assist and to access my machines desktop.  I am still new to all this, so if SSH can do way more then I am not aware of all it can do.  So I am looking for the method that would provide me the best user experience from the client prospective as I may be in another country when using this service.

[http://www.linux-tip.net/cms/content/view/302/26/]("http://www.linux-tip.net/cms/content/view/302/26/")

Or you can do x forwarding of your browser.
ssh -x ....

Even a vpn connection is possible.

---

### Post by robn30 on 2012-12-10
> **alfa16vjtd said:**
> [http://www.linux-tip.net/cms/content/view/302/26/](http://www.linux-tip.net/cms/content/view/302/26/)

Or you can do x forwarding of your browser.
ssh -x ....

Even a vpn connection is possible.

Did a google search for connecting Firefox through SSH and Bam, there it was, super easy.  I was able to SSH to my Fathers machine a whole state away and then configured my Firefox to proxy using SOCKS_v5.  Whats My IP then showed his IP.  This is fantastic, no need for VPN now, although I would still like to learn that as well.

---

### Post by ahallubuntu on 2012-12-10
I recommend you look into installing OpenVPN on your home router instead of on a Ubuntu computer.  The upside is, you don't have to leave a computer on all the time at home - the router is probably on anyway.  (You can wake up a Ubuntu box remotely too if it is in standby.)

The downside of the router approach is: your router must support OpenVPN.  I'm not sure any consumer router does out of the box, but if you can install the full version of DD-WRT (a Linux-based firmware) or Tomato or OpenWRT on it, you can run OpenVPN on the router - those firmwares have (many versions) OpenVPN built in.

If your router does not support DD-WRT or Tomato, one option is to get an old Linksys WRT54G or WRT54GL and use it just as a gateway + for OpenVPN and keep your existing wireless router.  You may be able to find one cheap.  If you get a WRT54G, get one that is version 4 or older; version 5 and newer won't support the full DD-WRT that includes OpenVPN.  A WRT54GS won't work, either.

The latest versions of DD-WRT has a fairly easy OpenVPN setup.  The trick is generating the keys and certificates and copying/pasting them to the right place.

I've installed OpenVPN on numerous DD-WRT routers as well as on a few Ubuntu 10.04 boxes.  Never done it with 12.04 .  I do find it easier with DD-WRT, actually.

---

### Post by alfa16vjtd on 2012-12-10
> **robn30 said:**
> Did a google search for connecting Firefox through SSH and Bam, there it was, super easy.  I was able to SSH to my Fathers machine a whole state away and then configured my Firefox to proxy using SOCKS_v5.  Whats My IP then showed his IP.  This is fantastic, no need for VPN now, although I would still like to learn that as well.

For openvpn

[http://openvpn.net/index.php/open-source/documentation.html]("http://openvpn.net/index.php/open-source/documentation.html")

---

### Post by robn30 on 2012-12-11
> **ahallubuntu said:**
> I recommend you look into installing OpenVPN on your home router instead of on a Ubuntu computer. The upside is, you don't have to leave a computer on all the time at home - the router is probably on anyway. (You can wake up a Ubuntu box remotely too if it is in standby.)
 
The downside of the router approach is: your router must support OpenVPN. I'm not sure any consumer router does out of the box, but if you can install the full version of DD-WRT (a Linux-based firmware) or Tomato or OpenWRT on it, you can run OpenVPN on the router - those firmwares have (many versions) OpenVPN built in.
 
If your router does not support DD-WRT or Tomato, one option is to get an old Linksys WRT54G or WRT54GL and use it just as a gateway + for OpenVPN and keep your existing wireless router. You may be able to find one cheap. If you get a WRT54G, get one that is version 4 or older; version 5 and newer won't support the full DD-WRT that includes OpenVPN. A WRT54GS won't work, either.
 
The latest versions of DD-WRT has a fairly easy OpenVPN setup. The trick is generating the keys and certificates and copying/pasting them to the right place.
 
I've installed OpenVPN on numerous DD-WRT routers as well as on a few Ubuntu 10.04 boxes. Never done it with 12.04 . I do find it easier with DD-WRT, actually.
 
Thats funny I am currently using a WRT-54GL with DD-WRT as a repeater bridge to allow my neighbor to share my network.  Is it still possible to use this as an entry point for OpenVPN?  The router connected to my modem is a TrendNet TEW-639GR which currently is not supported by DD-WRT.  The 639 has been a very solid router with N capability so i want to keep it as the main device if possible.  So if you have advice on how to configure the bridged 54GL that would be awesome.  As of now I have the SSH tunnel working and that is great but I would love to get the OpenVPN option working as well.  If anything just to further my knowledge and capability.  Thanks for the reply.

---

### Post by ahallubuntu on 2012-12-11
> **robn30 said:**
> Thats funny I am currently using a WRT-54GL with DD-WRT as a repeater bridge to allow my neighbor to share my network.  Is it still possible to use this as an entry point for OpenVPN?

Maybe.  Depends how your network is configured.  You could forward the VPN port (1194) from your modem to the WAN of the WRT54GL.  But if you get on the VPN, you'll be on the LAN of the WRT54GL (like your neighbor).  If that still allows you access back to your local network (it probably should - again, depends how you have set it up).

You might take a look at this guide: I used it the first time I set up an OpenVPN box on my DD-WRT router. 


[http://www.dd-wrt.com/wiki/index.php/VPN_(the_easy_way)_v24%2B](http://www.dd-wrt.com/wiki/index.php/VPN_(the_easy_way)_v24%2B)

FYI, you need to make sure your DD-WRT is the FULL version that includes OpenVPN.  The WRT54GL can handle it but you might have installed the smaller image.  To find out, login to your router and check the VPN section and see if OpenVPN is an option.

---

### Post by robn30 on 2012-12-11
> **ahallubuntu said:**
> Maybe.  Depends how your network is configured.  You could forward the VPN port (1194) from your modem to the WAN of the WRT54GL.  But if you get on the VPN, you'll be on the LAN of the WRT54GL (like your neighbor).  If that still allows you access back to your local network (it probably should - again, depends how you have set it up).

You might take a look at this guide: I used it the first time I set up an OpenVPN box on my DD-WRT router. 


[http://www.dd-wrt.com/wiki/index.php/VPN_(the_easy_way)_v24%2B]("http://www.dd-wrt.com/wiki/index.php/VPN_(the_easy_way)_v24%2B")

FYI, you need to make sure your DD-WRT is the FULL version that includes OpenVPN.  The WRT54GL can handle it but you might have installed the smaller image.  To find out, login to your router and check the VPN section and see if OpenVPN is an option.

I have the smaller version for sure I would have to reflash to the full version.  The way I have my network setup is the 639GR is connected directly to the Cable Modem.  The 54GL is then configured as a Wireless Repeater Bridge which connects to the 639GR wirelessly.  The 54GL has its own SSID for clients connecting to it, i.e. my neighbor, but it passes his signal on to the 639GR.  Not sure if you are familiar with this type of setup but it is awesome if you want to extend your network over much longer ranges.  The 54GL is a total kick butt unit, just wish it was wireless N capable.  So given what I have said, do you think it is at all possible to perform what you are proposing?

Edit: As a side note, if I connect my desktop to the 54GL by way of LAN Port 1, I am still able to SSH in from my laptop that is connected wirelessly to the 639GR.  So the port forwarding I have setup on the 639GR for SSH is correctly allowing entry and then routing the tunnel to the 54GL for connection to my desktop.  So I wonder if I port forward the correct ports of the 639GR to the subnet IP of the 54GL, if OpenVPN will work.  This a interesting thought, of course I am no network expert so this may be way out to lunch.

---

### Post by ahallubuntu on 2012-12-11
> **robn30 said:**
>   So given what I have said, do you think it is at all possible to perform what you are proposing?

I think it would work, but I would not recommend it given the way you have it set up.  That wireless connection from 54GL to your other router might give you a flakey VPN connection.

I have used repeaters like this a few times.  They are great solutions sometimes but I have not found them that reliable or giving good solid connections.

If I were you, I'd find another router that is DD-WRT capable.  Use that for OpenVPN or swap it for the 54GL repeater and use the 54GL (wireless disabled) as your gateway/firewall/OpenVPN server.

---

### Post by robn30 on 2012-12-11
> **ahallubuntu said:**
> I think it would work, but I would not recommend it given the way you have it set up.  That wireless connection from 54GL to your other router might give you a flakey VPN connection.

I have used repeaters like this a few times.  They are great solutions sometimes but I have not found them that reliable or giving good solid connections.

If I were you, I'd find another router that is DD-WRT capable.  Use that for OpenVPN or swap it for the 54GL repeater and use the 54GL (wireless disabled) as your gateway/firewall/OpenVPN server.

I think that is probably good advice.  I like the 639GR but it is definitely limited by not allowing DD-WRT.  I will look around for a router that allows DD-WRT.  Any recommendations as far as that goes?  The 54GL is so rock solid I have kept it on hand as a backup and just recently started using it as a repeater because I had to move the 639GR, which caused my neighbors signal strength to really bottom out.  Thanks for all the advice it will be very helpful.  At least for now I have the SSH Tunnel method working very well.

---

### Post by ahallubuntu on 2012-12-11
I've had good luck with a couple of different Asus routers.  Most of them seem to support DD-WRT - good because the stock firmwares are not known to be that great.  I have purchased a couple of Asus RT-N13U/B1 models for under $20 USD new (after rebate) in the last year.  One is my home firewall/router + N wireless.  It is very stable, hasn't been rebooted for months.  It supports the full DD-WRT with  OpenVPN - I use it all the time.  It is a very basic router with terrible front LEDs (hard to distinguish them), but who cares?  I just want a stable router I can run DD-WRT on.

---

