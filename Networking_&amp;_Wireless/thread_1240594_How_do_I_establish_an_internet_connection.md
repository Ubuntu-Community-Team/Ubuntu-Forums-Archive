---
title: "How do I establish an internet connection"
date: 2009-08-14
forum: Networking &amp; Wireless
---

### Post by iwant2 on 2009-08-14
I just installed Ubuntu on a Compaq desktop.  How do I set of a high speed cable internet connection?

---

### Post by Iowan on 2009-08-15
Might need a bit more info...
My DSL modem attends to the PPPOE details, so I just connect to it via ethernet. I use DHCP, so **auto eth0** option worked (after I disabled [rfc3442]("http://ubuntuforums.org/showthread.php?t=1156441")).

---

### Post by iwant2 on 2009-08-15
I can connect to a Motorola Surfboard via Ethernet or USB.

---

### Post by MaindotC on 2009-08-15
Try following the [Network Troubleshooting Guide](http://ubuntuforums.org/showthread.php?t=25557).  That has all the info you need to get started.

---

### Post by iwant2 on 2009-08-15
How does one "open a prompt"?

---

### Post by ahood on 2009-08-15
If using Ubuntu with Gnome desktop, press **Alt+F2**, then type [COLOR="DarkRed"]gnome-terminal[/COLOR] and left-click the **Run** button.

Hope this helps.

---

### Post by harry2006 on 2009-08-15
do provide some information regarding the problem you are facing and then we'll be in a better position to help you out!

---

### Post by Iowan on 2009-08-15
> **iwant2 said:**
> How does one "open a prompt"? I use a terminal so often, instead of Applications>Accessories>Terminal, I've added a Terminal shortcut to the top bar.

---

### Post by iwant2 on 2009-08-15
> **harry2006 said:**
> do provide some information regarding the problem you are facing and then we'll be in a better position to help you out!

OK Power on, Application, Accessories, Terminal
got prompt

typed -nr
command not found

typed route
Got
Kernel IP routing table
Destination Gateway Genmask      Flags Metric Ref        Use Iface
got prompt


What is the next step to connecting to the internet which is provided by my cable tv hookup via a Motorola Surfboard connected to a Compaq Presario S4100NX desktop via USB cable?

What additional information do you desire?

---

### Post by mick222 on 2009-08-15
isp might help i am in uk with virgin media cable just have to click the networks connection tab ( two little screens at on top task bar) and select auto eth0

---

### Post by iwant2 on 2009-08-15
> **mick222 said:**
> isp might help i am in uk with virgin media cable just have to click the networks connection tab ( two little screens at on top task bar) and select auto eth0


Hmm, OK 
Did that & the 2 screens changed to 2 small green dots w/ an arrow circling thru them.  After about 20 seconds a disconnected message appears.  Why did that happen?

What next?

---

### Post by Iowan on 2009-08-15
The prompt can be a bit confusing... the command should have been:```
netstat -nr
```
You can also check **ifconfig -a**. Those two circling green dots is the network trying to establish - apparently without success.

---

### Post by iwant2 on 2009-08-15
> **Iowan said:**
> The prompt can be a bit confusing... the command should have been:```
netstat -nr
```You can also check **ifconfig -a**. Those two circling green dots is the network trying to establish - apparently without success.

You got that right, confusing IS the operative word here.

ifconfig -a resulted in all zeros for RX & TX

What's the next step to successfully establish a connection?

Does one have to "mount" a USB port?

---

### Post by mick222 on 2009-08-15
have you got a router or just the modem.Try system preferences -> network configuration. might be better to use the Ethernet cable rather than usb if you can .

---

### Post by Fla-Newbie on 2009-08-15
OK, 
 
Here is another newbie. Just installed Ubuntu for the first time tonight. I have a wired connection and think that I have configured the static IP correctly. Have searched for step by step to make sure I didn't miss anything, but can't find anything.
 
When I place my mouse over the two computers...it states that "Wired network connection 'Auto eth0' active, however, I am still unable to access the Internet.
 
Any clarification would be great..and please remember. I have never installed or configured Ubuntu or any other linux flavor.
 
Thanks,

---

### Post by Greenroyd on 2009-08-15
> **Fla-Newbie said:**
> OK, 
 
Here is another newbie. Just installed Ubuntu for the first time tonight. I have a wired connection and think that I have configured the static IP correctly. Have searched for step by step to make sure I didn't miss anything, but can't find anything.
 
When I place my mouse over the two computers...it states that "Wired network connection 'Auto eth0' active, however, I am still unable to access the Internet.
 
Any clarification would be great..and please remember. I have never installed or configured Ubuntu or any other linux flavor.
 
Thanks,

Though I am new to Ubuntu myself, I would highly recommend posting a new topic for your issue instead of robbing someone else thread. FYI....

---

### Post by iwant2 on 2009-08-15
> **mick222 said:**
> have you got a router or just the modem.Try system preferences -> network configuration. might be better to use the Ethernet cable rather than usb if you can .

Cool, as soon as I plugged in the ethernet cable the arrow started circling thru the green dots.  
Bummer, after about 30 seconds a Disconnected message Again.

No one has the solution for a successful connection?

---

### Post by Iowan on 2009-08-16
Acts like it's not getting IP address. You can see if [this]("http://ubuntuforums.org/showthread.php?t=1156441") helps.

---

### Post by iwant2 on 2009-08-16
> **Iowan said:**
> Acts like it's not getting IP address. You can see if [this]("http://ubuntuforums.org/showthread.php?t=1156441") helps.

No. Too geeky. 

Beginning to realize that I need to buy XP.

---

### Post by iwant2 on 2009-08-16
Cool, I'll be online with my second computer in a few days.  Just won XP off ebay.

That appear to be the answer to:

"[SIZE=3]**How do I establish an internet connection**[/SIZE]" :)

---

### Post by misio129 on 2009-08-17
seeing as i am not as impatient as iwant2, i'll stick this one out.

I think my problem is quite similar, I want to connect two computers, both running ubuntu, together. I did this successfully, and was able to telnet from one to the other. However, when i tried to install telnetd on the one without the internet connection ('sudo apt-get install telnetd' - and yes i moved the ethernet cable across to that computer!) it kinda messed up all the connections.

So now I have one computer with no connection to anything, and another with a connection to the internet and a 'disconnected' network card.

Can anyone give some advice as to how i can make a connection using the network card between the two computers? I'm not really looking to share the inernet connection, just put the two on a network.

Cheers.

just underneath the networking icon, a mesage just flashed up saying sometyhing along the lines of 'network detection has been disabled'...so how do i re-enable network detection, and will this solve my problem?

---

### Post by cariboo on 2009-08-17
To make sure you will be automatically connected, right click on the network manager icon in the top panel, next click edit connections. Highlight your device, it should be eth0 and click edit. On the window that pops up make sure connect automatically is checked. Next click the IPv4 Settings tab and make sure that Automatic (DHCP) is selected in Method, then click apply and close the connection window.

To see if you can get an ip address, open an Applications-->Accessories-->terminal and type:

```
sudo dhclient eth0
```

Hopefully you should get an ip address and be able to connect to the internet.

---

### Post by roharme on 2009-08-17
One of my signature helps you setup a connection

---

### Post by misio129 on 2009-08-19
FIXED! turns out that changing 'managed=false' to true in /etc/NetworkManager/nm-system-settings.conf solved the problem. this does give me two new connections though, ifupdown(eth0) and ifupdown(eth1). what do these two refer to?

---

