---
title: "Volume Step Key error"
date: 2009-01-01
forum: Multimedia Software
---

### Post by syle102 on 2009-01-01
So I know this has already been posted about. 
I'm running 8.10, and I'm trying to set the volume step percentage to 2 percent. I went through the gconf-editor using administrator privileges and navigated to the key /apps/gnome_settings_daemon/volume_step .
I initially changed the key to 2 percent, which had no effect on the volume control. 
I clicked on make default and make mandatory on the right click drop down menu, and now it tells me that the value is 2, and it is not writeable. If I try to delete the key, it tells me the value is 6, but is not writeable, and when I restart gconf-editor, the value is 2 again. However, this still has no effect on the volume control and the step size.
Can anyone help?

thanks

---

### Post by wolterh on 2009-05-10
Urm, I just changed my /apps/gnome_settings_daemon/volume_step to 2 and it started working right away.

Perhaps check for /schemas/apps/gnome_settings/daemon/volume_step to have a value of '<schema>'. Don't really know if it will have an effect, but that is what I have.

---

### Post by muchelaguito on 2009-10-14
Has anybody found a solution to this yet? I have the same issue, not even rebooting fixes the step value. I have a Latitude D630, running Jaunty and Gnome.

---

### Post by wolterh on 2009-10-14
It is now working for me.

---

