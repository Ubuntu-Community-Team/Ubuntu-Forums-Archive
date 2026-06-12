---
title: "Capture video with Kino"
date: 2010-07-10
forum: Multimedia Software
---

### Post by jcVan on 2010-07-10
I'm trying to capture video from my Sony DCR-HC21 video camera. I've managed to install Kino fine but was getting the error 

aw 1394 kernel module not loaded or failure to read/write /dev/raw/1394
I could get it working by opening as root but then the files belong to root which I didn't want. So I did the following (as suggested in another thread: 

chmod 777 /dev/raw1394

And now I get the error "No AV/C compliant cam connected or not switched on"

I've tried so many things ie [https://help.ubuntu.com/community/Firewire](https://help.ubuntu.com/community/Firewire)

and as I'm a novice I'm reluctant to keep trying random things when I don't really know what its doing.

Is anyone able to help?


OK, it's back to the first error, is there anyway to run Kino and capture video without changing to root?

---

### Post by ubunterooster on 2010-07-10
try ```
sudo apt-get install cheese
```and use cheese instead of kino.

---

### Post by gandaran on 2010-07-11
look at this [fix]("http://www.kinodv.org/") for lucid

---

### Post by jcVan on 2010-07-11
> **gandaran said:**
> look at this [fix]("http://www.kinodv.org/") for lucid

thanks for the suggestions but I tried that and get :
gksu: symbol lookup error: /usr/lib/libcairo.so.2: undefined symbol: FT_Library_SetLcdFilter

which I have no idea what that means!

---

### Post by no2498 on 2010-07-11
1394 is for fire wire

---

### Post by gandaran on 2010-07-12
hi,
did you fix it?
I did that kino fix and now video capture works without root, it's just marvelous!
maybe running that chmod command broke something, I have had some bad experiences running chmod commands before, now I just refuse to run those commands anymore, theres always another solution.  
> gksu: symbol lookup error: /usr/lib/libcairo.so.2: undefined symbol: FT_Library_SetLcdFilter

I don't know what the error means, could be a gksu error! then try sudo instead.
and use the copy/paste method, maybe it was a typing error.
hope this helps.

---

### Post by HC48 on 2011-02-22
Hello,
I have a Sony handycam HC35E which works fine on someone else's computer with a similar set up to mine (Lucid Lynx). I have tried 3 firewires in case it's the hardware and most of the commands seen in the documentation. I haven't tried the solution of Kino as root but did the Kino site fix advised above without any result. I still get the message 'raw 1394 kernel module not loaded or failure to read/write /dev/raw/1394'.

I get this in the terminal when I do ' grep 1394 /var/log/kern.log':
Feb 21 10:26:02   kernel: [    1.312912] ohci1394 0000:02:0a.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Feb 21 10:26:02  kernel: [    1.374051] ohci1394: fw-host0: OHCI-1394  1.0 (PCI): IRQ=[21]  MMIO=[ffdff000-ffdff7ff]  Max Packet=[2048]  IR/IT  contexts=[4/8]
Feb 21 10:26:02   kernel: [    2.656186] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0010dc0000772c11]
Feb 21 10:38:11   kernel: [    1.312149] ohci1394 0000:02:0a.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Feb 21 10:38:11   kernel: [    1.370053] ohci1394: fw-host0: OHCI-1394  1.0 (PCI): IRQ=[21]  MMIO=[ffdff000-ffdff7ff]  Max Packet=[2048]  IR/IT  contexts=[4/8]
Feb 21 10:38:11   kernel: [    2.652185] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0010dc0000772c11]
Feb 21 10:38:11   kernel: [   13.313942] intel_rng: FWH not detected
Feb 21 10:47:05   kernel: [    1.314511] ohci1394 0000:02:0a.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Feb 21 10:47:05  p kernel: [    1.370038] ohci1394: fw-host0: OHCI-1394  1.0 (PCI): IRQ=[21]  MMIO=[ffdff000-ffdff7ff]  Max Packet=[2048]  IR/IT  contexts=[4/8]
Feb 21 10:47:05   kernel: [    2.652263] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0010dc0000772c11]
Feb 21 11:02:18   kernel: [    1.312988] ohci1394 0000:02:0a.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Feb 21 11:02:18   kernel: [    1.370051] ohci1394: fw-host0: OHCI-1394  1.0 (PCI): IRQ=[21]  MMIO=[ffdff000-ffdff7ff]  Max Packet=[2048]  IR/IT  contexts=[4/8]
Feb 21 11:02:18   kernel: [    2.652185] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0010dc0000772c11]
Feb 21 11:04:45   kernel: [    1.310943] ohci1394 0000:02:0a.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Feb 21 11:04:45 kernel: [    1.370054] ohci1394: fw-host0: OHCI-1394 1.0  (PCI): IRQ=[21]  MMIO=[ffdff000-ffdff7ff]  Max Packet=[2048]  IR/IT  contexts=[4/8]
Feb 21 11:04:45   kernel: [    2.652188] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0010dc0000772c11]
Feb 21 11:06:45   kernel: [    1.327071] ohci1394 0000:02:0a.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Feb 21 11:06:45   kernel: [    1.386045] ohci1394: fw-host0: OHCI-1394  1.0 (PCI): IRQ=[21]  MMIO=[ffdff000-ffdff7ff]  Max Packet=[2048]  IR/IT  contexts=[4/8]
Feb 21 11:06:45 kernel: [    2.668184] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0010dc0000772c11]
Feb 21 11:13:24   kernel: [  413.337546] ieee1394: raw1394: /dev/raw1394 device initialized
Feb 21 11:17:45   kernel: [    1.312478] ohci1394 0000:02:0a.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Feb 21 11:17:45   kernel: [    1.374050] ohci1394: fw-host0: OHCI-1394  1.0 (PCI): IRQ=[21]  MMIO=[ffdff000-ffdff7ff]  Max Packet=[2048]  IR/IT  contexts=[4/8]
Feb 21 11:17:45   kernel: [    2.656184] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0010dc0000772c11]
Feb 21 11:40:53   kernel: [    1.324648] ohci1394 0000:02:0a.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Feb 21 11:40:53  kernel: [    1.382063] ohci1394: fw-host0: OHCI-1394  1.0 (PCI): IRQ=[21]  MMIO=[ffdff000-ffdff7ff]  Max Packet=[2048]  IR/IT  contexts=[4/8]
Feb 21 11:40:53  p kernel: [    2.664274] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0010dc0000772c11]
Feb 21 11:50:38   kernel: [  599.525052] ieee1394: raw1394: /dev/raw1394 device initialized
Feb 21 11:55:11   kernel: [    1.299620] ohci1394 0000:02:0a.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Feb 21 11:55:11   kernel: [    1.358040] ohci1394: fw-host0: OHCI-1394  1.0 (PCI): IRQ=[21]  MMIO=[ffdff000-ffdff7ff]  Max Packet=[2048]  IR/IT  contexts=[4/8]
Feb 21 11:55:11   kernel: [    2.632195] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0010dc0000772c11]
Feb 22 09:46:02   kernel: [    1.287563] ohci1394 0000:02:0a.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Feb 22 09:46:02   kernel: [    1.346033] ohci1394: fw-host0: OHCI-1394  1.0 (PCI): IRQ=[21]  MMIO=[ffdff000-ffdff7ff]  Max Packet=[2048]  IR/IT  contexts=[4/8]
Feb 22 09:46:02  kernel: [    2.620186] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0010dc0000772c11]



-which shows I've tried several times to solve the same problem I think. I hope I haven't made it worse! If I have, how do I start from scratch? I can undo the Kino fix easily but lack experience with commands other than copy and paste.

Finally, could it simply be the port on the computer where I plug in the firewire?

I'd really appreciate any help.
HC

PS If it is the port how can I tell?

---

### Post by HC48 on 2011-02-22
hello again,
"If Ubuntu doesn't automatically create a device node you can force the creation by typing the following in a Terminal": 
 so later I tried this from the documentation _again_:
                     :~$ gksudo modprobe raw1394  
 :~$ gksudo modprobe dv1394  
 :~$ echo 'KERNEL=="raw1394", GROUP="video", MODE="0664"' |  
 > sudo tee /etc/udev/rules.d/50-raw1394.rules  
 KERNEL=="raw1394", GROUP="video", MODE="0664"  
 :~$ && sudo restart udev  
 bash: Erreur de syntaxe près du symbole inattendu « && »  
 :~$ sudo restart udev  
 udev start/running, process 2167 

-rebooted, no change so I tried:
                        "_Method 3. 'udev rule_'
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

PS I undid the Kino site fix for Lucid Lynx before doing this.

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

HC :(

---

### Post by HC48 on 2011-02-26
hello,
Yes it's me again. I thought I'd found the solution when I saw that I didn't have libavc 1394-dev in the synaptics. I installed it but still no luck! Tried the above again, same results as before.
Should I try the Kino fix suggested by gandaran again?

Thank you 
HC

did this:

dmesg | grep 1394
[    1.325741] ohci1394 0000:02:0a.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    1.382063] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[21]   MMIO=[ffdff000-ffdff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
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
Tried this:
sudo kino
[sudo] password : 
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

**ERROR: Caught a segmentation fault while loading plugin file**:
/usr/lib/gstreamer-0.10/libgstfrei0r.so

[B]Please either:
- remove it and restart.
- run with --gst-disable-segtrap and debug.[/B]

(gst-plugin-scanner:3237): GLib-CRITICAL **: g_ascii_strdown: assertion `str != NULL' failed

(gst-plugin-scanner:3237): GLib-CRITICAL **: g_strcanon: assertion `string != NULL' failed

**ERROR: Caught a segmentation fault while loading plugin file:**
/usr/lib/gstreamer-0.10/libgstfrei0r.so

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

Not sure what it all means, maybe I should go to absolute beginners???

Anyway still no change.

---

