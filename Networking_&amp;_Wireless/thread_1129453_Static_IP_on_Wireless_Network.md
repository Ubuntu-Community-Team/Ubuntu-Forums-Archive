---
title: "Static IP on Wireless Network"
date: 2009-04-18
forum: Networking &amp; Wireless
---

### Post by BJ_Covert_Action on 2009-04-18
So I am attempting to setup my computer to have a static IP address on my router. I have a WRT54GS router that is running the dd-wrt firmware. Right now, I have the router configured to hand out only 5 IP addresses, 192.168.1.200-192.168.1.204. I have my XBOX 360 hardwired to my router on the IP address 192.168.1.204. My roomate's laptop logs onto a random IP Address whenever he connects to the network. My ubuntu computer also has been configured to just pick any available ip address whenever I connect wirelessly to the network. However, I would like to change that.

I am trying to force my ubuntu box to log onto the IP address 192.168.1.203 everytime I connect to the router wirelessy. I have tried a number of things, non of which seem to be working. 

First, I tried using the nm-applet 0.6.6 icon on my system tray to configure a static IP Address. If I go to the GUI interface that this little icon takes me to via the manual configuration button, I can see an option to unlock the wireless configuration for editing. Doing so, I go to the wireless connection properties and uncheck the roaming mode option box. I then continued to put in all of my network information into the appropriate spots (network name, Password Type, password, IP Address, subnet mask, and gateway address). Then, after clicking ok to back out of the wireless properties, I go to the DNS tab and input the appropriate DNS server (192.168.0.1). After clicking okay and closing the GUI, my wireless network disconnects and I can only reconfigure it to connect by setting it back to roaming mode.

So, try method 2. I did some sleuthing on how to configure ubuntu for a static IP address and found [ This website ](http://www.ubuntugeek.com/how-to-set-a-static-ip-address-in-ubuntu-810-intrepid-ibex.html). I followed the instructions on it with only one change. Rather than putting:
```

iface eth0 inet static

```
I put:
```

iface wlan0 inet static

```
since I was setting up a static IP for my wireless connection rather than my ethernet connection. After doing a network restart and rebooting my computer, my computer fails to connect to the router entirely. 

This led me to one other realization. If I boot my computer with an ethernet cable hardwired to my router, but then disconnect the ethernet cable, there appears to be no way (that I can find) to force my computer to search for a wireless connection, manually or automatically. Instead, to get a wireless connection, apparently I have to reboot my computer with no ethernet cable attached and let it pick up one automatically. This seems a bit excessive. Am I missing something here?

Anyways, all I am trying to do is make it so that when I connect to my router wireless, my ubuntu box will always attach to the same IP Address so that I can configure some port forwarding options on my router. My network info is as follows:

SSID: HackThis
Router IP: 192.168.1.1
Internet IP Connection on Router: 192.168.0.1
Desired Computer IP: 192.168.1.201

Can anyone help me figure this out?

---

### Post by chili555 on 2009-04-18
Is this a stationary desktop computer that does not get hauled down to the cyber cafe, university or coffee shop? If it is, you don't really need Network Manager and nm-applet and you may wish to remove them. Then:```
sudo gedit /etc/network/interfaces
```Amend the file to set up your static interface like this:```
auto wlan0
iface wlan0 inet static
address 192.168.1.[COLOR="Red"]206[/COLOR]
netmask 255.255.255.255.0
gateway 192.168.1.1
wireless-essid HackThis
```By the way, may I assume this is a typo?> Internet IP Connection on Router: 192.168.0.1
Desired Computer IP: 192.168.1.201If your router is on 192.168.[COLOR="Red"]0[/COLOR].x, it will never hand out an address in the 192.168.[COLOR="Red"]1[/COLOR].x range.

Also, I recommend static IP addresses *outside* the range of the DHCP server. That's why I suggest your desired address be x.206 or higher.

---

### Post by BJ_Covert_Action on 2009-04-18
First off, no, that was not a typo. When I say that the internet connection on the router is 192.168.0.1, I mean that is the modem IP address. However, the router itself establishes IP addresses in the 192.168.1.XXX range for any computers connected to it.

Secondly, I am a bit confused, I thought if I configured the router to only hand out IP addresses in the 192.168.1.200-192.168.1.204 range, then I would not be able to connect to it with any other IP address (like 192.168.1.206). On a guess, I am supposing that the DHCP range does not control the only IP addresses allowed on the router, just the automatically assigned ones?

Ans yes, this is a stationary desktop and I will likely be uninstalling the nm-applet soon.

---

### Post by BJ_Covert_Action on 2009-04-18
Well, apparently you can get a static IP outside of the DHCP table. Good to know. I am still a bit new at the networking manual configuration thing so, I am learning as I go.

As for your configuration settings, they worked like a charm. Thank you very much. I would like to point out, however, in case anyone else reads this thread looking for help, that I had to run the command:

```

sudo /etc/init.d/networking restart

```

To get my network to connect again after changing the configuration settings.

Thank you for the help. Do you happen to know of any good online resources for networking knowledge in general? I think having access to something like that would behoove me greatly...

---

### Post by chili555 on 2009-04-18
> I am supposing that the DHCP range does not control the only IP addresses allowed on the router, just the automatically assigned ones?Correct.> I will likely be uninstalling the nm-applet soon.As well as Network Manager, I hope.> Do you happen to know of any good online resources for networking knowledge in general? Not any that I am aware of, but I'm confident there are some. 

Good luck and have fun!

---

### Post by BJ_Covert_Action on 2009-04-18
Yeah, Network Manager and nm-applet, that's what I meant.

Thank You.

---

### Post by pparks1 on 2009-04-30
DHCP is simply a range within the IP network that will be handed out as dynamic addresses.  The rest of the addresses are completely usable and can be set statically on other devices.

---

