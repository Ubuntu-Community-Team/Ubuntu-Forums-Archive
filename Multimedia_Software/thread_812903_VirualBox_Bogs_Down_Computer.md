---
title: "VirualBox Bogs Down Computer"
date: 2008-05-30
forum: Multimedia Software
---

### Post by lakelovers on 2008-05-30
I have Hardy installed and I've noticed my computer becoming sluggish. I first notice this after installing and using VirualBox. But I'm not sure that's the culprit. When I turn it off, the computer still seems sluggish. I have a Dell Diminsion 2300, with integrated Intel 3D AGP Graphics. I don't know how much memory that device has but I imagine there's a command to find out. I have 768 mb of ram though I've ordered another 512 to bring it up to 1G, which is the max the 2300 accepts. There are no drivers installed according to the "Hardware Divers" report. The Swap partition has 1.20 GB free (16% used, currently, and 83% free. Any ideas on how I get this machined out of its sluggishness?

---

### Post by overdrank on 2008-05-30
> **lakelovers said:**
> I have Hardy installed and I've noticed my computer becoming sluggish. I first notice this after installing and using VirualBox. But I'm not sure that's the culprit. When I turn it off, the computer still seems sluggish. I have a Dell Diminsion 2300, with integrated Intel 3D AGP Graphics. I don't know how much memory that device has but I imagine there's a command to find out. I have 768 mb of ram though I've ordered another 512 to bring it up to 1G, which is the max the 2300 accepts. There are no drivers installed according to the "Hardware Divers" report. The Swap partition has 1.20 GB free (16% used, currently, and 83% free. Any ideas on how I get this machined out of its sluggishness?

HI and you may can check in bios to try and adjust the amount of memory shared with the graphics.

---

### Post by lakelovers on 2008-05-30
Thanks for the suggestion. I looked at the Bios and did not find a display configration option

---

### Post by cariboo on 2008-05-30
Run **top** in a terminal and see if there is an application that is using a lot of resources. If you find a program the is using a lot of resources you can stop it by running:

```
ps ax | grep "appname"
```

where "appname" is the unruly application note the PID

eg: 
```
**11005** pts/0    Ss     0:00 bash
```

the PID is bold in this example. Then in a terminal:

```
sudo kill PID
```

for more kill options type man kill in a terminal.

Jim

---

### Post by lakelovers on 2008-05-31
Thanks. . . I ran TOP. The three memory hogs are gzip, virtual box, and firefox. I don't run virtual box often. Firefox is my browser, and I don't know what gzip is doing, but I'm hesitant to stop it because I assume that would stop something else that it's working on, maybe VirualBox.

---

