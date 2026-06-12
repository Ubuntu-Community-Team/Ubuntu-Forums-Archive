---
title: "Restore the &quot;Network Connections&quot; Icon in the top panel?"
date: 2010-06-01
forum: Networking &amp; Wireless
---

### Post by udeyrishi1994 on 2010-06-01
1. I'm totally new to ubuntu. So please please, use simple language. If technical stuff needs to be told, pleas explain. I have installed ubuntu just yesterday.

Ok So i installed edubuntu yesterday, and it was working flawlessly. Now suddenly the "Network Connections" icon in the top panel, to the left of clock and at the side of volume controller is missing. I don't know how to connect to my DSL Broadband internet! 
I'm using the "sudo pppoeconf" command temporarily to connect to internet. I've BSNL broadband internet connection, I live in India. Please help me how to bring back the network connection icon, so that i may connect net again. 
[http://www.blogcdn.com/www.downloadsquad.com/media/2010/03/lucid2010-03-1919-04-11.jpg](http://www.blogcdn.com/www.downloadsquad.com/media/2010/03/lucid2010-03-1919-04-11.jpg)

Like in the above picture, there are "2 oppositely pointing arrows" showing the network connection icon, to the side of volume controller. How to bring it back? It suddenly disappeared on itself!

I googled a bit and found that some people told to press alt+f2 and type some command (which i forgot and am not able to remember, sorry!). But that didn't work, although it worked for the person who had the same problem as mine. I don't know what is wrong. I'll be very thankful!

---

### Post by suseendran.rengabashyam on 2010-06-01
Hi,

Try the following step in your Edubuntu machine to add the Network Notification icon to the panel

Right Click on the Top Panel -> Add to Panel -> Notification Area -> Add

Hope this helps.

---

### Post by udeyrishi1994 on 2010-06-01
I ried adding it, there is "network manager" in the list of applets. I tried possible everything google can offer. I want some expert support i think. Can i contact some ubuntu engineer/programmer?

---

### Post by suseendran.rengabashyam on 2010-06-01
Hi,

You need not add the 'Network Manager' applet, try adding the 'Notification Area' applet.

---

### Post by udeyrishi1994 on 2010-06-01
tried doing that too, adding notification applet just adds "3 horizontal lines", showing that this is the notification area, but not the network manager. Those 3 lines look like the lines which are there at the edges of windows, used to show "drag from here to resize the window".

---

### Post by udeyrishi1994 on 2010-06-01
like in the pic i've attached, the lines which are there to the left side of the "network manager" icon, i.e. the leftmost icon on the right part of the top panel.

---

### Post by anand_30 on 2010-06-05
I am also new to ubuntu but i faced the same problem just like you.

First of all i should tell you when you configure your broadband connection using command
```
sudo pppoeconfig
``` 
you will lose your network icon at the right top corner.Its a strange thing but its a fact.

Solution:-
1)Press Alt+F2 and copy this command:-
```
gksudo gedit /etc/network/interfaces
```
Hit Run.
type your password and then you will see some text now delete text below

auto lo
iface lo inet loopback

Remember dont delete above lines.

2)Now you have lost your connection configuration.Restart your computer.

3)You will see network icon at right top but you have lost your bsnl broadband configuration.

4)To create connection right click on network icon then go to
Edit Connections..>>go to DSL tab at extreame right.

5)Click on Add.

6)Fill information such as Connection name such as bsnl,Username which is given by bsnl,Service such as bsnl-broadband and Password.If you like to coneect automatically when you turn on modem check the box for Connect Automatically.

7)Now go to last tab Ipv4 setting and select method Manual.Click on Add.

8)Now fill it with Address 192.168.1.2
                        Netmask 255.255.255.0
                        Geteway 192.168.1.1

9)click on apply and you are done.

Now whenever your modem is on state left click on that icon click on bsnl and you are connected.

Hope this help.
Reply if it worked.It worked for me.:)

---

### Post by udeyrishi1994 on 2010-06-05
@ anand...thanx for the help....but oops...i have already formatted by ubuntu installation! I'm downloading kubuntu now using windows....want to give it a shot...heard a lot about the usability of KDE....what do you say? KDE vs Gnome??

---

### Post by anand_30 on 2010-06-06
> **udeyrishi1994 said:**
> @ anand...thanx for the help....but oops...i have already formatted by ubuntu installation! I'm downloading kubuntu now using windows....want to give it a shot...heard a lot about the usability of KDE....what do you say? KDE vs Gnome??

Why are you downloading Kubuntu separately?you can install K desktop using default ubuntu also.But if you have already downloaded it completely then let it be and ofcourse try it.I haven't tried Kubuntu myself but my few friends use it.It looks more beautiful than gnome.

Enjoy Kubuntu.:popcorn:

But if you get same problem try that solution and don't be afraid to ask.

And yes don't forget to check MD5 sum after downloading image and if you are using CD then burn it at lower speeds.

---

### Post by udeyrishi1994 on 2010-06-07
Downloaded the DVD, planning to install it in a  day or 2

---

### Post by leily on 2012-04-18
Hi friends

I have the same problem and I can restore the connection icon by the solution which anand_30 explained.
But I don't have any Wireless connection, it shows only wired and vpn connection. I installed edubuntu 11.10 in vmware.
I attached its photo.
Would you please help me?

Regards.

---

