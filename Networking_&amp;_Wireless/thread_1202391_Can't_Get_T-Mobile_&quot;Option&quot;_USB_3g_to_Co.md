---
title: "Can't Get T-Mobile &quot;Option&quot; USB 3g to Connect"
date: 2009-07-02
forum: Networking &amp; Wireless
---

### Post by jamestech on 2009-07-02
I have Ubuntu NetBook Remix 9.04 x86 installed and a T-Mobile 3g dongle. After some research I found I needed "ozerocdoff". After installing this Ubuntu now recognises the dongle quite nicely.

The first time I plugged it in Ubuntu helped me set up the mobile broadband connection, and as far as I am aware the settings are all correct, however when I go to network manager to connect I almost immediately get "GSM Disconnected"

My dongle seems to have quite a few model numbers/markings...

"MB Stick 530"
"Option N.V."
"Qualcomm 3G CDMA"
"GI0431"
"NCMOGI0411"
"Bus 001 Device 014: ID 0af0:7501 Option"
"ZCOption HSUPA Modem"

I have also attached some logs I found which may help.

Any help would be greatly appreciated!

Cheers,

James

---

### Post by jamestech on 2009-07-03
OK, just a quick update, after further research I believe there may be a simple fix for someone with the know how, I have found the following logs which seem important...

```
Jul  3 10:02:02 ubuntu NetworkManager: <info>  Activation (ttyHS2) starting connection 'T-Mobile' 
Jul  3 10:02:02 ubuntu NetworkManager: <info>  (ttyHS2): device state change: 3 -> 4 
Jul  3 10:02:02 ubuntu NetworkManager: <info>  Activation (ttyHS2) Stage 1 of 5 (Device Prepare) scheduled... 
Jul  3 10:02:02 ubuntu NetworkManager: <info>  Activation (ttyHS2) Stage 1 of 5 (Device Prepare) started... 
Jul  3 10:02:02 ubuntu NetworkManager: <debug> [1246615322.406504] nm_serial_device_open(): (ttyHS2) opening device... 
Jul  3 10:02:02 ubuntu NetworkManager: <info>  Activation (ttyHS2) Stage 1 of 5 (Device Prepare) complete. 
Jul  3 10:02:13 ubuntu NetworkManager: <WARN>  init_done(): Modem initialization timed out 
Jul  3 10:02:13 ubuntu NetworkManager: <info>  (ttyHS2): device state change: 4 -> 9 
Jul  3 10:02:13 ubuntu NetworkManager: <debug> [1246615333.001780] nm_serial_device_close(): Closing device 'ttyHS2' 
Jul  3 10:02:13 ubuntu NetworkManager: <info>  Marking connection 'T-Mobile' invalid. 
Jul  3 10:02:13 ubuntu NetworkManager: <info>  Activation (ttyHS2) failed. 
Jul  3 10:02:13 ubuntu NetworkManager: <info>  (ttyHS2): device state change: 9 -> 3 
Jul  3 10:02:13 ubuntu NetworkManager: <info>  (ttyHS2): deactivating device (reason: 0). 
Jul  3 10:02:13 ubuntu NetworkManager: nm_system_device_flush_ip4_routes_with_iface: assertion `iface_idx >= 0' failed
Jul  3 10:02:13 ubuntu NetworkManager: nm_system_device_flush_ip4_addresses_with_iface: assertion `iface_idx >= 0' failed
```

I noticed the "Modem initialization timed out", are there some initialization commands I need to send to the modem before connecting?

---

### Post by computer13137 on 2009-07-03
I find myself once again replying to a thread that isn't my area of expertise, to point out something I found on Google, lol.

This launchpad bug page has a very extensive discussion of this error... a few people are suggesting workarounds that have worked for them.  You might try reading the whole thing, but I see no need to do that for you since this isn't my problem, and I don't have a T-Mobile Option to test with. :P

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/368325](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/368325)

-Kirk

---

### Post by Riverside on 2009-07-05
> **computer13137 said:**
> I find myself once again replying to a thread that isn't my area of expertise, to point out something I found on Google, lol.

This launchpad bug page has a very extensive discussion of this error... a few people are suggesting workarounds that have worked for them.  You might try reading the whole thing, but I see no need to do that for you since this isn't my problem, and I don't have a T-Mobile Option to test with. :P

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/368325](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/368325)
That's a different issue.  The original poster in this thread isn't getting that far.

---

### Post by Riverside on 2009-07-05
> **jamestech said:**
> I have Ubuntu NetBook Remix 9.04 x86 installed and a T-Mobile 3g dongle. After some research I found I needed "ozerocdoff". After installing this Ubuntu now recognises the dongle quite nicely.

The first time I plugged it in Ubuntu helped me set up the mobile broadband connection, and as far as I am aware the settings are all correct, however when I go to network manager to connect I almost immediately get "GSM Disconnected"

My dongle seems to have quite a few model numbers/markings...

"MB Stick 530"
"Option N.V."
"Qualcomm 3G CDMA"
"GI0431"
"NCMOGI0411"
"Bus 001 Device 014: ID 0af0:7501 Option"
"ZCOption HSUPA Modem"

I have also attached some logs I found which may help.

Any help would be greatly appreciated!

Cheers,

JamesExactly my experience also (9.04) and I have spent all afternoon and evening on this today.  The following should work:

[http://www.pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html](http://www.pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html)

But doesn't.

---

### Post by Andrew_S on 2009-08-23
Hi All,

Ive been struggling to get this to work in Ubuntu 9.04 or Xubuntu 9.04. I've got as far as it recognizing but selecting 'T-Mobile' from the list within NetworkManager Applet a notification appears stating:
[B]
GSM Network[/B]
Disconnected

Any advice with regards to debugging logs etc would be much appreciated as I'm rather n00b.

Kind Regards
Andrew

---

### Post by frankwakeman on 2009-09-04
Although there are threads on this forum which sort this problem out, which I found by typing the dongle model number into Google, I found a simpler solution when I wanted to try Kubuntu instead of Ubuntu, and didn't know how to do the same tasks I'd carried out with Ubuntu.

If you still have a Windows partition or access to someone's Windows system, temporarily use the Windows T-mobile software built-in to the dongle which has what I can only imagine is a more effective means of switching off the CD-Rom aspect of the dongle.

As soon as I'd done this, I started up my Linux machine, plugged in, the dongle was detected, the T-mobile set up chosen and now I'm online.  My first attempt to connect failed, but it was peak-time and that has sometimes happened anyway even with Vista.

---

### Post by msbc on 2009-09-10
After installing the web'n'walk software in Windows how do you remove/disable the ZeroCD?

---

### Post by terry_gardener on 2009-10-03
i have sent the last few hours trying to get this 3g card to get and work properly in ubuntu 9.04 UNR. 

i have managed to do it.

create a user group called dialout and add root and your username to it. 
then follow the instructions on the following site.
[http://www.betavine.net/bvportal/resources/datacards/os/ubuntu]("http://www.betavine.net/bvportal/resources/datacards/os/ubuntu")
then replace network manager with wicd.

run the vodafone mobile connect app.
it should find the 3g card and then click ok.
create a profile (i called mine tmobile) enter the apn details (ie, username: user, password: mms, APN: general.t-mobile.uk 
when you have created the profile new window should appear click connect and at the button it will say connected to 3g. 

now you have the internet.

---

### Post by pdc on 2009-10-03
well done terry to get the modem working;

I was interested you replaced network manager with wicd;

(I understand wicd will not run 3g modems, and will only run wifi: and so it is the vmc software that you are using to connect your 3G to the internet):

did you have advice that you needed to remove network manager?

---

### Post by terry_gardener on 2009-10-04
pdc 

yes i seen a thread somewhere that said to remove gnome network manager and replace it with wicd.

use wicd for ethernet and wifi and vmc for 3g mobile connections. 

i did try it with gnome network manager but firefox kept starting in offline mode and pidgin wouldn't connect. 

with VMC + WICD combo it works how it should.

---

