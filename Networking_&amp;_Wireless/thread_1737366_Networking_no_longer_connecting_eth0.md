---
title: "Networking no longer connecting eth0"
date: 2011-04-23
forum: Networking &amp; Wireless
---

### Post by lowebb on 2011-04-23
I can no longer connect to the network with Ubuntu. I literally did nothing. Windows on the same machine works fine

sudo dhclient eth0 returns 

DHCPOFFER of 192.168.1.99 from 192.168.1.254
DHCPREQUEST of 192.168.1.99 on eth0 to 255.255.255.255 port67
DHCPNAK from 192.168.1.254

---

### Post by lowebb on 2011-04-23
My Virtualbox XP instance running in Ubuntu can get a dhcp address fine also. 

What the hell???

---

### Post by KegHead on 2011-04-23
Hi!

What version are you running?

Dsl, cable or wifi problem?

KegHead

---

### Post by varunendra on 2011-04-24
> **lowebb said:**
> 
sudo dhclient eth0 returns 

DHCPOFFER of 192.168.1.99 from 192.168.1.254
DHCPREQUEST of 192.168.1.99 on eth0 to 255.255.255.255 port67
DHCPNAK from 192.168.1.254

> **lowebb said:**
> My Virtualbox XP instance running in Ubuntu can get a dhcp address fine also. 

Both your posts suggest you are at least connected to your modem/router and DHCP is working fine. Are you able to browse from the XP in VBox?

What do these say:
```
route -n
```
```
cat /etc/resolv.conf
```
```
ping -c 4 google.com
```

---

### Post by lowebb on 2011-04-24
None of them queries show anything useful, first 2 empty and thrid unknown host.

I managed to get eth0 working again by hard reseting my router, but that only fixed it until I rebooted Ubuntu and I dont wanna have to reset the thing every day.


Its only happening on Ubuntu, has something changed recently in an update to do with networking?

---

### Post by lowebb on 2011-04-24
Ok my router (bt homehub) had an auto firmware update on 21/04/2011. This is looking highly likely to be the culprit. Not that that helps me, but hopefully someone may be able to tell me wants changed and a workaround.

I also think it is related to the fact I reboot into win07 and back into Ubuntu regularly

---

### Post by tushargkwd on 2011-04-24
BUMP:::

I had the same problem too.....But I formatted my previous installation and installed a fresh one.....Currently on Lucid Lynx and very happy  :)

---

### Post by doas777 on 2011-04-24
> **lowebb said:**
> Ok my router (bt homehub) had an auto firmware update on 21/04/2011. This is looking highly likely to be the culprit. Not that that helps me, but hopefully someone may be able to tell me wants changed and a workaround.

I also think it is related to the fact I reboot into win07 and back into Ubuntu regularly
there are a couple things in your posts that indicate possible issues, so just wanted to check with you. 
1) in virtualbox, is your networking set to bridged, or nat? 
2) is your PC directly connected to your cablemodem, or is it a real router?
cablemodems don't usually like it when you switch the device they are connected to, and in your case, rebooting into another OS may qualify, especially if you have changed the MAC in ubuntu. to test this, reboot until you have a failure, and then unplug the cablemodem for > 1 minute and power it back up. 

just a few thoughts.

---

### Post by alanbboyd on 2011-04-25
I've run into the same problem & I have a BT HomeHub 2.0 - found your post trying to Google for any recent problems with Ubuntu, DHCP & BT HomeHubs :).

Everything working fine until Sunday morning (24th April) when my (wired) desktop could not connect (Ubuntu 10.10). Assuming a problem with the HomeHub I rebooted that, but it made no difference.

Further digging found:


[LIST]
[*]Booting into XP on the same box everything worked fine.
[*]My dual-boot laptop (Ubuntu 10.10 & XP) also had the same problem on a wireless connection to the router - everything ok on XP, no connection on Ubuntu.
[*]a wireshark trace shows the Ubuntu client making a DHCP request and the HomeHub making a DHCP offer for the correct address, but the client either doesn't see it or ignores it, and then makes another DHCP request. This is followed by a NACK from the router and the same again until the client times out.
[*]bringing my laptop into work this morning everything works fine on the wireless here, so it's definitely the HomeHub.
[*]I ran a system update on the Ubuntu laptop over the work wireless network and noticed one of the updates was to the DHCP client. May be coincidence but I'll check if this has made any difference tonight.
[/LIST]

I meant to check whether the firmware on my HomeHub had been recently upgraded but haven't got round to it yet.

If there's any change or new information I'll let you know.

---

### Post by lowebb on 2011-04-26
> **doas777 said:**
> there are a couple things in your posts that indicate possible issues, so just wanted to check with you. 
1) in virtualbox, is your networking set to bridged, or nat? 
2) is your PC directly connected to your cablemodem, or is it a real router?
cablemodems don't usually like it when you switch the device they are connected to, and in your case, rebooting into another OS may qualify, especially if you have changed the MAC in ubuntu. to test this, reboot until you have a failure, and then unplug the cablemodem for > 1 minute and power it back up. 

just a few thoughts.

1) Bridged
2) 'Real' router. I use the term 'Real' loosely as its a BT Homehub and BT are pretty pathetic. But it hook directly to an ASDL2 line


@alanbboyd and anyone else with specific issues with the BT Homehub Router since 21/04/2011, I've opened a thread on the BT forums about this issue. I've had no responses but the only way to get BT to waken up is to put as many voices to it as possible. I'd appreciate everyone to post and keep it high in the forum

[http://community.bt.com/t5/BB-Speed-Connection-Issues/BT-HomeHub-firmware-upgrade-broken-network-connectivity-Ubuntu/td-p/176473](http://community.bt.com/t5/BB-Speed-Connection-Issues/BT-HomeHub-firmware-upgrade-broken-network-connectivity-Ubuntu/td-p/176473)

---

### Post by lowebb on 2011-04-26
> **alanbboyd said:**
> I've run into the same problem & I have a BT HomeHub 2.0 - found your post trying to Google for any recent problems with Ubuntu, DHCP & BT HomeHubs :).

Everything working fine until Sunday morning (24th April) when my (wired) desktop could not connect (Ubuntu 10.10). Assuming a problem with the HomeHub I rebooted that, but it made no difference.

Further digging found:


[LIST]
[*]Booting into XP on the same box everything worked fine.
[*]My dual-boot laptop (Ubuntu 10.10 & XP) also had the same problem on a wireless connection to the router - everything ok on XP, no connection on Ubuntu.
[*]a wireshark trace shows the Ubuntu client making a DHCP request and the HomeHub making a DHCP offer for the correct address, but the client either doesn't see it or ignores it, and then makes another DHCP request. This is followed by a NACK from the router and the same again until the client times out.
[*]bringing my laptop into work this morning everything works fine on the wireless here, so it's definitely the HomeHub.
[*]I ran a system update on the Ubuntu laptop over the work wireless network and noticed one of the updates was to the DHCP client. May be coincidence but I'll check if this has made any difference tonight.
[/LIST]

I meant to check whether the firmware on my HomeHub had been recently upgraded but haven't got round to it yet.

If there's any change or new information I'll let you know.


Just to help out and highlight a point, I did more than reboot my router, I reset it, meaning I lost all settings. This fixed it until the next time I boot into Windows, at which point it bombed again on reboot into Ubuntu

---

### Post by blueskyabove on 2011-04-26
I've got exactly the same (baffling) problem with my BT HomeHub 2 and Ubuntu 10.10. - worked fine last Wednesday (20th April) and won't work today (26th April).  Can see the router just fine but won't connect wirelessly or wired but will connect to BT Open Zone which is enabled on my hub and a couple of other hubs nearby.  The OpenZone connection is full strength (which is my hub) - none of the neighbouring connections has ever been a full strength signal. Very odd.  

Checked to see if it was my Ubuntu set up by running the machine off the installation disk and got exactly the same symptoms.  My HomeHub also updated its firmware some time on the 21st April so, given that nothing else has changed (my windows 7 laptop has continued to work flawlessly) I am driven to the conclusion, like other correspondents here, that the HomeHub update is the culprit.

On to BT now to complain!

---

### Post by yossell on 2011-04-26
I had exactly the same problem, same router. Here's what worked for me:

[http://ubuntuforums.org/showthread.php?t=1736079](http://ubuntuforums.org/showthread.php?t=1736079)

---

### Post by blueskyabove on 2011-04-26
Well, having made a complaint online to BT today (26th April), I got a call back. Basically, they agreed that probably the upgrade to the BT Home Hub has changed the way the router works with Ubuntu/Linux so that it no longer works. They also said that they support Windows and Mac but they don't support Linux - a circumstance shared by Mac users a while ago until BT decided to support their operating system.

There seem to be two options from here: firstly, to put pressure on BT to accept Ubuntu/Linux as a system to support; secondly, replace the BT HomeHub with another BT compatible wireless router which doesn't update from time to time via BT.  Alternatively as a thrid option, I suppose those of us who care enough could simply take business away from BT and go elsewhere provided the alternative did support Linux.

---

### Post by yossell on 2011-04-26
@blueskyabove

Did the fix that worked for me not work for you?

sadly, BT's response doesn't surprise me. Linux is not a big priority for these people alas. I wonder whether it's possible to use some other router with BT broandband, one that you know to be Linux-compatible.

---

### Post by alanbboyd on 2011-04-26
> **lowebb said:**
> Just to help out and highlight a point, I did more than reboot my router, I reset it, meaning I lost all settings. This fixed it until the next time I boot into Windows, at which point it bombed again on reboot into Ubuntu

Ok, I've finally resolved the problem on my router.

The logs confirmed that the firmware on the HomeHub was updated sometime on 23/04/11 to 4.7.5.1.83.3.18 (Type B). I hadn't been around that day so the first time the fault was noticed was the morning of the 24th.

After the initial digging in my previous post I noticed that on the wireless laptop, while I couldn't connect to my own wireless network, it would fall back to connecting to the BTFON SSID running on the same HomeHub. So the HomeHub was handing out DHCP allocated IP addresses to my Ubuntu laptop, just not in the required way.

So next:

[LIST=1]
[*]I manually configured my Ubuntu desktop with the correct IP settings to connect to the HomeHub, which gave me a working connection.
[*]I logged onto the HomeHub web interface and backed up the Hub settings to file.
[*]next I Reset the HomeHub (settings only).
[*]once the HomeHub rebooted I put the Ubuntu desktop back to using DHCP for IP allocation, and now it connected fine, although with the "factory" IP settings.
[*]with a working connection I tried restoring settings from backup. Went through the process, rebooted the router and waited, but was back to no IP address being allocated from the HomeHub.
[/LIST]
Much swearing ensued.

So figuring an incompatibility between the updated HomeHub firmware and the "old" settings file I went back and ran through 3. and 4. again to get a "default" working HomeHub and reconfigured all my Hub settings by hand.

Took a little time but I now have everything back working as it was before the firmware update at the weekend. 

It's been a pain in the backside, but at least it's fixed now. I suspect the best result you'll get from BT is advice to reset the HomeHub to factory settings, so the above may help shortcut any further grief.

HTH

---

### Post by lowebb on 2011-04-27
@alanbboyd

Are you running a dual boot? If so log into Windows and then back into Ubuntu. I bet that breaks it again. I have a working theory the new firmware doesnt like 2 machines having the same mac address

---

### Post by doas777 on 2011-04-27
> **lowebb said:**
> @alanbboyd

Are you running a dual boot? If so log into Windows and then back into Ubuntu. I bet that breaks it again. I have a working theory the new firmware doesnt like 2 machines having the same mac address

well that makes it easier. just install and use MacChanger on the ubuntu install.
[http://www.ubuntugeek.com/macchanger-utility-for-manipulating-the-mac-address-of-network-interfaces-included-gui-utility.html](http://www.ubuntugeek.com/macchanger-utility-for-manipulating-the-mac-address-of-network-interfaces-included-gui-utility.html)

---

### Post by alanbboyd on 2011-04-27
> **lowebb said:**
> 
Are you running a dual boot? If so log into Windows and then back into Ubuntu. I bet that breaks it again. I have a working theory the new firmware doesnt like 2 machines having the same mac address

Apologies - you're quite correct. Both desktop & laptop are dual boot with XP. I booted the desktop into Windows that back into Ubuntu and.... no DHCP :(

I've avoided booting the laptop into Windows and it continues to work in Ubuntu with DHCP quite happily after a dozen reboots.

Looking again at the packet traces of the DHCP process when it fails, the client makes a DHCP request for the address it previously had (172.31.220.1) which is NAK'd by the HomeHub - the HomeHub says the address is already in use.

The HomeHub should only care what the MAC address of the client is, so I'm baffled. I've not yet found any significant difference in the successful Ubuntu DHCP transactions vs the unsuccessful ones that would indicate where the problem lies, but I've been short of time.

As a workaround for the moment I'm going to leave the laptop in Ubuntu only and hard-set the desktop IP address. Not ideal, but I need to be able to work.

I'll take some further packet traces of the DHCP transaction in both Windows & Ubuntu when I can and see if there's anything to be seen.

Not pleased.

---

### Post by blueskyabove on 2011-04-28
OK, following various  bits of advice here, I've set the IPv4 settings manually with the HomeHub's IP address etc.  And, voila and hallalujah, I can now connect to the hub which I could not do before.  A step forward but, alas, no connection to the web or, indeed, to the HomeHub home page itself.  Re-set the Hub - no change.  I'm now lost.  My Ubuntu laptop is just that - no dual boot but I still can't get it to work.

Not good from BT at all.  But I must also say that (in my humble view), if Ubuntu is really going to penetrate a true mass market - which it is easily good enough to do, then it has got to get to the point where things like this can be fixed without apparently highly technical fiddling around with things and obscure settings and command lines, most of which are way beyond the average user - like me.

---

### Post by alanbboyd on 2011-05-03
(Apologies for the slow response - I've been away)

> **blueskyabove said:**
> OK, following various  bits of advice here, I've set the IPv4 settings manually with the HomeHub's IP address etc.  And, voila and hallalujah, I can now connect to the hub which I could not do before.  A step forward but, alas, no connection to the web or, indeed, to the HomeHub home page itself.  Re-set the Hub - no change.  I'm now lost.  My Ubuntu laptop is just that - no dual boot but I still can't get it to work.

Not trying to teach anyone to suck eggs :), but.... in addition to configuring your static IP address, have you also configured a default route and a DNS server?

If not, you'll need your DNS server to be set to the IP address of your HomeHub, and you'll need to add a route with:


[LIST]
[*]Address: 0.0.0.0
[*]Netmask: 0.0.0.0
[*]Gateway: the IP address of your HomeHub
[*]Metric: leave blank
[/LIST]

> **blueskyabove said:**
> Not good from BT at all.  But I must also say that (in my humble view), if Ubuntu is really going to penetrate a true mass market - which it is easily good enough to do, then it has got to get to the point where things like this can be fixed without apparently highly technical fiddling around with things and obscure settings and command lines, most of which are way beyond the average user - like me.

The problem has come about due to something BT have done with the HomeHub DHCP service in the recent software update - and from other reports it may not be limited to Ubuntu. I agree that a lot of what has been discussed is overtly technical, but this is to try and workaround the problem until BT (hopefully) provide a fix for the HomeHub.

The problem was not caught before the firmware update was released because (as BT have stated) Ubuntu is not an officially supported OS. If the same problem had been evident in XP or Win 7 then pre-release testing of the HomeHub firmware would likely have caught it.

Not trying to take sides - I've been a BT internet customer since dial-up - but in this case I think the fault lies with BT. DHCP should "just work", so I'd be interested to know what changes they've made to to the HomeHub's DHCP service in the update.

cheers

---

### Post by blueskyabove on 2011-05-04
Well, to my immense surprise it's all working again this morning (4th May).  After trying and failing to get the manual settings entered and working (many thanks friends!), I despaired and as a last throw of the dice restored the "automatic (dhcp)" setting.  In other words, back to the status quo before the HomeHub stopped working with Linux.  And, it works.  No sign of a further firmware update on the hub since 21st April which was when the problems started.

As I said in an earlier message: hallelujah.  Very strange - any ideas anybody?

Post Script.  Missed out an action: I deleted, from the HomeHub's DHCP table, the one Unknown device which, by a process of elimination, was my Ubuntu laptop.  It was after that action that I restored the default settings to the Ubuntu wireless connection and when it all started working again.  The "unknown" device with its MAC address etc. has now reappeared in the DHCP table on the hub but, do I care?  No I don't 'cos it works.

PPS: Also, I now recall, I had been unable to connect to a couple of key Ubuntu/Linux repositories while attempting to update the system over the last 4 or 5 weeks.  This was a new event at the time and it puzzled me and it predated the HomeHub problems.  Currently, the system update is working fine and dandy and, as I type, is updating to Ubuntu 11.04.  Very odd all round

---

### Post by wilbyforce on 2011-05-16
This thread seems to have gone cold. My Ubuntu wireless is still dead despite my trying just about everything I can find on here. Any more info anyone? :confused:

---

