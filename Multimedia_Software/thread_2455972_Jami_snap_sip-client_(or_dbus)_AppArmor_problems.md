---
title: "Jami snap sip-client (or dbus) AppArmor problems"
date: 2021-01-01
forum: Multimedia Software
---

### Post by MocArt on 2021-01-01
[COLOR=#242729][FONT=Arial]I try to configure Jami sip client in ubuntu 20.04 and see in syslog file this message:
[/FONT][/COLOR]```
Jan  1 11:03:08 user-home dbus-daemon[1974]: apparmor="DENIED" operation="dbus_signal"  bus="session" path="/cx/ring/Ring/ConfigurationManager" interface="cx.ring.Ring.ConfigurationManager" member="volatileAccountDetailsChanged" mask="send" name="org.freedesktop.DBus" pid=11820 label="snap.jami.jami" peer_pid=2655 peer_label="unconfined"
```
```
sudo apparmor_status
apparmor module is loaded.
44 profiles are loaded.
25 profiles are in enforce mode.
   /snap/core/10577/usr/lib/snapd/snap-confine
   /snap/core/10577/usr/lib/snapd/snap-confine//mount-namespace-capture-helper
   /snap/snapd/10492/usr/lib/snapd/snap-confine
   /snap/snapd/10492/usr/lib/snapd/snap-confine//mount-namespace-capture-helper
   chromium_browser//browser_java
   chromium_browser//browser_openjdk
   chromium_browser//sanitized_helper
   snap-update-ns.core
   snap-update-ns.discord
   snap-update-ns.jami
   snap-update-ns.krdc
   snap-update-ns.p7zip-desktop
   snap-update-ns.snap-store
   snap-update-ns.telegram-desktop
   snap.core.hook.configure
   snap.discord.discord
   snap.discord.hook.configure
   snap.jami.jami
   snap.krdc.krdc
   snap.p7zip-desktop.p7zip-desktop
   snap.snap-store.hook.configure
   snap.snap-store.snap-store
   snap.snap-store.ubuntu-software
   snap.snap-store.ubuntu-software-local-file
   snap.telegram-desktop.telegram-desktop
19 profiles are in complain mode.
   /usr/sbin/dnsmasq
   /usr/sbin/dnsmasq//libvirt_leaseshelper
   avahi-daemon
   chromium_browser
   chromium_browser//chromium_browser_sandbox
   chromium_browser//lsb_release
   chromium_browser//xdgsettings
   identd
   klogd
   mdnsd
   nmbd
   nscd
   ping
   smbd
   smbldap-useradd
   smbldap-useradd///etc/init.d/nscd
   syslog-ng
   syslogd
   traceroute
6 processes have profiles defined.
6 processes are in enforce mode.
   /snap/jami/112/usr/bin/jami-gnome (5342) snap.jami.jami
   /snap/jami/112/usr/lib/ring/dring (5466) snap.jami.jami
   /usr/lib/x86_64-linux-gnu/webkit2gtk-4.0/WebKitWebProcess (5520) snap.jami.jami
   /usr/lib/x86_64-linux-gnu/webkit2gtk-4.0/WebKitNetworkProcess (5521) snap.jami.jami
   /snap/snap-store/518/usr/bin/snap-store (2400) snap.snap-store.ubuntu-software
   /snap/telegram-desktop/2315/usr/bin/telegram-desktop (2306) snap.telegram-desktop.telegram-desktop
0 processes are in complain mode.
0 processes are unconfined but have a profile defined.

```[COLOR=#242729][FONT=Arial]I think, it's linked with AppArmor, and it must be allowed for D-Bus or Jami app from enforced mode, but i can't understand it, how i can solve it? Thanks![/FONT][/COLOR]

---

