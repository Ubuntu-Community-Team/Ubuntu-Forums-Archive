---
title: "strange bug with flash"
date: 2010-07-04
forum: Multimedia Software
---

### Post by atma on 2010-07-04
hello everybody, I have got a strange problem with flash. If there is a flash video running in a page inside my browser (which can be firefox or chrome, the problem is the same), and I close or reload another page which is inside a tab in the same browser's window, flash stops working and the video becomes gray, and I have to reload it. Do you have any hint about it? thank you a lot

---

### Post by lovinglinux on 2010-07-04
Type **about[noparse]:[/noparse]config** in Firefox address bar, then type **plugin.expose_full_path** in the filter, then double-click the same item in the results to make it **true**. Then type **about[noparse]:[/noparse]plugins** in the address bar, find Shockwave Flash, copy the corresponding Path and Version and paste here.

---

### Post by atma on 2010-07-05
> **lovinglinux said:**
> Type **about[noparse]:[/noparse]config** in Firefox address bar, then type **plugin.expose_full_path** in the filter, then double-click the same item in the results to make it **true**. Then type **about[noparse]:[/noparse]plugins** in the address bar, find Shockwave Flash, copy the corresponding Path and Version and paste here.

thank you, the result is this:

File: /var/lib/flashplugin-installer/npwrapper.libflashplayer.so
Version: Shockwave Flash 10.1 r53

---

### Post by lovinglinux on 2010-07-05
You have the latest 32bit flash version as you are supposed to.

I have a similar issue that I can't reproduce or identify exactly when it happens. Sometimes flash simply stops working and I need to restart the browser to make it work again.

You could try to create a new Firefox user profile and check if the problem persists. See Firefox [Profiles](http://firefox-tutorials.blogspot.com/2010/05/profiles.html) tutorial.

---

### Post by atma on 2010-07-05
> **lovinglinux said:**
> You have the latest 32bit flash version as you are supposed to.

I have a similar issue that I can't reproduce or identify exactly when it happens. Sometimes flash simply stops working and I need to restart the browser to make it work again.

You could try to create a new Firefox user profile and check if the problem persists. See Firefox [Profiles](http://firefox-tutorials.blogspot.com/2010/05/profiles.html) tutorial.

I usually don't have to restart the browser, just to reload the page. The same problem occurs with chrome, so I guess it's a flash-related issue

---

### Post by lovinglinux on 2010-07-05
> **atma said:**
> I usually don't have to restart the browser, just to reload the page. The same problem occurs with chrome, so I guess it's a flash-related issue

Probably is an issue with version 10.1 r53 running on 64bit browser. I didn't have that problem while using the old 10.0.45 64bit version.

---

### Post by atma on 2010-08-22
> **lovinglinux said:**
> Probably is an issue with version 10.1 r53 running on 64bit browser. I didn't have that problem while using the old 10.0.45 64bit version.

I reverted to the previous version 10.0.45 and the problem is gone! thank you :)

---

### Post by lovinglinux on 2010-08-22
> **atma said:**
> I reverted to the previous version 10.0.45 and the problem is gone! thank you :)

Keep in mind that version has a critical vulnerability. You should get the latest 10.1.82.

Get [FLASH-AID](https://addons.mozilla.org/en-US/firefox/addon/161939/), an extension to remove conflicting flash plugins and install the proper version according to your browser architecture.

---

