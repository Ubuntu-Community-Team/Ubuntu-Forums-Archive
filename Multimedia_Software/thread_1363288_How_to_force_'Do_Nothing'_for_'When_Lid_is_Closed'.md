---
title: "How to force 'Do Nothing' for 'When Lid is Closed'"
date: 2009-12-24
forum: Multimedia Software
---

### Post by lsackette on 2009-12-24
Hi,

I am running Ubuntu Desktop 9.10 on a my laptop and sometimes I have an external monitor connected.  When that is the case, I want to close the lid.  But if I do, the laptop suspend.   I don't want that and there is no option for this in 9.10 under power management.  In 9.04, there were separate configurations for when on AC or Battery, and there was an option 'Do Nothing' when lid is close.

Can someone please tell me how to accomplish this without the 'Power Management' utility?

If there are Ubuntu developers here, please restore the separate configurations as it was in 9.04.

Thanks.

.v

---

### Post by CuBone on 2009-12-25
Did you find any solution for this? I'm having the same problem. I would like to put my laptop away when I'm at my desk and use external screen, keyboard and mouse. But at the moment, as soon as I close the lid, my external screen goes black.

---

### Post by xantus on 2010-01-11
This option was hidden.  Here's how you can set it:

```
#$ gconftool-2 --type string --set /apps/gnome-power-manager/buttons/lid_ac "nothing"
```

Reference: [https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/416236]("https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/416236")

---

### Post by netmoon on 2011-10-09
> **xantus said:**
> This option was hidden.  Here's how you can set it:

```
#$ gconftool-2 --type string --set /apps/gnome-power-manager/buttons/lid_ac "nothing"
```

Reference: [https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/416236]("https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/416236")

:p heeyyy thanks.it works good.

---

### Post by hamoid on 2011-11-16
It doesn't work for me. I have an integrated Intel graphic chipset and an external monitor connected using a DisplayPort cable.

I did set When laptop lid is closed: do nothing, but it ignores this setting and both displays go off.

I could not even switch off the laptop monitor using the Monitor Preferences, both monitors would go off, but using Xrandr works:

```
xrandr --output LVDS1 --off
```

This switches off the laptop monitor. But I can not close the lid. Why is the "do nothing" setting ignored?

---

### Post by lucazade on 2011-12-01
> **hamoid said:**
> It doesn't work for me. I have an integrated Intel graphic chipset and an external monitor connected using a DisplayPort cable.

I did set When laptop lid is closed: do nothing, but it ignores this setting and both displays go off.

I could not even switch off the laptop monitor using the Monitor Preferences, both monitors would go off, but using Xrandr works:

```
xrandr --output LVDS1 --off
```

This switches off the laptop monitor. But I can not close the lid. Why is the "do nothing" setting ignored?

the same happens here with oneiric and using an external monitor.. if I close the lid of the laptop the external monitor goes blank even if I've selected to do "nothing" from dconf.

---

