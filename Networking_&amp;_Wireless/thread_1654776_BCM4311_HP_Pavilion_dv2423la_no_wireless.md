---
title: "BCM4311 HP Pavilion dv2423la no wireless"
date: 2010-12-28
forum: Networking &amp; Wireless
---

### Post by devilskate on 2010-12-28
Hi everyone! well I tried almost every solution in internet, I installled my wireless card from ndiswrapper, I compiled the drivers that i downloaded from broadcom official web page, but for some reason I couldn't install the module. And the private drivers were already activated... and still not working. So I think I need some help here. I'm using Ubuntu 10.10

---

### Post by PatchesTheCaveman on 2010-12-29
You should be able to go to System > Administration > Additional Drivers and install the "Broadcom STA wireless driver".  That works fine for my BCM4312.  

ETA:  It's supposed to be compatible with BCM4311 too.

---

### Post by devilskate on 2010-12-29
Yes, I read the description, and as I wrote in the last post, the privative drivers were activated... so that is not working for me. My wireless card has a led that is orange when is off and turn blue when it is on... and it is always orange... and in the network manager says that is not activated... I don't know what else can I do. :S

---

### Post by PatchesTheCaveman on 2010-12-29
I assume you've tried using the wireless switch or Fn key to make sure the wireless is on?  (It might sound stupid, but this gets people all the time!)

If so, try turning power management on your wireless card off to keep it on 24/7.  Go to Applications > Accessories > Terminal and type the following command and press Enter:
```
sudo iwconfig
```

That will list all of the network interfaces on your machine, all but one of them will say no wireless extensions, except for one.  It's probably the one labeled *eth1*, but one never can be sure.  That one should list a bunch of information about your wireless state.

If it says *eth1* on the left, type the following command and press Enter.  If your wireless interface says something else on the left, replace *eth1* with that interface name.
```
sudo iwconfig eth1 power off
```

That might sound counterintuitive, but what you're actually doing is turning off the feature of your wireless card that turns it off when not in use, so that its on all the time.  If you're lucky, the light will turn blue and you'll be able to use it.  If not, try flipping your wireless switch/key again just in case.

If that fixes it, run the following command:
```
gksudo gedit /etc/rc.local
```

Add the *iwconfig eth1 power off* command you ran earlier (again replacing eth1 if necessary) to that file and save it.  Note that you don't need *sudo* here because this will run with root privileges every time your computer starts, making this fix permanent.

Good luck!

---

### Post by devilskate on 2010-12-29
Hey thanks! but I solved my problem doing something a little bit larger... I installed Ubuntu 10.04... the wireless was working... and then I upgrade it to 10.10. But I will save your post... to try it. Thank you anyway!! n_n

---

