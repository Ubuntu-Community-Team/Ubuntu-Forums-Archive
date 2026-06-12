---
title: "Sonata popup notifications"
date: 2009-01-28
forum: Multimedia Software
---

### Post by rozbarwinek on 2009-01-28
Is there a way to force sonata to use default ubuntu notifications instead of it's ugly yellow one?

---

### Post by shiva.n on 2009-08-12
Bump. Anyone solve this?
 
I have a almost monochrome wallpaper and AllBlack icons and running openbox. Both the notifications, and the Sonata theme look ugly on my setup.
 
How do I get Sonata to use Ubuntu Notifications? How can I change the theme for Sonata?

---

### Post by mcduck on 2009-08-12
You'd have to ask Sonata's developers to start using the new notification system Ubuntu 9.04 uses instead of Gnome's own notifications. But that's not very likely to happen, since as far as I know Ubuntu 9.04 is the only one using it..

Actually notifications seem to be more or less broken after Ubuntu started using it's own system for them. With the old notification-daemon there were several themes available, and notifications also used window type "Notification" which allowed making them transparent with Compiz. Now they use "Normal" window type instead..

But, at least, most themes allow you to change the notification color. Just go to System/Preferences/Appearance, Theme-tab, click the Customize-button and on the Color-tab change Tooltip color. (I really can't imagine why most themes default to yellow tooltips & notifications).

Now that I started looking into this, is your Sonata notification a square one, or does it look like a bubble with rounded corners? Because in previous ubuntu versions notifications used Ubuntu's own yellow bubble theme and I always had to change them to Gnome's own square theme that follow GTK theme colors. Now it seems that the key for this setting doesn't exist in gconf any more. At least my notifications use the Gnome theme instead of the ugly yellow Ubuntu-bubbles, so not having the configuration isn't that big of a problem, perhaps the ubuntu-theme for old notification-daemon was removed when new Ubuntu-style notifications were introduced..

---

### Post by Tibuda on 2009-08-12
> **mcduck said:**
> You'd have to ask Sonata's developers to start using the new notification system Ubuntu 9.04 uses instead of Gnome's own notifications. But that's not very likely to happen, since as far as I know Ubuntu 9.04 is the only one using it..

They have only to use libnotify, the same used before in intrepid. Notify OSD is only a new daemon to handle them.

---

### Post by mcduck on 2009-08-12
> **danielrmt said:**
> They have only to use libnotify, the same used before in intrepid. Notify OSD is only a new daemon to handle them.

In that case I really don't know what's the problem, since Sonata notifications used to have correct window type and follow notification-daemon's settings. Now the window type is wrong, and popups look like they were created by notification-daemon (which doesn't even exist any more).

I suppose the only way to get this sorted out is to ask the developers.

edit: I'm currently reading through Sonata's mailing lists to gather more info about this, and found this message: [https://lists.berlios.de/pipermail/sonata-users/2009-June/001097.html]("https://lists.berlios.de/pipermail/sonata-users/2009-June/001097.html")

So it seems that Sonata doesn't currently use real notifications at all (that explains a lot), but on the other hand at least somebody is working on plugin that provides Notify-OSD notifications by using pynotify.

edit2: SVN version of Sonata includes the plugin for Notify-OSD -style notifications: [http://smyte.wordpress.com/2009/05/18/music-player-daemon-sonata-notifications-with-notify-osd-tutorial-disclaimer-inside/]("http://smyte.wordpress.com/2009/05/18/music-player-daemon-sonata-notifications-with-notify-osd-tutorial-disclaimer-inside/")
[http://en.leoiannacone.com/en/blog/2009/05/a-simple-plugin-for-sonata/]("http://en.leoiannacone.com/en/blog/2009/05/a-simple-plugin-for-sonata/")

---

