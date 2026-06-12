---
title: "kino question ?"
date: 2007-06-16
forum: Multimedia Production
---

### Post by firedancer on 2007-06-16
Hi, i just purchased a firewire pci card (Lacie) 

my specs are 
intel D845gebv2
2.6 ghz 
1G ram 
40 g hd 

someone told me that celeron which i have will not do the job for me 

my pci card is detected
when i start kino this is the output 

Kino Common being built
> Creating page editor
> Creating Capture Page
> Creating Export Page
> Creating Export1394 Page
> Creating ExportAVI Page
> Creating ExportStills Page
> Creating ExportAudio Page
> Creating Preferences
Loading preferences from "/home/fayaman/.kinorc"
Saving preferences.
> Creating ExportMJPEG Page
/usr/share/kino/scripts/dvdauthor/dvdauthor-k3b.sh
/usr/share/kino/scripts/dvdauthor/growisofs.sh
/usr/share/kino/scripts/dvdauthor/none.sh
/usr/share/kino/scripts/dvdauthor/dvdauthor.sh
/usr/share/kino/scripts/dvdauthor/qdvdauthor.sh
> Initializing MJPEG Export Page settings from Preferences
> Creating ExportPipe Page
/usr/share/kino/scripts/exports/ffmpeg_3gp.sh
/usr/share/kino/scripts/exports/ffmpeg_utils.sh
/usr/share/kino/scripts/exports/ffmpeg_vcd.sh
/usr/share/kino/scripts/exports/ffmpeg2theora.sh
/usr/share/kino/scripts/exports/rawplay.sh
/usr/share/kino/scripts/exports/ffmpeg_dvd_dual.sh
/usr/share/kino/scripts/exports/ffmpeg_dvd.sh
/usr/share/kino/scripts/exports/ffmpeg_divx_dual.sh
/usr/share/kino/scripts/exports/ffmpeg_mp3.sh
/usr/share/kino/scripts/exports/ffmpeg_h264.sh
/usr/share/kino/scripts/exports/ffmpeg_flv.sh
/usr/share/kino/scripts/exports/ffmpeg_mp4.sh
/usr/share/kino/scripts/exports/extract_chapters
/usr/share/kino/scripts/exports/ffmpeg_mp4_dual.sh
/usr/share/kino/scripts/exports/ffmpeg_divx.sh
/usr/share/kino/scripts/exports/mencoder_dual.sh
/usr/share/kino/scripts/exports/mencoder.sh
/usr/share/kino/scripts/exports/ffmpeg_h264_dual.sh
> Creating page trim
>> image creator repository created
>>> Image Create: Fixed Colour
>>> Image Create: Random noise
>>> Image Create: Colour Range
>>> Image Create: Gradiant
>>> Image Create: Create From File
>> image filter repository created
>>> Image Filter: No Change
>>> Image Filter: Black & White
>>> Image Filter: Sepia
>>> Image Filter: Reverse Video
>>> Image Filter: Mirror
>>> Image Filter: Kaleidoscope
>>> Image Filter: Swap
>> image transition repository created
>>> Image Transition: No Change
>>> Image Transition: Switch
>>> Image Transition: Fade
>>> Image Transition: Push Wipe
>>> Image Transition: Barn Door Wipe
>>> Image Transition: Differences
>> audio filter repository created
>>> Audio Filter: No Change
>>> Audio Filter: Silence
>>> Audio Filter: Fade In
>>> Audio Filter: Fade Out
>> audio transition repository created
>>> Audio Transition: No Change
>>> Audio Transition: Cross Fade
>>> Audio Transition: Dub
>>> Audio Transition: Mix
> Creating Magick Page
>> Searching /usr/lib/kino-gtk2 for plugins
>>> Registering plugin /usr/lib/kino-gtk2/libdvtitler.so
>>> Registering plugin /usr/lib/kino-gtk2/libtimfx.so
>>> Image Filter: Titler
>>> Image Filter: Superimpose
>>> Image Filter: Blur
>>> Image Filter: Color Hold
>>> Image Filter: Soft Focus
>>> Image Transition: Luma Wipe
> setting video preview size to 320x240
>> Starting Editor
>>> dv1394Writer::dv1394Writer /dev/dv1394/0 channel 63 fd -1
>> Kino Common newFile
>> Creating undo/redo buffer
>>> Received playlist to store at position 0
>>>> Adding to end
>> on_main_window_map_event
>> Leaving Editor
>> Left Editor
>> Starting Capture
>> AV/C Enabled
>>> Using dv1394 capture
>> Kino Common newFile
>> Leaving Capture
>> Constructing File Capture tracker
>> Starting Editor
>>> dv1394Writer::dv1394Writer /dev/dv1394/0 channel 63 fd -1
>>> Received playlist to store at position 0

go into preferences and make some changes which i read about 

but whan i press capture , i notice that it goes on then it quits rite away , at first (before rebooting) teh capture 'button' would  not even turn on (red) 

is it that my system can't handle it , or is it the firewire or can it be something else 

i'm running ubuntu-studio at the moment .....................................what can i do , i have one day left to bring back the pci card (which i think funtions) and wait till i can afford a whole new motherboard and stuff (amd, dual core, whatelse..............................i gonna have to wait long guys:(

sorry for the mess , wasn't able to put output as attachment !

---

### Post by kayosiii on 2007-06-17
Sounds like a permissions problem
please copy and paste the following into a terminal and tell me what you get.

ls -l /dev/dv1394/

---

### Post by firedancer on 2007-06-17
Hi kayosiii, this is it 

fayaman@dragon-desktop:~$ ls -l /dev/dv1394/
ls: /dev/dv1394/: No such file or directory

?

---

### Post by firedancer on 2007-06-17
i noticed that i'm not in the video 'group'
groups

'fayaman adm dialout fax cdrom floppy tape audio dip plugdev scanner fuse'

so that will keep me from working with video , what's the code to add myself to the video group don't know how i did it with audio 


:cry:

---

### Post by firedancer on 2007-06-17
bump

---

### Post by eggdeng on 2007-06-17
With the camera _connected and turned on_ 

```
ls /dev | grep 1394
``` 

You should get an output like

```
dv1394-0
raw1394
```

What you need to know is the exact name of the first of these two. Now, in Kino, go to Edit -> Preferences -> IEEE1394 and see what is listed as the dv1394 Device. If the name does not coincide, change the device name on this tab to coincide with the one you retrieved with the ls command. If you need to check permissions

```
ls -l /dev | grep 1394
```

and you should get the following permissions

```
crw-rw---- 1 root video   171,  32 2007-06-17 23:37 dv1394-0
crw-rw---- 1 root disk    171,   0 2007-06-17 23:37 raw1394
```

You can add users to the video group by going to System -> Administration -> Users and groups. On the Groups tab, select video and click properties, select a user from the list on the left, click add, then OK.

---

### Post by firedancer on 2007-06-17
what i don't get is that i don't have a video group

i've ben searching for it so i added it myself , but when i check 'group' i get the same thing 


 twice you gie the same > ls /dev | grep 1394

but i don't get anything about permissions with this code (and shouldn't)


anyway , ..........................thnx, ..........................................

---

### Post by eggdeng on 2007-06-17
Should read ```
 ls -l /dev | grep 1394
```

---

### Post by firedancer on 2007-06-17
ok

---

### Post by firedancer on 2007-06-17
the two outputs i get are :


ls /dev | grep 1394:
dv1394
raw1394   (this is highlighted with white ?)

ls -l /dev | grep 1394:
drwxr-xr-x 2 root root          60 2007-06-17 18:00 dv1394
crw-rw---- 1 root disk    171,   0 2007-06-17 18:00 raw1394


and it's funny i'm missing the video group , so i added it

but when i repeat the code above it doesn't show 'root video' it still is 'root root'

are do i have to reboot for that , 

i 'upgraded' to ubuntu-studio and i don't know if that has something to do with it (missing 'video')

---

### Post by firedancer on 2007-06-17
this is frustrating man , 

is this a bug 


ls -l /dev/raw  :
'no such file or directory' 


maybe imy camcorder  is the problem :  sony DCR-TRV350 NTSC


ans in my sys.log there soem strange messages

---

### Post by firedancer on 2007-06-17
how else can i test this pci fire wire card , to see if it works , i don't have another  camera,camcorder,external hdd or such devices here at the moment 

if the system detects it , it should probably work rite ?

---

### Post by firedancer on 2007-06-18
thank  god /me 


puuuff after a whole 2 days trying to get kino working , 

this is a joke ......sudo kino did it for me , man 


ye know ubuntu/linux surprises me everytime, it always fixes when i'm ready to give up

and think there is no way out , and BANG 
sorry i'm so happy 

now i don't have the sound , but i'll go about reading again !:D

---

### Post by jespdj on 2007-06-29
When Kino works with sudo, then you are running Kino using the administrator (root) account. When it works with sudo and does not work without sudo, then it is definitely a permissions problem.

---

### Post by firedancer on 2007-06-29
works without sudo now :cool:

---

