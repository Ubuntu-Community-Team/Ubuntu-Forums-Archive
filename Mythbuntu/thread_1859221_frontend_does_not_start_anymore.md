---
title: "frontend does not start anymore"
date: 2011-10-13
forum: Mythbuntu
---

### Post by marco.hahn on 2011-10-13
I have set up a new standalone machine, backend and frontend on a single PC. Since I knew that I would encounter difficulties with the graphics driver and the hauppauge remote control, I somehow turned off automatic start of mythwelcome. Now I cannot find a way to turn it on again correctly.

Regardless of whether I switch on the PC manually or whether it automatically starts up to record a show, I want mythwelcome to start up. However, even if I select Mythbuntu if xfce session manager, I only get a xfce desktop, but no mythwelcome or mythfrontend.

System is mythbuntu 11.04.

What's wrong here? Any help is welcome!

Marco

---

### Post by nickrout on 2011-10-13
> **marco.hahn said:**
> I have set up a new standalone machine, backend and frontend on a single PC. Since I knew that I would encounter difficulties with the graphics driver and the hauppauge remote control, I somehow turned off automatic start of mythwelcome. Now I cannot find a way to turn it on again correctly.

Regardless of whether I switch on the PC manually or whether it automatically starts up to record a show, I want mythwelcome to start up. However, even if I select Mythbuntu if xfce session manager, I only get a xfce desktop, but no mythwelcome or mythfrontend.

System is mythbuntu 11.04.

What's wrong here? Any help is welcome!

Marco

mythbuntu control centre should sort that for you.

---

### Post by klc5555 on 2011-10-13
> **marco.hahn said:**
> I have set up a new standalone machine, backend and frontend on a single PC. Since I knew that I would encounter difficulties with the graphics driver and the hauppauge remote control, I somehow turned off automatic start of mythwelcome. Now I cannot find a way to turn it on again correctly.

Regardless of whether I switch on the PC manually or whether it automatically starts up to record a show, I want mythwelcome to start up. However, even if I select Mythbuntu if xfce session manager, I only get a xfce desktop, but no mythwelcome or mythfrontend.

System is mythbuntu 11.04.

What's wrong here? Any help is welcome!

Marco

Add the command mythfrontend to the 'Application Autostart' menu under 'Settings' > 'Session and Startup' in xfce's start menu.

---

### Post by marco.hahn on 2011-10-14
> **klc5555 said:**
> Add the command mythfrontend to the 'Application Autostart' menu under 'Settings' > 'Session and Startup' in xfce's start menu.

This is definitely not where I switched it off, but now it works like I want it. Thanks a lot!

Marco

---

