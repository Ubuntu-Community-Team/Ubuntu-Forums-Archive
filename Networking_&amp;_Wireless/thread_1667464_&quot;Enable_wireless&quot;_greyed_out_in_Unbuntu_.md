---
title: "&quot;Enable wireless&quot; greyed out in Unbuntu Desktop 10.10"
date: 2011-01-14
forum: Networking &amp; Wireless
---

### Post by pretty_whistle on 2011-01-14
I'm running Windows Vista Home Premium32bit (this is what I'm right now and using the internet with).

I've installed Ubuntu Desktop 10.10 and it's installed next to Windows. 

My computer is a Compaq presario CQ50 210US, laptop.

Hardware -
 Atheros AR5007 802.11b/g Wifi adapter
 

 Adapter type -
 Ethernet 802.3
 

 
When I get onto Ubuntu's desktop, the menu showing the option to enable wireless is greyed out and because of it I can't connect to the internet via wireless - it won't let me enable wireless because of this.  The question is WHY won't it let me.

If it's a driver for the wireless card problem, then I might be in trouble since according to the list on ubuntu's wiki mine isn't on it, I think.  My card? is :

Hardware -
 Atheros AR5007 802.11b/g Wifi adapter
 

 Adapter type -
 Ethernet 802.3
 

 At least, this is what the system info pulled up when I did it in Windows.  I presume the Atheros thing is the wireless card - dunno for sure, noob here.  If this IS the card, then am I out of luck???  I'm thinking so, but let me know if I'm way off on this.

In Ubuntu, since I have no connection, I cannot update any drivers (if that would even help) since it relies on a connection to do it.  Can you do this separately from Windows??  That is, could I download it and install it over on Ubuntu??  Let me know this too.  I haven't tried to connect via wired, just haven't bothered since I wanted to use it via wireless.

So, I'm wanting to connect to the internet via wireless but it won't let me - it's greyed out as I said.  How to fix this is what I want to know.

Anyway, there's everything.  If you need to more info, let me know.

---

### Post by wojox on 2011-01-14
I have that card on one of my netbooks and it worked. Can you unplug your Ethernet cable from your Windows box and connect it to Ubuntu and update?

---

### Post by pretty_whistle on 2011-01-14
> **wojox said:**
> I have that card on one of my netbooks and it worked. Can you unplug your Ethernet cable from your Windows box and connect it to Ubuntu and update?

Both OS are installed on the same laptop, just clarifying that.

But yes, I can do that.  I'll try that right now.  Thanx.

---

### Post by pretty_whistle on 2011-01-14
Update :

I got on via wired and had updates installed.

Now the greyed out issue is corrected.

Now I have a new problem - 

I cannot connect via wireless because of a new issue of some type.  I filled in the info to 'connect to a hidden network' and when done the wireless icon sort of blinks (for lack of a better description).  The menu under it shows the hidden network SSID and the word "disconnect" is right under it like it means I'm connected, but I'm not connected when I try to surf.

What is wrong?

P.S.  Here's a better explanation of this new issue :

I believe what the wireless icon is doing is showing it's "trying to  connect".  As it keeps trying I periodically get a window coming up that  asks me for the WPA key.  It's already entered every time so I just hit  'connect' and it continues doing the same thing.

This is all it does now.  Just repeatedly does this and I can't surf.

Thanks.

---

### Post by wojox on 2011-01-15
Do any networks show up? You should see yours and click on it.

---

### Post by pretty_whistle on 2011-01-15
> **wojox said:**
> Do any networks show up? You should see yours and click on it.

After I entered the info to 'connect to a hidden network", the small window where I entered this info has a 'connect' button.  I hit that and the icon then shows it's trying to connect but never does - after a while of doing this it keeps asking for the WPA key though it's already been entered.

I wonder how to fix this.

---

### Post by pretty_whistle on 2011-01-15
> **wojox said:**
> Do any networks show up? You should see yours and click on it.

After I entered the info to 'connect to a hidden network", the small window where I entered this info has a 'connect' button.  I hit that and the icon then shows it's trying to connect but never does - after a while of doing this it keeps asking for the WPA key though it's already been entered.

I wonder how to fix this.

--------------------------
PLEASE DELETE THIS POST : this post is a duplicate of the one before it

---

### Post by pretty_whistle on 2011-01-15
> **wojox said:**
> Do any networks show up? You should see yours and click on it.

After I entered the info to 'connect to a hidden network", the small window where I entered this info has a 'connect' button.  I hit that and the icon then shows it's trying to connect but never does - after a while of doing this it keeps asking for the WPA key though it's already been entered.

I wonder how to fix this.

------------------------
PLEASE DELETE THIS POST : this post is a duplicate of the one before it

---

### Post by pretty_whistle on 2011-01-15
> **wojox said:**
> Do any networks show up? You should see yours and click on it.

After I entered the info to 'connect to a hidden network", the small  window where I entered this info has a 'connect' button.  I hit that and  the icon then shows it's trying to connect but never does - after a  while of doing this it keeps asking for the WPA key though it's already  been entered.

I wonder how to fix this.

-----------------------

PLEASE DELETE THIS POST : this post is a duplicate of the one before it

---

### Post by pretty_whistle on 2011-01-15
> **wojox said:**
> Do any networks show up? You should see yours and click on it.

After I entered the info to 'connect to a hidden network", the small  window where I entered this info has a 'connect' button.  I hit that and  the icon then shows it's trying to connect but never does - after a  while of doing this it keeps asking for the WPA key though it's already  been entered.

I wonder how to fix this.

------------
PLEASE DELETE THIS POST : this post is a duplicate of the one before it

---

### Post by pretty_whistle on 2011-01-16
I'm still needing a solution to my problem.

Anybody?

Thanks.


[s]P.S.  Please excuse duplicate posts 7, 8, 9, & 10.  These were duplicates of post #6 due to the recent website bug issue.  The duplicate posts have been reported for deletion. Thanks for understanding.[/s]

---

### Post by Spr0k3t on 2011-01-16
Check to see if you can connect to the wireless network when it is not hidden.  If you still can't... then you need to go into the router and recheck the settings.  Some routers have a mixed mode ability to allow for a/b/g or a combination there of... change that to allow only what your wireless card can achieve.  Also, if you are using WPA2, check to see if there is a difference when connection using AES or TKIP encryption.

---

### Post by pretty_whistle on 2011-01-16
> **Spr0k3t said:**
> Check to see if you can connect to the wireless network when it is not hidden.  If you still can't... then you need to go into the router and recheck the settings.  Some routers have a mixed mode ability to allow for a/b/g or a combination there of... change that to allow only what your wireless card can achieve.  Also, if you are using WPA2, check to see if there is a difference when connection using AES or TKIP encryption.


I have Ubuntu on dual boot with Windows.  Whenever I boot over to Windows, I can surf with no problem as usual, like right now.... and I'm using the same wifi, btw.  

It's some Ubuntu only issue.

Sorry I didn't make this clear before.

---

### Post by Spr0k3t on 2011-01-17
> **pretty_whistle said:**
> I have Ubuntu on dual boot with Windows.  Whenever I boot over to Windows, I can surf with no problem as usual, like right now.... and I'm using the same wifi, btw.  

It's some Ubuntu only issue.

This last part is the reason why you should check that information on the router.  There's a known issue with the band coupling.  Sometimes it connects, sometimes it doesn't, and sometimes it won't accept the password forever.

Simple tests to perform:
1. Make the SSID visible.
2. Change the wireless banding to allow for a single band.
3. Connect using AES and TKIP encryption.
4. Try using WPA instead of WPA2.

If you are still having problems after step 4, I'd be shocked.  Once you isolate the issue, you can then turn off the SSID visibility as well as change your WPA/2 settings.  Yes, this is a Linux only issue... you won't see the problem inside Windows.

---

### Post by pretty_whistle on 2011-01-17
> **Spr0k3t said:**
> This last part is the reason why you should check that information on the router.  There's a known issue with the band coupling.  Sometimes it connects, sometimes it doesn't, and sometimes it won't accept the password forever.

Simple tests to perform:
1. Make the SSID visible.
2. Change the wireless banding to allow for a single band.
3. Connect using AES and TKIP encryption.
4. Try using WPA instead of WPA2.

If you are still having problems after step 4, I'd be shocked.  Once you isolate the issue, you can then turn off the SSID visibility as well as change your WPA/2 settings.  Yes, this is a Linux only issue... you won't see the problem inside Windows.

FYI, in my case these settings for wifi are located in the modem, not the router.
  
 Problem is :
 #1.  SSID is currently set to 'hidden'.  Will try it though I dont see why this would help.
 #2.  Doesn't exist in settings window.
 #3.  Already using TKIP in Windows.  With Ubuntu 10.10, who knows &#8211; it doesn't say what it is nor does it allow any option to choose which to use.
 #4.  Already using WPA and not WPA2, therefore is n/a.
 

 That only leaves me with #1 above to try.  I made the SSID not hidden and now I have the ORIGINAL PROBLEM BACK that I started this thread about.  The 'enable wireless' is grayed over and it won't allow connecting because of it......... so much for updating Ubuntu 'solving it' as I had said &#8211; it's back!
 

 So, making the SSID 'visible' not only didn't work, it made the connection attempt WORSE.  At least before it was in the stage of 'trying to connect&#8221; and stuck there, now it won't even allow wireless connection to be enabled.  Ugg, but not surprising.
 

 Oh, and I never mentioned this 'ongoing weirdness' previously :  Ever since I installed Linux, my wireless laptop button acts odd, even in Windows.  Here's what it does :
 

 -while on Ubuntu, the wireless button light stays on even if I turn the button OFF.
 -when I boot to Windows, the wireless is set to 'connect automatically&#8221; -  it doesn't.  The wireless light will show OFF &#8211; even when I was just using Windows with it ON.  In other words, restart the PC and the ON light then turns into an OFF one.  Because of this, it no longer auto-connects when getting onto the Windows desktop &#8211; to get it to connect, I have to turn it to OFF (though it's showing OFF already), turn it back ON and THEN it shows ON and works ok and connects.
 

 Notice a commonality between Windows and Ubuntu 10.10 and this wifi button light?  In both cases it's showing OFF when it's ON and visa versa.
 

 And btw, I've tested the wifi button.  It is NOT a hardware/laptop issue.  When I rid Linux and put Windows back in ALONE on the hard drive, the thing works PERFECTLY.  But as soon as I put in Ubuntu, here it goes again.
 

 I wouldn't know if this wifi button light thing is part of, or connected to, the problem I've been having, but if it's not it makes for interesting conversation, so to speak.  If it IS part of whatever's wrong connecting, does anyone have a clue on how to fix this?

---

### Post by pretty_whistle on 2011-01-17
Anyone know what's wrong with this?

---

### Post by Spr0k3t on 2011-01-17
> **pretty_whistle said:**
> Problem is :
 #2.  Doesn't exist in settings window.

Have you gone into the modem/router (I'm guessing this is a 2wire) to make the change?  Can you detail the information on your exact setup from wall plug, to wires used, to equipment (exact make/model/firmware)... that information would help so I can try and find the screens you are looking through on the modem/router.

---

### Post by pretty_whistle on 2011-01-18
> **Spr0k3t said:**
> Have you gone into the modem/router (I'm guessing this is a 2wire) to make the change?  Can you detail the information on your exact setup from wall plug, to wires used, to equipment (exact make/model/firmware)... that information would help so I can try and find the screens you are looking through on the modem/router.
Here's a reply :


> Have you gone into the modem/router (I'm guessing this is a 2wire) to make the change?Yes.  I went into both the router and modem.  The router doesn't have anything wifi related in it, although I also looked for band anything - it has nothing.  The modem has wifi settings, none of which are band related, although I also looked in every other window but it wasn't there either.

> Can you detail the information on your exact setup from wall plug, to wires used, to equipment (exact make/model/firmware)Here it is :

Modem is :  Actiontec M1000
with plug in wireless/wifi module (enables modem to get wifi) :  Actiontech W1000

Router is :  D-Link EBR 2310

Wiring :

Modem has 3 wires/cables.  1 is the AC power, 2nd is the phone line (through which comes the internet), 3rd is an ethernet cable.  This ethernet cable is connected to the routers internet port.

Router wiring :

Router has 3 wires/cable.  1 is the AC power, 2nd is the ethernet cable just mentioned above which is plugged into the internet port, 3rd is another ethernet cable which is plugged into a port and goes to the DirectTV HD-DVR (this enables the DVR to get movie downloads that can be saved).

---

### Post by grahammechanical on 2011-01-18
Can I muddy the waters a bit? I may not have the answer but it may help. A little bit.

If you left click the network manager and you can see a list of available wireless networks then that means that your wireless adapter is working and it is detecting wireless networks.

On my system I see two wired connections and one wireless connection plus four wireless connections belonging to my neighbors.

I am connected to my modem by cable and wireless so I see in black letters the word "Disconnect" under one of the wired connections and under my wireless connection. Under the other wired connection I can see "disconnect" in grey letters. Therefore, I am connected.

Another point I would like to make. I am sorry if you already know this. If network manager has the wrong password it will fail to connect. You will not get a "wrong password" message. It will just ask you to authenticate again. [clicking Connect will only re-issue the password that has already been entered - edit]. It is an easy thing to enter the log in password and not the password or pass phrase of the modem. Also called the wireless key or WPA-PSK. It is usually printed on a label stuck on the bottom of the modem. I tripped up over this myself. This is why I mention it here.

Finally, when you right click the icon is there a tick mark against the line Enable Networking? If there is not, then the line Enable Wireless will be greyed out. I should think. It is not obvious, but selecting each of the two lines and clicking them has the effect of putting a tick mark against them and switching on both networking and wireless networking. Then reboot. Things sometimes start working after a reboot.

I am only sharing my experience in the hope that something my help you.

Regards.

---

### Post by pretty_whistle on 2011-01-18
> **grahammechanical said:**
> Can I muddy the waters a bit? I may not have the answer but it may help. A little bit.

If you left click the network manager and you can see a list of available wireless networks then that means that your wireless adapter is working and it is detecting wireless networks.

On my system I see two wired connections and one wireless connection plus four wireless connections belonging to my neighbors.

I am connected to my modem by cable and wireless so I see in black letters the word "Disconnect" under one of the wired connections and under my wireless connection. Under the other wired connection I can see "disconnect" in grey letters. Therefore, I am connected.

Another point I would like to make. I am sorry if you already know this. If network manager has the wrong password it will fail to connect. You will not get a "wrong password" message. It will just ask you to authenticate again. [clicking Connect will only re-issue the password that has already been entered - edit]. It is an easy thing to enter the log in password and not the password or pass phrase of the modem. Also called the wireless key or WPA-PSK. It is usually printed on a label stuck on the bottom of the modem. I tripped up over this myself. This is why I mention it here.

Finally, when you right click the icon is there a tick mark against the line Enable Networking? If there is not, then the line Enable Wireless will be greyed out. I should think. It is not obvious, but selecting each of the two lines and clicking them has the effect of putting a tick mark against them and switching on both networking and wireless networking. Then reboot. Things sometimes start working after a reboot.

I am only sharing my experience in the hope that something my help you.

Regards.

Thanks for the reply.  I'll cover it this way.........

> If you left click the network manager and you can see a list of  available wireless networks then that means that your wireless adapter  is working and it is detecting wireless networks.
I've read that in other threads.  I find this interesting and weird as well since I've not once been able to see any wireless networks.  Never - not even when I had the 'enable wireless' issue seemingly cleared up.

Dunno why this is and has been the case.

When I boot into Windows, it always works however.  It's just not working on Linux.

> Another point I would like to make. I am sorry if you already know this.  If network manager has the wrong password it will fail to connect. You  will not get a "wrong password" message. It will just ask you to  authenticate again. [clicking Connect will only re-issue the password  that has already been entered - edit]. It is an easy thing to enter the  log in password and not the password or pass phrase of the modem. Also  called the wireless key or WPA-PSK. It is usually printed on a label  stuck on the bottom of the modem. I tripped up over this myself. This is  why I mention it here.
I did do this.  In fact, in case of a typo I deleted the profile (or whatever it's called) and redid it.  I did this a few times so I think that's covered and this can't be the problem.

Good idea to mention it though since Ive done that in Windows before. Hahaha.

> Finally, when you right click the icon is there a tick mark against the  line Enable Networking? If there is not, then the line Enable Wireless  will be greyed out. I should think. It is not obvious, but selecting  each of the two lines and clicking them has the effect of putting a tick  mark against them and switching on both networking and wireless  networking. Then reboot. Things sometimes start working after a reboot.
The 'enable networking' has always had a check by it.  Go figure because it's not acting like it!

Wait!  You got me thinking here.......... hmmmmmmmm........

I'll try this :

I'll uncheck 'enable networking', reboot.  When back up I'll check it again.  See if that works and lets me check 'enable wireless'.  If not, I'll try this variation :

Uncheck 'enable networking' again, reboot.  When back up, check 'enable networking', then reboot......... when back up, see if it's now letting me check 'enable wireless'.

Thanx for the idea. :)  These computers, er uh OS's can be pesky with networking.  I recall nearly pulling my hair out with Windows back when.

Going to try this right now........

---

### Post by Spr0k3t on 2011-01-18
Trust me, it can be mind nerving figuring everything out.  I remember having the AR5007 on a Dlink card that I've since removed for another (more stable and much more linux friendly).  I had to muttle with hitting the kernel modules blacklisting one, compiling another, whitelisting yet a third only to have everything break on me with a kernel update.  I found it was all tied to the AR5007 and one of the variant of the chipset.  This however was back in very late 2007 when the AR5007 didn't even work out of the box without a custom kernel with different drivers.

So anyway, on to the visual analysis of your network.  Your modem is your wireless access point and you have a separate router.  Does the router handle the network address translating and IP assignments for the access point, or is the router configured only as a switch allowing the modem to handle the DHCP?  Just for grins and giggles, are you able to connect to the modem/ap if encryption is completely turned off?  To me it is definitely related to Linux, but also an issue somehow with the AP and the method of encryption used on WPA/2.  Are you able to see the wireless connection if you boot off a live disc?

---

### Post by pretty_whistle on 2011-01-18
> **pretty_whistle said:**
> Thanks for the reply.  I'll cover it this way.........


I've read that in other threads.  I find this interesting and weird as well since I've not once been able to see any wireless networks.  Never - not even when I had the 'enable wireless' issue seemingly cleared up.

Dunno why this is and has been the case.

When I boot into Windows, it always works however.  It's just not working on Linux.


I did do this.  In fact, in case of a typo I deleted the profile (or whatever it's called) and redid it.  I did this a few times so I think that's covered and this can't be the problem.

Good idea to mention it though since Ive done that in Windows before. Hahaha.


The 'enable networking' has always had a check by it.  Go figure because it's not acting like it!

Wait!  You got me thinking here.......... hmmmmmmmm........

I'll try this :

I'll uncheck 'enable networking', reboot.  When back up I'll check it again.  See if that works and lets me check 'enable wireless'.  If not, I'll try this variation :

Uncheck 'enable networking' again, reboot.  When back up, check 'enable networking', then reboot......... when back up, see if it's now letting me check 'enable wireless'.

Thanx for the idea. :)  These computers, er uh OS's can be pesky with networking.  I recall nearly pulling my hair out with Windows back when.

Going to try this right now........


Update :

I tried it.  EPIC FAIL.  Though I tried several times, including a new idea to uncheck 'enable networking', wait a few minutes, then recheck it again.

---

### Post by pretty_whistle on 2011-01-18
I've solved this whole thing -

The problem is this Ubuntu version has a bug, which I'll be reporting.

The bug is that when Ubuntu is installed, it makes a change in the BIOS.  It 'disables' the Internal Network Adapter Boot - a.k.a. network adapter.

With this disabled, the computer cannot connect via wifi.

Something else happens as well :

Because the network adapter gets disabled in the BIOS, the moment the user boots and reaches the desktop, the operating system senses the BIOS setting is on disable and goes accordingly and 'turns off' the 'wireless device', a.k.a. "wireless LAN" in Vista (in my case, this part is found in HP Wireless Assistant which is found in the Control Panel under "Network and Sharing Center").

This caused BOTH Ubuntu and Vista to not be able to connect via wifi.

Now it's FIXED!!!   :P  :P

So, I'm leaving this solution here for everyone with a similar issue.

---

### Post by pretty_whistle on 2011-01-20
Thanks for trying to help everyone.

---

### Post by grahammechanical on 2011-01-21
I did not think of it being disabled in the BIOS.I did know that my BIOS has the option to disable USB WIFI (onboard wireless adapter).

In your case the clue was in the fact that both Vista and Ubuntu were not connecting. I do not like the idea of an OS switching off a function in the BIOS without a massive warning. But, I suppose that this is necessary for laptops to save on battery power.

I glad you figured it all out. This thread might help others.

Regards.
P.S. In my opinion, if the OS has switched off the adapter, no matter how it does it (software or BIOS), then there should not be a tick mark against the line Enable Networking. How else are we to figure out what has happened?

---

### Post by pretty_whistle on 2011-01-21
> **grahammechanical said:**
> I did not think of it being disabled in the BIOS.I did know that my BIOS has the option to disable USB WIFI (onboard wireless adapter).

In your case the clue was in the fact that both Vista and Ubuntu were not connecting. I do not like the idea of an OS switching off a function in the BIOS without a massive warning. But, I suppose that this is necessary for laptops to save on battery power.

I glad you figured it all out. This thread might help others.

Regards.
P.S. In my opinion, if the OS has switched off the adapter, no matter how it does it (software or BIOS), then there should not be a tick mark against the line Enable Networking. How else are we to figure out what has happened?

What you said in the "P.S." I agree with.  I'd call that one a 'smaller bug' since it left 'enable networking' checked as if it were actually working.

It does make me wonder why wifi can be disabled via the BIOS without some warning to the user.  I mean, what if it were disabled and the user didn't want it to be?  You'd think there'd be a warning in case this ever happened.  Go figure.

---

### Post by beauty on 2011-04-23
I had similar symptoms to the above, so I thought I would report the solution here.

My Ubuntu 10.04 had been running fine, then all of a sudden I can't get online :mad:. First, you would want to check some basic things:
[LIST=1]
[*]network feed to your router is live?
[*]your router wireless works at all? (verify with a working computer)
[*]hardware switches on the front/side of your laptop have not disabled wireless?
[*]BIOS has wireless enabled?
[/LIST]
The only place I can find to check from within the GUI is:
>    Systems / Preferences / Network Connections
but that had "Wireless Networks" greyed out.

So the solution turned out to be: something weird to do with Windows 7.

A brief background: I had to do something unrelated in Windoze on this dual boot Lenovo Ideapad U550. I updated stuff like Java that prompted me, then when I powered down the OS forced a bunch of updates without asking and said not to turn off during the power down - then I rebooted in Windoze and it did "Stage 2" of updates. I actually had several iterations of this before it settled down. And, BTW, I had wireless connected the whole time.

So I boot up in Ubuntu and wireless is dead. Here are some basic checks you do in this case (the following is for a working system):
```
$ sudo lshw -C network
[sudo] password for user: 
  *-network               
       description: Ethernet interface
       product: AR8131 Gigabit Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: c0
       serial: 00:1f:16:2d:bb:35
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.1-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:29 memory:d3500000-d353ffff ioport:3000(size=128)
  *-network
       description: Wireless interface
       product: PRO/Wireless 5100 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 00:26:c6:1d:81:ec
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=192.168.1.100 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:28 memory:d2500000-d2501fff

```

When I had the problem the above included:
>  *-network [COLOR="Red"]DISABLED[/COLOR] 

Next, type:

```
$ rfkill list
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

When I had the problem it included:
> 1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: [COLOR="Red"]yes[/COLOR] 

This is what you get when the hard switch is off on your laptop. However, my switch was *on*. In fact, the LED indicator was on, and you could turn it off and on again with the hardware switch.

BTW, Fn-F5 is labelled as a wireless switch, but it doesn't do anything on my machine.

So here was my solution: Reboot back up into Windoze. I found wireless to also be disabled there (even though it was enabled last time I used it). So I clicked on the wireless icon, and a troubleshooter offers itself. So for literally the first time in my life that a troubleshooter robot did any good, it displayed a radio button for enabling wireless. I clicked it and wireless became enabled. Then I rebooted back into Ubuntu and wireless was happy again!
:guitar:

This is disturbing that all signs said A-OK, but wireless remained disabled in reality. If anybody knows how this can be I would be interested.

---

