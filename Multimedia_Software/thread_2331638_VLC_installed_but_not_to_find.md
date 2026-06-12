---
title: "VLC installed but not to find"
date: 2016-07-24
forum: Multimedia Software
---

### Post by Roland_Msl on 2016-07-24
Just installed VLC.

The system came with the top right message "VLC installed"

In the software center, only the "Remove" button, but not the lounch button.

I tried the search. Search works really great. It discovered a stored web site, about a probiem from FLC with the apple store, even an old Windows installation file was found,
but nothing to start the just installed VLC.

---

### Post by ubfan1 on 2016-07-24
A quick package search gives:
$ apt-file search vlc |fgrep bin
freeplayer: /usr/bin/vlc-fbx
vlc: /usr/bin/qvlc
vlc: /usr/bin/svlc
vlc-nox: /usr/bin/cvlc
vlc-nox: /usr/bin/nvlc
vlc-nox: /usr/bin/rvlc
vlc-nox: /usr/bin/vlc
vlc-nox: /usr/bin/vlc-wrapper


It must be one of those.

---

### Post by Roland_Msl on 2016-07-24
> **ubfan1 said:**
> A quick package search gives:
$ apt-file search vlc |fgrep bin
freeplayer: /usr/bin/vlc-fbx
vlc: /usr/bin/qvlc
vlc: /usr/bin/svlc
vlc-nox: /usr/bin/cvlc
vlc-nox: /usr/bin/nvlc
vlc-nox: /usr/bin/rvlc
vlc-nox: /usr/bin/vlc
vlc-nox: /usr/bin/vlc-wrapper


It must be one of those.

I went wtih the nautilus to /usr/bin and searched for vlc

Nothing.

The installation took several minutes and I watched in gnome system monitor the network activity. Long enough 1,1 MB/sec download - the maximum speed of my ADSL connection - for the 100 MB, which was announced in the software center.

After this, I have seen, that I should use a terminal command.

I installed apt-file.

The command showed the same output.

---

### Post by ubfan1 on 2016-07-24
From a terminal type vlc or from the DASH launcher, type vlc in the search bar to find the VLC media player (click on it).  There might be some plugin required to play yout specific file though.

---

### Post by Roland_Msl on 2016-07-25
> **ubfan1 said:**
> From a terminal type vlc or from the DASH launcher, type vlc in the search bar to find the VLC media player (click on it).  There might be some plugin required to play yout specific file though.

Nothing to find.

But I just discovered in System Monitor -> File Systems 2 new entries

/dev/loop0/  /snap/untu-core/122    68 MB
/dev/loop1/  /snap/vlc/1/                115 MB

---

### Post by yoshii on 2016-07-25
look in /opt/

---

### Post by Roland_Msl on 2016-07-25
> **yoshii said:**
> look in /opt/

/opt/google/chrome

nothing else there

---

### Post by ubfan1 on 2016-07-25
How did you install, which package manager?  If the vlc file is on your disk,you should be able to find it with the locate vlc command.    If the package manager put it somewhere not in your PATH variable, then it wont run from a terminal by typing vlc, but will still run by typing in the full path name.

---

### Post by Roland_Msl on 2016-07-26
I installed with the software center.

I just typed vlc in the terminal, it opened.

Now it's suddenly also to find with the top left search icon.

---

### Post by ubfan1 on 2016-07-26
Good. Under the thread title, in the "thread tools" menu, you can mark this thread as "solved".

---

### Post by Roland_Msl on 2016-07-28
> **ubfan1 said:**
> Good. Under the thread title, in the "thread tools" menu, you can mark this thread as "solved".

Not complete solved. VLC shows videos,
but I installed it to convert videos from my camera to MP4.

I can choose "Convert", but nothing happens.

Seems the installation does now work like expected.

---

### Post by slickymaster on 2016-07-28
*Thread moved to **Multimedia Software**.*

---

### Post by Roland_Msl on 2016-08-04
I tried to remove the VLC and install new, since main functions like converting a video do not work.

But I can not install it,
I can not remove it.

When I click on the button "install", I get the pop up "Are You sure You want to remove VLC".

Here from the system log

Aug  4 12:19:03 founder-Aspire-ES1-331 org.gnome.Software[2854]: (gnome-software:21592): Gs-WARNING **: Failed to create permission org.freedesktop.packagekit.trigger-offline-update: GDBus.Errorrg.freedesktop.PolicyKit1.Error.Failed: Action org.freedesktop.packagekit.trigger-offline-update is not registered
Aug  4 12:19:03 founder-Aspire-ES1-331 /usr/lib/snapd/snapd[2468]: daemon.go:181: DEBUG: uid=1000;@ GET /v2/snaps/ubuntu-core 1.066233ms 200
Aug  4 12:19:17 founder-Aspire-ES1-331 org.gnome.Software[2854]: (gnome-software:21592): Gs-WARNING **: Failed to create permission org.freedesktop.packagekit.trigger-offline-update: GDBus.Errorrg.freedesktop.PolicyKit1.Error.Failed: Action org.freedesktop.packagekit.trigger-offline-update is not registered
Aug  4 12:19:48 founder-Aspire-ES1-331 org.gnome.Software[2854]: (gnome-software:21592): GLib-CRITICAL **: g_strv_contains: assertion 'str != NULL' failed
Aug  4 12:19:48 founder-Aspire-ES1-331 org.gnome.Software[2854]: (gnome-software:21592): Gs-WARNING **: State change on vlc_vlc.desktop from installed to available is not OK
Aug  4 12:19:58 founder-Aspire-ES1-331 org.gnome.Software[2854]: (gnome-software:21592): Gs-WARNING **: State change on vlc from available to removing is not OK
Aug  4 12:19:58 founder-Aspire-ES1-331 /usr/lib/snapd/snapd[2468]: daemon.go:181: DEBUG: uid=1000;@ POST /v2/snaps/vlc 15.133542ms 202
Aug  4 12:19:58 founder-Aspire-ES1-331 /usr/lib/snapd/snapd[2468]: taskrunner.go:238: DEBUG: Running task 21 on Do: Make snap "vlc" unavailable to the system
Aug  4 12:19:58 founder-Aspire-ES1-331 /usr/lib/snapd/snapd[2468]: taskrunner.go:238: DEBUG: Running task 22 on Do: Remove security profile for snap "vlc"
Aug  4 12:19:58 founder-Aspire-ES1-331 /usr/lib/snapd/snapd[2468]: taskrunner.go:238: DEBUG: Running task 23 on Do: Remove data for snap "vlc"
Aug  4 12:19:58 founder-Aspire-ES1-331 /usr/lib/snapd/snapd[2468]: taskrunner.go:238: DEBUG: Running task 24 on Do: Remove snap "vlc" from the system
Aug  4 12:19:58 founder-Aspire-ES1-331 systemd[1]: Unmounting Mount unit for vlc...
Aug  4 12:19:58 founder-Aspire-ES1-331 umount[22595]: umount: /snap/vlc/1: target is busy
Aug  4 12:19:58 founder-Aspire-ES1-331 umount[22595]:         (In some cases useful info about processes that
Aug  4 12:19:58 founder-Aspire-ES1-331 umount[22595]:          use the device is found by lsof(8) or fuser(1).)
Aug  4 12:19:58 founder-Aspire-ES1-331 systemd[1]: snap-vlc-1.mount: Mount process exited, code=exited status=32
Aug  4 12:19:58 founder-Aspire-ES1-331 systemd[1]: Failed unmounting Mount unit for vlc.
Aug  4 12:19:58 founder-Aspire-ES1-331 /usr/lib/snapd/snapd[2468]: task.go:250: DEBUG: 2016-08-04T12:19:58+02:00 ERROR cannot remove snap file "vlc", will retry: [stop snap-vlc-1.mount] failed with exit status 1: Job for snap-vlc-1.mount failed. See "systemctl status snap-vlc-1.mount" and "journalctl -xe" for details.
Aug  4 12:20:01 founder-Aspire-ES1-331 /usr/lib/snapd/snapd[2468]: daemon.go:181: DEBUG: uid=1000;@ GET /v2/snaps/ubuntu-core 1.174873ms 200
Aug  4 12:20:02 founder-Aspire-ES1-331 /usr/lib/snapd/snapd[2468]: api.go:407: DEBUG: use of obsolete "sources" parameter: "/v2/snaps?sources=local"
Aug  4 12:20:02 founder-Aspire-ES1-331 /usr/lib/snapd/snapd[2468]: daemon.go:181: DEBUG: uid=1000;@ GET /v2/snaps?sources=local 2.098685ms 200
Aug  4 12:20:02 founder-Aspire-ES1-331 org.gnome.Software[2854]: (gnome-software:21592): Gs-WARNING **: Failed to create permission org.freedesktop.packagekit.trigger-offline-update: GDBus.Errorrg.freedesktop.PolicyKit1.Error.Failed: Action org.freedesktop.packagekit.trigger-offline-update is not registered
Aug  4 12:20:02 founder-Aspire-ES1-331 org.gnome.Software[2854]: (gnome-software:21592): Gs-WARNING **: failed to get updates: no results to show
Aug  4 12:20:02 founder-Aspire-ES1-331 /usr/lib/snapd/snapd[2468]: api.go:402: DEBUG: use of obsolete "q" parameter: "/v2/snaps?q=vlc"
Aug  4 12:20:02 founder-Aspire-ES1-331 /usr/lib/snapd/snapd[2468]: api.go:483: jumping to "find" to better support legacy request "/v2/snaps?q=vlc"
Aug  4 12:20:02 founder-Aspire-ES1-331 snapd[2468]: 2016/08/04 12:20:02.201172 api.go:483: jumping to "find" to better support legacy request "/v2/snaps?q=vlc"
Aug  4 12:20:02 founder-Aspire-ES1-331 org.gnome.Software[2854]: (gnome-software:21592): GsPlugin-WARNING **: failed to load stock icon calibre: Icon 'calibre' not present in theme (null)
Aug  4 12:20:02 founder-Aspire-ES1-331 org.gnome.Software[2854]: (gnome-software:21592): GsPlugin-WARNING **: failed to load stock icon calibre: Icon 'calibre' not present in theme (null)
Aug  4 12:20:02 founder-Aspire-ES1-331 /usr/lib/snapd/snapd[2468]: daemon.go:181: DEBUG: uid=1000;@ GET /v2/snaps/ubuntu-core 1.056617ms 200
Aug  4 12:20:02 founder-Aspire-ES1-331 org.gnome.Software[2854]: (gnome-software:21592): Gs-WARNING **: Failed to create permission org.freedesktop.packagekit.trigger-offline-update: GDBus.Errorrg.freedesktop.PolicyKit1.Error.Failed: Action org.freedesktop.packagekit.trigger-offline-update is not registered
Aug  4 12:20:02 founder-Aspire-ES1-331 org.gnome.Software[2854]: (gnome-software:21592): GsPlugin-WARNING **: failed to load stock icon calibre: Icon 'calibre' not present in theme (null)
Aug  4 12:20:02 founder-Aspire-ES1-331 org.gnome.Software[2854]: (gnome-software:21592): GsPlugin-WARNING **: failed to load stock icon calibre: Icon 'calibre' not present in theme (null)
Aug  4 12:20:02 founder-Aspire-ES1-331 /usr/lib/snapd/snapd[2468]: daemon.go:181: DEBUG: uid=1000;@ GET /v2/snaps?q=vlc 465.857747ms 200
Aug  4 12:20:02 founder-Aspire-ES1-331 /usr/lib/snapd/snapd[2468]: daemon.go:181: DEBUG: uid=1000;@ GET /v2/snaps/vlc 1.433759ms 200
Aug  4 12:20:02 founder-Aspire-ES1-331 org.gnome.Software[2854]: (gnome-software:21592): Gs-WARNING **: State change on vlc from available to installed is not OK
Aug  4 12:20:07 founder-Aspire-ES1-331 org.gnome.Software[2854]: (gnome-software:21592): Gs-WARNING **: Failed to create permission org.freedesktop.packagekit.trigger-offline-update: GDBus.Errorrg.freedesktop.PolicyKit1.Error.Failed: Action org.freedesktop.packagekit.trigger-offline-update is not registered
Aug  4 12:20:22 founder-Aspire-ES1-331 org.gnome.Software[2854]: message repeated 4 times: [ (gnome-software:21592): Gs-WARNING **: Failed to create permission org.freedesktop.packagekit.trigger-offline-update: GDBus.Errorrg.freedesktop.PolicyKit1.Error.Failed: Action org.freedesktop.packagekit.trigger-offline-update is not registered]
Aug  4 12:21:06 founder-Aspire-ES1-331 dbus[2310]: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service'
Aug  4 12:21:06 founder-Aspire-ES1-331 systemd[1]: Starting Hostname Service...
Aug  4 12:21:06 founder-Aspire-ES1-331 dbus[2310]: [system] Successfully activated service 'org.freedesktop.hostname1'
Aug  4 12:21:06 founder-Aspire-ES1-331 systemd[1]: Started Hostname Service.
Aug  4 12:21:06 founder-Aspire-ES1-331 org.gtk.vfs.Daemon[2854]: ** (process:3525): WARNING **: send_infos_cb: No such interface 'org.gtk.vfs.Enumerator' on object at path /org/gtk/vfs/client/enumerator/2 (g-dbus-error-quark, 19)
Aug  4 12:21:06 founder-Aspire-ES1-331 org.gtk.vfs.Daemon[2854]: ** (process:3525): WARNING **: send_done_cb: No such interface 'org.gtk.vfs.Enumerator' on object at path /org/gtk/vfs/client/enumerator/2 (g-dbus-error-quark, 19)
Aug  4 12:21:30 founder-Aspire-ES1-331 gnome-session[3114]: ** (zeitgeist-datahub:3649): CRITICAL **: string_strip: assertion 'self != NULL' failed
Aug  4 12:21:30 founder-Aspire-ES1-331 gnome-session[3114]: (zeitgeist-datahub:3649): Gtk-CRITICAL **: gtk_recent_info_get_application_info: assertion 'app_name != NULL' failed
Aug  4 12:21:30 founder-Aspire-ES1-331 gnome-session[3114]: ** (zeitgeist-datahub:3649): WARNING **: recent-manager-provider.vala:106: (null) was not registered in RecentInfo item 0xe00cf0
Aug  4 12:21:40 founder-Aspire-ES1-331 org.gnome.Software[2854]: (gnome-software:21592): Gs-WARNING **: Failed to create permission org.freedesktop.packagekit.trigger-offline-update: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: Action org.freedesktop.packagekit.trigger-offline-update is not registered
Aug  4 12:22:12 founder-Aspire-ES1-331 org.gnome.Software[2854]: message repeated 3 times: [ (gnome-software:21592): Gs-WARNING **: Failed to create permission org.freedesktop.packagekit.trigger-offline-update: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: Action org.freedesktop.packagekit.trigger-offline-update is not registered]
Aug  4 12:22:12 founder-Aspire-ES1-331 /usr/lib/snapd/snapd[2468]: api.go:402: DEBUG: use of obsolete "q" parameter: "/v2/snaps?q=vlc"
Aug  4 12:22:12 founder-Aspire-ES1-331 /usr/lib/snapd/snapd[2468]: api.go:483: jumping to "find" to better support legacy request "/v2/snaps?q=vlc"
Aug  4 12:22:12 founder-Aspire-ES1-331 snapd[2468]: 2016/08/04 12:22:12.100170 api.go:483: jumping to "find" to better support legacy request "/v2/snaps?q=vlc"
Aug  4 12:22:12 founder-Aspire-ES1-331 /usr/lib/snapd/snapd[2468]: daemon.go:181: DEBUG: uid=1000;@ GET /v2/snaps?q=vlc 515.169544ms 200
Aug  4 12:22:12 founder-Aspire-ES1-331 /usr/lib/snapd/snapd[2468]: daemon.go:181: DEBUG: uid=1000;@ GET /v2/snaps/vlc 1.211384ms 200
Aug  4 12:22:12 founder-Aspire-ES1-331 org.gnome.Software[2854]: (gnome-software:21592): Gs-WARNING **: State change on vlc from available to installed is not OK
Aug  4 12:22:15 founder-Aspire-ES1-331 /usr/lib/snapd/snapd[2468]: daemon.go:181: DEBUG: uid=1000;@ POST /v2/snaps/vlc 750.113µs 500
Aug  4 12:22:15 founder-Aspire-ES1-331 org.gnome.Software[2854]: (gnome-software:21592): Gs-WARNING **: failed to call gs_plugin_app_install on snappy: snapd returned status code 500: Internal Server Error
Aug  4 12:22:15 founder-Aspire-ES1-331 org.gnome.Software[2854]: (gnome-software:21592): Gs-WARNING **: State change on vlc from available to installed is not OK
Aug  4 12:22:15 founder-Aspire-ES1-331 /usr/lib/snapd/snapd[2468]: daemon.go:181: DEBUG: uid=1000;@ GET /v2/snaps/vlc 1.71023ms 200
Aug  4 12:22:15 founder-Aspire-ES1-331 org.gnome.Software[2854]: (gnome-software:21592): Gs-WARNING **: State change on vlc from available to installed is not OK
Aug  4 12:22:15 founder-Aspire-ES1-331 /usr/lib/snapd/snapd[2468]: api.go:402: DEBUG: use of obsolete "q" parameter: "/v2/snaps?q=vlc"
Aug  4 12:22:15 founder-Aspire-ES1-331 /usr/lib/snapd/snapd[2468]: api.go:483: jumping to "find" to better support legacy request "/v2/snaps?q=vlc"
Aug  4 12:22:15 founder-Aspire-ES1-331 snapd[2468]: 2016/08/04 12:22:15.859987 api.go:483: jumping to "find" to better support legacy request "/v2/snaps?q=vlc"
Aug  4 12:22:16 founder-Aspire-ES1-331 /usr/lib/snapd/snapd[2468]: daemon.go:181: DEBUG: uid=1000;@ GET /v2/snaps?q=vlc 197.948313ms 200
Aug  4 12:22:16 founder-Aspire-ES1-331 /usr/lib/snapd/snapd[2468]: daemon.go:181: DEBUG: uid=1000;@ GET /v2/snaps/vlc 1.248745ms 200
Aug  4 12:22:16 founder-Aspire-ES1-331 org.gnome.Software[2854]: (gnome-software:21592): Gs-WARNING **: State change on vlc from available to installed is not OK
Aug  4 12:22:17 founder-Aspire-ES1-331 /usr/lib/snapd/snapd[2468]: daemon.go:181: DEBUG: uid=1000;@ POST /v2/snaps/vlc 1.266145ms 500
Aug  4 12:22:17 founder-Aspire-ES1-331 org.gnome.Software[2854]: (gnome-software:21592): Gs-WARNING **: failed to call gs_plugin_app_install on snappy: snapd returned status code 500: Internal Server Error
Aug  4 12:22:17 founder-Aspire-ES1-331 org.gnome.Software[2854]: (gnome-software:21592): Gs-WARNING **: State change on vlc from available to installed is not OK
Aug  4 12:22:17 founder-Aspire-ES1-331 /usr/lib/snapd/snapd[2468]: daemon.go:181: DEBUG: uid=1000;@ GET /v2/snaps/vlc 1.20311ms 200
Aug  4 12:22:17 founder-Aspire-ES1-331 org.gnome.Software[2854]: (gnome-software:21592): Gs-WARNING **: State change on vlc from available to installed is not OK
Aug  4 12:22:17 founder-Aspire-ES1-331 /usr/lib/snapd/snapd[2468]: api.go:402: DEBUG: use of obsolete "q" parameter: "/v2/snaps?q=vlc"
Aug  4 12:22:17 founder-Aspire-ES1-331 /usr/lib/snapd/snapd[2468]: api.go:483: jumping to "find" to better support legacy request "/v2/snaps?q=vlc"
Aug  4 12:22:17 founder-Aspire-ES1-331 snapd[2468]: 2016/08/04 12:22:17.982307 api.go:483: jumping to "find" to better support legacy request "/v2/snaps?q=vlc"
Aug  4 12:22:18 founder-Aspire-ES1-331 /usr/lib/snapd/snapd[2468]: daemon.go:181: DEBUG: uid=1000;@ GET /v2/snaps?q=vlc 104.1378ms 200
Aug  4 12:22:18 founder-Aspire-ES1-331 /usr/lib/snapd/snapd[2468]: daemon.go:181: DEBUG: uid=1000;@ GET /v2/snaps/vlc 1.258996ms 200
Aug  4 12:22:18 founder-Aspire-ES1-331 org.gnome.Software[2854]: (gnome-software:21592): Gs-WARNING **: State change on vlc from available to installed is not OK
Aug  4 12:22:19 founder-Aspire-ES1-331 /usr/lib/snapd/snapd[2468]: daemon.go:181: DEBUG: uid=1000;@ POST /v2/snaps/vlc 1.066077ms 500
Aug  4 12:22:19 founder-Aspire-ES1-331 org.gnome.Software[2854]: (gnome-software:21592): Gs-WARNING **: failed to call gs_plugin_app_install on snappy: snapd returned status code 500: Internal Server Error
Aug  4 12:22:19 founder-Aspire-ES1-331 org.gnome.Software[2854]: (gnome-software:21592): Gs-WARNING **: State change on vlc from available to installed is not OK
Aug  4 12:22:19 founder-Aspire-ES1-331 /usr/lib/snapd/snapd[2468]: daemon.go:181: DEBUG: uid=1000;@ GET /v2/snaps/vlc 1.180673ms 200
Aug  4 12:22:19 founder-Aspire-ES1-331 org.gnome.Software[2854]: (gnome-software:21592): Gs-WARNING **: State change on vlc from available to installed is not OK
Aug  4 12:22:19 founder-Aspire-ES1-331 /usr/lib/snapd/snapd[2468]: api.go:402: DEBUG: use of obsolete "q" parameter: "/v2/snaps?q=vlc"
Aug  4 12:22:19 founder-Aspire-ES1-331 snapd[2468]: 2016/08/04 12:22:19.131709 api.go:483: jumping to "find" to better support legacy request "/v2/snaps?q=vlc"
Aug  4 12:22:19 founder-Aspire-ES1-331 /usr/lib/snapd/snapd[2468]: api.go:483: jumping to "find" to better support legacy request "/v2/snaps?q=vlc"
Aug  4 12:22:19 founder-Aspire-ES1-331 /usr/lib/snapd/snapd[2468]: daemon.go:181: DEBUG: uid=1000;@ GET /v2/snaps?q=vlc 87.037492ms 200
Aug  4 12:22:19 founder-Aspire-ES1-331 /usr/lib/snapd/snapd[2468]: daemon.go:181: DEBUG: uid=1000;@ GET /v2/snaps/vlc 1.307982ms 200
Aug  4 12:22:19 founder-Aspire-ES1-331 org.gnome.Software[2854]: (gnome-software:21592): Gs-WARNING **: State change on vlc from available to installed is not OK
Aug  4 12:22:20 founder-Aspire-ES1-331 /usr/lib/snapd/snapd[2468]: daemon.go:181: DEBUG: uid=1000;@ POST /v2/snaps/vlc 868.984µs 500
Aug  4 12:22:20 founder-Aspire-ES1-331 org.gnome.Software[2854]: (gnome-software:21592): Gs-WARNING **: failed to call gs_plugin_app_install on snappy: snapd returned status code 500: Internal Server Error
Aug  4 12:22:20 founder-Aspire-ES1-331 org.gnome.Software[2854]: (gnome-software:21592): Gs-WARNING **: State change on vlc from available to installed is not OK
Aug  4 12:22:20 founder-Aspire-ES1-331 /usr/lib/snapd/snapd[2468]: daemon.go:181: DEBUG: uid=1000;@ GET /v2/snaps/vlc 1.165949ms 200
Aug  4 12:22:20 founder-Aspire-ES1-331 org.gnome.Software[2854]: (gnome-software:21592): Gs-WARNING **: State change on vlc from available to installed is not OK
Aug  4 12:22:20 founder-Aspire-ES1-331 /usr/lib/snapd/snapd[2468]: api.go:402: DEBUG: use of obsolete "q" parameter: "/v2/snaps?q=vlc"
Aug  4 12:22:20 founder-Aspire-ES1-331 /usr/lib/snapd/snapd[2468]: api.go:483: jumping to "find" to better support legacy request "/v2/snaps?q=vlc"
Aug  4 12:22:20 founder-Aspire-ES1-331 snapd[2468]: 2016/08/04 12:22:20.305685 api.go:483: jumping to "find" to better support legacy request "/v2/snaps?q=vlc"
Aug  4 12:22:20 founder-Aspire-ES1-331 /usr/lib/snapd/snapd[2468]: daemon.go:181: DEBUG: uid=1000;@ GET /v2/snaps?q=vlc 356.609129ms 200
Aug  4 12:22:20 founder-Aspire-ES1-331 /usr/lib/snapd/snapd[2468]: daemon.go:181: DEBUG: uid=1000;@ GET /v2/snaps/vlc 1.802416ms 200
Aug  4 12:22:20 founder-Aspire-ES1-331 org.gnome.Software[2854]: (gnome-software:21592): Gs-WARNING **: State change on vlc from available to installed is not OK
Aug  4 12:22:21 founder-Aspire-ES1-331 /usr/lib/snapd/snapd[2468]: daemon.go:181: DEBUG: uid=1000;@ POST /v2/snaps/vlc 1.027367ms 500
Aug  4 12:22:21 founder-Aspire-ES1-331 org.gnome.Software[2854]: (gnome-software:21592): Gs-WARNING **: failed to call gs_plugin_app_install on snappy: snapd returned status code 500: Internal Server Error
Aug  4 12:22:21 founder-Aspire-ES1-331 org.gnome.Software[2854]: (gnome-software:21592): Gs-WARNING **: State change on vlc from available to installed is not OK
Aug  4 12:22:21 founder-Aspire-ES1-331 /usr/lib/snapd/snapd[2468]: daemon.go:181: DEBUG: uid=1000;@ GET /v2/snaps/vlc 1.362417ms 200
Aug  4 12:22:21 founder-Aspire-ES1-331 org.gnome.Software[2854]: (gnome-software:21592): Gs-WARNING **: State change on vlc from available to installed is not OK
Aug  4 12:22:21 founder-Aspire-ES1-331 /usr/lib/snapd/snapd[2468]: api.go:402: DEBUG: use of obsolete "q" parameter: "/v2/snaps?q=vlc"
Aug  4 12:22:21 founder-Aspire-ES1-331 snapd[2468]: 2016/08/04 12:22:21.759472 api.go:483: jumping to "find" to better support legacy request "/v2/snaps?q=vlc"
Aug  4 12:22:21 founder-Aspire-ES1-331 /usr/lib/snapd/snapd[2468]: api.go:483: jumping to "find" to better support legacy request "/v2/snaps?q=vlc"
Aug  4 12:22:21 founder-Aspire-ES1-331 /usr/lib/snapd/snapd[2468]: daemon.go:181: DEBUG: uid=1000;@ GET /v2/snaps?q=vlc 133.025866ms 200
Aug  4 12:22:21 founder-Aspire-ES1-331 /usr/lib/snapd/snapd[2468]: daemon.go:181: DEBUG: uid=1000;@ GET /v2/snaps/vlc 1.469502ms 200
Aug  4 12:22:21 founder-Aspire-ES1-331 org.gnome.Software[2854]: (gnome-software:21592): Gs-WARNING **: State change on vlc from available to installed is not OK
Aug  4 12:22:22 founder-Aspire-ES1-331 /usr/lib/snapd/snapd[2468]: daemon.go:181: DEBUG: uid=1000;@ POST /v2/snaps/vlc 886.809µs 500
Aug  4 12:22:22 founder-Aspire-ES1-331 org.gnome.Software[2854]: (gnome-software:21592): Gs-WARNING **: failed to call gs_plugin_app_install on snappy: snapd returned status code 500: Internal Server Error
Aug  4 12:22:22 founder-Aspire-ES1-331 org.gnome.Software[2854]: (gnome-software:21592): Gs-WARNING **: State change on vlc from available to installed is not OK
Aug  4 12:22:22 founder-Aspire-ES1-331 /usr/lib/snapd/snapd[2468]: daemon.go:181: DEBUG: uid=1000;@ GET /v2/snaps/vlc 1.229747ms 200
Aug  4 12:22:22 founder-Aspire-ES1-331 org.gnome.Software[2854]: (gnome-software:21592): Gs-WARNING **: State change on vlc from available to installed is not OK
Aug  4 12:22:22 founder-Aspire-ES1-331 /usr/lib/snapd/snapd[2468]: api.go:402: DEBUG: use of obsolete "q" parameter: "/v2/snaps?q=vlc"
Aug  4 12:22:22 founder-Aspire-ES1-331 /usr/lib/snapd/snapd[2468]: api.go:483: jumping to "find" to better support legacy request "/v2/snaps?q=vlc"
Aug  4 12:22:22 founder-Aspire-ES1-331 snapd[2468]: 2016/08/04 12:22:22.921200 api.go:483: jumping to "find" to better support legacy request "/v2/snaps?q=vlc"
Aug  4 12:22:23 founder-Aspire-ES1-331 /usr/lib/snapd/snapd[2468]: daemon.go:181: DEBUG: uid=1000;@ GET /v2/snaps?q=vlc 165.920716ms 200
Aug  4 12:22:23 founder-Aspire-ES1-331 /usr/lib/snapd/snapd[2468]: daemon.go:181: DEBUG: uid=1000;@ GET /v2/snaps/vlc 1.254434ms 200
Aug  4 12:22:23 founder-Aspire-ES1-331 org.gnome.Software[2854]: (gnome-software:21592): Gs-WARNING **: State change on vlc from available to installed is not OK
Aug  4 12:24:57 founder-Aspire-ES1-331 gnome-session[3114]: ** (zeitgeist-datahub:3649): CRITICAL **: string_strip: assertion 'self != NULL' failed
Aug  4 12:24:57 founder-Aspire-ES1-331 gnome-session[3114]: (zeitgeist-datahub:3649): Gtk-CRITICAL **: gtk_recent_info_get_application_info: assertion 'app_name != NULL' failed
Aug  4 12:24:57 founder-Aspire-ES1-331 gnome-session[3114]: ** (zeitgeist-datahub:3649): WARNING **: recent-manager-provider.vala:106: (null) was not registered in RecentInfo item 0xe00d60
Aug  4 12:24:58 founder-Aspire-ES1-331 /usr/lib/snapd/snapd[2468]: taskrunner.go:238: DEBUG: Running task 24 on Doing: Remove snap "vlc" from the system
Aug  4 12:24:58 founder-Aspire-ES1-331 systemd[1]: Unmounting Mount unit for vlc...
Aug  4 12:24:58 founder-Aspire-ES1-331 umount[22750]: umount: /snap/vlc/1: target is busy
Aug  4 12:24:58 founder-Aspire-ES1-331 umount[22750]:         (In some cases useful info about processes that
Aug  4 12:24:58 founder-Aspire-ES1-331 umount[22750]:          use the device is found by lsof(8) or fuser(1).)
Aug  4 12:24:58 founder-Aspire-ES1-331 systemd[1]: snap-vlc-1.mount: Mount process exited, code=exited status=32
Aug  4 12:24:58 founder-Aspire-ES1-331 systemd[1]: Failed unmounting Mount unit for vlc.
Aug  4 12:24:58 founder-Aspire-ES1-331 /usr/lib/snapd/snapd[2468]: task.go:250: DEBUG: 2016-08-04T12:24:58+02:00 ERROR cannot remove snap file "vlc", will retry: [stop snap-vlc-1.mount] failed with exit status 1: Job for snap-vlc-1.mount failed. See "systemctl status snap-vlc-1.mount" and "journalctl -xe" for details.
Aug  4 12:25:02 founder-Aspire-ES1-331 AptDaemon: INFO: Quitting due to inactivity
Aug  4 12:25:02 founder-Aspire-ES1-331 AptDaemon: INFO: Quitting was requested
Aug  4 12:25:02 founder-Aspire-ES1-331 org.debian.apt[2310]: 12:25:02 AptDaemon [INFO]: Quitting due to inactivity
Aug  4 12:25:02 founder-Aspire-ES1-331 org.debian.apt[2310]: 12:25:02 AptDaemon [INFO]: Quitting was requested
Aug  4 12:26:37 founder-Aspire-ES1-331 org.gnome.zeitgeist.SimpleIndexer[2854]: ** (zeitgeist-fts:3667): WARNING **: Unable to get info on application://nautilus-autostart.desktop
Aug  4 12:26:38 founder-Aspire-ES1-331 gnome-session[3114]: (eog:22769): EOG-WARNING **: Failed to open file '/home/founder/.cache/thumbnails/normal/8e7076cfdb287264112883237ff1c411.png': No such file or directory
Aug  4 12:26:42 founder-Aspire-ES1-331 gnome-session[3114]: ** (zeitgeist-datahub:3649): CRITICAL **: string_strip: assertion 'self != NULL' failed
Aug  4 12:26:42 founder-Aspire-ES1-331 gnome-session[3114]: (zeitgeist-datahub:3649): Gtk-CRITICAL **: gtk_recent_info_get_application_info: assertion 'app_name != NULL' failed
Aug  4 12:26:42 founder-Aspire-ES1-331 gnome-session[3114]: ** (zeitgeist-datahub:3649): WARNING **: recent-manager-provider.vala:106: (null) was not registered in RecentInfo item 0xd57e50
Aug  4 12:28:22 founder-Aspire-ES1-331 org.gnome.Software[2854]: (gnome-software:21592): Gs-WARNING **: Failed to create permission org.freedesktop.packagekit.trigger-offline-update: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: Action org.freedesktop.packagekit.trigger-offline-update is not registered
Aug  4 12:28:24 founder-Aspire-ES1-331 org.gnome.Software[2854]: (gnome-software:21592): Gs-WARNING **: Failed to create permission org.freedesktop.packagekit.trigger-offline-update: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: Action org.freedesktop.packagekit.trigger-offline-update is not registered
Aug  4 12:28:38 founder-Aspire-ES1-331 org.gnome.Software[2854]: (gnome-software:21592): Gs-WARNING **: State change on vlc from available to removing is not OK
Aug  4 12:28:38 founder-Aspire-ES1-331 /usr/lib/snapd/snapd[2468]: daemon.go:181: DEBUG: uid=1000;@ POST /v2/snaps/vlc 487.392µs 500
Aug  4 12:28:38 founder-Aspire-ES1-331 org.gnome.Software[2854]: (gnome-software:21592): Gs-WARNING **: State change on vlc from available to installed is not OK
Aug  4 12:28:38 founder-Aspire-ES1-331 org.gnome.Software[2854]: (gnome-software:21592): Gs-WARNING **: failed to call gs_plugin_app_remove on snappy: snapd returned status code 500: Internal Server Error
Aug  4 12:28:38 founder-Aspire-ES1-331 /usr/lib/snapd/snapd[2468]: daemon.go:181: DEBUG: uid=1000;@ GET /v2/snaps/vlc 1.306991ms 200
Aug  4 12:28:38 founder-Aspire-ES1-331 org.gnome.Software[2854]: (gnome-software:21592): Gs-WARNING **: State change on vlc from available to installed is not OK
Aug  4 12:28:43 founder-Aspire-ES1-331 org.gnome.Software[2854]: (gnome-software:21592): Gs-WARNING **: Failed to create permission org.freedesktop.packagekit.trigger-offline-update: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: Action org.freedesktop.packagekit.trigger-offline-update is not registered
Aug  4 12:29:22 founder-Aspire-ES1-331 org.gnome.Software[2854]: message repeated 3 times: [ (gnome-software:21592): Gs-WARNING **: Failed to create permission org.freedesktop.packagekit.trigger-offline-update: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: Action org.freedesktop.packagekit.trigger-offline-update is not registered]
Aug  4 12:29:22 founder-Aspire-ES1-331 /usr/lib/snapd/snapd[2468]: api.go:402: DEBUG: use of obsolete "q" parameter: "/v2/snaps?q=vlc"
Aug  4 12:29:22 founder-Aspire-ES1-331 snapd[2468]: 2016/08/04 12:29:22.029378 api.go:483: jumping to "find" to better support legacy request "/v2/snaps?q=vlc"
Aug  4 12:29:22 founder-Aspire-ES1-331 /usr/lib/snapd/snapd[2468]: api.go:483: jumping to "find" to better support legacy request "/v2/snaps?q=vlc"
Aug  4 12:29:22 founder-Aspire-ES1-331 /usr/lib/snapd/snapd[2468]: daemon.go:181: DEBUG: uid=1000;@ GET /v2/snaps?q=vlc 364.273557ms 200
Aug  4 12:29:22 founder-Aspire-ES1-331 /usr/lib/snapd/snapd[2468]: daemon.go:181: DEBUG: uid=1000;@ GET /v2/snaps/vlc 2.594266ms 200
Aug  4 12:29:22 founder-Aspire-ES1-331 org.gnome.Software[2854]: (gnome-software:21592): Gs-WARNING **: State change on vlc from available to installed is not OK
Aug  4 12:29:30 founder-Aspire-ES1-331 dbus[2310]: [system] Activating service name='org.debian.apt' (using servicehelper)
Aug  4 12:29:30 founder-Aspire-ES1-331 AptDaemon: INFO: Initializing daemon
Aug  4 12:29:30 founder-Aspire-ES1-331 org.debian.apt[2310]: 12:29:30 AptDaemon [INFO]: Initializing daemon
Aug  4 12:29:30 founder-Aspire-ES1-331 dbus[2310]: [system] Successfully activated service 'org.debian.apt'
Aug  4 12:29:31 founder-Aspire-ES1-331 AptDaemon.PackageKit: INFO: Initializing PackageKit compat layer
Aug  4 12:29:31 founder-Aspire-ES1-331 org.debian.apt[2310]: /usr/lib/python3/dist-packages/aptdaemon/worker/pkworker.py:35: PyGIWarning: PackageKitGlib was imported without specifying a version first. Use gi.require_version('PackageKitGlib', '1.0') before import to ensure that the right version gets loaded.
Aug  4 12:29:31 founder-Aspire-ES1-331 org.debian.apt[2310]:   from gi.repository import PackageKitGlib as pk
Aug  4 12:29:31 founder-Aspire-ES1-331 org.debian.apt[2310]: 12:29:31 AptDaemon.PackageKit [INFO]: Initializing PackageKit compat layer
Aug  4 12:29:31 founder-Aspire-ES1-331 AptDaemon: INFO: InstallPackages() was called: dbus.Array([dbus.String('vlc')], signature=dbus.Signature('s'))
Aug  4 12:29:31 founder-Aspire-ES1-331 org.debian.apt[2310]: 12:29:31 AptDaemon [INFO]: InstallPackages() was called: dbus.Array([dbus.String('vlc')], signature=dbus.Signature('s'))
Aug  4 12:29:31 founder-Aspire-ES1-331 AptDaemon.Trans: INFO: Queuing transaction /org/debian/apt/transaction/356e37f0c08841a3bc437a0da76114ad
Aug  4 12:29:31 founder-Aspire-ES1-331 org.debian.apt[2310]: 12:29:31 AptDaemon.Trans [INFO]: Queuing transaction /org/debian/apt/transaction/356e37f0c08841a3bc437a0da76114ad
Aug  4 12:29:31 founder-Aspire-ES1-331 AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/356e37f0c08841a3bc437a0da76114ad
Aug  4 12:29:31 founder-Aspire-ES1-331 org.debian.apt[2310]: 12:29:31 AptDaemon.Worker [INFO]: Simulating trans: /org/debian/apt/transaction/356e37f0c08841a3bc437a0da76114ad
Aug  4 12:29:32 founder-Aspire-ES1-331 AptDaemon.Worker: INFO: Committing packages: dbus.Array([dbus.String('vlc')], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s'))
Aug  4 12:29:32 founder-Aspire-ES1-331 org.debian.apt[2310]: 12:29:32 AptDaemon.Worker [INFO]: Committing packages: dbus.Array([dbus.String('vlc')], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s'))
Aug  4 12:29:35 founder-Aspire-ES1-331 gnome-session[3114]: Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.
Aug  4 12:29:41 founder-Aspire-ES1-331 AptDaemon.Worker: INFO: Processing transaction /org/debian/apt/transaction/356e37f0c08841a3bc437a0da76114ad
Aug  4 12:29:41 founder-Aspire-ES1-331 org.debian.apt[2310]: 12:29:41 AptDaemon.Worker [INFO]: Processing transaction /org/debian/apt/transaction/356e37f0c08841a3bc437a0da76114ad
Aug  4 12:29:58 founder-Aspire-ES1-331 /usr/lib/snapd/snapd[2468]: taskrunner.go:238: DEBUG: Running task 24 on Doing: Remove snap "vlc" from the system
Aug  4 12:29:58 founder-Aspire-ES1-331 systemd[1]: Unmounting Mount unit for vlc...
Aug  4 12:29:58 founder-Aspire-ES1-331 umount[23052]: umount: /snap/vlc/1: target is busy
Aug  4 12:29:58 founder-Aspire-ES1-331 umount[23052]:         (In some cases useful info about processes that
Aug  4 12:29:58 founder-Aspire-ES1-331 umount[23052]:          use the device is found by lsof(8) or fuser(1).)
Aug  4 12:29:58 founder-Aspire-ES1-331 systemd[1]: snap-vlc-1.mount: Mount process exited, code=exited status=32
Aug  4 12:29:58 founder-Aspire-ES1-331 systemd[1]: Failed unmounting Mount unit for vlc.
Aug  4 12:29:58 founder-Aspire-ES1-331 /usr/lib/snapd/snapd[2468]: task.go:250: DEBUG: 2016-08-04T12:29:58+02:00 ERROR cannot remove snap file "vlc", will retry: [stop snap-vlc-1.mount] failed with exit status 1: Job for snap-vlc-1.mount failed. See "systemctl status snap-vlc-1.mount" and "journalctl -xe" for details.
Aug  4 12:30:03 founder-Aspire-ES1-331 org.gnome.Software[2854]: (gnome-software:21592): As-WARNING **: failed to rescan: Failed to parse /usr/share/applications/vlc.desktop file: cannot process file of type application/x-desktop
Aug  4 12:30:04 founder-Aspire-ES1-331 org.gnome.Software[2854]: (gnome-software:21592): As-WARNING **: failed to rescan: Failed to parse /usr/share/applications/bamf-2.index file: cannot process file of type text/plain
Aug  4 12:30:06 founder-Aspire-ES1-331 /usr/lib/snapd/snapd[2468]: daemon.go:181: DEBUG: uid=1000;@ GET /v2/snaps/ubuntu-core 955.307µs 200
Aug  4 12:30:07 founder-Aspire-ES1-331 /usr/lib/snapd/snapd[2468]: api.go:407: DEBUG: use of obsolete "sources" parameter: "/v2/snaps?sources=local"
Aug  4 12:30:07 founder-Aspire-ES1-331 /usr/lib/snapd/snapd[2468]: daemon.go:181: DEBUG: uid=1000;@ GET /v2/snaps?sources=local 2.238811ms 200
Aug  4 12:30:07 founder-Aspire-ES1-331 org.gnome.Software[2854]: (gnome-software:21592): Gs-WARNING **: Failed to create permission org.freedesktop.packagekit.trigger-offline-update: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: Action org.freedesktop.packagekit.trigger-offline-update is not registered
Aug  4 12:30:07 founder-Aspire-ES1-331 org.gnome.Software[2854]: (gnome-software:21592): Gs-WARNING **: failed to get updates: no results to show
Aug  4 12:30:07 founder-Aspire-ES1-331 /usr/lib/snapd/snapd[2468]: api.go:402: DEBUG: use of obsolete "q" parameter: "/v2/snaps?q=vlc"
Aug  4 12:30:07 founder-Aspire-ES1-331 /usr/lib/snapd/snapd[2468]: api.go:483: jumping to "find" to better support legacy request "/v2/snaps?q=vlc"
Aug  4 12:30:07 founder-Aspire-ES1-331 snapd[2468]: 2016/08/04 12:30:07.196053 api.go:483: jumping to "find" to better support legacy request "/v2/snaps?q=vlc"
Aug  4 12:30:07 founder-Aspire-ES1-331 org.gnome.Software[2854]: (gnome-software:21592): GsPlugin-WARNING **: failed to load stock icon calibre: Icon 'calibre' not present in theme (null)
Aug  4 12:30:07 founder-Aspire-ES1-331 org.gnome.Software[2854]: (gnome-software:21592): GsPlugin-WARNING **: failed to load stock icon calibre: Icon 'calibre' not present in theme (null)
Aug  4 12:30:07 founder-Aspire-ES1-331 /usr/lib/snapd/snapd[2468]: daemon.go:181: DEBUG: uid=1000;@ GET /v2/snaps/ubuntu-core 1.133438ms 200
Aug  4 12:30:07 founder-Aspire-ES1-331 org.gnome.Software[2854]: (gnome-software:21592): Gs-WARNING **: Failed to create permission org.freedesktop.packagekit.trigger-offline-update: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: Action org.freedesktop.packagekit.trigger-offline-update is not registered
Aug  4 12:30:07 founder-Aspire-ES1-331 org.gnome.Software[2854]: (gnome-software:21592): GsPlugin-WARNING **: failed to load stock icon calibre: Icon 'calibre' not present in theme (null)
Aug  4 12:30:07 founder-Aspire-ES1-331 org.gnome.Software[2854]: (gnome-software:21592): GsPlugin-WARNING **: failed to load stock icon calibre: Icon 'calibre' not present in theme (null)
Aug  4 12:30:07 founder-Aspire-ES1-331 /usr/lib/snapd/snapd[2468]: daemon.go:181: DEBUG: uid=1000;@ GET /v2/snaps?q=vlc 487.106115ms 200
Aug  4 12:30:07 founder-Aspire-ES1-331 /usr/lib/snapd/snapd[2468]: daemon.go:181: DEBUG: uid=1000;@ GET /v2/snaps/vlc 1.765008ms 200
Aug  4 12:30:07 founder-Aspire-ES1-331 org.gnome.Software[2854]: (gnome-software:21592): Gs-WARNING **: State change on vlc from available to installed is not OK
Aug  4 12:30:14 founder-Aspire-ES1-331 AptDaemon.Worker: INFO: Finished transaction /org/debian/apt/transaction/356e37f0c08841a3bc437a0da76114ad
Aug  4 12:30:14 founder-Aspire-ES1-331 org.debian.apt[2310]: /usr/lib/python3/dist-packages/aptdaemon/progress.py:491: Warning: Source ID 40 was not found when attempting to remove it
Aug  4 12:30:14 founder-Aspire-ES1-331 org.debian.apt[2310]:   GLib.source_remove(id)
Aug  4 12:30:14 founder-Aspire-ES1-331 org.debian.apt[2310]: /usr/lib/python3/dist-packages/aptdaemon/progress.py:491: Warning: Source ID 41 was not found when attempting to remove it
Aug  4 12:30:14 founder-Aspire-ES1-331 org.debian.apt[2310]:   GLib.source_remove(id)
Aug  4 12:30:14 founder-Aspire-ES1-331 org.debian.apt[2310]: 12:30:14 AptDaemon.Worker [INFO]: Finished transaction /org/debian/apt/transaction/356e37f0c08841a3bc437a0da76114ad
Aug  4 12:30:14 founder-Aspire-ES1-331 /usr/lib/snapd/snapd[2468]: api.go:402: DEBUG: use of obsolete "q" parameter: "/v2/snaps?q=vlc"
Aug  4 12:30:14 founder-Aspire-ES1-331 /usr/lib/snapd/snapd[2468]: api.go:483: jumping to "find" to better support legacy request "/v2/snaps?q=vlc"
Aug  4 12:30:14 founder-Aspire-ES1-331 snapd[2468]: 2016/08/04 12:30:14.250909 api.go:483: jumping to "find" to better support legacy request "/v2/snaps?q=vlc"
Aug  4 12:30:14 founder-Aspire-ES1-331 /usr/lib/snapd/snapd[2468]: daemon.go:181: DEBUG: uid=1000;@ GET /v2/snaps?q=vlc 453.711084ms 200
Aug  4 12:30:14 founder-Aspire-ES1-331 /usr/lib/snapd/snapd[2468]: daemon.go:181: DEBUG: uid=1000;@ GET /v2/snaps/vlc 1.260363ms 200
Aug  4 12:30:14 founder-Aspire-ES1-331 org.gnome.Software[2854]: (gnome-software:21592): Gs-WARNING **: State change on vlc from available to installed is not OK

---

### Post by mc4man on 2016-08-04
you installed the snap package version of vlc which may not function fully. If you look at attached screen you'll see "vlc" (snap) & "Vlc media player" (.deb)
So I'd get rid of the snap one - 
```
sudo snap remove vlc
```

If that works then ck. and or install the normal vlc - 
```
sudo apt install vlc
```

---

### Post by Roland_Msl on 2016-08-04
> **mc4man said:**
> you installed the snap package version of vlc which may not function fully. If you look at attached screen you'll see "vlc" (snap) & "Vlc media player" (.deb)
So I'd get rid of the snap one - 
```
sudo snap remove vlc
```

If that works then ck. and or install the normal vlc - 
```
sudo apt install vlc
```

Thanks,

just after the first command, it was possible to lounch VLC direct from the software center.

Just converting a video from *.MOV to *.MP4

There is now also a VLC icon with a menu in the top right task bar.
The icon was also bevore, but the drop down menu was empty, only a black strip down.

---

