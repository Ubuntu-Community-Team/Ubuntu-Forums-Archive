---
title: "ME-TV and Hauppauge HVR 1600"
date: 2008-10-26
forum: Multimedia Software
---

### Post by sofasurfer on 2008-10-26
Is me-tv supposed to work wiyh Hauppauge hvr 1600 tuner card. I get "invalid channel record in channel.conf" nessage.

---

### Post by elgreek84 on 2008-11-03
I get same thing on Intrepid, I don't know what to do.. sorry

---

### Post by xc3RnbFO8P on 2008-11-03
You could show the output of channel.conf.

---

### Post by sofasurfer on 2008-11-04
When I run ME-TV for the first time I get a message sayng "there is no channel.conf file. Would you like to create one?" I chose to create it. This is my terminal output...

```

daryl@daryl-desktop:~$ me-tv
Me TV-Message: 11/04/2008 23:07:28 - Me TV Version: 0.5.30
Me TV-Message: 11/04/2008 23:07:28 - Loading glade file '/usr/share/me-tv/glade/me-tv.glade'

(me-tv:8267): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(me-tv:8267): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(me-tv:8267): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(me-tv:8267): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(me-tv:8267): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(me-tv:8267): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(me-tv:8267): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
Me TV-Message: 11/04/2008 23:07:28 - Creating EPG file at '/home/daryl/.me-tv/epg.xml'
Me TV-Message: 11/04/2008 23:07:28 - EPG file loaded
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
service is running. Channel number: 19:1. Name: 'WDCQ-DT&#65533;'
service is running. Channel number: 19:2. Name: 'WDCQ-DT&#65533;'
service is running. Channel number: 19:3. Name: 'WDCQ-DT&#65533;'
service is running. Channel number: 19:4. Name: 'WDCQ-DT&#65533;'
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: daryl@daryl-desktop:~$ me-tv
Me TV-Message: 11/04/2008 23:07:28 - Me TV Version: 0.5.30
Me TV-Message: 11/04/2008 23:07:28 - Loading glade file '/usr/share/me-tv/glade/me-tv.glade'

(me-tv:8267): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(me-tv:8267): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(me-tv:8267): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(me-tv:8267): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(me-tv:8267): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(me-tv:8267): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(me-tv:8267): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
Me TV-Message: 11/04/2008 23:07:28 - Creating EPG file at '/home/daryl/.me-tv/epg.xml'
Me TV-Message: 11/04/2008 23:07:28 - EPG file loaded
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
service is running. Channel number: 19:1. Name: 'WDCQ-DT&#65533;'
service is running. Channel number: 19:2. Name: 'WDCQ-DT&#65533;'
service is running. Channel number: 19:3. Name: 'WDCQ-DT&#65533;'
service is running. Channel number: 19:4. Name: 'WDCQ-DT&#65533;'
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
service is running. Channel number: 5:2. Name: 'WNEM Digital Television'
service is running. Channel number: 5:1. Name: 'WNEM HDTV'
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
service is running. Channel number: 25:1. Name: 'WEYI High Def'
service is running. Channel number: 25:2. Name: 'WEYI Digital Television'
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
service is running. Channel number: 12:1. Name: 'WJRT-HD&#65533;'
service is running. Channel number: 12:2. Name: 'WJRT-S1&#65533;o tuA'
service is running. Channel number: 12:3. Name: 'WJRT-S2&#65533;onde1'
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
dumping lists (11 services)

(me-tv:8267): GLib-WARNING **: Invalid UTF-8 passed to g_io_channel_write_chars().
Me TV-Message: Exception message: 'Failed to write to channel: 'Invalid byte sequence in conversion input''
Me TV-Message: 11/04/2008 23:13:31 - Exception in void ScanDialog::scan(): Failed to write to channel: 'Invalid byte sequence in conversion input'
Me TV-Message: 11/04/2008 23:13:31 - Pushing error message onto queue: Failed to write to channel: 'Invalid byte sequence in conversion input'



WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
service is running. Channel number: 5:2. Name: 'WNEM Digital Television'
service is running. Channel number: 5:1. Name: 'WNEM HDTV'
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
service is running. Channel number: 25:1. Name: 'WEYI High Def'
service is running. Channel number: 25:2. Name: 'WEYI Digital Television'
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
service is running. Channel number: 12:1. Name: 'WJRT-HD&#65533;'
service is running. Channel number: 12:2. Name: 'WJRT-S1&#65533;o tuA'
service is running. Channel number: 12:3. Name: 'WJRT-S2&#65533;onde1'
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 
WARNING: >>> tuning failed!!!
>>> tune to:  (tuning failed)
WARNING: >>> tuning failed!!!
dumping lists (11 services)

(me-tv:8267): GLib-WARNING **: Invalid UTF-8 passed to g_io_channel_write_chars().
Me TV-Message: Exception message: 'Failed to write to channel: 'Invalid byte sequence in conversion input''
Me TV-Message: 11/04/2008 23:13:31 - Exception in void ScanDialog::scan(): Failed to write to channel: 'Invalid byte sequence in conversion input'
Me TV-Message: 11/04/2008 23:13:31 - Pushing error message onto queue: Failed to write to channel: 'Invalid byte sequence in conversion input'

```

At this point, channel.conf contain only this...

WDCQ-DT

Now when I run "me-tv"...

```

daryl@daryl-desktop:~$ me-tv
Me TV-Message: 11/04/2008 23:27:21 - Me TV Version: 0.5.30
Me TV-Message: 11/04/2008 23:27:21 - Loading glade file '/usr/share/me-tv/glade/me-tv.glade'

(me-tv:8417): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(me-tv:8417): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(me-tv:8417): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(me-tv:8417): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(me-tv:8417): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(me-tv:8417): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(me-tv:8417): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
Me TV-Message: 11/04/2008 23:27:21 - Creating EPG file at '/home/daryl/.me-tv/epg.xml'
Me TV-Message: 11/04/2008 23:27:21 - EPG file loaded
Me TV-Message: Exception message: 'There's an invalid channel record in the channels.conf file'
Me TV-Message: 11/04/2008 23:27:22 - Exception in void Application::init(): There's an invalid channel record in the channels.conf file


```

And at this point a window comes up saying "There's an invalid channel record in the channels.conf file"

---

### Post by xc3RnbFO8P on 2008-11-05
You got Me-TV Version: 0.5.30
[https://launchpad.net/me-tv]("https://launchpad.net/me-tv")
> Oh, Me TV 0.6 does not support ATSC in its current state. My apologies, this is a bug because Me TV should tell you that it can't use your device rather than trying to parse an ATSC file.
[https://bugs.launchpad.net/me-tv/+bug/283549]("https://bugs.launchpad.net/me-tv/+bug/283549")

---

### Post by sofasurfer on 2008-11-05
So your saying that me-tv won't work for me?

Anyway, just for the heck of it I removed me-tv 5.3 and tried to install me-tv 7. At the end of the ./configure command I get an error. Following are the last few lines of output...

```

checking for SQLITE... configure: error: Package requirements (sqlite3 >= 3.0) were not met:

No package 'sqlite3' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables SQLITE_CFLAGS
and SQLITE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


```

According to synaptic 'sqlite3' is installed. 
How can I fix this error? Or an I for sure wasting my time trying to get me-tv to work?

---

### Post by xc3RnbFO8P on 2008-11-05
Yes, Me-TV doesn't support ATSC. 
Try to install **libsqlite3-dev**

---

### Post by gusman21 on 2008-12-18
> **Ringi said:**
> You got Me-TV Version: 0.5.30
[https://launchpad.net/me-tv]("https://launchpad.net/me-tv")

[https://bugs.launchpad.net/me-tv/+bug/283549]("https://bugs.launchpad.net/me-tv/+bug/283549")

is this still the case?

```

Me TV 0.7.6
12/18/2008 09:24:17: No frontend available
12/18/2008 09:24:17: Me TV terminated

```

---

