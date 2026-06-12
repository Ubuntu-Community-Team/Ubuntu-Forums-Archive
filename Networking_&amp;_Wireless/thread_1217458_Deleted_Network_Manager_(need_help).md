---
title: "Deleted Network Manager (need help)"
date: 2009-07-19
forum: Networking &amp; Wireless
---

### Post by VandalEmperor16 on 2009-07-19
Hello I'm newer to Ubuntu, and for first couple of days I was able to connect to the internet, but one day I could not find Network Manger anywhere, I searched and searched to no avail, and now I can't connect wirelessly or with Ethernet cable to the internet using Ubuntu, but I can still connect perfectly using Vista.  Is there anyway I can connect manually?

p.s:  If it as an importance I have Netgear RangeMax Wireless router.

Any help would be much appreciated

---

### Post by mikewhatever on 2009-07-19
You are probably missing something called notification area, that's where the network manager lives. Right click on the panel, select Add to panel, find Notification area in the list and add it to the panel.

---

### Post by ugm6hr on 2009-07-19
> **mikewhatever said:**
> You are probably missing something called notification area, that's where the network manager lives. Right click on the panel, select Add to panel, find Notification area in the list and add it to the panel.

If it still isn't there after this, press Alt+F2 and enter:
```
nm-applet --sm-disable
```

---

### Post by VandalEmperor16 on 2009-07-19
> **ugm6hr said:**
> If it still isn't there after this, press Alt+F2 and enter:
```
nm-applet --sm-disable
```
After I put this command in, the terminal said,
"The Program nm-applet can be found in the following packages:
*network-manager-gnome
*mythbuntu-diskless-client

What does this mean and what should I do ugm6hr??

---

### Post by varun1786 on 2009-07-20
it means u dont have the network manager application installed. open up a terminal(alt + f2) and type

$sudo apt-get install network-manager-gnome

then

$nm-applet --sm-disable

---

### Post by VandalEmperor16 on 2009-07-20
> **varun1786 said:**
> $sudo apt-get install
this doesn't work because I can't connect to the internet in ubuntu

---

### Post by ugm6hr on 2009-07-20
I presume you are using Gnome (i.e. standard Ubuntu).

Did you try and install an alternative network application?

If not, I do not understand why it is no longer installed.

Search for the appropriate **network-manager-gnome** .deb file here: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

It should also be on the LiveCD (install CD) somewhere.

Then install it.

Then try again.

---

### Post by GuruKid on 2009-07-26
I'm having a similar problem with Jaunty. I accidentally deleted the "network manager applet" and couldn't find any way of adding it to the panel again. I can go to network connections and edit the settings but I can't conect without the applet. 

What I did was make a new user which had all the default settings. The network manager applet was alive and kicking there so I connected to the network and then switched back to my admin account. 

So that's one hacky way of doing it.

---

