---
title: "What programme do you use for VNC?"
date: 2009-11-03
forum: Mythbuntu
---

### Post by geekyhawkes on 2009-11-03
Pretty much as per the title really.  I would really like to use VNC remote admin on my myth box but havent had much luck finding a decent vnc client for Ubuntu.  

Also, could someone give me an idea what port the vnc is setup onto by default under myth (is it the standard 5900?)

Thanks

---

### Post by dro0g on 2009-11-03
I use UltraVNC through wine - none of the native VNC clients support AD authentication.

---

### Post by hackmeister on 2009-11-04
xvncviewer

In my experiences it's faster than vinagre or the other vnc clients available.

---

### Post by DominicF on 2009-11-04
I've used NoMachine in the past for this.

---

### Post by badger_fruit on 2009-11-04
I use TSClient - has support for VNC and RDP (so a single tool for windows remote-desktop and VNC clients). VNC ports are usually 5800 and 5900 but can be configured to be anything you want (IIRC).

---

### Post by geekyhawkes on 2009-11-04
If i run tsclient i dont have vnc available from the drop down menu. All i have is RDP and RDP v5 selectable!???  

As a seperate question is the computer field expecting a name or IP address?  

I cant find xvncviewer to add in the normal 910 repos either.

---

### Post by badger_fruit on 2009-11-13
> **geekyhawkes said:**
> If i run tsclient i dont have vnc available from the drop down menu. All i have is RDP and RDP v5 selectable!???  

As a seperate question is the computer field expecting a name or IP address?  

I cant find xvncviewer to add in the normal 910 repos either.

I'm not sure why you're not getting a VNC option; in my 9.04 it was there and if I recall correctly, didn't need any additional packages etc to be installed.

The "Computer" field should accept either the name or the IP address.

---

