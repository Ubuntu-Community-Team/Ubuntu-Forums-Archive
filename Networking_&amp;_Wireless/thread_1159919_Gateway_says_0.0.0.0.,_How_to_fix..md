---
title: "Gateway says 0.0.0.0., How to fix."
date: 2009-05-15
forum: Networking &amp; Wireless
---

### Post by thecapitalbama on 2009-05-15
I typed in my gateway address, and I just checked my routing table information and its says the gateways is 0.0.0.0. It says connected but does not go to web pages, could this gateway problem be it, if so, can someone tell me how to fix it where it doesn't say that? Thanks

---

### Post by bruno9779 on 2009-05-15
Could you paste also your private IP? 169.x.x.x? 192.x.x.x?
Are you giving a static IP to your connection?
Can you ping anything on your LAN?

---

### Post by thecapitalbama on 2009-05-15
> **bruno9779 said:**
> Could you paste also your private IP? 169.x.x.x? 192.x.x.x?
Are you giving a static IP to your connection?
Can you ping anything on your LAN? 192.168.1.1. If you mean static by me putting it in manually, then yes, but I can only ping me, don't know if will help but I use comcast internet and have a motorola router hooked to a netgear router.

---

### Post by bruno9779 on 2009-05-15
you should try to have an IP assigned by DHCP: it is the easiest solution by far

Alternatively, in the setup interface of your router you should have options to set the private IP of your Gateway (private range 192.168.x.x)

on a side note: Gateway is usually assigned to IPs finishing with .1, like 192.168.x.1, (derfault 192.168.48.1)
so if you need to force your IP use something like 192.168.1.11

---

### Post by thecapitalbama on 2009-05-15
> **bruno9779 said:**
> you should try to have an IP assigned by DHCP: it is the easiest solution by far

Alternatively, in the setup interface of your router you should have options to set the private IP of your Gateway (private range 192.168.x.x)

on a side note: Gateway is usually assigned to IPs finishing with .1, like 192.168.x.1, (derfault 192.168.48.1)
so if you need to force your IP use something like 192.168.1.11

Im not trying to sound to dum or ask too much, but how would I go about doing that.
DHCP, and setting the interface and stuff? Thanks

---

### Post by Peter09 on 2009-05-15
There appears to be a bug drifting around regarding this.

[https://bugs.launchpad.net/ubuntu/+source/dhcp3/+bug/307204](https://bugs.launchpad.net/ubuntu/+source/dhcp3/+bug/307204)

The fix seems to be
> 
Commenting out lines relating to rfc3442 in dhclient.conf fixed the issue as well.

---

### Post by bruno9779 on 2009-05-15
if you right-click on the connection icon, next to system clock, you can access preferences for your connection.

if you set IP to be assigned by DHCP (automatic), you do not have to set anything else: just choose your connection (if on wifi) and let it is done.

If you set IP to Manual, you must provide also a Gateway address and a subnetmask. You may need to give also DNS servers (depending on the ISP)

If you are unsure, just go with DHCP.

are you connecing wired, or wireless?

---

### Post by quad456 on 2010-01-30
> **bruno9779 said:**
> if you right-click on the connection icon, next to system clock, you can access preferences for your connection.

if you set IP to be assigned by DHCP (automatic), you do not have to set anything else: just choose your connection (if on wifi) and let it is done.

If you set IP to Manual, you must provide also a Gateway address and a subnetmask. You may need to give also DNS servers (depending on the ISP)

If you are unsure, just go with DHCP.

are you connecing wired, or wireless?

First of all a static IP is better than dynamic. That way you always know what your IP is if you want to VPN in to the computer or have a network share that you want to access from another computer. If it is dynamic you have to check your router or the Ubuntu machine itself to find that. Just another extra step to waste time.

Second I am having the same problem. I have setup Windows 7 and MacOS X on this netbook and also triple booting Ubuntu.

Setting a static IP is one of the basic things an OS should be able to do out of the box. This should work right off the bat. And it is not.

IP: 192.168.1.110
Netmask: 255.255.255.0
Gateway: 0.0.0.0 (supposed to be 192.168.1.1)

I am telling network manager to use 192.168.1.1 for gateway and it is not saving the setting. It returns 0.0.0.0

This sucks. If Ubuntu is really going to be an alternative for Windows or MacOS they have to get at least the basics right.

Now in 2010 Ubuntu / Linux is still not ready for the average user.

Sure I can figure this out by searching the net and there is probably some tweak or patch that needs to be installed. But WHY??? This is a fresh install and should work out of the box.

Another thing I don't like is I have a dual monitor setup with netbook screen sitting in front of 22" LCD. When I move a window from netbook screen to 22" above it snaps back to netbook screen when I release the mouse button. It will not allow me to drop it on the 22" screen. The only way I can make it stick to the 22" screen is by moving the window so it touches the top of the 22" screen and then waiting a second or so and then gently releasing the mouse button. Not good at all. I should be able to drop the window anywhere I want on any monitor at all times.

Dissapointed!

---

### Post by quad456 on 2010-01-30
Edit:

I was able to make it work by deleting the wired entry and first typing the gateway entry before adding netmask and ip address.

However the order should not matter.

Also noticed that regarding the windows snapping to the netbook screen that it must be by design. A quick mouse release will snap it to the screen but a small pause will drop it anywhere you want on multiple screens. I guess I could get used to that but would like to know if this behavior could be changed so it performs like other Operating Systems. Interestingly the Karmic Beta did not have this behavior. This seems to be new with Karmic Final.

Overall it seems to be working now and I like the new icons and wallpaper. VNC is also working nicely out of the box after enabling remote access.

One suggestion I have is that the login UI should be a little more polished. I'd like my logon screen resolution to be the same as the desktop resolution. Right now it defaults to a low resolution first. And the wallpapers change from default to some brown wallpaper that does not fill the whole screen and is justified to the top left and then finally once it logs on the customized user wallpaper. It does not look very professional. Is there a way to make this more consistent??

MacOS and Vista / Seven does not have these wallpaper issues.

I'd like to give Ubuntu the benefit of the doubt but really these are things that should have been sorted out by now.

---

### Post by xx58 on 2010-01-30
:rolleyes: Dear Quad456,
Don't cry, but ask help and you will have. If you don't know, then somebody will and help is always in this forum. OK.
Now answer to your question :
Under address
192.168.1.110 (very important) press[COLOR=Red] ENTER[/COLOR]
Under Netmask
255.255.255.0 (very important) press [COLOR=Red]ENTER[/COLOR]
Under Gateway
192.168.1.1 (very important) press[COLOR=Red] ENTER[/COLOR]
and everything will be just OK.
This Ubuntu Forum are place, where you can have always help. [COLOR=Red]Don't cry, ask help.[/COLOR]

---

### Post by Iowan on 2010-01-30
> **quad456 said:**
> First of all a static IP is better than dynamic. That way you always know what your IP is if you want to VPN in to the computer or have a network share that you want to access from another computer. If it is dynamic you have to check your router or the Ubuntu machine itself to find that. Just another extra step to waste time.A static lease from the DHCP server has many of the advantages of both. The machine gets the same address each time, and the DHCP server can pass along information about DNS servers, gateway, etc. If the machine (laptop?) is taken to another network, settings don't need to be changed to connect to a different DHCP-based network.
Of course, it won't solve the  problem of getting an address from a DHCP server...

---

### Post by Fr33d0m on 2010-08-19
Some of the responses to this are just ridiculous.  Quad456 is exactly correct that this is basic functionality and it is unforgivable that it doesn't work.  Why we use nm-applet after so many years of it failing to perform its most basic functions is a question that needs an answer from the top. Can we just get someone competent to develop it?  This is my last load of Ubuntu unless it comes up with a better solution.  And no, WICD is not the solution.  

That said to address several other comments. There are plenty of reasons to do either DHCP or static addressing depending on your specific needs and hardware. Some routers do not give you choices in managing DHCP leases. This is functionality that IS built into network manager but does not work.

---

### Post by LightSpirit on 2010-10-08
> **xx58 said:**
> :rolleyes: Dear Quad456,
Don't cry, but ask help and you will have. If you don't know, then somebody will and help is always in this forum. OK.
Now answer to your question :
Under address
192.168.1.110 (very important) press[COLOR=Red] ENTER[/COLOR]
Under Netmask
255.255.255.0 (very important) press [COLOR=Red]ENTER[/COLOR]
Under Gateway
192.168.1.1 (very important) press[COLOR=Red] ENTER[/COLOR]
and everything will be just OK.
This Ubuntu Forum are place, where you can have always help. [COLOR=Red]Don't cry, ask help.[/COLOR]

This worked for me, thx man ;-)

---

### Post by snakebob on 2011-01-14
> **quad456 said:**
> First of all a static IP is better than dynamic. That way you always know what your IP is if you want to VPN in to the computer or have a network share that you want to access from another computer. If it is dynamic you have to check your router or the Ubuntu machine itself to find that. Just another extra step to waste time.
 
Second I am having the same problem. I have setup Windows 7 and MacOS X on this netbook and also triple booting Ubuntu.
 
Setting a static IP is one of the basic things an OS should be able to do out of the box. This should work right off the bat. And it is not.
 
IP: 192.168.1.110
Netmask: 255.255.255.0
Gateway: 0.0.0.0 (supposed to be 192.168.1.1)
 
I am telling network manager to use 192.168.1.1 for gateway and it is not saving the setting. It returns 0.0.0.0
 
This sucks. If Ubuntu is really going to be an alternative for Windows or MacOS they have to get at least the basics right.
 
Now in 2010 Ubuntu / Linux is still not ready for the average user.
 
Sure I can figure this out by searching the net and there is probably some tweak or patch that needs to be installed. But WHY??? This is a fresh install and should work out of the box.
 
Another thing I don't like is I have a dual monitor setup with netbook screen sitting in front of 22" LCD. When I move a window from netbook screen to 22" above it snaps back to netbook screen when I release the mouse button. It will not allow me to drop it on the 22" screen. The only way I can make it stick to the 22" screen is by moving the window so it touches the top of the 22" screen and then waiting a second or so and then gently releasing the mouse button. Not good at all. I should be able to drop the window anywhere I want on any monitor at all times.
 
Dissapointed!
 
Now I am using Ubuntu desktop 10.10 and......it's network IP stupid thing is still same ..not improved.
 
I agree with you.

---

### Post by snakebob on 2011-01-14
> **quad456 said:**
> First of all a static IP is better than dynamic. That way you always know what your IP is if you want to VPN in to the computer or have a network share that you want to access from another computer. If it is dynamic you have to check your router or the Ubuntu machine itself to find that. Just another extra step to waste time.
 
Second I am having the same problem. I have setup Windows 7 and MacOS X on this netbook and also triple booting Ubuntu.
 
Setting a static IP is one of the basic things an OS should be able to do out of the box. This should work right off the bat. And it is not.
 
IP: 192.168.1.110
Netmask: 255.255.255.0
Gateway: 0.0.0.0 (supposed to be 192.168.1.1)
 
I am telling network manager to use 192.168.1.1 for gateway and it is not saving the setting. It returns 0.0.0.0
 
This sucks. If Ubuntu is really going to be an alternative for Windows or MacOS they have to get at least the basics right.
 
Now in 2010 Ubuntu / Linux is still not ready for the average user.
 
Sure I can figure this out by searching the net and there is probably some tweak or patch that needs to be installed. But WHY??? This is a fresh install and should work out of the box.
 
Another thing I don't like is I have a dual monitor setup with netbook screen sitting in front of 22" LCD. When I move a window from netbook screen to 22" above it snaps back to netbook screen when I release the mouse button. It will not allow me to drop it on the 22" screen. The only way I can make it stick to the 22" screen is by moving the window so it touches the top of the 22" screen and then waiting a second or so and then gently releasing the mouse button. Not good at all. I should be able to drop the window anywhere I want on any monitor at all times.
 
Dissapointed!
 
Now I am using Ubuntu desktop 10.10 and......it's network IP stupid thing is still same ..not improved.
 
I agree with you.

---

