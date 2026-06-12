---
title: "Set MTU value in 10.04"
date: 2010-08-24
forum: Networking &amp; Wireless
---

### Post by prasanthsd on 2010-08-24
Hi all,

Im using 10.04 64bit.

I have created a ppp connection using network manager. The connection isnt set to automatically connect, I manually connect it each time after boot using the network manager applet.

I have set a MTU from the GUI it has no effect. Also tried editing /etc/network/interfaces but that didnt work. I want the MTU for ppp0 to be permanently set to 1454 instead of 1492.

I can set it manually using sudo ifconfig ppp0 mtu 1454.

Thank you

---

### Post by linuxyogi on 2011-03-29
Same problem.

I want to set  **[COLOR=Red]ppp0's[/COLOR] ****(not eth0)** mtu to 1400 permanently. At 1492 some sites won't open.

This is quite an old thread. So I if anyone is sure of the fact that what we want is not possible please reply.

OS: Xubuntu 10.04 (32Bit)

---

### Post by linuxyogi on 2011-03-29
@ prasanthsd

Just curious. Are you using a BSNL Broadband Connection ?

---

### Post by dineshs on 2011-03-30
If you are connecting via DSL tab in network manager ,
Rightclick network manager icon-edit connections-DSL tab-select your connection-edit-wired tab-set MTU and apply

---

### Post by linuxyogi on 2011-03-31
> **dineshs said:**
> If you are connecting via DSL tab in network manager ,
Rightclick network manager icon-edit connections-DSL tab-select your connection-edit-wired tab-set MTU and apply

I have already done that. It doesn't work. I guess its a bug.

---

### Post by dineshs on 2011-03-31
Are you connecting via DSL in NM or using the command pon dsl-provider?

---

### Post by linuxyogi on 2011-03-31
> **dineshs said:**
> Are you connecting via DSL in NM or using the command pon dsl-provider?

I am connecting via DSL in NM.

---

### Post by dineshs on 2011-03-31
Did you check whether the MTU value set via GUI is getting saved in the respective file? You may try editing the file .It will be in /etc/NetworkManager/system-connections
```
gksudo nautilus /etc/NetworkManager/system-connections
```

---

### Post by linuxyogi on 2011-03-31
> **dineshs said:**
> Did you check whether the MTU value set via GUI is getting saved in the respective file? You may try editing the file .It will be in /etc/NetworkManager/system-connections
```
gksudo nautilus /etc/NetworkManager/system-connections
```

This is how the file looks like



```
[connection]
id=BSNL
uuid=fde65857-6324-4a3d-94a6-31e0acb4ad79
type=pppoe

[ppp]
refuse-eap=true
refuse-mschap=true
refuse-mschapv2=true

[ipv4]
method=auto

[pppoe]
username=xyz
password=***********

[802-3-ethernet]
duplex=full

```


I tried adding the line mtu=1400 at the end and then did ```
sudo /etc/init.d/networking restart
```

ifconfig shows MTU of ppp0 is still 1492

Did I do something wrong?

---

### Post by linuxyogi on 2011-03-31
**Okay, solution found**

Just added two lines (mru=1400 & mtu=1400) Got the idea by studying the same file in my openSUSE box.

See below

[ppp]
refuse-eap=true
refuse-mschap=true
refuse-mschapv2=true
[B]mru=1400
mtu=1400[/B]

Then 
```
sudo /etc/init.d/networking restart
```

Done

[COLOR=Red]Thank you Dineshs. THANKS A LOT !!![/COLOR]:popcorn:

---

### Post by dineshs on 2011-03-31
> Okay, solution found
Glad to hear that
> sudo /etc/init.d/networking restartI think you should do ```
sudo service network-manager restart
```if you are using NM and
sudo /etc/init.d/networking restart if you are using /etc/network/interfaces
> Just added two lines (mru=1400 & mtu=1400) Got the idea by studying the same file in my openSUSE box.
Just adding mtu=1400 at the end of ```
[802-3-ethernet]
duplex=full
```should work I think

---

