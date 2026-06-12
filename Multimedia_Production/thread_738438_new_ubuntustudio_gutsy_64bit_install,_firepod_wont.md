---
title: "new ubuntustudio gutsy 64bit install, firepod wont work"
date: 2008-03-28
forum: Multimedia Production
---

### Post by FieldbornTemple on 2008-03-28
I just installed UbuntuStudio Gutsy 64bit on my amd64 4000+ system. I own a presonus firepod and can not get it to work with Jack or anything else on my new linux system. What am I not doing? The red light will not turn blue. I have read through these forums about everything regarding the firepod but have found no help to work yet. I must confess I am very poor at working in the terminal window. But all the same I did try. 
Any help would be hugely appreciated. Thank you in advance!

---

### Post by Stochastic on 2008-03-28
One of the most common problems is that audio is not given permission to access the firewire devices.  How to fix this is:
open terminal and do ```
sudo gedit /etc/udev/rules.d/40-permissions.rules
```
then find the line that has:
KERNEL=="raw1394",                      GROUP="disk"
and change it to:
KERNEL=="raw1394",                      GROUP="audio"
then save the file and close the editor.

now when you run qjackctl, go into settings and choose freebob as the driver.  If this doesn't work let me know I'll be happy to help further.

---

### Post by FieldbornTemple on 2008-03-29
I had actually already tried that, in a way... I think I did it a bit wrong though, someone said to change it to that line also, but I removed the other KERNAL notes too. There should be something about dv1934 as well right? Oops. Is there a way to get back the other lines? But as it is below I pasted what my 40-permissions.rules file contains on that subject......

# IEEE1394 (firewire) devices
# Please note that raw1394 gives unrestricted, raw access to every single
# device on the bus and those devices may do anything as root on your system.
# Yes, I know it also happens to be the only way to rewind your video camera,
# but it's not going to be group "video", okay?
KERNEL=="raw1394",			GROUP="audio"

I am capable of learning quickly, but yet I may be doing something wrong in Jackctrl too.

---

### Post by Stochastic on 2008-03-29
The lines (of that section) in your 40-permissions.rules file should read:

# IEEE1394 (firewire) devices
# Please note that raw1394 gives unrestricted, raw access to every single
# device on the bus and those devices may do anything as root on your system.
# Yes, I know it also happens to be the only way to rewind your video camera,
# but it's not going to be group "video", okay?
KERNEL=="raw1394",                      GROUP="audio"
KERNEL=="dv1394*",                      GROUP="video"
KERNEL=="video1394*",                   GROUP="video"

so if you have that correct, try this:

-have your firepod fully plugged in and powered up
-reboot your computer
-open a terminal and do ```
jackd -v -R -d freebob
```
-post the resulting messages that the code spews out

---

### Post by FieldbornTemple on 2008-03-31
fieldborntemple@ubuntu:~$ jackd -v -R -d freebob
getting driver descriptor from /usr/lib64/jack/jack_oss.so
getting driver descriptor from /usr/lib64/jack/jack_dummy.so
getting driver descriptor from /usr/lib64/jack/jack_freebob.so
getting driver descriptor from /usr/lib64/jack/jack_alsa.so
jackd 0.103.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
server `default' registered
registered builtin port type 32 bit float mono audio
registered builtin port type 8 bit raw midi
clock source = system clock via clock_gettime
loading driver ..
Enhanced3DNow! detected
SSE2 detected
Freebob using Firewire port 0, node -1
new client: freebob_pcm, id = 1 type 1 @ 0x62baa0 fd = -1
new buffer size 1024
LibFreeBoB MSG: FreeBoB Streaming Device Init
LibFreeBoB MSG:  Using FreeBoB lib version libfreebob 1.0.3
LibFreeBoB MSG:  Device information:
LibFreeBoB MSG:  Device options:
LibFreeBoB MSG:   Port                     : 0
LibFreeBoB MSG:   Device Node Id           : -1
LibFreeBoB MSG:   Samplerate               : 48000
LibFreeBoB MSG:   Period Size              : 1024
LibFreeBoB MSG:   Nb Buffers               : 3
LibFreeBoB MSG:   Directions               : 0
showDevice: not implemented
FreeBoB MSG: Register MIDI IN port dev1c_MidiIn
FreeBoB MSG: Register MIDI OUT port dev1p_MidiOut
FreeBoB MSG: Streaming thread running with Realtime scheduling, priority 14
FreeBoB MSG: Registering capture port dev1c_LineIn 1+2 left
FreeBoB MSG: Registering capture port dev1c_LineIn 1+2 right
FreeBoB MSG: Registering capture port dev1c_LineIn 3+4 left
FreeBoB MSG: Registering capture port dev1c_LineIn 3+4 right
FreeBoB MSG: Registering capture port dev1c_LineIn 5+6 left
FreeBoB MSG: Registering capture port dev1c_LineIn 5+6 right
FreeBoB MSG: Registering capture port dev1c_LineIn 7+8 left
FreeBoB MSG: Registering capture port dev1c_LineIn 7+8 right
FreeBoB MSG: Registering capture port dev1c_SpdifIn left
FreeBoB MSG: Registering capture port dev1c_SpdifIn right
FreeBoB MSG: Don't register capture port dev1c_MidiIn
FreeBoB MSG: Registering playback port dev1p_LineOut 1+2 left
FreeBoB MSG: Registering playback port dev1p_LineOut 1+2 right
FreeBoB MSG: Registering playback port dev1p_LineOut 3+4 left
FreeBoB MSG: Registering playback port dev1p_LineOut 3+4 right
FreeBoB MSG: Registering playback port dev1p_LineOut 5+6 left
FreeBoB MSG: Registering playback port dev1p_LineOut 5+6 right
FreeBoB MSG: Registering playback port dev1p_LineOut 7+8 left
FreeBoB MSG: Registering playback port dev1p_LineOut 7+8 right
FreeBoB MSG: Registering playback port dev1p_SpdifOut left
FreeBoB MSG: Registering playback port dev1p_SpdifOut right
FreeBoB MSG: Don't register playback port dev1p_MidiOut
registered port freebob_pcm:dev1c_LineIn 1+2 left, offset = 4096
registered port freebob_pcm:dev1c_LineIn 1+2 right, offset = 8192
registered port freebob_pcm:dev1c_LineIn 3+4 left, offset = 12288
registered port freebob_pcm:dev1c_LineIn 3+4 right, offset = 16384
registered port freebob_pcm:dev1c_LineIn 5+6 left, offset = 20480
registered port freebob_pcm:dev1c_LineIn 5+6 right, offset = 24576
registered port freebob_pcm:dev1c_LineIn 7+8 left, offset = 28672
registered port freebob_pcm:dev1c_LineIn 7+8 right, offset = 32768
registered port freebob_pcm:dev1c_SpdifIn left, offset = 36864
registered port freebob_pcm:dev1c_SpdifIn right, offset = 40960
registered port freebob_pcm:dev1p_LineOut 1+2 left, offset = 0
registered port freebob_pcm:dev1p_LineOut 1+2 right, offset = 0
registered port freebob_pcm:dev1p_LineOut 3+4 left, offset = 0
registered port freebob_pcm:dev1p_LineOut 3+4 right, offset = 0
registered port freebob_pcm:dev1p_LineOut 5+6 left, offset = 0
registered port freebob_pcm:dev1p_LineOut 5+6 right, offset = 0
registered port freebob_pcm:dev1p_LineOut 7+8 left, offset = 0
registered port freebob_pcm:dev1p_LineOut 7+8 right, offset = 0
registered port freebob_pcm:dev1p_SpdifOut left, offset = 0
registered port freebob_pcm:dev1p_SpdifOut right, offset = 0
++ jack_rechain_graph():
client freebob_pcm: internal client, execution_order=0.
-- jack_rechain_graph()
FreeBoB MSG: MIDI threads running with Realtime scheduling, priority 13
FreeBoB MSG: MIDI queue thread started
libiec61883 warning: Established connection on channel 0.
You may need to manually set the channel on the receiving node.
libiec61883 warning: Established connection on channel 1.
You may need to manually set the channel on the transmitting node.
6320 waiting for signals
load = 0.6117 max usecs: 261.000, spare = 21072.000
load = 0.9317 max usecs: 267.000, spare = 21066.000
load = 1.1268 max usecs: 282.000, spare = 21051.000
load = 1.2689 max usecs: 301.000, spare = 21032.000
load = 1.2040 max usecs: 243.000, spare = 21090.000
load = 1.2278 max usecs: 267.000, spare = 21066.000
load = 1.2983 max usecs: 292.000, spare = 21041.000
load = 1.2890 max usecs: 273.000, spare = 21060.000
load = 0.9914 max usecs: 148.000, spare = 21185.000
load = 0.8355 max usecs: 145.000, spare = 21188.000
load = 0.7412 max usecs: 138.000, spare = 21195.000
load = 0.9941 max usecs: 266.000, spare = 21067.000
load = 1.1369 max usecs: 273.000, spare = 21060.000
load = 1.1684 max usecs: 256.000, spare = 21077.000
load = 1.2335 max usecs: 277.000, spare = 21056.000
load = 1.2660 max usecs: 277.000, spare = 21056.000
load = 1.2892 max usecs: 280.000, spare = 21053.000
load = 1.2118 max usecs: 242.000, spare = 21091.000
load = 1.2153 max usecs: 260.000, spare = 21073.000
load = 1.1842 max usecs: 246.000, spare = 21087.000
load = 1.2484 max usecs: 280.000, spare = 21053.000
... and lines  like this continue on until the entire terminal window is filled from top to bottom and it just keeps coming without stop.

---

### Post by Stochastic on 2008-03-31
Congrats, you got jack to run! (and consequently the firepod light to turn blue?)

Now while jack is running you can open any program that depends on it (including qjackctl, or patchage to make connections between other apps).
Next time you won't have to bother with the command line, you can just simply open qjackctl (go into setup and change the driver to freebob) then hit start and you're off to the races.

---

### Post by FieldbornTemple on 2008-04-07
Hey thank you! I was too busy to return to my computer lately but having tried it it does work. Thank you very much. Now to spend some time figuring out all of the details of Jack and Ardour. 
So it does work, thank you!
It isn´t a real problem for me, but it seems I do need the ¨jackd -v -R -d freebob¨ program to be running in order for my firepod to work. When I close it the firepod light goes back to red and won´t work. Even after restarting and whatnot. But as it  is it does work, and I thank you very much for your instruction. 
Thanks again!

---

### Post by Stochastic on 2008-04-08
Yeah once you've killed jack then you'll need to unplug and re-plug the firewire cable to get jack started again.  Are you able to get it working with qjackctl?  If not, chances are that it's a settings issue in qjackctl.
Oh and you don't need to use the '-v' flag on a regular basis (it's the verbose flag) just when troubleshooting.

---

### Post by FieldbornTemple on 2008-04-10
Yes, jackctrl does work with the firepod so long as I keep the terminal window upon with that ¨jackd -R -d freebob¨ command. I did try unplugging the cable and restarting jack, but if there is a very specific method I may have not done it exactly  properly.

---

### Post by Stochastic on 2008-04-10
Sorry, I meant is qjackctl able to start jack on its own?  (after a fresh boot, open qjackctl choose freebob in the settings and click start)

---

### Post by FieldbornTemple on 2008-04-12
Not on it´s own... I get this message when I try to start Jack on it´s own...



01:43:06.644 Patchbay deactivated.
01:43:06.692 Statistics reset.
JACK tmpdir identified as [/dev/shm]
01:43:06.879 MIDI connection graph change.
01:43:06.948 MIDI connection change.
01:43:07.991 Startup script...
01:43:07.992 artsshell -q terminate
JACK tmpdir identified as [/dev/shm]
01:43:08.224 Startup script terminated with exit status=256.
01:43:08.224 JACK is starting...
01:43:08.224 jackd-realtime -R -u -dfreebob -dhw:0 -r96000 -p32 -n3 -D
01:43:08.227 Could not start JACK. Sorry.
01:43:11.020 JACK was stopped successfully.
01:43:11.022 Post-shutdown script...
01:43:11.024 killall jackd
jackd: no process killed
01:43:11.263 Post-shutdown script terminated with exit status=256.

---

### Post by Stochastic on 2008-04-12
Okay, try going into qjackctl settings, turning off "Unlock Memory", setting your Frames/Period to 256 (or 128 if you need it), turn on "Verbose Message Output", save your preferences, then unplug the firewire cable, plug it back in, and try to start it again.  If it doesn't start please post a screenshot of your preferences panel.

---

### Post by FieldbornTemple on 2008-04-12
It still won´t start from Jack Control. Here is a screenshot of my Jack settings.
[http://picasaweb.google.com/decipherthevoices/Desktop](http://picasaweb.google.com/decipherthevoices/Desktop)

---

### Post by Stochastic on 2008-04-13
Okay, try making these alterations:

-Change the server path to jackd (might want to try jackd-realtime)
-Turn on the Realtime option
-Change port maximum to 512
and if it still doesn't work switch your sample rate to 44100 or 48000

I notice you have the 'Monitor', 'H/W monitor', and 'H/W Meter' x'ed but greyed, mine aren't x'ed but are also greyd (don't know how to change that).

How far does that get you?

---

### Post by FieldbornTemple on 2008-04-13
Only changing the server path to jackd made any difference. It still didn´t work, but it did take about 5 seconds to try before failing. Whereas all previous attempts failed instantly. None of the other changes made any difference. 

The grayed boxes you were talking about, I found I can change the driver from freebob to something else, that allows the boxes to be unchecked, then changing back to freebob.

---

### Post by Stochastic on 2008-04-13
Well when you call jackd from the command line with ```
jackd -R -d freebob 
``` you're asking jackd to start using realtime mode (-R) and the freebob driver (-d freebob) everything else is left to run as the default setting (usually 48000fps and 1024 buffer).  If you're able to get jack up and running with that code then it's just a small issue in qjackctl that's stopping things from going smoothly there.  Probably a setting, but maybe something a bit deeper under the hood (maybe something blatant and simple too).  I'd start to muck around in qjackctl's menus to try to find what's not right.  And in the worst case scenario, use the command line until Hardy to comes out, then re-install and hope whatever bug is stopping your firepod disappears.

Oh, and if you're going to be running from the command line instead of qjackctl you may want to read the help portions of jackd ```
 jackd --help 
``` and ```
 jackd -d freebob --help 
``` Also, you may want to look at Patchage as an app that lets you make jack connections and save your configurations (I don't think qjackctl lets you save).

---

### Post by FieldbornTemple on 2008-04-13
Ok. That makes it seem less intimidating, knowing what that command means. So yeah I&#314;l fool around in Jacks settings and see if I can come up with a setting that is the key. Thank you for your help through the duration. You´ve been very kind. I´ll let you know if I get it to work properly, or if I can´t I´ll just keep using the command line. 
Thank you!

---

### Post by t0538109 on 2008-05-23
this is what i got when running the command. Whats wrong?

bowditchstudio@bowditchstudio:~$ jackd -v -R -d freebob
getting driver descriptor from /usr/lib/jack/jack_freebob.so
getting driver descriptor from /usr/lib/jack/jack_dummy.so
getting driver descriptor from /usr/lib/jack/jack_alsa.so
getting driver descriptor from /usr/lib/jack/jack_oss.so
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
server `default' registered
cannot lock down memory for jackd (Cannot allocate memory)
registered builtin port type 32 bit float mono audio
registered builtin port type 8 bit raw midi
clock source = system clock via clock_gettime
loading driver ..
new client: freebob_pcm, id = 1 type 1 @ 0x806fea8 fd = -1
Freebob using Firewire port 0, node -1
new buffer size 1024
JACK: unable to mlock() port buffers: Cannot allocate memory
JACK: unable to mlock() port buffers: Cannot allocate memory
LibFreeBoB MSG: FreeBoB Streaming Device Init
LibFreeBoB MSG:  Using FreeBoB lib version libfreebob 1.0.7
LibFreeBoB MSG:  Device information:
LibFreeBoB MSG:  Device options:
LibFreeBoB MSG:   Port                     : 0
LibFreeBoB MSG:   Device Node Id           : -1
LibFreeBoB MSG:   Samplerate               : 48000
LibFreeBoB MSG:   Period Size              : 1024
LibFreeBoB MSG:   Nb Buffers               : 3
LibFreeBoB MSG:   Directions               : 0
send oops
send oops
send oops
send oops
send oops
send oops

---

