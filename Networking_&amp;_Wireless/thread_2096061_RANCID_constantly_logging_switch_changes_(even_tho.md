---
title: "RANCID constantly logging switch changes (even though there are none)"
date: 2012-12-18
forum: Networking &amp; Wireless
---

### Post by dysun on 2012-12-18
Hi all,

First time on Ubuntu forums. I'm running RANCID, a network backup configuration & dff tool for Cisco, Juniper, Foundry, and hp devices (and more). It's great at catching changes made to the devices, but there's just one really annoying thing that really gets to me.

So everytime RANCID runs, it mails me a change notification and updates the CVS tree, but when I check, there's really no change at all. I also check with my 3 other teammates (4 people our IT), who also confirm that they in fact have not made any changes to the devices in question.

Here's a sample output:

- !VLAN: 1    default                          active    Fa3/32, Gi5/3, Gi5/4,  Gi5/5
- !VLAN:                                                 Gi5/6,  Gi6/28
+ !VLAN: 1    default                          active    Fa3/32,  Gi5/3, Gi5/4, Gi5/5, Gi5/6, Gi6/28

As you can see, there's no new port addittions to VLAN 1, but it still registered as a change, presumably because of the line break. That's not so bad when it's one switch or when there are a few ports, but when the out put looks something like below, it kinda makes the email notification lose value. (Yes I manually went through and checked each port to see if it was different)

 !VLAN: 136  3RD_FLOOR_DATA                   active    Fa2/1, Fa2/2, Fa2/3,  Fa2/4, Fa2/5, Fa2/6, Fa2/7, Fa2/8, Fa2/9, Fa2/10, Fa2/11, Fa2/12, Fa2/13,  Fa2/14, Fa2/15, Fa2/16, Fa2/17, Fa2/18, Fa2/19, Fa2/20, Fa2/21, Fa2/22, Fa2/23,  Fa2/24, Fa2/25, Fa2/26, Fa2/27, Fa2/28, Fa2/29, Fa2/30, Fa2/31, Fa2/32, Fa2/33,  Fa2/34, Fa2/35, Fa2/36, Fa2/37, Fa2/38, Fa2/39, Fa2/40, Fa2/41, Fa2/42, Fa2/43,  Fa2/44, Fa2/45, Fa2/46, Fa2/47, Fa2/48, Fa3/1, Fa3/2, Fa3/3, Fa3/4, Fa3/5,  Fa3/6, Fa3/7, Fa3/8, Fa3/9, Fa3/11, Fa3/13, Fa3/14, Fa3/15, Fa3/16, Fa3/17,  Fa3/18, Fa3/19, Fa3/20, Fa3/21, Fa3/22, Fa3/23, Fa3/24, Fa3/25, Fa3/26, Fa3/27,  Fa3/28, Fa3/29, Fa3/30, Fa3/31, Fa3/33, Fa3/34, Fa3/36, Fa3/37, Fa3/38, Fa3/39,  Fa3/40, Fa3/41, Fa3/42, Fa3/43, Fa3/44, Fa3/45, Fa3/46, Fa3/47, Fa3/48, Fa4/1,  Fa4/2, Fa4/3, Fa4/4, Fa4/5, Fa4/6, Fa4/7, Fa4/8, Fa4/9, Fa4/10, Fa4/11, Fa4/12,  Fa4/13, Fa4/14, Fa4/15, Fa4/16, Fa4/17, Fa4/18, Fa4/19, Fa4/20, Fa4/21, Fa4/22,  Fa4/23, Fa4/24, Fa4/25, Fa4/26, Fa4/27, Fa4/28, Fa4/29, 
 Fa4/30, Fa4/31,  Fa4/32, Fa4/33, Fa4/34, Fa4/35, Fa4/36, Fa4/37, Fa4/38, Fa4/39, Fa4/40, Fa4/41,  Fa4/42, Fa4/46, Gi6/1, Gi6/2, Gi6/3, Gi6/4, Gi6/5, Gi6/6, Gi6/7, Gi6/8, Gi6/9,  Gi6/10, Gi6/11, Gi6/12, Gi6/13, Gi6/15, Gi6/16, Gi6/17, Gi6/18, Gi6/21, Gi6/23,  Gi6/24, Gi6/25, Gi6/26, Gi6/27, Gi6/29, Gi6/30, Gi6/31, Gi6/37, Gi6/39,  Gi6/40

+ !VLAN: 136  3RD_FLOOR_DATA                   active    Fa2/1, Fa2/2,  Fa2/3, Fa2/4, Fa2/5, Fa2/6, Fa2/7, Fa2/8, Fa2/9, Fa2/10, Fa2/11
+  !VLAN:                                                 Fa2/12, Fa2/13, Fa2/14,  Fa2/15, Fa2/16, Fa2/17, Fa2/18, Fa2/19, Fa2/20, Fa2/21
+  !VLAN:                                                 Fa2/22, Fa2/23, Fa2/24,  Fa2/25, Fa2/26, Fa2/27, Fa2/28, Fa2/29, Fa2/30, Fa2/31
+  !VLAN:                                                 Fa2/32, Fa2/33, Fa2/34,  Fa2/35, Fa2/36, Fa2/37, Fa2/38, Fa2/39, Fa2/40, Fa2/41
+  !VLAN:                                                 Fa2/42, Fa2/43, Fa2/44,  Fa2/45, Fa2/46, Fa2/47, Fa2/48, Fa3/1, Fa3/2, Fa3/3, Fa3/4
+  !VLAN:                                                 Fa3/5, Fa3/6, Fa3/7,  Fa3/8, Fa3/9, Fa3/11, Fa3/13, Fa3/14, Fa3/15, Fa3/16, Fa3/17
+  !VLAN:                                                 Fa3/18, Fa3/19, Fa3/20,  Fa3/21, Fa3/22, Fa3/23, Fa3/24, Fa3/25, Fa3/26, Fa3/27
+  !VLAN:                                                 Fa3/28, Fa3/29, Fa3/30,  Fa3/31, Fa3/33, Fa3/34, Fa3/36, Fa3/37, Fa3/38, Fa3/39
+  !VLAN:                                                 Fa3/40, Fa3/41, Fa3/42,  Fa3/43, Fa3/44, Fa3/45, Fa3/46, Fa3/47, Fa3/48, Fa4/1, Fa4/2
+  !VLAN:                                                 Fa4/3, Fa4/4, Fa4/5,  Fa4/6, Fa4/7, Fa4/8, Fa4/9, Fa4/10, Fa4/11, Fa4/12, Fa4/13
+  !VLAN:                                                 Fa4/14, Fa4/15, Fa4/16,  Fa4/17, Fa4/18, Fa4/19, Fa4/20, Fa4/21, Fa4/22, Fa4/23
+  !VLAN:                                                 Fa4/24, Fa4/25, Fa4/26,  Fa4/27, Fa4/28, Fa4/29, Fa4/30, Fa4/31, Fa4/32, Fa4/33
+  !VLAN:                                                 Fa4/34, Fa4/35, Fa4/36,  Fa4/37, Fa4/38, Fa4/39, Fa4/40, Fa4/41, Fa4/42, Fa4/46
+  !VLAN:                                                 Gi6/1, Gi6/2, Gi6/3,  Gi6/4, Gi6/5, Gi6/6, Gi6/7, Gi6/8, Gi6/9, Gi6/10, Gi6/11
+  !VLAN:                                                 Gi6/12, Gi6/13, Gi6/15,  Gi6/16, Gi6/17, Gi6/18, Gi6/21, Gi6/23, Gi6/24, Gi6/25
+  !VLAN:                                                 Gi6/26, Gi6/27, Gi6/29,  Gi6/30, Gi6/31, Gi6/37, Gi6/39, Gi6/40

Because of this issue, I'm only monitoring one switch right now. I don't want the RANCID change notification email to be filled with vlan information from dozens of switches that have in fact not been changed. My team doesn't many changes, but it'd still be nice to receive email notifications about what changes have been made to the network.

Here's what I'm running and the instructions I used

Ubuntu 12.10
Rancid 2.3.8 (installed via sudo apt-get install rancid)
Switch - Catalyst 4506 (Don't have the IOS version on me)

Guides:
[http://evilrouters.net/2010/05/31/installing-rancid-on-ubuntu-10-04-lts/](http://evilrouters.net/2010/05/31/installing-rancid-on-ubuntu-10-04-lts/)
[https://help.ubuntu.com/community/RANCID](https://help.ubuntu.com/community/RANCID)


What am I doing wrong? Please help!

Thanks,

dysun

---

