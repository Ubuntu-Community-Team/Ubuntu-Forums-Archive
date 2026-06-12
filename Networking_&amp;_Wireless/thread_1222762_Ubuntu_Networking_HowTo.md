---
title: "Ubuntu Networking HowTo"
date: 2009-07-25
forum: Networking &amp; Wireless
---

### Post by djgenesis on 2009-07-25
Hello All,

I've just reinstalled ubuntu GNOME on a spare machine I have and have connected it through my router.

The problem is that my router is ADSL but I have a cable connection. So instead of connecting the router directly to the cable modem, I have connected my windows PC and activated ICS.
I have then connected my router to the PC and all the other devices I am connecting to the router use manual DNS and GTW the IP of the PC.

So I am trying to configure the default gtw on my Ubuntu machine and I am getting crazy.

How can there be so differnt ways to do that?!?! Can anyone help me differentiate which ones are the same?

1) From thr KDE control panel "Network Connections" (where I can't see eth1 on the list... why?)

2) From webmin Networking -> Network Configuration

3) From /etc/network/interfaces

4) from the terminal, with command "route" 

Which of these above are linked? 

I mean, the status bar on the KDE doesn't show my PC as connected to the wired, although I can access my LAN OK.

When I change the default gtw with "route", remove the default gtw of my router and issue
```
sudo /etc/ini.t/network restart
```
the manual gtw is dropped, and the router gtw is back!!!


I ran the Network Connections app from the terminal with :
```
sudo nm-connection-editor
```
but when I try to create a new network interface or modify anything in there I get a message when I try to save:

```
"Could not add connection"
"PolicyKit authorization could not be created; invalid action ID[
```

When I changed the settings in WebMin and applied, they look as I want them but my machine is still not using these settings

aaaw.... I am so confused!!!

Can anyone explain a little bit please?

---

### Post by Charlietje on 2009-07-25
Hi,

How do you connect from your ubuntu pc to your windows pc?
Do you use a crossover kabel?

You say that you can't see eth1... How is your device called?
You can find all available devices by typing: ifconfig -a

If you connect your ubuntu pc directly to the adls router, do you then get an ip address?


Regards

---

### Post by djgenesis on 2009-07-25
> **Charlietje said:**
> Hi,

1.How do you connect from your ubuntu pc to your windows pc?
Do you use a crossover kabel?

2.You say that you can't see eth1... How is your device called?
You can find all available devices by typing: ifconfig -a

3.If you connect your ubuntu pc directly to the adls router, do you then get an ip address?


Regards


Hi!, thanks for your reply,
1. I've used a stratigh through Cat5 straight to the router.
The Windows PC is also connected wirelessly to the router.

The ethernet cable from my cable modem goes to my Windows PC and I have done ICS with my wireless connection which connects to the router. 

2. I can see eth1 in /etc/network/interfaces, ifconfig and webmiin, but I can't see it in the nm-connection-editor.

3. Yes, the IP address that it has acquired is :
192.168.0.2

The router's IP address is 192.168.0.254

---

### Post by Iowan on 2009-07-26
> **djgenesis said:**
> 2. I can see eth1 in /etc/network/interfaces, ifconfig and webmiin, but I can't see it in the nm-connection-editor.NM won't control interfaces defined in */etc/network/interfaces*. Try commenting out (#) the definition there and restarting.

---

