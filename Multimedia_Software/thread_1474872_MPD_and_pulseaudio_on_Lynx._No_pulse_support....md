---
title: "MPD and pulseaudio on Lynx. No pulse support..."
date: 2010-05-06
forum: Multimedia Software
---

### Post by Method X on 2010-05-06
Good day, everybody

I have a problem don't know what to do. Tired of googling.
I upgraded to 10.04 from 9.10. After that i'm not able to use mpd. I configured pulseaudio, so everything on my system use it. Everything ok, but not mpd. And i need pulseaudio for it. If i type:
> mpd --version it says it has support only for fifo, null and oss output. Pulseaudio doesn't work. Tracks are paused when trying to play. Hope, somebody will help me with it.

I use mpd 0.15.9.

Thanks

---

### Post by tekknokrat on 2010-05-07
See this thread for some solutions/workarounds of your issue: 

[http://ubuntuforums.org/showthread.php?p=8926858#post8926858](http://ubuntuforums.org/showthread.php?p=8926858#post8926858)

Would be great if further discussion of your goes into this thread.
Hope that helps.

Best,
Gunnar

---

### Post by Method X on 2010-05-08
Thank you.
But I still can't use pulse output in mpd.

If it can help, i can show output of log file:

```
May 08 03:24 : player_thread: problems opening audio device while playing "Amon Tobin/Foley Room/03.Amon Tobin - Keep Your Distance.m4a"
May 08 03:24 : output: Failed to enable "My Pulse Output" [pulse]: pa_context_new() has failed
```

---

### Post by tekknokrat on 2010-05-08
Can you provide output of mpd.conf (espc. the output config) 
and from command: "pactl stat" (esp. sink output)

Do you plan to use mpd with or without X? 

The thread [http://ubuntuforums.org/showthread.php?p=8926858#post8926858](http://ubuntuforums.org/showthread.php?p=8926858#post8926858) describes usage without X and enabling systemwide config (using system.pa). 
For myself I use pulseaudio usermode (default.pa) and on yesterdays testing with 10.04 and sytemmode I noticed issues with the config described.

---

### Post by Method X on 2010-05-08
1. Ok. Here is pulse output in mpd.conf, as i want it to work:

```
audio_output {
        type            "pulse"
        name            "My Pulse Output"
        server          "127.0.0.1"             # optional
        sink            "alsa_input.pci-0000_00_1b.0.analog-stereo"     # optional
}

```

But it doesn't work. If i try to play track, it is paused.

This config works:

```
audio_output {
type "ao"
driver "esd"
options "host=127.0.0.1:16001"
name "esd"
}
```
But tracks changes too slow.

2.pactl stat output:

```
Currently in use: 285 blocks containing 866.7 KiB bytes total.
Allocated during whole lifetime: 128053 blocks containing 441.1 MiB bytes total.
Sample cache size: 0 B
User name: methodx
Host Name: Thinkpad
Server Name: pulseaudio
Server Version: 0.9.21-63-gd3efa-dirty
Default Sample Specification: s16le 2ch 44100Hz
Default Channel Map: front-left,front-right
Default Sink: alsa_output.pci-0000_00_1b.0.analog-stereo
Default Source: alsa_input.pci-0000_00_1b.0.analog-stereo
Cookie: 38208eab

```

3.About mpd in X.
I think with X :)


4. Big thanks for your help.
B.t.w., maybe its better to reinstall lucid? (I know, I'm crazy).


P.S.: mpd --version output:

```
`Supported decoders:

[audiofile] wav au aiff aif
[faad] aac

Supported outputs:

null fifo oss 

Supported protocols:

file:// 

```

Maybe its not pulse problem?

---

### Post by tekknokrat on 2010-05-08
Hi,

you should use the sink instead of the source in mpd.conf:

instead of:

alsa_input.pci-0000_00_1b.0.analog-stereo

use:

alsa_output.pci-0000_00_1b.0.analog-stereo

Please also enable the tcp module, like described in the other thread,either with adding that to default.pa or with enabling it via paprefs. paprefs can be installed through synaptic/aptitude/apt-get. 

You should also try to copy the cookie. Don't know if that was necessary for user session. Check that mpd is added to pulse-access.

Please publish the output of /var/log/mpd/mpd.log and /var/log/syslog (the lines with pulse) if none of this works. We'll get that work ;)

---

### Post by Method X on 2010-05-08
Ok, thank you.

Changed input to output. No sound, just pause.

Output of var/log/mpd/mpd.log:
```
May 08 22:37 : output: Failed to enable "My Pulse Output" [pulse]: pa_context_new() has failed
May 08 22:37 : player_thread: problems opening audio device while playing "Aphex Twin/I Care Because You Do/03.Aphex Twin - Wax The Nip.m4a"
May 08 22:37 : output: Failed to enable "My Pulse Output" [pulse]: pa_context_new() has failed
May 08 22:37 : player_thread: problems opening audio device while playing "Aphex Twin/I Care Because You Do/10.Aphex Twin - Alberto Balsalm.m4a"
May 08 22:39 : output: Failed to enable "My Pulse Output" [pulse]: pa_context_new() has failed
May 08 22:39 : player_thread: problems opening audio device while playing "Aphex Twin/I Care Because You Do/07.Aphex Twin - Start As You Mean To Go On.m4a"
May 08 22:39 : output: Failed to enable "My Pulse Output" [pulse]: pa_context_new() has failed
May 08 22:39 : player_thread: problems opening audio device while playing "Aphex Twin/I Care Because You Do/05.Aphex Twin - Ventolin (Video Version).m4a"
May 08 22:39 : output: Failed to enable "My Pulse Output" [pulse]: pa_context_new() has failed
May 08 22:39 : player_thread: problems opening audio device while playing "Aphex Twin/I Care Because You Do/03.Aphex Twin - Wax The Nip.m4a"
May 08 22:39 : output: Failed to enable "My Pulse Output" [pulse]: pa_context_new() has failed
May 08 22:39 : player_thread: problems opening audio device while playing "Aphex Twin/I Care Because You Do/04.Aphex Twin - Icct Hedral (Edit).m4a"
May 08 22:39 : output: Failed to enable "My Pulse Output" [pulse]: pa_context_new() has failed
May 08 22:39 : player_thread: problems opening audio device while playing "Aphex Twin/I Care Because You Do/10.Aphex Twin - Alberto Balsalm.m4a"
May 08 22:39 : output: Failed to enable "My Pulse Output" [pulse]: pa_context_new() has failed
May 08 22:39 : player_thread: problems opening audio device while playing "Aphex Twin/I Care Because You Do/07.Aphex Twin - Start As You Mean To Go On.m4a"
May 08 22:39 : output: Failed to enable "My Pulse Output" [pulse]: pa_context_new() has failed
May 08 22:39 : player_thread: problems opening audio device while playing "Aphex Twin/I Care Because You Do/07.Aphex Twin - Start As You Mean To Go On.m4a"
May 08 22:39 : output: Failed to enable "My Pulse Output" [pulse]: pa_context_new() has failed
May 08 22:39 : player_thread: problems opening audio device while playing "Aphex Twin/I Care Because You Do/07.Aphex Twin - Start As You Mean To Go On.m4a"

```

2. /var/log/syslog :

```
May  8 22:33:15 Thinkpad pulseaudio[3270]: module-alsa-card.c: Failed to find a working profile.
May  8 22:33:15 Thinkpad pulseaudio[3270]: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="29" name="platform-thinkpad_acpi" card_name="alsa_card.platform-
thinkpad_acpi" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.
May  8 22:33:16 Thinkpad gdm-simple-greeter[3329]: Gtk-WARNING: /build/buildd/gtk+2.0-2.20.0/gtk/gtkwidget.c:5636: widget not within a GtkWindow
May  8 22:33:19 Thinkpad bonobo-activation-server (methodx-3336): could not associate with desktop session: Failed to connect to socket /tmp/dbus-U59bGiaraz: Connection refused
May  8 22:33:21 Thinkpad gdm-session-worker[3330]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
May  8 22:33:25 Thinkpad pulseaudio[3270]: module-alsa-card.c: Failed to find a working profile.
May  8 22:33:25 Thinkpad pulseaudio[3270]: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="29" name="platform-thinkpad_acpi" card_name="alsa_card.platform-
thinkpad_acpi" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.
May  8 22:33:25 Thinkpad pulseaudio[3270]: module-alsa-card.c: Failed to find a working profile.
May  8 22:33:25 Thinkpad pulseaudio[3270]: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="29" name="platform-thinkpad_acpi" card_name="alsa_card.platform-
thinkpad_acpi" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.
.....
May  8 22:37:08 Thinkpad pulseaudio[4096]: socket-server.c: bind(): Address already in use
May  8 22:37:08 Thinkpad pulseaudio[4096]: socket-server.c: bind(): Address already in use
May  8 22:37:08 Thinkpad pulseaudio[4096]: module.c: Failed to load  module "module-native-protocol-tcp" (argument: "auth-anonymous=1"): initialization failed.
May  8 22:37:08 Thinkpad pulseaudio[4096]: module-gconf.c: pa_module_load() failed
May  8 22:38:34 Thinkpad pulseaudio[4096]: ratelimit.c: 1074 events suppressed
May  8 22:38:46 Thinkpad pulseaudio[4096]: ratelimit.c: 1932 events suppressed


```
Doesn't work :(

Cookie copied.



ALSO look at it:

> root@Thinkpad:/home/methodx# pulseaudio --system
W: main.c: Running in system mode, but --disallow-exit not set!
W: main.c: Running in system mode, but --disallow-module-loading not set!
N: main.c: Running in system mode, forcibly disabling SHM mode!
N: main.c: Running in system mode, forcibly disabling exit idle time!
W: main.c: OK, so you are running PA in system mode. Please note that you most likely shouldn't be doing that.
W: main.c: If you do it nonetheless then it's your own fault if things don't work as expected.
W: main.c: Please read [http://pulseaudio.org/wiki/WhatIsWrongWithSystemMode](http://pulseaudio.org/wiki/WhatIsWrongWithSystemMode) for an explanation why system mode is usually a bad idea.
W: module.c: module-detect is deprecated: Please use module-udev-detect instead of module-detect!
E: module-protocol-stub.c: Failed to parse module arguments
E: module.c: Failed to load  module "module-native-protocol-tcp" (argument: "add auth-anonymous=1"): initialization failed.
E: main.c: Module load failed.
E: main.c: Failed to initialize daemon.


---

### Post by tekknokrat on 2010-05-08
OK, your logfile output looks promising!

First lets keep with the session mode so only pulse default.pa please.

```
May  8 22:37:08 Thinkpad pulseaudio[4096]: socket-server.c: bind(): Address already in use

```
The line above indicates that another instance is already running so you need to destroy former pulseaudio daemon with ```
killall pulseaudio
```

1. If you have also in default.pa:

```
module-native-protocol-tcp add auth-anonymous
```

change this to:

```
module-native-protocol-tcp
```

If you have copied the cookie and changed the owner (chown pulse: /var/lib/mpd/.pulse-cookie) the auth-anonymous is not necessary (btw. "add" was not part of the syntax, i removed that from the codeblock).

2. Restart X
Ctrl+Alt+F1 for Shell and ```
/etc/init.d/gdm/restart
```

3. Restart mpd

---

### Post by Method X on 2010-05-08
Same result.
Don't know, will it help, but when i restart mpd (/etc/init.d/mpd restart) i can see some protocols blinking in pulseaudio manager->clients.
Native client (unix socket) or Alsa plugin [mpd]

Just blinking.
If i play throug ao - it shpws libao.

Also, output of pulseaudio -vvv have this (in red):

> E: module-alsa-card.c: Failed to find a working profile.
E: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="29" name="platform-thinkpad_acpi" card_name="alsa_card.platform-thinkpad_acpi" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.
...
...
E: module.c: Failed to load  module "module-esound-protocol-unix" (argument: ""): initialization failed.
E: main.c: Module load failed.
E: main.c: Failed to initialize daemon.


---

### Post by tekknokrat on 2010-05-10
Hi,

please remove the esound pulse modules. They shouldn't be used and they 
prevent other modules from loading.

Then perform a test with my default.pa.

Just replace it with 

```

gunzip ~/default.pa.gz -c | sudo tee /etc/pulse/default.pa

```

and restart gdm && mpd.

---

### Post by Method X on 2010-05-10
Woohoo!
It works. Thank you!
But...a small problem now...it crashes when i try to play aac (m4a) files...and no /var/log/mpd/mpd.log info....

---

### Post by tekknokrat on 2010-05-10
Nice that it finally works for you! 
What were your last steps regarding that issue?

Regarding the problem with aac playing, this is already known and discussed here: [https://bugs.launchpad.net/ubuntu/+source/mpd/+bug/519787](https://bugs.launchpad.net/ubuntu/+source/mpd/+bug/519787) 

Just curious, is package libavcodec52 installed as dependency?

Otherwise it seems, like you need to wait for a package upgrade to mpd-0.15-6 / libavcode52-0.5+svn20091129-0.0 :-\"
or try to build yourself or gather the packages from somewhere else (can cause other issues!!!).

---

### Post by Method X on 2010-05-10
Thank you.
:)
Will try to do anything with it.

---

### Post by Method X on 2010-05-10
Problem solved.
I installed early version of mpd from karmic.
:guitar:

---

