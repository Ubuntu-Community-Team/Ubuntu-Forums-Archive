---
title: "Streaming Over Networking Not Working"
date: 2011-01-30
forum: Networking &amp; Wireless
---

### Post by Sugi on 2011-01-30
I am streaming files over my network with auto mounting in fstab, but for some reason just recently multiple files in my playlist doesn't work correctly.  In totem, it will play the first file file, but the next file doesn't start.  It reports the time as 0:00/0:00 and nothing else happens.

Doesn't report any errors or feedback.
>  totem --no-existing-session

(totem:23705): Gtk-CRITICAL **: IA__gtk_tree_view_scroll_to_cell: assertion `tree_view->priv->tree != NULL' failed



Sometimes, I get the following error as well.
> ** Message: Error: Disconnected: Connection terminated
pulsesink.c(290): gst_pulsering_is_dead (): /GstPlayBin2:play/GstPlaySink:playsink0/GstBin:abin/GstBin:audiosinkbin/GstGConfAudioSink:audio-sink/GstBin:bin6/GstAutoAudioSink:autoaudiosink3/GstPulseSink:autoaudiosink3-actual-sink-pulse


In VLC, it reports issues with the playback, it seems to have problems with characters.  It will play for a bit, and then reset to the beginning of the movie without audio.

> VLC media player 1.1.4 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x15d7160] main libvlc: vlc&#12399;&#12487;&#12501;&#12457;&#12523;&#12488;&#12398;&#12452;&#12531;&#12479;&#12540;&#12501;&#12455;&#12540;&#12473;&#12391;&#23455;&#34892;&#12375;&#12390;&#12356;&#12414;&#12377;&#12290;&#12452;&#12531;&#12479;&#12540;&#12501;&#12455;&#12540;&#12473;&#12398;&#12394;&#12356; vlc &#12434;&#20351;&#29992;&#12377;&#12427;&#12395;&#12399;'cvlc'&#12434;&#20351;&#29992;&#12375;&#12390;&#12367;&#12384;&#12373;&#12356;&#12290;
**[The above is just talking about running the default interface.]**
Blocked: call to setlocale(6, "")
Blocked: call to sigaction(17, 0x7f61069edb20, 0x7f61069eda80)
Warning: call to signal(13, 0x1)
Warning: call to signal(13, 0x1)
Warning: call to srand(1296720270)
Warning: call to rand()
Blocked: call to setlocale(6, "")

(process:18625): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
Warning: call to signal(13, 0x1)
Warning: call to signal(13, 0x1)
 m_el[mi_level] == NULL
 arrrrrrrrrrrrrg Up cannot escape itself
 m_el[mi_level] == NULL
 arrrrrrrrrrrrrg Up cannot escape itself
 m_el[mi_level] == NULL
 arrrrrrrrrrrrrg Up cannot escape itself
 m_el[mi_level] == NULL
 arrrrrrrrrrrrrg Up cannot escape itself
 m_el[mi_level] == NULL
 arrrrrrrrrrrrrg Up cannot escape itself
 m_el[mi_level] == NULL
 arrrrrrrrrrrrrg Up cannot escape itself
 m_el[mi_level] == NULL
 arrrrrrrrrrrrrg Up cannot escape itself


Ubuntu 10.10 x64
VLC 1.1.4
Totem 2.32.0
Sugi

---

### Post by Sugi on 2011-01-30
I have finally got an error from totem, but I believe it may not relay any information that is helpful to me. :S

> totem --no-existing-session
Stream with high frequencies VQ coding

Sugi

---

### Post by SeijiSensei on 2011-01-31
What file-sharing method are you using?  I've found NFS offers much better streaming performance than SMB (Samba).

---

### Post by Sugi on 2011-02-01
I am using Samba via auto-mounting within fstab, though this kind of problem did not happen before the auto-mounting.

Sugi

---

### Post by SeijiSensei on 2011-02-01
If the server and client are both running Linux, [NFS]("https://help.ubuntu.com/community/SettingUpNFSHowTo") is a better choice.

---

### Post by Sugi on 2011-02-03
Sadly, my stuff is being stored on a windows base computer.  It's on windows XP. Btw, this didn't happen before the auto-mount.  I misspoke in my last comment.

Sugi

---

### Post by Sugi on 2011-02-06
This error doesn't always pop, but it may be linked to the problem.
```
** Message: Error: Disconnected: Connection terminated
pulsesink.c(290): gst_pulsering_is_dead (): /GstPlayBin2:play/GstPlaySink:playsink0/GstBin:abin/GstBin:audiosinkbin/GstGConfAudioSink:audio-sink/GstBin:bin6/GstAutoAudioSink:autoaudiosink3/GstPulseSink:autoaudiosink3-actual-sink-pulse

```

Sugi

---

### Post by Sugi on 2011-02-07
Bump for this thread.

Sugi

---

