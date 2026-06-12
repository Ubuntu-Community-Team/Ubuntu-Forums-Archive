---
title: "Cannot click on flash, again..."
date: 2010-07-28
forum: Multimedia Software
---

### Post by mvandemar on 2010-07-28
Recently in the course of normal nightly updates my Firefox got updated to a newer version. I believe that it was a security update, so I don't really want to roll back to an earlier version (I went from 3.5.x to 3.6.8), but I am having some issues with the current version. One of the more annoying issues is that a previous bug that was fixed has resurfaced, and now the prior solution no longer works.

The only way I can left-click within Flash and have it work is by holding down the right mouse button at the same time as I click. Previously I was able to get around this with this fix:

> **lovinglinux said:**
> The extension installed the 32bit plugin because Adobe is no longer supporting the 64bit and ALL currently available versions have a critical vulnerability. You shouldn't use the 64bit version anymore, at least until the provide a new version. When they do, I will provide it again with FLASH-AID.

Meanwhile, you can fix you problem doing the following:

```
gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
```

Add the following line before the last line of the file opened by the previous command:

```
export GDK_NATIVE_WINDOWS=1
```

Save and restart the browser.

That line is still there, and I even tried reinstalling flash (using the FLASH-AID plugin someone on these boards wrote), but nadda. The problem does not exist in free standing flash applications and flash running in Chrome works fine, and it worked fine in Firefox before the upgrade.

Does anyone have a solution for this?

Thanks!

-Michael

---

### Post by lovinglinux on 2010-07-29
Type **about[noparse]:[/noparse]config** in Firefox address bar, then type **plugin.expose_full_path** in the filter, then double-click the same item in the results to make it **true**. Then type **about[noparse]:[/noparse]plugins** in the address bar, find Shockwave Flash, copy the corresponding Path and Version and paste here.

---

### Post by mvandemar on 2010-07-29
> **lovinglinux said:**
> Type **about[noparse]:[/noparse]config** in Firefox address bar, then type **plugin.expose_full_path** in the filter, then double-click the same item in the results to make it **true**. Then type **about[noparse]:[/noparse]plugins** in the address bar, find Shockwave Flash, copy the corresponding Path and Version and paste here.

The full path was already exposed. The info is:

Shockwave Flash

    File: /var/lib/flashplugin-installer/npwrapper.libflashplayer.so
    Version: 
    Shockwave Flash 10.1 r53

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes

Thanks.

-Michael

---

### Post by lovinglinux on 2010-07-29
I dunno why the fix isn't working.

---

### Post by mvandemar on 2010-07-31
> **lovinglinux said:**
> I dunno why the fix isn't working.

I don't either. I just completely uninstalled flash, removed the fix, and then reinstalled flash... and now it's working, without the fix there. Go figure. :)

However, I seem to remember it working for a while the last time too, so will see if it sticks this time or not.

-Michael

---

### Post by lovinglinux on 2010-07-31
> **mvandemar said:**
> I don't either. I just completely uninstalled flash, removed the fix, and then reinstalled flash... and now it's working, without the fix there. Go figure. :)

However, I seem to remember it working for a while the last time too, so will see if it sticks this time or not.

-Michael

That's weird :)

---

### Post by mvandemar on 2010-08-06
> **lovinglinux said:**
> That's weird :)

Yes, it is weird. As I suspected it stopped working after a brief period of time.

Am I the only one experiencing this...?

-Michael

---

### Post by lovinglinux on 2010-08-06
> **mvandemar said:**
> Yes, it is weird. As I suspected it stopped working after a brief period of time.

Am I the only one experiencing this...?

-Michael

I haven't seen any similar issue.

---

### Post by mvandemar on 2010-08-06
Ok, so the tiniest details do make a difference. :)

> Add the following line **before** the last line of the file opened by the previous command:

I was adding it at the end of the file, so flash was starting before that line was getting called.

Thank you for looking. This was driving me nuts.

-Michael

---

### Post by lovinglinux on 2010-08-07
> **mvandemar said:**
> Ok, so the tiniest details do make a difference. :)

I was adding it at the end of the file, so flash was starting before that line was getting called.

Thank you for looking. This was driving me nuts.

-Michael

I'm glad you fixed it.

---

