---
title: "Computer Shuts Down - with no warning."
date: 2010-09-03
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by 23dornot23d on 2010-09-03
I am not sure what is happening here but will supply the Syslog.

It is shutting down while trying to write a thread on a Blog is quite annoying to say the
least.

It did not shutdown fully - just kicked me out to a console window ...... but I would like to know why its done this ........ if anybody can see anything in this log that tells them what is happening and why it is deciding to shutdown.

I can supply any other information you require ........


There was only one user on this laptop ..... but the Syslog says 2 users ...... am I miss reading this - does it mean someon else was accessing my computer ?
 
(I did not have a separate console open either).

Does this mean someone is gaining access to my computer or am 

I miss understanding what is happening here ...... is this the correct place to look for why its kicking me out to the console
and restarting at the login screen.

( Its happened 3 or 4 times now since upgrading to generic-19 and the new Nvidia 256.53 driver ....... )
clutching at straws here ..... anybody that can help work out what is happening - it will be appreciated .....


```

Sep  3 13:18:24 keith-laptop AptDaemon: INFO: Quiting due to inactivity
Sep  3 13:18:24 keith-laptop AptDaemon: INFO: Shutdown was requested
Sep  3 13:21:23 keith-laptop ntpd[1817]: synchronized to 91.189.94.4, stratum 2
Sep  3 13:21:26 keith-laptop NetworkManager[944]: <error> [1283512886.308918] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
Sep  3 13:21:26 keith-laptop acpid: client 1130[0:0] has disconnected
Sep  3 13:21:26 keith-laptop acpid: client connected from 2523[0:0]
Sep  3 13:21:26 keith-laptop acpid: 1 client rule loaded
Sep  3 13:21:27 keith-laptop acpid: client connected from 2523[0:0]
Sep  3 13:21:27 keith-laptop acpid: 1 client rule loaded
Sep  3 13:21:29 keith-laptop NetworkManager[944]: <error> [1283512889.33541] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
Sep  3 13:21:29 keith-laptop rtkit-daemon[2006]: Successfully made thread 2564 of process 2564 (n/a) owned by '114' high priority at nice level -11.
Sep  3 13:21:29 keith-laptop rtkit-daemon[2006]: Supervising 1 threads of 1 processes of 1 users.
Sep  3 13:21:30 keith-laptop rtkit-daemon[2006]: Successfully made thread 2569 of process 2564 (n/a) owned by '114' RT at priority 5.
Sep  3 13:21:30 keith-laptop rtkit-daemon[2006]: Supervising 2 threads of 1 processes of 1 users.
Sep  3 13:21:30 keith-laptop rtkit-daemon[2006]: Successfully made thread 2570 of process 2564 (n/a) owned by '114' RT at priority 5.
Sep  3 13:21:30 keith-laptop rtkit-daemon[2006]: Supervising 3 threads of 1 processes of 1 users.
Sep  3 13:21:30 keith-laptop gdm-simple-greeter[2557]: Gtk-WARNING: /build/buildd/gtk+2.0-2.21.6/gtk/gtkwidget.c:5676: widget not within a GtkWindow
Sep  3 13:21:33 keith-laptop gdm-session-worker[2560]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Sep  3 13:21:37 keith-laptop NetworkManager[944]: <error> [1283512897.454168] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
Sep  3 13:21:37 keith-laptop NetworkManager[944]: <error> [1283512897.478474] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
Sep  3 13:21:37 keith-laptop gnome-session[2600]: EggSMClient-WARNING: Desktop file '/home/keith/.config/autostart/cairo-dock.desktop' has malformed Icon key 'cairo-dock.svg'(should not include extension)
Sep  3 13:21:37 keith-laptop rtkit-daemon[2006]: Successfully made thread 2661 of process 2661 (n/a) owned by '1000' high priority at nice level -11.
Sep  3 13:21:37 keith-laptop rtkit-daemon[2006]: Supervising 4 threads of 2 processes of 2 users.
Sep  3 13:21:37 keith-laptop pulseaudio[2661]: pid.c: Stale PID file, overwriting.
Sep  3 13:21:38 keith-laptop rtkit-daemon[2006]: Successfully made thread 2676 of process 2661 (n/a) owned by '1000' RT at priority 5.
Sep  3 13:21:38 keith-laptop rtkit-daemon[2006]: Supervising 5 threads of 2 processes of 2 users.
Sep  3 13:22:42 keith-laptop AptDaemon: INFO: Initializing daemon
Sep  3 13:27:42 keith-laptop AptDaemon: INFO: Quiting due to inactivity
Sep  3 13:27:42 keith-laptop AptDaemon: INFO: Shutdown was requested


```

Its been doing this now since the last upgrade ..... seems to run ok for so long .... then kicks me out.

After the first crash ..... it then seems to be ok for hours ......

---

### Post by viralmeme on 2010-09-03
> **23dornot23d said:**
> I am not sure what is happening here but will supply the Syslog. It is shutting down while trying to write a thread on a Blog is quite annoying to say the least

[Unwanted shutdowns - caused by AptDaemon?]("http://ubuntuforums.org/showthread.php?t=1491072")

---

### Post by 23dornot23d on 2010-09-03
Cheers for the reply .... viralmeme

It does not seem to be overheating and it does not do it on any of the other distributions that I have running ....... so I doubt the BIOS needs upgrading ......

If I do disable the ACPI ..... this may solve the problem for me ..... 

As that may be where the problem lies, but why has it just started to happen.

____________________________________________

Where do we look for clues ? .......

I have a feeling its to do with pulseaudio ...... after reading a few threads..... 

My reason for thinking its Pulseaudio

Mainly that Pulsaudio and  rtkit are linked together .........
( Because when I first saw it - I thought that possibly another user was on my system - which I do not think is the case now )

This one line intrigues me ....... 

Sep  3 13:21:26 keith-laptop NetworkManager[944]: <error> [1283512886.308918] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
Its the only real error ..... before the crash .....   

But to do with the network manager = but what triggers it ? 


and in my kernel I had a sign of a problem ..... with pulseaudio ..... 
I will add to this later as I am on another computer now.

---

### Post by cariboo on 2010-09-03
The reason you are seeing two users, is that you more than likely have a terminal open.

---

### Post by 23dornot23d on 2010-09-03
> **cariboo907 said:**
> The reason you are seeing two users, is that you more than likely have a terminal open.

I wish that was the case ..... but it is not ...... the only thing that I used was firefox.

rkhunter never found anything either ....
_____________________________________________________________

I get a crash now after ever fresh cold boot of the computer into Maverick ...

Latest messages just before crash and after it ..... 

I have only logged in the once this evening ..... 

I get one crash ..... then it seems to work ok for the rest of the evening

```

Sep  3 00:06:17 keith-laptop kernel: [ 9215.813467] ACPI Warning for \_SB_.PCI0.PEGP.VGA_.MXMI: Excess arguments - needs 1, found 2 (20100428/nspredef-319)
Sep  3 00:06:17 keith-laptop kernel: [ 9215.813514] ACPI Warning for \_SB_.PCI0.PEGP.VGA_.MXMS: Excess arguments - needs 1, found 2 (20100428/nspredef-319)
Sep  3 00:07:04 keith-laptop kernel: [ 9263.184043] usb 1-2: reset high speed USB device using ehci_hcd and address 2
Sep  3 00:20:45 keith-laptop kernel: [10083.833447] WARNING! power/level is deprecated; use power/control instead
Sep  3 00:20:45 keith-laptop kernel: [10083.916285] usb 1-2: USB disconnect, address 2
Sep  3 05:02:29 keith-laptop kernel: Kernel logging (proc) stopped.
Sep  3 13:12:10 keith-laptop kernel: imklog 4.2.0, log source = /proc/kmsg started.
Sep  3 13:12:10 keith-laptop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="914" x-info="http://www.rsyslog.com"] (re)start
Sep  3 13:12:10 keith-laptop rsyslogd: rsyslogd's groupid changed to 103
Sep  3 13:12:10 keith-laptop rsyslogd: rsyslogd's userid changed to 101

```I will do a safe-upgrade ..... if that does not cure it then 


Safe-upgrade did not cure it in fact made matters worse ..... cairo-dock now no longer runs ..... 

[IMG]http://a.imageshack.us/img683/3029/screenshot1sn.jpg[/IMG]



Last log before I re-install .... it may be useful to someone .....

```

Sep  3 20:33:41 keith-laptop NetworkManager[1090]: <error> [1283538821.702048] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
Sep  3 20:33:41 keith-laptop acpid: client 1205[0:0] has disconnected
Sep  3 20:33:41 keith-laptop acpid: client 1205[0:0] has disconnected
Sep  3 20:33:41 keith-laptop acpid: client connected from 2432[0:0]
Sep  3 20:33:41 keith-laptop acpid: 1 client rule loaded
Sep  3 20:33:41 keith-laptop kernel: [  176.940259] ACPI Warning for \_SB_.PCI0.PEGP.VGA_.MXMI: Excess arguments - needs 1, found 2 (20100428/nspredef-319)
Sep  3 20:33:41 keith-laptop kernel: [  176.940331] ACPI Warning for \_SB_.PCI0.PEGP.VGA_.MXMS: Excess arguments - needs 1, found 2 (20100428/nspredef-319)
Sep  3 20:33:43 keith-laptop acpid: client connected from 2432[0:0]
Sep  3 20:33:43 keith-laptop acpid: 1 client rule loaded
Sep  3 20:33:45 keith-laptop NetworkManager[1090]: <error> [1283538825.66918] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
Sep  3 20:33:45 keith-laptop rtkit-daemon[2139]: Successfully made thread 2477 of process 2477 (n/a) owned by '114' high priority at nice level -11.
Sep  3 20:33:45 keith-laptop rtkit-daemon[2139]: Supervising 1 threads of 1 processes of 1 users.
Sep  3 20:33:46 keith-laptop rtkit-daemon[2139]: Successfully made thread 2482 of process 2477 (n/a) owned by '114' RT at priority 5.
Sep  3 20:33:46 keith-laptop rtkit-daemon[2139]: Supervising 2 threads of 1 processes of 1 users.
Sep  3 20:33:46 keith-laptop gdm-simple-greeter[2468]: Gtk-WARNING: /build/buildd/gtk+2.0-2.21.7/gtk/gtkwidget.c:5678: widget not within a GtkWindow
Sep  3 20:33:46 keith-laptop rtkit-daemon[2139]: Successfully made thread 2484 of process 2477 (n/a) owned by '114' RT at priority 5.
Sep  3 20:33:46 keith-laptop rtkit-daemon[2139]: Supervising 3 threads of 1 processes of 1 users.
Sep  3 20:33:53 keith-laptop gdm-session-worker[2471]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Sep  3 20:33:59 keith-laptop NetworkManager[1090]: <error> [1283538839.874891] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
Sep  3 20:33:59 keith-laptop NetworkManager[1090]: <error> [1283538839.899994] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
Sep  3 20:34:00 keith-laptop gnome-session[2513]: EggSMClient-WARNING: Desktop file '/home/keith/.config/autostart/cairo-dock.desktop' has malformed Icon key 'cairo-dock.svg'(should not include extension)
Sep  3 20:34:00 keith-laptop rtkit-daemon[2139]: Successfully made thread 2577 of process 2577 (n/a) owned by '1000' high priority at nice level -11.
Sep  3 20:34:00 keith-laptop rtkit-daemon[2139]: Supervising 4 threads of 2 processes of 2 users.
Sep  3 20:34:00 keith-laptop pulseaudio[2577]: pid.c: Stale PID file, overwriting.
Sep  3 20:34:00 keith-laptop rtkit-daemon[2139]: Successfully made thread 2589 of process 2577 (n/a) owned by '1000' RT at priority 5.
Sep  3 20:34:00 keith-laptop rtkit-daemon[2139]: Supervising 5 threads of 2 processes of 2 users.
Sep  3 20:34:00 keith-laptop rtkit-daemon[2139]: Successfully made thread 2596 of process 2596 (n/a) owned by '1000' high priority at nice level -11.
Sep  3 20:34:00 keith-laptop rtkit-daemon[2139]: Supervising 6 threads of 3 processes of 2 users.
Sep  3 20:34:00 keith-laptop pulseaudio[2596]: pid.c: Daemon already running.
Sep  3 20:35:36 keith-laptop ntpd[1676]: synchronized to 91.189.94.4, stratum 2
Sep  3 20:35:36 keith-laptop ntpd[1676]: time reset -0.457701 s
Sep  3 20:35:36 keith-laptop ntpd[1676]: kernel time sync status change 2001
Sep  3 20:39:01 keith-laptop CRON[2747]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)


```____________________________________________________________________________

I will do a fresh clean install and we will see if it still happens ...... and if that don't work ......

___________________________________________________________________________

I feel the need to start again ...... and this was going oh so well back at 2.6.35-14-generic with Nvidia driver 256.44

I have gone back to that version and seems better now ....... 


```

[   400.740] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[   400.740] X Protocol Version 11, Revision 0
[   400.740] Build Operating System: Linux 2.6.24-25-server i686 Ubuntu
[   400.740] Current Operating System: Linux keith-laptop 2.6.35-14-generic #20-Ubuntu SMP Fri Aug 6 21:49:44 UTC 2010 i686
[   400.740] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-14-generic root=UUID=56d12a92-6e7e-409f-918f-41d096af4be7 ro quiet splash
[   400.740] Build Date: 03 September 2010  12:27:29PM
[   400.740] xorg-server 2:1.9.0-0ubuntu4 (For technical support please see http://www.ubuntu.com/support) 
[   400.740] Current version of pixman: 0.18.2
[   400.740]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[   400.740] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   400.741] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Sep  4 00:12:20 2010
[   400.741] (==) Using config file: "/etc/X11/xorg.conf"
[   400.741] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   400.741] (==) No Layout section.  Using the first Screen section.
[   400.741] (==) No screen section available. Using defaults.
[   400.741] (**) |-->Screen "Default Screen Section" (0)
[   400.741] (**) |   |-->Monitor "<default monitor>"
[   400.741] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[   400.741] (==) Automatically adding devices
[   400.741] (==) Automatically enabling devices
[   400.742] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   400.742]     Entry deleted from font path.
[   400.742] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[   400.742] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   400.742] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[   400.742] (II) Loader magic: 0x81f8e00
[   400.742] (II) Module ABI versions:
[   400.742]     X.Org ANSI C Emulation: 0.4
[   400.742]     X.Org Video Driver: 8.0
[   400.742]     X.Org XInput driver : 11.0
[   400.742]     X.Org Server Extension : 4.0
[   400.743] (--) PCI:*(0:1:0:0) 10de:06e9:1025:0142 rev 161, Mem @ 0xce000000/16777216, 0xd0000000/268435456, 0xcc000000/33554432, I/O @ 0x00002000/128
[   400.743] (II) Open ACPI successful (/var/run/acpid.socket)
[   400.743] (II) LoadModule: "extmod"
[   400.744] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[   400.744] (II) Module extmod: vendor="X.Org Foundation"
[   400.744]     compiled for 1.9.0, module version = 1.0.0
[   400.744]     Module class: X.Org Server Extension
[   400.744]     ABI class: X.Org Server Extension, version 4.0
[   400.744] (II) Loading extension MIT-SCREEN-SAVER
[   400.744] (II) Loading extension XFree86-VidModeExtension
[   400.745] (II) Loading extension XFree86-DGA
[   400.745] (II) Loading extension DPMS
[   400.745] (II) Loading extension XVideo
[   400.745] (II) Loading extension XVideo-MotionCompensation
[   400.745] (II) Loading extension X-Resource
[   400.745] (II) LoadModule: "dbe"
[   400.745] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[   400.745] (II) Module dbe: vendor="X.Org Foundation"
[   400.745]     compiled for 1.9.0, module version = 1.0.0
[   400.745]     Module class: X.Org Server Extension
[   400.745]     ABI class: X.Org Server Extension, version 4.0
[   400.745] (II) Loading extension DOUBLE-BUFFER
[   400.745] (II) LoadModule: "glx"
[   400.746] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   400.746] (II) Module glx: vendor="X.Org Foundation"
[   400.746]     compiled for 1.9.0, module version = 1.0.0
[   400.746]     ABI class: X.Org Server Extension, version 4.0
[   400.746] (==) AIGLX enabled
[   400.746] (II) Loading extension GLX
[   400.746] (II) LoadModule: "record"
[   400.746] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[   400.747] (II) Module record: vendor="X.Org Foundation"
[   400.747]     compiled for 1.9.0, module version = 1.13.0
[   400.747]     Module class: X.Org Server Extension
[   400.747]     ABI class: X.Org Server Extension, version 4.0
[   400.747] (II) Loading extension RECORD
[   400.747] (II) LoadModule: "dri"
[   400.747] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   400.747] (II) Module dri: vendor="X.Org Foundation"
[   400.747]     compiled for 1.9.0, module version = 1.0.0
[   400.747]     ABI class: X.Org Server Extension, version 4.0
[   400.747] (II) Loading extension XFree86-DRI
[   400.747] (II) LoadModule: "dri2"
[   400.748] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   400.748] (II) Module dri2: vendor="X.Org Foundation"
[   400.748]     compiled for 1.9.0, module version = 1.2.0
[   400.748]     ABI class: X.Org Server Extension, version 4.0
[   400.748] (II) Loading extension DRI2
[   400.748] (==) Matched nouveau as autoconfigured driver 0
[   400.748] (==) Matched nv as autoconfigured driver 1
[   400.748] (==) Matched vesa as autoconfigured driver 2
[   400.748] (==) Matched fbdev as autoconfigured driver 3
[   400.748] (==) Assigned the driver to the xf86ConfigLayout
[   400.748] (II) LoadModule: "nouveau"
[   400.748] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[   400.749] (II) Module nouveau: vendor="X.Org Foundation"
[   400.749]     compiled for 1.8.99.905, module version = 0.0.16
[   400.749]     Module class: X.Org Video Driver
[   400.749]     ABI class: X.Org Video Driver, version 8.0
[   400.749] (II) LoadModule: "nv"
[   400.749] (II) Loading /usr/lib/xorg/modules/drivers/nv_drv.so
[   400.749] (II) Module nv: vendor="X.Org Foundation"
[   400.749]     compiled for 1.8.99.905, module version = 2.1.17
[   400.749]     Module class: X.Org Video Driver
[   400.749]     ABI class: X.Org Video Driver, version 8.0
[   400.749] (II) LoadModule: "vesa"
[   400.749] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   400.750] (II) Module vesa: vendor="X.Org Foundation"
[   400.750]     compiled for 1.8.99.905, module version = 2.3.0
[   400.750]     Module class: X.Org Video Driver
[   400.750]     ABI class: X.Org Video Driver, version 8.0
[   400.750] (II) LoadModule: "fbdev"
[   400.750] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   400.750] (II) Module fbdev: vendor="X.Org Foundation"
[   400.750]     compiled for 1.8.99.905, module version = 0.4.2
[   400.750]     ABI class: X.Org Video Driver, version 8.0
[   400.750] (II) NOUVEAU driver Date:   Thu Aug 5 00:40:40 2010 +0200
[   400.750] (II) NOUVEAU driver for NVIDIA chipset families :
[   400.750]     RIVA TNT    (NV04)
[   400.750]     RIVA TNT2   (NV05)
[   400.750]     GeForce 256 (NV10)
[   400.750]     GeForce 2   (NV11, NV15)
[   400.750]     GeForce 4MX (NV17, NV18)
[   400.750]     GeForce 3   (NV20)
[   400.750]     GeForce 4Ti (NV25, NV28)
[   400.750]     GeForce FX  (NV3x)
[   400.750]     GeForce 6   (NV4x)
[   400.750]     GeForce 7   (G7x)
[   400.750]     GeForce 8   (G8x)
[   400.750] (II) NOUVEAU driver Date:   Thu Aug 5 00:40:40 2010 +0200
[   400.750] (II) NOUVEAU driver for NVIDIA chipset families :
[   400.750]     RIVA TNT    (NV04)
[   400.750]     RIVA TNT2   (NV05)
[   400.750]     GeForce 256 (NV10)
[   400.750]     GeForce 2   (NV11, NV15)
[   400.751]     GeForce 4MX (NV17, NV18)
[   400.751]     GeForce 3   (NV20)
[   400.751]     GeForce 4Ti (NV25, NV28)
[   400.751]     GeForce FX  (NV3x)
[   400.751]     GeForce 6   (NV4x)
[   400.751]     GeForce 7   (G7x)
[   400.751]     GeForce 8   (G8x)
[   400.751] (II) VESA: driver for VESA chipsets: vesa
[   400.751] (II) FBDEV: driver for framebuffer: fbdev
[   400.751] (--) using VT number 8

[   400.754] drmOpenDevice: node name is /dev/dri/card0
[   400.754] drmOpenDevice: open result is 8, (OK)
[   400.754] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[   400.754] drmOpenDevice: node name is /dev/dri/card0
[   400.754] drmOpenDevice: open result is 8, (OK)
[   400.754] drmOpenByBusid: drmOpenMinor returns 8
[   400.754] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[   400.754] (II) [drm] nouveau interface version: 0.0.16
[   400.754] (WW) Falling back to old probe method for vesa
[   400.754] (WW) Falling back to old probe method for fbdev
[   400.754] (II) Loading sub module "fbdevhw"
[   400.754] (II) LoadModule: "fbdevhw"
[   400.755] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   400.755] (II) Module fbdevhw: vendor="X.Org Foundation"
[   400.755]     compiled for 1.9.0, module version = 0.0.2
[   400.755]     ABI class: X.Org Video Driver, version 8.0
[   400.755] (II) Loading sub module "dri"
[   400.755] (II) LoadModule: "dri"
[   400.755] (II) Reloading /usr/lib/xorg/modules/extensions/libdri.so
[   400.755] (II) NOUVEAU(0): Loaded DRI module
[   400.755] drmOpenDevice: node name is /dev/dri/card0
[   400.755] drmOpenDevice: open result is 9, (OK)
[   400.756] drmOpenDevice: node name is /dev/dri/card0
[   400.756] drmOpenDevice: open result is 9, (OK)
[   400.756] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[   400.756] drmOpenDevice: node name is /dev/dri/card0
[   400.756] drmOpenDevice: open result is 9, (OK)
[   400.756] drmOpenByBusid: drmOpenMinor returns 9
[   400.756] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[   400.756] (II) [drm] DRM interface version 1.3
[   400.756] (II) [drm] DRM open master succeeded.
[   400.756] (--) NOUVEAU(0): Chipset: "NVIDIA NV98"
[   400.756] (II) NOUVEAU(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[   400.756] (==) NOUVEAU(0): Depth 24, (--) framebuffer bpp 32
[   400.756] (==) NOUVEAU(0): RGB weight 888
[   400.756] (==) NOUVEAU(0): Default visual is TrueColor
[   400.756] (==) NOUVEAU(0): Using HW cursor
[   400.756] (II) NOUVEAU(0): Output LVDS-1 has no monitor section
[   400.765] (II) NOUVEAU(0): Output DVI-D-1 has no monitor section
[   400.863] (II) NOUVEAU(0): Output VGA-1 has no monitor section
[   400.863] (II) NOUVEAU(0): EDID for output LVDS-1
[   400.863] (II) NOUVEAU(0): Manufacturer: AUO  Model: 6287  Serial#: 0
[   400.863] (II) NOUVEAU(0): Year: 2007  Week: 1
[   400.863] (II) NOUVEAU(0): EDID Version: 1.3
[   400.863] (II) NOUVEAU(0): Digital Display Input
[   400.863] (II) NOUVEAU(0): Max Image Size [cm]: horiz.: 37  vert.: 23
[   400.863] (II) NOUVEAU(0): Gamma: 2.20
[   400.863] (II) NOUVEAU(0): No DPMS capabilities specified
[   400.863] (II) NOUVEAU(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[   400.863] (II) NOUVEAU(0): First detailed timing is preferred mode
[   400.863] (II) NOUVEAU(0): redX: 0.590 redY: 0.345   greenX: 0.315 greenY: 0.555
[   400.863] (II) NOUVEAU(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
[   400.863] (II) NOUVEAU(0): Manufacturer's mask: 0
[   400.864] (II) NOUVEAU(0): Supported detailed timing:
[   400.864] (II) NOUVEAU(0): clock: 96.3 MHz   Image Size:  367 x 229 mm
[   400.864] (II) NOUVEAU(0): h_active: 1440  h_sync: 1648  h_sync_end 1680 h_blank_end 1760 h_border: 0
[   400.864] (II) NOUVEAU(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 912 v_border: 0
[   400.864] (II) NOUVEAU(0): Unknown vendor-specific block f
[   400.864] (II) NOUVEAU(0):  AUO
[   400.864] (II) NOUVEAU(0):  B170PW06 V2
[   400.864] (II) NOUVEAU(0): EDID (in hex):
[   400.864] (II) NOUVEAU(0):     00ffffffffffff0006af876200000000
[   400.864] (II) NOUVEAU(0):     01110103802517780a1cf59758508e27
[   400.864] (II) NOUVEAU(0):     27505400000001010101010101010101
[   400.864] (II) NOUVEAU(0):     0101010101019e25a04051840c30d020
[   400.864] (II) NOUVEAU(0):     36006fe5100000180000000f00000000
[   400.864] (II) NOUVEAU(0):     00000000000000000020000000fe0041
[   400.864] (II) NOUVEAU(0):     554f0a200020202020202020000000fe
[   400.864] (II) NOUVEAU(0):     004231373050573036205632200a000b
[   400.864] (II) NOUVEAU(0): EDID vendor "AUO", prod id 25223
[   400.864] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   400.864] (II) NOUVEAU(0): Modeline "1440x900"x0.0   96.30  1440 1648 1680 1760  900 903 909 912 -hsync -vsync (54.7 kHz)
[   400.864] (II) NOUVEAU(0): Printing probed modes for output LVDS-1
[   400.864] (II) NOUVEAU(0): Modeline "1440x900"x60.0   96.30  1440 1648 1680 1760  900 903 909 912 -hsync -vsync (54.7 kHz)
[   400.864] (II) NOUVEAU(0): Modeline "1152x864"x60.0   81.75  1152 1216 1336 1520  864 867 871 897 -hsync +vsync (53.8 kHz)
[   400.864] (II) NOUVEAU(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
[   400.864] (II) NOUVEAU(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
[   400.864] (II) NOUVEAU(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
[   400.864] (II) NOUVEAU(0): Modeline "720x400"x59.6   22.25  720 744 808 896  400 403 413 417 -hsync +vsync (24.8 kHz)
[   400.864] (II) NOUVEAU(0): Modeline "640x400"x60.0   20.00  640 664 720 800  400 403 409 417 -hsync +vsync (25.0 kHz)
[   400.864] (II) NOUVEAU(0): Modeline "640x350"x59.8   17.50  640 664 720 800  350 353 363 366 -hsync +vsync (21.9 kHz)
[   400.873] (II) NOUVEAU(0): EDID for output DVI-D-1
[   400.971] (II) NOUVEAU(0): EDID for output VGA-1
[   400.971] (II) NOUVEAU(0): Output LVDS-1 connected
[   400.971] (II) NOUVEAU(0): Output DVI-D-1 disconnected
[   400.971] (II) NOUVEAU(0): Output VGA-1 disconnected
[   400.971] (II) NOUVEAU(0): Using exact sizes for initial modes
[   400.971] (II) NOUVEAU(0): Output LVDS-1 using initial mode 1440x900
[   400.971] (II) NOUVEAU(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[   400.971] (--) NOUVEAU(0): Virtual size is 1440x900 (pitch 1440)
[   400.971] (**) NOUVEAU(0):  Driver mode "1440x900": 96.3 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
[   400.971] (II) NOUVEAU(0): Modeline "1440x900"x60.0   96.30  1440 1648 1680 1760  900 903 909 912 -hsync -vsync (54.7 kHz)
[   400.971] (**) NOUVEAU(0):  Driver mode "1152x864": 81.8 MHz (scaled from 0.0 MHz), 53.8 kHz, 60.0 Hz
[   400.971] (II) NOUVEAU(0): Modeline "1152x864"x60.0   81.75  1152 1216 1336 1520  864 867 871 897 -hsync +vsync (53.8 kHz)
[   400.971] (**) NOUVEAU(0):  Driver mode "1024x768": 63.5 MHz (scaled from 0.0 MHz), 47.8 kHz, 59.9 Hz
[   400.971] (II) NOUVEAU(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
[   400.971] (**) NOUVEAU(0):  Driver mode "800x600": 38.2 MHz (scaled from 0.0 MHz), 37.4 kHz, 59.9 Hz
[   400.971] (II) NOUVEAU(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
[   400.971] (**) NOUVEAU(0):  Driver mode "640x480": 23.8 MHz (scaled from 0.0 MHz), 29.7 kHz, 59.4 Hz
[   400.971] (II) NOUVEAU(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
[   400.971] (**) NOUVEAU(0):  Driver mode "720x400": 22.2 MHz (scaled from 0.0 MHz), 24.8 kHz, 59.6 Hz
[   400.971] (II) NOUVEAU(0): Modeline "720x400"x59.6   22.25  720 744 808 896  400 403 413 417 -hsync +vsync (24.8 kHz)
[   400.971] (**) NOUVEAU(0):  Driver mode "640x400": 20.0 MHz (scaled from 0.0 MHz), 25.0 kHz, 60.0 Hz
[   400.971] (II) NOUVEAU(0): Modeline "640x400"x60.0   20.00  640 664 720 800  400 403 409 417 -hsync +vsync (25.0 kHz)
[   400.971] (**) NOUVEAU(0):  Driver mode "640x350": 17.5 MHz (scaled from 0.0 MHz), 21.9 kHz, 59.8 Hz
[   400.971] (II) NOUVEAU(0): Modeline "640x350"x59.8   17.50  640 664 720 800  350 353 363 366 -hsync +vsync (21.9 kHz)
[   400.971] (**) NOUVEAU(0): Display dimensions: (370, 230) mm
[   400.971] (**) NOUVEAU(0): DPI set to (98, 99)
[   400.971] (II) Loading sub module "wfb"
[   400.971] (II) LoadModule: "wfb"
[   400.972] (II) Loading /usr/lib/xorg/modules/libwfb.so
[   400.972] (II) Module wfb: vendor="X.Org Foundation"
[   400.972]     compiled for 1.9.0, module version = 1.0.0
[   400.972]     ABI class: X.Org ANSI C Emulation, version 0.4
[   400.972] (II) Loading sub module "fb"
[   400.972] (II) LoadModule: "fb"
[   400.972] (II) Loading /usr/lib/xorg/modules/libfb.so
[   400.972] (II) Module fb: vendor="X.Org Foundation"
[   400.972]     compiled for 1.9.0, module version = 1.0.0
[   400.972]     ABI class: X.Org ANSI C Emulation, version 0.4
[   400.972] (II) Loading sub module "exa"
[   400.972] (II) LoadModule: "exa"
[   400.973] (II) Loading /usr/lib/xorg/modules/libexa.so
[   400.973] (II) Module exa: vendor="X.Org Foundation"
[   400.973]     compiled for 1.9.0, module version = 2.5.0
[   400.973]     ABI class: X.Org Video Driver, version 8.0
[   400.973] (II) Loading sub module "shadowfb"
[   400.973] (II) LoadModule: "shadowfb"
[   400.974] (II) Loading /usr/lib/xorg/modules/libshadowfb.so
[   400.974] (II) Module shadowfb: vendor="X.Org Foundation"
[   400.974]     compiled for 1.9.0, module version = 1.0.0
[   400.974]     ABI class: X.Org ANSI C Emulation, version 0.4
[   400.974] (II) UnloadModule: "nv"
[   400.974] (II) Unloading /usr/lib/xorg/modules/drivers/nv_drv.so
[   400.974] (II) UnloadModule: "vesa"
[   400.974] (II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   400.974] (II) UnloadModule: "fbdev"
[   400.974] (II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   400.974] (II) UnloadModule: "fbdevhw"
[   400.974] (II) Unloading /usr/lib/xorg/modules/libfbdevhw.so
[   400.974] (--) Depth 24 pixmap format is 32 bpp
[   400.982] (II) NOUVEAU(0): Opened GPU channel 2
[   400.983] (II) NOUVEAU(0): [DRI2] Setup complete
[   400.983] (II) NOUVEAU(0): [DRI2]   DRI driver: nouveau
[   400.983] (II) NOUVEAU(0): GART: 512MiB available
[   400.985] (II) NOUVEAU(0): GART: Allocated 16MiB as a scratch buffer
[   400.985] (II) EXA(0): Driver allocated offscreen pixmaps
[   400.985] (II) EXA(0): Driver registered support for the following operations:
[   400.985] (II)         Solid
[   400.985] (II)         Copy
[   400.985] (II)         Composite (RENDER acceleration)
[   400.985] (II)         UploadToScreen
[   400.985] (II)         DownloadFromScreen
[   400.985] (==) NOUVEAU(0): Backing store disabled
[   400.985] (==) NOUVEAU(0): Silken mouse enabled
[   400.986] (II) NOUVEAU(0): [XvMC] Associated with Nouveau GeForce 8/9 Textured Video.
[   400.986] (II) NOUVEAU(0): [XvMC] Extension initialized.
[   400.986] (==) NOUVEAU(0): DPMS enabled
[   400.986] (II) NOUVEAU(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[   400.986] (--) RandR disabled
[   400.986] (II) Initializing built-in extension Generic Event Extension
[   400.986] (II) Initializing built-in extension SHAPE
[   400.986] (II) Initializing built-in extension MIT-SHM
[   400.986] (II) Initializing built-in extension XInputExtension
[   400.986] (II) Initializing built-in extension XTEST
[   400.986] (II) Initializing built-in extension BIG-REQUESTS
[   400.986] (II) Initializing built-in extension SYNC
[   400.986] (II) Initializing built-in extension XKEYBOARD
[   400.986] (II) Initializing built-in extension XC-MISC
[   400.986] (II) Initializing built-in extension SECURITY
[   400.986] (II) Initializing built-in extension XINERAMA
[   400.986] (II) Initializing built-in extension XFIXES
[   400.986] (II) Initializing built-in extension RENDER
[   400.986] (II) Initializing built-in extension RANDR
[   400.986] (II) Initializing built-in extension COMPOSITE
[   400.986] (II) Initializing built-in extension DAMAGE
[   400.986] (II) Initializing built-in extension GESTURE
[   400.998] (II) AIGLX error: dlopen of /usr/lib/dri/nouveau_dri.so failed (/usr/lib/dri/nouveau_dri.so: cannot open shared object file: No such file or directory)
[   400.998] (II) AIGLX: reverting to software rendering
[   400.998] (II) AIGLX: Screen 0 is not DRI capable
[   401.000] (II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
[   401.000] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[   401.013] (II) NOUVEAU(0): NVEnterVT is called.
[   401.013] (II) NOUVEAU(0): Setting screen physical size to 380 x 238
[   401.013] resize called 1440 900
[   401.043] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   401.055] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[   401.055] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   401.055] (II) LoadModule: "evdev"
[   401.055] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   401.055] (II) Module evdev: vendor="X.Org Foundation"
[   401.056]     compiled for 1.9.0, module version = 2.3.2
[   401.056]     Module class: X.Org XInput Driver
[   401.056]     ABI class: X.Org XInput driver, version 11.0
[   401.056] (**) Power Button: always reports core events
[   401.056] (**) Power Button: Device: "/dev/input/event3"
[   401.069] (II) Power Button: Found keys
[   401.069] (II) Power Button: Configuring as keyboard
[   401.069] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[   401.069] (**) Option "xkb_rules" "evdev"
[   401.069] (**) Option "xkb_model" "pc105"
[   401.069] (**) Option "xkb_layout" "gb"
[   401.074] (II) XKB: reuse xkmfile /var/lib/xkb/server-2B4266AA55228AE7D9557A18F1965DBA19850816.xkm
[   401.076] (II) config/udev: Adding input device Video Bus (/dev/input/event9)
[   401.076] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[   401.076] (**) Video Bus: always reports core events
[   401.076] (**) Video Bus: Device: "/dev/input/event9"
[   401.085] (II) Video Bus: Found keys
[   401.085] (II) Video Bus: Configuring as keyboard
[   401.085] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[   401.085] (**) Option "xkb_rules" "evdev"
[   401.085] (**) Option "xkb_model" "pc105"
[   401.085] (**) Option "xkb_layout" "gb"
[   401.088] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[   401.088] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   401.088] (**) Power Button: always reports core events
[   401.088] (**) Power Button: Device: "/dev/input/event1"
[   401.101] (II) Power Button: Found keys
[   401.101] (II) Power Button: Configuring as keyboard
[   401.101] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[   401.101] (**) Option "xkb_rules" "evdev"
[   401.101] (**) Option "xkb_model" "pc105"
[   401.101] (**) Option "xkb_layout" "gb"
[   401.102] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[   401.102] (II) No input driver/identifier specified (ignoring)
[   401.102] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[   401.102] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[   401.102] (**) Sleep Button: always reports core events
[   401.102] (**) Sleep Button: Device: "/dev/input/event2"
[   401.117] (II) Sleep Button: Found keys
[   401.117] (II) Sleep Button: Configuring as keyboard
[   401.117] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[   401.117] (**) Option "xkb_rules" "evdev"
[   401.117] (**) Option "xkb_model" "pc105"
[   401.117] (**) Option "xkb_layout" "gb"
[   401.121] (II) config/udev: Adding input device HID 04d9:048e (/dev/input/event5)
[   401.121] (**) HID 04d9:048e: Applying InputClass "evdev pointer catchall"
[   401.121] (**) HID 04d9:048e: always reports core events
[   401.121] (**) HID 04d9:048e: Device: "/dev/input/event5"
[   401.133] (II) HID 04d9:048e: Found 9 mouse buttons
[   401.133] (II) HID 04d9:048e: Found scroll wheel(s)
[   401.133] (II) HID 04d9:048e: Found relative axes
[   401.133] (II) HID 04d9:048e: Found x and y relative axes
[   401.133] (II) HID 04d9:048e: Configuring as mouse
[   401.133] (**) HID 04d9:048e: YAxisMapping: buttons 4 and 5
[   401.133] (**) HID 04d9:048e: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   401.133] (II) XINPUT: Adding extended input device "HID 04d9:048e" (type: MOUSE)
[   401.133] (II) HID 04d9:048e: initialized for relative axes.
[   401.134] (II) config/udev: Adding input device HID 04d9:048e (/dev/input/mouse0)
[   401.134] (II) No input driver/identifier specified (ignoring)
[   401.140] (II) config/udev: Adding input device Acer Crystal Eye webcam (/dev/input/event10)
[   401.140] (**) Acer Crystal Eye webcam: Applying InputClass "evdev keyboard catchall"
[   401.140] (**) Acer Crystal Eye webcam: always reports core events
[   401.140] (**) Acer Crystal Eye webcam: Device: "/dev/input/event10"
[   401.149] (II) Acer Crystal Eye webcam: Found keys
[   401.149] (II) Acer Crystal Eye webcam: Configuring as keyboard
[   401.149] (II) XINPUT: Adding extended input device "Acer Crystal Eye webcam" (type: KEYBOARD)
[   401.149] (**) Option "xkb_rules" "evdev"
[   401.149] (**) Option "xkb_model" "pc105"
[   401.149] (**) Option "xkb_layout" "gb"
[   401.160] (II) config/udev: Adding input device CHESEN USB Keyboard (/dev/input/event6)
[   401.160] (**) CHESEN USB Keyboard: Applying InputClass "evdev keyboard catchall"
[   401.160] (**) CHESEN USB Keyboard: always reports core events
[   401.160] (**) CHESEN USB Keyboard: Device: "/dev/input/event6"
[   401.169] (II) CHESEN USB Keyboard: Found keys
[   401.169] (II) CHESEN USB Keyboard: Configuring as keyboard
[   401.169] (II) XINPUT: Adding extended input device "CHESEN USB Keyboard" (type: KEYBOARD)
[   401.169] (**) Option "xkb_rules" "evdev"
[   401.169] (**) Option "xkb_model" "pc105"
[   401.169] (**) Option "xkb_layout" "gb"
[   401.170] (II) config/udev: Adding input device CHESEN USB Keyboard (/dev/input/event7)
[   401.170] (**) CHESEN USB Keyboard: Applying InputClass "evdev keyboard catchall"
[   401.170] (**) CHESEN USB Keyboard: always reports core events
[   401.170] (**) CHESEN USB Keyboard: Device: "/dev/input/event7"
[   401.171] (II) CHESEN USB Keyboard: Found keys
[   401.171] (II) CHESEN USB Keyboard: Configuring as keyboard
[   401.171] (II) XINPUT: Adding extended input device "CHESEN USB Keyboard" (type: KEYBOARD)
[   401.171] (**) Option "xkb_rules" "evdev"
[   401.171] (**) Option "xkb_model" "pc105"
[   401.171] (**) Option "xkb_layout" "gb"
[   401.172] (II) config/udev: Adding input device UC-LOGIC Tablet WP5540U (/dev/input/event8)
[   401.172] (**) UC-LOGIC Tablet WP5540U: Applying InputClass "evdev pointer catchall"
[   401.172] (**) UC-LOGIC Tablet WP5540U: Applying InputClass "evdev tablet catchall"
[   401.172] (**) UC-LOGIC Tablet WP5540U: always reports core events
[   401.173] (**) UC-LOGIC Tablet WP5540U: Device: "/dev/input/event8"
[   401.185] (II) UC-LOGIC Tablet WP5540U: Found 10 mouse buttons
[   401.185] (II) UC-LOGIC Tablet WP5540U: Found scroll wheel(s)
[   401.185] (II) UC-LOGIC Tablet WP5540U: Found relative axes
[   401.185] (II) UC-LOGIC Tablet WP5540U: Found x and y relative axes
[   401.185] (II) UC-LOGIC Tablet WP5540U: Found absolute axes
[   401.185] (II) evdev-grail: failed to open grail, no gesture support
[   401.185] (II) UC-LOGIC Tablet WP5540U: Found x and y absolute axes
[   401.185] (II) UC-LOGIC Tablet WP5540U: Found absolute tablet.
[   401.185] (II) UC-LOGIC Tablet WP5540U: Configuring as tablet
[   401.185] (**) UC-LOGIC Tablet WP5540U: YAxisMapping: buttons 4 and 5
[   401.185] (**) UC-LOGIC Tablet WP5540U: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   401.185] (II) XINPUT: Adding extended input device "UC-LOGIC Tablet WP5540U" (type: TABLET)
[   401.185] (WW) UC-LOGIC Tablet WP5540U: touchpads, tablets and touchscreens ignore relative axes.
[   401.185] (II) UC-LOGIC Tablet WP5540U: initialized for absolute axes.
[   401.186] (II) config/udev: Adding input device UC-LOGIC Tablet WP5540U (/dev/input/mouse1)
[   401.186] (II) No input driver/identifier specified (ignoring)
[   401.192] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[   401.192] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[   401.193] (**) AT Translated Set 2 keyboard: always reports core events
[   401.193] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[   401.209] (II) AT Translated Set 2 keyboard: Found keys
[   401.209] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[   401.209] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[   401.209] (**) Option "xkb_rules" "evdev"
[   401.209] (**) Option "xkb_model" "pc105"
[   401.209] (**) Option "xkb_layout" "gb"
[   401.210] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event11)
[   401.210] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[   401.210] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[   401.210] (II) LoadModule: "synaptics"
[   401.211] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[   401.211] (II) Module synaptics: vendor="X.Org Foundation"
[   401.211]     compiled for 1.8.99.905, module version = 1.2.2
[   401.211]     Module class: X.Org XInput Driver
[   401.211]     ABI class: X.Org XInput driver, version 11.0
[   401.211] (II) Synaptics touchpad driver version 1.2.2
[   401.211] (**) Option "Device" "/dev/input/event11"
[   401.257] (II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
[   401.257] (II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
[   401.257] (II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[   401.257] (II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
[   401.257] (II) SynPS/2 Synaptics TouchPad: buttons: left right
[   401.289] (--) SynPS/2 Synaptics TouchPad: touchpad found
[   401.289] (**) SynPS/2 Synaptics TouchPad: always reports core events
[   401.305] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[   401.305] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[   401.305] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 0
[   401.305] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[   401.305] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[   401.337] (--) SynPS/2 Synaptics TouchPad: touchpad found
[   401.337] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse2)
[   401.337] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[   401.337] (II) Synaptics touchpad driver version 1.2.2
[   401.977] SynPS/2 Synaptics TouchPad no synaptics event device found
[   401.977] (**) Option "Device" "/dev/input/mouse2"
[   402.013] Query no Synaptics: 6003C8
[   402.013] (--) SynPS/2 Synaptics TouchPad: no supported touchpad found
[   402.013] (EE) SynPS/2 Synaptics TouchPad Unable to query/initialize Synaptics hardware.
[   402.013] (EE) PreInit failed for input device "SynPS/2 Synaptics TouchPad"
[   402.013] (II) UnloadModule: "synaptics"
[   402.387] (II) NOUVEAU(0): EDID vendor "AUO", prod id 25223
[   402.387] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   402.387] (II) NOUVEAU(0): Modeline "1440x900"x0.0   96.30  1440 1648 1680 1760  900 903 909 912 -hsync -vsync (54.7 kHz)
[   402.496] (II) NOUVEAU(0): EDID vendor "AUO", prod id 25223
[   402.496] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   402.496] (II) NOUVEAU(0): Modeline "1440x900"x0.0   96.30  1440 1648 1680 1760  900 903 909 912 -hsync -vsync (54.7 kHz)
[   402.611] (II) NOUVEAU(0): EDID vendor "AUO", prod id 25223
[   402.611] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   402.611] (II) NOUVEAU(0): Modeline "1440x900"x0.0   96.30  1440 1648 1680 1760  900 903 909 912 -hsync -vsync (54.7 kHz)
[   402.719] (II) NOUVEAU(0): EDID vendor "AUO", prod id 25223
[   402.719] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   402.719] (II) NOUVEAU(0): Modeline "1440x900"x0.0   96.30  1440 1648 1680 1760  900 903 909 912 -hsync -vsync (54.7 kHz)
[   402.827] resize called 1440 900
[   427.436] (II) NOUVEAU(0): EDID vendor "AUO", prod id 25223
[   427.436] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   427.436] (II) NOUVEAU(0): Modeline "1440x900"x0.0   96.30  1440 1648 1680 1760  900 903 909 912 -hsync -vsync (54.7 kHz)
[   427.545] (II) NOUVEAU(0): EDID vendor "AUO", prod id 25223
[   427.545] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   427.545] (II) NOUVEAU(0): Modeline "1440x900"x0.0   96.30  1440 1648 1680 1760  900 903 909 912 -hsync -vsync (54.7 kHz)
[   427.654] (II) NOUVEAU(0): EDID vendor "AUO", prod id 25223
[   427.654] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   427.654] (II) NOUVEAU(0): Modeline "1440x900"x0.0   96.30  1440 1648 1680 1760  900 903 909 912 -hsync -vsync (54.7 kHz)
[   427.762] (II) NOUVEAU(0): EDID vendor "AUO", prod id 25223
[   427.762] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   427.762] (II) NOUVEAU(0): Modeline "1440x900"x0.0   96.30  1440 1648 1680 1760  900 903 909 912 -hsync -vsync (54.7 kHz)
[   427.871] resize called 1440 900
[   432.828] (II) NOUVEAU(0): EDID vendor "AUO", prod id 25223
[   432.828] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   432.828] (II) NOUVEAU(0): Modeline "1440x900"x0.0   96.30  1440 1648 1680 1760  900 903 909 912 -hsync -vsync (54.7 kHz)


```It almost seemed to be ok till the GLX part ...... 

It runs ok after one crash ....  but its sluggish ..... software rendering ...... oh no ......

though all the 3D programs seem to work ok ..... but there is definately no accelaration as such .......

hey ho ....... what next ...... re-install ...... 

I really did not want to do this ...... as it was going so very very well .........

Ok I have not yet ...

```

[   660.529] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[   660.529] X Protocol Version 11, Revision 0
[   660.529] Build Operating System: Linux 2.6.24-25-server i686 Ubuntu
[   660.529] Current Operating System: Linux keith-laptop 2.6.35-14-generic #20-Ubuntu SMP Fri Aug 6 21:49:44 UTC 2010 i686
[   660.529] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-14-generic root=UUID=56d12a92-6e7e-409f-918f-41d096af4be7 ro quiet splash
[   660.529] Build Date: 03 September 2010  12:27:29PM
[   660.529] xorg-server 2:1.9.0-0ubuntu4 (For technical support please see http://www.ubuntu.com/support) 
[   660.529] Current version of pixman: 0.18.2
[   660.529]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[   660.529] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   660.529] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Sep  4 01:03:30 2010
[   660.530] (==) Using config file: "/etc/X11/xorg.conf"
[   660.530] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   660.530] (==) ServerLayout "Layout0"
[   660.530] (**) |-->Screen "Screen0" (0)
[   660.530] (**) |   |-->Monitor "Monitor0"
[   660.530] (**) |   |-->Device "Device0"
[   660.530] (**) |-->Input Device "Keyboard0"
[   660.530] (**) |-->Input Device "Mouse0"
[   660.530] (==) Automatically adding devices
[   660.530] (==) Automatically enabling devices
[   660.531] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   660.531]     Entry deleted from font path.
[   660.531] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[   660.531] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   660.531] (WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[   660.531] (WW) Disabling Keyboard0
[   660.531] (WW) Disabling Mouse0
[   660.531] (II) Loader magic: 0x81f8e00
[   660.531] (II) Module ABI versions:
[   660.531]     X.Org ANSI C Emulation: 0.4
[   660.531]     X.Org Video Driver: 8.0
[   660.531]     X.Org XInput driver : 11.0
[   660.531]     X.Org Server Extension : 4.0
[   660.532] (--) PCI:*(0:1:0:0) 10de:06e9:1025:0142 rev 161, Mem @ 0xce000000/16777216, 0xd0000000/268435456, 0xcc000000/33554432, I/O @ 0x00002000/128
[   660.532] (II) Open ACPI successful (/var/run/acpid.socket)
[   660.532] (II) LoadModule: "extmod"
[   660.533] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[   660.533] (II) Module extmod: vendor="X.Org Foundation"
[   660.533]     compiled for 1.9.0, module version = 1.0.0
[   660.533]     Module class: X.Org Server Extension
[   660.533]     ABI class: X.Org Server Extension, version 4.0
[   660.533] (II) Loading extension MIT-SCREEN-SAVER
[   660.533] (II) Loading extension XFree86-VidModeExtension
[   660.533] (II) Loading extension XFree86-DGA
[   660.533] (II) Loading extension DPMS
[   660.533] (II) Loading extension XVideo
[   660.533] (II) Loading extension XVideo-MotionCompensation
[   660.533] (II) Loading extension X-Resource
[   660.533] (II) LoadModule: "dbe"
[   660.534] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[   660.534] (II) Module dbe: vendor="X.Org Foundation"
[   660.534]     compiled for 1.9.0, module version = 1.0.0
[   660.534]     Module class: X.Org Server Extension
[   660.534]     ABI class: X.Org Server Extension, version 4.0
[   660.534] (II) Loading extension DOUBLE-BUFFER
[   660.534] (II) LoadModule: "glx"
[   660.534] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   660.561] (II) Module glx: vendor="NVIDIA Corporation"
[   660.561]     compiled for 4.0.2, module version = 1.0.0
[   660.561]     Module class: X.Org Server Extension
[   660.561] (II) NVIDIA GLX Module  256.53  Fri Aug 27 21:28:41 PDT 2010
[   660.561] (II) Loading extension GLX
[   660.561] (II) LoadModule: "record"
[   660.561] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[   660.562] (II) Module record: vendor="X.Org Foundation"
[   660.562]     compiled for 1.9.0, module version = 1.13.0
[   660.562]     Module class: X.Org Server Extension
[   660.562]     ABI class: X.Org Server Extension, version 4.0
[   660.562] (II) Loading extension RECORD
[   660.562] (II) LoadModule: "dri"
[   660.562] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   660.562] (II) Module dri: vendor="X.Org Foundation"
[   660.562]     compiled for 1.9.0, module version = 1.0.0
[   660.562]     ABI class: X.Org Server Extension, version 4.0
[   660.562] (II) Loading extension XFree86-DRI
[   660.562] (II) LoadModule: "dri2"
[   660.563] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   660.563] (II) Module dri2: vendor="X.Org Foundation"
[   660.563]     compiled for 1.9.0, module version = 1.2.0
[   660.563]     ABI class: X.Org Server Extension, version 4.0
[   660.563] (II) Loading extension DRI2
[   660.563] (II) LoadModule: "nvidia"
[   660.563] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[   660.564] (II) Module nvidia: vendor="NVIDIA Corporation"
[   660.564]     compiled for 4.0.2, module version = 1.0.0
[   660.564]     Module class: X.Org Video Driver
[   660.564] (II) NVIDIA dlloader X Driver  256.53  Fri Aug 27 21:05:55 PDT 2010
[   660.564] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[   660.564] (--) using VT number 8

[   660.660] (II) Loading sub module "fb"
[   660.660] (II) LoadModule: "fb"
[   660.660] (II) Loading /usr/lib/xorg/modules/libfb.so
[   660.660] (II) Module fb: vendor="X.Org Foundation"
[   660.660]     compiled for 1.9.0, module version = 1.0.0
[   660.660]     ABI class: X.Org ANSI C Emulation, version 0.4
[   660.660] (II) Loading sub module "wfb"
[   660.660] (II) LoadModule: "wfb"
[   660.661] (II) Loading /usr/lib/xorg/modules/libwfb.so
[   660.661] (II) Module wfb: vendor="X.Org Foundation"
[   660.661]     compiled for 1.9.0, module version = 1.0.0
[   660.661]     ABI class: X.Org ANSI C Emulation, version 0.4
[   660.661] (II) Loading sub module "ramdac"
[   660.661] (II) LoadModule: "ramdac"
[   660.661] (II) Module "ramdac" already built-in
[   660.661] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[   660.661] (==) NVIDIA(0): RGB weight 888
[   660.661] (==) NVIDIA(0): Default visual is TrueColor
[   660.661] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[   660.661] (**) NVIDIA(0): Enabling RENDER acceleration
[   660.662] (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
[   660.662] (II) NVIDIA(0):     enabled.
[   661.299] (II) NVIDIA(0): NVIDIA GPU GeForce 9300M GS (G98) at PCI:1:0:0 (GPU-0)
[   661.299] (--) NVIDIA(0): Memory: 524288 kBytes
[   661.299] (--) NVIDIA(0): VideoBIOS: 62.98.51.00.06
[   661.299] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[   661.299] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[   661.299] (--) NVIDIA(0): Connected display device(s) on GeForce 9300M GS at PCI:1:0:0:
[   661.299] (--) NVIDIA(0):     AUO (DFP-0)
[   661.299] (--) NVIDIA(0): AUO (DFP-0): 330.0 MHz maximum pixel clock
[   661.299] (--) NVIDIA(0): AUO (DFP-0): Internal Dual Link LVDS
[   661.363] (II) NVIDIA(0): Assigned Display Device: DFP-0
[   661.363] (==) NVIDIA(0): 
[   661.363] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[   661.363] (==) NVIDIA(0):     will be used as the requested mode.
[   661.363] (==) NVIDIA(0): 
[   661.363] (II) NVIDIA(0): Validated modes:
[   661.363] (II) NVIDIA(0):     "nvidia-auto-select"
[   661.363] (II) NVIDIA(0): Virtual screen size determined to be 1440 x 900
[   662.410] (--) NVIDIA(0): DPI set to (98, 99); computed from "UseEdidDpi" X config
[   662.410] (--) NVIDIA(0):     option
[   662.410] (==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
[   662.410] (--) Depth 24 pixmap format is 32 bpp
[   662.410] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[   662.411] (II) NVIDIA(0): Initialized GPU GART.
[   662.416] (II) NVIDIA(0): ACPI display change hotkey events enabled: the X server is new
[   662.416] (II) NVIDIA(0):     enough to receive ACPI hotkey events.
[   662.417] (II) NVIDIA(0): ACPI brightness change hotkey events enabled.
[   662.419] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[   662.718] (II) Loading extension NV-GLX
[   662.747] (II) NVIDIA(0): Initialized OpenGL Acceleration
[   662.761] (==) NVIDIA(0): Disabling shared memory pixmaps
[   662.761] (II) NVIDIA(0): Initialized X Rendering Acceleration
[   662.761] (==) NVIDIA(0): Backing store disabled
[   662.761] (==) NVIDIA(0): Silken mouse enabled
[   662.776] (**) NVIDIA(0): DPMS enabled
[   662.776] (II) Loading extension NV-CONTROL
[   662.776] (II) Loading extension XINERAMA
[   662.776] (II) Loading sub module "dri2"
[   662.776] (II) LoadModule: "dri2"
[   662.777] (II) Reloading /usr/lib/xorg/modules/extensions/libdri2.so
[   662.777] (II) NVIDIA(0): [DRI2] Setup complete
[   662.777] (==) RandR enabled
[   662.777] (II) Initializing built-in extension Generic Event Extension
[   662.777] (II) Initializing built-in extension SHAPE
[   662.777] (II) Initializing built-in extension MIT-SHM
[   662.777] (II) Initializing built-in extension XInputExtension
[   662.777] (II) Initializing built-in extension XTEST
[   662.777] (II) Initializing built-in extension BIG-REQUESTS
[   662.777] (II) Initializing built-in extension SYNC
[   662.777] (II) Initializing built-in extension XKEYBOARD
[   662.777] (II) Initializing built-in extension XC-MISC
[   662.777] (II) Initializing built-in extension SECURITY
[   662.777] (II) Initializing built-in extension XINERAMA
[   662.777] (II) Initializing built-in extension XFIXES
[   662.777] (II) Initializing built-in extension RENDER
[   662.777] (II) Initializing built-in extension RANDR
[   662.777] (II) Initializing built-in extension COMPOSITE
[   662.777] (II) Initializing built-in extension DAMAGE
[   662.777] (II) Initializing built-in extension GESTURE
[   662.781] (II) Initializing extension GLX
[   662.817] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   662.829] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[   662.829] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   662.829] (II) LoadModule: "evdev"
[   662.830] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   662.830] (II) Module evdev: vendor="X.Org Foundation"
[   662.830]     compiled for 1.9.0, module version = 2.3.2
[   662.830]     Module class: X.Org XInput Driver
[   662.830]     ABI class: X.Org XInput driver, version 11.0
[   662.830] (**) Power Button: always reports core events
[   662.830] (**) Power Button: Device: "/dev/input/event3"
[   662.841] (II) Power Button: Found keys
[   662.841] (II) Power Button: Configuring as keyboard
[   662.841] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[   662.841] (**) Option "xkb_rules" "evdev"
[   662.841] (**) Option "xkb_model" "pc105"
[   662.841] (**) Option "xkb_layout" "gb"
[   662.843] (II) XKB: reuse xkmfile /var/lib/xkb/server-2B4266AA55228AE7D9557A18F1965DBA19850816.xkm
[   662.844] (II) config/udev: Adding input device Video Bus (/dev/input/event9)
[   662.844] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[   662.844] (**) Video Bus: always reports core events
[   662.844] (**) Video Bus: Device: "/dev/input/event9"
[   662.857] (II) Video Bus: Found keys
[   662.857] (II) Video Bus: Configuring as keyboard
[   662.857] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[   662.857] (**) Option "xkb_rules" "evdev"
[   662.857] (**) Option "xkb_model" "pc105"
[   662.857] (**) Option "xkb_layout" "gb"
[   662.859] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[   662.860] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   662.860] (**) Power Button: always reports core events
[   662.860] (**) Power Button: Device: "/dev/input/event1"
[   662.873] (II) Power Button: Found keys
[   662.873] (II) Power Button: Configuring as keyboard
[   662.873] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[   662.873] (**) Option "xkb_rules" "evdev"
[   662.873] (**) Option "xkb_model" "pc105"
[   662.873] (**) Option "xkb_layout" "gb"
[   662.874] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[   662.874] (II) No input driver/identifier specified (ignoring)
[   662.874] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[   662.874] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[   662.874] (**) Sleep Button: always reports core events
[   662.874] (**) Sleep Button: Device: "/dev/input/event2"
[   662.889] (II) Sleep Button: Found keys
[   662.889] (II) Sleep Button: Configuring as keyboard
[   662.889] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[   662.889] (**) Option "xkb_rules" "evdev"
[   662.889] (**) Option "xkb_model" "pc105"
[   662.889] (**) Option "xkb_layout" "gb"
[   662.892] (II) config/udev: Adding input device HID 04d9:048e (/dev/input/event5)
[   662.892] (**) HID 04d9:048e: Applying InputClass "evdev pointer catchall"
[   662.892] (**) HID 04d9:048e: always reports core events
[   662.892] (**) HID 04d9:048e: Device: "/dev/input/event5"
[   662.905] (II) HID 04d9:048e: Found 9 mouse buttons
[   662.905] (II) HID 04d9:048e: Found scroll wheel(s)
[   662.905] (II) HID 04d9:048e: Found relative axes
[   662.905] (II) HID 04d9:048e: Found x and y relative axes
[   662.905] (II) HID 04d9:048e: Configuring as mouse
[   662.905] (**) HID 04d9:048e: YAxisMapping: buttons 4 and 5
[   662.905] (**) HID 04d9:048e: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   662.905] (II) XINPUT: Adding extended input device "HID 04d9:048e" (type: MOUSE)
[   662.905] (II) HID 04d9:048e: initialized for relative axes.
[   662.906] (II) config/udev: Adding input device HID 04d9:048e (/dev/input/mouse0)
[   662.906] (II) No input driver/identifier specified (ignoring)
[   662.912] (II) config/udev: Adding input device Acer Crystal Eye webcam (/dev/input/event10)
[   662.912] (**) Acer Crystal Eye webcam: Applying InputClass "evdev keyboard catchall"
[   662.912] (**) Acer Crystal Eye webcam: always reports core events
[   662.912] (**) Acer Crystal Eye webcam: Device: "/dev/input/event10"
[   662.921] (II) Acer Crystal Eye webcam: Found keys
[   662.921] (II) Acer Crystal Eye webcam: Configuring as keyboard
[   662.921] (II) XINPUT: Adding extended input device "Acer Crystal Eye webcam" (type: KEYBOARD)
[   662.921] (**) Option "xkb_rules" "evdev"
[   662.921] (**) Option "xkb_model" "pc105"
[   662.921] (**) Option "xkb_layout" "gb"
[   662.931] (II) config/udev: Adding input device CHESEN USB Keyboard (/dev/input/event6)
[   662.932] (**) CHESEN USB Keyboard: Applying InputClass "evdev keyboard catchall"
[   662.932] (**) CHESEN USB Keyboard: always reports core events
[   662.932] (**) CHESEN USB Keyboard: Device: "/dev/input/event6"
[   662.945] (II) CHESEN USB Keyboard: Found keys
[   662.945] (II) CHESEN USB Keyboard: Configuring as keyboard
[   662.945] (II) XINPUT: Adding extended input device "CHESEN USB Keyboard" (type: KEYBOARD)
[   662.945] (**) Option "xkb_rules" "evdev"
[   662.945] (**) Option "xkb_model" "pc105"
[   662.945] (**) Option "xkb_layout" "gb"
[   662.946] (II) config/udev: Adding input device CHESEN USB Keyboard (/dev/input/event7)
[   662.946] (**) CHESEN USB Keyboard: Applying InputClass "evdev keyboard catchall"
[   662.946] (**) CHESEN USB Keyboard: always reports core events
[   662.946] (**) CHESEN USB Keyboard: Device: "/dev/input/event7"
[   662.961] (II) CHESEN USB Keyboard: Found keys
[   662.961] (II) CHESEN USB Keyboard: Configuring as keyboard
[   662.961] (II) XINPUT: Adding extended input device "CHESEN USB Keyboard" (type: KEYBOARD)
[   662.961] (**) Option "xkb_rules" "evdev"
[   662.961] (**) Option "xkb_model" "pc105"
[   662.961] (**) Option "xkb_layout" "gb"
[   662.968] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[   662.968] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[   662.968] (**) AT Translated Set 2 keyboard: always reports core events
[   662.968] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[   662.985] (II) AT Translated Set 2 keyboard: Found keys
[   662.985] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[   662.985] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[   662.985] (**) Option "xkb_rules" "evdev"
[   662.985] (**) Option "xkb_model" "pc105"
[   662.985] (**) Option "xkb_layout" "gb"
[   662.986] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event11)
[   662.986] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[   662.986] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[   662.986] (II) LoadModule: "synaptics"
[   662.987] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[   662.987] (II) Module synaptics: vendor="X.Org Foundation"
[   662.987]     compiled for 1.8.99.905, module version = 1.2.2
[   662.987]     Module class: X.Org XInput Driver
[   662.987]     ABI class: X.Org XInput driver, version 11.0
[   662.987] (II) Synaptics touchpad driver version 1.2.2
[   662.987] (**) Option "Device" "/dev/input/event11"
[   663.033] (II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
[   663.033] (II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
[   663.033] (II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[   663.033] (II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
[   663.033] (II) SynPS/2 Synaptics TouchPad: buttons: left right
[   663.065] (--) SynPS/2 Synaptics TouchPad: touchpad found
[   663.065] (**) SynPS/2 Synaptics TouchPad: always reports core events
[   663.081] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[   663.081] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[   663.081] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 0
[   663.081] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[   663.081] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[   663.113] (--) SynPS/2 Synaptics TouchPad: touchpad found
[   663.113] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse2)
[   663.113] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[   663.113] (II) Synaptics touchpad driver version 1.2.2
[   663.709] SynPS/2 Synaptics TouchPad no synaptics event device found
[   663.709] (**) Option "Device" "/dev/input/mouse2"
[   663.745] Query no Synaptics: 6003C8
[   663.745] (--) SynPS/2 Synaptics TouchPad: no supported touchpad found
[   663.745] (EE) SynPS/2 Synaptics TouchPad Unable to query/initialize Synaptics hardware.
[   663.745] (EE) PreInit failed for input device "SynPS/2 Synaptics TouchPad"
[   663.745] (II) UnloadModule: "synaptics"


```I have acceleration and I have 3D ...... happy again .... ;)

I went  back to re-installing the nvidia 256.53 driver in the kernel   -    2.6.35-14-generic

We will see how long I can go and see if Maverick settles down again .... with the graphics .....

It still makes the xserver restart just once after a cold login .... 
it appears to happen when entering a blog edit screen or calling up a console .....

no idea what's causing that yet .......
but it will become apparent ..... soon.

---

