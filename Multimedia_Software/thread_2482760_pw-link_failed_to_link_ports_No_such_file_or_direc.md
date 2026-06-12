---
title: "pw-link failed to link ports: No such file or directory"
date: 2023-01-10
forum: Multimedia Software
---

### Post by breaker-of-stone on 2023-01-10
I'm attempting a project that will play single channel audio clips on any of a set of USB audio adapters, with each clip starting independently and sometimes overlapping clips played on other channels / adapters.  The theory we have is that every channel gets declared as a virtual, single-channel device i.e. FL separate from FR and so on.

We achieved this in a demo, and now having difficulty re-creating the setup because pw-link is giving [FONT=courier new]No such file or directory[/FONT] errors, e.g.:
[SIZE=2][FONT=courier new]
$ PIPEWIRE_DEBUG=3 pw-link chan1:monitor_1 alsa_output.usb-Plugable_Plugable_USB_Audio_Device_000000000000-00.analog-stereo:monitor_FL
...
[I][02626.747050] mod.protocol-native | [  local-socket.c:   91 try_connect()] connecting to 'pipewire-0' runtime_dir:/run/user/1000
failed to link ports: No such file or directory

PIPEWIRE_DEBUG=3 pw-link -d 84
...
[I][00697.434136] mod.protocol-native | [  local-socket.c:   91 try_connect()] connecting to 'pipewire-0' runtime_dir:/run/user/1000
failed to unlink ports: No such file or directory
[SIZE=1][FONT=arial]
Context:
Ubuntu 22.04 (Jammy) Desktop distro on a Raspberry Pi 4B
Swapped out pipewire-media-session, replaced it with wireplumber.

pipewire.service, pipewire.socket and wireplumber.service are all loaded and active, no recent errors on any of the journals

pactl creates module/ virtual devices:

[SIZE=2][FONT=courier new]pactl load-module module-null-sink sink_name=chan1 object.linger=1 media.class=Audio/Sink channel_map=FL
536870913
noisebin@rpi:~$ pw-link -Iol
...
  64 alsa_output.usb-Plugable_Plugable_USB_Audio_Device_000000000000-00.analog-stereo:monitor_FL
...
  84 chan1:monitor_1[/FONT][/SIZE]
[/FONT][/SIZE]

ls -l $XDG_RUNTIME_DIR
total 0
srw-rw-rw- 1 noisebin noisebin   0 Jan 10 09:44 bus
drwx------ 3 noisebin noisebin  60 Jan 10 09:44 dbus-1
drwx------ 2 noisebin noisebin  60 Jan 10 09:44 dconf
dr-x------ 2 noisebin noisebin   0 Jan  1  1970 doc
drwx------ 2 noisebin noisebin 140 Jan 10 09:44 gnupg
dr-x------ 2 noisebin noisebin   0 Jan 10 09:44 gvfs
drwx------ 2 noisebin noisebin  40 Jan 10 09:44 gvfsd
srw-rw-rw- 1 noisebin noisebin   0 Jan 10 09:44 pipewire-0
-rw-rw---- 1 noisebin noisebin   0 Jan 10 09:44 pipewire-0.lock
srw-rw-rw- 1 noisebin noisebin   0 Jan 10 09:44 pk-debconf-socket
drwx------ 2 noisebin noisebin  80 Jan 10 09:44 pulse
srw-rw-rw- 1 noisebin noisebin   0 Jan 10 09:44 snapd-session-agent.socket
drwx------ 3 noisebin noisebin  60 Jan 10 09:44 snap.snapd-desktop-integration
drwxr-xr-x 5 noisebin noisebin 140 Jan 10 12:54 systemd

looking at the journals tells me the services are having permission or resource limit errors:[/FONT][/SIZE][INDENT][FONT=monospace]vi /etc/systemd/system/wireplumber.service

add:
[Service]
Environment=WIREPLUMBER_DEBUG=D

systemctl --user status wireplumber.service
&#9679; wireplumber.service - Multimedia Service Session Manager
     Loaded: loaded (/usr/lib/systemd/user/wireplumber.service; enabled; vendor preset: enabled)
     Active: active (running) since Wed 2023-01-11 13:34:13 AWST; 7s ago
   Main PID: 41671 (wireplumber)
      Tasks: 5 (limit: 4102)
     Memory: 6.1M
        CPU: 793ms
     CGroup: /user.slice/user-1000.slice/user@1000.service/session.slice/wireplumber.service
             &#9492;&#9472;41671 /usr/bin/wireplumber

Jan 11 13:34:20 rpi wireplumber[20437]: RTKit error: org.freedesktop.DBus.Error.AccessDenied
Jan 11 13:34:20 rpi wireplumber[20437]: could not make thread 20438 realtime using RTKit: Permission denied
Jan 11 13:34:21 rpi wireplumber[20437]: listen(): Address already in use
Jan 11 13:34:21 rpi wireplumber[20437]: RegisterProfile() failed: org.bluez.Error.NotPermitted
Jan 11 13:34:21 rpi wireplumber[20437]: RegisterProfile() failed: org.bluez.Error.NotPermitted
Jan 11 13:34:21 rpi wireplumber[20437]: <WpSiStandardLink:0xaaaafdd85c00> Failed to create links because of wrong ports
Jan 11 13:34:21 rpi wireplumber[20437]: <WpSiStandardLink:0xaaaafdd85ca0> Failed to create links because of wrong ports

[/FONT]
[/INDENT]
[INDENT][FONT=monospace]
systemctl --user status pipewire.service
&#9679; pipewire.service - PipeWire Multimedia Service
     Loaded: loaded (/usr/lib/systemd/user/pipewire.service; enabled; vendor preset: enabled)
     Active: active (running) since Wed 2023-01-11 13:22:04 AWST; 34min ago
TriggeredBy: &#9679; pipewire.socket
   Main PID: 1610 (pipewire)
      Tasks: 2 (limit: 4102)
     Memory: 8.0M
        CPU: 870ms
     CGroup: /user.slice/user-1000.slice/user@1000.service/session.slice/pipewire.service
             &#9492;&#9472;1610 /usr/bin/pipewire

Jan 11 13:34:21 rpi pipewire[1610]: mod.loopback: error id:3 seq:82 res:-2 (No such file or directory): no node available
Jan 11 13:34:21 rpi pipewire[1610]: mod.loopback: error id:3 seq:82 res:-2 (No such file or directory): no node available
...

systemctl --user status pipewire.socket
&#9679; pipewire.socket - PipeWire Multimedia System Socket
     Loaded: loaded (/usr/lib/systemd/user/pipewire.socket; enabled; vendor preset: enabled)
     Active: active (running) since Wed 2023-01-11 13:22:04 AWST; 35min ago
   Triggers: &#9679; pipewire.service
     Listen: /run/user/1000/pipewire-0 (Stream)
     CGroup: /user.slice/user-1000.slice/user@1000.service/app.slice/pipewire.socket

Jan 11 13:22:04 rpi systemd[1602]: Listening on PipeWire Multimedia System Socket.[/FONT]

[/INDENT]
[SIZE=2][FONT=courier new][SIZE=1][FONT=arial]Ok, any clues?

Attaching:
 * Terminal session with additional diagnostics
 * pipewire service - TRACE level logging
 * wireplumber service - TRACE level debugging
[/FONT][/SIZE]
[/FONT][/SIZE]

---

### Post by breaker-of-stone on 2023-02-04
Update:
Progressed beyond this by fixing permissions for RTkit through polkit, adding the user to audio group because I'm running headless - endless experimentation, however got fed up with the paucity of documentation & support.
pipewire on Ubuntu is clearly premature, and the pace of releases is glacial.

Built a new image with Manjaro.  All working, without any of the weirdness.  Have moved on to new rabbit-hole with python-sounddevice :)

---

