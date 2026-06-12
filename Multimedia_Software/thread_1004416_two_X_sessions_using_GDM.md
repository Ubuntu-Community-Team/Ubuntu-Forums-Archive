---
title: "two X sessions using GDM"
date: 2008-12-07
forum: Multimedia Software
---

### Post by detl_ on 2008-12-07
Hi,
I would like to start a two X Sessions during startup using GDM.

Background: 
During my daily work I sometimes need to run end user tests for an application which requires a running X session. In order to not interfeer
the tests I would like to have them running on a second X session which I can configure with the DISPLAY environment variable.( currently DISPLAY is set to ':0').

As I read in the GDM manual I should be able to configure a new x server in my gdm.conf-custom file. But I cannot figure out how I can start the session without control, so I dont need to login to the new session.

Does anybody know how to run a second X server which starts with my Standard X Server and can be configured to use it in the described scenario ?


thanks,
detl

---

### Post by Jose Catre-Vandis on 2008-12-07
I could be wrong, but I think you need a second/different user on your system, and then you have to log in as that user to get a second X session.

---

### Post by detl_ on 2008-12-11
that means, that I have to login to the other X session as well as to my 'primary' one.
What I want is that the 'invisible' x session also starts when I start my 'primary' session.

---

