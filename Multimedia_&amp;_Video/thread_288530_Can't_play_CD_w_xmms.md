---
title: "Can't play CD w/ xmms"
date: 2006-10-30
forum: Multimedia &amp; Video
---

### Post by orsula on 2006-10-30
Hi,
I am fairly new to the community. I recently installed Edgy 6.10. I am trying to use xmms as my main music player. I can easily stream .m3u for instance but can't play a simple CD with xmms. I searched the forums but couldn't find a link for help. When I try to play a location or simply browse to my music files, I can't see the files on the CD. I know it gets mounted when I insert the CD because I get an icon on the desktop that when clicked on , opens soundjuicer which plays the CD. If I try to browse to /media/cdrom or /media/cdrom0 I see nothing there! I think I am missing something (big time..) in how the file system works. Do I need to mount the CD every time? I thought it does it automatically? Also, I thought music CD's do not have to be mounted like other media because they are not file systems per say..

Please help if you can. I would simply like to insert CD and have xmms play it right away.

Thanks  ](*,) 
Gideon

---

### Post by libertyblues on 2006-11-12
I'm having the same problem using Xubuntu Dapper 6.06... If I find anything out I'll get back to you.

---

### Post by glennric on 2006-11-14
Hit Ctrl-P to bring up the options dialog.  Select the "Audio I/O Plugins" tab and then select the "CD Audio Player 1.2.10" input plugin.  Then click configure and see if there is something there that you can do.  As to getting an audio CD to automatically play in XMMS when inserted go to System->Preferences->Removable Drives and Media, and select the multimedia tab.  Then put ```
/usr/bin/xmms --play /media/cdrom
``` in for the Audio CD Disks Command.

---

### Post by RBEmerson on 2008-01-15
Thanks for the starting point on sorting this problem (had it with this distro and with SuSE, too) out!  I tried looking at /cdrom and couldn't find anything but selecting /media/cdrom was all I needed to get xmms playing CD's.  :cool:

---

