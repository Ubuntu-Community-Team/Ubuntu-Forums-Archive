---
title: "Cannot resume VNC session"
date: 2009-06-30
forum: Networking &amp; Wireless
---

### Post by dgege on 2009-06-30
Hi,
I've setup vncserver to run at startup. I want to be able to VNC into a virtual session (not the physical one). It works fine, I can VNC inside. However, as soon as my client disconnects, it's like vnc dies. I cannot reconnect to my session. I tried everything from tutorials to trial and error, to no avail. I had the exact same setup under opensuse and it was working perfectly.

Anyone got an idea?

---

### Post by superprash2003 on 2009-06-30
well isnt that common, since you are directly using vnc to the virtual OS and then when the client disconnects even the connection to the Virtual OS would disconnect right

---

### Post by dgege on 2009-06-30
> **superprash2003 said:**
> well isnt that common, since you are directly using vnc to the virtual OS and then when the client disconnects even the connection to the Virtual OS would disconnect right

Well I didn't have that problem with opensuse, the session was resumable. Any way I can get that behaviour back?

---

### Post by dgege on 2009-07-02
> **dgege said:**
> Well I didn't have that problem with opensuse, the session was resumable. Any way I can get that behaviour back?

I reinstalled Jaunty and the problem went away. I must have screwed something up the first time!

---

