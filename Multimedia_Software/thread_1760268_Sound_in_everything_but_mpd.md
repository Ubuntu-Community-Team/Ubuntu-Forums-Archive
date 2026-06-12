---
title: "Sound in everything but mpd"
date: 2011-05-16
forum: Multimedia Software
---

### Post by iskaar22 on 2011-05-16
I am using mpd and ncmpcpp as a music player. Until today it worked perfectly fine but now when I play a song it begins playing but with no sound (yet sound works in every other program). I am using a creative x-fi xtreme gamer sound card.

Here are my configs:

~/.mpdconf:
```
# An example configuration file for MPD
# See the mpd.conf man page for a more detailed description of each parameter.


# Files and directories #######################################################
#
# This setting controls the top directory which MPD will search to discover the
# available audio files and add them to the daemon's online database. This 
# setting defaults to the XDG directory, otherwise the music directory will be
# be disabled and audio files will only be accepted over ipc socket (using
# file:// protocol) or streaming files over an accepted protocol.
#
music_directory        "~/Music/music/"
#
# This setting sets the MPD internal playlist directory. The purpose of this
# directory is storage for playlists created by MPD. The server will use 
# playlist files not created by the server but only if they are in the MPD
# format. This setting defaults to playlist saving being disabled.
#
playlist_directory        "~/Music/playlists/"
#
# This setting sets the location of the MPD database. This file is used to
# load the database at server start up and store the database while the 
# server is not up. This setting defaults to disabled which will allow
# MPD to accept files over ipc socket (using file:// protocol) or streaming
# files over an accepted protocol.
#
db_file            "~/Music/db/tag_cache"
# 
# These settings are the locations for the daemon log files for the daemon.
# These logs are great for troubleshooting, depending on your log_level
# settings.
#
# The special value "syslog" makes MPD use the local syslog daemon. This
# setting defaults to logging to syslog, otherwise logging is disabled.
#
log_file            "~/Music/log/mpd.log"
#
# This setting sets the location of the file which stores the process ID
# for use of mpd --kill and some init scripts. This setting is disabled by
# default and the pid file will not be stored.
#
pid_file            "~/Music/pid/pid"
#
# This setting sets the location of the file which contains information about
# most variables to get MPD back into the same general shape it was in before
# it was brought down. This setting is disabled by default and the server 
# state will be reset on server start up.
#
state_file            "~/Music/state/state"
#
###############################################################################


# General music daemon options ################################################
#
# This setting specifies the user that MPD will run as. MPD should never run as
# root and you may use this setting to make MPD change its user ID after
# initialization. This setting is disabled by default and MPD is run as the
# current user.
#
#user                "mpd"
#
# This setting sets the address for the daemon to listen on. Careful attention
# should be paid if this is assigned to anything other then the default, any.
# This setting can deny access to control of the daemon.
#
# For network
bind_to_address        "127.0.0.1"
#
# And for Unix Socket
#bind_to_address        "/var/run/mpd/socket"
#
# This setting is the TCP port that is desired for the daemon to get assigned
# to.
#
port                "6600"
#
# This setting controls the type of information which is logged. Available 
# setting arguments are "default", "secure" or "verbose". The "verbose" setting
# argument is recommended for troubleshooting, though can quickly stretch
# available resources on limited hardware storage.
#
#log_level            "default"
#
# If you have a problem with your MP3s ending abruptly it is recommended that 
# you set this argument to "no" to attempt to fix the problem. If this solves
# the problem, it is highly recommended to fix the MP3 files with vbrfix
# (available from <http://www.willwap.co.uk/Programs/vbrfix.php>), at which
# point gapless MP3 playback can be enabled.
#
#gapless_mp3_playback            "yes"
#
# This setting enables MPD to create playlists in a format usable by other
# music players.
#
#save_absolute_paths_in_playlists    "no"
#
# This setting defines a list of tag types that will be extracted during the 
# audio file discovery process. Optionally, 'comment' can be added to this
# list.
#
#metadata_to_use    "artist,album,title,track,name,genre,date,composer,performer,disc"
#
###############################################################################


# Symbolic link behavior ######################################################
#
# If this setting is set to "yes", MPD will discover audio files by following 
# symbolic links outside of the configured music_directory.
#
#follow_outside_symlinks    "yes"
#
# If this setting is set to "yes", MPD will discover audio files by following
# symbolic links inside of the configured music_directory.
#
#follow_inside_symlinks        "yes"
#
###############################################################################


# Zeroconf / Avahi Service Discovery ##########################################
#
# If this setting is set to "yes", service information will be published with
# Zeroconf / Avahi.
#
#zeroconf_enabled        "yes"
#
# The argument to this setting will be the Zeroconf / Avahi unique name for
# this MPD server on the network.
#
#zeroconf_name            "Music Player"
#
###############################################################################


# Permissions #################################################################
#
# If this setting is set, MPD will require password authorization. The password
# can setting can be specified multiple times for different password profiles.
#
#password                        "password@read,add,control,admin"
#
# This setting specifies the permissions a user has who has not yet logged in. 
#
#default_permissions             "read,add,control,admin"
#
###############################################################################


# Input #######################################################################
#

input {
        plugin "curl"
#       proxy "proxy.isp.com:8080"
#       proxy_user "user"
#       proxy_password "password"
}

#
###############################################################################

# Audio Output ################################################################
#
# MPD supports various audio output types, as well as playing through multiple 
# audio outputs at the same time, through multiple audio_output settings 
# blocks. Setting this block is optional, though the server will only attempt
# autodetection for one sound card.
#
# See <http://mpd.wikia.com/wiki/Configuration#Audio_Outputs> for examples of 
# other audio outputs.
#
# An example of an ALSA output:
#
audio_output {
    type        "alsa"
    name        "My ALSA Device"
    device        "hw:0,0"    # optional
    format        "44100:16:2"    # optional
    mixer_device    "default"    # optional
    mixer_control    "Master"        # optional
    mixer_index    "0"        # optional
}
#
# An example of an OSS output:
#
#audio_output {
#    type        "oss"
#    name        "My OSS Device"
#    device        "/dev/dsp"    # optional
#    format        "44100:16:2"    # optional
#    mixer_device    "/dev/mixer"    # optional
#    mixer_control    "PCM"        # optional
#}
#
# An example of a shout output (for streaming to Icecast):
#
#audio_output {
#    type        "shout"
#    encoding    "ogg"            # optional
#    name        "My Shout Stream"
#    host        "localhost"
#    port        "8000"
#    mount        "/mpd.ogg"
#    password    "hackme"
#    quality        "5.0"
#    bitrate        "128"
#    format        "44100:16:1"
#    protocol    "icecast2"        # optional
#    user        "source"        # optional
#    description    "My Stream Description"    # optional
#    genre        "jazz"            # optional
#    public        "no"            # optional
#    timeout        "2"            # optional
#}
#
# An example of a httpd output (built-in HTTP streaming server):
#
#audio_output {
#    type        "httpd"
#    name        "My HTTP Stream"
#    encoder        "vorbis"        # optional, vorbis or lame
#    port        "8000"
#    quality        "5.0"            # do not define if bitrate is defined
#    bitrate        "128"            # do not define if quality is defined
#    format        "44100:16:1"
#}
#
# An example of a pulseaudio output (streaming to a remote pulseaudio server)
#
#audio_output {
#    type        "pulse"
#    name        "My Pulse Output"
#    server        "remote_server"        # optional
#    sink        "remote_server_sink"    # optional
#}
#
## Example "pipe" output:
#
#audio_output {
#    type        "pipe"
#    name        "my pipe"
#    command        "aplay -f cd 2>/dev/null"
## Or if you're want to use AudioCompress
#    command        "AudioCompress -m | aplay -f cd 2>/dev/null"
## Or to send raw PCM stream through PCM:
#    command        "nc example.org 8765"
#    format        "44100:16:2"
#}
#
## An example of a null output (for no audio output):
#
#audio_output {
#    type        "null"
#    name        "My Null Output"
#}
#
# This setting will change all decoded audio to be converted to the specified
# format before being passed to the audio outputs. By default, this setting is
# disabled.
#
#audio_output_format        "44100:16:2"
#
# If MPD has been compiled with libsamplerate support, this setting specifies 
# the sample rate converter to use.  Possible values can be found in the 
# mpd.conf man page or the libsamplerate documentation. By default, this is
# setting is disabled.
#
#samplerate_converter        "Fastest Sinc Interpolator"
#
###############################################################################


# Volume control mixer ########################################################
#
# These are the global volume control settings. By default, this setting will
# be detected to the available audio output device, with preference going to 
# hardware mixing. Hardware and software mixers for individual audio_output
# sections cannot yet be mixed.
#
# An example for controlling an ALSA, OSS or Pulseaudio mixer; If this
# setting is used other sound applications will be affected by the volume
# being controlled by MPD.
#
mixer_type            "hardware"
#
# An example for controlling all mixers through software. This will control
# all controls, even if the mixer is not supported by the device and will not
# affect any other sound producing applications.
#
#mixer_type            "software"
#
# This example will not allow MPD to touch the mixer at all and will disable
# all volume controls.
#
#mixer_type            "disabled"
#
###############################################################################


# Normalization automatic volume adjustments ##################################
#
# This setting specifies the type of ReplayGain to use. This setting can have
# the argument "album" or "track". See <http://www.replaygain.org> for more
# details. This setting is disabled by default.
#
#replaygain            "album"
#
# This setting sets the pre-amp used for files that have ReplayGain tags. By
# default this setting is disabled.
#
#replaygain_preamp        "0"
#
# This setting enables on-the-fly normalization volume adjustment. This will
# result in the volume of all playing audio to be adjusted so the output has 
# equal "loudness". This setting is disabled by default.
#
#volume_normalization        "no"
#
###############################################################################


# MPD Internal Buffering ######################################################
#
# This setting adjusts the size of internal decoded audio buffering. Changing
# this may have undesired effects. Don't change this if you don't know what you
# are doing.
#
#audio_buffer_size        "2048"
#
# This setting controls the percentage of the buffer which is filled before 
# beginning to play. Increasing this reduces the chance of audio file skipping, 
# at the cost of increased time prior to audio playback.
#
#buffer_before_play        "10%"
#
###############################################################################


# Resource Limitations ########################################################
#
# These settings are various limitations to prevent MPD from using too many
# resources. Generally, these settings should be minimized to prevent security
# risks, depending on the operating resources.
#
#connection_timeout        "60"
#max_connections        "10"
#max_playlist_length        "16384"
#max_command_list_size        "2048"
#max_output_buffer_size        "8192"
#
###############################################################################


# Character Encoding ##########################################################
#
# If file or directory names do not display correctly for your locale then you 
# may need to modify this setting. After modification of this setting mpd 
# --create-db must be run to change the database.
#
filesystem_charset        "UTF-8"
#
# This setting controls the encoding that ID3v1 tags should be converted from.
#
id3v1_encoding            "UTF-8"
#
###############################################################################
```~/.ncmpcpp/config:
```
####################################################
## this is example configuration file, copy it to ##
## ~/.ncmpcpp/config and set up your preferences  ##
####################################################
#
##### connection settings #####
#
## set it in order to make tag editor and renaming files work properly
#
mpd_host = "localhost"
#
mpd_port = "6600"
#
mpd_music_dir = "~/Music/music"
#
#mpd_connection_timeout = "5"
#
#mpd_crossfade_time = "5"
#
#mpd_communication_mode = "notifications" (polling/notifications)
#
##### music visualizer #####
##
## Note: In order to make music visualizer work you'll
## need to use mpd fifo output, whose format parameter
## has to be set to 44100:16:1. Example configuration:
## (it has to be put into mpd.conf)
##
## audio_output {
##        type            "fifo"
##        name            "My FIFO"
##        path            "/tmp/mpd.fifo"
##        format          "44100:16:1"
## }
##
#
#visualizer_fifo_path = ""
#
##
## Note: Below parameter is needed for ncmpcpp
## to determine which output provides data for
## visualizer and thus allow syncing between
## visualization and sound as currently there
## are some problems with it.
##
#
#visualizer_output_name = ""
#
##
## Note: Below parameter defines how often ncmpcpp
## has to "synchronize" visualizer and audio outputs.
## 30 seconds is optimal value, but if you experience
## synchronization problems, set it to lower value.
## Keep in mind that sane values start with >=10.
##
#
#visualizer_sync_interval = "30"
#
##
## Note: To enable spectrum frequency visualization
## you need to compile ncmpcpp with fftw3 support.
##
#
#visualizer_type = "wave" (spectrum/wave)
#
##### system encoding #####
##
## ncmpcpp should detect your charset encoding
## but if it failed to do so, you can specify
## charset encoding you are using here.
##
## Note: You can see whether your ncmpcpp build
## supports charset detection by checking output
## of `ncmpcpp --version`.
##
## Note: Since MPD uses utf8 by default, setting
## this option makes sense only if your encoding
## is different.
##
#
#system_encoding = ""
#
##### delays #####
#
## delay after playlist highlighting will be disabled (0 = don't disable)
#
#playlist_disable_highlight_delay = "5"
#
## defines how long various messages are supposed to be visible
#
#message_delay_time = "4"
#
##### song format #####
##
## for song format you can use:
##
## %l - length
## %f - filename
## %D - directory
## %a - artist
## %A - album artist
## %t - title
## %b - album
## %y - year
## %n - track number (01/12 -> 01)
## %N - full track info (01/12 -> 01/12)
## %g - genre
## %c - composer
## %p - performer
## %d - disc
## %C - comment
## $R - begin right alignment
##
## you can also put them in { } and then it will be displayed
## only if all requested values are available and/or define alternate
## value with { }|{ } eg. {%a - %t}|{%f}
##
## Note: If you want to set limit on maximal length of a tag, just
## put the appropriate number between % and character that defines
## tag type, e.g. to make album take max. 20 terminal cells, use '%20b'.
##
## Note: Format that is similar to "%a - %t" (i.e. without any additional
## braces) is equal to "{%a - %t}", so if one of the tags is missing,
## you'll get nothing.
##
## text can also have different color than the main window has,
## eg. if you want length to be green, write $3%l$9
##
## available values:
##
## - 0 - default window color (discards all other colors)
## - 1 - black
## - 2 - red
## - 3 - green
## - 4 - yellow
## - 5 - blue
## - 6 - magenta
## - 7 - cyan
## - 8 - white
## - 9 - end of current color
##
## Note: colors can be nested.
##
#
song_list_format = "{%a - }{%t}|{$8%f$9}$R{$3(%l)$9}"
#
song_status_format = "{{%a{ \"%b\"{ (%y)}} - }{%t}}|{%f}"
#
song_library_format = "{%n - }{%t}|{%f}"
#
tag_editor_album_format = "{(%y) }%b"
#
##
## Note: Below variables are for alternative version of user's interface.
## Their syntax supports all tags and colors listed above plus some extra
## markers used for text attributes. They are followed by character '$'.
## After that you can put:
##
## - b - bold text
## - u - underline text
## - r - reverse colors
## - a - use alternative character set
##
## If you don't want to use an attribute anymore, just put it again, but
## this time insert character '/' between '$' and attribute character,
## e.g. {$b%t$/b}|{$r%f$/r} will display bolded title tag or filename
## with reversed colors.
##
#
#alternative_header_first_line_format = "$b$1$aqqu$/a$9 {%t}|{%f} $1$atqq$/a$9$/b"
#
#alternative_header_second_line_format = "{{$4$b%a$/b$9}{ - $7%b$9}{ ($4%y$9)}}|{%D}"
#
##
## Note: Below variables also supports
## text attributes listed above.
##
#
now_playing_prefix = "$b"
#
now_playing_suffix = "$/b"
#
browser_playlist_prefix = "$2playlist$9 "
#
selected_item_prefix = "$6"
#
selected_item_suffix = "$9"
#
## colors are not supported for below variable
#
#song_window_title_format = "{%a - }{%t}|{%f}"
#
##### columns settings #####
##
## syntax of song columns list format is "column column etc."
##
## - syntax for each column is:
##
## (width of column)[column's color]{displayed tag}
##
## Note: Width is by default in %, if you want a column to
## have fixed size, add 'f' after the value, e.g. (10)[white]{a}
## will be the column that take 10% of screen (so the real column's
## width will depend on actual screen size), whereas (10f)[white]{a}
## will take 10 terminal cells, no matter how wide the screen is.
##
## - color is optional (if you want the default one, type [])
##
## Note: You can give a column additional attributes by putting appropriate
## character after displayed tag character. Available attributes are:
##
## - r - column will be right aligned
## - E - if tag is empty, empty tag marker won't be displayed
##
## You can also:
##
## - give a column custom name by putting it after attributes,
##   separated with character ':', e.g. {lr:Length} gives you
##   right aligned column of lengths named "Length".
##
## - define sequence of tags, that have to be displayed in case
##   predecessor is empty in a way similar to the one in classic
##   song format, i.e. using '|' character, e.g. {a|c|p:Owner}
##   creates column named "Owner" that tries to display artist
##   tag and then composer and performer if previous ones are
##   not available.
##
#
#song_columns_list_format = "(7f)[green]{l} (25)[cyan]{a} (40)[]{t|f} (30)[red]{b}"
#
##### various settings #####
#
##
## Note: Custom command that will be executed each
## time song changes. Useful for notifications etc.
##
## Attention: It doesn't support song format anymore.
## Use `ncmpcpp --now-playing SONG_FORMAT` instead.
##
#execute_on_song_change = ""
#
#playlist_show_remaining_time = "no"
#
#playlist_shorten_total_times = "no"
#
#playlist_separate_albums = "no"
#
#playlist_display_mode = "classic" (classic/columns)
#
#browser_display_mode = "classic" (classic/columns)
#
#search_engine_display_mode = "classic" (classic/columns)
#
#discard_colors_if_item_is_selected = "yes"
#
#incremental_seeking = "yes"
#
#seek_time = "1"
#
#autocenter_mode = "no"
#
#centered_cursor = "no"
#
##
## Note: You can specify third character which will
## be used to build 'empty' part of progressbar.
##
progressbar_look = "=>"
#
default_place_to_search_in = "database" (database/playlist)
#
#user_interface = "classic" (classic/alternative)
#
#media_library_left_column = "a" (possible values: a,y,g,c,p, legend above)
#
default_find_mode = "wrapped" (wrapped/normal)
#
default_space_mode = "add" (add/select)
#
#default_tag_editor_left_col = "albums" (albums/dirs)
#
#default_tag_editor_pattern = "%n - %t"
#
#header_visibility = "yes"
#
#statusbar_visibility = "yes"
#
#titles_visibility = "yes"
#
#header_text_scrolling = "yes"
#
#fancy_scrolling = "yes"
#
#cyclic_scrolling = "no"
#
#lines_scrolled = "2"
#
#follow_now_playing_lyrics = "no"
#
#store_lyrics_in_song_dir = "no"
#
##
## Note: If you set this variable, ncmpcpp will try to
## get info from last.fm in language you set and if it
## fails, it will fall back to english. Otherwise it will
## use english the first time.
##
## Note: Language has to be expressed as an ISO 639 alpha-2 code.
##
#lastfm_preferred_language = ""
#
#ncmpc_like_songs_adding = "no" (enabled - add/remove, disabled - always add)
#
#show_hidden_files_in_local_browser = "no"
#
#display_screens_numbers_on_start = "yes"
#
##
## How shall key_screen_switcher work?
##
## - "previous" - switch between current and last used screen
## - "sequence: 2 -> 9 -> 5" - switch between given sequence of screens.
##
## Screen numbers you can use after 'sequence' keyword are:
##
## - 1 - help
## - 2 - playlist
## - 3 - browser
## - 4 - search engine
## - 5 - media library
## - 6 - playlist editor
## - 7 - tag editor
## - 8 - outputs
## - 9 - visualizer
## - 10 - clock
##
## As you can see, above example will switch between
## playlist, visualizer and media library screens.
##
#screen_switcher_mode = "sequence: 2 -> 3"
#
##
## Note: You can define startup screen for ncmpcpp
## by choosing screen number from the list above.
##
#startup_screen = "2"
#
#jump_to_now_playing_song_at_start = "yes"
#
#ask_before_clearing_main_playlist = "no"
#
#clock_display_seconds = "no"
#
#display_volume_level = "yes"
#
#display_bitrate = "no"
#
#display_remaining_time = "no"
#
#regular_expressions = "basic" (basic/extended)
#
##
## Note: If below is enabled, ncmpcpp will ignore leading
## "The" word while sorting items in browser, tags in
## media library, etc.
##
#ignore_leading_the = "no"
#
#block_search_constraints_change_if_items_found = "yes"
#
mouse_support = "yes"
#
mouse_list_scroll_whole_page = "yes"
#
#empty_tag_marker = "<empty>"
#
#tag_editor_extended_numeration = "no"
#
#media_library_display_date = "yes"
#
#media_library_disable_two_column_mode = "no"
#
enable_window_title = "yes"
#
##
## Note: You can choose default search mode for search
## engine. Available modes are:
##
## - 1 - use mpd built-in searching (no regexes, pattern matching)
## - 2 - use ncmpcpp searching (pattern matching with support for regexes,
##       but if your mpd is on a remote machine, downloading big database
##       to process it can take a while
## - 3 - match only exact values (this mode uses mpd function for searching
##       in database and local one for searching in current playlist)
##
#
#search_engine_default_search_mode = "1"
#
##
## Note: Below variables can allow you to physically
## remove files and directories from your hdd using
## ncmpcpp's browser screen.
##
#
#allow_physical_files_deletion = "no"
#
#allow_physical_directories_deletion = "no"
#
#external_editor = ""
#
#use_console_editor = "no" (set to yes, if your editor is console app)
#
##### colors definitions #####
#
#colors_enabled = "yes"
#
#empty_tag_color = "cyan"
#
#header_window_color = "default"
#
#volume_color = "default"
#
#state_line_color = "default"
#
#state_flags_color = "default"
#
#main_window_color = "yellow"
#
#color1 = "white"
#
#color2 = "green"
#
#main_window_highlight_color = "yellow"
#
#progressbar_color = "default"
#
#statusbar_color = "default"
#
#alternative_ui_separator_color = "black"
#
#active_column_color = "red"
#
#visualizer_color = "yellow"
#
#window_border_color = "green"
#
#active_window_border = "red"
#

```

---

### Post by iskaar22 on 2011-05-19
bumping, for some reason it started working for awhile and now it doesn't again, it just works when it wants to I guess.

---

### Post by kostkon on 2011-05-19
Are you using Ubuntu, and what version.

---

### Post by iskaar22 on 2011-05-19
> **kostkon said:**
> Are you using Ubuntu, and what version.
Ubuntu 11.04

---

### Post by kostkon on 2011-05-19
OK, try this; put a song playing in ncmpcpp and then open your sound preferences and select the "Applications" tab

Do you see an entry for ncmpcpp or mpd appearing there?

---

### Post by iskaar22 on 2011-05-19
> **kostkon said:**
> OK, try this; put a song playing in ncmpcpp and then open your sound preferences and select the "Applications" tab

Do you see an entry for ncmpcpp or mpd appearing there?

Nope

---

### Post by kostkon on 2011-05-19
> **iskaar22 said:**
> Nope
Then consider configuring your mpd to use pulseaudio, i.e. I assume by commenting this block of code
```
# An example of an ALSA output:
#
audio_output {
    type        "alsa"
    name        "My ALSA Device"
    device        "hw:0,0"    # optional
    format        "44100:16:2"    # optional
    mixer_device    "default"    # optional
    mixer_control    "Master"        # optional
    mixer_index    "0"        # optional
}
```
and commenting out this block
```
# An example of a pulseaudio output (streaming to a remote pulseaudio server)
#
#audio_output {
#    type        "pulse"
#    name        "My Pulse Output"
```
You will also need to restart your mpd afterwards.

---

### Post by iskaar22 on 2011-05-19
> **kostkon said:**
> Then consider configuring your mpd to use pulseaudio, i.e. I assume by commenting this block of code
```
# An example of an ALSA output:
#
audio_output {
    type        "alsa"
    name        "My ALSA Device"
    device        "hw:0,0"    # optional
    format        "44100:16:2"    # optional
    mixer_device    "default"    # optional
    mixer_control    "Master"        # optional
    mixer_index    "0"        # optional
}
```and commenting out this block
```
# An example of a pulseaudio output (streaming to a remote pulseaudio server)
#
#audio_output {
#    type        "pulse"
#    name        "My Pulse Output"
```You will also need to restart your mpd afterwards.

Same problem :/

---

### Post by kostkon on 2011-05-19
> **iskaar22 said:**
> Same problem :/
Hmm ok. It seems that mpd keeps a log in
```
~/Music/log/mpd.log
```
you could just open it and check for any errors or warnings.

---

### Post by iskaar22 on 2011-05-19
> **kostkon said:**
> Hmm ok. It seems that mpd keeps a log in
```
~/Music/log/mpd.log
```you could just open it and check for any errors or warnings.

No files in that folder.

---

### Post by kostkon on 2011-05-19
You could check this [how-to]("http://mpd.wikia.com/wiki/PulseAudio").

---

