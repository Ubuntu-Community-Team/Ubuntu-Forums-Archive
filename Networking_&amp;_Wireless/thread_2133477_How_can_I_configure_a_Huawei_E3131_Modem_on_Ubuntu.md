---
title: "How can I configure a Huawei E3131 Modem on Ubuntu 10.04"
date: 2013-04-08
forum: Networking &amp; Wireless
---

### Post by smuwanga on 2013-04-08
[LEFT][COLOR=#000000][FONT=Arial]am using an E3131 Huawei usb modem. I tried instructions [/FONT][/COLOR][/LEFT]
[here]("https://franklinchua.wordpress.com/2010/05/03/huawei-e1550-on-ubuntu-10-04-lucid-lynx/#comment-345")[LEFT][COLOR=#000000][FONT=Arial], but not success yet. I installed the mod-switch as advised. I ran
[/FONT][/COLOR]```
[COLOR=#000000][FONT=Consolas]$ lsusb | grep 12d1[/FONT][/COLOR]
```[COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]I get the output below
[/FONT][/COLOR]```
[COLOR=#000000][FONT=Consolas]Bus 002 Device 005: ID 12d1:14fe Huawei Technologies Co., Ltd.[/FONT][/COLOR]
```[COLOR=#000000][FONT=Arial]

[/FONT][/COLOR][COLOR=#000000][FONT=Arial]here is the list of files in[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][/LEFT]
```

$ ls /etc/udev/rules.d/15-huawei-155x.rules31-huawei-e3131.rules
```

[LEFT][COLOR=#000000][FONT=Arial]Content of 15-huawei-155x.rules[/FONT][/COLOR][/LEFT]
```
[LEFT][COLOR=#000000][FONT=Consolas]TEM==”usb”,[/FONT][/COLOR][/LEFT]
ATTRS{idProduct}==”14fe”,ATTRS{idVendor}==”12d1&#8243;, [LEFT][COLOR=#000000][FONT=Consolas]RUN+=”/lib/udev/modem-modeswitch –vendor 0x$attr{idVendor} –product 0x$attr{idProduct} –type option-zerocd”[/FONT][/COLOR][/LEFT]

```

[LEFT][COLOR=#000000][FONT=Arial]Content of 31-huawei-e3131.rules
```


```[/FONT][/COLOR][/LEFT]
```

ACTION!=”add”, GOTO=”huawei_zerocd_end”SUBSYSTEM==”usb”, ATTR{bDeviceClass}!=”ff” ,ENV{DEVTYPE}==”usb_device”, GOTO=”huawei_zerocd_disable”SUBSYSTEM==”scsi”, ENV{DEVTYPE}==”scsi_device”, GOTO=”huawei_zerocd_disable”GOTO=”huawei_zerocd_end”LABEL=”huawei_zerocd_disable”ATTRS{idVendor}==”12d1&#8243;, ATTRS{idProduct}==”14fe&#8243;, RUN+=”modem-modeswitch -v 0x%s{idVendor} -p 0x%s{idProduct} -t option-zerocd” [LEFT][COLOR=#000000][FONT=Consolas]LABEL=”huawei_zerocd_end”[/FONT][/COLOR][/LEFT]

```[LEFT][COLOR=#000000][FONT=Arial]

[/FONT][/COLOR][COLOR=#000000][FONT=Arial]I started the udev service. Unfortunately, the e3131 modem does not perform. I made configurations for the APN, but no change whatsoever. Would you possibly correct me? 
Thanking you, Simon.[/FONT][/COLOR][/LEFT]

---

### Post by mörgæs on 2013-04-08
[http://ubuntuforums.org/showthread.php?t=2076601](http://ubuntuforums.org/showthread.php?t=2076601)

---

### Post by Bucky Ball on 2013-04-08
Perhaps you should consider upgrading to 12.04 LTS and see how you go with that. 10.04 LTS reaches end-of-life in about two weeks and will no longer receive updates, including security updates, from that point. 12.04 LTS is supported until April 2017.

---

### Post by smuwanga on 2013-04-08
I chose to cling to the one I first tried. I have been using 10.04 LTS for the last two years. I might have to install a new OS all together. Upgrading once messed up my work. Thanks for the link you provided, it looks familiar though.

---

### Post by alexfish on 2013-04-08
possible try latest usb mode switch , all at own risk , but they do have a forum.

[http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)

do not use the debian link / read how to install first before compiling ,

HTH

Other readers note , do not try this in Ubuntu **>**10.04

Alex

---

