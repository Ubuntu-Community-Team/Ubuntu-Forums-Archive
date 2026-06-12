---
title: "Totem works, Rhythmbox and MythTV don't"
date: 2010-02-18
forum: Multimedia Software
---

### Post by beausoleil on 2010-02-18
I recently switched from Fedora 12 to Ubuntu 9.10 x86-64, and am having problems getting sound working in Rhythmbox and MythTV.

My motherboard is an Gigabyte G33M-S2H with Intel HDA hardware.

alsa-info.sh reports"
> !!ALSA Version
!!------------

Driver version:     1.0.20
Library version:    1.0.20
Utilities version:  1.0.20


!!Loaded ALSA modules
!!-------------------

snd_hda_intel


!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf3400000 irq 22


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
01:00.0 Multimedia video controller: Conexant Systems, Inc. CX23885 PCI Video and Audio Decoder (rev 04)


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:1b.0 0403: 8086:293e (rev 02)
    Subsystem: 1458:a022Rhythmbox is 0.12.5, Totem is 2.28.2, gstreamer is 0.10.25, pulseaudio server is 0.9.19. I've un-muted everything in alsa mixer and pulseaudio volume control, but both it and and the gnome volume control don't show any application when Rhythmbox is playing - but they do show Totem.

Right now I'm trying to concentrate on getting Rhythmbox working before I tackle the audio in MythTV - I figure that will be easy if I get Rhytmbox working first. As a further note, it's definitely not a problem with codecs. I'm listening to a .flac recording of John Mayer right now in Totem, so it's not a problem with non-free codecs like mp3...

I have a real crappy internet connection right now, and searching for similar problems/solutions is tedious at best. Any hints?

I should add that it was "almost" a total initial install - formatted / and /boot partitions, kept /home partition, so I did have some minor problems with UIDs and GIDs...

---

### Post by beausoleil on 2010-02-19
Well, I got mythtv working. One of the audio devices was "[FONT=Courier New]ALSA:plughw:0,3[/FONT]", and changing it to [FONT=Courier New]"ALSA:plughw:0,[/FONT]0" fixed it. (Ok - how do I delete the smilie?)

My ALSA config is [here]("http://www.alsa-project.org/db/?f=3ebbe1e999d78a40ec09fbf141a6425ae220e644") at the alsaproject website

So how do I troubleshoot rhythmbox? I see that it keeps the music library at '~/.local/share/rhythmbox', but where does it store its config? I'm assuming that gstreamer is working fine since totem works fine.

---

### Post by Yellow Pasque on 2010-02-20
Start rhythmbox from the terminal?

---

### Post by beausoleil on 2010-02-22
If I run Rhythmbox from a terminal with the --debug option, it seems to report no problems that I can recognize. When I play a .flac song (gstreamer codec for it is installed - remember that totem and mythtv play them fine), it reports the time ticks like it's playing, but there's no sound. I could post the output here, but it's huge, so here's a snippet where it preps and begins to play:

```
(10:30:24) [0x2276040] [set_state_and_wait] rb-player-gst.c:608: playbin reached state PAUSED
(10:30:24) [0x2276040] [set_state_and_wait] rb-player-gst.c:608: playbin reached state PLAYING
(10:30:24) [0x2276040] [playing_stream_cb] rb-shell-player.c:3429: new playing stream: file:///home/jon/Music/Shared%20Music/music/4_Non_Blondes/Bigger,_Better,_Faster,_More_/01_-_Train.flac
(10:30:24) [0x2276040] [rb_header_sync] rb-header.c:434: syncing with entry = file:///home/jon/Music/Shared%20Music/music/4_Non_Blondes/Bigger,_Better,_Faster,_More_/01_-_Train.flac
(10:30:24) [0x2276040] [rb_shell_player_sync_with_source] rb-shell-player.c:2897: playing source: 0x248e620, active entry: 0x7f8d901ca750
(10:30:24) [0x2276040] [rb_shell_set_window_title] rb-shell.c:2011: setting title to "4 Non Blondes - Train"
(10:30:24) [0x2276040] [rb_shell_player_sync_buttons] rb-shell-player.c:2992: syncing with source 0x248e620
(10:30:24) [0x2276040] [rb_player_gst_find_element_with_property] rb-player-gst-helper.c:121: iterating bin looking for property volume
(10:30:24) [0x2276040] [find_property_element] rb-player-gst-helper.c:99: didn't find property "volume" on element bin2
(10:30:24) [0x2276040] [find_property_element] rb-player-gst-helper.c:99: didn't find property "volume" on element halaudiosink0
(10:30:24) [0x2276040] [find_property_element] rb-player-gst-helper.c:99: didn't find property "volume" on element bin3
(10:30:24) [0x2276040] [find_property_element] rb-player-gst-helper.c:99: didn't find property "volume" on element alsasink0
(10:30:24) [0x2276040] [impl_play] rb-player-gst.c:813: applying initial volume: 1.000000
(10:30:24) [0x2276040] [rb_shell_player_set_playing_entry] rb-shell-player.c:1684: Success!
(10:30:24) [0x2276040] [rb_shell_clipboard_entryview_changed_cb] rb-shell-clipboard.c:786: entryview changed
(10:30:24) [0x2276040] [rb_shell_clipboard_sync] rb-shell-clipboard.c:584: syncing clipboard
(10:30:24) [0x2276040] [tick_cb] rb-shell-player.c:3513: tick: [file:///home/jon/Music/Shared%20Music/music/4_Non_Blondes/Bigger,_Better,_Faster,_More_/01_-_Train.flac, 202448979:222000000000(0)]
```All I can tell is that it can't find the property "volume" on bin2, halaudiosink, bin3 or alsasink - but not which audio device it's playing through. What do I look for, and when I find it, how do I tell Rhythmbox to use the correct one?

---

### Post by d3v1150m471c on 2010-02-22
you could try

```

alsamixer

```

and try adjusting the levels.

---

### Post by beausoleil on 2010-02-22
> **d3v1150m471c said:**
> you could try

```

alsamixer

```and try adjusting the levels.

Did that - they're all unmuted and at about 80%.

Remember - I'm getting sound from all apps now (including MythTV), but Rhythmbox. And in Rhythmbox, it doesn't matter if the audio file is mp3 or flac. Totem plays both fine, MythTV's music player plays them fine. Heck, Rhythmbox even extracts flac files fine from CDs, it just can't play them audibly. Once I get a decent Internet connection (being on a boat at a marina does have it's disadvantages!), I'll try removing then re-installing Rhythmbox...

---

