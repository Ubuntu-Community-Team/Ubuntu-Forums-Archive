---
title: "NeedHelp : Missing raw1394"
date: 2008-09-02
forum: Multimedia Software
---

### Post by Dreamerman on 2008-09-02
Hi. My raw1394 is missing from /dev after I changed its permission via sudo nautilus. Other threads mainly focus on getting raw1394 to work but what happens if it is missing ?

I used to be able to sudo kino & capture dv but thought of having a permanent solution, hence changing permission.

Can anyone help ? BTW, I reinstalled libraw1394 from synaptic but the file is still missing.

---

### Post by Erlander on 2008-09-02
Try doing a Complete Removal with Synapatic and then Re-Install as a second step.

Rob

---

### Post by Dreamerman on 2008-09-02
> **Erlander said:**
> Try doing a Complete Removal with Synapatic and then Re-Install as a second step.

Rob

If I do a complete removal, synaptic will also remove other linked apps, I am trying to avoid this. Any other ideas ?

---

### Post by Dreamerman on 2008-09-02
SOLVED.....

I reinstalled libiec61883-0 & libraw1394-8, reboot, plug in my DV camera & presto - raw1394 came back !!

---

### Post by Erlander on 2008-09-02
Great to hear that is solved.  

Rob

---

### Post by Dreamerman on 2008-09-03
> **Erlander said:**
> Great to hear that is solved.  

Rob

Yeah but now another minor problem, I could not get permissions to stick after reboot. I sudo nautilus & changed permissions to allow me read+write access. Works ok but permission seems to reset itself once I reboot. Nothing I do will stick after reboot. As a temporary workaround, I created a launcher with sudo chmod 777 /dev/raw1394.

Do you have a permanent solution ?

---

### Post by remeeraz on 2008-10-13
> **Dreamerman said:**
> Yeah but now another minor problem, I could not get permissions to stick after reboot. I sudo nautilus & changed permissions to allow me read+write access. Works ok but permission seems to reset itself once I reboot. Nothing I do will stick after reboot. As a temporary workaround, I created a launcher with sudo chmod 777 /dev/raw1394.

Do you have a permanent solution ?

do this

```
**sudo chown** username **/dev/raw1394**
```

:cool:

---

