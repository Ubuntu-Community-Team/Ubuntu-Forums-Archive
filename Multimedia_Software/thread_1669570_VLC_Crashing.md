---
title: "VLC Crashing"
date: 2011-01-17
forum: Multimedia Software
---

### Post by rflores2323 on 2011-01-17
my VLC keeps crashing when trying to open it with VLC stream and convert.

see below

```
xbmc@xbmc-desktop:~$ vlc
VLC media player 1.1.5 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
Warning: call to signal(13, 0x1)
[0x9738c04] main interface: creating httpd
Blocked: call to setenv("_PX_CONFIG_ORDER", "", 1)
Blocked: call to setlocale(6, "")
Warning: call to signal(13, 0x1)
Blocked: call to setenv("_PX_CONFIG_ORDER", "", 1)
Blocked: call to setlocale(6, "")
Warning: call to signal(13, 0x1)
Segmentation fault

```I followed the below however now when I try to open vlc it doesnt pull up anymore. how can I start it up on ubuntu so I can change preferences etc..  Below is how I change it.
2.) Start VLC and go to 
    A.) Tools->Preferences
    B.) On the bottom left click on the "All" radio button to show all settings.
    C.) On the treeview to the left exapnd the Interface tree node and select the "Main interfaces" tree item.
    D.) On the right side check the "HTTP remote control interface" option and press the Save button.

---

