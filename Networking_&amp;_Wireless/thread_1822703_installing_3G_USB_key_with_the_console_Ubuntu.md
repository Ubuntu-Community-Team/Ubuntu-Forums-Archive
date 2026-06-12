---
title: "installing 3G USB key with the console Ubuntu"
date: 2011-08-10
forum: Networking &amp; Wireless
---

### Post by wael.day on 2011-08-10
Hello, the problem is: because I wanted to replace Gnome by KDE, I made a fatal fault: I deleted Gnome without installing KDE previously, thus i'm in console mode. Some friends proposed me this apt-get install kde command but that does not work because I have no internet connection, my question is: how to install my key 3G Orange by using the console?
Thank you in advance

---

### Post by TechSupportx86 on 2011-08-10
You don't have access an ethernet connection? Or wireless?

Both can be setup via the command line and are quite simple

---

### Post by nmaster on 2011-08-10
> **TechSupportx86 said:**
> You don't have access an ethernet connection? Or wireless?

Both can be setup via the command line and are quite simple

i agree.  even if you don't have a personal wifi connection, just go to a coffee shop or public library.  follow these steps:

[http://www.ghacks.net/2009/04/14/connect-to-a-wireless-network-via-command-line/](http://www.ghacks.net/2009/04/14/connect-to-a-wireless-network-via-command-line/)

---

### Post by wael.day on 2011-08-10
> **nmaster said:**
> i agree.  even if you don't have a personal wifi connection, just go to a coffee shop or public library.  follow these steps:

[http://www.ghacks.net/2009/04/14/connect-to-a-wireless-network-via-command-line/](http://www.ghacks.net/2009/04/14/connect-to-a-wireless-network-via-command-line/)

thanks for this solution, it is really usefull, but the problem that i just want to connect my laptop with the 3G key, is there any solution?
if not, thanks for the help :)

---

### Post by TechSupportx86 on 2011-08-11
lol, well let's not get ahead of ourselfs there Eager McBeaver. Even if we did get the 3G working, you wouldn't be able to use the internet very well from just the terminal (plus the KDE Desktop package is quite large and would take massive amounts of your 3G data just to install, not to mention it would be _***HORRENDOUSLY***_ slow).

I am willing to bet the 3G key is going to need a driver of some sort, which is most likely gonna have to be downloaded... And since you are going to install KDE Desktop anyhow, we might as well do that first to make this process 1000X easier.

All you need to do is connect to a Wi-Fi network or use an Ethernet Cable. After you establish a connection to the internet, run the apt-get command to install KDE (This is going to take about 15-20 minutes depending on your internet speed). Once it's installed we can focus on getting the 3G working.

So, Step 1: Plug in an ethernet cable or connect to a wifi network. Once that's done we get started ;)

---

### Post by wael.day on 2011-08-11
> **nmaster said:**
> i agree.  even if you don't have a personal wifi connection, just go to a coffee shop or public library.  follow these steps:

[http://www.ghacks.net/2009/04/14/connect-to-a-wireless-network-via-command-line/](http://www.ghacks.net/2009/04/14/connect-to-a-wireless-network-via-command-line/)
hi, i tried to connect on a wireless network of a friend of mine and i submitted the command you've told me but this is the problem:

Error for wireless request "SET ESSID" (8B1A):
    SET failed on device wlan0: operation not permitted.

please help :(

---

### Post by TechSupportx86 on 2011-08-11
Try:

```
*sudo iwconfig wlan0 essid NETWORK_ID key WIRELESS_KEY*
```

Edit: Actually can you post the out put from **ifconfig** , That would probably help.

---

### Post by wael.day on 2011-08-11
> **TechSupportx86 said:**
> Try:

```
*sudo iwconfig wlan0 essid NETWORK_ID key WIRELESS_KEY*
```

Edit: Actually can you post the out put from **ifconfig** , That would probably help.

my friend's wireless is:
ESSID: "chiha wifi" and his keypass is 12345
so i wrote:
sudo iwconfig wlan0 essid chiha wifi key 12345 
but it didn't work, the same error!!!
help please :(

---

### Post by TechSupportx86 on 2011-08-11
type in:

```
iwconfig
```and tell me which one does NOT say "no wireless extensions" (example wlan0, wlan1, eth1, ect)

---

### Post by wael.day on 2011-08-11
> **TechSupportx86 said:**
> type in:

```
iwconfig
```and tell me which one does NOT say "no wireless extensions" (example wlan0, wlan1, eth1, ect)

wlan0 does not say "no wireless extensions"
so?

---

### Post by wael.day on 2011-08-11
> **TechSupportx86 said:**
> type in:

```
iwconfig
```and tell me which one does NOT say "no wireless extensions" (example wlan0, wlan1, eth1, ect)
wlan0     IEEE 802.11bgn    ESSID:off/any
          Mode:Managed Access Point: Not-Associated    Tx-Power=20 dBm
          Retry   long limit:7  RTS thr=2347  B   Fragment  thr:off
          Power Management:off

---

### Post by TechSupportx86 on 2011-08-11
That means wlan0 is the wireless device, So it should be working.

Just to make sure everything goes right, run all of these commands in order:

```
sudo ifconfig wlan0 down
``````
sudo ifconfig wlan0 up
``````
iwconfig wlan0 essid china wifi key :s 12345
```

---

### Post by wael.day on 2011-08-11
> **TechSupportx86 said:**
> That means wlan0 is the wireless device, So it should be working.

Just to make sure everything goes right, run all of these commands in order:

```
sudo ifconfig wlan0 down
``````
sudo ifconfig wlan0 up
``````
iwconfig wlan0 essid china wifi key :s 12345
```

OMG!!! it's the same error!!!! error for wireless request "Set ESSID" (8B1A)!!!!!
what shall i do??

---

### Post by TechSupportx86 on 2011-08-11
Well if you can i would go with a wired connection, But i am afraid i can no longer help as it is to late for me.

If you do use a wired connection just make sure your NIC is setup for DHCP. To do this open run:

```
sudo nano /etc/network/interfaces
```and make sure it reads:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0 
iface eth0 inet dhcp

```Your NIC may not be eth0, so run ifconfig to see what it is. Most cases it will work right away.

---

### Post by wael.day on 2011-08-11
thanks for your time and your help :))

---

### Post by nmaster on 2011-08-11
> **wael.day said:**
> what shall i do??
this might be stupid, but what if you put quotes around the ssid (use "china wifi" instead of china wifi)? i'm just wondering if the white space messes it up...

---

### Post by nmaster on 2011-08-17
> **wael.day said:**
> OMG!!! it's the same error!!!! error for wireless request "Set ESSID" (8B1A)!!!!!
what shall i do??

did you ever figure it out? i just ran into the same problem actually, lol... but it sucks.  i can work around it, but i feel like a newb again. i shouldn't have to rely on gui tools :(

---

