---
title: "Am I the only one who loses Firefox' global menu sometimes?"
date: 2011-03-26
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Bazon on 2011-03-26
Sometimes it's there, sometimes not. I can't really reproduce it. I wish I could, so that I could file a bug, but so?

---

### Post by lucazade on 2011-03-26
> **Bazon said:**
> Sometimes it's there, sometimes not. I can't really reproduce it. I wish I could, so that I could file a bug, but so?

I haven't seen this error but anyway I see a warning about dbus-menu service (needed by globalmenu) when I start firefox

```
$ firefox

(firefox-bin:1846): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_menuitem_property_set_shortcut: assertion `gtk_accelerator_valid(key, modifier)' failed
```

do you have any?

---

### Post by Bazon on 2011-03-26
Yes, I get exactly the same.

Directly after starting, the global menu is most of the time there. I seem to lose it only after some time.

I keep watching in the Terminal to see if there is anything related to that.

---

### Post by Iehova on 2011-03-26
Yep, that's happened to me. I think it's also happened with empathy once or twice...

---

### Post by rajeev1204 on 2011-03-26
What about synaptic? I have not seen a global menu yet for this application.

---

### Post by rburkartjo on 2011-03-26
yup it happens on my end periodically

---

### Post by Atermoon on 2011-03-26
> **rajeev1204 said:**
> What about synaptic? I have not seen a global menu yet for this application.

It's not synaptic specific. Apps that you run as root don't use the global menu. I read somewhere that it was on purpose but don't remember why, it was months ago.

On topic: yeah, my menus disappear every once in a while as well.

---

### Post by r-senior on 2011-03-26
I've had it happen with Firefox and Geany. In some cases I think it comes back but I don't know a specific sequence of things that makes it do so.

---

### Post by webme on 2011-03-26
Firefox's appmenu is packaged independently, it has its own package different from the rest, so, it could be firefox-specific only bug.

---

### Post by chrisccoulson on 2011-03-26
No, it's not firefox specific. What you are seeing is [bug 718926]("https://bugs.launchpad.net/ubuntu/+source/bamf/+bug/718926")

---

