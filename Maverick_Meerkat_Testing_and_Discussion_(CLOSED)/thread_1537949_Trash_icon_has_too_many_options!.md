---
title: "Trash icon has too many options!"
date: 2010-07-24
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by mmcmonster on 2010-07-24
When you right click on the trash icon, there are just too many options.

Ideally, there should be three:
  Empty Trash
  Open Trash
  Options

With options having all the other possibilities in it.

---

### Post by Mr. Picklesworth on 2010-07-24
That's a matter of how gnome-panel is designed. Every panel applet is like that.

Yes, I agree it's horrible. I filed an enhancement request here: [https://bugzilla.gnome.org/show_bug.cgi?id=616244](https://bugzilla.gnome.org/show_bug.cgi?id=616244)

---

### Post by MacUntu on 2010-07-24
Not sure he's talking about the panel icon, but the desktop icon's context menu is a joke:

[img]http://img.xrmb2.net/images/874338.png[/img]

Yeah, I wanna compress Trash. :D

---

### Post by ktp on 2010-07-24
> **MacUntu said:**
> Yeah, I wanna compress Trash. :D

At least compress trash will take up less space. :lolflag:

---

### Post by cariboo on 2010-07-24
Don't use trash. :)

---

### Post by kyleabaker on 2010-07-24
Shift+Del :D

It would be nice if the panel applet could be replaced with an indicator applet version that can be placed separate from the other indicator icons. Then it could be easily tweaked to perfection.

I can't think of the number of times that I've right-clicked and selected "Remove from Panel" by accident. Sure its trivial to fix, but its an annoyance all the same.

Is this trash menu problem the type that would be considered a paper cut?

---

### Post by Mr. Picklesworth on 2010-07-24
> **kyleabaker said:**
> Is this trash menu problem the type that would be considered a paper cut?

It isn't, because it isn't easily fixed.

---

### Post by kyleabaker on 2010-07-24
> **Mr. Picklesworth said:**
> It isn't, because it isn't easily fixed.

Thats too bad. So it won't be getting fixed for Maverick.. :(

Writing a modified applet and submitting it would be trivial, but I still don't think it would make it to Maverick.

---

### Post by ktp on 2010-07-24
> **kyleabaker said:**
> It would be nice if the panel applet could be replaced with an indicator applet version that can be placed separate from the other indicator icons. Then it could be easily tweaked to perfection.

I can't think of the number of times that I've right-clicked and selected "Remove from Panel" by accident. Sure its trivial to fix, but its an annoyance all the same.

I still sometimes remove the Indicator Applet because I am just so used to right clicking on the "notification" icons.  When I see "remove for panel" for some reason the brain still thinks it will only remove that icon.  I guess some habits are really hard to break.

---

### Post by Merk42 on 2010-07-24
> **ktp said:**
> I still sometimes remove the Indicator Applet because I am just so used to right clicking on the "notification" icons.  When I see "remove for panel" for some reason the brain still thinks it will only remove that icon.  I guess some habits are really hard to break.How can you removed a specific applet? Is it even possible?

---

### Post by ktp on 2010-07-25
> **Merk42 said:**
> How can you removed a specific applet? Is it even possible?

you can't but when I right click on the icon and see the menu with item "Remove From Panel", the brain most of the time assumes it will remove just that applet/icon.  I guess I am still used to "old ways", where right click would have quit or such to close the app.  I guess I just need to get used it; maybe one day.  But for now, I still right click the icon before realizing oh wait...:D

---

### Post by Mr. Picklesworth on 2010-07-25
> **ktp said:**
> I still sometimes remove the Indicator Applet because I am just so used to right clicking on the "notification" icons.  When I see "remove for panel" for some reason the brain still thinks it will only remove that icon.  I guess some habits are really hard to break.

You aren't the only one, believe me:

[https://bugs.launchpad.net/ubuntu/+source/indicator-applet/+bug/519553](https://bugs.launchpad.net/ubuntu/+source/indicator-applet/+bug/519553)

Unfortunately, it all just points back to the panel being a really ugly bit of software that needs to be replaced. Some day...

---

### Post by 23meg on 2010-07-25
> **Merk42 said:**
> How can you removed a specific applet? Is it even possible?

If you mean components that are hosted by the indicator applet and Indicator Applet Session, you can remove them individually by removing any of the indicator-me, indicator-session, indicator-application, indicator-sound and indicator-messages packages. To remove a specific application-specific indicator, you go to the preferences of the application and disable it there.

---

### Post by Merk42 on 2010-07-25
> **23meg said:**
> If you mean components that are hosted by the indicator applet and Indicator Applet Session, you can remove them individually by removing any of the indicator-me, indicator-session, indicator-application, indicator-sound and indicator-session packages. To remove a specific application-specific indicator, you go to the preferences of the application and disable it there.
I was referring to the former.
It requires manually removing packages? Okay I guess Canonical doesn't want you to edit them easily

---

### Post by 23meg on 2010-07-25
> **Merk42 said:**
> I was referring to the former.
It requires manually removing packages? Okay I guess Canonical doesn't want you to edit them easily

Okay, I guess you don't want me to help you easily.

---

### Post by ktp on 2010-07-25
> **Merk42 said:**
> I was referring to the former.
It requires manually removing packages? Okay I guess Canonical doesn't want you to edit them easily

oh...I removed most of them, since i don't really use/need them, by removing the packages. I am hoping, in future since this is "work-in-progress", there is better way to remove them.  At least package names are easy to remember.

---

### Post by ktp on 2010-07-25
> **Mr. Picklesworth said:**
> You aren't the only one, believe me:

[https://bugs.launchpad.net/ubuntu/+source/indicator-applet/+bug/519553](https://bugs.launchpad.net/ubuntu/+source/indicator-applet/+bug/519553)

Unfortunately, it all just points back to the panel being a really ugly bit of software that needs to be replaced. Some day...

Thanks for the bug link...marked it "This bug affects you".

---

