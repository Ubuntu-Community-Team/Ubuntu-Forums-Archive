---
title: "How to disable audio device for cetain user"
date: 2009-11-07
forum: Multimedia Software
---

### Post by m_alnaanah on 2009-11-07
I have installed Ubuntu 9.04 in a Library and the machines has built-in speakers.

I want to prevent the user from accessing the audio system.

I tried to change user privileges and removing the user from audio group, but that didn't work.


Can anyone help me.

Can I do it with normal permission/group manipulation.

I used to do that in other distros. by disabling access to /dev/audio file.
but that didn't work in Ubuntu. Why.

Please help

---

### Post by digitalbenji on 2009-12-03
I'd try going into System -> Administration -> Authorizations.  Then go to device-access, select Directly access sound devices, click on block, and select the user you want to disallow.

---

