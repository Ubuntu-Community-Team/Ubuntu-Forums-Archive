---
title: "Asunder CD Ripper Stopped Working"
date: 2018-04-20
forum: Multimedia Software
---

### Post by webmanoffesto on 2018-04-20
For a long time Asunder has been my go-to cd-ripper.
[http://littlesvr.ca/asunder/](http://littlesvr.ca/asunder/)
But recently it stopped working. Other CD rippers work fine: i.e. Sound Juicer, K3b.
In Asunder, I click "Rip", progress remains at 0%, and later I get the message "0 Files created successfully".
How do I get this working again?

I'm trying to rip to Ogg Vorbis.

As part of my troubleshooting I also uninstalled and reinstalled Asunder, but that didn't help.


Some /var/log/syslog Log File items copied here [https://pastebin.com/0re6YBDF](https://pastebin.com/0re6YBDF)


Asunder 2.8.1
Ubuntu 16.04.4 LTS 64-bit, Gnome

```
Some Asunder related log items


Apr 20 08:36:22 tom-HP-ProBook-450-G3 kernel: [ 2656.945555] audit: type=1400 audit(1524227782.553:58): apparmor="DENIED" operation="open" profile="snap.ASUNDER-casept.ASUNDER" name="/dev/sr0" pid=12120 comm="cdparanoia" requested_mask="w" denied_mask="w" fsuid=1000 ouid=0
Apr 20 08:37:16 tom-HP-ProBook-450-G3 /usr/lib/gdm3/gdm-x-session[1884]: Activating service name='io.snapcraft.Launcher'
Apr 20 08:37:16 tom-HP-ProBook-450-G3 /usr/lib/gdm3/gdm-x-session[1884]: Successfully activated service 'io.snapcraft.Launcher'
Apr 20 08:37:16 tom-HP-ProBook-450-G3 io.snapcraft.Launcher[1898]: 2018/04/20 08:37:16.130200 userd.go:74: Starting snap userd


...


Apr 20 08:01:15 tom-HP-ProBook-450-G3 systemd-udevd[5776]: failed to execute '/usr/lib/snapd/snap-device-helper' '/usr/lib/snapd/snap-device-helper change snap_ASUNDER-casept_ASUNDER /devices/pci0000:00/0000:00:17.0/ata2/host1/target1:0:0/1:0:0:0/block/sr0 11:0': No such file or directory
Apr 20 08:01:15 tom-HP-ProBook-450-G3 systemd-udevd[5769]: Process '/usr/lib/snapd/snap-device-helper change snap_ASUNDER-casept_ASUNDER /devices/pci0000:00/0000:00:17.0/ata2/host1/target1:0:0/1:0:0:0/block/sr0 11:0' failed with exit code 2.
Apr 20 08:01:15 tom-HP-ProBook-450-G3 systemd-udevd[5777]: failed to execute '/usr/lib/snapd/snap-device-helper' '/usr/lib/snapd/snap-device-helper change snap_vlc_vlc /devices/pci0000:00/0000:00:17.0/ata2/host1/target1:0:0/1:0:0:0/block/sr0 11:0': No such file or directory
Apr 20 08:01:15 tom-HP-ProBook-450-G3 systemd-udevd[5769]: Process '/usr/lib/snapd/snap-device-helper change snap_vlc_vlc /devices/pci0000:00/0000:00:17.0/ata2/host1/target1:0:0/1:0:0:0/block/sr0 11:0' failed with exit code 2.
Apr 20 08:01:15 tom-HP-ProBook-450-G3 systemd-udevd[5791]: failed to execute '/usr/lib/snapd/snap-device-helper' '/usr/lib/snapd/snap-device-helper change snap_ASUNDER-casept_ASUNDER /devices/pci0000:00/0000:00:17.0/ata2/host1/target1:0:0/1:0:0:0/block/sr0 11:0': No such file or directory
Apr 20 08:01:15 tom-HP-ProBook-450-G3 systemd-udevd[5779]: Process '/usr/lib/snapd/snap-device-helper change snap_ASUNDER-casept_ASUNDER /devices/pci0000:00/0000:00:17.0/ata2/host1/target1:0:0/1:0:0:0/block/sr0 11:0' failed with exit code 2.
Apr 20 08:01:15 tom-HP-ProBook-450-G3 systemd-udevd[5792]: failed to execute '/usr/lib/snapd/snap-device-helper' '/usr/lib/snapd/snap-device-helper change snap_vlc_vlc /devices/pci0000:00/0000:00:17.0/ata2/host1/target1:0:0/1:0:0:0/block/sr0 11:0': No such file or directory
Apr 20 08:01:15 tom-HP-ProBook-450-G3 systemd-udevd[5779]: Process '/usr/lib/snapd/snap-device-helper change snap_vlc_vlc /devices/pci0000:00/0000:00:17.0/ata2/host1/target1:0:0/1:0:0:0/block/sr0 11:0' failed with exit code 2.
Apr 20 08:01:15 tom-HP-ProBook-450-G3 org.gtk.vfs.Daemon[1898]: (process:2322): GLib-GObject-WARNING **: invalid unclassed pointer in cast to 'GVfsBackendCdda'
Apr 20 08:01:20 tom-HP-ProBook-450-G3 pulseaudio[2052]: [pulseaudio] shm.c: shm_open() failed: No such file or directory
Apr 20 08:01:20 tom-HP-ProBook-450-G3 pulseaudio[2052]: [pulseaudio] shm.c: shm_open() failed: No such file or directory
Apr 20 08:01:54 tom-HP-ProBook-450-G3 chromium-browser.desktop[2746]: [2746:2746:0420/080154.454411:ERROR:exclusive_access_context.cc(15)] Not implemented reached in virtual void ExclusiveAccessContext::UpdateUIForTabFullscreen(ExclusiveAccessContext::TabFullscreenState)
Apr 20 08:02:18 tom-HP-ProBook-450-G3 chromium-browser.desktop[2746]: [2746:2746:0420/080218.456164:ERROR:exclusive_access_context.cc(15)] Not implemented reached in virtual void ExclusiveAccessContext::UpdateUIForTabFullscreen(ExclusiveAccessContext::TabFullscreenState)


...
```

---

### Post by mc4man on 2018-04-20
The snap version (asunder-casept) does not work in 16.04 & appears to have been abandoned.
[https://github.com/casept/snap-asunder/issues/1](https://github.com/casept/snap-asunder/issues/1)
If you were to run snap info asunder-casept  you'd see there are no new versions available even though asunder is currently at 2.9.3.  So the snap at 2.8.1 is only marginally newer than the .deb at 2.8.0

Use the repo .deb version which works fine.

---

### Post by webmanoffesto on 2018-04-20
Thanks, it works great now.

I followed instructions for an Ubuntu install
```
$ sudo add-apt-repository ppa:webupd8team/unstable
$ sudo apt-get update
$ sudo apt-get install asunder
```
[http://linuxg.net/how-to-install-asunder-2-7-on-ubuntu-15-04-ubuntu-14-10-ubuntu-14-04-ubuntu-12-04-and-derivative-systems/](http://linuxg.net/how-to-install-asunder-2-7-on-ubuntu-15-04-ubuntu-14-10-ubuntu-14-04-ubuntu-12-04-and-derivative-systems/)

---

