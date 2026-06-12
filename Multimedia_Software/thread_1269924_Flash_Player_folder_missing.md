---
title: "Flash Player folder missing?"
date: 2009-09-18
forum: Multimedia Software
---

### Post by isecdemo on 2009-09-18
I read about the threat posed by Flash cookies and tried locating the folder where Flash cookies are supposed to be located.

~/.macromedia/Flash_Player/#SharedObjects/
~/.macromedia/Flash_Player/macromedia.com/

I couldn't find the Flash Player folder on my Ubuntu 9.04 system. Is Flash Player not installed by default on Ubuntu? I'm able to view Flash content on my Firefox browser though. This is puzzling. I hope someone can clear my confusion.

---

### Post by yabbadabbadont on 2009-09-18
Exactly *how* did you try to find thoes directories?  The leading period '.' in the name makes them hidden by default.

Example:
```
/home/daffy $ ls -alR .macromedia
.macromedia:
total 12
drwx------  3 daffy daffy 4096 2009-09-16 02:38 .
drwxr-xr-x 28 daffy daffy 4096 2009-09-18 18:18 ..
drwxr-x---  4 root  daffy 4096 2009-09-16 02:38 Flash_Player

.macromedia/Flash_Player:
total 16
drwxr-x--- 3 root  daffy 4096 2009-09-16 02:38 #SharedObjects
drwxr-x--- 4 root  daffy 4096 2009-09-16 02:38 .
drwx------ 3 daffy daffy 4096 2009-09-16 02:38 ..
drwxr-x--- 3 root  daffy 4096 2009-09-16 02:38 macromedia.com

.macromedia/Flash_Player/#SharedObjects:
total 12
drwxr-x--- 3 root daffy 4096 2009-09-16 02:38 .
drwxr-x--- 4 root daffy 4096 2009-09-16 02:38 ..
drwxr-x--- 2 root daffy 4096 2009-09-16 02:38 Y2WCRNMP

.macromedia/Flash_Player/#SharedObjects/Y2WCRNMP:
total 8
drwxr-x--- 2 root daffy 4096 2009-09-16 02:38 .
drwxr-x--- 3 root daffy 4096 2009-09-16 02:38 ..

.macromedia/Flash_Player/macromedia.com:
total 12
drwxr-x--- 3 root daffy 4096 2009-09-16 02:38 .
drwxr-x--- 4 root daffy 4096 2009-09-16 02:38 ..
drwxr-x--- 3 root daffy 4096 2009-09-16 02:38 support

.macromedia/Flash_Player/macromedia.com/support:
total 12
drwxr-x--- 3 root daffy 4096 2009-09-16 02:38 .
drwxr-x--- 3 root daffy 4096 2009-09-16 02:38 ..
drwxr-x--- 3 root daffy 4096 2009-09-16 02:38 flashplayer

.macromedia/Flash_Player/macromedia.com/support/flashplayer:
total 12
drwxr-x--- 3 root daffy 4096 2009-09-16 02:38 .
drwxr-x--- 3 root daffy 4096 2009-09-16 02:38 ..
drwxr-x--- 2 root daffy 4096 2009-09-16 02:39 sys

.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys:
total 12
drwxr-x--- 2 root daffy 4096 2009-09-16 02:39 .
drwxr-x--- 3 root daffy 4096 2009-09-16 02:38 ..
-rw-r--r-- 1 root daffy  374 2009-09-16 02:39 settings.sol


```
Note that I have modified the permissions on my setup so that most flash objects will work correctly while preventing the storage of any data whatsoever.

---

### Post by isecdemo on 2009-09-19
I CD'd to my home folder.

cd /home/<username>/

Then I looked for the Macromedia folder using the following command.

ls -la .macromedia

The Macromedia could not be found. I tried other variants like search for "flash_player" and "adobe" folders. Could not find them.
I then used the find command from root to try to find words matching "macromedia", "flash" and "adobe". Also hunted for "*.sol" files. All returned no result.

---

### Post by isecdemo on 2009-09-19
I used the command you listed in your post.

<username>@<machine>:~$ ls -alR .macromedia
ls: cannot access .macromedia: No such file or directory

---

### Post by yabbadabbadont on 2009-09-19
Then I would guess that you actually *don't* have Adobe's version of flash installed.  It isn't included in the default install, you have to add it.  What happens if you go to the following webpage?  (It is the settings manager page for Adobe/Macromedia flash)

[http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager.html](http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager.html)

---

### Post by isecdemo on 2009-09-20
I visited the site you provided. I can't see the manager panel so that means I don't have Flash installed. How is it that I'm able to view Flash content from Firefox? Does Ubuntu provide another plugin that supports Flash content? Do I still need to install Flash Player if that is the case?

---

### Post by yabbadabbadont on 2009-09-20
If you enter about:plugins in the address bar in firefox, is there any plugin listed that handles *.swf or *.flv?

---

### Post by isecdemo on 2009-09-21
Yes. There are 2 plugins that handle each extension. Does that imply that I do not need to manually install Flash Player?

---

### Post by yabbadabbadont on 2009-09-22
No, it means that those plugins are imperfect at handling all flash content.  You'll have to decide if you can live with it the way it is currently, or choose to install Adobe's flash player.  If you choose the latter, you may end up having to uninstall the other plugins.  Try it with them all installed first.  Only remove things if you run into further problems.

---

