---
title: "Suddenly my Digital camera isn't detected"
date: 2007-03-31
forum: Multimedia &amp; Video
---

### Post by skelooth on 2007-03-31
I'm not sure when this broke, but it's certainly broken...  

When I used to plug in my camera via usb an import dialog would pop up. Now.... it acts like nothing is there. I tried installing gtkam for visual confirmation and it says no devices found. I followed a couple of bug fixes which included editing a rules file which also did not do anything for me.

Does anyone have any ideas? I tried my camera on a friend's windows laptop and it worked fine. So? I know it used to work.

---

### Post by skelooth on 2007-04-04
Hi? :(

---

### Post by mgmiller on 2007-04-04
I think this came in through the backports repository.  Feisty detects USB cameras differently than Edgy, and this causes the breakage in Edgy

I have had the same problem on 2 recent occasions.  This is how I fixed it:

```
sudo gedit /etc/udev/rules.d/45-libgphoto2.rules
```

Line 3 currently reads:
```

BUS!="usb*", GOTO="libgphoto2_rules_end"
```

Put a # in front of that line to "comment it out" so it does not execute.

Finally, paste the following line below it:

```
SUBSYSTEM!="usb_device", GOTO="libgphoto2_rules_end"
```

Save the file and it should work.  Did for me on 2 occasions.

---

### Post by emilih on 2007-04-06
I have the problem and:

With Synaptic search libgphoto2-2 and force install back version
Idem with libgphoto-2-2.dev

i

---

