---
title: "Network manager problem"
date: 2010-07-18
forum: Networking &amp; Wireless
---

### Post by alenn on 2010-07-18
Everything worked fine until I downloaded some Ubuntu upgrades. Now, every time I try to connect to internet via network manager it says: " Network: Disconnected - you are now offline". so what to do...

---

### Post by Iowan on 2010-07-18
Right-click on Network Manager Icon and verify "Enable Networking" is checked - some updates have reportedly "unchecked" this.

---

### Post by lelantus on 2010-07-18
It's not the "Enable Networking", it's the "Enable Wireless". It's grayed out.. any ideas?

---

### Post by alenn on 2010-07-18
"enable networking" is already checked, but connection don't work, I connect to internet via terminal.

---

### Post by walt.smith1960 on 2010-07-18
> **lelantus said:**
> It's not the "Enable Networking", it's the "Enable Wireless". It's grayed out.. any ideas?

Easiest thing first--have you tried a restart?  If that doesn't fix it, I'd log on with administrator privileges and see if I could check "Enable Networking" there.  I hope this helps.

---

### Post by alenn on 2010-07-18
> **walt.smith1960 said:**
> Easiest thing first--have you tried a restart?  If that doesn't fix it, I'd log on with administrator privileges and see if I could check "Enable Networking" there.  I hope this helps.

what do you mean, restart, how to restart network manager ?

---

### Post by Iowan on 2010-07-18
From a terminal, try **sudo restart network-manager**. There is another way (using **service**) that I need to look up...
(**sudo service network-manager restart**)

---

### Post by lelantus on 2010-07-18
Mhmm, I've tried a restart, and restarted network-manager.

I've addressed this issue here [http://ubuntuforums.org/showpost.php?p=9577841&postcount=13](http://ubuntuforums.org/showpost.php?p=9577841&postcount=13) but haven't gotten any results or feedback regarding the issue.

Help?

---

### Post by alenn on 2010-07-19
I tryed everything you said but it still don't work, and by the way, I use dsl connection.

---

### Post by alenn on 2010-07-19
c'mon people, help

---

### Post by Iowan on 2010-07-19
Spring-boarding off the link, you can check */var/lib/NetworkManager/NetworkManager.state*. You should see ```
NetworkingEnabled=true

```

[Here]("http://ubuntuforums.org/showthread.php?t=1505217") is a similar thread...

---

### Post by dineshs on 2010-07-19
> **alenn said:**
>  I connect to internet via terminal.
running *pon* command?(have you run *sudo pppoeconf* command to create the dsl connection)?

---

### Post by alenn on 2010-07-20
> **dineshs said:**
> running *pon* command?(have you run *sudo pppoeconf* command to create the dsl connection)?

of course

---

### Post by alenn on 2010-07-20
> **Iowan said:**
> Spring-boarding off the link, you can check */var/lib/NetworkManager/NetworkManager.state*. You should see ```
NetworkingEnabled=true

```

[Here]("http://ubuntuforums.org/showthread.php?t=1505217") is a similar thread...

here is what it says:

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

---

### Post by dineshs on 2010-07-20
If you are using NM it is better to avoid using pppoeconf command because if you run this command, there will be additional lines/entries in /etc/network/interfaces which will cause NM not to manage things.Can you please post what is in /etc/network/interfaces
```
cat /etc/network/interfaces
```
Please have a look here
[http://ubuntuguide.net/fix-dsl-pppoe-connection-problem-with-network-manager-in-ubuntu-9-10](http://ubuntuguide.net/fix-dsl-pppoe-connection-problem-with-network-manager-in-ubuntu-9-10)

---

### Post by alenn on 2010-07-20
> **dineshs said:**
> If you are using NM it is better to avoid using pppoeconf command because if you run this command, there will be additional lines/entries in /etc/network/interfaces which will cause NM not to manage things.Can you please post what is in /etc/network/interfaces
```
cat /etc/network/interfaces
```
Please have a look here
[http://ubuntuguide.net/fix-dsl-pppoe-connection-problem-with-network-manager-in-ubuntu-9-10](http://ubuntuguide.net/fix-dsl-pppoe-connection-problem-with-network-manager-in-ubuntu-9-10)

auto lo
iface lo inet loopback


auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth1 up # line maintained by pppoeconf
provider dsl-provider

auto eth1
iface eth1 inet manual


and I've tryed these steps on this link you've posted, but it's the same again

---

### Post by dineshs on 2010-07-20
I understand that you 
1)edited the file so that it contained only```
auto lo
iface lo inet loopback
```
2)[COLOR="Blue"]restarted[/COLOR] your machine and 
3)Configured your connection via the DSL tab in NM
But it didnt work.Am I right?

---

### Post by alenn on 2010-07-20
> **dineshs said:**
> I understand that you 
1)edited the file so that it contained only```
auto lo
iface lo inet loopback
```
2)[COLOR="Blue"]restarted[/COLOR] your machine and 
3)Configured your connection via the DSL tab in NM
But it didnt work.Am I right?

yes, you are right

---

### Post by alenn on 2010-07-21
if you can't help me with network manager, can you recomend me some other programs which I can use to manage dsl connection.

---

### Post by dineshs on 2010-07-21
1).Cant you configure your modem/router in PPPoE mode so that you can save your username and password in the modem/router so that the connection will always be ON once the modem is ON.Most of the modems/routers support this.
2).remove network manager and proceed with pppoeconf .Then connect /disconnect via pon/poff.I am not sure about this.You may read this post(postcount #2)
[http://ubuntuforums.org/showthread.php?p=8975701#post8975701](http://ubuntuforums.org/showthread.php?p=8975701#post8975701)

---

### Post by alenn on 2010-07-21
> **dineshs said:**
> 1).Cant you configure your modem/router in PPPoE mode so that you can save your username and password in the modem/router so that the connection will always be ON once the modem is ON.Most of the modems/routers support this.
2).remove network manager and proceed with pppoeconf .Then connect /disconnect via pon/poff.I am not sure about this.You may read this post(postcount #2)
[http://ubuntuforums.org/showthread.php?p=8975701#post8975701](http://ubuntuforums.org/showthread.php?p=8975701#post8975701)

will this affect on my internet connection on windows?

---

### Post by dineshs on 2010-07-22
> will this affect on my internet connection on windows? 
No.Only thing you will no longer require the PPPoE dialler in windows.ie the connection will always be ON.Also if you find any problem you can reprogram the modem in BRIDGE mode
Do you share the connection with other PCs?How many ethernet cards do you have?Please post the results of > lshw -C network

---

### Post by alenn on 2010-07-22
> **dineshs said:**
> No.Only thing you will no longer require the PPPoE dialler in windows.ie the connection will always be ON.Also if you find any problem you can reprogram the modem in BRIDGE mode
Do you share the connection with other PCs?How many ethernet cards do you have?Please post the results of

WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: 3c940 10/100/1000Base-T [Marvell]
       vendor: 3Com Corporation
       physical id: 5
       bus info: pci@0000:02:05.0
       logical name: eth0
       version: 12
       serial: 00:0c:6e:e4:0a:ec
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=skge driverversion=1.13 firmware=N/A latency=64 maxlatency=31 mingnt=23 multicast=yes
       resources: irq:22 memory:feafc000-feafffff ioport:d800(size=256)
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: b
       bus info: pci@0000:02:0b.0
       logical name: eth1
       version: 10
       serial: 00:e0:4c:c0:bf:70
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 multicast=yes
       resources: irq:23 ioport:d400(size=256) memory:feafbc00-feafbcff memory:30000000-3000ffff(prefetchable)

don't share connection with other PC's, and I have two ethernet cards, but I use only one.

---

### Post by dineshs on 2010-07-22
You can try PPPoE mode if your router/modem supports it.
So first connect your modem to one ethernet port,then run
```
sudo dhclient
```
then ```
ifconfig -a
```
Do you get IP? 
If not you can connect modem to the other LAN port and repeat the steps

---

### Post by alenn on 2010-07-22
> **dineshs said:**
> You can try PPPoE mode if your router/modem supports it.
So first connect your modem to one ethernet port,then run
```
sudo dhclient
```
then ```
ifconfig -a
```
Do you get IP? 
If not you can connect modem to the other LAN port and repeat the steps

yeah, I get IP, well I get more then one IP's.

but look, I don't want to do this what you telling me to do because sometimes I need my connection OFF in windows, so this will just make me difficult to work on windows.

can you tell me if there is some other program which I can use to manage dsl connection.

---

### Post by dineshs on 2010-07-23
> **alenn said:**
> 
but look, I don't want to do this what you telling me to do because sometimes I need my connection OFF in windows, so this will just make me difficult to work on windows.
To solve this you can create a shortct of Local Area Connection on the desktop(in Windows)then enable(connect) or disable (disconnect)it .Does it make any difference?same way in ubuntu you can disable or enable eth

> can you tell me if there is some other program which I can use to manage dsl connection.
I have heard of another program called rp-pppoe.But I havent tried.The following  links or a google search may help
[http://ubuntuforums.org/showthread.php?t=816858](http://ubuntuforums.org/showthread.php?t=816858)
[http://ubuntuforums.org/showpost.php?p=3182052&postcount=10](http://ubuntuforums.org/showpost.php?p=3182052&postcount=10)

---

### Post by alenn on 2010-07-23
tryed this program too but it doesn't work, I think that I will stick to terminal and sudo pon dsl-provider, tnx guys for your effort, I wanted to fix my network manager but if you can't help with this then I'll continue to use terminal.

---

### Post by dineshs on 2010-07-23
If pon via terminal is working,there is a GUI tool for that.It is gpppon.
[http://ubuntuforums.org/showpost.php?p=9417472&postcount=4](http://ubuntuforums.org/showpost.php?p=9417472&postcount=4)

Links to network manager issues(You may have tried already as lowan suggested some)
[http://ubuntuforums.org/showpost.php?p=7041625&postcount=4](http://ubuntuforums.org/showpost.php?p=7041625&postcount=4)
[http://ubuntuforums.org/showpost.php?p=5132230&postcount=3](http://ubuntuforums.org/showpost.php?p=5132230&postcount=3)
[http://ubuntuforums.org/showthread.php?t=1533554&page=3](http://ubuntuforums.org/showthread.php?t=1533554&page=3)
(You may add sudo before the commands mentioned here)
Points to check
system-preferences-startup applications tick network manager
Right click on the top panel-click add to panel-select notification area -click add
Right click on the NM icon and tick"Enable Networking"

---

### Post by alenn on 2010-07-24
can anyone tell me how to set network manager to default and then you tell me how to fix it, because I changed some things in NM because I followed some suggestions from other sites in order to fix NM.

---

### Post by Leonasha on 2010-07-24
deleted - posted in wrong topic, sorry!

---

### Post by ashwinrao on 2010-07-24
Even I had experienced same issue after the update. The 'Auto eth0' displays disconnected every time even if LAN is active. I was able to connect once and managed to re install network manager using Synaptic Package Manager. Now, it is stable for time being. I think some thing surely went wrong with updates.

---

### Post by dineshs on 2010-07-25
Recently found this
[http://ubuntuforums.org/showpost.php?p=9631393&postcount=7](http://ubuntuforums.org/showpost.php?p=9631393&postcount=7)

---

### Post by alenn on 2010-07-25
> **dineshs said:**
> Recently found this
[http://ubuntuforums.org/showpost.php?p=9631393&postcount=7](http://ubuntuforums.org/showpost.php?p=9631393&postcount=7)

this fixed one my other problem but not this with NM. can anyone tell me how to set NM and all of it settings to default, how to make it just like it was when I installed ubuntu, I have some ideas how to fix NM but I can't start with that until I set everything to default.

---

### Post by dineshs on 2010-07-25
Hint:Actually NM writes configurations in /etc/NetworkManager/system-connections

---

### Post by alenn on 2010-07-25
> **dineshs said:**
> Hint:Actually NM writes configurations in /etc/NetworkManager/system-connections

can you check if you typed this correctly

---

### Post by dineshs on 2010-07-25
> **alenn said:**
> can you check if you typed this correctly

```
gksudo nautilus /etc/NetworkManager
```
What are the contents

---

### Post by alenn on 2010-07-26
> **dineshs said:**
> ```
gksudo nautilus /etc/NetworkManager
```
What are the contents

Initializing nautilus-gdu extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' vratio grešku 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error Nema takve datoteke ili direktorija
Please ask your system administrator to enable user sharing.

---

### Post by alenn on 2010-07-26
> **alenn said:**
> Initializing nautilus-gdu extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' vratio grešku 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error Nema takve datoteke ili direktorija
Please ask your system administrator to enable user sharing.

some of this are on bosnian, I just copied everything what came out afetr that command

---

### Post by dineshs on 2010-07-27
Sorry to say that I dont understand the reason for this output

---

### Post by alenn on 2010-07-27
> **dineshs said:**
> Sorry to say that I dont understand the reason for this output

ok, tnx for trying.

---

### Post by alenn on 2010-07-27
I just need a way to set NM on default, can anyone help me

---

### Post by alenn on 2010-07-29
any help?

---

### Post by VastOne on 2010-08-05
> **alenn said:**
> I just need a way to set NM on default, can anyone help me

Can you explain a little more of what it is you actually want done?

---

### Post by alenn on 2010-08-06
> **VastOne said:**
> Can you explain a little more of what it is you actually want done?

I want to set my NM on defaults, I want it to be just like it was when I installed Ubuntu, I hope you understand.

and not just NM, but all it's settings, and everythinf connected to NM.

---

### Post by VastOne on 2010-08-06
> **alenn said:**
> I want to set my NM on defaults, I want it to be just like it was when I installed Ubuntu, I hope you understand.

and not just NM, but all it's settings, and everythinf connected to NM.

Did you remove it and try something else?  Did set up anything manual in the /etc/network/interfaces?  

What I am asking is what is different now?

---

### Post by alenn on 2010-08-07
> **VastOne said:**
> Did you remove it and try something else?  Did set up anything manual in the /etc/network/interfaces?  

What I am asking is what is different now?

yes, I made some changes in /etc/network/interfaces

---

### Post by VastOne on 2010-08-07
> **alenn said:**
> yes, I made some changes in /etc/network/interfaces

```
sudo gedit /etc/network/interfaces 
```

Make sure it looks like this again

```

auto lo
iface lo inet loopback

```


Then open Network Manager and make sure it will open


If you have removed Network Manager you can re install it with

```
sudo apt-get install -d --reinstall network-manager network-manager-gnome 
```

---

### Post by alenn on 2010-08-08
> **VastOne said:**
> ```
sudo gedit /etc/network/interfaces 
```

Make sure it looks like this again

```

auto lo
iface lo inet loopback

```


Then open Network Manager and make sure it will open


If you have removed Network Manager you can re install it with

```
sudo apt-get install -d --reinstall network-manager network-manager-gnome 
```

this is how it looks:

auto lo
iface lo inet loopback



#iface dsl-provider inet ppp
#pre-up /sbin/ifconfig eth1 up # line maintained by pppoeconf
#provider dsl-provider

#auto eth0
#iface eth1 inet manual

---

### Post by VastOne on 2010-08-08
> **alenn said:**
> this is how it looks:

auto lo
iface lo inet loopback



#iface dsl-provider inet ppp
#pre-up /sbin/ifconfig eth1 up # line maintained by pppoeconf
#provider dsl-provider

#auto eth0
#iface eth1 inet manual

So now if you open Network Manager, you should be back to the same.

---

### Post by alenn on 2010-08-09
> **VastOne said:**
> So now if you open Network Manager, you should be back to the same.

it is opened already, when I try to connect to internet it just says: " Network: Disconnected - you are now offline "

---

