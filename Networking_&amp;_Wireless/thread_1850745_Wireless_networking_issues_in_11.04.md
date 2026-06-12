---
title: "Wireless networking issues in 11.04"
date: 2011-09-27
forum: Networking &amp; Wireless
---

### Post by interacter on 2011-09-27
Hi all

I'm a complete Ubunutu noob and am having issues with connecting wirelessly to the net.

I've searched this forum and bookmarked a few useful looking pages, but they don't quite seem to match my situation...

I'm using an older Packard Bell desktop (most forum topics seem to concern laptops) which I have recently reformatted to escape the tyranny of Windows!

My WiFi connection is through a LinySys dongle which connects to a Belkin 54g router plugged into the cable connection.

When installing Ubuntu from USB, I can get a connection.  It takes two attempts but it works nicely.

However, as soon as Ubunutu downloads the immediate updates (I assume much the same as Windows updating itself on first boot), the connection goes.  I can see the wireless network but can I get a connection?

Spent about half an hour this morning playing with the security settings.  IP6 doesn't make a difference BUT when I assign an address (tried 192.168.0.9 as I don't think that should be used by anything) in IPv4, I can get a connection.

However, this connection does not allow any data through whatsoever!  It's connected but that is as far as it goes.

I've tried everything that I can think of from my time with Windows, but can't see anything obvious.  The update manager is going on about a modem update, but as I can't connect to the net, that's not going to happen!

Any advice you can give would be greatly appreciated.  I can't get a hard line to the PC where it's located, otherwise I would have tried that first!

Thank you!
Neil

---

### Post by NikolasKS on 2011-09-27
Hi Neil,
I don't know exactly the reason of the problem - (I'm a noob too :) ),
 but I can tell you what you have to do to possibly make it work (it works for me):

1) Go to  Menu: System > Administration > User and groups.
there you have to change your account type to "Administrator" (it must be "custom" by default.)
then click the "advanced settings" button and in the second tab "User Privileges", enable the
"connect to wireless and ethernet networks" option and exit

2) Right click on the wifi indicator on your taskbar and then click "edit connections", in the second tab
named "Wireless" you will see your wireless network name ,highlight it and then click the "edit" button 
and enable the bottom left checkbox "available to all users", then save and close.
You have to restart your system... ( I set the IPv4 to automaic HDCP )

I hope that works for you too...):P
( I apologize about my english but it's not my native language...)

---

### Post by grahammechanical on 2011-09-27
Hi and welcome to the forums.

NikolasKS has given some good advice. Does it work for you? If your wireless adapter can see networks then the adapter is recognized by Ubuntu and is working. In other words you already have a driver for it. This is always a good thing.

I have found that Network manager remembers network settings even those attempts that have failed and sometimes these failed attempts prevent making a connection.

If the advice in the previous post does not solve this, try removing/deleting the wireless connections that you have in Network Manager Edit Connections. Reboot and start again by selecting your network from the list given by Network manager. You will need to select the Mode which usually is Infrastructure and the Security or encryption setting which should be the same setting as being used by the Belkin router - WPA & WPA2 Personal usually works. And do not forget that the password is not your log in password but the pass phrase or wireless key to gain access to the router. I have made this mistake in the past. Network manager will do the rest.

Regards.

---

### Post by interacter on 2011-09-27
Hi guys

Thanks for the advice - will try it as soon as I get in later!

Will let you know how I go!

Neil

---

### Post by gandaran on 2011-09-27
> However, as soon as Ubunutu downloads the immediate updates (I assume much the same as Windows updating itself on first boot), the connection goes. I can see the wireless network but can I get a connection?
could be a driver update issue, check which channel is set on the router, if anything over 12 try set a lower one.
> Spent about half an hour this morning playing with the security settings. IP6 doesn't make a difference BUT when I assign an address (tried 192.168.0.9 as I don't think that should be used by anything) in IPv4, I can get a connection.
works with manually set IP? check if DCHP server is enabled on the router.

---

### Post by interacter on 2011-09-27
Hi all

Thanks for your advice - unfortunately it didn't work :(

Followed all of your steps (and have confirmed that the information held through the reboots) but no joy.

I can see the network, but just can't connect.  The install is currently sitting still trying to connected (WiFi indicator is 'scrolling') but with no joy.

I have changed my router channel to 6 (it was 13) but that hasn't seemed to help either!  

If there is anything else that you can suggest, I really would be grateful as I'm panning to use this as my main PC for work purposes!

Thank you
Neil

EDIT - Once again I can "connect" with an IP address under IPV4.  Am apparently connected at 48mb/s with a driver "rt2800usb".

It's giving me the IP address (which matches what the router thinks, a hardware address which again matches the router, subnet mask of 255.255.255.0 and a broadcast address ending in 255).
Interface is 802.11 WiFi (wlan0)

---

### Post by interacter on 2011-09-27
> **gandaran said:**
> could be a driver update issue, check which channel is set on the router, if anything over 12 try set a lower one.

works with manually set IP? check if DCHP server is enabled on the router.

I believe that the DCHP is enabled...

---

### Post by gandaran on 2011-09-27
> EDIT - Once again I can "connect" with an IP address under IPV4. Am apparently connected at 48mb/s with a driver "rt2800usb".
so the problem is fixed?
wireless adapters  with ralink chipsets sometimes load the wrong ralink module/driver, you just have to find out which one the adapter works with and blacklist the others, check the chipset model with
```
lsusb
```
and search the forum for 'ralink rt2800usb' (or the ralink chipset) threads there are plenty of them with instructions on how to blacklist and load the correct driver
[http://ubuntuforums.org/showthread.php?t=1256810](http://ubuntuforums.org/showthread.php?t=1256810)

---

### Post by NikolasKS on 2011-09-27
> **interacter said:**
> Hi all
EDIT - Once again I can "connect" with an IP address under IPV4.  Am apparently connected at 48mb/s with a driver "rt2800usb".

It's giving me the IP address (which matches what the router thinks, a hardware address which again matches the router, subnet mask of 255.255.255.0 and a broadcast address ending in 255).
Interface is 802.11 WiFi (wlan0)

I'm not sure.. but... If your connection  is working when you manually give an IP then maybe you can make this IP permanent for your wifi adapter trough the router's web interface. I think that is allowed only for wired connections but...you never know....:)
So, while you are connected go to your router's web interface and look at the DHCP client list ( the IP and MAC address  of your adapter must be on that list) and check if there is an option -usually a checkbox- that allows you to reserve the IP for the current device.

(I speak generally since i don't know your router's interface )

---

### Post by interacter on 2011-09-28
Morning both

A quick update - with a static IP assigned to the Ubuntu box, I get "connected" but not online.
The IP address is the same as that which is stored in the router and doesn't seem to change. 

Late last night I had a thought and pinged the router - 100% successful with a 5.09ms average.

So I'm now thinking that it is something in the router settings?  However I have checked everything that I can think of (passwords do indeed match!) and can not find anything that looks obvious. IP, MAC all addresses match the settings on the Ubuntu box.

The only thing that did come to mind is that I named this box the same as the Windows boxed that it replaced. Could this be a problem?

The final, final option from my router is to get the Ubunutu box through the firewall using the 'DMZ' feature - completely unrestricted net access.  Should I do this? Is it a good idea?


Thanks again!
Neil

---

### Post by interacter on 2011-09-28
Update - DMZ didn't make a blind bit of difference.

I also rebooted the router, just to see if that was a problem (has been on Windows installs before).  The IP address entry for the Ubuntu box has now disappeared from the router's DCHP list, even though the box still think that it is connected.

All very odd...

---

### Post by gandaran on 2011-09-28
have you checked the adapter chipset? maybe you need the rt2870sta driver loaded for your adapter and blacklist the rt2800usb.

---

### Post by interacter on 2011-09-28
> **gandaran said:**
> have you checked the adapter chipset? maybe you need the rt2870sta driver loaded for your adapter and blacklist the rt2800usb.

I'll have a look tonight - thanks! I assume I do that using your previous information?

---

### Post by interacter on 2011-09-28
Hi there

Right I've tried the lsusb command and the wireless line is as follows:

Bus 001 Device 004: ID 148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless adaptor.

I've had a look around the forum and am finding it quite confusing about how to blacklist some driver and run another (sorry for being a total noob).
Is there an idiot's guide somewhere?

Thank you!

(On a positive note I did work out how the file system works, ish, all by myself so I could force my Thunderbird profile in!!!)

---

### Post by interacter on 2011-09-28
I did find this : [http://ubuntuforums.org/showthread.php?t=1839151&highlight=ralink+rt2800usb&page=2](http://ubuntuforums.org/showthread.php?t=1839151&highlight=ralink+rt2800usb&page=2)

Post #14 seemed helpful - I found the blacklist.conf file but it's read-only. Saving a copy to my desktop then adding the blacklist command - can't copy it back into the original folder.

I've tried the sudo su commands in the Terminal window and it doesn't like them.
It also didn't like the gksu command either. Just said that it didn't recognise it.

I've also noticed that there are a few folders in the File System that I haven't got permission to get into.

I am an Administrator with every option ticked, so I would have thought that I'm all-powerful (or something)?

---

### Post by gandaran on 2011-09-28
> **interacter said:**
> I did find this : [http://ubuntuforums.org/showthread.php?t=1839151&highlight=ralink+rt2800usb&page=2](http://ubuntuforums.org/showthread.php?t=1839151&highlight=ralink+rt2800usb&page=2)

Post #14 seemed helpful - I found the blacklist.conf file but it's read-only. Saving a copy to my desktop then adding the blacklist command - can't copy it back into the original folder.

I've tried the sudo su commands in the Terminal window and it doesn't like them.
It also didn't like the gksu command either. Just said that it didn't recognise it.

I've also noticed that there are a few folders in the File System that I haven't got permission to get into.

I am an Administrator with every option ticked, so I would have thought that I'm all-powerful (or something)?
very simple, type in terminal
```
gksu gedit /etc/modprobe.d/blacklist.conf
```
this opens root gedit then add this line to the file in the bottom and save
```
blacklist rt2800usb
```
now reboot PC and check if the adapter works if not check if the rt2870sta driver is loaded using this command
```
lsmod
```
if not but if you find another driver instead (all ralink drivers begin with 'rt') you will have to blacklist it too.

---

### Post by NikolasKS on 2011-09-28
> **interacter said:**
> 
Post #14 seemed helpful - I found the blacklist.conf file but it's read-only. Saving a copy to my desktop then adding the blacklist command - can't copy it back into the original folder.


You can also edit files directly with gedit (but always keep a copy of the originals before you do it)
In a terminal, type: sudo gedit /"path"/"filename"

e.g. sudo gedit /etc/modprobe.d/blacklist.conf (in my case)

The file opens in the editor with write permissions.
Edit and save it :)

---

### Post by interacter on 2011-09-29
It works!

Thanks gandaran - I tried the gksu command before but it wasn't having it - today it worked like a dream!

I'm online at this very second!  

Thank you, too, NikolasK - will keep your suggestion for the future!

Many many thanks all - and thank you too for your patience!

Neil

---

### Post by NikolasKS on 2011-09-29
> **interacter said:**
> 
Many many thanks all - and thank you too for your patience!

Neil

U R welcome.. Anyway, that is the reason why this forum exists...:)

---

