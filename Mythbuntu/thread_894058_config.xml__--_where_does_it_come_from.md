---
title: "config.xml  -- where does it come from?"
date: 2008-08-18
forum: Mythbuntu
---

### Post by Dewey_Oxberger on 2008-08-18
Crazy question.  I'm up to my eyeballs in problems so I'm looking through logs and watching for scary messages.

I've noticed my .mythtv/config.xml is empty.

When I run mythfrontend I'm getting "unexpected end of file" for that file so I'm wondering how to make a new one?

What config app creates that xml file?

---

### Post by Loaded.len on 2008-08-18
./mythtv/config.xml contains the databas host name, db user name, db password (randomly generated during package installation, and db name (mythconverg).

Not sure if running mythtv-setup will correct this or not, but it's worth a try.

---

### Post by Dewey_Oxberger on 2008-08-19
Running mythtv-setup doesn't seem to write config.xml.

On a system with the front and back ends on the same hardware is config.xml still needed?

---

### Post by Loaded.len on 2008-08-19
Yes, because the frontend and backend operate independently of each other. They could care less if they are in the same box or not, they still need a roadmap to talk to each other.

---

### Post by mukulakivi on 2008-09-29
> **Dewey_Oxberger said:**
> Crazy question.  I'm up to my eyeballs in problems so I'm looking through logs and watching for scary messages.

I've noticed my .mythtv/config.xml is empty.

When I run mythfrontend I'm getting "unexpected end of file" for that file so I'm wondering how to make a new one?

What config app creates that xml file?

Same problem to me and mythfrontend is not starting anymore - it will also complain of every theme files nowadays. I did one update yesterday and nvidia GLX library also stop working. Would be nice to know if this is because empty config.xml or not

---

### Post by frokki on 2008-11-08
Don't know, but I also get this error despite MythTV seems to be working like a charm! (for once, lol).

---

