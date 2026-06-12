---
title: "knetworkmanager not starting at boot"
date: 2009-09-18
forum: Networking &amp; Wireless
---

### Post by ken_ver_2.5 on 2009-09-18
Let me try to explain this. First off I am using kde desktop
I use knetworkmanager so I can switch from wireless to
wired. for some reason I have to start it manually at each boot.

This is what I have tried.
System/system settings/ advanced tab/ auto start.
I pointed to the file in there.

If I reboot some times it loads. But if I do a cold boot
it does not start. I have placed the file on my desktop
for easy access. and I start it from there.

seems to me it should start automatically.

Should I be using another connection manager?

thanks in advance for your help.

---

### Post by malkdude on 2010-08-07
> **ken_ver_2.5 said:**
> Let me try to explain this. First off I am using kde desktop
I use knetworkmanager so I can switch from wireless to
wired. for some reason I have to start it manually at each boot.

This is what I have tried.
System/system settings/ advanced tab/ auto start.
I pointed to the file in there.

If I reboot some times it loads. But if I do a cold boot
it does not start. I have placed the file on my desktop
for easy access. and I start it from there.

seems to me it should start automatically.

Should I be using another connection manager?

thanks in advance for your help.

Hi. I was having the same problem. Here is how I got it fixed after random trying out things. Click on knetworkmanager icon in the system tray, then click on the Other tab. Then select show tray icon. Also, click on the KDE menu, and search for autostart. Add knetworkmanager there, and then, select it, and click on properties, then application then advanced options. There, in the Startup, I selected Enable launch feedback and place in system tray. In D-bus registration, I selected Run until finished.

Ok, I'm not sure if all these were necessary :), but now knetworkmanager starts up automatically (I do have another issue though, which is that it doesn't show the list of available networks by itself, unless I click on connect to other network. If anyone does know how to fix that, then please let me know, but I guess it deserves another thread). There, if that fixes it on your system, then could you please set the thread as SOLVED? Take care...

---

