---
title: "Internet Connection Sharing to Windows XP"
date: 2010-11-18
forum: Networking &amp; Wireless
---

### Post by Ardghal on 2010-11-18
Hello. I need help configuring Internet Connection Sharing from my Ubuntu 10.10 machine to a Windows XP machine. I've seen How To's but they didn't work, yet.

  The Ubuntu machine connects to the Internet through a DSL USB modem that required packages not provided with the distribution, and specific instructions to configure it; so getting Internet working alone was difficult. As a result, I don't even use Network Manager, rather connect using the command *pppoe-start*.
  The machine is connected to the Windows PC through a simple cable, through the Ethernet card.

Some tutorials I've seen on ICS are for machines with two Ethernet cards, or for wireless connections; but I've seen none for a USB modem. However I once found one, years ago, and it worked, but I couldn't find it now. It was using iptables, and I didn't really understand what I was doing, but it worked. But then I had to format the disk, and now I can't find a way to get it working again.

Can anyone direct me to a proper tutorial?

---

### Post by dineshs on 2010-11-19
I am not an expert.Not sure this will work
_Ubuntu Machine_
For connecting DSL you are using pon command,no problem
Right click Network manager icon on top right of the panel(Is that icon there? If not try step-I [ here]("http://ubuntuforums.org/showpost.php?p=9611450&postcount=2") then restart) then click edit connections-select wired tab-click ethernet connection-edit-click ipv4-Method [COLOR="Blue"]Shared to other computers[/COLOR]-apply
_Windows machine_
Under network connections-double click Local area connection-properties-TCP/IP properties-Use the following IP
IP- [COLOR="Blue"]10.42.43.100[/COLOR]
Mask -[COLOR="Blue"]255.255.255.0[/COLOR]
Gateway [COLOR="Blue"]10.42.43.1[/COLOR]
Primary DNS say [COLOR="Blue"]4.2.2.1[/COLOR]
Secondary [COLOR="Blue"]8.8.8.8[/COLOR]
Click OK
Any progress?

---

### Post by Ardghal on 2010-11-19
First, thanks for responding. :D

Before I change the sttings on the Windows XP machine, I must say it's already set up to get shared Internet from this machine, but when I'm on Windows 7. As opposed to when I had XP, which was really easy to configure to share the connection, with Windows 7 it took some effort to get it working.

So, I guess changing the Windows XP machine's settings to those you posted would cut off the ICS already in place from Windows 7. Do you know what would I need to set it to in the existing shared connection before I try that?

The reason I can't just try, is because the Windows XP machine is used for a business and it must be working 8 hours a day. I only get a limited ammount of time of access to it.

In any case, I'll try that as soon as I get time on the XP machine. :) Thanks, again.

---

### Post by dineshs on 2010-11-19
You mean your ubuntu machine is a dual boot with windows7?

---

### Post by Ardghal on 2010-11-19
> **dineshs said:**
> You mean your ubuntu machine is a dual boot with windows7?

Yes. I have Windows 7 and Ubuntu 10.10 on the same PC. Both with Internet access (it was difficult in Ubuntu!), and Windows 7 shares the Internet connection with the Windows XP PC. I'd like Ubuntu to share the connection too, as it did on a previous version, before I had to format the hard drive.

---

### Post by dineshs on 2010-11-20
Can you post the result of```
ipconfig /all
```from both win XP and Win 7 ?

---

### Post by Ardghal on 2010-11-20
I've followed your instructions and now Ubuntu can share the connection with the XP machine. It worked. :D

Then, Windows 7 couldn't share the connection, but I changed the settings that were under TCP/IP->IPv4 that were the ones configured to share it in the first place, and using the settings you gave me, I guessed the right setting. Now it works from Windows too. The only thing I had to change was the IP. The mask was the same, and under gateway and DNS there was nothing. I left those the same.

Thanks! But, how did you know those settings would work? I didn't see those numbers anywhere on Ubuntu. In any way, it's great I didn't have to edit iptables like the last time. :D

One more thing: now when the Windows XP machine disconnects or is turned off, it cuts off **my** Internet connection on Ubuntu. Then I have to go to the console and do *pppoe-stop*, then *pppoe-start* again, then it works.

Why? :confused: The other machine shouldn't have that authority over my connection that works with a USB modem. It's just a minor annoyance, though.

---

### Post by dineshs on 2010-11-20
> But, how did you know those settings would work? I didn't see those numbers anywhere on Ubuntu. In any way, it's great I didn't have to edit iptables like the last time
When an interface is configured for internet connection sharing in Network manager the IP that automatically gets assigned is 10.42.43.1 (google search)
So for the other machine we can use an IP in the same pool
> One more thing: now when the Windows XP machine disconnects or is turned off, it cuts off my Internet connection on Ubuntu. Then I have to go to the console and do pppoe-stop, then pppoe-start again, then it works.
What is the output of```
cat /etc/network/interfaces
```

---

### Post by Ardghal on 2010-11-21
> **dineshs said:**
> When an interface is configured for internet connection sharing in Network manager the IP that automatically gets assigned is 10.42.43.1 (google search)
So for the other machine we can use an IP in the same pool

I see. Great. :D All I saw when setting shared connections was the IP used for a LAN (192.168.0.1) and its variants for the other machines. I think that's what ICS was using for Windows 7-Windows XP before I changed it with these new values.

[QUOTE=dineshs]What is the output of```
cat /etc/network/interfaces
```[/QUOTE]

This is what it returns:

```
auto lo
iface lo inet loopback


```

---

