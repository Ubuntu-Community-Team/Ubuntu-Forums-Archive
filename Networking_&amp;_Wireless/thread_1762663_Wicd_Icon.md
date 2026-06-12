---
title: "Wicd Icon"
date: 2011-05-19
forum: Networking &amp; Wireless
---

### Post by neo_omni on 2011-05-19
I have just upgraded to Natty but since doing so the Wicd icon is missing. Everything is working ok, connection is as it should be but I would prefer to have the icon showing that I am connected to my network.

I have spent hours looking for a solution and tried several different remedies, none of which work.

Can anyone help please?

---

### Post by jawilljr on 2011-05-19
Type this in a terminal:

```
gsettings set com.canonical.Unity.Panel systray-whitelist "['all']"
```

Logoff then relogin.

Jerry

---

### Post by neo_omni on 2011-05-19
Thankyou sir, all is now well.

---

