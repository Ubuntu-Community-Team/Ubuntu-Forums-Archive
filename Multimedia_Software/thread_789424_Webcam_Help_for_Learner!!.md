---
title: "Webcam Help for Learner!!"
date: 2008-05-10
forum: Multimedia Software
---

### Post by Lizardpath on 2008-05-10
Hello, my name is Adam, I'm 16 an still very new to linux.
I bought an Asus Pundit earlier this year with Gutsy preinstalled, and its great.
I'm still using 7.10 and last night tried to install a webcamera, (I have Gnome Ubuntu but prefer to use Kopete for my IM client, hope this isn't sacrilege to anyone!)  here's the trouble: its not recognised.
I have a Trust HiRes WB-3320X, cheap, but that's the point :)
I know I need drivers and was just wondering if anyone new if this cam was supported, or if I do have to exchange this one which if anyone knows which one I can get for £15 that will definitely work!
Thanks very much in advance for any help,
Here's hoping...
AJ.

---

### Post by linuxwizard on 2008-05-10
Post the results of the command > lsusb

---

### Post by Lizardpath on 2008-05-10
Bus 002 Device 006: ID 093a:2621 Pixart Imaging, Inc. 
Bus 002 Device 004: ID 13dd:0001  
Bus 002 Device 002: ID 046d:c512 Logitech, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 0424:2228 Standard Microsystems Corp. 
Bus 001 Device 001: ID 0000:0000  
adam@adam-desktop:~$ 


Thanks for your response. AJ

---

### Post by linuxwizard on 2008-05-10
Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Video > Video Devices > try changing some of the settings.( Video Plugin if it shows V4L change to V4L2)

To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

---

### Post by Lizardpath on 2008-05-11
Thank you.
Have tried ekiga setup and settings and the message "no device found" appears everywhere!
I've searched compatibility sites but find it difficult as the code uused to name the camera isnt always the actual *model number*.
Hmm, I'm not sure.
Thanks again.

---

### Post by linuxwizard on 2008-05-11
I like testing a webcam with Ekiga first to see if it will work. Alot of webcams will just work out of the box. Doing more searching on your webcam > Bus 002 Device 006: ID 093a:2621 Pixart Imaging, Inc.  > can not find a listing of your webcam or a driver for it.

---

### Post by Lizardpath on 2008-05-12
Well thank you very much for your time, its much appreciated.
I shall just have to buy another cheap one and have a go, give this one to charity or keep it until I learn to write my own drivers!  The day may come...
Thanks again for now - AJ :)

---

### Post by ubontik on 2010-07-17
Hello everybody,

I try to use webcam on Skype. I checked under Options/Video Devices. I got CIF single chip (/dev/video0). When I tested I saw for a split of second splash of light in the camera and that's it.
lsusb gives this list of devices
-------------------
$ lsusb
Bus 004 Device 002: ID 046d:c00e Logitech, Inc. M-BJ58/M-BJ69 Optical Wheel Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 093a:2468 Pixart Imaging, Inc. Cammaestro 2.5DU/X-EYE/Orite SC-120/ICGear TravelCam/Easy Snap Snake Eye Webcam
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
and
-----------------------
$ lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
ipt_MASQUERADE          1407  0 
xt_DSCP                 1677  0 
ipt_REJECT              1928  1 
ipt_LOG                 4542  8 
xt_limit                1382  8 
xt_tcpudp               2011  7 
ipt_addrtype            1631  0 
xt_state                1098  6 
ip6table_filter         2343  1 
ip6_tables             11227  1 ip6table_filter
snd_intel8x0           25588  2 
nf_nat_irc              1124  0 
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
nf_conntrack_irc        3332  1 nf_nat_irc
snd_mixer_oss          13746  1 snd_pcm_oss
nf_nat_ftp              1836  0 
snd_pcm                70662  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
iptable_nat             4414  0 
nf_nat                 15735  4 ipt_MASQUERADE,nf_nat_irc,nf_nat_ftp,iptable_nat
nf_conntrack_ipv4      10672  9 iptable_nat,nf_nat
iptable_mangle          2771  0 
snd_seq_dummy           1338  0 
nf_defrag_ipv4          1073  1 nf_conntrack_ipv4
snd_seq_oss            26726  0 
nf_conntrack_ftp        5381  1 nf_nat_ftp
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
nf_conntrack           61583  9 ipt_MASQUERADE,xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,iptable_nat,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
fbcon                  35102  71 
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
tileblit                2031  1 fbcon
iptable_filter          2271  1 
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ip_tables               9991  3 iptable_nat,iptable_mangle,iptable_filter
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
snd_timer              19098  2 snd_pcm,snd_seq
x_tables               14299  11 ipt_MASQUERADE,xt_DSCP,ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,ipt_addrtype,xt_state,ip6_tables,iptable_nat,ip_tables
gspca_pac207            5400  0 
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
gspca_main             21199  1 gspca_pac207
softcursor              1189  1 bitblit
usbhid                 36110  0 
nvidia               4701243  32 
ppdev                   5259  0 
videodev               34361  1 gspca_main
lp                      7028  0 
snd                    54148  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
vga16fb                11385  1 
parport_pc             25962  1 
v4l1_compat            13251  1 videodev
vgastate                8961  1 vga16fb
hid                    67032  1 usbhid
intel_agp              24119  1 
shpchp                 28820  0 
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
parport                32635  3 ppdev,lp,parport_pc
agpgart                31724  2 nvidia,intel_agp
ohci1394               26950  0 
8139too                18545  0 
8139cp                 16186  0 
ieee1394               81181  1 ohci1394
mii                     4381  2 8139too,8139cp
floppy                 53016  0 
-----------------------
Thank you in advance:)

P.S.
I have Ubuntu 10.04

---

### Post by k-laminero on 2010-07-18
All,

I am trying to get my webcam to work in cheese. 
It used to work every now and then but now i cannot get cheese to pick it up.

Here is the troubleshooting i have done so far, following this thread:

-lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 046d:08c3 Logitech, Inc. Camera (Notebooks Pro)
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 0763:200f Midiman M-Audio MobilePre
Bus 001 Device 004: ID 05e3:0605 Genesys Logic, Inc. USB 2.0 Hub [ednet]
Bus 001 Device 003: ID 0ace:1215 ZyDAS WLA-54L 802.11bg
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

-When i open ekiga softphone, it seems to detect the webcam for sound purposes but not for video. If i open the call panel and click on "Display images from your camera device, an ekiga logo starts bouncing up and down inside a grey square with a "Standby" message.
Cheese just gives me a "Device not found" message


I have Lucid Lynx

Thank you for the help.

---

### Post by no2498 on 2010-07-18
lol the one that started this was 16 is now 18 
i dont think there setting at the computer now

have you tried the cam in gstreamer-properties


open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

cheese has a nice help file look in the faq's
this may help for cheese

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so cheese 


hope this helps

---

### Post by ubontik on 2010-07-20
I ran gstreamer-properties. When I clicked test I got the following message:
***************
The program 'gstreamer-properties' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 55 error_code 11 request_code 133 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
******************
The same error I got while running cheese.
For 
#xawtv I got this:
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.32-23-generic)
xinerama 0: 1280x1024+0+0
WARNING: No DGA direct video mode for this display.
/dev/video0 [v4l2]: no overlay support
v4l-conf had some trouble, trying to continue anyway
Warning: Cannot convert string "-*-ledfixed-medium-r-*--39-*-*-*-c-*-*-*" to type FontStruct
ioctl: VIDIOC_G_STD(std=0x1 [PAL_B]): Invalid argument
ioctl: VIDIOC_S_STD(std=0x0 []): Invalid argument
scroll by 99    length 150    shown 0.000000    top 0.180392 => 0.312392
scroll by 32    length 150    shown 0.000000    top 0.309804 => 0.352471
***********
Thanks

---

### Post by no2498 on 2010-07-21
sounds like you need a driver for your cam

and im sorry i dont have the list of what cams need what driver

---

### Post by ubontik on 2010-07-22
> **no2498 said:**
> sounds like you need a driver for your cam

and im sorry i dont have the list of what cams need what driver
I thought the driver is there
#lsusb
Bus 002 Device 002: ID 093a:2468 Pixart Imaging, Inc. Cammaestro 2.5DU/X-EYE/Orite SC-120/ICGear TravelCam/Easy Snap Snake Eye Webcam

---

### Post by no2498 on 2010-07-22
do you have gstreamer good, bad, ugly,and 10 installed

look in the add remove it should tell you

---

### Post by ubontik on 2010-07-22
> **no2498 said:**
> do you have gstreamer good, bad, ugly,and 10 installed

look in the add remove it should tell you
I've installed them. 
*************
$ gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
************
Where do I get those plugins?

---

### Post by no2498 on 2010-07-23
we all get the same message 

 gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'




you didnt say if the cam come on or not

---

### Post by ubontik on 2010-07-24
> **no2498 said:**
> 
you didn't say if the cam come on or not
It came on with Linux v412. But it didn't come on with Skype test.

---

### Post by no2498 on 2010-07-25
glad it come on  does it work in cheese, xawtv

skype has its own problems 

you may try this

open a terminal put this in it

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

hope it helps

---

### Post by ubontik on 2010-07-27
> **no2498 said:**
> 
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

Skype came on. Then I tried to run a videotest. The light on the camera came on but the test failed with message in terminal:
********
X Error, request 133, minor 18, error code 11 BadAlloc (insufficient resources for operation)
********
Speaking of Skype do you know by chance why incoming ring does not start (even on test) . I see only a message that somebody is calling to me.

Thanks

---

### Post by no2498 on 2010-07-28
you need to make a new ? for skype and your error 

im just not into skype sorry

---

