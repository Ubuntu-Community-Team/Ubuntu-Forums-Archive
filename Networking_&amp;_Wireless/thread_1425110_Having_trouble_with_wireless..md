---
title: "Having trouble with wireless."
date: 2010-03-08
forum: Networking &amp; Wireless
---

### Post by Gabeyo on 2010-03-08
Hey guys, I just recently switch over to Ubuntu, I am a total noob. So far I really like it, it beats my vista in speed and when I use ethernet it work very quickly. Now I'm having some trouble with my wireless. I followed some directions on another thread regarding the MAC address for my router (a belkin G) and I cloned it from my computer. Now it connects and the internet is VERY slow. I tried to go to my girfriends apartment and connect to her wireless but it won't do it. It finds the router but refuses to connect, I'm current at home trying to fix this, any ideas?

---

### Post by Gabeyo on 2010-03-08
I reinstalled Ubuntu and now I cannot see any wireless networks.

---

### Post by Gabeyo on 2010-03-08
> **Gabeyo said:**
> I reinstalled Ubuntu and now I cannot see any wireless networks.
Still no luck. I've been frantically searching but so far nothing. I've been at this all day and I'm just about going to give up.

---

### Post by hansdown on 2010-03-08
Hi Gabeyo.

Which version of ubuntu are you using?

---

### Post by Gabeyo on 2010-03-08
Thank you for the reply! I'm using the newest one 9.1. 

WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0

03:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 02)

---

### Post by 2hot6ft2 on 2010-03-08
> **Gabeyo said:**
> Thank you for the reply! I'm using the newest one 9.1. 

WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Network controller
       product: **BCM4311** 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0

03:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 02)
You have a BCM4311 see this thread or search for BCM4311 in the forum
 [[SOLVED] Wireless Trouble Broadcom BCM4311 ]("http://ubuntuforums.org/showthread.php?t=1421191")

---

### Post by hansdown on 2010-03-08
When you re-installed, did you install ndiswrapper ?

Edit:

2hot6ft2 has a good link.

---

### Post by Gabeyo on 2010-03-08
> **hansdown said:**
> When you re-installed, did you install ndiswrapper ?

Edit:

2hot6ft2 has a good link.

How do I go about doing this? I'm attempting to install Network manager since I put in Wicd and it didn't work out for me too well.

I rebooted and now my Wifi light is on, still no wireless showing up though.

---

### Post by 2hot6ft2 on 2010-03-08
> **Gabeyo said:**
> How do I go about doing this? I'm attempting to install Network manager since I put in Wicd and it didn't work out for me too well.

I rebooted and now my Wifi light is on, still no wireless showing up though.
Can you connect to a wired connection?
If you can hook it up and when it's connected run this in a terminal
```
sudo apt-get install network-manager network-manager-gnome
```
Applications > Accessories  > Terminal
When it finishes you will need to reboot.

Or were you referring to reading the thread that was linked to until you came across the link to this thread in post #9
[BroadcomWireless Driver]("http://ubuntuforums.org/showthread.php?t=1417733")
and found this to run in the terminal in post #4
```
sudo apt-get install bcmwl-kernel-source
```
Copy and paste it so you don't have any typos.

---

### Post by hansdown on 2010-03-08
ndiswrapper is in synaptic package manager.

---

### Post by Gabeyo on 2010-03-08
Ok, I have success! I went ahead and installed the network manager now I can connect to my wifi. I went over to my girlfriends place and I cannot connect to hers. I can connect to mine fine now and it runs very well. If this can't be solved then there is no problem, I'll take what I can get.

The wireless does show up but when I click it, it doesn't connect.

---

### Post by 2hot6ft2 on 2010-03-08
> **Gabeyo said:**
> Ok, I have success! I went ahead and installed the network manager now I can connect to my wifi. I went over to my girlfriends place and I cannot connect to hers. I can connect to mine fine now and it runs very well. If this can't be solved then there is no problem, I'll take what I can get.

The wireless does show up but when I click it, it doesn't connect.
Does she use encryption? WEP WPA etc. if so then you need the key or passphrase to connect to hers. And if she has MAC filtering enabled on her router she would have to allow your adapters MAC Address to get an IP Address assigned.

When you're satisfied that your issue is resolved don't forget to mark the thread as solved using the Thread Tools at the top of the thread and enjoy.

---

### Post by Gabeyo on 2010-03-08
She does not use encryption, it is an unsecured network. Could it be my settings?

---

### Post by 2hot6ft2 on 2010-03-08
> **Gabeyo said:**
> She does not use encryption, it is an unsecured network. Could it be my settings?
If it's unsecured and the router isn't setup to filter MAC Addresses, and it's not setup to only allow so many addresses by DHCP and they are all being used then it may be on your end but there are so many possibilities to consider.

Mine filters by MAC Addresses and I only allow for 1 misc. connection once in a while.

Otherwise, if you haven't disabled roaming it should connect.
System > Administration > Network
should show "Roaming mode enabled" as in the pic below.

---

### Post by Gabeyo on 2010-03-08
> **2hot6ft2 said:**
> If it's unsecured and the router isn't setup to filter MAC Addresses, and it's not setup to only allow so many addresses by DHCP and they are all being used then it may be on your end but there are so many possibilities to consider.

Mine filters by MAC Addresses and I only allow for 1 misc. connection once in a while.

Otherwise, if you haven't disabled roaming it should connect.
System > Administration > Network
should show "Roaming mode enabled" as in the pic below.
It doesn't seem like I have "network" under Administration. Is there a program I don't have?

---

### Post by 2hot6ft2 on 2010-03-08
> **Gabeyo said:**
> It doesn't seem like I have "network" under Administration. Is there a program I don't have?
I use a different version of ubuntu so sometimes I take for granted that everyone has the things I do. You can install it with
```
sudo apt-get install network-admin
```
in a terminal
Applications > Accessories > Terminal

---

### Post by Gabeyo on 2010-03-08
> **2hot6ft2 said:**
> I use a different version of ubuntu so sometimes I take for granted that everyone has the things I do. You can install it with
```
sudo apt-get install network-admin
```in a terminal
Applications > Accessories > Terminal
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package network-admin


I'll see if I can look it up through Synaptic. You've been a big help, thank you.

---

### Post by 2hot6ft2 on 2010-03-08
> **Gabeyo said:**
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package network-admin


I'll see if I can look it up through Synaptic. You've been a big help, thank you.
You're welcome. Strange, I figured it would be in the regular repositories. I use Ultimate Edition so I have some other repositories as well as the normal ubuntu ones.

It's listed as gnome-network-admin so this should work
```
sudo apt-get install gnome-network-admin
```
I was going by the actual command that is executed when clicking on it in the menu.

---

### Post by Gabeyo on 2010-03-08
Looks like roaming is enabled. I'll have to search around to see if anyone else has had this happen to them.

---

### Post by 2hot6ft2 on 2010-03-08
> **Gabeyo said:**
> Looks like roaming is enabled. I'll have to search around to see if anyone else has had this happen to them.
Ok, tempting as it may be you shouldn't use System > Administration > Network to make changes to your settings.

Have fun

---

### Post by Gabeyo on 2010-03-08
So I decided to reboot it and it went back to not working. The password isn't working and I just reseted it. I was so happy and now I'm bummed.

---

