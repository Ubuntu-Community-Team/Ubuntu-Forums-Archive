---
title: "Checkgmail not working in 11.04"
date: 2011-03-20
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by kanishkdudeja on 2011-03-20
Ive installed checkgmail in 11.04..

but its icon doesn't get showed in the top right corner where it used to be in 10.10.

Any suggestions to fix this ?

---

### Post by lisati on 2011-03-20
*Thread moved to **Natty Narwhal Testing and Discussion**.*

---

### Post by kerry_s on 2011-03-20
gm-notify works the best.

---

### Post by MacUntu on 2011-03-20
> **kerry_s said:**
> gm-notify works the best.

+1, as it integrates fine into the messages menu:

[img]http://img.xrmb2.net/images/331095.png[/img]

Unfortunately you cannot open your account directly (I don't store such sensitive cookies/passwords in my browser), but maybe that has changed at Google's end.

---

### Post by kanishkdudeja on 2011-03-20
are you notified if any new mail arrives ?

---

### Post by MacUntu on 2011-03-20
Yes, the mail icon turns green and a notification bubble turns up.

---

### Post by kanishkdudeja on 2011-03-20
okay..thanks mate..il check it out..:)

---

### Post by rburkartjo on 2011-03-20
working fine on my end

---

### Post by Framli on 2011-03-20
Checkgmail won't work OOTB in Unity because it uses the notification area, which is now "whitelist based".

The default whitelist can be displayed via 
```
gsettings get com.canonical.Unity.Panel systray-whitelist
```
To whitelist another application
```
gsettings set com.canonical.Unity.Panel systray-whitelist "['JavaEmbeddedFrame', 'Wine', 'Skype', '<application name here>']"
```
Or simply whitelist everything
```
gsettings set com.canonical.Unity.Panel systray-whitelist "['all']"
```

---

