---
title: "Bluetooth-Alsa Headphone Problems"
date: 2007-04-03
forum: Multimedia &amp; Video
---

### Post by nellering on 2007-04-03
I have a pair of  logitech bluetooth headphones.  I have  been trying to get them to audio sync with my Ubuntu 6.10 install.  I followed the directions on the [http://bluetooth-alsa.sourceforge.net/build.html](http://bluetooth-alsa.sourceforge.net/build.html) page.  I get up to the point where I run a2dpd with the bluetooth headphones in discoverable mode.  This is the output I get

```
nick@nick-laptop:~$ a2dpd
A2DPD[00:55:31.525]: init_ipc: Selected IPC: unix, addr=127.0.0.1, bcst=127.0.0.255, port=21453
A2DPD[00:55:31.525]: make_daemon_process: a2dpd [Apr  3 2007 00:30:17] starting ...
A2DPD[00:55:31.526]: main: (errno=9:Bad file descriptor)a2dpd addr=00:0D:44:49:67:BF timer=4000 us [Apr  3 2007 00:30:31]
A2DPD[00:55:31.526]: a2dpd_signal_init: Getting on DBUS
A2DPD[00:55:31.531]: a2dpd_signal_init: Installing watch
A2DPD[00:55:31.532]: add_dbus_watch: Added watch 0 0x809a7c0 disabled
A2DPD[00:55:31.532]: add_dbus_watch: Added watch 1 0x809a7e8 enabled
A2DPD[00:55:31.532]: a2dpd_signal_init: Registering object path: /com/access/a2dpd
A2DPD[00:55:31.532]: a2dpd_signal_init: Acquiring service: com.access.a2dpd
A2DPD[00:55:31.534]: a2dpd_signal_init: OK
A2DPD[00:55:31.534]: a2dpd_signal_init: OK
A2DPD[00:55:31.575]: a2dpd_register_sdp: OK
A2DPD[00:55:31.576]: add_avrtg: 
A2DPD[00:55:31.577]: add_a2source: 
A2DPD[00:55:31.577]: main_loop: 
A2DPD[00:55:31.577]: make_server_socket: 
A2DPD[00:55:31.577]: bta2dpdevicenew: 
A2DPD[00:55:31.577]: a2dpd_signal_address_changed: 00:0D:44:49:67:BF
A2DPD[00:55:31.578]: a2dpd_signal_set_socket: Signal socket set to 7
A2DPD[00:55:31.579]: a2dpd_signal_state: Disconnected 
A2DPD[00:55:31.580]: a2dp_alloc: 
A2DPD[00:55:31.580]: a2dp_alloc: (a2dp = 0x809faa0)
A2DPD[00:55:31.580]: a2dp_new: 00:0D:44:49:67:BF, 44100
A2DPD[00:55:31.580]: a2dp_new: State AVDTP_STATE_DISCONNECTED
A2DPD[00:55:31.580]: alsa_new: 
A2DPD[00:55:31.580]: alsa_new: device=plughw:0,0, framerate=44100
A2DPD[00:55:31.580]: alsa_new: State ALSA_STATE_DISCONNECTED
A2DPD[00:55:31.580]: alsa_new: returning 0x80a1c28
A2DPD[00:55:31.581]: sco_new: 
A2DPD[00:55:31.581]: sco_new: State SCO_STATE_DISCONNECTED
A2DPD[00:55:31.581]: sco_state_disconnect: Filtering state : already disconnected
A2DPD[00:55:31.581]: main_loop: Bluetooth Device Settings [44100 hz, 2 channels, 16 bits]
A2DPD[00:55:31.582]: avrcp_new: Listening for AVRCP on socket 9
A2DPD[00:55:31.582]: avrcp_new: 0x80a1d38
A2DPD[01:04:00.138]: sigint_handler: handling SIGINT
A2DPD[01:04:00.138]: alsa_destroy: 
A2DPD[01:04:00.138]: alsa_state_disconnect: State ALSA_STATE_DISCONNECTED
A2DPD[01:04:00.138]: alsa_destroy: OK
A2DPD[01:04:00.138]: a2dp_destroy: a2dp = 0xbfe15aa4
A2DPD[01:04:00.138]: a2dp_free: Disconnecting
A2DPD[01:04:00.138]: a2dp_disconnect: 
A2DPD[01:04:00.138]: a2dp_stream_stop: Closing stream socket 0
A2DPD[01:04:00.138]: a2dp_stream_stop: Closed
A2DPD[01:04:00.138]: a2dp_stream_stop: State AVDTP_STATE_IDLE
A2DPD[01:04:00.138]: a2dp_disconnect: Closing ctl socket 0
A2DPD[01:04:00.139]: a2dp_disconnect: Closed
A2DPD[01:04:00.139]: a2dp_disconnect: State AVDTP_STATE_DISCONNECTED
A2DPD[01:04:00.139]: a2dp_free: Freeing sbc
A2DPD[01:04:00.139]: a2dp_free: (a2dp = 0x809faa0)
A2DPD[01:04:00.139]: a2dp_free: OK
A2DPD[01:04:00.139]: sco_destroy: sco = 0xbfe15aa8
A2DPD[01:04:00.139]: sco_free: Disconnecting
A2DPD[01:04:00.139]: sco_free: (sco = 0x809ada8)
A2DPD[01:04:00.139]: close_socket: Closing 9
A2DPD[01:04:00.140]: avrcp_destroy: 0x80a1d38
A2DPD[01:04:00.140]: a2dpd_signal_set_socket: Signal socket set to -1
A2DPD[01:04:00.140]: close_socket: Closing 8
A2DPD[01:04:00.140]: close_socket: Closing 7
A2DPD[01:04:00.140]: close_socket: Closing 6
A2DPD[01:04:00.140]: a2dpd_unregister_sdp: OK
A2DPD[01:04:00.140]: a2dpd_signal_kill: OK
A2DPD[01:04:00.140]: main: Terminated succesfully

```

The following is my .a2dprc file
```
[a2dpd]
#
# Rate
# use 32000 if your headset seems to not support 44100 (HP/Logitech works well at 44100, Sonorix at 32000)
# However, 44100 is mandatory
# If using SCO, then 8000hz is the value needed.
# if the plugin do not give the 8000hz stream, then the conversion will be done by the daemon
# Until we use a real resample library, we won't get a good quality, this is prototype software.
#
rate=44100
#rate=32000

# buggy if I remember well
#channels=2

#
# plugin-rate default is the rate used between the plugin and the daemon
# if this value is not 0 then alsa will convert all stream to the specified rate and then send it to the daemon
# if this value is 0, then alsa will do no conversion at all, the daemon will do it's own resampling.
# This "features" is disabled because of the crappy quality of the daemon resampler
# For example, to test a2dpd resampling from 32000 to 44100 use plugin-rate=32000 and rate=44100
#plugin-rate=32000

# Allows to specify the sbc bitpool, this can help reducing bandwith
# 8 Allows to run on a 115200 bauds with corresponding quality ;)
# 64 needs USB or 921600 bauds
# Recommended value from Bluetooth spec. is 53
sbcbitpool=32

# flags that will later be combinable
# 1: display bandwith each seconds.
# 3: current state
flags=0

# Recommended
enablereversestereo=1

# Automatically connect to selected headset if a stream if started
# not recommended if running on battery ;)
enableautoconnect=1

# Automatically disconnect after a timeout (1 <=> 3ms)
timeout=2000

#
# AVRCP Commands to run
# If these entries are emptied, then some keyboard entry will be sent to /dev/uinput
#
cmdplay=xmms --play
cmdpause=xmms --pause
cmdprev=xmms --rew
cmdnext=xmms --fwd
cmdnew=xmms --play
cmdstop=xmms --stop
#cmdplay=dcop amarok player play
#cmdpause=dcop amarok player pause
#cmdprev=dcop amarok player prev
#cmdnext=dcop amarok player next
#cmdnew=dcop amarok player play
#cmdstop=dcop amarok player stop

# Put to 0 to ignore AVRCP (if your computer freezes when commands are received)
enableavrcp=1

#
# Audio routing
#
# If set to 1 (at a2dp startup only) a2dp will reread configuration file
# for audio routing changes each second
enablerereadconfig=1

# Display debug traces or not
enabledebug=1

# Redirect stdout to this file
#logfile=/dev/null

# Poll stdin for control commands ('c'onnect/'s'tart/'p'ause/'d'isconnect/'a'utoconnect)
# Use a2dpd_ctl instead
enablestdin=0

# 0 => Bluetooth A2DP Sink
# 1 => Alsa
enableredirectalsa=0

# Your bluetooth headset address
address=00:0D:44:49:67:BF

# Address of your alsa output (default : plughw:0,0) you have to know what to do
alsaoutput=

```

Does anyone know  what is wrong?

---

### Post by emil10001 on 2007-05-01
Bump. 

Has anyone had luck with this. The instructions on the bluetooth-alsa page are a bit lacking. Are there more detailed instructions somewhere else? Or some sort of troubleshooting page?

For me, everything seems to compile/install fine. I can find my headphones with hcitool scan, then connect with hcitool cc <BDADDR>, but i get a similar output when i run a2dpd (needs to be run as root), and i get errors when trying to specify that output mplayer -ao alsa:device=headset, or xmms device = a2dpd . 

Like I said, I'm mostly looking for where to go for answers, currently I haven't found anything useful googling, and I'm searching the bluez-devel mailing list for info. If I don't get a reply here, I'll ask over there and post back here if I get it working.

-John

---

### Post by emil10001 on 2007-05-01
Ok, I got mine going, xmms still doesn't do it, but mplayer is, so I can go from there. Here's what I did:
go into plugz/alsa-plugins/a2dpd/.libs/ and copy the libasound_module_pcm_a2dpd* to /usr/lib/alsa-lib/ (and/or /usr/lib64/alsa-lib/). After that, it worked fine.

If that doesn't help, go to the bluez mailing lists on sourceforge.net and search for a2dp.
[http://sourceforge.net/mail/?group_id=26526](http://sourceforge.net/mail/?group_id=26526)

Hope this helps.
-John

---

### Post by Arless on 2007-05-29
With xmms and mplayer i cant see the a2dpd device but with audacity i can use it perfectly, someone know how to configure the other progs like audacity?

---

