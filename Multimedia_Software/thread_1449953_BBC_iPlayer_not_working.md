---
title: "BBC iPlayer not working"
date: 2010-04-08
forum: Multimedia Software
---

### Post by yakekaj on 2010-04-08
I have done all the 'How to' for multimedia, but iPlayer doesn't work.

When I click on a program I want to watch it goes through to the next page, then when I click play it 'Loads' continuously...

This is the only thing stopping me from converting fully to Linux.  I currently run Vista as well as Ubuntu on my Dell Laptop, but because of iPlayer not functioning I can't break away from Microsoft...Curses

Can anyone help me out here... Please....

---

### Post by ajgreeny on 2010-04-08
Does flash work on other websites?  It is needed for the iPlayer on BBC sites, so if you don't have it make sure to install with ```
sudo apt-get install flashplugin-installer
```and it will be downloaded and installed direct from Adobe.

---

### Post by Fenris_rising on 2010-04-08
Just checking. Are you in the UK? iPlayer is UK only although you may be able to use a proxy to get round this restriction.

Regards

Fenris

---

### Post by AlanR8 on 2010-04-08
Has worked perfectly for me for the last year or so on all distributions of K/Ubuntu. 

As asked earlier, are you in the UK? 

Can you view YouTube vids? 

If you can it means you have Flash installed so the iPlayer should work.

I'm running Lucid Beta but have had no problems over the last year or so.....

Keep us posted

---

### Post by UserSince2003 on 2010-04-12
Try this.  It worked for me:
[http://kevin.vanzonneveld.net/techblog/article/fix_flash_problems_on_ubuntu/](http://kevin.vanzonneveld.net/techblog/article/fix_flash_problems_on_ubuntu/)

---

### Post by cjcj on 2010-04-26
This one sounds like the problem I had. I found this fix on another thread.

The fix was to add "export GDK_NATIVE_WINDOWS=1" to the /usr/lib/nspluginwrapper/i386/linux/npviewer file.

My npviewer file:
Code:
#!/bin/sh
TARGET_OS=linux
TARGET_ARCH=i386
export GDK_NATIVE_WINDOWS=1
. /usr/lib/nspluginwrapper/noarch/npviewer

The export bit is the bit that is missing. You will probably find that the environment variable is already being set but not exported. Obviously this line must come before npviewer is run (in the last line of the file).

---

