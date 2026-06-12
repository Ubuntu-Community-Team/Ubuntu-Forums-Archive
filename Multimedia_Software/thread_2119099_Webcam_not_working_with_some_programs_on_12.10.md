---
title: "Webcam not working with some programs on 12.10"
date: 2013-02-23
forum: Multimedia Software
---

### Post by balasupv on 2013-02-23
Hi,
I am fairly new user to Ubuntu. I have a fresh install of 64 bit Ubuntu 12.10 with the gnome remix. The laptop is Lenovo thinkpad T430u. The issue is my integrated laptop webcam is not working with Skype and Cheese.  
```
lsusb
```gives
```
Bus 003 Device 002: ID 04f2:b327 Chicony Electronics Co., Ltd 
```for the web cam identifier

With guvcview the camera works. I installed skype from the Skype webpage and used the mixed architecture 12.04 download. I hope some one can provide a solution! Will be glad to give more info if needed!

---

### Post by varunendra on 2013-02-23
*Thread moved to **Multimedia & Video**.*

----------

When you open Cheese, goto Edit > Preferences > Webcam tab
Do you see a device in "Device" field?

For example, mine is "Asus USB2.0 WebCam (/dev/video0)"

---

### Post by balasupv on 2013-02-24
Thanks a lot for taking the time out to read my question.

I checked in the Preferences. There was no specific camera name for the device-- 

Integrated Camera (/dev/video0)

was what I found in the field.

---

### Post by varunendra on 2013-02-24
Since you are able to use the camera on guvcview, let's compare which device it is detecting the camera as.

Open a terminal and run guvcview with following command -
```
guvcview | grep -i video
```
Post back the outputs in the terminal. You may close guvcview normally.

Additionally, to get details of your camera, also post output of -
```
usb-devices | grep -iB2 -A6 b327
```

---

### Post by balasupv on 2013-02-24
Hi, here is the output you asked for-
```
 
guvcview | grep -i video

ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.rear
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.center_lfe
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.side
ALSA lib audio/pcm_bluetooth.c:1614:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1614:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1614:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1614:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
video device: /dev/video0 
driver:uvcvideo
VIDIOC_G_COMP:: Inappropriate ioctl for device
Checking video mode 640x480@32bpp : OK

```next

```

usb-devices | grep -iB2 -A6 b327
T:  Bus=03 Lev=01 Prnt=01 Port=03 Cnt=01 Dev#=  2 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=04f2 ProdID=b327 Rev=29.27
S:  Manufacturer=Chicony Electronics Co.,Ltd.
S:  Product=Integrated Camera
S:  SerialNumber=0x0001
C:  #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=uvcvideo
I:  If#= 1 Alt= 0 #EPs= 0 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo

```

---

### Post by varunendra on 2013-02-25
For now, please try what is suggested in this thread : [http://ubuntuforums.org/showthread.php?t=1937857](http://ubuntuforums.org/showthread.php?t=1937857)

If it makes skype work, we can make cheese work the same way. If not, we can proceed with taking a look at-
```
lsmod
usb-devices | grep -iB2 -A6 b327
dmesg | grep uvcvideo
```
..while cheese is running.

Also, as a test, try the following if you have vlc installed -
```
vlc v4l2:///dev/video0
```
from a terminal.
Can vlc use the camera this way? Are there any error messages?

---

### Post by balasupv on 2013-02-26
I had a go at the suggestions from the thread you linked-
The first issue was that the libv4l in my case is located in the /lib/x86_64-linux-gnu
which may mean that this is 64 bit library and on using the command
```
LD_PRELOAD=/usr/lib/x86_64-linux-gnu/libv4l/v4l1convert.so skype
```i get the error
```
**ERROR: ld.so: object '/usr/lib/x86_64-linux-gnu/libv4l/v4l1convert.so' from LD_PRELOAD cannot be preloaded: ignored.**
```As a result I did what was suggested in 
[http://forum.ubuntu-it.org/viewtopic.php?f=95&t=546530](http://forum.ubuntu-it.org/viewtopic.php?f=95&t=546530)
and installed the 32 bit libv4l packages (since I am guessing skype is a 32 bit application?). On using the commands
```
 LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype
```the earlier error does not appear, but still I cannot get skype video to work. Within skype when I disable and enable video (which I read somewhere may help) I see the following error
```
libv4l2: error dequeuing buf: Invalid argument
```I have also tried v4l2convert.so in the above command and face the same problem and error message as the one above.

With cheese running I did what you asked-
```

lsmod

Module                  Size  Used by
michael_mic            12613  4 
arc4                   12530  2 
snd_hda_codec_hdmi     32049  1 
snd_hda_codec_realtek    78147  1 
joydev                 17458  0 
coretemp               13401  0 
kvm                   414071  0 
ghash_clmulni_intel    13221  0 
aesni_intel            51038  0 
cryptd                 20404  2 ghash_clmulni_intel,aesni_intel
aes_x86_64             17256  1 aesni_intel
thinkpad_acpi          81199  0 
snd_seq_midi           13325  0 
snd_rawmidi            30513  1 snd_seq_midi
btusb                  22475  0 
snd_seq_midi_event     14900  1 snd_seq_midi
snd_seq                61555  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               76750  1 
videobuf2_core         32852  1 uvcvideo
videodev              120310  3 uvcvideo,videobuf2_core
videobuf2_vmalloc      12861  1 uvcvideo
videobuf2_memops       13405  1 videobuf2_vmalloc
lib80211_crypt_tkip    17380  0 
snd_hda_intel          33492  5 
snd_hda_codec         134213  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              17699  1 snd_hda_codec
microcode              22804  0 
snd_pcm                96668  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
wl                   2573608  0 
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
snd_timer              29426  2 snd_seq,snd_pcm
snd_page_alloc         18485  2 snd_hda_intel,snd_pcm
rtsx_pci_ms            13012  0 
mei                    40691  0 
psmouse                95595  0 
memstick               16555  1 rtsx_pci_ms
serio_raw              13216  0 
lpc_ich                17062  0 
i915                  520615  4 
lib80211               14382  2 lib80211_crypt_tkip,wl
drm_kms_helper         49113  1 i915
drm                   288721  5 i915,drm_kms_helper
i2c_algo_bit           13414  1 i915
snd                    78921  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,thinkpad_acpi,snd_rawmidi,snd_seq,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq_device,snd_timer
wmi                    19071  0 
soundcore              15048  1 snd
parport_pc             32689  0 
nvram                  14363  1 thinkpad_acpi
ppdev                  17074  0 
video                  19391  1 i915
tpm_tis                18681  0 
bnep                   18141  2 
rfcomm                 46620  12 
bluetooth             209249  22 btusb,bnep,rfcomm
mac_hid                13206  0 
lp                     17760  0 
parport                46346  3 parport_pc,ppdev,lp
rtsx_pci_sdmmc         17476  0 
sdhci_pci              18617  0 
sdhci                  32646  1 sdhci_pci
r8169                  61651  0 
rtsx_pci               28325  2 rtsx_pci_ms,rtsx_pci_sdmmc


usb-devices | grep -iB2 -A6 b327

T:  Bus=03 Lev=01 Prnt=01 Port=03 Cnt=01 Dev#=  2 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=04f2 ProdID=b327 Rev=29.27
S:  Manufacturer=Chicony Electronics Co.,Ltd.
S:  Product=Integrated Camera
S:  SerialNumber=0x0001
C:  #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=uvcvideo
I:  If#= 1 Alt= 7 #EPs= 1 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo

dmesg | grep uvcvideo
[   15.010887] uvcvideo: Found UVC 1.00 device Integrated Camera (04f2:b327)
[   15.016508] usbcore: registered new interface driver uvcvideo


```Finally, I have vlc and I see

```

vlc v4l2:///dev/video0
VLC media player 2.0.5 Twoflower (revision 2.0.5-0-g1661b7d)
[0x1dbc108] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
"sni-qt/6510" WARN  00:28:23.084 void StatusNotifierItemFactory::connectToSnw() Invalid interface to SNW_SERVICE 

```Thanks once again for your patient replies!

---

### Post by varunendra on 2013-02-26
Hmm.. I'm getting out of (the stolen) ideas then.

I remember a few cases where google-earth package messed up some libqtgui4 related packages which resulted in error on all the apps that used it for their interface - including vlc. Wondering if this one maybe a similar issue, especially given the error message that vlc returned -
> "**sni-qt**/6510" WARN.... **Invalid interface** to SNW_SERVICE
But this may also be just a red herring, I don't know for sure.

I'm on a terribly slow gprs connection which may take more than an hour to download the 29 MB skype package you mentioned. So I guess I'll download it later sometime to experiment with it.

Meanwhile, you may try to completely remove (purge) skype and reinstall libqtgui4 package to see if you can at least make cheese work, or if the vlc test works after this -
```
sudo apt-get install --reinstall libqtgui4
```
.

---

### Post by balasupv on 2013-02-27
Hi I purged Skype. While purging skype I also realised I may have more than one skype version installed since I had to remove skype:i1386 and skype-bin packages separately. After that I uninstalled and reinstalled the libqtgui4 package and ran cheese. I think the problem has worsened. The last time around I thought I saw my web cam light on when cheese was running..now it does not even recognise a camera device and here is the error I see in the terminal-
```
** (cheese:13074): WARNING **: cheese-main.vala:251: Error: No device found


(cheese:13074): cheese-CRITICAL **: cheese_camera_device_get_device_node: assertion `CHEESE_IS_CAMERA_DEVICE (device)' failed

(cheese:13074): GLib-CRITICAL **: g_variant_new_string: assertion `string != NULL' failed

(cheese:13074): GLib-GIO-CRITICAL **: g_settings_schema_key_type_check: assertion `value != NULL' failed

(cheese:13074): GLib-CRITICAL **: g_variant_get_type_string: assertion `value != NULL' failed

(cheese:13074): GLib-GIO-CRITICAL **: g_settings_set_value: key 'camera' in 'org.gnome.Cheese' expects type 's', but a GVariant of type '(null)' was given

** (cheese:13074): CRITICAL **: cheese_preferences_dialog_setup_resolutions_for_device: assertion `device != NULL' failed 
```Also, guvcview is not working as well, I am a little worried now... it says- unable to open device, make sure camera is connected and displays the following in the terminal
```

guvcview 1.5.3
ALSA lib pcm_dmix.c:1018:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.rear
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.center_lfe
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.side
ALSA lib audio/pcm_bluetooth.c:1614:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1614:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1614:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1614:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
ALSA lib pcm_dmix.c:1018:(snd_pcm_dmix_open) unable to open slave
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
video device: /dev/video0 
unable to detect video devices on your system (0)
ERROR opening V4L interface: No such file or directory
Init video returned -1
VIDIOC_REQBUFS - Failed to delete buffers: Invalid argument (errno 22)
cleaned allocations - 100%
Closing portaudio ...OK
Terminated.

```I am wondering if I messed something up in the skype purge, the commands I used were-
```

sudo apt-get --purge remove skype-bin
sudo apt-get --purge remove skype:i386

```any help to even get the web cam recognised again would be great...

Please ignore the above regarding guvcview not working....it worked after a reboot. Also cheese does not give an error message and the camera light is on but again no video on cheese! Finally tried VLC now and I get the same error message
```
[0x795108] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
"sni-qt/15060" WARN  08:22:15.514 void StatusNotifierItemFactory::connectToSnw() Invalid interface to SNW_SERVICE 

```
Finally, vlc is hard to quit now and I have to kill the process to stop vlc after this command...thought that may be useful. Also finally what would be your ideal way to install skype for the future - from the website? using apt-get?

---

### Post by varunendra on 2013-02-27
Thank God at least the situation didn't get worse!

Initially your post looked like some horror show has begun. I quoted your post to ask a question and noticed your edit - huge relief I must say (at least we are more or less where we were).

Anyway..
> **balasupv said:**
> Also finally what would be your ideal way to install skype for the future - from the website? using apt-get?
I have never used skype, so can't answer this question. However, I have the same (I hope) package downloaded that you pointed to, and going to test it on a live session on a VM (my lappy doesn't have enough space to do a full installation). Will post back if I experienced something odd.

One question for now - ***[COLOR="Navy"]did you have cheese working before installing skype?[/COLOR]***

Also, I have opened the downloaded package on archive manager and it does not seem to have brought any custom lib packages with it. Only its own binary, documentation, some configuration files and images etc. As such, it is not likely that it could mess up the qt packages as I suspected.

Although the 'control' file in the package shows following info -
> Architecture: i386

Depends: **libasound2 (>= 1.0.23), libc6 (>= 2.3.6-6~), libc6 (>= 2.7), libgcc1 (>= 1:4.1.1), libqt4-dbus (>= 4:4.5.3), libqt4-network (>= 4:4.8.0), libqt4-xml (>= 4:4.5.3), libqtcore4 (>= 4:4.7.0~beta1), libqtgui4 (>= 4:4.8.0), libqtwebkit4 (>= 2.2~2011week36), libstdc++6 (>= 4.6), libx11-6, libxext6, libxss1, libxv1, libssl1.0.0**

Recommends: sni-qt, libasound2-plugins

Conflicts: skype-mid, skype-common, skype-bin
Replaces: skype-mid, skype-common, skype-bin

Installed-Size: 35903
The highlighted ones are the packages that may have been changed during its installation. So you may try reinstalling them if cheese was working before installing skype. Otherwise just don't bother.

Clearly, I don't have many clues at the moment, so can't suggest anything substantial.

I'll test the installation in the VM in a few hours or maybe tomorrow and shall post back my experience.

---

### Post by balasupv on 2013-02-27
Yes, I am glad that it did not get worse! Although I am discovering some issue or the other every day :-) But I guess that is how one learns. In any case I did not have cheese working before. Also my Ubuntu is 64 bit. Earlier before a fresh install of Ubuntu I tried Fedora on this machine, cheese worked on it but skype did not! I will check out other suggestions in your last post and do let me know if you find anything.
Thanks!

---

