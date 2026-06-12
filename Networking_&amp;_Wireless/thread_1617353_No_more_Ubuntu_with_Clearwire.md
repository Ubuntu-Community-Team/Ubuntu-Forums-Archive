---
title: "No more Ubuntu with Clearwire"
date: 2010-11-09
forum: Networking &amp; Wireless
---

### Post by egkeat on 2010-11-09
Looks like I can't use it after talking with Clearwire (I have a wired modem connect to a router) they say they're not compatible with Ubuntu. My router sees the connection but the network manager doesn't, as though something else is blocking out the connection. I had tried just about everything but nothing works. I still like Ubuntu but looks like I'll have to use it without internet, therefore I'll have to keep dual boot until things change.

---

### Post by chili555 on 2010-11-09
I think Clearwire is really saying that they do not have Linux-knowledgeable technicians on staff and, because of the small marketplace, less than 3%, they are not going to hire any. I have used Linux for ten years in a variety of locations and have never been unable to connect.

If your router sees the modem and gets an IP address from it, then I am confident we can get your computer to connect. Please help me understand more details. Is this your setup?

===internet==>modem==>router==>ubuntu computer(s)

Is this a DSL modem? They generally require a user name and password to connect. In my experience, the authentication is generally better accomplished in the router. Please see attached.

Once that's done, your Ubuntu computer should see a normal ethernet connection with no special configuration.

Please be sure the modem is connected to the **W**AN port on the router and the computer(s) are attached to LAN ports.

Post back and we'll get you going.

---

### Post by egkeat on 2010-11-09
Hi Chili555,

That is my setup and you all have been very helpful in trying to assist me with this problem but it seems the same thing keeps happening no matter what.

Not good at explaining this so bear with me...

I am on an HP Pavilion desktop connected via ethernet. My router shows the connection, and everything else seems to work except the network manager constantly showing network disconnected.  I've checked and unchecked the box over and over with no results there.

When I go into the network.state file, it shows all entries set at true. In the network manager (or tools, I forgot which one as I am in Windows now), I see "multicast" disabled on eth0. In network manager, there is no eth0, only "lo."  

I have just recently upgraded to 10.10, and it was working until I played a game, the game froze, and I had to restart the computer.  Before upgrading, the net connection would do the same (whenever I either restarted or went back into Windows) then somehow magically start working again.

Now, I have some problems as well in Windows, as the connection drops from internet to "local" all the time, but in Windows, the connection always returns when I open a browser. I don't know if this is a problem with my ethernet port or what, but it sure does make me want to give up on using the internet in Ubuntu.
:(

---

### Post by chili555 on 2010-11-09
Let's take a look at your ethernet settings. Since the internet is not working over on Ubuntu, let's create a zip file with all the important data and perhaps you can transfer it on a USB key so you can post it here as an attachment to your reply. In Ubuntu, open Applications > Accessories > Terminal and do:```
sudo ethtool eth0 > egkeat.txt
ifconfig eth0 >> egkeat.txt
sudo lshw -C network >> egkeat.txt
dmesg >> egkeat.txt
zip egkeat.zip egkeat.txt
```In your home directory, you will find a file called egkeat.zip. Please attach it to your reply.

Is the PPPoE authentication set up in the router as I suggested?

Are you starting to suspect a problem with the ethernet card? Are you open to replacing it if that turns out to be the case?

---

### Post by pricetech on 2010-11-09
It does look like your Ubuntu install is "losing" your NIC, perhaps due to the NIC failing.

It also appears, however, that your Internet connection is timing out.  That may well be the nature of your connection with your ISP, so there may not be any "fix" for that.

Bottom line is your router is connected to the Internet through the modem and it doesn't care what's connected to its LAN ports.

---

### Post by egkeat on 2010-11-09
> **chili555 said:**
> Let's take a look at your ethernet settings. Since the internet is not working over on Ubuntu, let's create a zip file with all the important data and perhaps you can transfer it on a USB key so you can post it here as an attachment to your reply. In Ubuntu, open Applications > Accessories > Terminal and do:```
sudo ethtool eth0 > egkeat.txt
ifconfig eth0 >> egkeat.txt
sudo lshw -C network >> egkeat.txt
dmesg >> egkeat.txt
zip egkeat.zip egkeat.txt
```In your home directory, you will find a file called egkeat.zip. Please attach it to your reply.

Is the PPPoE authentication set up in the router as I suggested?

Are you starting to suspect a problem with the ethernet card? Are you open to replacing it if that turns out to be the case?


sudo ethtool resulted in "ethtool not found" or something like it.

Anyhow, here is the .zip.

I don't think I've set up PPPoE correctly in the router. 

Thanks for your help.

---

### Post by chili555 on 2010-11-09
Here is the first problem. Let's try to fix it and hope all the remaining issues are, in turn, solved.> NetworkManager: page allocation failure. order:3, mode:0x4020I am Googling...

Edit: It's a known bug: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/605045](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/605045)

Edit: It may be interaction between the driver module r8169 and Network Manager: [https://bugzilla.redhat.com/show_bug.cgi?id=566389](https://bugzilla.redhat.com/show_bug.cgi?id=566389)

---

### Post by chili555 on 2010-11-09
Please try:```
sudo rmmod -f r8169
sudo modprobe r8169
sudo lshw -C network
```Is the  *-network DISABLED still showing?> I don't think I've set up PPPoE correctly in the router.Can you get into the router's administration pages and fix it?

---

### Post by egkeat on 2010-11-09
*-network disabled still showing...

---

### Post by chili555 on 2010-11-09
Please go to System > Preferences > Startup Applications and uncheck Network Manager. Reboot. Just to be sure, run:```
ps aux | grep -i network
```Is Network Manager stopped; that is, not listed? Now recheck for DISABLED. If it does not appear, then run:```
sudo dhclient eth0
```Any improvement?

See you tomorrow. Good night.

---

### Post by egkeat on 2010-11-10
Still nothing...but this:

SIOCSIFFLAGS: Cannot allocate memory

and this:
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER of 192.168.1.3 from 192.168.1.1
DHCPREQUEST of 192.168.1.3 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.3 from 192.168.1.1
bound to 192.168.1.3 -- renewal in 32964 seconds.

Now I'm getting somewhat haunted by this....

Last night when I logged back into Ubuntu, it started checking disk for errors, then my wallpaper had white lines running all through it and most of the icons didn't display correctly.

---

### Post by chili555 on 2010-11-10
> bound to 192.168.1.3 -- renewal in 32964 seconds.If you got an IP address from the DHCP server, that is, the router, then you are connected.

Can you open Firefox and get web pages?

---

### Post by egkeat on 2010-11-10
No, I can not.  The router shows a connection yet does not flash as it would when connected in Windows, and cannot connect to webpages at all.

---

### Post by chili555 on 2010-11-10
In a terminal, do:```
ping -c3 192.168.1.1
ping -c3 74.125.229.18
```Can you access the router's administration pages by opening, in Firefox, [http://192.158.1.1?](http://192.158.1.1?) Does the router have an external IP address? Here is a sample from mine.

If you do not have an IP address in the router, I suspect you must correct your user name and password and reboot the router. You will know you are successful when the router gets an IP address.

---

### Post by egkeat on 2010-11-10
Yes, the router is just fine. No problems getting in there. The problem seems to be somewhere in during boot of Ubuntu. That's where it loses internet, Ubuntu network manager seems frozen at disabled.

---

### Post by chili555 on 2010-11-10
> The problem seems to be somewhere in during boot of Ubuntu.Let's see if there are any interesting messages. Please run and post:```
dmesg | grep eth
```This may or may not give us a clue about what's going wrong. We can run other tests if not.

What about the ping tests? Does your router have an external IP address?

---

### Post by egkeat on 2010-11-10
here's from dmesg:

[    0.784140] r8169 0000:02:00.0: eth0: RTL8168c/8111c at 0xf80e2000, (mac address), XID 1c2000c0 IRQ 42

Anything there?

---

### Post by chili555 on 2010-11-10
Not much. I assume Network Manager is still disabled. Let's see:```
dmesg | grep 8169
```

---

### Post by egkeat on 2010-11-10
Here it is: 

  0.742703] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    0.742744] r8169 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.742836] r8169 0000:02:00.0: setting latency timer to 64
[    0.743011] r8169 0000:02:00.0: irq 42 for MSI/MSI-X
[    0.743572] r8169 0000:02:00.0: eth0: RTL8168c/8111c at 0xf807e000, (mac address), XID 1c2000c0 IRQ 42
[   33.589147]  [<f80715ff>] rtl8169_rx_fill+0x9f/0x1c0 [r8169]
[   33.589152]  [<f8071fc5>] rtl8169_init_ring+0x65/0xa0 [r8169]
[   33.589157]  [<f8072609>] rtl8169_open+0xd9/0x410 [r8169]

---

### Post by chili555 on 2010-11-10
> rtl8169_rx_fillSearching keeps coming back to bugs like this: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/655413](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/655413)

As you can see, the latest response is only a couple of days old. I can't find any solution.

I have seen several posts that say they have downloaded r816[COLOR="Red"]8[/COLOR] from RealTek but that it doesn't solve the problem.

Is it time to think about a newer (non-RealTek) card for your computer? I am almost always against solving a problem by throwing money at it, but I am not sure there is another solution.

I am certain that Clearwire is not the problem.

---

### Post by egkeat on 2010-11-10
Well, I kinda figured it might come down to that. I can't do anything about the setup...the ethernet is built right into the motherboard and I'm really not able to go out and purchase another.  Oh well, guess I'll just have to try the download and see if that helps at all.

Thanks so much for trying to help.

---

### Post by chili555 on 2010-11-10
I am subscribed to the thread, so post back if I can help you further. Sorry I could not have been of more help.> I'm really not able to go out and purchase another. Is a PCI ethernet card in the budget? There are lots available on line at US$10 or so, although I'd investigate its chipset before buying.

---

### Post by egkeat on 2010-11-10
All right, I'll sure check it out and see if there's anything doable on this. Believe me you've been a lot of help. I'll let you know how it turns out.

---

### Post by egkeat on 2010-11-14
As a total newbie with Linux, I found myself unable to do anything about this on my own other than uninstalling 10.10 and reinstalling 10.04 from .iso.  Now I'm connected (as least as long as I don't boot into Windows.....haven't tried that yet).  Hope I'm able to catch on to this sometime soon. Windows is starting to hurt my eyes. Ubuntu is a much more suitable operating system as far as being user-friendly and the overall looks of the desktop. That's just my opinion

---

