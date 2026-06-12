---
title: "Rhythmbox tray-icon plugin not working"
date: 2012-10-02
forum: Multimedia Software
---

### Post by MrsUser on 2012-10-02
Hello, does anyone know how to get the Rhythmboy tray-icon plugin to work?

I followed these instructions to add plugins:
[http://askubuntu.com/questions/147942/how-do-i-install-third-party-rhythmbox-plugins](http://askubuntu.com/questions/147942/how-do-i-install-third-party-rhythmbox-plugins)

But there is no tray-icon showing up. Plugin is activated, I checked alreaday. Notice: I am not talking about the notification icon in the volume menu. I want a separate system tray icon for Rhythmbox for easy and quick access.

Rhythmbox 2.96
Ubuntu 12.04, 64-bit.

EDIT: 
I contacted the developer. You have to whitelist it for system tray. This can easily be done with dconf-editor under
Desktop > Unity > Panel

Then in the systray-whitelist add the entry 'tray_icon_worker'.

[[IMG]http://i.imgur.com/uLLYas.png[/IMG]]("http://imgur.com/uLLYa")

---

