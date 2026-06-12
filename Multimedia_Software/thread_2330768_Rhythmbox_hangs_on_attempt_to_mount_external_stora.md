---
title: "Rhythmbox hangs on attempt to mount external storage"
date: 2016-07-14
forum: Multimedia Software
---

### Post by bruxillensis on 2016-07-14
Hello,

I have been having trouble with rhythmbox (and any other music player I have installed: clementine, gnome music, etc.) in that it hangs on startup. This happens when I have connected to external server storage, google drive or an nfs file share I setup at home, that is not accessible to rhythmbox (google drive won't allow access, nfs is only available in home network). The issue goes away after a reboot because these file systems are not automounted. I have tried disabling rhythmbox plugins and searching for ways to stop if from searching for removable media to no avail.

Running rhythmbox --debug gives this output:

(rhythmbox:8148): Rhythmbox-WARNING **: Unable to grab media player keys: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SettingsDaemon was not provided by any .service files
(10:58:48) [0x26c9610] [grab_mmkey] rb-mmkeys-plugin.c:227: Error grabbing key
(10:58:48) [0x26c9610] [grab_mmkey] rb-mmkeys-plugin.c:227: Error grabbing key
(10:58:48) [0x26c9610] [grab_mmkey] rb-mmkeys-plugin.c:227: Error grabbing key
(10:58:48) [0x26c9610] [grab_mmkey] rb-mmkeys-plugin.c:227: Error grabbing key
(10:58:48) [0x26c9610] [grab_mmkey] rb-mmkeys-plugin.c:227: Error grabbing key
(10:58:48) [0x26c9610] [name_acquired_cb] rb-mpris-plugin.c:1398: successfully acquired dbus name org.mpris.MediaPlayer2.rhythmbox
(10:58:48) [0x26c9610] [name_acquired_cb] rb-dbus-media-server-plugin.c:2344: acquired dbus name org.gnome.UPnP.MediaServer2.Rhythmbox
(10:58:48) [0x26c9610] [rb_statusbar_sync_status] rb-statusbar.c:297: updating status with: '0 songs', '', 999.000000
(10:58:48) [0x26c9610] [expand_rows_cb] rb-display-page-tree.c:371: expanding 1 rows
(10:58:48) [0x26c9610] [rb_shell_clipboard_entryview_changed_cb] rb-shell-clipboard.c:678: entryview changed
(10:58:48) [0x26c9610] [idle_process_update] rhythmdb-query-model.c:1209: inserting 0 rows
(10:58:48) [0x26c9610] [idle_process_update] rhythmdb-query-model.c:1209: inserting 0 rows
(10:58:48) [0x26c9610] [idle_process_update] rhythmdb-query-model.c:1209: inserting 0 rows
(10:58:48) [0x26c9610] [idle_process_update] rhythmdb-query-model.c:1209: inserting 0 rows
(10:58:48) [0x26c9610] [idle_process_update] rhythmdb-query-model.c:1209: inserting 0 rows
(10:58:48) [0x26c9610] [idle_process_update] rhythmdb-query-model.c:1209: inserting 0 rows
(10:58:48) [0x26c9610] [idle_process_update] rhythmdb-query-model.c:1209: inserting 0 rows
(10:58:48) [0x26c9610] [idle_process_update] rhythmdb-query-model.c:1209: inserting 0 rows
(10:58:48) [0x26c9610] [dump_volume_identifiers] rb-removable-media-manager.c:599: nfs-mount = 192.168.0.155:/
(10:58:48) [0x26c9610] [rb_removable_media_manager_add_volume] rb-removable-media-manager.c:642: Unhandled media
(10:58:48) [0x26c9610] [dump_volume_identifiers] rb-removable-media-manager.c:599: nfs-mount = 192.168.0.155:/
found device path 192.168.0.155:/ for mount /media/bruxillensis/pi-personal
unable to find device 192.168.0.155:/ in udev
finding mount point for /media/bruxillensis/pi-personal
/media/bruxillensis/pi-personal is already a mount point

...(hangs from here)

Thank you for your help!

---

### Post by shantiq on 2016-07-22
Hi Bruxillensis I would suggest you [automount]("https://ubuntuforums.org/showthread.php?t=2267199&p=13236504#post13236504") those volumes ..   surely then problem would be solved

to do in terminal and
 ```
gedit /etc/fstab
```

PS   also read the entire thread for more help

---

### Post by bruxillensis on 2016-07-25
Hi Shantiq,

Thanks for your reply. I have learned a bit more and can clarify my question I think. Rhythmbox attempting to access a dead nfs link (because I have left my house) or media that is not accessible to the program (google drive). I do not think automounting these file systems would work because they are not always available. Is it possible to stop a program from attempting to access this storage or have the OS automatically unmount a dead nfs link?

---

### Post by bruxillensis on 2016-07-25
Hi Shantiq,

Thanks for your reply. I have learned a bit more and can clarify my question I think. Rhythmbox attempting to access a dead nfs link (because I have left my house) or media that is not accessible to the program (google drive). I do not think automounting these file systems would work because they are not always available. Is it possible to stop a program from attempting to access this storage or have the OS automatically unmount a dead nfs link?

---

### Post by shantiq on 2016-07-25
sorry B   had not seen   nfs link

do not know about those;   surely someone will

---

