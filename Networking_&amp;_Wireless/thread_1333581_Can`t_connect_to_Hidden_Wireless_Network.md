---
title: "Can`t connect to Hidden Wireless Network"
date: 2009-11-21
forum: Networking &amp; Wireless
---

### Post by _VZ_ on 2009-11-21
Hello to all!!!

After updating to 9.10 I can not connect to Hidden wireless network. I have created new Ad-Hoc network and entered static IP and WEP Key. When I trying to connect, I get attached image. I was surprised why the "Key" field is empty. Thats why, I think, "Connect" button is grey.

Can anyone help?

---

### Post by _VZ_ on 2009-11-23
No ideas?

---

### Post by sotomajor on 2009-11-23
I've filed bug regarding this issue
[https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/461385](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/461385)

---

### Post by sgosnell on 2009-11-23
Don't create a new network, just left-click on the network icon in the panel and select Connect to Hidden Network.  Enter the SSID, change the security information, and it should connect.

---

### Post by _VZ_ on 2009-11-23
Thank you sotomajor. I think so also.

> **sgosnell said:**
> Don't create a new network, just left-click on the network icon in the panel and select Connect to Hidden Network.  Enter the SSID, change the security information, and it should connect.

So worked when I 9.04 had and had no problem. In Ubuntu 9.10 this is does not work, when I have static IP and WEP-key and Ad-Hoc mode. Why? I do not know. :-(

---

### Post by sgosnell on 2009-11-23
Have you tried enabling the SSD broadcast temporarily, and trying a connection?

---

### Post by _VZ_ on 2009-11-25
> **sgosnell said:**
> Have you tried enabling the SSD broadcast temporarily, and trying a connection?

No. I do not know what is this. Can you tell me how can I do this?

---

### Post by sgosnell on 2009-11-25
Go into your router's settings via your browser.  It may help to read the manual for the router.  The IP address should be either 192.168.1.1 or 192.168.0.1, those are the usual ones.  Somewhere under the wireless settings there should be an option to enable or disable the SSID.  Sometimes it's easier to get a system to connect to a router broadcasting the SSID (not 'hidden') and it will continue to connect after rehiding the SSID.

---

### Post by _VZ_ on 2009-11-26
I have not a router. I have created Ad-Hoc network in my notebook. In 9.04 first I connect to this created network (left click NM then "Connect to hidden wireless network" and then my network) and then other computers and mobiles connect to me.

---

### Post by joshuapurcell on 2009-12-03
I have this same issue. I am connecting to my work's hidden wireless network and I don't have the option for unhiding the ESSID. I start my laptop, once booted I choose 'Connect to Hidden Wireless Network...', select the correct network listed in the dropdown, and the data for that network connection populates but without the password as shown in the screenshot in the first post of this thread. It is uneditable, so I must then choose 'New' from the list and manually enter all that information again. Every time I boot up.

---

### Post by sgosnell on 2009-12-03
If you edit that connection, do you have the checkbox "Connect automatically", at the top of the dialog, checked?

---

### Post by Vasyl on 2009-12-08
I solved this problem setting encryption key manually with **sudo iwconfig bla0 enc blablabla**
and then connecting with networkmanager

---

### Post by brookie on 2009-12-10
Hello, 

I am experiencing this in Karmic 32 bit on three machines with all the current updates. This bug seems like it has been duped with others here: 

This looks like the original: 
[https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/446394](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/446394) 

Post #20 in #446394 has a workaround. 

Duped in these: 
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/450097](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/450097) 
[https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/449287](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/449287) 
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/455161](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/455161)
[https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/461385](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/461385)

If this is indeed a dup of #446394 it should be marked as so and folks should post comments on the 446394 thread. 

If people are still experiencing this like I was on a Broadcom BCM4318, probably no need to hack the driver with all the workarounds in other posts. The b43xx cutter driver actually works. The ndiswrapper hack I found in many posts was unnecessary in my case. 

We should probably post info in the original thread at launchpad to get this fixed. Just sign up for an account and give the devs any information they may ask for. 

Cheers,
brook

---

### Post by _VZ_ on 2009-12-10
> **sgosnell said:**
> If you edit that connection, do you have the checkbox "Connect automatically", at the top of the dialog, checked?

There is off. I tried check on and off but this does not help me. 

> **Vasyl said:**
> I solved this problem setting encryption key manually with **sudo iwconfig bla0 enc blablabla**
and then connecting with networkmanager

This does not work. :(
I have entered:
sudo iwconfig wlan0 enc **********(my WEP)

To [brookie]("http://ubuntuforums.org/member.php?u=729189") and [sgosnell]("http://ubuntuforums.org/member.php?u=774876")
As I understand this checkbox work when this network is already on and I can connect.
But I want myself this Ad-Hoc network turn on.

---

### Post by Crick on 2010-02-17
I think this issue may be related to the one stated [here]("http://ubuntuforums.org/showthread.php?t=288245"):

I changed my SSID to an all-lowercase sequence (broadcast still disabled), and it is connecting fine now. Note that when it asks for the WPA2(personal) password, you put in the actual passphrase, not the psk generated by wpa_passphrase.

---

### Post by _VZ_ on 2010-02-17
My SSID was all-lowercase and it was not work.

But Bug-fix ([https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/446394](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/446394)) helped me and now all work gut.

Thank you all for help!

---

