---
title: "Firewire camera on Lucid Lynx problem"
date: 2010-06-07
forum: Multimedia Software
---

### Post by themunkee on 2010-06-07
I'm having problems installing a UniBrain Fire-i camera on Lucid Lynx. It's connected with firewire and is known to work with previous versions of Ubuntu and other Linux distributions (CentOS) on other machines. I've also tested it with Win7 on the same machine with no problems.

I started off running through this tutorial and have tried the 10.04 specific command at the end.
[https://help.ubuntu.com/community/Firewire](https://help.ubuntu.com/community/Firewire)

I'm running 2.6.32-22-generic-pae with libdc1394-22 (2.1.2-2), libraw1394-11 (2.0.4-1).

Running Kino gives:

[INDENT][B]WARNING: raw1394 kernel module not loaded or failure to read/write
/dev/raw1394![/B][/INDENT]

running it as root gives:

[INDENT]**No AV/C compliant cam connected or not switched on?**[/INDENT]

lspci brings up the following line. I've only got the one firewire port, so I assume thats it.

[INDENT]**03:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. Device 3403**[/INDENT]

Here are the permissions of relevant items under /dev/

[INDENT][B]ls -la /dev/
drwxr-xr-x   2 root root          60 2010-06-07 10:07 video1394
crw-rw-r--   1 root disk    171,   0 2010-06-07 12:16 raw1394[/B][/INDENT]

I'm a member of the disk and video groups.

Running Coriander produces:

[INDENT][B]libdc1394 error: Failed to initialize libdc1394
Segmentation fault[/B][/INDENT]

Checking dmesg outputs:

[INDENT][B]dmesg | grep 1394
[    1.057395] ohci1394 0000:03:00.0: PCI INT A -> GSI 17 (level, low) ->
IRQ 17
[    1.057400] ohci1394 0000:03:00.0: setting latency timer to 64
[    1.116191] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17] 
MMIO=[fbeff800-fbefffff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    2.395231] ieee1394: config ROM CRC error
[    2.395301] ieee1394: Node added: ID:BUS[0-00:1023] 
GUID[0814436102637e40]
[    2.395363] ieee1394: Host added: ID:BUS[0-01:1023] 
GUID[a4badb8000eee818]
[   16.719096] video1394: Installed video1394 module
[   16.733291] ieee1394: raw1394: /dev/raw1394 device initialized
[   19.013940] [fglrx] Reserved FB block: Unshared offset:3fff4000,
size:c000 
[ 5682.332610] coriander[3915]: segfault at 0 ip b714d2b7 sp bfceef50
error 4 in libdc1394.so.22.1.4[b7140000+2c000]
[ 5696.820545] coriander[3917]: segfault at 0 ip b70a02b7 sp bfc07d90
error 4 in libdc1394.so.22.1.4[b7093000+2c000]
[ 5852.326463] coriander[4016]: segfault at 0 ip b715f2b7 sp bf99a1f0
error 4 in libdc1394.so.22.1.4[b7152000+2c000]
[ 5918.634746] coriander[4086]: segfault at 0 ip b70392b7 sp bf823ac0
error 4 in libdc1394.so.22.1.4[b702c000+2c000]
[ 6776.501479] ieee1394: Node changed: 0-01:1023 -> 0-00:1023
[ 6776.501489] ieee1394: Node paused: ID:BUS[0-00:1023] 
GUID[0814436102637e40]
[ 6779.551745] ieee1394: Node removed: ID:BUS[0-00:1023] 
GUID[0814436102637e40]
[ 6782.231716] ieee1394: The root node is not cycle master capable;
selecting a new root node and resetting...
[ 6782.507732] ieee1394: Node added: ID:BUS[0-00:1023] 
GUID[0814436102637e40]
[ 6782.508074] ieee1394: Node changed: 0-00:1023 -> 0-01:1023
[ 6834.929078] coriander[4709]: segfault at 0 ip b71212b7 sp bfdc44f0
error 4 in libdc1394.so.22.1.4[b7114000+2c000]
[ 6862.291151] coriander[4719]: segfault at 0 ip b716c2b7 sp bff6fb20
error 4 in libdc1394.so.22.1.4[b715f000+2c000][/B][/INDENT]

I'd be grateful for any suggestions!

---

### Post by themunkee on 2010-06-07
I've found a temporary solution. By compiling libdc1394 (2.1.2) and libraw1394 (2.0.5) from source I am able to get coriander working, however kino still fails.

---

### Post by David Stodolsky on 2010-07-02
Also worked thru the tutorial including the 10.4 specific commands and can't get anything from the Fire-i. 
Libraw1394-11 (2.0.4-1ubuntu2) and libdc1394-22 (2.1.2-2-2) installed.

---

### Post by Atrophy on 2011-01-26
Hello,

I am having the exact same issue with kino. I'm working with a Canon XH A1, and running 10.04 64-bit on an Asus M50 series laptop.

---

### Post by HC48 on 2011-02-22
Hello,
I have a Sony handycam HC35E which works fine on someone else's computer with a similar set up to mine (Lucid Lynx). I have tried 3 firewires in case it's the hardware and the appropriate commands seen in the documentation ([https://help.ubuntu.com/community/Firewire](https://help.ubuntu.com/community/Firewire)). I haven't tried the solution of Kino as root but did the Kino site fix ([http://www.kinodv.org/](http://www.kinodv.org/)) without any result. I still get the message 'raw 1394 kernel module not loaded or failure to read/write /dev/raw/1394'in Kino.
I get this in the terminal when I do ' grep 1394 /var/log/kern.log':
Feb 21 10:26:02   kernel: [    1.312912] ohci1394 0000:02:0a.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Feb 21 10:26:02  kernel: [    1.374051] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[21]  MMIO=[ffdff000-ffdff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Feb 21 10:26:02   kernel: [    2.656186] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0010dc0000772c11]
Feb 21 10:38:11   kernel: [    1.312149] ohci1394 0000:02:0a.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Feb 21 10:38:11   kernel: [    1.370053] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[21]  MMIO=[ffdff000-ffdff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Feb 21 10:38:11   kernel: [    2.652185] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0010dc0000772c11]
Feb 21 10:38:11   kernel: [   13.313942] intel_rng: FWH not detected
Feb 21 10:47:05   kernel: [    1.314511] ohci1394 0000:02:0a.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Feb 21 10:47:05  p kernel: [    1.370038] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[21]  MMIO=[ffdff000-ffdff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Feb 21 10:47:05   kernel: [    2.652263] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0010dc0000772c11]
Feb 21 11:02:18   kernel: [    1.312988] ohci1394 0000:02:0a.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Feb 21 11:02:18   kernel: [    1.370051] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[21]  MMIO=[ffdff000-ffdff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Feb 21 11:02:18   kernel: [    2.652185] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0010dc0000772c11]
Feb 21 11:04:45   kernel: [    1.310943] ohci1394 0000:02:0a.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Feb 21 11:04:45 kernel: [    1.370054] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[21]  MMIO=[ffdff000-ffdff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Feb 21 11:04:45   kernel: [    2.652188] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0010dc0000772c11]
Feb 21 11:06:45   kernel: [    1.327071] ohci1394 0000:02:0a.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Feb 21 11:06:45   kernel: [    1.386045] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[21]  MMIO=[ffdff000-ffdff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Feb 21 11:06:45 kernel: [    2.668184] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0010dc0000772c11]
Feb 21 11:13:24   kernel: [  413.337546] ieee1394: raw1394: /dev/raw1394 device initialized
Feb 21 11:17:45   kernel: [    1.312478] ohci1394 0000:02:0a.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Feb 21 11:17:45   kernel: [    1.374050] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[21]  MMIO=[ffdff000-ffdff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Feb 21 11:17:45   kernel: [    2.656184] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0010dc0000772c11]
Feb 21 11:40:53   kernel: [    1.324648] ohci1394 0000:02:0a.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Feb 21 11:40:53  kernel: [    1.382063] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[21]  MMIO=[ffdff000-ffdff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Feb 21 11:40:53  p kernel: [    2.664274] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0010dc0000772c11]
Feb 21 11:50:38   kernel: [  599.525052] ieee1394: raw1394: /dev/raw1394 device initialized
Feb 21 11:55:11   kernel: [    1.299620] ohci1394 0000:02:0a.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Feb 21 11:55:11   kernel: [    1.358040] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[21]  MMIO=[ffdff000-ffdff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Feb 21 11:55:11   kernel: [    2.632195] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0010dc0000772c11]
Feb 22 09:46:02   kernel: [    1.287563] ohci1394 0000:02:0a.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Feb 22 09:46:02   kernel: [    1.346033] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[21]  MMIO=[ffdff000-ffdff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Feb 22 09:46:02  kernel: [    2.620186] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0010dc0000772c11]

-which I shows I've tried several times to solve the same problem I think. I hope I haven't made it worse! If I have, how do I start from scratch? I can undo the Kino fix easily but lack experience with commands other than by copy and paste. 

Finally, could it simply be the port on the computer where I plug in the firewire? How can I tell?

I'd really appreciate any help.
HC

---

### Post by HC48 on 2011-02-22
hello again,
"If Ubuntu doesn't automatically create a device node you can force the creation by typing the following in a Terminal": 
 so later I tried this from the documentation _again_:
 :    ~$ gksudo modprobe raw1394  
 :~$ gksudo modprobe dv1394  
 :~$ echo 'KERNEL=="raw1394", GROUP="video", MODE="0664"' |  
 > sudo tee /etc/udev/rules.d/50-raw1394.rules  
 KERNEL=="raw1394", GROUP="video", MODE="0664"  
 :~$ && sudo restart udev  
 bash: Erreur de syntaxe près du symbole inattendu « && »  
 :~$ sudo restart udev  
 udev start/running, process 2167 

 -rebooted, no change so I tried:
            _"Method 3. 'udev rule_'
 A straight-forward method is to add a raw1394 specific udev rule. Type this in a terminal":  
 
:~$ echo 'KERNEL=="raw1394", GROUP="video", MODE="0664"' > /tmp/raw1394.rules 
 :~$ sudo cp /tmp/raw1394.rules /etc/udev/rules.d/ 
 [sudo] password:  
 :~$ modprobe -r raw1394 && modprobe raw1394 
 [B]FATAL: Error inserting raw1394 (/lib/modules/2.6.32-28-generic/kernel/drivers/ieee1394/raw1394.ko): Operation not permitted
[/B]  

 Any ideas?
 

 Thank you,
 HC

PS I undid the Kino site fix for Lucid Lynx before doing this...

---

### Post by HC48 on 2011-02-23
Hello,
I have redone everything for Lucid Lynx as in the firewire documentation:

echo 'KERNEL=="raw1394", GROUP="video", MODE="0664"' |
sudo tee /etc/udev/rules.d/50-raw1394.rules
&& sudo restart udev

+reboot

(BTW, I get a message when I type the above as it is = 
bash: Erreur de syntaxe près du symbole inattendu « && »  
 so I take out the && and type the 2 commands seperately, I don't know 
if I'm doing the right thing ..)
I uninstalled and redownloaded Kino again, 
checked the packets (dvgrab, kino are there ) but Kino doesn't create the 
nodes so I did the following as advised:
gksudo modprobe raw1394
gksudo modprobe dv1394

and Kino seems to pick up the connection in capture, the capture button 
unfreezes,but it says that no camcorder AV/C is connected.I don't get the
 previous error message at least.When I reboot Kino goes back to the error 
message anyway.

I also saw this on another site (in French)
[http://fr.lprod.org/wiki/doku.php/ressources:1394:droits_auto](http://fr.lprod.org/wiki/doku.php/ressources:1394:droits_auto) :

sudo cp /etc/init.d/rc.local /etc/init.d/rc.local.old
sudo gedit /etc/init.d/rc.local 
#activation automatique des droits sur le firewire chmod 777 /dev/raw1394 

-which allows permissions automatically on the firewire (I think).
This site deals with Kino but doesn't mention Lucid Lynx users, 
it seems to stop at Karmic.
Anyway I'd be really grateful if anyone can help me solve the problem.
It's strange that this camcorder behaved perfectly on another computer
using Lucid Lynx (grrrr!)

HC:(

---

### Post by HC48 on 2011-02-26
hello,
Yes it's me again. I thought I'd found the solution when I saw that I  didn't have libavc 1394-dev in the synaptics. I installed it but still  no luck! Tried the above again, same results as before.
Should I try the Kino fix for Lucid on their site again?

Thank you 
HC

did this:

dmesg | grep 1394
[    1.325741] ohci1394 0000:02:0a.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    1.382063] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[21]  MMIO=[ffdff000-ffdff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    2.664186] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0010dc0000772c11]
[  258.308740] ieee1394: raw1394: /dev/raw1394 device initialized

... so?

---

### Post by HC48 on 2011-02-28
hello, talking to myself... anyway:
I installed almost all the 1EEE 1394 packages in synaptics hoping that I'd simply not understood which were needed... no result.
Redid all the commands as in the documentation, then tried:
/dev/dv1394/0
bash: /dev/dv1394/0: Permission non accordée
 
(working in France : translation = permission not granted)

so what do I do next? Maybe the Kino Lucid Lynx fix for permissions?

---

### Post by HC48 on 2011-02-28
tried this:
sudo kino
[sudo] password: 
> help language code fr
> Kino Common being built
> Creating page editor
> Creating Capture Page
> Creating Export Page
> Creating Export1394 Page
> Creating ExportAVI Page
> Creating ExportStills Page
> Creating ExportAudio Page
> Creating ExportMJPEG Page
/usr/share/kino/scripts/dvdauthor/growisofs.sh
/usr/share/kino/scripts/dvdauthor/dvdauthor-k3b.sh
/usr/share/kino/scripts/dvdauthor/dvdauthor.sh
/usr/share/kino/scripts/dvdauthor/none.sh
/usr/share/kino/scripts/dvdauthor/qdvdauthor.sh
/usr/share/kino/scripts/dvdauthor/dvdauthor-brasero.sh
> Initializing MJPEG Export Page settings from Preferences
> Creating ExportPipe Page
/usr/share/kino/scripts/exports/gstreamer_theora.sh

(gst-plugin-scanner:3236): GLib-CRITICAL **: g_ascii_strdown: assertion `str != NULL' failed

(gst-plugin-scanner:3236): GLib-CRITICAL **: g_strcanon: assertion `string != NULL' failed

[B]ERROR: Caught a segmentation fault while loading plugin file:
/usr/lib/gstreamer-0.10/libgstfrei0r.so[/B]

Please either:
- remove it and restart.
- run with --gst-disable-segtrap and debug.

(gst-plugin-scanner:3237): GLib-CRITICAL **: g_ascii_strdown: assertion `str != NULL' failed

(gst-plugin-scanner:3237): GLib-CRITICAL **: g_strcanon: assertion `string != NULL' failed

[B]ERROR: Caught a segmentation fault while loading plugin file:
/usr/lib/gstreamer-0.10/libgstfrei0r.so[/B]

Please either:
- remove it and restart.
- run with --gst-disable-segtrap and debug.
/usr/share/kino/scripts/exports/mencoder.sh
/usr/share/kino/scripts/exports/ffmpeg2theora.sh
/usr/share/kino/scripts/exports/ffmpeg_huffyuv.sh
/usr/share/kino/scripts/exports/ffmpeg_xvid_dual.sh
/usr/share/kino/scripts/exports/extract_chapters
/usr/share/kino/scripts/exports/ffmpeg_xvid.sh
/usr/share/kino/scripts/exports/ffmpeg_divx_dual.sh
/usr/share/kino/scripts/exports/ffmpeg_mp3.sh
/usr/share/kino/scripts/exports/rawplay.sh
/usr/share/kino/scripts/exports/ffmpeg_mp4.sh
/usr/share/kino/scripts/exports/ffmpeg_divx.sh
/usr/share/kino/scripts/exports/ffmpeg_vcd.sh
/usr/share/kino/scripts/exports/ffmpeg_dvd.sh
/usr/share/kino/scripts/exports/gstreamer_utils.sh
/usr/share/kino/scripts/exports/ffmpeg_mp4_dual.sh
/usr/share/kino/scripts/exports/ffmpeg_dvd_dual.sh
/usr/share/kino/scripts/exports/ffmpeg_mov.sh
/usr/share/kino/scripts/exports/ffmpeg_h264_ps3.sh
/usr/share/kino/scripts/exports/ffmpeg_h264.sh
/usr/share/kino/scripts/exports/ffmpeg_h264_dual.sh
/usr/share/kino/scripts/exports/ffmpeg2dirac.sh
/usr/share/kino/scripts/exports/ffmpeg_3gp.sh
/usr/share/kino/scripts/exports/ffmpeg_flv.sh
/usr/share/kino/scripts/exports/ffmpeg_utils.sh
> Creating page trim
>>> Image Create: Plage de couleurs
>>> Image Create: Couleur uniforme fixe
>>> Image Create: Depuis un fichier
>>> Image Create: Dégradé
>>> Image Create: Bruit aléatoire
>>> Image Filter: Aucune modification
>>> Image Filter: Noir et Blanc
>>> Image Filter: Kaléidoscope
>>> Image Filter: Fondu entrant
>>> Image Filter: Fondu sortant
>>> Image Filter: Pivoter
>>> Image Filter: Miroir
>>> Image Filter: Vidéo inverse
>>> Image Filter: Sépia
>>> Image Transition: Fondu
>>> Image Transition: Volet porte
>>> Image Transition: Différences
>>> Image Transition: Aucune modification
>>> Image Transition: Volet défilant
>>> Image Transition: Commutation
>>> Audio Filter: Aucune modification
>>> Audio Filter: Doublage
>>> Audio Filter: Fondu entrant
>>> Audio Filter: Fondu sortant
>>> Audio Filter: Gain
>>> Audio Filter: Mélange
>>> Audio Filter: Silence
>>> Audio Transition: Fondu enchaîné
>>> Audio Transition: Aucune modification
> Creating Magick Page
>> Searching /usr/lib/kino-gtk2 for plugins
>>> Registering plugin /usr/lib/kino-gtk2/libtimfx.so
>>> Registering plugin /usr/lib/kino-gtk2/libkinoplus.so
>>> Registering plugin /usr/lib/kino-gtk2/libdvtitler.so
>>> Image Filter: Flou
>>> Image Filter: Conserver une couleur
>>> Image Filter: Soft Focus
>>> Image Transition: Volet de luminance (« luma »)
>>> Image Filter: Moyenne de couleur
>>> Image Filter: Fusain
>>> Image Filter: Saccadé
>>> Image Filter: Niveaux
>>> Image Filter: Panoramique et zoom
>>> Image Filter: Pixeliser
>>> Image Transition: Composition
>>> Image Transition: Clé chromatique bleue
>>> Image Transition: Clé chromatique verte
>>> Image Filter: Superposition
>>> Image Filter: Titrage
>> Creating undo/redo buffer
> setting video preview size to 384x288
>> Starting Editor
>> Kino Common newFile
>>> Received playlist to store at position 0
>>>> Adding to end
>> Leaving Editor
>> Left Editor
>> Starting Capture
>> AV/C Activée
>>> Using iec61883 capture
>>> iec61883Reader::StartThread on port 0
>> Constructing File Capture tracker
>> Kino Common newFile
>> Leaving Capture
>> Starting Editor
>>> Received playlist to store at position 0
>>>> Adding to end
Exiting Kino

Still no change... I'm not sure what all this means...

---

