---
title: "My network manager is missing"
date: 2011-12-17
forum: Networking &amp; Wireless
---

### Post by Fertech on 2011-12-17
I have ubuntu 10.04LTS and my daughter was using my computer and when I seen the screen I notice my Network Manager was missing on my desktop. I can still use the Internet, but sometimes when I reboot the computer I have no internet, and  I have to keep on rebooting the computer, Instead of trying to connect from network manager. Is there any way to put the nm-applet back in place?

---

### Post by Fertech on 2011-12-17
I don't know if the Local Area Network connection missing, how do I find out?

---

### Post by N00b-un-2 on 2011-12-17
alt-f2
nm-applet

---

### Post by Fertech on 2011-12-17
alt-f2 doesn't work

---

### Post by N00b-un-2 on 2011-12-17
try opening a terminal and executing nm-applet

---

### Post by Fertech on 2011-12-17
got this error "an instance of nm-applet is already running.

** (nm-applet:2300) : warning **: <warn> constructor(): couldn't initialize the d-bus manager.

---

### Post by Iowan on 2011-12-17
*Might* need to add a Notification Area to the top panel.

---

### Post by Fertech on 2011-12-17
How do I do that?

---

### Post by ubix on 2011-12-17
Make sure that ***»Network manager«*** is installed on your system. (search for it in Ubuntu Software Centre, or in Synaptic Package manager). If it is missing install it.
 
You can move your network manager to the panel by moving it there from your ***»System->Preferences«*** menu by right clicking ***»Network connections«***, or by simply dragging it to the panel. This may not be exactly the same as before but it does the job.

However, if you want it to be the same as it used to be, following is the alternative way of doing it:  

You must make sure ***»Notification Area«*** is present on your top panel. It is rather hard to see. If you are not sure, install it anyway. You can remove it later if you like. 

To install *»Notification Area«* _***right-click***_ the _top Ubuntu panel_, and select _***Add to Panel***_. Now select the _***Notification Area***_ and click _***Add***_. If you have bad eyes you may have trouble seeing it on the panel when it is empty.

Now reboot your system. After rebooting the ***»Network manager«*** should appear on the panel.

Good luck

---

