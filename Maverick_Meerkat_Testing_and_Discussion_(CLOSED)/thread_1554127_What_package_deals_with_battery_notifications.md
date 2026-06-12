---
title: "What package deals with battery notifications?"
date: 2010-08-16
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by zekopeko on 2010-08-16
I'm specifically talking about that dialog that pops up when your battery is about to reach 0%.

---

### Post by 23meg on 2010-08-16
> **zekopeko said:**
> I'm specifically talking about that dialog that pops up when your battery is about to reach 0%.

Dialog? Do you mean the Notify OSD bubble? A screenshot might help illustrate what's wrong.

---

### Post by 23meg on 2010-08-16
> **zekopeko said:**
> I'm specifically talking about that dialog that pops up when your battery is about to reach 0%.

Dialog? Do you mean the Notify OSD bubble? A screenshot might help illustrate what's wrong.

---

### Post by 23meg on 2010-08-16
> **zekopeko said:**
> I'm specifically talking about that dialog that pops up when your battery is about to reach 0%.

Dialog? Do you mean the Notify OSD bubble? A screenshot might help illustrate what's wrong.

---

### Post by zekopeko on 2010-08-16
> **23meg said:**
> Dialog? Do you mean the Notify OSD bubble? A screenshot might help illustrate what's wrong.

No. It's a window that has a text that goes something like "Your computer is about to shutdown etc." plus a OK and Cancel button.

The problem is that it makes no sense. Both Cancel and OK do the same thing. They close the window. It should only have an OK button or more options such as Hibernate, Shutdown Now.

---

### Post by 23meg on 2010-08-16
> **zekopeko said:**
> No. It's a window that has a text that goes something like "Your computer is about to shutdown etc." plus a OK and Cancel button.

The problem is that it makes no sense. Both Cancel and OK do the same thing. They close the window. It should only have an OK button or more options such as Hibernate, Shutdown Now.

It's part of the Notify OSD spec to implement this with [morphing alert boxes]("https://wiki.ubuntu.com/NotificationDesignGuidelines#morphing") (the implementation being somewhat overdue), so it doesn't look like you need to file a bug report. What currently happens is that you get a standard Notify OSD fallback alert box, which is suboptimal.

---

### Post by ronacc on 2010-08-16
> **23meg said:**
> It's part of the Notify OSD spec to implement this with [morphing alert boxes]("https://wiki.ubuntu.com/NotificationDesignGuidelines#morphing") (the implementation being somewhat overdue), so it doesn't look like you need to file a bug report. What currently happens is that you get a standard Notify OSD fallback alert box, which is suboptimal.

It is not only suboptimal it is also wrong . I just installed A3 on my netbook and it is telling me that my known good and fully charged battery has only 1.9% capcity while it is actually plugged into the charger .

---

### Post by 23meg on 2010-08-16
> **ronacc said:**
> It is not only suboptimal it is also wrong . I just installed A3 on my netbook and it is telling me that my known good and fully charged battery has only 1.9% capcity while it is actually plugged into the charger .

If that's actually incorrect (gnome-power-manager's concept of "capacity" refers the charging performance of your battery compared to the manufacturer's specification, not its current level of charge; so it's relevant whether or not your device is plugged in) it's still an entirely unrelated issue to the subject of this thread, which is the alert box that pops up when your battery is empty.

---

### Post by ronacc on 2010-08-16
I am not sure whether notify osd or gnome-power manager popped up the dialog box , I am sure that whichever it was it was giving incorrect information . The charge state of the battery was 100% and just 2 days prior I had done a full power-cycle to auto shutdown that yielded within a couple of minutes of the "when new" duration . This warning also does not occur in earlier releases of ubuntu or the factory installed distro (xandros it's an EEE).

---

### Post by 23meg on 2010-08-16
> **ronacc said:**
> I am not sure whether notify osd or gnome-power manager popped up the dialog box , I am sure that whichever it was it was giving incorrect information . The charge state of the battery was 100% and just 2 days prior I had done a full power-cycle to auto shutdown that yielded within a couple of minutes of the "when new" duration . This warning also does not occur in earlier releases of ubuntu or the factory installed distro (xandros it's an EEE).

If this is consistent with the "capacity" you see in the battery indicator, that's definitely not a Notify OSD bug. It's either ACPI (the kernel) or gnome-power-manager. Remember to search for existing bugs.

---

