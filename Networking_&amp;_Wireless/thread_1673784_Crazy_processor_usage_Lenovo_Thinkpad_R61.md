---
title: "Crazy processor usage Lenovo Thinkpad R61"
date: 2011-01-22
forum: Networking &amp; Wireless
---

### Post by likwidoxigen on 2011-01-22
So here's an interesting one. 
This is all after a clean reboot and the machine was NOT suspended and resumed.

On boot my events/1 spikes all the way up to 110% but is usually pretty stable at 65% when I view it on top.

I looked into the issue and saw that it's a network issue and disabling networking usually fixes it. I initially disabled all networking in network manager. 

That fixed it.

I then tried disabling the wifi which is usually the issue, and there was no effect. So I got frustrated flipped wifi back on and then disabled ethernet. Voila, 
That fixed it again. 

I have no idea why a standard run of the mill e1000e could cause this sort of issue....

I've googled all I can think of and I'm not getting anything useful. I don't usually use the wired but it would be nice to have the opportunity available without insane slowness.

I tailed dmesg and got nothing, tailed messages next and just got the status message that nothing was connected.

```

  56: None 03.0: 10701 Ethernet
  [Created at net.124]
  Unique ID: GP_i.ndpeucax6V1
  Parent ID: DkES.QgxdHTFew92
  SysFS ID: /class/net/eth3
  SysFS Device Link: /devices/pci0000:00/0000:00:19.0
  Hardware Class: network interface
  Model: "Ethernet network interface"
  Driver: "e1000e"
  Driver Modules: "e1000e"
  Device File: eth3
  HW Address: 00:1c:25:1c:38:5c
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #14 (Ethernet controller)

```

---

### Post by Spr0k3t on 2011-01-23
How long has this issue been happening?  I'm sure there's a simple explination for it... possibly from the latest kernel update or some other software issue.  The e1Ke is not completely clean of past issues at the kernel level.  Perhaps getting the details of the latest updates since the issue started and picking through from there might help.

---

