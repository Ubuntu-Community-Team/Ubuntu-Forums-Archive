---
title: "Problem with Audacious"
date: 2009-03-03
forum: Multimedia Software
---

### Post by DachaArh on 2009-03-03
MY Audacious 1.5.1 ia not working for some time.
When I double click some song nothing happens, song never starts to play, so I wanted to ask does Audacious has some folder where he keeps settings, because I wan't to restart my audacious profile to see if it works then. ( some folder in home, like most applications have)

thanks in advance...

---

### Post by neu2buntu on 2009-03-03
try right click on the song you want to play and in popup window choose "open with" from there you should be able to choose audacious . or also try > applications > accessories > terminal and do code ```
audacious
``` paste any errors you get from that...

---

### Post by DachaArh on 2009-03-03
I can open audacious and I do have a playlist in it, but nothing happens when I play it, File is not missing, I have tried al my files but song is never played...

---

### Post by neu2buntu on 2009-03-03
do as i said above open "audacious" with the terminal and try and play a song to see if the terminal gives any errors, paste  the output of that terminal here....

---

### Post by neu2buntu on 2009-03-03
also have you looked at the sound settings in preferences ,open this window by right clicking on a blank part of the audacious gui......  and choose preferences you will see a window like this.... see screenshot...    you should be able to troubleshoot your audio problem from here hopefully



also maybe look at plugins and make sure all the decoders are ticked on!!!

---

### Post by DachaArh on 2009-03-03
this is the error I get in terminal :

> ** (audacious:7746): WARNING **: alsa_setup(): Sample format not available for playback: Invalid argument
MADPlug-Message: failed to open audio output: XMMS reverse compatibility output plugin

All other audio players work fine...

---

### Post by neu2buntu on 2009-03-03
not too sure about the error you are getting,possibly have you removed  a dependency with another program,.  i have found the config file for audacious do code ```
gedit .config/audacious/config
``` here mine if you want to compare 

[rootvis]
debug=0
stereo=1
geometry_posx=520
geometry_posy=1
geometry_orientation=0
geometry_height=50
geometry_space=1
bar_width=8
bar_falloff=5
bar_shadow=1
bar_bevel=0
bar_gradient=1
bar_color_1=#e6ff64ff
bar_color_2=#cdf62bff
bar_color_3=#b8dd27ff
bar_color_4=#a3c422ff
bar_bevel_color=#00ff00ff
bar_shadow_color=#00000066
peak_enabled=1
peak_falloff=4
peak_step=5
peak_color=#ffffffdd
peak_shadow=0
data_cutoff=180
data_div=4
data_linearity=0.33
data_fps=30
[rootvis2]
geometry_posx=520
geometry_posy=52
geometry_orientation=1
geometry_height=40
geometry_space=2
bar_width=8
bar_falloff=5
bar_shadow=0
bar_bevel=0
bar_gradient=1
bar_color_1=#e6ff6466
bar_color_2=#e6ff6455
bar_color_3=#e6ff6433
bar_color_4=#e6ff6422
bar_bevel_color=#00ff00ff
bar_shadow_color=#00000066
peak_enabled=1
peak_falloff=4
peak_step=5
peak_color=#ffffff88
peak_shadow=0
data_cutoff=180
data_div=4
data_linearity=0.33
data_fps=30
[jack]
volume_left=25
volume_right=25
[audacious]
allow_multiple_instances=FALSE
use_realtime=FALSE
always_show_cb=TRUE
convert_underscore=TRUE
convert_twenty=TRUE
convert_slash=TRUE
show_numbers_in_pl=TRUE
show_separator_in_pl=TRUE
snap_windows=TRUE
save_window_positions=TRUE
dim_titlebar=TRUE
get_info_on_load=FALSE
get_info_on_demand=TRUE
eq_scaled_linked=TRUE
no_playlist_advance=FALSE
refresh_file_list=TRUE
sort_jump_to_file=FALSE
use_pl_metadata=TRUE
warn_about_win_visibility=TRUE
use_backslash_as_dir_delimiter=FALSE
player_shaded=FALSE
player_visible=TRUE
shuffle=FALSE
repeat=FALSE
scaled=FALSE
autoscroll_songname=TRUE
stop_after_current_song=FALSE
playlist_shaded=FALSE
playlist_visible=FALSE
use_fontsets=FALSE
mainwin_use_bitmapfont=TRUE
equalizer_visible=TRUE
equalizer_active=TRUE
equalizer_shaded=FALSE
equalizer_autoload=TRUE
easy_move=FALSE
use_eplugins=FALSE
always_on_top=FALSE
sticky=FALSE
random_skin_on_play=FALSE
pause_between_songs=FALSE
show_wm_decorations=FALSE
eq_extra_filtering=TRUE
analyzer_peaks=TRUE
allow_broken_skins=FALSE
close_dialog_open=TRUE
close_dialog_add=TRUE
resume_playback_on_startup=FALSE
playlist_detect=TRUE
show_filepopup_for_tuple=TRUE
recurse_for_cover=FALSE
use_file_cover=FALSE
use_xmms_style_fileselector=FALSE
use_extension_probing=TRUE
filepopup_showprogressbar=TRUE
close_jtf_dialog=TRUE
twoway_scroll=TRUE
software_volume_control=FALSE
warn_about_broken_gtk_engines=TRUE
disable_inline_gtk=FALSE
remember_jtf_entry=TRUE
enable_replay_gain=TRUE
enable_clipping_prevention=TRUE
replay_gain_track=TRUE
replay_gain_album=FALSE
enable_adaptive_scaler=FALSE
enable_src=TRUE
bypass_dsp=FALSE
player_x=123
player_y=306
timer_mode=0
vis_type=2
analyzer_mode=1
analyzer_type=1
scope_mode=0
vu_mode=1
voiceprint_mode=0
vis_refresh_rate=0
analyzer_falloff=3
peaks_falloff=1
playlist_x=1149
playlist_y=325
playlist_width=275
playlist_height=232
playlist_position=0
equalizer_x=687
equalizer_y=278
snap_distance=10
pause_between_songs_time=2
mouse_wheel_change=8
scroll_pl_by=3
titlestring_preset=0
resume_playback_on_startup_time=-1
output_buffer_size=500
recurse_for_cover_depth=0
filepopup_pixelsize=150
filepopup_delay=20
colorize_r=255
colorize_g=255
colorize_b=255
output_bit_depth=16
saved_volume=64764
src_rate=48000
src_type=0
playlist_font=Sans Bold 9
mainwin_font=Sans Bold 8
eqpreset_default_file=dir_default.preset
eqpreset_extension=preset
generic_title_format=${?artist:${artist} - }${?album:${album} - }${title}
cover_name_exclude=back
equalizer_preamp=-2.88
replay_gain_preamp=0
default_gain=-9
equalizer_band0=0
equalizer_band1=0
equalizer_band2=0
equalizer_band3=0
equalizer_band4=0
equalizer_band5=0
equalizer_band6=0
equalizer_band7=0
equalizer_band8=0
equalizer_band9=0
scale_factor=2
skin=/usr/share/audacious/Skins/Refugee
enabled_vplugins=spectrum.so (#0)
filesel_path=/home/h4ck3r/Desktop
url_history_length=0
output_plugin=/usr/lib/audacious/Output/pulse_audio.so (#0)
[AdPlug]
16bit=TRUE
Stereo=FALSE
Frequency=44100
Endless=FALSE
[CDDA]
use_dae=TRUE
limitspeed=1
use_cdtext=TRUE
use_cddb=TRUE
cddbserver=freedb.org
cddbport=8880
cddbhttp=FALSE
debug=FALSE
[AudioCompress]
anticlip=FALSE
target=0
gainmax=0
gainsmooth=0
buckets=0
[ALSA]
buffer_time=500
period_time=100
pcm_device=default
mixer_card=0
mixer_device=PCM
volume_left=100
volume_right=100

if u cant fix the settings here.....
u should also use nautilus to go to this directory tick show hidden files and see if the config file has a backup then just delete the file in use and on the next restart the backup file will be used instead.....

---

### Post by DachaArh on 2009-03-12
tried your config and not working

---

### Post by markbuntu on 2009-03-12
Have you tried reinstalling it?

---

