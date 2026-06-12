---
title: "Webcam, so close but not sure what to do next..."
date: 2011-06-25
forum: Multimedia Software
---

### Post by Ken UK on 2011-06-25
Hi,

I have a Creative Optia Pro webcam and I have been trying to get it to work in Skype.

So I have been going through the Ubuntu webcam related pages and so far:

- Tried cheese but doesn't seem to work (hangs up, turns gray, then crashes.
- Skype doesn't pick up any device
- VLC seems to capture and play it back fine through the Video for Linux 2 default device capture option
- Tried running the code it suggested for skype to create a new loader for V4L, didn't do anything.

I read that the normal Optia worked ok with 7.10 for skype by installing UVC drivers:
[https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams)

But then I also read that the drivers are included in the new Kernals by default so you shouldn't need to install them.

What can I try next? I feel like I'm close but I'm missing the last piece to the puzzle because of my lack of knowledge.

Thanks,

Ken

---

### Post by Ken UK on 2011-06-26
I tried ```
lsmod | grep videodev
``` in the terminal too, it came up with this:

```
videodev               75143  10 cx88_blackbird,cx2341x,wm8775,tuner,cx8800,uvcvideo,cx88xx,v4l2_common

```

Any ideas?

---

### Post by no2498 on 2011-06-26
you try the cam in gstreamer-properties

in a terminal type gstreamer-properties click enter
click video
try v4l and v4l2
use the bottom test button for each 1
you may need to change the plugin to auto find your cam

if i use my cam in vlc it stops all other programs from finding my cam
i like the program wxcam
[http://sourceforge.net/projects/wxcam/](http://sourceforge.net/projects/wxcam/)
you can get it in a deb file
also try xawtv and guvcview  both in the repose 
after you get the cam working
retry skype

---

### Post by Ken UK on 2011-06-26
I typed what you said into the terminal and it brought up this:
```

gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lsrc'

```

I tried guvcview but the application wouldn't even start. xawtv switched on my cam and started using it straight away.

So what does this all mean?
Thanks alot for the reply.

---

### Post by no2498 on 2011-06-26
xawtv loads a cam grabber

every one gets some of these

$ gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'

so did the cam come on in gstreamer-properties

gstreamer we need good , bad , ugly , and 0.10 for the ubuntu/linux you use

---

### Post by Ken UK on 2011-06-26
Nothing appeared other than those lines in the terminal...

I'm guessing something went horribly wrong then.

---

### Post by no2498 on 2011-06-26
no just they have stopped putting all the gstreamer's in for us
do you also have the restricted extras installed  

good set bad set ugly set and the 0.10 for your ubuntu/linux

get all the  gstreamer's befor you try skype

---

### Post by Ken UK on 2011-06-26
I'm a Linux newbie so I have no idea what you are talking about. Are these codecs the only thing thats stopping Skype from working?

I clicked installed added extras when installing Ubuntu and I looked in the software centre, I have all the gstreamerr including "Gstreamer extra plugins"

---

### Post by no2498 on 2011-06-26
ubuntu/linux restricted extras 
the one you use
not Gstreamer 
it give you some codes for video

---

### Post by Ken UK on 2011-06-26
Ok I installed Ubuntu Restricted Extras. Now what do I do?
I tried typing that command into the terminal again and nothing happened.

---

### Post by no2498 on 2011-06-26
still not coming up in gstreamer-properties odd
iv only see these two files 2 times 
1 is a gstreamer config this ones kind of new
other is a v4l so v4l2 compat this ones in a skype ?

1  [http://ubuntuforums.org/search.php?searchid=81711151](http://ubuntuforums.org/search.php?searchid=81711151)


2  [http://ubuntuforums.org/search.php?searchid=81711165](http://ubuntuforums.org/search.php?searchid=81711165)

best i could come up with i need to run soon

hope you find them

---

### Post by Ken UK on 2011-06-26
Thanks for the replies, I'm not sure what to think now. I dont really understand this stuff at all so not sure why its not working. Anyone explain how webcams work in Ubuntu and why its so difficult?

---

### Post by Ken UK on 2011-06-27
Calling all webcam experts, why is it so hard to get a webcam working in Ubuntu? Surely they can come up with a better way of getting a webcam working, maybe through 'additional drivers' or something.

---

### Post by no2498 on 2011-06-27
[http://ubuntuforums.org/showthread.php?t=1777612&highlight=cheese](http://ubuntuforums.org/showthread.php?t=1777612&highlight=cheese)

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

swamytk 
Way Too Much Ubuntu

  
 
  
Join Date: Jul 2005
Location: Santa Clara, CA
 Beans: 290 
 Ubuntu Development Release 	Re: Webcam works with Cheese, but not with Skype 
Quote: Originally Posted by befana  
And how to make Skype to run with working webcam without typing in a terminal?
 I am asking this because of my parents - they are too old to type in a terminal.

To create a shortcut for skype with this fix:

 1. Create a simple script shown below with the name launchskype in your home folder
Quote: #!/bin/sh
 export LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so 
skype & 

2. Set it as executable file. In file browser, right click the file and select "Make Link" option. It will create a link. Cut and paste this link to your desktop.
 3. Double click this shortcut to launch skype. If it is prompted to "display or execute", select execute (or make select as default action in nautilus preferences)


[http://ubuntuforums.org/showthread.php?t=993262&highlight=skype](http://ubuntuforums.org/showthread.php?t=993262&highlight=skype)

---

### Post by Ken UK on 2011-06-28
Thanks for the link but it doesnt do anything. It might help my brother though, Skype detects his webcam but doesnt work still.

There must be a way....

---

### Post by Ken UK on 2011-06-29
*Bump*

---

### Post by no2498 on 2011-06-29
that was for skype and cheese
that should help cheese for you
and gstreamer-properties thats what cheese uses
try this program wxcam

[http://sourceforge.net/projects/wxcam/](http://sourceforge.net/projects/wxcam/)

you can get it in a deb file just try 1 till it loads

as your cam does work just not in all programs

---

### Post by no2498 on 2011-06-29
[https://help.ubuntu.com/community/Webcam/Troubleshooting](https://help.ubuntu.com/community/Webcam/Troubleshooting)

---

### Post by Ken UK on 2011-06-30
Thanks for the replies. I had alook through those problems and once I read into them I couldn't find one that sounded like mine.

I keep coming back to the same things and I can't understand why that properties command isn't working. It could be the fact I'm using open graphics drivers, I did read that somewhere.

I know UVC should be already available in 11.04 but maybe it could be that...?

---

### Post by tobiz on 2011-07-01
> **Ken UK said:**
> Thanks for the replies. I had alook through those problems and once I read into them I couldn't find one that sounded like mine.

I keep coming back to the same things and I can't understand why that properties command isn't working. It could be the fact I'm using open graphics drivers, I did read that somewhere.

I know UVC should be already available in 11.04 but maybe it could be that...?
Ken, did you try running Skype from the command line as suggested by ie:
1. Create a simple script shown below with the name launchskype in your home folder
Quote: #!/bin/sh
export LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so
skype & 

If so what was the result?  Was it still no video from the webcam?

If you can get another program to work with the webcam then it strongly suggests it's Skype.  I couldn't get my Philips webcam to work with Skype after installing an update to Skype, the code above fixed it (Ubuntu 10.04).

Try installing guvcview from the Ubuntu Software Centre or synaptic (which I prefer).  If this works then it's Skype.

I just tried the script above and it didn't work!!
My script that I have running is:

#! /bin/sh
# This is a fix published on the Skype web site for V25 (12/04/2011) failing to open video
#
LD_PRELOAD=/usr/lib32/libv4l/v4l2convert.so skype 

You don't have to make a script to run this, just type the last line into a terminal window and hit return, much simpler.

---

### Post by Ken UK on 2011-07-01
> **tobiz said:**
> Ken, did you try running Skype from the command line as suggested by ie:
1. Create a simple script shown below with the name launchskype in your home folder
Quote: #!/bin/sh
export LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so
skype & 

If so what was the result?  Was it still no video from the webcam?

If you can get another program to work with the webcam then it strongly suggests it's Skype.  I couldn't get my Philips webcam to work with Skype after installing an update to Skype, the code above fixed it (Ubuntu 10.04).

Try installing guvcview from the Ubuntu Software Centre or synaptic (which I prefer).  If this works then it's Skype.

I just tried the script above and it didn't work!!
My script that I have running is:

#! /bin/sh
# This is a fix published on the Skype web site for V25 (12/04/2011) failing to open video
#
LD_PRELOAD=/usr/lib32/libv4l/v4l2convert.so skype 

You don't have to make a script to run this, just type the last line into a terminal window and hit return, much simpler.

Thanks for the reply but as stated previously in this thread I tried that method by pasting that line of code into the terminal. It opened skype as normal but no difference with the webcam.
I shall reinstall guvcview to try it again but when I tried it first time the application wouldn't even start.
When your webcam didn't work what happened, was it detected at all in skype?

I don't think its just skype because cheese doesn't work either, only acouple of media applications worked eg. VLC. When I try cheese it just sits there loading but never gets there and if I click 'preferences' it freezes up and then I need to relogin to get rid of the old process and start a new one.

Must be something wrong with my installation, don't fancy reinstalling just for webcam though...

---

### Post by tobiz on 2011-07-01
After you've reinstalled guvcview try running it from a terminal, this may give you some information as to what's going wrong.  If you run guvcview -v it will give you more output, eg look to see what it says about the video device.

When the webcam didn't work for me in Skype it was detected, this can be seen using {bottom LHS S symbol}>options>video devices.  Mine says USB camera (/dev/video0), but when I selected the test button the area stayed black, the pre-load fixed it. Your problem sounds more serious.

Can't remember if you've done this but run lsusb (assuming your webcam is usb connected) and lsmod and post the results in the forum.  lsusb will tell you if the webcam has been detected and lsmod will tell you which drivers (modules) have been loaded; this info could help diagnose the problem.

---

### Post by no2498 on 2011-07-01
vlc made my cam stop working in cheese and wxcam i had to do the gstreamer-properties 5 or 6 times  and set the plugin to auto find my cam
just to get cheese and wxcam working again

---

### Post by no2498 on 2011-07-01
guvcview  uses totem or mplayer to see the cam

---

### Post by Ken UK on 2011-07-02
I tried guvcview from the terminal and got this output:
```
ken@ken-System:~$ guvcview -v
guvcview 1.4.1
video_device: /dev/video0
vid_sleep: 0
cap_meth: 1
resolution: 640 x 480
windowsize: 480 x 700
vert pane: 0
spin behavior: 0
mode: mjpg
fps: 1/25
Display Fps: 0
bpp: 0
hwaccel: 1
avi_format: 0
sound: 1
sound Device: 0
sound samp rate: 0
sound Channels: 0
Sound delay: 0 nanosec
Sound Format: 80 
Pan Step: 2 degrees
Tilt Step: 2 degrees
Video Filter Flags: 0
image inc: 0
profile(default):/home/ken/default.gpfl
starting portaudio...
ALSA lib pcm_asym.c:106:(_snd_pcm_asym_open) capture slave is not defined
ALSA lib confmisc.c:1286:(snd_func_refer) Unable to find definition 'cards.SB-XFi.pcm.hdmi.0:CARD=0,AES0=4,AES1=130,AES2=0,AES3=2'
ALSA lib conf.c:4184:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:4663:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM hdmi
ALSA lib confmisc.c:1286:(snd_func_refer) Unable to find definition 'cards.SB-XFi.pcm.hdmi.0:CARD=0,AES0=4,AES1=130,AES2=0,AES3=2'
ALSA lib conf.c:4184:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:4663:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM hdmi
ALSA lib confmisc.c:1286:(snd_func_refer) Unable to find definition 'cards.SB-XFi.pcm.modem.0:CARD=0'
ALSA lib conf.c:4184:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:4663:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.phoneline:CARD=0,DEV=0
ALSA lib confmisc.c:1286:(snd_func_refer) Unable to find definition 'cards.SB-XFi.pcm.modem.0:CARD=0'
ALSA lib conf.c:4184:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:4663:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.phoneline:CARD=0,DEV=0
ALSA lib confmisc.c:1286:(snd_func_refer) Unable to find definition 'cards.SB-XFi.pcm.modem.0:CARD=0'
ALSA lib conf.c:4184:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:4663:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM phoneline
ALSA lib confmisc.c:1286:(snd_func_refer) Unable to find definition 'cards.SB-XFi.pcm.modem.0:CARD=0'
ALSA lib conf.c:4184:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:4663:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM phoneline
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
language catalog=> dir:/usr/share/locale type:UTF-8 lang:en_GB cat:guvcview.mo
mjpg: setting format to 1196444237
capture method = 1
video device: /dev/video0 
/dev/video0 - device 1

```

Here is the output for lsusb:
```
Bus 004 Device 006: ID 046d:c222 Logitech, Inc. G15 Keyboard / LCD
Bus 004 Device 005: ID 046d:c051 Logitech, Inc. G3 (MX518) Optical Mouse
Bus 004 Device 004: ID 0781:5530 SanDisk Corp. 
Bus 004 Device 003: ID 046d:c221 Logitech, Inc. G11/G15 Keyboard / Keyboard
Bus 004 Device 002: ID 046d:c223 Logitech, Inc. G11/G15 Keyboard / USB Hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 001 Device 004: ID 0d49:7450 Maxtor Basics Portable USB Device
Bus 001 Device 003: ID 0204:6025 Chipsbank Microelectronics Co., Ltd CBM2080 Flash drive controller
Bus 001 Device 002: ID 041e:4065 Creative Technology, Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

I presume that: Bus 001 Device 002: ID 041e:4065 Creative Technology, Ltd 
Is the webcam or it could be my sound card...

---

### Post by no2498 on 2011-07-03
if you ever get cheese to open 
this is why it dont show your cam resolution: 640 x 480
set cheese to something like 464x480 
cheese uses odd sizes
click edit preferences to set the size

with guvcview you need to have i think its mplayer installed
or it wont show anything

---

### Post by Ken UK on 2011-07-03
Dam I can't get into preferences to change it. Cheese opens but as soon as I click on preferences it locks up. Is there any other way to change it? Maybe through the terminal?

I installed mplayer and it doesn't seem to have made a difference but I will keep trying...

---

### Post by no2498 on 2011-07-04
try guvcview  now that you have mplayer
ah wait mplayer uses gstreamer also
you need to get gstreamer working

1 of the links i gave was for gstreamer config or something like it

---

### Post by tobiz on 2011-07-04
Ken, if you take a look at [http://www.ideasonboard.org/uvc/]("http://www.ideasonboard.org/uvc/") you'll see that ID 041e:4065 is listed as a supported webcam (some good news).  What was the result of lsmod?  BTW if I run guvcview -v I get stuff after the last "video device: /dev/video0", eg
video device: /dev/video0 
/dev/video0 - device 1
Init. USB camera (location: usb-0000:00:1d.0-2)
{ pixelformat = 'JPEG', description = 'JPEG' }
{ discrete: width = 160, height = 120 }
	Time interval between frame: 
{ discrete: width = 320, height = 240 }
	Time interval between frame: 
{ discrete: width = 640, height = 480 }
...........
...........

This looks like it's picking up my webcam.  If you're not getting this then it might hint at the problem

---

### Post by Ken UK on 2011-07-12
```
ken@ken-System:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12617  4 
nls_cp437              12751  4 
vfat                   17335  4 
fat                    55505  1 vfat
cryptd                 19801  0 
aes_i586               16956  2978 
aes_generic            38023  1 aes_i586
dm_crypt               22463  0 
binfmt_misc            13213  1 
snd_wavefront          34696  0 
cx88_blackbird         22936  1 
cx2341x                27688  1 cx88_blackbird
cx22702                13240  1 
cx88_dvb               33267  0 
cx88_vp3054_i2c        12799  1 cx88_dvb
videobuf_dvb           13867  1 cx88_dvb
dvb_core               90587  2 cx88_dvb,videobuf_dvb
wm8775                 12902  1 
snd_usb_audio          91410  1 
snd_cs4236             29291  0 
tuner_simple           18134  2 
tuner_types            18907  1 tuner_simple
snd_wss_lib            30006  2 snd_wavefront,snd_cs4236
snd_usbmidi_lib        24388  1 snd_usb_audio
snd_hda_codec_realtek   255820  1 
snd_opl3_lib           18760  2 snd_wavefront,snd_cs4236
snd_mpu401             13800  0 
tda9887                17887  1 
cx88_alsa              13797  1 
snd_mpu401_uart        13865  3 snd_wavefront,snd_cs4236,snd_mpu401
snd_ctxfi              85192  2 
tda8290                22227  0 
tuner                  26802  2 
snd_seq_midi           13132  0 
snd_hda_intel          24140  2 
snd_rawmidi            25269  4 snd_wavefront,snd_usbmidi_lib,snd_mpu401_uart,snd_seq_midi
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
snd_seq_midi_event     14475  1 snd_seq_midi
snd_hwdep              13274  4 snd_wavefront,snd_usb_audio,snd_opl3_lib,snd_hda_codec
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_pcm                80244  7 snd_cs4236,snd_usb_audio,snd_wss_lib,cx88_alsa,snd_hda_intel,snd_hda_codec,snd_ctxfi
cx8800                 33381  2 cx88_blackbird
ppdev                  12849  0 
cx8802                 18577  2 cx88_blackbird,cx88_dvb
ir_lirc_codec          12770  0 
lirc_dev               18720  1 ir_lirc_codec
snd_timer              28659  4 snd_wss_lib,snd_opl3_lib,snd_seq,snd_pcm
ir_sony_decoder        12493  0 
uvcvideo               66851  0 
cx88xx                 78563  5 cx88_blackbird,cx88_dvb,cx88_alsa,cx8800,cx8802
ir_jvc_decoder         12490  0 
snd_seq_device         14110  4 snd_opl3_lib,snd_seq_midi,snd_rawmidi,snd_seq
ir_rc6_decoder         12490  0 
ir_rc5_decoder         12490  0 
ir_nec_decoder         12490  0 
rc_core                25760  7 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx88xx
tveeprom               17009  1 cx88xx
v4l2_common            16757  6 cx88_blackbird,cx2341x,wm8775,tuner,cx8800,cx88xx
videodev               75143  10 cx88_blackbird,cx2341x,wm8775,tuner,cx8800,uvcvideo,cx88xx,v4l2_common
snd                    55295  31 snd_wavefront,snd_cs4236,snd_usb_audio,snd_wss_lib,snd_usbmidi_lib,snd_hda_codec_realtek,snd_opl3_lib,cx88_alsa,snd_mpu401,snd_mpu401_uart,snd_hda_intel,snd_rawmidi,snd_hda_codec,snd_ctxfi,snd_hwdep,snd_seq,snd_pcm,snd_timer,snd_seq_device
videobuf_dma_sg        18747  6 cx88_blackbird,cx88_dvb,cx88_alsa,cx8802,cx8800,cx88xx
videobuf_core          25193  6 cx88_blackbird,videobuf_dvb,cx8800,cx8802,cx88xx,videobuf_dma_sg
btcx_risc              13400  4 cx88_alsa,cx8800,cx8802,cx88xx
psmouse                73312  0 
ns558                  12618  0 
gameport               15027  2 ns558
shpchp                 32345  0 
i2c_ali15x3            12878  0 
k8temp                 12872  0 
i2c_ali1535            12777  0 
snd_page_alloc         14073  4 snd_wss_lib,snd_hda_intel,snd_ctxfi,snd_pcm
lm63                   13998  0 
soundcore              12600  1 snd
serio_raw              12990  0 
parport_pc             32111  1 
asus_atk0110           17664  0 
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
firewire_ohci          31504  0 
firewire_core          56138  1 firewire_ohci
usbhid                 41704  0 
hid                    77084  1 usbhid
usb_storage            43946  4 
uas                    17676  0 
radeon                896428  4 
skge                   44850  0 
crc_itu_t              12627  1 firewire_core
sata_sil24             17801  0 
ahci                   21591  2 
pata_ali               13564  0 
libahci                25548  1 ahci
sky2                   49172  0 
floppy                 60032  0 
ttm                    65184  1 radeon
drm_kms_helper         40745  1 radeon
ati_agp                13202  0 
drm                   180037  6 radeon,ttm,drm_kms_helper
i2c_algo_bit           13184  3 cx88_vp3054_i2c,cx88xx,radeon

```

Can't see any sign of anything to do with my webcam but I'm ot an expert on these things.

For me it just ends with ```
mjpg: setting format to 1196444237
capture method = 1
video device: /dev/video0 
/dev/video0 - device 1

```

Then its as if the program is running but theres nothing there, only a process I can't kill in the background.

As far I can see and understand VL2 is picking up and using my webcam (which is selectable in VLC) but apart from that I dont understand how any of it works or what I need to do.

---

### Post by no2498 on 2011-07-13
put this in a terminal dmesg click enter
did it find your cam

---

### Post by Ken UK on 2011-07-20
Not had much time on the computer lately..

I tried it and it output over 1300 lines lol
But I copied and pasted it into text editor and did a search for "cam" which found these 2 lines:
```
[   18.300570] uvcvideo: Found UVC 1.00 device VF0380 Live! Cam Optia Pro (041e:4065)
[   18.308856] input: VF0380 Live! Cam Optia Pro as /devices
```

So that must mean its detected then?

---

### Post by tobiz on 2011-07-20
> **Ken UK said:**
> Not had much time on the computer lately..

I tried it and it output over 1300 lines lol
But I copied and pasted it into text editor and did a search for "cam" which found these 2 lines:
```
[   18.300570] uvcvideo: Found UVC 1.00 device VF0380 Live! Cam Optia Pro (041e:4065)
[   18.308856] input: VF0380 Live! Cam Optia Pro as /devices
```

So that must mean its detected then?

If you look here [http://www.ideasonboard.org/uvc/]("http://www.ideasonboard.org/uvc/"), you'll see that device 041e:4065 is supported by the UVC driver, ie module. If you look back at the output from your lsmod you'll see that uvcvideo has "0" against it, ie unused, that looks like the problem. I had a similar problem with the cxd2820r driver (module) which had to be built from source. When this was done on 2.6.32-32 the driver wasn't loaded; when I upgraded to 2.6.32-33 and repeated the build, install, reboot it all worked. No one has been able to explain why. You may be having a similar problem, ie upgrade to the next kernel version and see if the problem still exists. If there's a kernel upgrade available from the ubuntu repository then this a relatively safe option.

---

### Post by no2498 on 2011-07-21
i know the numbers are not the same for your cam
but this is all i can think of


BicyclerBoy 
Skinny Soy Caramel Ubuntu

  
Join Date: Apr 2009
Location: Aotearoha
 Beans: 656 
 Ubuntu 10.04 Lucid Lynx 	Re: Webcam not working (Dell SP2208WFP) 
Try from terminal
rmmod uvcvideo
 modprobe uvcvideo
 dmseg

 Repeat these (<5) until the camera initialises okay..

 You could try this ppa to update some v4l components..

[https://launchpad.net/~libv4l/+archi...ilter=maverick](https://launchpad.net/~libv4l/+archi...ilter=maverick)


sudo rmmod uvcvideo
sudo modprobe uvcvideo

---

### Post by Ken UK on 2011-08-07
I tried updating to the latest Kernal but this is a frsh 11.04 install so I knew that was unlikely to do anything.

From rmmod uvcvideo.

I got:
```
ERROR: Module uvcvideo does not exist in /proc/modules

```

This is just too complicated for my beginner knowledge, I dont understand any of this at all. This is one thing that needs to be simplified in future Ubuntu releases!

---

### Post by tobiz on 2011-08-07
> **Ken UK said:**
> I tried updating to the latest Kernal but this is a frsh 11.04 install so I knew that was unlikely to do anything.

From rmmod uvcvideo.

I got:
```
ERROR: Module uvcvideo does not exist in /proc/modules

```

This is just too complicated for my beginner knowledge, I dont understand any of this at all. This is one thing that needs to be simplified in future Ubuntu releases!
I agree with you this is far too complicated, it needs to be simplified. My own experience is I connected my Philips web cam to my 10.04 system and everything worked, absolutely no problems. The real problem is that the suppliers of products such as your webcam don't supply the drivers it needs to work under Linux, normally they provide them only for Windows, the many, many versions of Windows out there.  Just imagine the problems you'd have if you bought a webcam and it didn't include a driver for the version of Windows you may have, which as I understand it can happen if you're using Windows 7! Result, exactly the situation you're in now. None of which, of course solves your problem but does put it into context. In simpe terms what happens when you plug in a USB device is that the ID is detected and provided it is recognised, ie there is appropriate code to support that device then the driver (or module) is loaded for use by the kernel.  If the USB device ID is not recognised or there is no driver associated with it then it just won't work. You can see if the device was recognised as a usb device by running the command 'lsusb' and you should see an entry for the device ID (as mentioned a while back).  If the ID doesn't appear in the lsusb then it wasn't recognised: step 1.  If you get past step 1 then run the command lsmod, this lists all the modules loaded into the kernel.  Since there can be a lot of modules the output can be long. If you run 'lsmod|grep uvc' (if it's a uvc device, you only need a few of the characters in the driver name string, not all) then only the entries with uvc will be output.  If there are none then there's no module loaded for your device and it won't work.  Of course if you get success from steps 1 and 2 then the device has been recognised and a driver (module) loaded for it, hence it should work; if it doesn't work then it gets a lot harder to find out what's wrong. If you really want it to be simple then the best, (but not the least expensive) solution is to do some web research and find a webcam that is known, ie proven to work with your distribution version and get one; I hope you don't have to do this.  One thought, is you webcam plugged in directly to the computer or via a usb hub?  I've had problems with webcams connected via hubs, just a thought.

---

### Post by no2498 on 2011-08-08
this is why cheese is not working
this is the cheese help file



Frequently Asked Questions

    * Cheese Manual

    * 6.1.&#8194;The video is sluggish/has a slow response. What can I do?
    * 6.2.&#8194;I have a Mac with iSight and a ATI graphics card, and the colors are weird.
    * 6.3.&#8194;My webcam works with gstreamer, but does not work with Cheese. What's wrong?
    * 6.4.&#8194;My webcam works with other programs such as Ekiga, Camorama, but not with Cheese. What's wrong?
    * 6.5.&#8194;Where does Cheese store my photos and videos?
    * 6.6.&#8194;My Quickcam Express doesn't work with Cheese...
    * 6.7.&#8194;"No Camera Found" Error Message
    * 6.8.&#8194;Which cameras are supported?

6.1.&#8195;The video is sluggish/has a slow response. What can I do?


      You may have set "ximagesink" (X Window System (No Xv)) as video-output.
      This means that your CPU is doing all the work. Change it to "xvimagesink"
      (X Window System (X11/XShm/Xv)) in order to let your graphics card do the work.
    


      To change this setting, run the gstreamer-properties
      command, click the Video tab
      and change the appropriate setting.
    
6.2.&#8195;I have a Mac with iSight and a ATI graphics card, and the colors are weird.


      This is a problem with the ATI graphics card, though there is a work around.
      Change the video-output to custom and insert the following: "ffmpegcolorspace !
      video/x-raw-yuv,format=(fourcc)YV12 ! ffmpegcolorspace ! xvimagesink".
    


      To change this setting, run the gstreamer-properties command, 
      click the Video tab
      and select custom from the drop down menu.
    
6.3.&#8195;My webcam works with gstreamer, but does not work with Cheese. What's wrong?


      Using the gstreamer-properties mentioned in the above question, try changing from
      xvimagesink to ximagesink or vice-versa.
      If this still does not work, run cheese --verbose on
      the command line and copy the logging into a bug report in our 
      
      bug tracker.
    
6.4.&#8195;My webcam works with other programs such as Ekiga, Camorama, but not with Cheese. What's wrong?


      See if your webcam works when testing it in
      gstreamer-properties. If it works
      there, but not in Cheese, please file a bug report in our 
      
      bug tracker.
    
6.5.&#8195;Where does Cheese store my photos and videos?


      Cheese stores your pictures in a folder called Webcam inside the
      XDG-Directory set for Pictures (in most distributions its ~/Pictures/Webcam).
      The same applies for Videos: ~/Videos/Webcam. XDG is a standard to
      declare default folders in your system. You can find more information
      about XDG here.
    


      If the XDG-Path is not set on your System, cheese has a fallback solution: it
      will store both your pictures and videos in ~/.gnome2/cheese/media. This is the default
      directory for your media if you have an older version of Cheese.
    


      How to set an alternate path is described in Section 4.2 &#8213; GConf settings.
    

      

Attention: leave this settings blank if you want Cheese to use the default directories.

    

		  


		    You can also save your pictures to an alternate location from within Cheese. Please see
		    Section 5.2 &#8213; Saving photos and videos to an alternate location for information on this.
		  

		
6.6.&#8195;My Quickcam Express doesn't work with Cheese...


      or gstreamer, and I see errors like "Not enough buffers. We got 1, we
      want at least 2" in the Cheese output. With driver "qc-usb".
    


      Try running qcset /dev/video0 compat=dblbuf to enable double buffer
      compatibility mode, then restart Cheese.
    
6.7.&#8195;"No Camera Found" Error Message


      "When I launch Cheese, I get the message 'No Camera Found' but I have my webcam plugged into my computer".
    


      There are many situations that can cause this, and the exact problem that is causing it needs to be isolated.
      If possible, try each of the following to try and get your webcam working:
    

   1.


                
                 Plug your webcam into another computer. If it works there, then it is a problem 
                 with the connection to your computer, or the operating system if it was a different
                 one on the other computer. Check the ports on your computer (try another one) and
                 consult support for your particular operating system.
                
              
   2.

                
                 See if your camera is being detected by your computer. On Linux, open up the terminal or console
                 and type "dmesg" before you plug in your webcam. Notice the most recent entries, and then plug in
                 your webcam. Type "dmesg" again and see if the most recent entries differ. If the message mentions
                 a USB device being detected, and your webcam is the only USB device that has been changed, then
                 your computer is detecting your webcam fine. If not, then test to see if the webcam is working on
                 another computer. This may only work with USB webcams.
                
              
   3.

                
                 As Cheese uses the gstreamer backend, it is most likely because gstreamer is not detecting the webcam (or
                 gstreamer has become corrupt). Please contact support for the particular operating system that
                 you are running with as many details as possible. For Ubuntu, please use the
                 Ubuntu Forums.
                
              

6.8.&#8195;Which cameras are supported?


      Cheese uses gstreamer for video grabbing. So in principle Cheese supports 
      any camera that works with GStreamer. That should be any camera
      which supports video4linux or video4linux2.

---

