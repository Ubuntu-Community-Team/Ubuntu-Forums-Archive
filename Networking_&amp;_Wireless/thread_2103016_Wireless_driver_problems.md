---
title: "Wireless driver problems"
date: 2013-01-08
forum: Networking &amp; Wireless
---

### Post by binaryCrusader00 on 2013-01-08
I installed unbuntu as my main OS and i seem to have gotten myself into some trouble.
My desktop uses a wireless adapter to connect to the internet, and i cant install the drivers since they are in exe format. Ive tried installing dosemu and wine, but to no avail.
If it is relevant at all its an old dimension c521.

But how can i install the drivers?

---

### Post by squakie on 2013-01-08
Actually, you wouldn't.  What we need to do is find you the Linux driver.  So, please post the output of the following back here:

lspci | grep Network

iwconfig

ifconfig

---

### Post by binaryCrusader00 on 2013-01-08
Apologies for images instead of text, and for the terrible camera.

---

### Post by binaryCrusader00 on 2013-01-08
Forgot the lspci

---

### Post by squakie on 2013-01-09
I don't see anything in either of those outputs that indicates a wireless adapter.  It shows the regular ethernet controller and a Conextant modem.

Did you install a wireless card?  If so, can you look on the card for the maker/model/revision?

---

### Post by binaryCrusader00 on 2013-01-09
Yeah i did, its a linksys/cisco wireless adapter model ae1200.

---

### Post by Bucky Ball on 2013-01-09
[I]Thread moved to [B]Networking & Wireless

[/B][/I]Have you got access to an ethernet cable? Are you sure the card is seated properly and antennae wires are attached correctly?

---

### Post by binaryCrusader00 on 2013-01-09
Yeah, it just plugs right in. It came with an install disk which im trying to run to install the driver.
And the ethernet cable, yes but not at the moment

---

### Post by grahammechanical on 2013-01-09
Why are you trying to install wireless drivers? Because the wireless adapter came with a disk that had drivers on it. Is that not the reason? That is the way things are done in the Microsoft world. But not in the Linux world.

Usually drivers come as part of the operating system. That may be the situation for you.

If you click on the Network manager icon in the top panel (two arrows going in opposite directions) you may see a list of wireless access points. Make sure you have both Networking and WiFi enabled. If you see a list of available wireless access points, then the driver is installed as part of the OS and we know that the wireless adapter is recognised.

With 12.04 and 12.10 we can go to System Settings>Networking and switch the wireless adapter off and on from there as well as make connections.

We can also run the command

```
nm-tool
```

Does that show a list of wireless access points?

Regards.

---

### Post by verymadpip on 2013-01-09
Is this a USB wireless adapter?  If so "lsusb" will identify it for us.
Can you connect to the internet without installing the driver?

I have found wireless in Ubuntu to pretty much work out of the box 8 out of 10 times.  Perhaps I've been lucky.  I have had to fiddle with stuff periodically.

Yet again, I am spectacularly too slow typing...

---

### Post by binaryCrusader00 on 2013-01-09
Is this a USB wireless adapter? If so "lsusb" will identify it for us.
Can you connect to the internet without installing the driver?

I have found wireless in Ubuntu to pretty much work out of the box 8 out of 10 times. Perhaps I've been lucky. I have had to fiddle with stuff periodically.

Yet again, I am spectacularly too slow typing...

Yes, I am using a USB wireless adapter


Why are you trying to install wireless drivers? Because the wireless adapter came with a disk that had drivers on it. Is that not the reason? That is the way things are done in the Microsoft world. But not in the Linux world.

Usually drivers come as part of the operating system. That may be the situation for you.

If you click on the Network manager icon in the top panel (two arrows going in opposite directions) you may see a list of wireless access points. Make sure you have both Networking and WiFi enabled. If you see a list of available wireless access points, then the driver is installed as part of the OS and we know that the wireless adapter is recognised.

With 12.04 and 12.10 we can go to System Settings>Networking and switch the wireless adapter off and on from there as well as make connections.

We can also run the command

nm-tool
Does that show a list of wireless access points?

Regards.

Ill try this when I get home, ill try and post results


Thanks a ton everybody for the help, im extremely new to this

---

### Post by flash63 on 2013-01-09
Hello,
Linsys/Cisco USB WiFi Adapter AE1200 and AE2500 are Broadcom based devices. You need ndiswrapper and the Windows-Driver.

[http://homesupport.cisco.com/en-us/support/adapters/AE1200](http://homesupport.cisco.com/en-us/support/adapters/AE1200)

---

### Post by squakie on 2013-01-09
From what I saw looking on the net, flash63 is correct this time.  There is very limited support for the chipset involved and only of certain versions of the adapter (see brcmfmac).  Ndiswrapper does seem to be the recommended choice for many Linux derivatives on the net.

First, determine if you installed the "normal" Ubuntu (32 bit) or if you installed the 64-bit version.  Unless some things have changed, you need to know this for 2 reasons:

[LIST]
[*]ndiswrapper only supports XP drivers in the vast majority of cases
[*]ndiswrapper expects the OS architecture (32 or 64 bit) and the driver architecture (32 or 64 bit) to match
[/LIST]
So, I would first download the zip file that is the XP driver file.  Next, extract the .inf and .sys files to your desktop.  Hopefully the architecture (32 or 64 bit) will match your installed Ubuntu.



Now, install ndiswrapper and ndisgtk.  Since you appear to have a wired connection, you should be able to this via the package manager (I use synaptic package manager).  Using the package manager should insure that the dependencies are all installed as well.


Next, start up ndisgtk.  Click add (or perhaps it's new), then point it to ~.Desktop/<driver .inf file>.  It should load the driver and enable ndiswrapper.


Close out of ndisgtk.


Check network manager:

[LIST]
[*]does "Enable Wireless" now appear?  If so, be sure it is clicked as enabled.
[*]wait a few seconds, then check for wireless networks it detects and try to connect.
[/LIST]
If none of this works, or you have other questions, don't hesitate to post back.  We're here to try to help.  I'm not familiar with your adapter, but we can hopefully get it working for you.


One of the threads on the net for this suggests that certain security types on the router may not work with this adapter.  Let's just try to get it showing available networks, then go from there.

---

### Post by binaryCrusader00 on 2013-01-09
> **squakie said:**
> From what I saw looking on the net, flash63 is correct this time.  There is very limited support for the chipset involved and only of certain versions of the adapter (see brcmfmac).  Ndiswrapper does seem to be the recommended choice for many Linux derivatives on the net.

First, determine if you installed the "normal" Ubuntu (32 bit) or if you installed the 64-bit version.  Unless some things have changed, you need to know this for 2 reasons:

[LIST]
[*]ndiswrapper only supports XP drivers in the vast majority of cases
[*]ndiswrapper expects the OS architecture (32 or 64 bit) and the driver architecture (32 or 64 bit) to match
[/LIST]
So, I would first download the zip file that is the XP driver file.  Next, extract the .inf and .sys files to your desktop.  Hopefully the architecture (32 or 64 bit) will match your installed Ubuntu.



Now, install ndiswrapper and ndisgtk.  Since you appear to have a wired connection, you should be able to this via the package manager (I use synaptic package manager).  Using the package manager should insure that the dependencies are all installed as well.


Next, start up ndisgtk.  Click add (or perhaps it's new), then point it to ~.Desktop/<driver .inf file>.  It should load the driver and enable ndiswrapper.


Close out of ndisgtk.


Check network manager:

[LIST]
[*]does "Enable Wireless" now appear?  If so, be sure it is clicked as enabled.
[*]wait a few seconds, then check for wireless networks it detects and try to connect.
[/LIST]
If none of this works, or you have other questions, don't hesitate to post back.  We're here to try to help.  I'm not familiar with your adapter, but we can hopefully get it working for you.


One of the threads on the net for this suggests that certain security types on the router may not work with this adapter.  Let's just try to get it showing available networks, then go from there.

Thanks, i got to installing the driver but it gives me a "module ndiswrapper not found" yet it shows up in my software center. I dont quite understand

---

### Post by squakie on 2013-01-09
> **binaryCrusader00 said:**
> Thanks, i got to installing the driver but it gives me a "module ndiswrapper not found" yet it shows up in my software center. I dont quite understand
 
Oops - forgot the following you need to do before ndisgtk:
 
sudo modprobe ndiswrapper
 
sudo echo ndiswrapper >> /etc/modules
 
Then things should go better (I think).

---

### Post by binaryCrusader00 on 2013-01-09
> **squakie said:**
> Oops - forgot the following you need to do before ndisgtk:
 
sudo modprobe ndisgtk
 
sudo echo ndiswrapper >> /etc/modules
 
Then things should go better (I think).

Should i uninstall ndiswrapper and do this all over again? or can i do this now with no problems

---

### Post by binaryCrusader00 on 2013-01-09
I tried both of those and got errors. You meant do them *before* installing them?

---

### Post by squakie on 2013-01-10
no, you need to install ndiswrapper and ndisgtk first, do those 2 commands, then start ndisgtk to install the driver.

---

### Post by flash63 on 2013-01-10
@ binaryCrusader00

Hello,
there are currently problems with Ndiswrappper V1.57 and Ubuntu 12.10. Which version do you use?

```
uname -a
cat /etc/lsb-release
```

---

### Post by binaryCrusader00 on 2013-01-10
Ubuntu 12.04 LTS 64 Bit version

---

### Post by binaryCrusader00 on 2013-01-10
I think it would just be easier to get a different wireless adapter.

Thanks for the help everyone

---

### Post by Bucky Ball on 2013-01-10
ndiswrapper definite;y not the way to go. Bad advice. Once that is installed all bets are off. Nothing else will work while that is installed, open sourcd drivers included ...

All advice from here on in is going to be inconsequential unless it deals with uninstalling ndiswrapper. Broadcom is supportive and well catered for in the Linux world.

---

### Post by flash63 on 2013-01-10
> **Bucky Ball said:**
> 

All advice from here on in is going to be inconsequential unless it deals with uninstalling ndiswrapper. Broadcom is supportive and well catered for in the Linux world.

Broadcom based USB-Devices unfortunately not.

@binaryCrusader00

Reinstall the packages with connection over ethernet:
```
sudo apt get install --reinstall ndiswrapper-common ndiswrapper-utils-1.9 ndiswrapper-dkms ndisgtk
```

Alternatively get them directly from the server and install them by double clicking (Software-Center opens) :
[http://packages.ubuntu.com/search?keywords=ndiswrapper&searchon=names&suite=precise&section=all](http://packages.ubuntu.com/search?keywords=ndiswrapper&searchon=names&suite=precise&section=all)

Check:
```
modinfo ndiswrapper
gksu ndisgtk
```

If it works, you can install the driver by selecting the bcmwlhigh5.inf file from the WinXP driver package I've already linked.

---

### Post by binaryCrusader00 on 2013-01-10
> **Bucky Ball said:**
> ndiswrapper definite;y not the way to go. Bad advice. Once that is installed all bets are off. Nothing else will work while that is installed, open sourcd drivers included ...

All advice from here on in is going to be inconsequential unless it deals with uninstalling ndiswrapper. Broadcom is supportive and well catered for in the Linux world.

in other words, uninstall ndisgtk and ndiswrapper? before i get in too deep i want to be sure that this new (and linux supported) adapter will *hopefully* be detected when you plug it in

---

### Post by squakie on 2013-01-10
If you are getting a new adapter, then by all means reverse everything I told you.
 
Bucky Ball:  everything I read on the net, including very recent posts, indicated that this device, even though it is Broadcom, has no Linux driver and that it was necessary to use ndiswrapper.  That's why I had the OP going the direction I did.
 
I suspect the reason the attempt at using the Windows driver failed because it is 32-bit whereas the OP has now indicated they are using 64-bit Ubuntu.  Architecture differences haven't been allowed in ndiswrapper when I've been forced to use it.

---

### Post by Bucky Ball on 2013-01-11
> **squakie said:**
> 
Bucky Ball:  everything I read on the net, including very recent posts, indicated that this device, even though it is Broadcom, has no Linux driver and that it was necessary to use ndiswrapper.  That's why I had the OP going the direction I did.
 
I suspect the reason the attempt at using the Windows driver failed because it is 32-bit whereas the OP has now indicated they are using 64-bit Ubuntu.  Architecture differences haven't been allowed in ndiswrapper when I've been forced to use it.

You raise some valid points and you're right; some of the newer cards aren't supported (yet). ndiswrapper can become a dog's breakfast, though. If that is the only way, then that is the only way, though ...

---

### Post by squakie on 2013-01-11
> **Bucky Ball said:**
> You raise some valid points and you're right; some of the newer cards aren't supported (yet). ndiswrapper can become a dog's breakfast, though. If that is the only way, then that is the only way, though ...
 
I know what you mean ;)  Back before driver support was improved so much it was the way many of us were forced to go, and there are a lot of ways to screw that up royally.  I used to be a strong advocate of it via ndisgtk, but today the driver support is so much improved that I'd personally prefer there was no need for it at all anymore.  So many old posts out there that don't even apply now - and people read those old posts before asking for help (at least they are trying! ;) ), and they have usually done something to make things worse.
 
Oh well, just wanted to let you know I agree with you 100%.  Hope things are going well for you.
 
Dave

---

### Post by kurt18947 on 2013-01-11
> **binaryCrusader00 said:**
> I think it would just be easier to get a different wireless adapter.

Thanks for the help everyone

That's the simplest way though some regard it as the coward's way out.:D   Here are a couple adapters that I've had very good luck with.  They're sorta twins,  both use the RealTek 8192SU chip which seems to have very good built-in support.

Dlink DWA-131 rev. A1

TrendNet TEW-649UB

Here's a bargain but it's kinda old, big and slow.  On the other hand, it has been plug 'n' play since Ubuntu 9.10

TrendNet TEW-424UB v3.  In the case the v3 is important.  v2 used a different chip set and was NOT plug 'n' play.

I'm certain there are other excellent choices but I have no experience with them.

---

### Post by squakie on 2013-01-12
I'm using a Tenda adapter that cost me less than $10 at MicroCenter I *think* it's a w311m.  It has worked straight "out of the box" for me and Ubuntu for a couple of years.

---

