---
title: "MythTV : mythdvd and mtd transcode support"
date: 2006-07-20
forum: Multimedia &amp; Video
---

### Post by tbonius on 2006-07-20
I have noticed that the mythdvd .deb sources in Ubuntu repositiories have no support in mtd for transcode.  Does anyone know of any other repositories that have good mythtv .deb files for Ubuntu Dapper Drake?

Thanks

Thom :mad:

---

### Post by wallcrawler78 on 2006-10-30
I noticed this as well.  It completly drove me nuts.  Did you ever get past it? I am running Edgy on an AMD64.  Ubuntu Repos seem to workt the best and easiest to install,  but I really need transcoding to work in MythDVD since i want to put my DVD collecton on the box.  Any advice?

---

### Post by superm1 on 2006-10-30
Are you guys sure that transcode isn't working?

I haven't personally tried it yet, but the latest edgy binary for mythdvd included mtd.

Looking at the mythplugins configure script, there is no build time option for transcode support in mythdvd anymore.  Regardless, mythplugins is built with --enable-all.

I'll try this later on however.

---

### Post by vanhoja on 2006-10-30
> **wallcrawler78 said:**
> I noticed this as well.  It completly drove me nuts.  Did you ever get past it? I am running Edgy on an AMD64.  Ubuntu Repos seem to workt the best and easiest to install,  but I really need transcoding to work in MythDVD since i want to put my DVD collecton on the box.  Any advice?

I just recently re-installed MythTV on my AMD64 box after breifly toying with Fedora Core 6... and used the myth-* packages from the Ubuntu repositories, but I too found the MythDVD plugin lacking transcoding support... or, *more accurately,* encrypted DVD support.

I checked the documentation for libdvdread3, and followed its suggestion to look at the debian-unofficial repository.  I'm not at home at the moment, so I can't check the URL for it, but try looking them up.  **Note bene,** the DMCA applies in the US, so please read all documentation concerning the dvd packages.

Hope this helps... :-k

---

### Post by superm1 on 2006-10-30
If its encrypted DVD support you are missing, you will need to install libdvdcss2.  This is outlined here:

[https://help.ubuntu.com/community/MythTV_Edgy_media](https://help.ubuntu.com/community/MythTV_Edgy_media)

---

### Post by wallcrawler78 on 2006-10-30
Thanks for the great info everyone.  I will give it another shot tommorow night.  :)

---

### Post by rworne on 2006-11-12
I had this same issue.  The answer was to add libdvdcss2 AND run mtd as root.

That got dvd playback and transcoding working for me.

So try to run mtd as root and see if it works better - I'm guessing it needs to be root to access /dev/dvd which in my case is symlinked to /dev/hda.

lrwxrwxrwx 1 root root  3 2006-11-12 02:56 dvd -> hda
brw-rw---- 1 root cdrom 3, 0 2006-11-12 02:56 hda

It's too late now for me to mess with it further, but I'd guess changing the permissions on /dev/hda to brw-rw-rw- would fix it without having to run mtd as root.

---

### Post by superm1 on 2006-11-12
Well, just making sure that "mythtv" is in the cdrom group should do.  No needs to run as root.

I'll add this to the todo list for the feisty package.

---

### Post by rworne on 2006-11-12
Thanks! I knew there was an easy answer.

---

