---
title: "unable to connect to wireless networks in 9.10"
date: 2009-12-12
forum: Networking &amp; Wireless
---

### Post by whalen_eric on 2009-12-12
Hey!  I'm somewhat new to Ubuntu, and recently upgraded to 9.10 (about 1.5 months ago.)  Everything had been fine until I recently encountered the following...

After booting, my network manager is does not list or display wireless networks.  The icon is available, but when clicking on it no networks display.  Of course, this means I cannot connect to any networks either.  I have not been able to try connecting directly (eth0) but I'll try that as soon as I can and post how it goes.  

Also, curiously when shutting down, a new message displays saying "eric-laptop login: modem-manager: caught signal 15"...   I've never seen this display until this problem occured.  

Here's some info on my setup...
HP Compaq nc6220 laptop running 9.10 xubuntu with the 32 chipset.
When selecting the network manager icon the box is checked for 'enable wireless'
When I run iwconfig it states that the radio is off but I'm not certain how to enable it.

Please let me know if you need more information and I'm happy to get it.

Thanks for any help/solutions you can offer!  I really appreciate it!

---

### Post by acidblue on 2009-12-12
I'm having the same problem.
Funny thing is though, the Live CD detects all wireless networks,
But after HD install it doesn't.

Something is happening during the install thats messing with the wireless.

---

### Post by whalen_eric on 2009-12-13
Any Ideas?

---

### Post by Schamess on 2009-12-13
I'm having the same problem.  Installed Xubuntu on Dell mini, now it can't find the wireless signal.  I know the router is working because I'm online on my other computer via wireless.  Suggestions?

---

### Post by acidblue on 2009-12-14
I got mine to work!
I re-installed using the alternate live/install CD.
I think i chose expert mode, cause the install was
the old graphic/text mode.

It connected to my network during the install, just had to supply
my wep key, and installed additional packages.
However initially after the install I had the same problem, no
networks under the icon, but a reboot solved that.

Now am able to connect to wireless networks with no problem. 
I suggest you guys try the alternate install CD and report back.

Maybe choosing expert mode with the regular CD might do the 
trick also, but i haven't tried this.

---

### Post by MaindotC on 2009-12-14
I'm sorry I didn't see this thread sooner, but in the future instead of doing a re-install, please try the [Ubuntu Wireless Troubleshooting Guide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide).  Ubuntu should not have to be reinstalled in order to fix these types of issues.

---

### Post by whalen_eric on 2009-12-14
Hey, this guide is fantastic!!   Thanks so much for the link!

I feel like this should be on a sticky at the start of the networking section.

I do still have one problem...  I've found that my wireless connection's channel is set to 0.  I'm certain this is a problem, and the guide shows ways to set the channel/frequency, but I don't know what it should be set to.  

I'm in the US, should I assume that the channel should be set to 1 (frequency = 2.412)???

How can I find out what the frequency/channel should be?  (it isn't mentioned in the guide)
Or, is it set to channel 0 right now because of some other problem?

---

### Post by whalen_eric on 2009-12-14
Oh, another note is that when I run sudo iwconfig it states that the wireless connection is "unassociated" which I assume means that there is no connection because the frequency isn't set.  Is that right?

---

### Post by MaindotC on 2009-12-14
Association just means your wireless adapter needs to be connected to an access point.  [Check out this post](http://ubuntuforums.org/showpost.php?p=3094416&postcount=4) and view the whole thread for further details.  I don't know what channel you need - that is typically defined by the access point.

---

### Post by whalen_eric on 2009-12-14
I really appreciate the help!  

I went to the post and tried to manually connect the wireless, but the eth1 scan didn't show any networks available though.  I know that there are networks available as I'm on one with this computer right now.

I wish I could copy the info from my terminal but the only way I can get on this forum is through another computer.  So I'll try to provide as much information as possible.  

I fixed the radio so it is now on.  I'm also seeing in my network manager that there is an eth1 (wireless) option in my eth0 (wired) section, which I'm unable to delete.  Could that be part of the problem, in addition to what I've already described?

---

### Post by whalen_eric on 2009-12-14
also, when I run sudo ifconfig this is a portion of the output that might be a problem...
------------------------------------------------------------------------------
eth1     Link encap:ethernet  HWaddr 00:13:ce:c7:c4:a2
           inet6 addr: fe80::213:ceff:fec7:c4a2/64 Scope:Link
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
           RX packets:0    <my notes...  all the rest is basic stuff or packet zeros>

eth1avahi  Link encap:ethernet  HWaddr 00:13:ce:c7:c4:a2
           inet addr:169:254:11:63  Bcast:169:254:255:255  Mask:255.255.0.0
           UP BROADCAST RUNNING MULTICAST MTU:1500  Metric:1
           Interrupt:21 Base address:0x6000 Memory:d0100000=d0100fff
----------------------------------------------------------------

There is also an entry fo eth0 and lo, but I didn't type those because it's a pain in the butt.  I'm curious why there are two entries for eth1, esecially the entry "eth1avahi"

---

### Post by whalen_eric on 2009-12-14
Just to summarize, here are the symptoms I'm seeing...  (eth0 is my wired, eth1 is my wireless)

Upon booting, network manager does not display any wireless networks, and under wireless networks say "device not managed"

When I hit "connection information" in network manager it returns "no valid active connections found"

When I edit connections in network manager, under the Wired section, the network "ifupdown (eth1)" shows up right alongside "Auto eth0" which seems out of place.   In the wireless section, all previous wireless networks I've used appear.

When I run "sudo iwlist eth1 scan" the terminal returns "eth1 No scan results"

When I run "sudo iwconfig" the terminal shows eth1 is unassociated.

When I run "sudo ifconfig" the terminal shows an entry for eth0, two entries for eth1, and one entry for lo.  The results for eth1 are posted below.

------------------------------------------------------------------------------
eth1       Link encap:ethernet  HWaddr 00:13:ce:c7:c4:a2
           .         inet6 addr: fe80::213:ceff:fec7:c4a2/64 Scope:Link
           .         UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
           .         RX packets:0    <my notes...  all the rest is basic stuff or packet zeros>

eth1avahi  Link encap:ethernet  HWaddr 00:13:ce:c7:c4:a2
.         inet addr:169:254:11:63  Bcast:169:254:255:255  Mask:255.255.0.0
.         UP BROADCAST RUNNING MULTICAST MTU:1500  Metric:1
.         Interrupt:21 Base address:0x6000 Memory:d0100000=d0100fff
----------------------------------------------------------------

Thanks for any help you can provide!!!

---

### Post by Schamess on 2009-12-15
I found these two posts related to the dell mini, where I'm having the problem - maybe they will be helpful to others.  I haven't had time to try them out yet but will report back when I do.

Apparently, the wifi issue is a pretty common one with 9.10.

[http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html](http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html)

[http://www.bauer-power.net/2009/11/getting-wireless-to-work-on-dell-mini-9.html](http://www.bauer-power.net/2009/11/getting-wireless-to-work-on-dell-mini-9.html)

---

### Post by whalen_eric on 2009-12-21
Ok, now that I'm able to use a wired connection, I've been working through some of these fixes.  Nothing has worked yet.

(bump)  If anyone has other suggestions they are very welcome.  Thanks!

---

### Post by MaindotC on 2009-12-22
I know this doesn't really solve the problem but unless you're a developer and you're going to write a module for your wireless card you may want to just purchase a wireless card that is supported.  Check the [list of supported wireless cards](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported).  Again, it doesn't solve the problem but you're looking at $20 max for a decent card.

---

