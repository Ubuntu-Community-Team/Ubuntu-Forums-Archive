---
title: "Unity system tray notification fix"
date: 2011-04-23
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by tlcstat on 2011-04-23
Greetings,
Unity defaults to tray notifications for Mumble, Wine, Skype, and HP. If you want additional tray notification you can add it with the following terminal commands.
You may have to reboot to activate the change.

Reset or whitelist panel notifications.

Whitelist all use.
gsettings set com.canonical.Unity.Panel systray-whitelist "['all']"

White list one or more apps, default apps are preserved and add your own app(s) at the end.
gsettings set com.canonical.Unity.Panel systray-whitelist "['JavaEmbeddedFrame', 'Mumble', 'Wine', 'Skype', 'hp-systray', 'YOUR_APPLICATION']"

Reset to original default use.
gsettings set com.canonical.Unity.Panel systray-whitelist "['JavaEmbeddedFrame', 'Mumble', 'Wine', 'Skype', 'hp-systray']"

Example: to add Claws Email
gsettings set com.canonical.Unity.Panel systray-whitelist  "['JavaEmbeddedFrame', 'Mumble', 'Wine', 'Skype', 'hp-systray',  'claws-mail']"
Be sure you use the same syntax that call the program from the command line. In other words not Claws-Mail or clawsmail etc. It should be claws-mail to work. Also, in this example you would have to activate the tray notification plug-in in Claws Mail.

Note: there are programs that will allow you to do this but I prefer the command line.

tlcstat

---

### Post by 41Nick on 2011-04-25
Thanks for this post. The Skype icon usually not appearing in my system tray has been driving me mad. I think that the reason for this is that I autostart skype when I log in. If skype started before the desktop, the icon did not appear.
I think I have solved this by making the skype startup script sleep for 15 seconds before it launches skype.

---

### Post by YuiDaoren on 2011-04-25
Thank you, tlcstat

---

