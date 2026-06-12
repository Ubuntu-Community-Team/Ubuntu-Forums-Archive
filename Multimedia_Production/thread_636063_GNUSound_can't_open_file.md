---
title: "GNUSound: can't open file"
date: 2007-12-09
forum: Multimedia Production
---

### Post by tkrisz on 2007-12-09
I can't open anything in GNUSound 0.7.4. Tried mp3, ogg, wav.

```
Error: Unknown file format for xxxxxx.mp3
[dispatch-cmd]
```

Any idea what's the problem? Seems like i have all prerequisites.  I don't have any ~/.gnome/gnusound file.

```

sample_init:642: Using plain C minmax
module_init:218: collecting modules in path modules
module_init:220: expansion 0: modules
module_init:218: collecting modules in path ~/.gnusound/modules
module_init:220: expansion 0: /home/krisz/.gnusound/modules
module_init:218: collecting modules in path /usr/lib/gnusound/modules
module_init:220: expansion 0: /usr/lib/gnusound/modules
file_register_driver:127: registered AudioFile
file_register_driver:127: registered ffmpeg
FAIL : src/module.c:module_load:113: no manifest in /usr/lib/gnusound/modules/file_flac.so
FAIL : src/module.c:module_load:113: no manifest in /usr/lib/gnusound/modules/file_gmerlin_avdec.so
FAIL : src/module.c:module_load:113: no manifest in /usr/lib/gnusound/modules/file_lame.so
file_register_driver:127: registered sndfile
pref_set:467: clamping value for ladspa.segment_time, lower bound: 0,000010, upper bound: 10000,000000, requested: 0,000010
ladspa_init:1420: collecting GLADSPA plugins in path /usr/lib/ladspa/
FAIL : ladspa.c:ladspa_load:398: GLADSPA plugin TAP Dynamics (St) (tap_dynamics_st/2153) not loaded because maximum amount of GLADSPA plugins was reached, increase MAX_PLUGINS (loaded: 300, max: 300).
FAIL : ladspa.c:ladspa_load:398: GLADSPA plugin TAP Stereo Echo (tap_stereo_echo/2143) not loaded because maximum amount of GLADSPA plugins was reached, increase MAX_PLUGINS (loaded: 300, max: 300).
FAIL : ladspa.c:ladspa_load:398: GLADSPA plugin Tape Delay Simulation (tapeDelay/1211) not loaded because maximum amount of GLADSPA plugins was reached, increase MAX_PLUGINS (loaded: 300, max: 300).
FAIL : ladspa.c:ladspa_load:398: GLADSPA plugin TAP Equalizer/BW (tap_equalizer_bw/2151) not loaded because maximum amount of GLADSPA plugins was reached, increase MAX_PLUGINS (loaded: 300, max: 300).
FAIL : ladspa.c:ladspa_load:398: GLADSPA plugin TAP Equalizer (tap_equalizer/2141) not loaded because maximum amount of GLADSPA plugins was reached, increase MAX_PLUGINS (loaded: 300, max: 300).
FAIL : ladspa.c:ladspa_load:398: GLADSPA plugin TAP Scaling Limiter (tap_limiter/2145) not loaded because maximum amount of GLADSPA plugins was reached, increase MAX_PLUGINS (loaded: 300, max: 300).
FAIL : ladspa.c:ladspa_load:398: GLADSPA plugin TAP Pink/Fractal Noise (tap_pinknoise/2155) not loaded because maximum amount of GLADSPA plugins was reached, increase MAX_PLUGINS (loaded: 300, max: 300).
FAIL : ladspa.c:ladspa_load:398: GLADSPA plugin TAP Pitch Shifter (tap_pitch/2150) not loaded because maximum amount of GLADSPA plugins was reached, increase MAX_PLUGINS (loaded: 300, max: 300).
FAIL : ladspa.c:ladspa_load:398: GLADSPA plugin TAP Reflector (tap_reflector/2154) not loaded because maximum amount of GLADSPA plugins was reached, increase MAX_PLUGINS (loaded: 300, max: 300).
FAIL : ladspa.c:ladspa_load:398: GLADSPA plugin TAP Reverberator (tap_reverb/2142) not loaded because maximum amount of GLADSPA plugins was reached, increase MAX_PLUGINS (loaded: 300, max: 300).
FAIL : ladspa.c:ladspa_load:398: GLADSPA plugin TAP Rotary Speaker (tap_rotspeak/2149) not loaded because maximum amount of GLADSPA plugins was reached, increase MAX_PLUGINS (loaded: 300, max: 300).
FAIL : ladspa.c:ladspa_load:398: GLADSPA plugin TAP Sigmoid Booster (tap_sigmoid/2157) not loaded because maximum amount of GLADSPA plugins was reached, increase MAX_PLUGINS (loaded: 300, max: 300).
FAIL : ladspa.c:ladspa_load:398: GLADSPA plugin TAP Tremolo (tap_tremolo/2144) not loaded because maximum amount of GLADSPA plugins was reached, increase MAX_PLUGINS (loaded: 300, max: 300).
FAIL : ladspa.c:ladspa_load:398: GLADSPA plugin TAP TubeWarmth (tap_tubewarmth/2158) not loaded because maximum amount of GLADSPA plugins was reached, increase MAX_PLUGINS (loaded: 300, max: 300).
FAIL : ladspa.c:ladspa_load:398: GLADSPA plugin TAP Vibrato (tap_vibrato/2148) not loaded because maximum amount of GLADSPA plugins was reached, increase MAX_PLUGINS (loaded: 300, max: 300).
FAIL : ladspa.c:ladspa_load:398: GLADSPA plugin Signal Tracker (Audio Rates) (tracker_gaaadaia_oa/2025) not loaded because maximum amount of GLADSPA plugins was reached, increase MAX_PLUGINS (loaded: 300, max: 300).
FAIL : ladspa.c:ladspa_load:398: GLADSPA plugin Signal Tracker (Control Rates) (tracker_gaacdcia_oa/2026) not loaded because maximum amount of GLADSPA plugins was reached, increase MAX_PLUGINS (loaded: 300, max: 300).
FAIL : ladspa.c:ladspa_load:398: GLADSPA plugin Transient mangler (transient/1206) not loaded because maximum amount of GLADSPA plugins was reached, increase MAX_PLUGINS (loaded: 300, max: 300).
FAIL : ladspa.c:ladspa_load:398: GLADSPA plugin Bandlimited Variable Slope Triangle Oscillator (FASA) (triangle_fasa_oa/1649) not loaded because maximum amount of GLADSPA plugins was reached, increase MAX_PLUGINS (loaded: 300, max: 300).
FAIL : ladspa.c:ladspa_load:398: GLADSPA plugin Bandlimited Variable Slope Triangle Oscillator (FASC) (triangle_fasc_oa/1650) not loaded because maximum amount of GLADSPA plugins was reached, increase MAX_PLUGINS (loaded: 300, max: 300).
FAIL : ladspa.c:ladspa_load:398: GLADSPA plugin Bandlimited Variable Slope Triangle Oscillator (FCSA) (triangle_fcsa_oa/1651) not loaded because maximum amount of GLADSPA plugins was reached, increase MAX_PLUGINS (loaded: 300, max: 300).
FAIL : ladspa.c:ladspa_load:398: GLADSPA plugin Bandlimited Variable Slope Triangle Oscillator (FCSC) (triangle_fcsc_oa/1652) not loaded because maximum amount of GLADSPA plugins was reached, increase MAX_PLUGINS (loaded: 300, max: 300).
FAIL : ladspa.c:ladspa_load:398: GLADSPA plugin Triple band parametric with shelves (triplePara/1204) not loaded because maximum amount of GLADSPA plugins was reached, increase MAX_PLUGINS (loaded: 300, max: 300).
FAIL : ladspa.c:ladspa_load:398: GLADSPA plugin Valve saturation (valve/1209) not loaded because maximum amount of GLADSPA plugins was reached, increase MAX_PLUGINS (loaded: 300, max: 300).
FAIL : ladspa.c:ladspa_load:398: GLADSPA plugin Valve rectifier (valveRect/1405) not loaded because maximum amount of GLADSPA plugins was reached, increase MAX_PLUGINS (loaded: 300, max: 300).
FAIL : ladspa.c:ladspa_load:398: GLADSPA plugin Resonant Lowpass Filter (vcf_reslp/1721) not loaded because maximum amount of GLADSPA plugins was reached, increase MAX_PLUGINS (loaded: 300, max: 300).
FAIL : ladspa.c:ladspa_load:398: GLADSPA plugin Lowpass Filter (vcf_lp/1722) not loaded because maximum amount of GLADSPA plugins was reached, increase MAX_PLUGINS (loaded: 300, max: 300).
FAIL : ladspa.c:ladspa_load:398: GLADSPA plugin Highpass Filter (vcf_hp/1723) not loaded because maximum amount of GLADSPA plugins was reached, increase MAX_PLUGINS (loaded: 300, max: 300).
FAIL : ladspa.c:ladspa_load:398: GLADSPA plugin Bandpass Filter I (vcf_bp1/1724) not loaded because maximum amount of GLADSPA plugins was reached, increase MAX_PLUGINS (loaded: 300, max: 300).
FAIL : ladspa.c:ladspa_load:398: GLADSPA plugin Bandpass Filter II (vcf_bp2/1725) not loaded because maximum amount of GLADSPA plugins was reached, increase MAX_PLUGINS (loaded: 300, max: 300).
FAIL : ladspa.c:ladspa_load:398: GLADSPA plugin Notch Filter (vcf_notch/1726) not loaded because maximum amount of GLADSPA plugins was reached, increase MAX_PLUGINS (loaded: 300, max: 300).
FAIL : ladspa.c:ladspa_load:398: GLADSPA plugin Peaking EQ Filter (vcf_peakeq/1727) not loaded because maximum amount of GLADSPA plugins was reached, increase MAX_PLUGINS (loaded: 300, max: 300).
FAIL : ladspa.c:ladspa_load:398: GLADSPA plugin Low Shelf Filter (vcf_lshelf/1728) not loaded because maximum amount of GLADSPA plugins was reached, increase MAX_PLUGINS (loaded: 300, max: 300).
FAIL : ladspa.c:ladspa_load:398: GLADSPA plugin High Shelf Filter (vcf_hshelf/1729) not loaded because maximum amount of GLADSPA plugins was reached, increase MAX_PLUGINS (loaded: 300, max: 300).
FAIL : ladspa.c:ladspa_load:398: GLADSPA plugin Resonant Lowpass Filter (vcf_reslp/1721) not loaded because maximum amount of GLADSPA plugins was reached, increase MAX_PLUGINS (loaded: 300, max: 300).
FAIL : ladspa.c:ladspa_load:398: GLADSPA plugin Lowpass Filter (vcf_lp/1722) not loaded because maximum amount of GLADSPA plugins was reached, increase MAX_PLUGINS (loaded: 300, max: 300).
FAIL : ladspa.c:ladspa_load:398: GLADSPA plugin Highpass Filter (vcf_hp/1723) not loaded because maximum amount of GLADSPA plugins was reached, increase MAX_PLUGINS (loaded: 300, max: 300).
FAIL : ladspa.c:ladspa_load:398: GLADSPA plugin Bandpass Filter I (vcf_bp1/1724) not loaded because maximum amount of GLADSPA plugins was reached, increase MAX_PLUGINS (loaded: 300, max: 300).
FAIL : ladspa.c:ladspa_load:398: GLADSPA plugin Bandpass Filter II (vcf_bp2/1725) not loaded because maximum amount of GLADSPA plugins was reached, increase MAX_PLUGINS (loaded: 300, max: 300).
FAIL : ladspa.c:ladspa_load:398: GLADSPA plugin Notch Filter (vcf_notch/1726) not loaded because maximum amount of GLADSPA plugins was reached, increase MAX_PLUGINS (loaded: 300, max: 300).
FAIL : ladspa.c:ladspa_load:398: GLADSPA plugin Peaking EQ Filter (vcf_peakeq/1727) not loaded because maximum amount of GLADSPA plugins was reached, increase MAX_PLUGINS (loaded: 300, max: 300).
FAIL : ladspa.c:ladspa_load:398: GLADSPA plugin Low Shelf Filter (vcf_lshelf/1728) not loaded because maximum amount of GLADSPA plugins was reached, increase MAX_PLUGINS (loaded: 300, max: 300).
FAIL : ladspa.c:ladspa_load:398: GLADSPA plugin High Shelf Filter (vcf_hshelf/1729) not loaded because maximum amount of GLADSPA plugins was reached, increase MAX_PLUGINS (loaded: 300, max: 300).
FAIL : ladspa.c:ladspa_load:398: GLADSPA plugin VyNil (Vinyl Effect) (vynil/1905) not loaded because maximum amount of GLADSPA plugins was reached, increase MAX_PLUGINS (loaded: 300, max: 300).
FAIL : ladspa.c:ladspa_load:398: GLADSPA plugin Simple waveguide mesh (CR Controls) (wg_mesh_cr/2670) not loaded because maximum amount of GLADSPA plugins was reached, increase MAX_PLUGINS (loaded: 300, max: 300).
FAIL : ladspa.c:ladspa_load:398: GLADSPA plugin Wave Terrain Oscillator (waveTerrain/1412) not loaded because maximum amount of GLADSPA plugins was reached, increase MAX_PLUGINS (loaded: 300, max: 300).
FAIL : ladspa.c:ladspa_load:398: GLADSPA plugin Crossfade (xfade/1915) not loaded because maximum amount of GLADSPA plugins was reached, increase MAX_PLUGINS (loaded: 300, max: 300).
FAIL : ladspa.c:ladspa_load:398: GLADSPA plugin Crossfade (4 outs) (xfade4/1917) not loaded because maximum amount of GLADSPA plugins was reached, increase MAX_PLUGINS (loaded: 300, max: 300).
FAIL : ladspa.c:ladspa_load:398: GLADSPA plugin z-1 (zm1/1428) not loaded because maximum amount of GLADSPA plugins was reached, increase MAX_PLUGINS (loaded: 300, max: 300).
player_register_driver:1202: registered player driver ALSA
player_register_driver:1202: registered player driver JACK
player_register_driver:1202: registered player driver OSS
player_register_driver:1202: registered player driver Dummy
player_init:1227: initializing audio driver OSS
dialog_init:138: creating dialog preferencesdialog
mixer_buffers_alloc:894: mixer buffers allocated: muxbuf: 65536 bytes@0x8334348, srcbufs: 2048 bytes (* 32)
file_identify:146: probing 01 - Embermadár.ogg using driver AudioFile
Audio File Library: '01 - Embermadár.ogg': unrecognized audio file format [error 0]
file_identify:146: probing 01 - Embermadár.ogg using driver sndfile
file_identify:146: probing 01 - Embermadár.ogg using driver ffmpeg
ffmpeg_open_for_reading:132: skipping stream type 0
ffmpeg_open_for_reading:138: no audio streams
history_rollback:416: rolling back load-file
FAIL : src/arbiter.c:arbiter_event_source_dispatch:267: runtime error during dispatch-cmd: Unknown file format for 01 - Embermadár.ogg
msg_send:74: sending message history::committed
msg_send:83: recipient: view-history-changed
view_history_changed:34: history changed
msg_send:74: sending message history::committed
msg_send:83: recipient: view-history-changed
view_history_changed:34: history changed
shell_destroy_internal:300: destroying Untitled1
shell_destroy_tool_one:255: destroying tool select
shell_destroy_tool_one:255: destroying tool markers
shell_destroy_tool_one:255: destroying tool mix
shell_destroy_tool_one:255: destroying tool pencil
shell_destroy_tool_one:255: destroying tool move
msg_unsubscribe_by_data:161: unsubscribing view-history-changed from history::committed
msg_unsubscribe_by_data:161: unsubscribing view-track-inserted from clip::track-inserted
msg_unsubscribe_by_data:161: unsubscribing view-track-deleted from clip::track-deleted
msg_unsubscribe_by_data:161: unsubscribing view-track-moved from clip::track-moved
msg_unsubscribe_by_data:161: unsubscribing view-clip-snd-changed from clip::snd-changed
msg_send:74: sending message clip::destroy
mixer_destroy:752: destroying mixer
file_destroy:168: destroy 0x835bad8, use: 1
arbiter_remove_shell:173: shells: 0
mixer_buffers_free:843: freed mixer buffers 0x8334348
mixer_destroy:752: destroying mixer
msg_send:74: sending message clip::destroy
mixer_destroy:752: destroying mixer
dialog_on_destroy:74: destroying dialog preferencesdialog
main:119: main done

```

---

### Post by tkrisz on 2007-12-15
No idea? I'm sure there must be a stupid mistake from me. But no idea what.

---

