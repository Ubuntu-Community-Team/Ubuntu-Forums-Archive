---
title: "Sound problems"
date: 2007-08-13
forum: Multimedia &amp; Video
---

### Post by demonicdude on 2007-08-13
Ok, so at first i started a thread in the beginner forum, but not that much luck =). The guy that was helping me told me that i should try here, so lets give it a shot.

I know that my sound is set up perfectly fine and all, i think i just need to do one thing, switch my sound output from an analog one, to a digital one. 



This is was i get when i type aplay -l:
**** List of PLAYBACK Hardware Devices ****
card 0: AudioPCI [Ensoniq AudioPCI], device 0: ES1371/1 [ES1371 DAC2/ADC]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: AudioPCI [Ensoniq AudioPCI], device 1: ES1371/2 [ES1371 DAC1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

This is what i get with lspci:
02:0a.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 09)

Err, also lsmod? i dont know what that does but the guy said to put it >.<:
Module                  Size  Used by
nls_utf8                3072  1 
ntfs                  107764  1 
nls_cp437               6784  1 
isofs                  36284  1 
udf                    85252  0 
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25856  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ppdev                  10116  0 
radeon                124576  2 
drm                    81044  3 radeon
speedstep_lib           6148  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9228  0 
cpufreq_conservative     8200  0 
cpufreq_userspace       5408  0 
cpufreq_stats           7360  0 
freq_table              5792  2 cpufreq_ondemand,cpufreq_stats
tc1100_wmi              8068  0 
dev_acpi               12292  0 
pcc_acpi               13184  0 
sony_acpi               6284  0 
sbs                    15652  0 
button                  8720  0 
i2c_ec                  6016  1 sbs
i2c_core               22656  1 i2c_ec
asus_acpi              17308  0 
battery                10756  0 
video                  16388  0 
container               5248  0 
ac                      6020  0 
backlight               7040  1 asus_acpi
dock                   10268  0 
ipv6                  268960  8 
ndiswrapper           194608  0 
lp                     12452  0 
fuse                   46612  0 
snd_ens1371            27552  2 
gameport               16520  1 snd_ens1371
snd_ac97_codec         98464  1 snd_ens1371
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  1 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_ens1371,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  2 snd_ens1371,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
usbhid                 26592  0 
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
hid                    27392  1 usbhid
snd_timer              23684  2 snd_pcm,snd_seq
psmouse                38920  0 
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
serio_raw               7940  0 
parport_pc             36388  1 
parport                36936  3 ppdev,lp,parport_pc
snd                    54020  12 snd_ens1371,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  2 snd
snd_page_alloc         10888  1 snd_pcm
pcspkr                  4224  0 
intel_agp              25244  1 
agpgart                35400  2 drm,intel_agp
iTCO_wdt               11812  0 
iTCO_vendor_support     4868  1 iTCO_wdt
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
af_packet              23816  4 
tsdev                   8768  0 
evdev                  11008  3 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0 
sr_mod                 17060  1 
cdrom                  37664  1 sr_mod
sd_mod                 23428  4 
floppy                 59524  0 
3c59x                  46632  0 
mii                     6528  1 3c59x
uhci_hcd               25360  0 
usbcore               134280  4 ndiswrapper,usbhid,uhci_hcd
ata_piix               15492  4 
ata_generic             9092  0 
libata                125720  2 ata_piix,ata_generic
scsi_mod              142348  4 sg,sr_mod,sd_mod,libata
generic                 5124  0 [permanent]
thermal                14856  0 
processor              31048  1 thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability


ok so my speakers are Boston Digital BA735, and like i've said, i think the only problem is switching from analog to digital. I looked in alsamixer, and no switch or option for that. I tried unmutting everything, muting somestuff, and that. Also, i used to have this issue with Windows as well (right now i'm dual-booting with windows xp and the speakers work fine on windows). It was an issue of digital speakers not being able to do analog output. I also have these old compaq speakers from like 1995 which are probably analog output, so when i plug those in for my speakers, they work perfectly fine. 

So... anyone can help? (sorry the post is so long! =D) Oh, i would also like to thank Arthur Archnix and Carloslosgrande for helping me out in my other thread o.O

---

### Post by moore.bryan on 2007-08-13
*did you try compiling the newest alsa stuff from source?*

---

### Post by demonicdude on 2007-08-13
i believe i have not compiled them, but i have been downloading different packages through snyaptic. I dont know which one will give me that option though, any ideas?

Edit: I believe i'm installing the newest alsa driver right now ... o.o..

ermmm could u tell me if i'm doing it right lol? i downloaded the driver, unarchived it, went to terminal, went to the directory and typed make. So now i'm guessing its making something (idk what lol..) then after that i would type make intsall..?

---

### Post by fredj on 2007-08-13
You sound card seems to be supported in the installed version of Alsa so I don't see any reason
for you to upgrade.
Open the Alsa mixer. Go to the File->Change Device menu and see if there is any option
there to switch to digital output rather than analog. If not go to the Edit->Preferences menu
and add all the possible volume controls and switches for both record and playback. This
may give you a switch that allows you to switch to digital output.

---

### Post by demonicdude on 2007-08-13
> **fredj said:**
> You sound card seems to be supported in the installed version of Alsa so I don't see any reason
for you to upgrade.
Open the Alsa mixer. Go to the File->Change Device menu and see if there is any option
there to switch to digital output rather than analog. If not go to the Edit->Preferences menu
and add all the possible volume controls and switches for both record and playback. This
may give you a switch that allows you to switch to digital output.


Did that already, could not find an option. Its funny, with windows, i had the same problem and i couldnt get to the button either. It was like it didnt exist. Somehow windows changed itself after like a year and my speakers worked lol.

---

### Post by moore.bryan on 2007-08-14
> **demonicdude said:**
> ermmm could u tell me if i'm doing it right lol? i downloaded the driver, unarchived it, went to terminal, went to the directory and typed make. So now i'm guessing its making something (idk what lol..) then after that i would type make intsall..?
*exactly...*

---

### Post by demonicdude on 2007-08-14
i've done all that, still nothing. There has to be some way to change the god damn output ](*,)

:KS:KS

---

### Post by moore.bryan on 2007-08-14
[I]now type ```
alsamixergui
```, unmute the first three things, and move the progress bars to the top.  exit out of the mixer and type ```
sudo alsactl store
```  now, edit your /etc/rc.local file to include ```
alsactl restore
```

let me know if anything's unclear...[/I]

---

### Post by demonicdude on 2007-08-14
in the alsamixergui the third one, i can't move the bar. It looks like its all the way down and i cant move it at all =/.

---

### Post by moore.bryan on 2007-08-14
*okay... just try ```
alsamixer
``` and use the arrow keys are your keyboard to navigate.*

---

### Post by demonicdude on 2007-08-14
ah the reason why that wouldnt move up is because its a switch >.>. 3dcontrol switch. H/o going to edit this once i do that stuff again.

Edit: Nope nothing =/. Thanks for all the help your giving though =)

---

### Post by Arthur Archnix on 2007-08-14
What does this return?
```
sudo cat /proc/asound/modules
sudo cat /proc/asound/pcm
aplay -L
```

And just for fun, try this:```

sudo gedit ~/.asoundrc
```
Paste this in there:
```
pcm.!default spdif
```
Save and close. Reboot. If that doesn't work, delete the stuff above and paste this in instead:
```
pcm.!default {
       type hw
       card 0
       device 2
}
```
Save, close, reboot.

---

### Post by demonicdude on 2007-08-14
sudo cat /proc/asound/modules:
 0 snd_ens1371

sudo cat /proc/asound/pcm:
00-01: ES1371/2 : ES1371 DAC1 : playback 1
00-00: ES1371/1 : ES1371 DAC2/ADC : playback 1 : capture 1

aplay -L:
PCM list:
cards 'cards.pcm'
front 'cards.pcm.front'
rear 'cards.pcm.rear'
center_lfe 'cards.pcm.center_lfe'
side 'cards.pcm.side'
surround40 'cards.pcm.surround40'
surround41 'cards.pcm.surround41'
surround50 'cards.pcm.surround50'
surround51 'cards.pcm.surround51'
surround71 'cards.pcm.surround71'
iec958 'cards.pcm.iec958'
spdif iec958
dmix 'cards.pcm.dmix'
dsnoop 'cards.pcm.dsnoop'
modem 'cards.pcm.modem'
phoneline 'cards.pcm.phoneline'
hw {
        @args.0 CARD
        @args.1 DEV
        @args.2 SUBDEV
        @args.CARD {
                type string
                default {
                        @func getenv
                        vars {
                                0 ALSA_PCM_CARD
                                1 ALSA_CARD
                        }
                        default {
                                @func refer
                                name 'defaults.pcm.card'
                        }
                }
        }
        @args.DEV {
                type integer
                default {
                        @func igetenv
                        vars {
                                0 ALSA_PCM_DEVICE
                        }
                        default {
                                @func refer
                                name 'defaults.pcm.device'
                        }
                }
        }
        @args.SUBDEV {
                type integer
                default {
                        @func refer
                        name 'defaults.pcm.subdevice'
                }
        }
        type hw
        card $CARD
        device $DEV
        subdevice $SUBDEV
        hint {
                show {
                        @func refer
                        name 'defaults.namehint.extended'
                }
                description 'Direct hardware device without any conversions'
        }
}
plughw {
        @args.0 CARD
        @args.1 DEV
        @args.2 SUBDEV
        @args.CARD {
                type string
                default {
                        @func getenv
                        vars {
                                0 ALSA_PCM_CARD
                                1 ALSA_CARD
                        }
                        default {
                                @func refer
                                name 'defaults.pcm.card'
                        }
                }
        }
        @args.DEV {
                type integer
                default {
                        @func igetenv
                        vars {
                                0 ALSA_PCM_DEVICE
                        }
                        default {
                                @func refer
                                name 'defaults.pcm.device'
                        }
                }
        }
        @args.SUBDEV {
                type integer
                default {
                        @func refer
                        name 'defaults.pcm.subdevice'
                }
        }
        type plug
        slave.pcm {
                type hw
                card $CARD
                device $DEV
                subdevice $SUBDEV
        }
        hint {
                show {
                        @func refer
                        name 'defaults.namehint.extended'
                }
                description 'Hardware device with all software conversions'
        }
}
plug {
        @args.0 SLAVE
        @args.SLAVE {
                type string
        }
        type plug
        slave.pcm $SLAVE
}
shm {
        @args.0 SOCKET
        @args.1 PCM
        @args.SOCKET {
                type string
        }
        @args.PCM {
                type string
        }
        type shm
        server $SOCKET
        pcm $PCM
}
tee {
        @args.0 SLAVE
        @args.1 FILE
        @args.2 FORMAT
        @args.SLAVE {
                type string
        }
        @args.FILE {
                type string
        }
        @args.FORMAT {
                type string
                default raw
        }
        type file
        slave.pcm $SLAVE
        file $FILE
        format $FORMAT
}
file {
        @args.0 FILE
        @args.1 FORMAT
        @args.FILE {
                type string
        }
        @args.FORMAT {
                type string
                default raw
        }
        type file
        slave.pcm null
        file $FILE
        format $FORMAT
}
null {
        type null
        hint {
                show {
                        @func refer
                        name 'defaults.namehint.basic'
                }
                description 'Discard all samples (playback) or generate zero samples (capture)'
        }
}
default {
        type hw
        card 0
        device 2
}
Tried the asoundrc file thing, didnt work T.T

---

### Post by Arthur Archnix on 2007-08-14
> =demonicdude;3190083]sudo cat /proc/asound/modules:
 0 snd_ens1371

Ok, this shows only one module loaded. If two were then blacklisted the non-ens might have solved your problem. :(

> sudo cat /proc/asound/pcm:
00-01: ES1371/2 : ES1371 DAC1 : playback 1
00-00: ES1371/1 : ES1371 DAC2/ADC : playback 1 : capture 1
This shows you two hardware profiles for your sound card (I think). What we need to do is tell ALSA only to use the second (again, I think).

> aplay -L:
iec958 'cards.pcm.iec958'
spdif iec958
modem 'cards.pcm.modem'
Again, I'm outside my paygrade here, but I think this just confirms that your card supports digital output (I know, windows confirms that, but whatever). It's the spdif I think. In your ALSA mixer, make sure the iec958 is muted, and the other digital iec958 is unmuted. Also, I think we should ask someone if blacklisting the modem might help. I'm not sure how to do that, but I've read threads were the modem being loaded may force analog playback. 

> Tried the asoundrc file thing, didnt work T.T
That may just because I copied and pasted it from another thread about a different distribution. If someone more schooled in ubuntu could help explain how to force ALSA to use the second config on your card, that may help too. 

Is it ~/.asoundrc? Or is it /etc/asoundrc or something else?

As you can see, I'm very interested in seeing you solve your problem. It's a frequent occurance with your speakers from what I've been able to find.

Oh and see if you can use "wrap" tags in your other post, or maybe code tags, so that the post  doesn't go  so long.

---

### Post by demonicdude on 2007-08-14
well, i dont have iec958 in alsamixer. =/

---

### Post by Arthur Archnix on 2007-08-14
Post a screenshot of alsamixer.

Edit: Thanks. Aside from the fact that I don't like your theme[-(

... I got nothing.:-k

Except to try and wrap you output above to make it easier for the real pros to follow the thread.

Best,

---

### Post by demonicdude on 2007-08-14
[IMG]http://i7.photobucket.com/albums/y283/sonictheholy/Screenshot.png[/IMG]

lol, sorry for the colors, i've been messing with the theme =D

Thats everything on i believe.

EDIT: IGNORE THAT MASTER IS MUTED, i just had it that way because i was testing something else out, It still doesnt work with that unmuted! dont be decieved >.>.

---

### Post by Arthur Archnix on 2007-08-14
Well, I think I've found the files that controls the default audio device. It's /etc/modprobe.d/alsa-base

Now if only we knew what to do with it... ;)

EDIT: How about this...from the ALSA page on your card...
```

sudo gedit ~/asoundrc
```
paste this:
```
 pcm.ens1371 {
          type hw
          card 0
       }
       
       ctl.ens1371 {
          type hw
          card 0
       }
```
save and close, restart may help. If it doesn't work, try swapping out card 1 instead of 0. 

Just FYI, I found another thread where a guy said that playing around with making an asoundrc files messed up sound totally so that even analog wouldn't work anymore. Not sure why, but I thought you should know.

EDIT 2: Sorry, I had 1370, not 1371

---

### Post by Arthur Archnix on 2007-08-14
Sorry, I know I'm doing a real scattergun approach here, but I'm just hoping someone more knowledgeable will come along and tell me to shut up while they help you. :)

Until then, try:
```
modprobe snd-ens1371
```
I doubt it will work, since lsmod shows it already loaded. But what they hay. Better than doing nothing. Now, let's see if I can find any more straws to grasp at somewhere on the inter-tubes...

Straw #2: When booting, go into grub, and then press E on your kernel to edit the boot config (only temporary for this boot only) and add
"acpi=ht" to the end of the kernel line.

If it works you can add it permanently later.

---

### Post by demonicdude on 2007-08-14
mm still no luck T.T. Thanks for all the help though =D. Maybe this will help idk? Well, like the card and everythin gis like that, i think i have like creative sound blaster with this??? i dunno its confusing...

link to it:[http://www.alsa-project.org/main/index.php/Matrix:Module-ens1371](http://www.alsa-project.org/main/index.php/Matrix:Module-ens1371)

---

### Post by demonicdude on 2007-08-15
*bump~~*

---

### Post by moore.bryan on 2007-08-15
*unfortunately, it looks as though you MAY have to compile your own kernel, if i read everything on the alsa site correctly...*

---

### Post by demonicdude on 2007-08-15
so  i would have to compile my own kernel.... Oh geez can anyone help me do that >.<.....

---

### Post by moore.bryan on 2007-08-15
[I]like i wrote, you MAY need to compile your own.  the problem with that approach, though, is it might answer some problems and create others.

[this]("http://www.howtoforge.com/kernel_compilation_ubuntu") is a pretty straight-forward guide...[/I]

---

### Post by demonicdude on 2007-08-15
hmm.. i think i'll hold off on that, until its absolutely necessary. There has to be a way to get that darn button somehow >.>

---

### Post by moore.bryan on 2007-08-15
[I]i don't blame you... i've had, let's just say, mixed success with self-compiled kernels.

could you do me favor and try to play something in xmms (or other program) from the command-line and post any errors from the term?[/I]

---

### Post by demonicdude on 2007-08-15
i sure can if you could tell me how XD. Sorry, i'm not used to the command stuff yet, Windows so makes all this easier, Except it hogs memory and crap like hell :P

---

### Post by moore.bryan on 2007-08-15
[I]not a problem... if you have xmms installed, just type
```
xmms /path/to/your/music_file.mp3
```
if you don't have xmms and just installed the "base" ubuntu right-off the cd, then try
```
rhythmbox /path/to/your/music_file.mp3
```[/I]

---

### Post by demonicdude on 2007-08-15
well i installed xmms for the heck of it :P. This is what i get:

Message: device: default


And then xmms launches and plays the file i selected. No sound through the boston digital speakers, sound through the crap analog 1995 compaq speakers :P.

---

### Post by moore.bryan on 2007-08-15
[I]okay, this might be going back over stuff you've already tried, but to keep things going... did you try [this stuff]("http://www.alsa-project.org/main/index.php/Matrix:Module-ens1371") for your card?  if so, it looks as though there's a "switch" somewhere for analog-digital... now, no site has been specific, but that could be on the card itself, on the computer, or somewhere in the settings--perhaps even in the kernel config.

this might also sound funny, but are you plugging the speakers into the digital output jack?

also, [here]("http://cybernightlife.50webs.com/ba735.html")'s someone who insists it's possible...[/I]

---

### Post by demonicdude on 2007-08-15
Hmm yeah, i'll try that site out again.

Well, theres three slots. One is for micrphone, other is for speakers, and one int he middle is for..  god knows what but it doesnt work either when i plug it ther e:P 

Yeah, i cant tell what the picture says, its 404'd lol.

Edit: This is interesting. When I was following the instructions ont hat first website for the quick installation of the alsa (i think >.<). I believe i installed the driver and lib fine, but when it got to the utils i get this:
configure: error: this packages requires a curses library
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.

also, i did not do this when installing:
Make a directory to store the alsa source code in: 
       cd /usr/src
       mkdir alsa
       cd alsa
       cp /downloads/alsa-* .


I dont think that is a big deal right?, I've been dling the files in the same directory anyways.

---

### Post by Arthur Archnix on 2007-08-15
Here's something...

> Getting SPDIF output

(from gralves from the Gentoo forums)

    * In GNOME Volume Control, under the Options tab, change the IEC958 to PCM. This option can be enabled in the preferences.
    * If you don't have GNOME Volume Control installed,
          o Edit /etc/asound.state. This file is where alsasound stores your mixer settings.
          o Find a line that says: 'IEC958 Playback Switch'. Near it you will find a line saying value:false. Change it to value:true.
          o Now find this line: 'IEC958 Playback AC97-SPSA'. Change its value to 0.
          o Restart alsa. 

Alternative way to enable SPDIF output automatically on login (tested on SoundBlaster Audigy):

    * add following lines to /etc/rc.local: 

 # Use COAX-digital output
 amixer set 'IEC958 Optical' 100 unmute
 amixer set 'Audigy Analog/Digital Output Jack' on

You can see the name of your card's digital output with:

 amixer scontrols

---

### Post by demonicdude on 2007-08-15
my asound.state file is blank!

---

### Post by Arthur Archnix on 2007-08-15
It's for a different distribution, but if it could be adapted to ubuntu... I'm not sure if the file names and locations are the same...

---

### Post by demonicdude on 2007-08-15
if i were able to install alsa-utils would it make a difference? right now, i'm getting this error


configure: error: this packages requires a curses library
make: *** No targets specified and no makefile found. Stop.
make: *** No rule to make target `install'. Stop.

Idk if i already have ala-utils, i probably do.

---

### Post by Arthur Archnix on 2007-08-15
Did you add this to /etc/rc.local, before exit 0?
```
# Use COAX-digital output
amixer set 'IEC958 Optical' 100 unmute
amixer set 'Audigy Analog/Digital Output Jack' on
```

---

### Post by demonicdude on 2007-08-16
yeah that didnt work

I also found the asound.state file as well, Its basically the volume control but in word form :/

I found something interesting though:

In the readme file of alsa-utils, it says

This package contains the command line utilities (bla bla bla)

(bla)
iecset		- a utility to show/set the IEC958 status bits

Now, when i try to use iecset this is what i get:

control "IEC958 Playback Default" not found


EDIT: well i got alsa-utils installed, i had to install libaca-dev, but i still dont get an iec option, nor does the sound work =(

---

### Post by Arthur Archnix on 2007-08-16
It's unfortunate you choose such a generic title for the thread. Someone who knows the answer might just skim past it. If possible, change it to something like "How to make digital output the default in 7.04 - then the name of your soundcard." Maybe if you can't change it an admin will do that for you.

---

### Post by demonicdude on 2007-08-16
i couldn't think of anything else lol. But i found some interesting stuff in my search for sound:

Aplay -L: list pcm devices:
front:CARD=AudioPCI,DEV=0
    Ensoniq AudioPCI, ES1371 DAC2/ADC
    Front speakers
surround40:CARD=AudioPCI,DEV=0
    Ensoniq AudioPCI, ES1371 DAC2/ADC
    4.0 Surround output to Front and Rear speakers
iec958:CARD=AudioPCI,DEV=0
    Ensoniq AudioPCI, ES1371 DAC2/ADC
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)

well would you look at that!, theres iec958!

when i try aplay -D *front/surround40/iec958 (one of the three) *musicfile.au* All that works is the front one with garbled sound on the analog, and *when the boston speakers fully up, * very soft garble on those! 

the other two give me this:
IEc:
ALSA lib setup.c:555:(add_elem) Cannot obtain info for CTL elem (PCM,'IEC958 Playback PCM Stream',0,0,0): No such file or directory
aplay: main:545: audio open error: No such file or directory
surround:
ALSA lib setup.c:555:(add_elem) Cannot obtain info for CTL elem (MIXER,'AC97 2ch->4ch Copy Switch',0,0,0): No such file or directory
aplay: main:545: audio open error: No such file or directory

same filed used for all three.

How would i tell an admin to change the title thread? like where or who -.-

Edit: Also, what i dont get is why the sound worked on Dapper, but not now? LIke, i didnt need to edit on dapper.

---

### Post by Arthur Archnix on 2007-08-16
[https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/94189](https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/94189)

I think that might be your answer on why it worked in Dapper but not Feisty. They may have decided to disable digital output by default. THe thread is pretty hilarious, since it says stuff like "people who want digital will know how to turn it on".  Geez, thanks for that tidbit of info!

---

### Post by demonicdude on 2007-08-16
LOL and here we are complaining about how i dont have sound :P. Damn those guys...

---

### Post by demonicdude on 2007-08-16
bump....


*sigh*

---

### Post by Arthur Archnix on 2007-08-16
I'll bump this and ask you to post your /etc/modprobe.d/alsa-base

---

### Post by moore.bryan on 2007-08-16
> **Arthur Archnix said:**
> [https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/94189](https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/94189)

I think that might be your answer on why it worked in Dapper but not Feisty. They may have decided to disable digital output by default. THe thread is pretty hilarious, since it says stuff like "people who want digital will know how to turn it on".  Geez, thanks for that tidbit of info!
*becoming more interested in compiling a kernel?  ;-)*

---

### Post by Arthur Archnix on 2007-08-16
But recompiling it how? What changes would he make when recompiling? It's not a module problem. It seems to be a rather "simple" matter of disabling analog output, and enabling digital output.

I know this may seem a bit silly demonicdude, but maybe start another thread asking that very question. How do I disable analog output and enabled digital output? I just can't believe there's no one on the forums who knows how to do this, I think it's more likely they just glance at your thread title and move on.

---

### Post by moore.bryan on 2007-08-16
> **Arthur Archnix said:**
> But recompiling it how? What changes would he make when recompiling? It's not a module problem. It seems to be a rather "simple" matter of disabling analog output, and enabling digital output.
[i]
on one of the forums i went bleary-eyed looking at to see if there was some simple answer for this, i saw many comments on how digital output is disabled in the kernel config... if we've hit a dead-end, compiling a new kernel can be useful on many fronts... not just a possible sound-fix, but also streamlining a machine.
:-)
just throwing thoughts out there...
[/i]

---

### Post by Arthur Archnix on 2007-08-16
Hmm... if that's true then I'd have to agree. I've recompiled a kernel before and it's not too hard. But still, I find it rather hard to believe that Ubuntu has disabled digital output in the kernel. At least, I doubt they'd disable it in such a way that the only way to turn it back on is by recompiling the kernel. I could be wrong.

---

### Post by moore.bryan on 2007-08-16
> **Arthur Archnix said:**
> Hmm... if that's true then I'd have to agree. I've recompiled a kernel before and it's not too hard. But still, I find it rather hard to believe that Ubuntu has disabled digital output in the kernel. At least, I doubt they'd disable it in such a way that the only way to turn it back on is by recompiling the kernel. I could be wrong.
[i]
i'm with you... but it does all depend on the kernels running.  when i did a minimalist install, there was, surprisingly, a lot turned-off by default... but not what one would expect: like wireless.

;-)
[/i]

---

### Post by demonicdude on 2007-08-16
Alright. I think i'll take a shot at that kernel thing. First, can someone give me a detailed explanation on how to do it :P. And second, do i have to do anything to ubuntu, like reinstall it or anything like that?

---

### Post by Arthur Archnix on 2007-08-16
Someone probably can. But I'm afraid I won't. I think it's wrong to try and recompile your kernel without trying one more thread on the forums. Be very specific in the title of the thread what you're having trouble with. Otherwise... good luck!

---

### Post by moore.bryan on 2007-08-16
> **Arthur Archnix said:**
> Someone probably can. But I'm afraid I won't. I think it's wrong to try and recompile your kernel without trying one more thread on the forums. Be very specific in the title of the thread what you're having trouble with. Otherwise... good luck!
[i]
i agree with "art;" for this issue, compiling should be a last resort.  post a much more specifically titled thread and hope.  you can read-up on kernelling [here]("http://www.howtoforge.com/kernel_compilation_ubuntu").[/i]

---

### Post by demonicdude on 2007-08-16
Ok, so before i make a new thread, what should i name it lol. I'm really bad at describing stuff, *as you can see by the title :P*. Should it be like this?:

"*Ubuntu 7.04 sound issues, switching from Analog to Digital Output "CreativeAudioPCi soundcard /or ENS1731"*

Or should i go like this:

"*Help, switching sound from analog output to digital output "creative audoPCI/ or ENS1371"*

And my first post, what information should i give? I probably should tell them that with my digital speakers, the sound doesn't work, and with the analog they do. Also, should i include aplay -l, -L ? Should i also make a link to this thread? 

I was thinking to include just the aplay -L and information about how i dont have a god damn iec958 button :P.

---

### Post by Arthur Archnix on 2007-08-16
That looks pretty good. I might do:

How to disable analog audio / enable digital out on Feisty: Speakers require digital only

Something simple but clear. Linking to the thread is a good idea. I'd just include the name of your card, the name of your speakers, the fact that old crappy speakers play the sound fine, but these digital only ones don't. And that you can't for the life of you figure out how or what to change in feisty to switch. 

What we know: You're card supports digital out. Your speakers work. You've had this working before under 6.06. 

Good luck!

---

### Post by sada_lives on 2007-08-17
For the record, I use Boston BA735 digital speakers, and the solution was entering Volume Control (via double clicking the speaker icon in the taskbar), navigating to "switches", and making sure "SB Live Analog/Digital Output Jack" is checked.  I have Headphone LFE checked as well, but I am not sure if that is relevant.

Obviously yours will not say "SB Live", but I hope some similar switch is there to help you.

---

