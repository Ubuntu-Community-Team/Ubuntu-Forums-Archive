---
title: "resolution changes by itself after login"
date: 2011-12-01
forum: Multimedia Software
---

### Post by petru.marginean on 2011-12-01
Hi,

I have this problem when using a new monitor:
- I just upgraded the monitor from 1680 x 1050 to 1920 x 1080
- I changed the resolution using nvidia-settings app; it works without any issue
- the new resolution is saved into the /etc/X11/xorg.conf
- the new resolution is fine while I'm logged it
- once I log out (or after I kill X), the resolution is still fine: I can see a sharp image while the login screen is displayed; also I can see in the lofile the resolution doesn't change
- once I re-login the resolution goes back to the old 1680 x 1050, and I can see a fuzzy image

I'm using ubuntu 11.10:

```
$> uname -a
Linux ubuntu 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686 i686 i386 GNU/Linux
```Here you can see how after fresh reboot, the computer uses the new resolution until I login (246 sec below)

```

$> grep Setting /var/log/Xorg.0.log
[   241.422] (II) NVIDIA(0): Setting mode "1920x1080+0+0"
[   246.671] (II) NVIDIA(0): Setting mode "1680x1050"
```There are no errors in the log file (searched for 'EE' pattern etc); still the resolution changes (by itself) when I login:

```
//...
[   241.541] (II) config/udev: Adding input device HDA Intel Headphone (/dev/input/event5)
[   241.541] (II) No input driver/identifier specified (ignoring)
[   246.671] (II) NVIDIA(0): Setting mode "1680x1050"
[   246.902] (II) XKB: reuse xkmfile /var/lib/xkb/server-81EC4871279DB1D73113D19E789F270C19322F52.xkm
```What is causing the resolution to change?!

Here are some parts of the logfile, after killing X.
You can see at the end how the resolution just changes when I login back in (79715 sec):

```

//...
[ 79707.897] (--) NVIDIA(0): Acer G235H (CRT-1): 400.0 MHz maximum pixel clock
[ 79707.940] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID has been
[ 79707.940] (**) NVIDIA(0):     enabled on all display devices.
[ 79707.956] (II) NVIDIA(0): Assigned Display Device: CRT-1
[ 79707.956] (II) NVIDIA(0): Validated modes:
[ 79707.956] (II) NVIDIA(0):     "1920x1080+0+0"
[ 79707.956] (II) NVIDIA(0):     "nvidia-auto-select+0+0"
[ 79707.956] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
[ 79707.980] (--) NVIDIA(0): DPI set to (93, 94); computed from "UseEdidDpi" X config
[ 79707.980] (--) NVIDIA(0):     option
[ 79707.980] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[ 79707.989] (II) NVIDIA(0): Setting mode "1920x1080+0+0"
//...
[ 79708.114] (II) config/udev: Adding input device HDA Intel Headphone (/dev/input/event2)
[ 79708.114] (II) No input driver/identifier specified (ignoring)
[ 79715.125] (II) NVIDIA(0): Setting mode "1680x1050"
[ 79715.524] (II) XKB: reuse xkmfile /var/lib/xkb/server-81EC4871279DB1D73113D19E789F270C19322F52.xkm

```Here is the Screen section in /etc/X11/xorg.conf file:
```
Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    16
    Option         "TwinView" "0"
    Option         "metamodes" "1920x1080 +0+0; nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       16
    EndSubSection
EndSection
```

Please help,
PM

---

### Post by petru.marginean on 2011-12-03
To make sure this is not user related (some setting from the time of the old monitor/resolution was used) I've created a new test user, and tried again.

I see the same behaviour; after login the resolution switches back to 1680x1050, no matter what. If I then switch it back manually to 1920x1080, it works fine as long as I do not logout.

Please help,
PM

---

### Post by BicyclerBoy on 2011-12-03
The nvidia driver is an X server driver only..

It does **not** operate outside of X server session..

When you log out you have stopped the X server & are in plymouth.
A different video (framebuffer) driver is operating.

AFAIK You can set the video mode of plymouth/greeter by settings in grub..

---

### Post by petru.marginean on 2011-12-05
Thanks for reply.

I looked more and figured out there are lots of errors into the ~/.xsession-errors file.
It is possible that because of these errors it is rolling back to the prev resolution.

I believe it did the same even before upgrading the monitor (I don not think the errors are new), but it was rolling back to the same resolution, so it was appearing like working fine...

I'm not sure how to solve all the errors (lots of assertion failures in gnome etc).
For now I gave up and installed... xubuntu. I like it so far, and I'll use it until I'll figure out a way to fix the resolution issue.

Below are the errors in the .xsession-errors file.
Is there a way to fresh install gnome?!

```

$> ls -lh .xsession-errors
-rw------- 1 petrum petrum 71K 2011-12-04 22:31 .xsession-errors

$> cat .xsession-errors
Running X session wrapper
Loading profile from /etc/profile
Loading profile from /home/lori/.profile
Loading resource: /etc/X11/Xresources/x11-common
Loading X session script /etc/X11/Xsession.d/20x11-common_process-args
Loading X session script /etc/X11/Xsession.d/30x11-common_xresources
Loading X session script /etc/X11/Xsession.d/40x11-common_xsessionrc
Loading X session script /etc/X11/Xsession.d/50_check_unity_support
Loading X session script /etc/X11/Xsession.d/50x11-common_determine-startup
Loading X session script /etc/X11/Xsession.d/52libcanberra-gtk3-module_add-to-gtk-modules
Loading X session script /etc/X11/Xsession.d/52libcanberra-gtk-module_add-to-gtk-modules
Loading X session script /etc/X11/Xsession.d/55gnome-session_gnomerc
Loading X session script /etc/X11/Xsession.d/60x11-common_localhost
Loading X session script /etc/X11/Xsession.d/60x11-common_xdg_path
Loading X session script /etc/X11/Xsession.d/60xdg-user-dirs-update
Loading X session script /etc/X11/Xsession.d/65compiz_profile-on-session
Loading X session script /etc/X11/Xsession.d/70gconfd_path-on-session
Loading X session script /etc/X11/Xsession.d/75dbus_dbus-launch
Loading X session script /etc/X11/Xsession.d/80appmenu
Loading X session script /etc/X11/Xsession.d/80appmenu-gtk3
Loading X session script /etc/X11/Xsession.d/80im-switch
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
Loading X session script /etc/X11/Xsession.d/80kubuntu-xmodmap
Loading X session script /etc/X11/Xsession.d/80qtgraphicssystem
Loading X session script /etc/X11/Xsession.d/90consolekit
Loading X session script /etc/X11/Xsession.d/90gpg-agent
Loading X session script /etc/X11/Xsession.d/90qt-a11y
Loading X session script /etc/X11/Xsession.d/90x11-common_ssh-agent
Loading X session script /etc/X11/Xsession.d/99x11-common_start
gnome-session[30097]: WARNING: Unable to find default provider 'notify-osd' of required provider 'notifications'
gnome-session[30097]: WARNING: Failed to start app: Unable to start application: Failed to execute child process "gnome-power-manager" (No such file or directory)
GNOME_KEYRING_CONTROL=/tmp/keyring-cSa8Gt
GPG_AGENT_INFO=/tmp/keyring-cSa8Gt/gpg:0:1
GNOME_KEYRING_CONTROL=/tmp/keyring-cSa8Gt
GPG_AGENT_INFO=/tmp/keyring-cSa8Gt/gpg:0:1
GNOME_KEYRING_CONTROL=/tmp/keyring-cSa8Gt
GPG_AGENT_INFO=/tmp/keyring-cSa8Gt/gpg:0:1
GNOME_KEYRING_CONTROL=/tmp/keyring-cSa8Gt
GPG_AGENT_INFO=/tmp/keyring-cSa8Gt/gpg:0:1
SSH_AUTH_SOCK=/tmp/keyring-cSa8Gt/ssh

(gnome-settings-daemon:30170): color-plugin-WARNING **: failed to get edid: unable to get EDID for output
gnome-session[30097]: WARNING: Unable to parse command from  'file:///etc/xdg/autostart/synaptiks_init_config.desktop': Key file contains key 'Terminal' which has value that cannot be interpreted.
gnome-session[30097]: WARNING: Failed to start app: Unable to start application: Key file contains key 'Terminal' which has value that cannot be interpreted.
** (gnome-fallback-mount-helper:30206): DEBUG: Starting automounting manager
** (nautilus:30209): DEBUG: Syncdaemon not running, waiting for it to start in NameOwnerChanged
** (gnome-fallback-mount-helper:30206): DEBUG: Found ConsoleKit session at path /org/freedesktop/ConsoleKit/Session38
** (gnome-fallback-mount-helper:30206): DEBUG: ScreenSaver name appeared
** (gnome-fallback-mount-helper:30206): DEBUG: ScreenSaver proxy ready
** (gnome-fallback-mount-helper:30206): DEBUG: Screensaver GetActive() returned 0
** (gnome-fallback-mount-helper:30206): DEBUG: ConsoleKit session is active 1
Initializing nautilus-gdu extension
** Message: applet now removed from the notification area
** (nm-applet:30205): DEBUG: old state indicates that this was not a disconnect 0
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/blueman/plugins/BasePlugin.py", line 65, in _load
    self.on_load(parent)
  File "/usr/lib/python2.7/dist-packages/blueman/plugins/applet/PulseAudio.py", line 173, in on_load
    raise Exception("PulseAudio too old, required 0.9.15 or higher")
Exception: PulseAudio too old, required 0.9.15 or higher
** Message: using fallback from indicator to GtkStatusIcon

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_image_menu_item_set_always_show_image: assertion `GTK_IS_IMAGE_MENU_ITEM (image_menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_image_menu_item_set_always_show_image: assertion `GTK_IS_IMAGE_MENU_ITEM (image_menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_image_menu_item_set_always_show_image: assertion `GTK_IS_IMAGE_MENU_ITEM (image_menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_image_menu_item_set_always_show_image: assertion `GTK_IS_IMAGE_MENU_ITEM (image_menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_image_menu_item_set_always_show_image: assertion `GTK_IS_IMAGE_MENU_ITEM (image_menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_image_menu_item_set_always_show_image: assertion `GTK_IS_IMAGE_MENU_ITEM (image_menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_image_menu_item_set_always_show_image: assertion `GTK_IS_IMAGE_MENU_ITEM (image_menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_image_menu_item_set_always_show_image: assertion `GTK_IS_IMAGE_MENU_ITEM (image_menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_image_menu_item_set_always_show_image: assertion `GTK_IS_IMAGE_MENU_ITEM (image_menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_image_menu_item_set_always_show_image: assertion `GTK_IS_IMAGE_MENU_ITEM (image_menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_image_menu_item_set_always_show_image: assertion `GTK_IS_IMAGE_MENU_ITEM (image_menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_image_menu_item_set_always_show_image: assertion `GTK_IS_IMAGE_MENU_ITEM (image_menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_image_menu_item_set_always_show_image: assertion `GTK_IS_IMAGE_MENU_ITEM (image_menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_image_menu_item_set_always_show_image: assertion `GTK_IS_IMAGE_MENU_ITEM (image_menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_image_menu_item_set_always_show_image: assertion `GTK_IS_IMAGE_MENU_ITEM (image_menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_image_menu_item_set_always_show_image: assertion `GTK_IS_IMAGE_MENU_ITEM (image_menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_image_menu_item_set_always_show_image: assertion `GTK_IS_IMAGE_MENU_ITEM (image_menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_image_menu_item_set_always_show_image: assertion `GTK_IS_IMAGE_MENU_ITEM (image_menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_image_menu_item_set_always_show_image: assertion `GTK_IS_IMAGE_MENU_ITEM (image_menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_image_menu_item_set_always_show_image: assertion `GTK_IS_IMAGE_MENU_ITEM (image_menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_image_menu_item_set_always_show_image: assertion `GTK_IS_IMAGE_MENU_ITEM (image_menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_image_menu_item_set_always_show_image: assertion `GTK_IS_IMAGE_MENU_ITEM (image_menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_image_menu_item_set_always_show_image: assertion `GTK_IS_IMAGE_MENU_ITEM (image_menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_image_menu_item_set_always_show_image: assertion `GTK_IS_IMAGE_MENU_ITEM (image_menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_image_menu_item_set_always_show_image: assertion `GTK_IS_IMAGE_MENU_ITEM (image_menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_image_menu_item_set_always_show_image: assertion `GTK_IS_IMAGE_MENU_ITEM (image_menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_image_menu_item_set_always_show_image: assertion `GTK_IS_IMAGE_MENU_ITEM (image_menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_image_menu_item_set_always_show_image: assertion `GTK_IS_IMAGE_MENU_ITEM (image_menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_image_menu_item_set_always_show_image: assertion `GTK_IS_IMAGE_MENU_ITEM (image_menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_image_menu_item_set_always_show_image: assertion `GTK_IS_IMAGE_MENU_ITEM (image_menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_image_menu_item_set_always_show_image: assertion `GTK_IS_IMAGE_MENU_ITEM (image_menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_image_menu_item_set_always_show_image: assertion `GTK_IS_IMAGE_MENU_ITEM (image_menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_image_menu_item_set_always_show_image: assertion `GTK_IS_IMAGE_MENU_ITEM (image_menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_image_menu_item_set_always_show_image: assertion `GTK_IS_IMAGE_MENU_ITEM (image_menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_image_menu_item_set_always_show_image: assertion `GTK_IS_IMAGE_MENU_ITEM (image_menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_image_menu_item_set_always_show_image: assertion `GTK_IS_IMAGE_MENU_ITEM (image_menu_item)' failed

(gnome-panel:30193): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.30.0/./gobject/gsignal.c:2295: signal `size_request' is invalid for instance `0x95f9638'
** Message: applet now embedded in the notification area

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_menu_shell_insert: assertion `GTK_IS_MENU_SHELL (menu_shell)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_menu_shell_insert: assertion `GTK_IS_MENU_SHELL (menu_shell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_menu_shell_insert: assertion `GTK_IS_MENU_SHELL (menu_shell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_widget_get_parent: assertion `GTK_IS_WIDGET (widget)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_menu_shell_insert: assertion `GTK_IS_MENU_SHELL (menu_shell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_menu_shell_insert: assertion `GTK_IS_MENU_SHELL (menu_shell)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_menu_shell_insert: assertion `GTK_IS_MENU_SHELL (menu_shell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_menu_shell_insert: assertion `GTK_IS_MENU_SHELL (menu_shell)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_menu_shell_insert: assertion `GTK_IS_MENU_SHELL (menu_shell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_widget_get_parent: assertion `GTK_IS_WIDGET (widget)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_image_menu_item_set_always_show_image: assertion `GTK_IS_IMAGE_MENU_ITEM (image_menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_widget_get_parent: assertion `GTK_IS_WIDGET (widget)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_widget_get_parent: assertion `GTK_IS_WIDGET (widget)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): LIBDBUSMENU-GLIB-CRITICAL **: dbusmenu_server_set_root: assertion `DBUSMENU_IS_MENUITEM(root)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_image_menu_item_set_always_show_image: assertion `GTK_IS_IMAGE_MENU_ITEM (image_menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_widget_get_parent: assertion `GTK_IS_WIDGET (widget)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_widget_get_parent: assertion `GTK_IS_WIDGET (widget)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_image_menu_item_set_always_show_image: assertion `GTK_IS_IMAGE_MENU_ITEM (image_menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_widget_get_parent: assertion `GTK_IS_WIDGET (widget)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_widget_get_parent: assertion `GTK_IS_WIDGET (widget)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_image_menu_item_set_always_show_image: assertion `GTK_IS_IMAGE_MENU_ITEM (image_menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_widget_get_parent: assertion `GTK_IS_WIDGET (widget)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_widget_get_parent: assertion `GTK_IS_WIDGET (widget)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_image_menu_item_set_always_show_image: assertion `GTK_IS_IMAGE_MENU_ITEM (image_menu_item)' failed
** (process:30286): DEBUG: Telepathy Indicator started

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_widget_get_parent: assertion `GTK_IS_WIDGET (widget)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_widget_get_parent: assertion `GTK_IS_WIDGET (widget)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_image_menu_item_set_always_show_image: assertion `GTK_IS_IMAGE_MENU_ITEM (image_menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_widget_get_parent: assertion `GTK_IS_WIDGET (widget)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_widget_get_parent: assertion `GTK_IS_WIDGET (widget)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_image_menu_item_set_always_show_image: assertion `GTK_IS_IMAGE_MENU_ITEM (image_menu_item)' failed

** (gnome-screensaver:30287): WARNING **: screensaver already running in this session

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_widget_get_parent: assertion `GTK_IS_WIDGET (widget)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_widget_get_parent: assertion `GTK_IS_WIDGET (widget)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error Permission denied
You do not have permission to create a usershare. Ask your administrator to grant you permissions to create a share.


(nautilus:30209): Gtk-CRITICAL **: gtk_image_menu_item_set_always_show_image: assertion `GTK_IS_IMAGE_MENU_ITEM (image_menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_widget_get_parent: assertion `GTK_IS_WIDGET (widget)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_widget_get_parent: assertion `GTK_IS_WIDGET (widget)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_image_menu_item_set_always_show_image: assertion `GTK_IS_IMAGE_MENU_ITEM (image_menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_widget_get_parent: assertion `GTK_IS_WIDGET (widget)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_widget_get_parent: assertion `GTK_IS_WIDGET (widget)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_image_menu_item_set_always_show_image: assertion `GTK_IS_IMAGE_MENU_ITEM (image_menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_widget_get_parent: assertion `GTK_IS_WIDGET (widget)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_widget_get_parent: assertion `GTK_IS_WIDGET (widget)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:30209): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:30209): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed
No bp log location saved, using default.
[000:016] Browser XEmbed support present: 1
[000:017] Browser toolkit is Gtk2.
[000:017] Using Gtk2 toolkit
[000:020] Warning(clientchannel.cc:525): Unreadable or no port file.  Could not initiate GoogleTalkPlugin connection
[000:020] Warning(clientchannel.cc:380): Could not initiate GoogleTalkPlugin connection
[000:021] Warning(optionsfile.cc:23): Load: Could not open file, err=2
[000:021] Failed to get flute install path. Trying default.
[000:023] Started GoogleTalkPlugin, path=/opt/google/talkplugin/GoogleTalkPlugin
[000:023] Waiting for GoogleTalkPlugin to start...
[001:119] Read port file, port=42541
[001:120] Initiated connection to GoogleTalkPlugin
[001:221] Socket connection established
[001:221] ScheduleOnlineCheck: Online check in 5000ms
[001:320] Got cookie response, socket is authorized
[001:320] AUTHORIZED; socket handshake complete
** (nautilus:30209): DEBUG: Got notification of SyncDaemon startup in NameOwnerChanged
[006:231] HandleOnlineCheck: Starting check
[006:231] HandleOnlineCheck: OK; current state: 3

(gnome-settings-daemon:30170): GLib-CRITICAL **: g_variant_get_int32: assertion `g_variant_is_of_type (value, G_VARIANT_TYPE_INT32)' failed

(check-new-release-gtk:30492): Gtk-WARNING **: Unknown property: GtkMessageDialog.has-separator
WARNING:root:timeout reached, exiting
** (deja-dup-monitor:30544): DEBUG: monitor.vala:221: Automatic backups disabled.  Not scheduling a backup.
[237:560] Error(scriptinterface.cc:284): Passed a non-object for onmessasge_callback
method return sender=:1.9 -> dest=:1.990 reply_serial=2
** (gnome-fallback-mount-helper:30206): DEBUG: ConsoleKit session is active 0
** (gnome-fallback-mount-helper:30206): DEBUG: Screensaver active changed to 1
** (gnome-fallback-mount-helper:30206): DEBUG: Volume 0x80f3ec0 removed, removing from the queue
** (deja-dup-monitor:30544): DEBUG: monitor.vala:221: Automatic backups disabled.  Not scheduling a backup.
gnome-session[30097]: Gdk-WARNING: gnome-session: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.


(gnome-settings-daemon:30170): Gdk-WARNING **: gnome-settings-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.

g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.
g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.
g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.
g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.
Loading configuration plugins
blueman-applet version 1.22 starting
Using gconf config backend
Using gconf config backend
Using gconf config backend
Using gconf config backend
Using gconf config backend
Using gconf config backend
Using gconf config backend
Using gconf config backend
Using gconf config backend
Using gconf config backend
Using gconf config backend
Deleting plugin instance <blueman.plugins.applet.PulseAudio.PulseAudio object at 0xa10db0c>
Using gconf config backend
g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.
Has notifications support True
rename failed
Loading...
Connecting to daemon...
Connected.
displaytray True
Done loading.
g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.
g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.
g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.
** (process:30374): DEBUG: zeitgeist-datahub.vala:58: Zeitgeist-daemon disappeared from the bus, exitting...

** (process:30374): WARNING **: zeitgeist-datahub.vala:218: Unable to get name "org.gnome.zeitgeist.datahub" on the bus!
g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.
g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.
g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.
g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.
** Message: PID 30205 (we are 30205) sent signal 15, shutting down...

(nm-applet:30205): libappindicator-WARNING **: Unable to send signal for NewStatus: The connection is closed
** Message: moving back from GtkStatusIcon to indicator

(nm-applet:30205): Gtk-CRITICAL **: gtk_status_icon_set_visible: assertion `GTK_IS_STATUS_ICON (status_icon)' failed
g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.
(evolution-alarm-notify:30418): libecal-DEBUG: GDBus connection is closed, remote peer vanished: Underlying GIOStream returned 0 bytes on an async read
(evolution-alarm-notify:30418): libecal-DEBUG: e-cal-client.c:359: ECalClient GDBus connection is closed, remote peer vanished: Underlying GIOStream returned 0 bytes on an async read
(evolution-alarm-notify:30418): libecal-DEBUG: e-cal-client.c:359: ECalClient GDBus connection is closed, remote peer vanished: Underlying GIOStream returned 0 bytes on an async read
(evolution-alarm-notify:30418): libecal-DEBUG: e-cal-client.c:359: ECalClient GDBus connection is closed, remote peer vanished: Underlying GIOStream returned 0 bytes on an async read
(evolution-alarm-notify:30418): libecal-DEBUG: e-cal-client.c:359: ECalClient GDBus connection is closed, remote peer vanished: Underlying GIOStream returned 0 bytes on an async read
g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.
Window manager warning: Fatal IO error 104 (Connection reset by peer) on display ':1'.

(gdu-notification-daemon:30336): Gdk-WARNING **: gdu-notification-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.


```

---

### Post by endian675 on 2012-05-15
Hi Petru, I'm having exactly the same issue.  Did you ever resolve it, other than to install XUbuntu?

EDIT:  I've just resolved it.  In the file ~/.config/monitors.xml the old resolution details were still present (1680x1050).  Changing those to 1920x1200 allowed me to login.  Nasty!

---

### Post by petru.marginean on 2012-07-17
yes, my issue was the script:
```

$> cat /usr/share/lightdmxrandr.sh 
#!/bin/sh  xrandr --size 1680x1050

``` that was invoked after login by lightdm, had hard-coded the wrong resolution.
```

$> cat /etc/lightdm/lightdm.conf  
//...
display-setup-script=/usr/share/lightdmxrandr.sh

```I was able to track this by checking the log:
```
/var/log/lightdm/lightdm.log
```Regards,
PM

---

### Post by petru.marginean on 2012-07-17
Closing this issue.

---

