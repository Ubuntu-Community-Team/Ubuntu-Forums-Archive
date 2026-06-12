---
title: "Wireless Network Found, can't connect, repeated requests for authentication"
date: 2012-08-24
forum: Networking &amp; Wireless
---

### Post by hermholland on 2012-08-24
After trawling through the internet, on forums, support websites, and through dozens upon dozens of answered questions on the Ask Ubuntu site, I've not found a solution to what seems like a fairly regular problem...

**I cannot connect to a wireless network, and am continually asked for the network password.**

I have tried countless suggested solutions on the different locations I've already referred to. None of them have worked.


Details of my experience are as follows:

> I have just recently installed Ubuntu 12.04.1 (32-bit).
Ubuntu installed on my system seemingly fine, and I even formatted my hard drive during the process. It's as if it were a new desktop computer.

During the installation I was asked to connect to a Wireless Network. I have a USB Wireless Card connected which I have used to connect desktop PC's, laptops, and a Wii to the internet from approximately the same area of the house (thus the same distance from the Wireless Router). I chose my network, entered the correct password for it (I double checked; it's definitely the right password) and proceeded with the installation.
Several times before the installation was complete, I was asked to authenticate the connection, and this seemed to do nothing each time. On the repeated screens the password was already entered in the appropriate box.

When Ubuntu booted up the first thing I was faced with (other than something about Language settings, or something) was another request for authentication. Again, the password was already there, so I clicked connect. It did not connect. Instead, I was once again faced with repeated requests every few minutes.

I went onto my laptop, which is connected to this network, checked the details of the network, and entered them manually into my Ubuntu PC (including the IPv4 and IPv6 information) but this didn't work either, so I set it back to finding the settings automatically.
Note, also, that the "Connect automatically" and "Available to all users" boxes are checked, and have been unchecked & rechecked countless times. I have also tried having my User account connect automatically, and to need a password entered at the welcome screen.

Whilst I've been writing this, it has gone through a spat of connecting successfully to the network for less than a minute, before coming offline again, only to repeat the process. But it has now returned to prompting me for a password every couple of minutes.

This computer has already run on the Fedora OS, and had no trouble connecting to, and maintaining a connection.
I also have a laptop running Windows 7 less than a metre away from this desktop PC, which is connected and has no trouble maintaining a connection at 50%-100% strength (fluctuating).

Therefore:
- I know it's not the wireless card
- I know it's not the PC itself
- I know it's not the access point
- I know it's not the location of my PC or wireless card
- It is solely because of Ubuntu

Everything else has worked fine, but the moment Ubuntu was introduced into the equation, it has gone completely wrong.
Honestly; I prefer Ubuntu as an OS to Fedora, but if I can't solve the problem it'll be straight back to Fedora that I'll have to go.

**Can anyone help me at all?**

---

### Post by oldsoundguy on 2012-08-24
this was my thread on the subject:
[http://ubuntuforums.org/showthread.php?t=2046342](http://ubuntuforums.org/showthread.php?t=2046342)

---

### Post by OM55 on 2012-08-24
Hello hermholland,

It would be helpful to view the wireless system log that is generated during the attempt to connect.
Here is you do it: 
1. Leave your laptop idle for a few of minutes (wireless off, so the connection attempt of the time stamp in the log will be clear) and then try to connect to the wireless router. 

2. Right after the unsuccessful attempt to connect to the wireless router, type in terminal:

```
cat /var/log/syslog | grep NetworkManager > WirelessLog.txt

```then:
```
gedit WirelessLog.txt

```We will start looking at the events with the time stamp of the moment you tried to connect to the wireless connection. The events we are interested in will start at the last time-stamp jump and have "NetworkManager" at the beginning of the line. 

Normally you would see reports on the network SSID it is connecting to, two DNS servers being assigned, IP address being assigned by the DHCP etc.
In your case some of it is not happening and you may be able to see what it is trying to do and cannot, resulting in no-wireless connection.

So this may give us some hints as for what is NOT happening that should, and why.
If you post the WirelessLog.txt file here as an attached file (only the bottom lines, starting at the last time-stamp jump), we should be able to help you find a clue and identify the problem.


_**For general information**_ - There is a known bug with Network Manager that happens with some specific drivers on specific hardware and it has been reported before several times. I think there is a patch available for Network Manager but not yet updated in the repositories.


[SIZE=3]_So, regardless of inspecting the log files for clues, here is a quick possible workaround that may work for you anyway:_
[/SIZE] 
You can replace Network Manager and use Wicd instead (**[https://launchpad.net/wicd](https://launchpad.net/wicd)**), it is in the Software Center and the Ubuntu repositories. Wicd is a nicer graphical interface for wired/wireless network management that pretty much replaces all the functionality of Network Manager.

The only small risk in doing this exchange - you have to be careful and do things step by step, or might be left without any network connection... Given that in Ubuntu everything is done via the Internet connection, it wont be fun when that happens... (you will need to download the .deb file of Network Manager using a different laptop, transfer to this one and install).

To install Wicd and properly disable Network Manager, follow the instructions in the following link (coincidentally, it was done to solve the exact same problem you have):
**[http://www.techrepublic.com/blog/australia/fixing-fedoras-wi-fi-with-wicd/463](http://www.techrepublic.com/blog/australia/fixing-fedoras-wi-fi-with-wicd/463)**

You can install Wicd directly from Software Center, or try the latest version from the developer's website

IMPORTANT: It is critical that you will disable Network Manager only after Wicd is working, or will be left without a networking connection.

Hope that the above will finally resolve your wireless hassle!
Let us know if Wicd worked for you.

---

### Post by eheitner on 2013-05-02
Hi. I was having the exact same problem. Here is my wireless log. What do you think?[ATTACH]242113[/ATTACH]

---

