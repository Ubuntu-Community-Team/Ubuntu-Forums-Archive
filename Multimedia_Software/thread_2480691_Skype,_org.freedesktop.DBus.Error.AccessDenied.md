---
title: "Skype, org.freedesktop.DBus.Error.AccessDenied"
date: 2022-11-06
forum: Multimedia Software
---

### Post by buddhabas2 on 2022-11-06
Hi all!
what about these errors?
I'm on Ubuntu 22.10 and last Skype version.
Thanks so much!


```
xxx@xxx-HP-Pavilion-Sleekbook-15:~$ skype
+ [ -f /home/xxx/snap/skype/common/.config/skypeforlinux/settings.json ]
+ export SKYPE_LOGS=/home/xxx/snap/skype/234/logs
+ [ ! -d /home/xxx/snap/skype/234/logs ]
+ exec /snap/skype/234/usr/share/skypeforlinux/skypeforlinux
[1106/204429.535342:ERROR:aria_reporter.cc(105)] expecting aria url scheme

(skypeforlinux:6742): Gtk-WARNING **: 20:44:30.733: Theme parsing error: gtk.css:1422:23: 'font-feature-settings' is not a valid property name

(skypeforlinux:6742): Gtk-WARNING **: 20:44:30.745: Theme parsing error: gtk.css:3308:25: 'font-feature-settings' is not a valid property name

(skypeforlinux:6742): Gtk-WARNING **: 20:44:30.750: Theme parsing error: gtk.css:3770:23: 'font-feature-settings' is not a valid property name
WARNING: Kernel has no file descriptor comparison support: Operation not permitted
[6742:1106/204433.016046:ERROR:object_proxy.cc(623)] Failed to call method: org.freedesktop.login1.Manager.Inhibit: object_path= /org/freedesktop/login1: org.freedesktop.DBus.Error.AccessDenied: An AppArmor policy prevents this sender from sending this message to this recipient; type="method_call", sender=":1.157" (uid=1000 pid=6742 comm="/snap/skype/234/usr/share/skypeforlinux/skypeforli" label="snap.skype.skype (enforce)") interface="org.freedesktop.login1.Manager" member="Inhibit" error name="(unset)" requested_reply="0" destination="org.freedesktop.login1" (uid=0 pid=504 comm="/lib/systemd/systemd-logind" label="unconfined")
[6742:1106/204433.027574:ERROR:object_proxy.cc(623)] Failed to call method: org.freedesktop.login1.Manager.Inhibit: object_path= /org/freedesktop/login1: org.freedesktop.DBus.Error.AccessDenied: An AppArmor policy prevents this sender from sending this message to this recipient; type="method_call", sender=":1.157" (uid=1000 pid=6742 comm="/snap/skype/234/usr/share/skypeforlinux/skypeforli" label="snap.skype.skype (enforce)") interface="org.freedesktop.login1.Manager" member="Inhibit" error name="(unset)" requested_reply="0" destination="org.freedesktop.login1" (uid=0 pid=504 comm="/lib/systemd/systemd-logind" label="unconfined")
[6742:1106/204439.029282:ERROR:object_proxy.cc(623)] Failed to call method: org.freedesktop.ScreenSaver.GetActive: object_path= /org/freedesktop/ScreenSaver: org.freedesktop.DBus.Error.NotSupported: This method is not implemented
[6742:1106/204439.034471:ERROR:object_proxy.cc(623)] Failed to call method: org.gnome.ScreenSaver.GetActive: object_path= /: org.freedesktop.DBus.Error.AccessDenied: An AppArmor policy prevents this sender from sending this message to this recipient; type="method_call", sender=":1.179" (uid=1000 pid=6742 comm="/snap/skype/234/usr/share/skypeforlinux/skypeforli" label="snap.skype.skype (enforce)") interface="org.gnome.ScreenSaver" member="GetActive" error name="(unset)" requested_reply="0" destination="org.gnome.ScreenSaver" (uid=1000 pid=2221 comm="/usr/bin/gjs /usr/share/gnome-shell/org.gnome.Scre" label="unconfined")
Error occurred in handler for 'keychain:get-password': Error: No stored credentials fetched from keytar.
    at /snap/skype/234/usr/share/skypeforlinux/resources/app.asar/main.js:2:504313
    at async node:electron/js2c/browser_init:193:563
Error occurred in handler for 'keychain:get-password': Error: No stored credentials fetched from keytar.
    at /snap/skype/234/usr/share/skypeforlinux/resources/app.asar/main.js:2:504313
    at async node:electron/js2c/browser_init:193:563
Error occurred in handler for 'keychain:get-password': Error: No stored credentials fetched from keytar.
    at /snap/skype/234/usr/share/skypeforlinux/resources/app.asar/main.js:2:504313
    at async node:electron/js2c/browser_init:193:563
```

```
Linux 5.19.0-23-generic x86_64
```

---

### Post by tawilik2 on 2022-11-13
Hi,
I've run into the same issue. Have you happened to find out the solution for it yet?

---

