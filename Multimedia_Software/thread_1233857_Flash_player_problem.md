---
title: "Flash player problem"
date: 2009-08-07
forum: Multimedia Software
---

### Post by petersohn on 2009-08-07
My flash player was working properly, but when an update came, it started not to work properly. I tried reverting to the old version, but I wasn't successful. Finally I fully reinstalled Firefox. Since then, I can't install Flash player neither by the Ubuntu repositories nor by the deb file I download from Adobe. It uses some "Flash player 9.0 r999", which points to /usr/lib/swfdec-mozilla/libswfdecmozilla.so, and it doesn't work properly.

I downloaded the .so file directly from Adobe, and put it in /usr/lib/firefox-3.5.2/plugins, then Firefox displays that the plugin is present,  but it doesn't display Flash content if I disable the r999 version (as if Flash wasn't installed at all).

Is there any way to make it work again?

---

### Post by SoMBS on 2009-08-07
When you go to Synaptic Package Manager, what do you show installed for Flash? Some options may be adobe-flashplugin, flashplugin-nonfree, swfdec-mozilla. You only want one of these installed. I use adobe-flashplugin. I had some issues when initially going to version 10 and ended up having to remove .mozilla from my home directory and removing any Flash plugins that were installed and Firefox and then reinstalling. After doing that Flash sites now work.

---

### Post by Lampi on 2009-08-07
@petersohn: open synaptic, remove swfdec-mozilla, install adobe-flashplugin

---

### Post by lovinglinux on 2009-08-07
See **Solution** [*[COLOR="Red"]**FOT004**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT004).

---

### Post by petersohn on 2009-08-07
> **Lampi said:**
> @petersohn: open synaptic, remove swfdec-mozilla, install adobe-flashplugin
Thanks, that helped.

---

