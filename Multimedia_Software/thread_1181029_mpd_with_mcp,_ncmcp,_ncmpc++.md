---
title: "mpd with mcp, ncmcp, ncmpc++"
date: 2009-06-07
forum: Multimedia Software
---

### Post by bgc on 2009-06-07
Hi,

In my somewhat aimless meandering to find a good media player to stick with in Linux, and after trying Audacious, Aqualung, gmusicbrowser, CMus, and a few more, I have come across a favourite of many: using mpd with which ever front end of preference.

I'm generally interested in CLI front ends, hence mcp, ncmpc and/or ncmpc++. I installed all of these and tried configuring as per various 'how-to's available on the web, some recommending to configure the mpd.conf file in your home directory, some the /etc/mpd.conf file. However, it does not work.

If I type ~$ mpd, I generally get told it is already running (even if I stop it using init.d). Starting mcp, ncmpc or ncmpcpp shows no signs of the music files which I had previously set the path to in the config files. In one case they did show up, but in playback I could here nothing, despite having uncommented the ALSA lines in the config file. I otherwise generally got the error that port 6600 was in use already.

I have also attempted to uninstall mpd in order to try to start from scratch, but was unsuccessful as Synaptic just wouldn't let me.

Does anybody know how to uninstall, and more importantly, how to set up mpd and the frontend correctly? This is for use on the local machine only, for now.

I run Jaunty (recently did a clean install) on dual boot. Would appreciate any help anyone can give me!

Thank you!

bgc

---

### Post by bgc on 2009-06-08
Can I also add that I would appreciate any suggestions for a media player!

I started off using Audacious, mainly due to its good file format support, but progressively saw that its memory footprint was becoming substantial (maybe a bug? At some point, with no loaded library or anything it reached 1GB of RAM!). I have tried Aqualung and gmusicbrowser, both of which show potential, but that don't quite fit the bill.

MPlayer looks good as long as I learn how to use it properly to create playlists etc., although visualising playlists for instance would be useful.

CMus is good, except that I don't want a program that loads all my media into a library using id3 tags. Because of that it still uses ~ 20MB of RAM, which for a CLI media player is quite substantial IMO.

Basically I would like extensive format support (mainly mp3, ogg, ape, flac, cue), simple interface (CL is good, but also willing to consider GUI), easy to create and sort playlists, the ability to browse directory structure of music (my music is well organised in terms of structure, as opposed to the id3 tags, which are not), and a small memory footprint!

My point of reference back in Windows was foobar2000, which was highly configurable, played anything you could throw at it, and was simple enough and not a massive memory hog (as Windows programs go).

So any suggestions are very welcome! Thanks!

---

### Post by dioltas on 2009-06-08
Hey, I'm using mpd + ncmpcpp. Love it. Tried loads of music players and setled on this (for now anyway). If you wanted a graphical interface you can use sonata. 

I like the way the deamon runs in the background so that you can control it with whatever app you want. Like I have kb shortcuts set up to skip, pause etc using mpc. I browse songs and stuff using ncmpcpp.

Could you post your /etc/mpd.conf file maybe? I'm not sure but I think mpd is supposed to be run as root and then it changes itself to a normal user. I have it set to run as a deamon in /etc/rc.conf so it's just always running in the background. I open up ncmpcpp then if I want to do something.

---

### Post by bgc on 2009-06-08
Hi! Thanks for your reply! MPD seems to be the choice of many, which is why I was interested in trying. I have to be honest with you: I have tried many configurations to try and get it to work. Not always the best strategy as things can get mixed up badly. Some prefer to move config files to the home directory and run as user, some prefer to use the config file in /etc/ keeping 'mpd' as user, so I'm not sure where I'm at right now. This is my /etc/mpd.conf file:

(Apologies for length of output, but don't know how to do it differently!)



# Required files and directories ##############################################
#
# This setting controls the top directory which MPD will search to discover the
# available audio files and add them to the daemon's online database.
#
music_directory			"/media/Data/music"
#
# This setting sets the MPD internal playlist directory. The purpose of this
# directory is storage for playlists created by MPD. The server will use 
# playlist files not created by the server but only if they are in the MPD
# format.
#
playlist_directory		"/var/lib/mpd/playlists"
#
# This setting sets the location of the MPD database. This file is used to
# load the database at server start up and store the database while the 
# server is not up.
#
db_file				"/var/lib/mpd/mpd.db"
# 
# These settings are the locations for the daemon log files for the daemon.
# These logs are great for troubleshooting, depending on your log_level
# settings.
#
log_file			"/var/log/mpd/mpd.log"
error_file			"/var/log/mpd/mpd.error"
###############################################################################


# Optional files ##############################################################
#
# This setting sets the location of the file which stores the process ID
# for use of mpd --kill and some init scripts. This setting is disabled by
# default.
#
#pid_file			"/var/run/mpd/mpd.pid"
#
# This setting sets the location of the file which contains information about
# most variables to get MPD back into the same general shape it was in before
# it was brought down. This setting is disabled by default.
#
state_file			"/var/lib/mpd/mpdstate"
#
###############################################################################


# General music daemon options ################################################
#
# This setting specifies the user that MPD will run as, if set. MPD should
# never run as root and you may use this setting to make MPD change its user 
# id after initialization. Do not use this setting if you start MPD as an
# unprivileged user. This setting is disabled by default, and the server will
# run as root.
#
user				"mpd"
#
# This setting sets the address for the daemon to listen on. Careful attention
# should be paid if this is assigned to anything other then the default, any.
# This setting can deny access to control of the daemon.
#
# For network
bind_to_address		"127.0.0.1"
#
# And for Unix Socket
#bind_to_address		"~/.mpd/socket"
#
# This setting is the port that is desired for the daemon to get assigned to.
#
#port				"6600"
#
# This setting controls the type of information which is logged. Available 
# setting arguments are "default", "secure" or "verbose". The "verbose" setting
# argument is recommended for troubleshooting, though can quickly stretch
# available resources on limited hardware storage.
#
#log_level			"default"
#
# If you have a problem with your MP3s ending abruptly it is recommended that 
# you set this argument to "no" to attempt to fix the problem. If this solves
# the problem, it is highly recommended to fix the MP3 files with vbrfix
# (available from <http://www.willwap.co.uk/Programs/vbrfix.php>), at which
# point gapless MP3 playback can be enabled.
#
gapless_mp3_playback			"yes"
#
# This setting enables MPD to create playlists in a format usable by other
# music players.
#
#save_absolute_paths_in_playlists	"no"
#
# This setting defines a list of tag types that will be extracted during the 
# audio file discovery process. Optionally, 'comment' can be added to this
# list.
#
#metadata_to_use	"artist,album,title,track,name,genre,date,composer,performer,disc"
#
###############################################################################

# Symbolic link behavior ######################################################
#
# If this setting is set to "yes", MPD will discover audio files by following 
# symbolic links outside of the configured music_directory.
#
#follow_outside_symlinks	"yes"
#
# If this setting is set to "yes, MPD will discover audio files by following
# symbolic links inside of the configured music_directory.
#
#follow_inside_symlinks		"yes"
#
###############################################################################

# Zeroconf / Avahi Service Discovery ##########################################
#
# If this setting is set to "yes", service information will be published with
# Zeroconf / Avahi.
#
#zeroconf_enabled		"yes"
#
# The argument to this setting will be the Zeroconf / Avahi unique name for
# this MPD server on the network.
#
#zeroconf_name			"Music Player"
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

---

### Post by dioltas on 2009-06-08
Ya, that's more or less like mine, except my music directory is /home/user/music

I'd try uncommenting the lines (just delete the #)

pid_file "/var/run/mpd/mpd.pid"
and 
port 6600

maybe that's why the clients can't connect, although I'd say the mpd port would be set to 6600 by default anyway...

then do "sudo /etc/rc.d/mpd restart"   (or start if it's not already running)
then run "mpc status" and see what output you get.

Did you do "mpd --create-db", this adds all the sonds from your music dir (/media/Data/music) to mpd's database.

---

### Post by bgc on 2009-06-08
Hi, I followed your suggestions. Firstly I'm assuming that the way to restart mpd is with "sudo /etc/init.d/mpd restart", as your command didn't work. mpc status essentially says that it has problems connecting to "localhost" on port 6600, connection refused. I have also done the mpd --create-db (which it seemed to do at some point), although trying now says that it cannot setgid for user "mpd" at line 58...

---

### Post by dioltas on 2009-06-08
You could try "sudo -i" and then /etc/rc.d/mpd restart

It could be that the permissions and stuff for the mpd user are not set up correctly.
This is the guide that I used for setting up mpd originally, it's for arch linux, but should apply to ubuntu as well.
[http://wiki.archlinux.org/index.php/Mpd#New_Setup_Instructions](http://wiki.archlinux.org/index.php/Mpd#New_Setup_Instructions)

You have to create those /var/ files and mpd has to be the owner of those files. The guide shows how to do it. This might have been done automatically though in ubuntu.

---

### Post by bgc on 2009-06-08
Hi, I think that website is one of the ones I tried following. I have followed all steps. Now, mpc status gives me vol, rep and ran settings, and opening ncmpc(pp) also shows the music, but no sound.

Also, when I try to uninstall or reinstall mpd I do get an error, so I do wonder how much could be because of something I changed elsewhere, or whether a clean installation would be better!

Thanks for your help!

---

### Post by dioltas on 2009-06-08
That's a goos sign anyway, seems to be working!

Stupid question, but is does mpc show the volume is turned up and that it's playing?
"mpc play" is the command to start playing, I think.


Here is the output when I type mpc:
> Ash - Let It Flow
[playing] #28/2733   3:29/4:43 (74%)
volume: 23%   repeat: off   random: on 

---

### Post by bgc on 2009-06-08
Hi, I get the same output as you (the time counter doesn't change, but repeating the command shows that the song has moved on), and volume is 100%!

I'm also playing music with MPlayer, which has no issues, so it's not related to sound card drivers or permission to access sound or anything like that I don't think...

This is as close as I've been to making it work!!! Aaarrgh!

---

### Post by dioltas on 2009-06-08
ha, it muust be frustrating alright, I know the feeling. Ya it doesn't change. It should be playing so.

Try closing mplayer maybe and restarting mpd again? I remember when I was using ubuntu I sometimes had a problem when using rythmbox and trying to play sound with something else at the same time. 

Before you try that actually, try "cat /etc/group | grep mpd" and make sure that mpd is listed after audio. Just to make sure mpd is a member of the audio group.

if it's not, try "sudo usermod -a -G audio mpd"

---

### Post by bgc on 2009-06-08
Well... when I try to do the restart, it says it successfully stops mpd, but cannot restart it because: "unable to bind port 6600: Address already in use; Maybe MPD is still running? Aborted".

Also, I have no 'groups' director/file, only 'group', and when running the command you suggest I get no output...

Thanks for the patience!

---

### Post by dioltas on 2009-06-08
Ya, sorry I meant to type /etc/group !

try "ps aux | grep mpd" to check if it's still running, and if you want to force it to quit you could do "sudo killall mpd"

The group thing could be your problem so. I think mpd should be a member of groups mpd and audio.

try "groups mpd"
If it's not a member of audio try "sudo usermod -a -G audio mpd" and fingers crossed it might work!

Edit: On mine I get 
> [me@arch_laptop ~]$ groups mpd
audio mpd

---

### Post by bgc on 2009-06-08
Cool. mpd was still running and I killed it. "groups mpd" did return audio. I still ran the line you mention "sudo usermod -a -G audio mpd". Then running mpd or mpc gives me an error, 'problems opening file /etc/mpd.conf for reading: Permission denied' and 'problems connecto to "localhost" on port 6600' respectively. However, I did follow the steps for setting permissions on the wiki you sent me, so I have no clue why that may be!

Actually, on mine I get 
user@usercomp$ groups mpd
audio

---

### Post by dioltas on 2009-06-08
try starting it as root. I think mpd starts as user root then changes itself to user: mpd.

If mpd was already a member of audio, then that command shouldn't make any difference...

---

### Post by bgc on 2009-06-08
Ah ok... so it does start, but still no sound!

Also, is it normal for it to use substantial amounts of CPU? Because while it's running it seems to do so!

---

### Post by dioltas on 2009-06-08
Ya that's weird. Mine is using 1.7% of my cpu and 1.1% of my memory at the moment. I'm trying to think why it wouldn't play any sound.

Maybe mpd isn't detecting your settings properly at startup. There is some troubleshooting for that here
[http://wiki.archlinux.org/index.php/Mpd#Autodetection_failed](http://wiki.archlinux.org/index.php/Mpd#Autodetection_failed)
(Same guide).

Is mpd also a member of mpd as well as audio? Maybe that could be something to do with it?

Edit: After I finished typing this I checked again and it had jumped to nearly 5 % of the cpu, right now its 4%. I had it paused before I started typing.

---

### Post by bgc on 2009-06-08
I have no idea of not being part of the mpd group is an issue, nor how that can be changed!

I followed the indications on the website, and uncommented those parts of the mpd.conf files, and started mpd again. This time a file seems to start playing but then stops. mpc status shows nothing.

When running mpd was taking about 100% of one of two CPUs! I remember reading somewhere that it could be because it was resampling the music continuously, or something like that. So I'm hoping there's an option somewhere to change that, because otherwise the 'lightweight' goes out of the window!

---

### Post by dioltas on 2009-06-08
Just do "groups mpd" again and the output should be mpd audio.
If it's not you could do "sudo usermod -a -G audio mpd" to add it.

I don't know if that will make a difference tbh...
Maybe undo those changes so from that site.

Christ, 100% of a cpu is definitely not right! :D mpd is supposed to be light weight alright. Must be something wrong there!

Maybe your best bet would be to wipe mpd from your system and start fresh. You said you installed it with synaptic and it won't let you remove it? Hope all this hassle is worth it in the end for you!

---

### Post by dioltas on 2009-06-08
Oh ya, meant to suggest earlier try having a look at /var/log/mpd/mpd.log and /var/log/mpd/mpd.error. Maybe post them up, might clear up a few things.

---

### Post by bgc on 2009-06-08
groups mpd still showed 'audio' only. Ran the line you mention, but it still is 'audio' only when doing groups mpd...

The thing is, before changing things from the website you mention, I managed to 'completely remove' mpd, mpc, ncmpc, and ncmpcpp, and reinstalled all of them, so all of this is happening on a fresh install of mpd!

Well, settling on a media player would be good. I didn't know, though, that it would be this problematic, considering how popular the player is.

I guess it also doesn't help that I'm fairly new to linux so still don't know my way around!

---

### Post by dioltas on 2009-06-08
Ya linux can be frustrating like that sometimes. mpd worked for me "out of the box" really! Some programs seem to work perfectly for some and cause awful trouble for others!

Post up the log files I mentioned anyway, they might help.

As for the group thing, there must not be a group called mpd, because other wise it would have been listed in /etc/group when you did the other command.

Try "sudo groupadd mpd"
and then the usermod command to add mpd to that group. It might not make any difference, but worth a try.

---

### Post by bgc on 2009-06-08
Hi, here they are! doing the groupadd changed nothing, as 'groups mpd' still returns audio only.

mpd.log

Jun 08 15:14 : Avahi: Service 'Music Player' successfully established.
Jun 08 16:04 : Avahi: Service 'Music Player' successfully established.
Jun 08 16:16 : Avahi: Service 'Music Player' successfully established.

mpd.error

No protocol specified
E: client-conf-x11.c: XOpenDisplay() failed
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
[WARN 11595] polkit-session.c:144:polkit_session_set_uid(): session != NULL
 Not built with -rdynamic so unable to print a backtrace
No protocol specified
E: client-conf-x11.c: XOpenDisplay() failed
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
[WARN 11737] polkit-session.c:144:polkit_session_set_uid(): session != NULL
 Not built with -rdynamic so unable to print a backtrace
No protocol specified
E: client-conf-x11.c: XOpenDisplay() failed
Jun 08 16:16 : can't find alsa mixer_control "PCM"
Jun 08 16:16 : using software volume
Jun 08 16:16 : Error opening ALSA device "hw:0,0": Device or resource busy
Jun 08 16:16 : problems opening audio device while playing "7/Parsifal1.ape"
Jun 08 16:16 : problems opening audio device while playing "7/Parsifal1.ape"
Jun 08 16:16 : Error opening ALSA device "hw:0,0": Device or resource busy
Jun 08 16:16 : problems opening audio device while playing "7/Parsifal1.ape"
Jun 08 16:16 : problems opening audio device while playing "7/Parsifal2.ape"
Jun 08 16:17 : Error opening ALSA device "hw:0,0": Device or resource busy
Jun 08 16:17 : problems opening audio device while playing "7/Parsifal2.ape"

---

### Post by dioltas on 2009-06-08
lol at smileys in log file! :)

Ok, loads of errors there. It seems the problem is with alsa. Did you try closing all other media players, like mplayer and restarting mpd? See if that helps. alsa controls the sound on your computer. I think the reason id something to do with whether your sound card supports hardward mixing.


After the groupadd, you still have to run "sudo usermod -a -G mpd mpd" then groups command should show both audio and mpd. As I said, I doubt that's the problem.

---

### Post by bgc on 2009-06-08
Hi, ok, now I get audio mpd for 'groups mpd'. I killed mpd again, mplayer isn't playing, tried restarting, and get the same issue (i.e. now it doesn't actually even play, it hints at starting and then stops). No sound either.

Does mplayer not use ALSA? I mean, how can I get sound from mplayer, aqualung, gmusicbrowser, audacious (i.e. a rather big range of players, I don't know what program they use)?

Sorry about the smileys! :)

---

### Post by dioltas on 2009-06-08
Think this is the same problem:
[https://bugs.launchpad.net/ubuntu/+source/mpd/+bug/192735](https://bugs.launchpad.net/ubuntu/+source/mpd/+bug/192735)

Maybe try John Smith's solution a bit down the page,
> 
audio_output {
type "pulse"
driver "esd"
options "host=localhost"
name "esd"
}

change settings to that in your mpd.conf file. I think it seems to be a ubuntu problem judging from the comments on that page.

---

### Post by dioltas on 2009-06-08
I'm not 100% sure tbh, as I said I remember sometimes if I had more that one audio player open I used to have problems under ubuntu. Wouldn't be an expert on it anyway!

Maybe someone else knows more about it? I'm using alsa on this computer (arch linux), and everything plays fine.

**Edit:** [http://www.musicpd.org/forum/index.php?topic=1587.0](http://www.musicpd.org/forum/index.php?topic=1587.0) here's another thread on the same problem (I think).

---

### Post by bgc on 2009-06-08
Hi, thanks again for your ongoing help! I have changed mpd.conf with those settings. Now, ncmpc seems to be playing again, with no sound! As a probably meaningless note, the time passes by in jolts, sometimes two seconds at a time...

I tried the paplay /usr/share/sounds/alsa/Front_Center.wav thing mentioned in the launchpad page you mention, and it works. I'm getting really confused...

---

### Post by dioltas on 2009-06-08
Maybe try step 3 here.

[QUOTE=http://www.musicpd.org/forum/index.php?topic=1587.0]
1. I apt-get installed mpd
2. set type "pulse" as audio output
3. edit /etc/pulse/default.pa and add
load-module module-native-protocol-tcp auth-anonymous=1
this gives permission to everybody to use pulse.
4. start mpd
5. play music


So mpd is just fine.[/QUOTE]

Mpd should be set up to use pulse after the last step you did. Maybe post up your mpd.error file again and see what it's saying now. Not sure why the time is like that now...

---

### Post by bgc on 2009-06-08
No luck still! No sound...

Here's mpd.error:

> No protocol specified
E: client-conf-x11.c: XOpenDisplay() failed
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
[WARN 11595] polkit-session.c:144:polkit_session_set_uid(): session != NULL
 Not built with -rdynamic so unable to print a backtrace
No protocol specified
E: client-conf-x11.c: XOpenDisplay() failed
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
[WARN 11737] polkit-session.c:144:polkit_session_set_uid(): session != NULL
 Not built with -rdynamic so unable to print a backtrace
No protocol specified
E: client-conf-x11.c: XOpenDisplay() failed
Jun 08 16:16 : can't find alsa mixer_control "PCM"
Jun 08 16:16 : using software volume
Jun 08 16:16 : Error opening ALSA device "hw:0,0": Device or resource busy
Jun 08 16:16 : problems opening audio device while playing "7/Parsifal1.ape"
Jun 08 16:16 : problems opening audio device while playing "7/Parsifal1.ape"
Jun 08 16:16 : Error opening ALSA device "hw:0,0": Device or resource busy
Jun 08 16:16 : problems opening audio device while playing "7/Parsifal1.ape"
Jun 08 16:16 : problems opening audio device while playing "7/Parsifal1.ape"
Jun 08 16:17 : Error opening ALSA device "hw:0,0": Device or resource busy
Jun 08 16:17 : problems opening audio device while playing "7/Parsifal1.ape"
No protocol specified
E: client-conf-x11.c: XOpenDisplay() failed
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
[WARN 12651] polkit-session.c:144:polkit_session_set_uid(): session != NULL
 Not built with -rdynamic so unable to print a backtrace
No protocol specified
E: client-conf-x11.c: XOpenDisplay() failed
Jun 08 17:16 : can't find alsa mixer_control "PCM"
Jun 08 17:16 : using software volume
Jun 08 17:17 : Error opening ALSA device "hw:0,0": Device or resource busy
Jun 08 17:17 : problems opening audio device while playing "7/Parsifal1.ape"
Jun 08 17:17 : problems opening audio device while playing "7/Parsifal2.ape"
No protocol specified
E: client-conf-x11.c: XOpenDisplay() failed
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
[WARN 12871] polkit-session.c:144:polkit_session_set_uid(): session != NULL
 Not built with -rdynamic so unable to print a backtrace
No protocol specified
E: client-conf-x11.c: XOpenDisplay() failed
Jun 08 17:27 : can't find alsa mixer_control "PCM"
Jun 08 17:27 : using software volume
No protocol specified
E: client-conf-x11.c: XOpenDisplay() failed
No protocol specified
E: client-conf-x11.c: XOpenDisplay() failed
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
[WARN 13041] polkit-session.c:144:polkit_session_set_uid(): session != NULL
 Not built with -rdynamic so unable to print a backtrace
No protocol specified
E: client-conf-x11.c: XOpenDisplay() failed
Jun 08 17:37 : can't find alsa mixer_control "PCM"
Jun 08 17:37 : using software volume
No protocol specified
E: client-conf-x11.c: XOpenDisplay() failed
No protocol specified
E: client-conf-x11.c: XOpenDisplay() failed
No protocol specified
E: client-conf-x11.c: XOpenDisplay() failed
No protocol specified
E: client-conf-x11.c: XOpenDisplay() failed
No protocol specified
E: client-conf-x11.c: XOpenDisplay() failed
No protocol specified
E: client-conf-x11.c: XOpenDisplay() failed

I've also tried with other file formats (just in case it was having issues with ape), but still the same.

---

### Post by dioltas on 2009-06-08
I'm not sure what the problem is man.

Jun 08 17:37 : can't find alsa mixer_control "PCM"
If you run "alsamixer" on my comp there is a column called pcm and it's this that the volume in mpd controls. Maybe try turning up all of the columns and making sure none are muted (by pressing m).

Otherwise maybe try running alsaconf, just be careful that you don't mess up your normal sound settings. Actually now that i think of it, that probably won't help cause your other apps seem to be working fine, so better off not running alsaconf.

Also try running "xhost + mpd" or "sudo xhost + mpd" to fix the XOpenDisplay() failed error. Got that from this page:

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/192735/+viewstatus](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/192735/+viewstatus)

and don't forget to restart mpd after. Not sure if it'd be necessary to restart x or not.

---

### Post by bgc on 2009-06-08
Hi, no worries, thanks for your patient help!

I checked alsamixer, and Front mic was down, but putting it all the way up just increases noise, but doesn't play back music. Mic was down as well, but still doesn't change anything.

I ran the line 'xhost + mpd' and got 'xhost: bad hostname "mpd"'...

I'll have to leave soon, so I'll only be able to continue later on this evening or tomorrow, but again thanks very much for your help!!!

---

### Post by dioltas on 2009-06-08
No bother, sorry I couldn't help more. 

Did you try the "sudo xhost + mpd" command. Maybe do that and post the error log again.

---

### Post by bgc on 2009-06-08
Here's the output of mpd.error (that is without an X restart):

```

No protocol specified
E: client-conf-x11.c: XOpenDisplay() failed
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
[WARN 11595] polkit-session.c:144:polkit_session_set_uid(): session != NULL
 Not built with -rdynamic so unable to print a backtrace
No protocol specified
E: client-conf-x11.c: XOpenDisplay() failed
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
[WARN 11737] polkit-session.c:144:polkit_session_set_uid(): session != NULL
 Not built with -rdynamic so unable to print a backtrace
No protocol specified
E: client-conf-x11.c: XOpenDisplay() failed
Jun 08 16:16 : can't find alsa mixer_control "PCM"
Jun 08 16:16 : using software volume
Jun 08 16:16 : Error opening ALSA device "hw:0,0": Device or resource busy
Jun 08 16:16 : problems opening audio device while playing "7/Parsifal1.ape"
Jun 08 16:16 : problems opening audio device while playing "7/Parsifal1.ape"
Jun 08 16:16 : Error opening ALSA device "hw:0,0": Device or resource busy
Jun 08 16:16 : problems opening audio device while playing "7/Parsifal1.ape"
Jun 08 16:16 : problems opening audio device while playing "7/Parsifal2.ape"
Jun 08 16:17 : Error opening ALSA device "hw:0,0": Device or resource busy
Jun 08 16:17 : problems opening audio device while playing "7/Parsifal1.ape"
No protocol specified
E: client-conf-x11.c: XOpenDisplay() failed
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
[WARN 12651] polkit-session.c:144:polkit_session_set_uid(): session != NULL
 Not built with -rdynamic so unable to print a backtrace
No protocol specified
E: client-conf-x11.c: XOpenDisplay() failed
Jun 08 17:16 : can't find alsa mixer_control "PCM"
Jun 08 17:16 : using software volume
Jun 08 17:17 : Error opening ALSA device "hw:0,0": Device or resource busy
Jun 08 17:17 : problems opening audio device while playing "7/Parsifal1.ape"
Jun 08 17:17 : problems opening audio device while playing "7/Parsifal1.ape"
No protocol specified
E: client-conf-x11.c: XOpenDisplay() failed
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
[WARN 12871] polkit-session.c:144:polkit_session_set_uid(): session != NULL
 Not built with -rdynamic so unable to print a backtrace
No protocol specified
E: client-conf-x11.c: XOpenDisplay() failed
Jun 08 17:27 : can't find alsa mixer_control "PCM"
Jun 08 17:27 : using software volume
No protocol specified
E: client-conf-x11.c: XOpenDisplay() failed
No protocol specified
E: client-conf-x11.c: XOpenDisplay() failed
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
[WARN 13041] polkit-session.c:144:polkit_session_set_uid(): session != NULL
 Not built with -rdynamic so unable to print a backtrace
No protocol specified
E: client-conf-x11.c: XOpenDisplay() failed
Jun 08 17:37 : can't find alsa mixer_control "PCM"
Jun 08 17:37 : using software volume
No protocol specified
E: client-conf-x11.c: XOpenDisplay() failed
No protocol specified
E: client-conf-x11.c: XOpenDisplay() failed
No protocol specified
E: client-conf-x11.c: XOpenDisplay() failed
No protocol specified
E: client-conf-x11.c: XOpenDisplay() failed
No protocol specified
E: client-conf-x11.c: XOpenDisplay() failed
No protocol specified
E: client-conf-x11.c: XOpenDisplay() failed
No protocol specified
E: client-conf-x11.c: XOpenDisplay() failed
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
[WARN 13344] polkit-session.c:144:polkit_session_set_uid(): session != NULL
 Not built with -rdynamic so unable to print a backtrace
No protocol specified
E: client-conf-x11.c: XOpenDisplay() failed
Jun 08 17:56 : can't find alsa mixer_control "PCM"
Jun 08 17:56 : using software volume
No protocol specified
E: client-conf-x11.c: XOpenDisplay() failed
No protocol specified
E: client-conf-x11.c: XOpenDisplay() failed
No protocol specified
E: client-conf-x11.c: XOpenDisplay() failed
No protocol specified
E: client-conf-x11.c: XOpenDisplay() failed
No protocol specified
E: client-conf-x11.c: XOpenDisplay() failed
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
[WARN 13368] polkit-session.c:144:polkit_session_set_uid(): session != NULL
 Not built with -rdynamic so unable to print a backtrace
No protocol specified
E: client-conf-x11.c: XOpenDisplay() failed
Jun 08 17:58 : can't find alsa mixer_control "PCM"
Jun 08 17:58 : using software volume
No protocol specified
E: client-conf-x11.c: XOpenDisplay() failed
No protocol specified
E: client-conf-x11.c: XOpenDisplay() failed
No protocol specified
E: client-conf-x11.c: XOpenDisplay() failed
No protocol specified
E: client-conf-x11.c: XOpenDisplay() failed
No protocol specified
E: client-conf-x11.c: XOpenDisplay() failed
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
[WARN 13539] polkit-session.c:144:polkit_session_set_uid(): session != NULL
 Not built with -rdynamic so unable to print a backtrace
No protocol specified
E: client-conf-x11.c: XOpenDisplay() failed
Jun 08 18:01 : can't find alsa mixer_control "PCM"
Jun 08 18:01 : using software volume
No protocol specified
E: client-conf-x11.c: XOpenDisplay() failed
No protocol specified
E: client-conf-x11.c: XOpenDisplay() failed
No protocol specified
E: client-conf-x11.c: XOpenDisplay() failed
No protocol specified
E: client-conf-x11.c: XOpenDisplay() failed
Jun 08 18:02 : can't find alsa mixer_control "PCM"
Jun 08 18:02 : using software volume
No protocol specified
E: client-conf-x11.c: XOpenDisplay() failed
No protocol specified
E: client-conf-x11.c: XOpenDisplay() failed
No protocol specified
E: client-conf-x11.c: XOpenDisplay() failed
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
[WARN 13578] polkit-session.c:144:polkit_session_set_uid(): session != NULL
 Not built with -rdynamic so unable to print a backtrace
No protocol specified
E: client-conf-x11.c: XOpenDisplay() failed
Jun 08 18:03 : can't find alsa mixer_control "PCM"
Jun 08 18:03 : using software volume
No protocol specified
E: client-conf-x11.c: XOpenDisplay() failed
```

---

### Post by bgc on 2009-06-09
OK, I have no idea why or what or when, but evidently restarting X eventually did the trick and it now seems to work! Thanks for your help!!!

---

### Post by dioltas on 2009-06-09
Hey, nice 1! Glad I could help.

---

