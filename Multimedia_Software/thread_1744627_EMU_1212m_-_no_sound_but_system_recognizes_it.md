---
title: "EMU 1212m - no sound but system recognizes it"
date: 2011-04-30
forum: Multimedia Software
---

### Post by Kubatko on 2011-04-30
Hello,

I have installed ubuntu (version 11.04) on my desktop pc and i need to enable there sound somehow. I would be happy if someone could help me. My soundcard is PCI EMU 1212m

if i do lspci -v it gives me

```
05:00.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
    Subsystem: Creative Labs E-MU 1010
    Flags: medium devsel, IRQ 16
    I/O ports at ec00 [size=32]
    Capabilities: <access denied>
    Kernel modules: snd-emu10k1

```So it seems that Ubuntu knows what card i have but even though i try to play anything nothing comes out.
But if i open up the sound preferences window and go to hardware nothing is listed there, no device.
My volume slider is to 100% so i do not know where the fault might be.

I guess it might not be anything serious but i would appreciate any help.

This is the file alsa-project gave me

[http://www.alsa-project.org/db/?f=672f499fd6784597356084ead2eb126ac1e3a19c](http://www.alsa-project.org/db/?f=672f499fd6784597356084ead2eb126ac1e3a19c)

This is alsa-base.conf

```
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modpro$
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss $
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sb$
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-mi$
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k$
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ;$
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2




```Thank you for your time.

Jakub

---

### Post by lidex on 2011-04-30
The problem is alsa doesn't recognize your card. Not sure why. Try re-installing alsa.
Using a Terminal="Applications->Accessories->Terminal"
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```
**Reboot.**

For a 'command not found' error simply install aptitude:
```
sudo apt-get install aptitude
```

---

### Post by Kubatko on 2011-05-01
Hello,

thank you very much for your reply!

Something has changed but no sound so far

this is alsa.conf after the update you sent me

```
#
#  ALSA library configuration file
#

# pre-load the configuration files

@hooks [
    {
        func load
        files [
            "/usr/share/alsa/pulse.conf"
            "/usr/share/alsa/bluetooth.conf"
            "/etc/asound.conf"
            "~/.asoundrc"
        ]
        errors false
    }
]

# load card-specific configuration files (on request)

cards.@hooks [
    {
        func load
        files [
            {
                @func concat
                strings [
                    { @func datadir }
                    "/cards/aliases.conf"
                ]
            }
        ]
    }
    {
        func load_for_all_cards
        files [
            {
                @func concat
                strings [
                    { @func datadir }
                    "/cards/"
                    { @func private_string }
                    ".conf"
                ]
            }
        ]
        errors false
    }
]

#
# defaults
#

# show all name hints also for definitions without hint {} section
defaults.namehint.showall on
# show just basic name hints
defaults.namehint.basic on
# show extended name hints
defaults.namehint.extended on
#
defaults.ctl.card 0
defaults.pcm.card 0
defaults.pcm.device 0
defaults.pcm.subdevice -1
defaults.pcm.nonblock 1
defaults.pcm.compat 0
defaults.pcm.minperiodtime 5000        # in us
defaults.pcm.ipc_key 5678293
defaults.pcm.ipc_gid audio
defaults.pcm.ipc_perm 0660
defaults.pcm.dmix.max_periods 0
defaults.pcm.dmix.rate 48000
defaults.pcm.dmix.format "unchanged"
defaults.pcm.dmix.card defaults.pcm.card
defaults.pcm.dmix.device defaults.pcm.device
defaults.pcm.dsnoop.card defaults.pcm.card
defaults.pcm.dsnoop.device defaults.pcm.device
defaults.pcm.front.card defaults.pcm.card
defaults.pcm.front.device defaults.pcm.device
defaults.pcm.rear.card defaults.pcm.card
defaults.pcm.rear.device defaults.pcm.device
defaults.pcm.center_lfe.card defaults.pcm.card
defaults.pcm.center_lfe.device defaults.pcm.device
defaults.pcm.side.card defaults.pcm.card
defaults.pcm.side.device defaults.pcm.device
defaults.pcm.surround40.card defaults.pcm.card
defaults.pcm.surround40.device defaults.pcm.device
defaults.pcm.surround41.card defaults.pcm.card
defaults.pcm.surround41.device defaults.pcm.device
defaults.pcm.surround50.card defaults.pcm.card
defaults.pcm.surround50.device defaults.pcm.device
defaults.pcm.surround51.card defaults.pcm.card
defaults.pcm.surround51.device defaults.pcm.device
defaults.pcm.surround71.card defaults.pcm.card
defaults.pcm.surround71.device defaults.pcm.device
defaults.pcm.iec958.card defaults.pcm.card
defaults.pcm.iec958.device defaults.pcm.device
defaults.pcm.modem.card defaults.pcm.card
defaults.pcm.modem.device defaults.pcm.device
# truncate files via file or tee PCM
defaults.pcm.file_format    "raw"
defaults.pcm.file_truncate    true
defaults.rawmidi.card 0
defaults.rawmidi.device 0
defaults.rawmidi.subdevice -1
defaults.hwdep.card 0
defaults.hwdep.device 0
defaults.timer.class 2
defaults.timer.sclass 0
defaults.timer.card 0
defaults.timer.device 0
defaults.timer.subdevice 0

#
#  PCM interface
#

# redirect to load-on-demand extended pcm definitions
pcm.cards cards.pcm

pcm.default cards.pcm.default
pcm.front cards.pcm.front
pcm.rear cards.pcm.rear
pcm.center_lfe cards.pcm.center_lfe
pcm.side cards.pcm.side
pcm.surround40 cards.pcm.surround40
pcm.surround41 cards.pcm.surround41
pcm.surround50 cards.pcm.surround50
pcm.surround51 cards.pcm.surround51
pcm.surround71 cards.pcm.surround71
pcm.iec958 cards.pcm.iec958
pcm.spdif iec958
pcm.hdmi cards.pcm.hdmi
pcm.dmix cards.pcm.dmix
pcm.dsnoop cards.pcm.dsnoop
pcm.modem cards.pcm.modem
pcm.phoneline cards.pcm.phoneline

pcm.hw {
    @args [ CARD DEV SUBDEV ]
    @args.CARD {
        type string
        default {
            @func getenv
            vars [
                ALSA_PCM_CARD
                ALSA_CARD
            ]
            default {
                @func refer
                name defaults.pcm.card
            }
        }
    }
    @args.DEV {
        type integer
        default {
            @func igetenv
            vars [
                ALSA_PCM_DEVICE
            ]
            default {
                @func refer
                name defaults.pcm.device
            }
        }
    }
    @args.SUBDEV {
        type integer
        default {
            @func refer
            name defaults.pcm.subdevice
        }
    }        
    type hw
    card $CARD
    device $DEV
    subdevice $SUBDEV
    hint {
        show {
            @func refer
            name defaults.namehint.extended
        }
        description "Direct hardware device without any conversions"
    }
}

pcm.plughw {
    @args [ CARD DEV SUBDEV ]
    @args.CARD {
        type string
        default {
            @func getenv
            vars [
                ALSA_PCM_CARD
                ALSA_CARD
            ]
            default {
                @func refer
                name defaults.pcm.card
            }
        }
    }
    @args.DEV {
        type integer
        default {
            @func igetenv
            vars [
                ALSA_PCM_DEVICE
            ]
            default {
                @func refer
                name defaults.pcm.device
            }
        }
    }
    @args.SUBDEV {
        type integer
        default {
            @func refer
            name defaults.pcm.subdevice
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
            name defaults.namehint.extended
        }
        description "Hardware device with all software conversions"
    }
}

pcm.plug {
    @args [ SLAVE ]
    @args.SLAVE {
        type string
    }
    type plug
    slave.pcm $SLAVE
}

pcm.shm {
    @args [ SOCKET PCM ]
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

pcm.tee {
    @args [ SLAVE FILE FORMAT ]
    @args.SLAVE {
        type string
    }
    @args.FILE {
        type string
    }
    @args.FORMAT {
        type string
        default {
            @func refer
            name defaults.pcm.file_format
        }
    }
    type file
    slave.pcm $SLAVE
    file $FILE
    format $FORMAT
    truncate {
        @func refer
        name defaults.pcm.file_truncate
    }
}

pcm.file {
    @args [ FILE FORMAT ]
    @args.FILE {
        type string
    }
    @args.FORMAT {
        type string
        default {
            @func refer
            name defaults.pcm.file_format
        }
    }
    type file
    slave.pcm null
    file $FILE
    format $FORMAT
    truncate {
        @func refer
        name defaults.pcm.file_truncate
    }
}

pcm.null {
    type null
    hint {
        show {
            @func refer
            name defaults.namehint.basic
        }
        description "Discard all samples (playback) or generate zero samples (capture)"
    }
}

#
#  Control interface
#
    
ctl.default {
    type hw
    card {
        @func getenv
        vars [
            ALSA_CTL_CARD
            ALSA_CARD
        ]
        default {
            @func refer
            name defaults.ctl.card
        }
    }
}

ctl.hw {
    @args [ CARD ]
    @args.CARD {
        type string
        default {
            @func getenv
            vars [
                ALSA_CTL_CARD
                ALSA_CARD
            ]
            default {
                @func refer
                name defaults.ctl.card
            }
        }
    }
    type hw
    card $CARD
}

ctl.shm {
    @args [ SOCKET CTL ]
    @args.SOCKET {
        type string
    }
    @args.CTL {
        type string
    }
    type shm
    server $SOCKET
    ctl $CTL
}

#
#  RawMidi interface
#

rawmidi.default {
    type hw
    card {
        @func getenv
        vars [
            ALSA_RAWMIDI_CARD
            ALSA_CARD
        ]
        default {
            @func refer
            name defaults.rawmidi.card
        }
    }
    device {
        @func igetenv
        vars [
            ALSA_RAWMIDI_DEVICE
        ]
        default {
            @func refer
            name defaults.rawmidi.device
        }
    }
}

rawmidi.hw {
    @args [ CARD DEV SUBDEV ]
    @args.CARD {
        type string
        default {
            @func getenv
            vars [
                ALSA_RAWMIDI_CARD
                ALSA_CARD
            ]
            default {
                @func refer
                name defaults.rawmidi.card
            }
        }
    }
    @args.DEV {
        type integer
        default {
            @func igetenv
            vars [
                ALSA_RAWMIDI_DEVICE
            ]
            default {
                @func refer
                name defaults.rawmidi.device
            }
        }
    }
    @args.SUBDEV {
        type integer
        default -1
    }
    type hw
    card $CARD
    device $DEV
    subdevice $SUBDEV
    hint {
        description "Direct rawmidi driver device"
        device $DEV
    }
}

rawmidi.virtual {
    @args [ MERGE ]
    @args.MERGE {
        type string
        default 1
    }
    type virtual
    merge $MERGE
}

#
#  Sequencer interface
#

seq.default {
    type hw
}

seq.hw {
    type hw
}

#
#  HwDep interface
#

hwdep.default {
    type hw
    card {
        @func getenv
        vars [
            ALSA_HWDEP_CARD
            ALSA_CARD
        ]
        default {
            @func refer
            name defaults.hwdep.card
        }
    }
    device {
        @func igetenv
        vars [
            ALSA_HWDEP_DEVICE
        ]
        default {
            @func refer
            name defaults.hwdep.device
        }
    }
}

hwdep.hw {
    @args [ CARD DEV ]
    @args.CARD {
        type string
        default {
            @func getenv
            vars [
                ALSA_HWDEP_CARD
                ALSA_CARD
            ]
            default {
                @func refer
                name defaults.hwdep.card
            }
        }
    }
    @args.DEV {
        type integer
        default {
            @func igetenv
            vars [
                ALSA_HWDEP_DEVICE
            ]
            default {
                @func refer
                name defaults.hwdep.device
            }
        }
    }
    type hw
    card $CARD
    device $DEV
}

#
#  Timer interface
#

timer_query.default {
    type hw
}

timer_query.hw {
    type hw
}

timer.default {
    type hw
    class {
        @func refer
        name defaults.timer.class
    }
    sclass {
        @func refer
        name defaults.timer.sclass
    }
    card {
        @func refer
        name defaults.timer.card
    }
    device {
        @func refer
        name defaults.timer.device
    }
    subdevice {
        @func refer
        name defaults.timer.subdevice
    }
    hint.description "Default direct hardware timer device"
}

timer.hw {
    @args [ CLASS SCLASS CARD DEV SUBDEV ]
    @args.CLASS {
        type integer
        default {
            @func refer
            name defaults.timer.class
        }
    }
    @args.SCLASS {
        type integer
        default {
            @func refer
            name defaults.timer.sclass
        }
    }
    @args.CARD {
        type string
        default {
            @func refer
            name defaults.timer.card
        }
    }
    @args.DEV {
        type integer
        default {
            @func refer
            name defaults.timer.device
        }
    }
    @args.SUBDEV {
        type integer
        default {
            @func refer
            name defaults.timer.subdevice
        }
    }
    type hw
    class $CLASS
    sclass $SCLASS
    card $CARD
    device $DEV
    subdevice $SUBDEV
}
```

I tried to run some troubleshooting procedure from ubuntu help. here is what i got (the most intresting are probably the last lines):

```
jakubholovsky@Jakub-Ubuntu-PC:~$ cat /proc/asound/{version,cards,devices,hwdep,pcm,seq/clients}; sudo rm /etc/asound.conf; sudo rm -r ~/.pulse ~/.asound* ;sudo rm ~/.pulse-cookie; sudo apt-get update; sudo apt-get install aptitude; sudo aptitude install paman gnome-alsamixer libasound2-plugins padevchooser libsdl1.2debian-pulseaudio; sudo lshw -short;ls -lart /dev/snd;  cat /dev/sndstat; lspci -nn;  sudo which alsactl; sudo fuser -v /dev/dsp /dev/snd/* ; dpkg -S bin/slmodemd; dmesg | egrep 'EMU|probe|emu|ALSA|alsa|ac97|udi|snd|ound|irmware'; sudo /etc/init.d/sl-modem-daemon status; sudo grep model /etc/modprobe.d/* ; sudo dmidecode|grep roduct; lsmod | egrep 'snd|usb|midi|udio'; aplay -l; sudo lshw -C sound
Advanced Linux Sound Architecture Driver Version 1.0.23.
--- no soundcards ---
  1:        : sequencer
 33:        : timer
Client info
  cur  clients : 1
  peak clients : 1
  max  clients : 192

Client   0 : "System" [Kernel]
  Port   0 : "Timer" (Rwe-)
  Port   1 : "Announce" (R-e-)
Client  14 : "Midi Through" [Kernel]
  Port   0 : "Midi Through Port-0" (RWe-)
[sudo] password for jakubholovsky: 
rm: cannot remove `/etc/asound.conf': No such file or directory
rm: cannot remove `/home/jakubholovsky/.asound*': No such file or directory
Ign http://cz.archive.ubuntu.com natty InRelease
Ign http://cz.archive.ubuntu.com natty-updates InRelease                               
Hit http://cz.archive.ubuntu.com natty Release.gpg                                     
Hit http://cz.archive.ubuntu.com natty-updates Release.gpg                             
Hit http://cz.archive.ubuntu.com natty Release                                         
Ign http://extras.ubuntu.com natty InRelease                                           
Hit http://cz.archive.ubuntu.com natty-updates Release                                 
Ign http://archive.canonical.com natty InRelease                                       
Ign http://security.ubuntu.com natty-security InRelease                                
Hit http://cz.archive.ubuntu.com natty/main Sources                                    
Hit http://cz.archive.ubuntu.com natty/restricted Sources                              
Hit http://cz.archive.ubuntu.com natty/universe Sources                                
Hit http://cz.archive.ubuntu.com natty/multiverse Sources                              
Hit http://cz.archive.ubuntu.com natty/main amd64 Packages                             
Hit http://cz.archive.ubuntu.com natty/restricted amd64 Packages                       
Hit http://cz.archive.ubuntu.com natty/universe amd64 Packages                         
Hit http://cz.archive.ubuntu.com natty/multiverse amd64 Packages                       
Ign http://cz.archive.ubuntu.com natty/main TranslationIndex                           
Ign http://cz.archive.ubuntu.com natty/multiverse TranslationIndex                     
Ign http://cz.archive.ubuntu.com natty/restricted TranslationIndex                     
Hit http://extras.ubuntu.com natty Release.gpg                                         
Hit http://archive.canonical.com natty Release.gpg                                     
Hit http://security.ubuntu.com natty-security Release.gpg            
Ign http://cz.archive.ubuntu.com natty/universe TranslationIndex     
Hit http://cz.archive.ubuntu.com natty-updates/main Sources                            
Hit http://cz.archive.ubuntu.com natty-updates/restricted Sources                      
Hit http://cz.archive.ubuntu.com natty-updates/universe Sources                        
Hit http://cz.archive.ubuntu.com natty-updates/multiverse Sources                      
Hit http://cz.archive.ubuntu.com natty-updates/main amd64 Packages                     
Hit http://cz.archive.ubuntu.com natty-updates/restricted amd64 Packages               
Hit http://cz.archive.ubuntu.com natty-updates/universe amd64 Packages                 
Hit http://cz.archive.ubuntu.com natty-updates/multiverse amd64 Packages               
Ign http://cz.archive.ubuntu.com natty-updates/main TranslationIndex                   
Ign http://cz.archive.ubuntu.com natty-updates/multiverse TranslationIndex             
Ign http://cz.archive.ubuntu.com natty-updates/restricted TranslationIndex             
Ign http://cz.archive.ubuntu.com natty-updates/universe TranslationIndex               
Hit http://extras.ubuntu.com natty Release                                             
Hit http://archive.canonical.com natty Release                                         
Hit http://security.ubuntu.com natty-security Release                                  
Hit http://extras.ubuntu.com natty/main Sources                                        
Hit http://archive.canonical.com natty/partner amd64 Packages        
Hit http://security.ubuntu.com natty-security/main Sources           
Hit http://extras.ubuntu.com natty/main amd64 Packages               
Ign http://extras.ubuntu.com natty/main TranslationIndex             
Ign http://archive.canonical.com natty/partner TranslationIndex      
Hit http://security.ubuntu.com natty-security/restricted Sources     
Hit http://security.ubuntu.com natty-security/universe Sources       
Hit http://security.ubuntu.com natty-security/multiverse Sources     
Hit http://security.ubuntu.com natty-security/main amd64 Packages    
Hit http://security.ubuntu.com natty-security/restricted amd64 Packages
Ign http://cz.archive.ubuntu.com natty/main Translation-en_US        
Ign http://cz.archive.ubuntu.com natty/main Translation-en           
Ign http://cz.archive.ubuntu.com natty/multiverse Translation-en_US  
Ign http://cz.archive.ubuntu.com natty/multiverse Translation-en     
Ign http://cz.archive.ubuntu.com natty/restricted Translation-en_US  
Ign http://cz.archive.ubuntu.com natty/restricted Translation-en     
Ign http://cz.archive.ubuntu.com natty/universe Translation-en_US    
Hit http://security.ubuntu.com natty-security/universe amd64 Packages
Hit http://security.ubuntu.com natty-security/multiverse amd64 Packages
Ign http://security.ubuntu.com natty-security/main TranslationIndex  
Ign http://security.ubuntu.com natty-security/multiverse TranslationIndex
Ign http://security.ubuntu.com natty-security/restricted TranslationIndex
Ign http://security.ubuntu.com natty-security/universe TranslationIndex
Ign http://cz.archive.ubuntu.com natty/universe Translation-en       
Ign http://cz.archive.ubuntu.com natty-updates/main Translation-en_US
Ign http://cz.archive.ubuntu.com natty-updates/main Translation-en   
Ign http://cz.archive.ubuntu.com natty-updates/multiverse Translation-en_US
Ign http://cz.archive.ubuntu.com natty-updates/multiverse Translation-en
Ign http://cz.archive.ubuntu.com natty-updates/restricted Translation-en_US
Ign http://cz.archive.ubuntu.com natty-updates/restricted Translation-en
Ign http://cz.archive.ubuntu.com natty-updates/universe Translation-en_US
Ign http://cz.archive.ubuntu.com natty-updates/universe Translation-en
Ign http://extras.ubuntu.com natty/main Translation-en_US            
Ign http://archive.canonical.com natty/partner Translation-en_US     
Ign http://extras.ubuntu.com natty/main Translation-en
Ign http://archive.canonical.com natty/partner Translation-en
Ign http://security.ubuntu.com natty-security/main Translation-en_US
Ign http://security.ubuntu.com natty-security/main Translation-en
Ign http://security.ubuntu.com natty-security/multiverse Translation-en_US
Ign http://security.ubuntu.com natty-security/multiverse Translation-en
Ign http://security.ubuntu.com natty-security/restricted Translation-en_US
Ign http://security.ubuntu.com natty-security/restricted Translation-en
Ign http://security.ubuntu.com natty-security/universe Translation-en_US
Ign http://security.ubuntu.com natty-security/universe Translation-en
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
aptitude is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
The following NEW packages will be installed:
  libgconfmm-2.6-1c2{a} padevchooser paman paprefs{a} pavumeter{a} 
  pulseaudio-module-zeroconf{a} 
0 packages upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 261 kB of archives. After unpacking 1,876 kB will be used.
Do you want to continue? [Y/n/?] y
Get:1 http://cz.archive.ubuntu.com/ubuntu/ natty/main libgconfmm-2.6-1c2 amd64 2.28.0-1 [30.4 kB]
Get:2 http://cz.archive.ubuntu.com/ubuntu/ natty/universe pavumeter amd64 0.9.3-1ubuntu1 [30.1 kB]
Get:3 http://cz.archive.ubuntu.com/ubuntu/ natty/universe paman amd64 0.9.4-1ubuntu2 [92.5 kB]
Get:4 http://cz.archive.ubuntu.com/ubuntu/ natty/main pulseaudio-module-zeroconf amd64 1:0.9.22+stable-queue-24-g67d18-0ubuntu3 [22.3 kB]
Get:5 http://cz.archive.ubuntu.com/ubuntu/ natty/universe paprefs amd64 0.9.9-2ubuntu1 [63.9 kB]
Get:6 http://cz.archive.ubuntu.com/ubuntu/ natty/universe padevchooser amd64 0.9.3-2ubuntu4 [21.6 kB]
Fetched 261 kB in 0s (568 kB/s)     
Selecting previously deselected package libgconfmm-2.6-1c2.
(Reading database ... 135489 files and directories currently installed.)
Unpacking libgconfmm-2.6-1c2 (from .../libgconfmm-2.6-1c2_2.28.0-1_amd64.deb) ...
Selecting previously deselected package pavumeter.
Unpacking pavumeter (from .../pavumeter_0.9.3-1ubuntu1_amd64.deb) ...
Selecting previously deselected package paman.
Unpacking paman (from .../paman_0.9.4-1ubuntu2_amd64.deb) ...
Selecting previously deselected package pulseaudio-module-zeroconf.
Unpacking pulseaudio-module-zeroconf (from .../pulseaudio-module-zeroconf_1%3a0.9.22+stable-queue-24-g67d18-0ubuntu3_amd64.deb) ...
Selecting previously deselected package paprefs.
Unpacking paprefs (from .../paprefs_0.9.9-2ubuntu1_amd64.deb) ...
Selecting previously deselected package padevchooser.
Unpacking padevchooser (from .../padevchooser_0.9.3-2ubuntu4_amd64.deb) ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for man-db ...
Processing triggers for python-support ...
Setting up libgconfmm-2.6-1c2 (2.28.0-1) ...
Setting up pavumeter (0.9.3-1ubuntu1) ...
Setting up paman (0.9.4-1ubuntu2) ...
Setting up pulseaudio-module-zeroconf (1:0.9.22+stable-queue-24-g67d18-0ubuntu3) ...
Setting up paprefs (0.9.9-2ubuntu1) ...
Setting up padevchooser (0.9.3-2ubuntu4) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
                                         
H/W path             Device      Class       Description
========================================================
                                 system      System Product Name (To Be Filled By O.E.M.
/0                               bus         P5Q DELUXE
/0/0                             memory      64KiB BIOS
/0/4                             processor   Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.4
/0/4/5                           memory      128KiB L1 cache
/0/4/6                           memory      8MiB L2 cache
/0/3e                            memory      4GiB System Memory
/0/3e/0                          memory      2GiB DIMM DDR2 Synchronous 800 MHz (1.2 ns)
/0/3e/1                          memory      DIMM [empty]
/0/3e/2                          memory      2GiB DIMM DDR2 Synchronous 800 MHz (1.2 ns)
/0/3e/3                          memory      DIMM [empty]
/0/100                           bridge      4 Series Chipset DRAM Controller
/0/100/1                         bridge      4 Series Chipset PCI Express Root Port
/0/100/1/0                       display     G84 [GeForce 8600 GT]
/0/100/1a                        bus         82801JI (ICH10 Family) USB UHCI Controller 
/0/100/1a.1                      bus         82801JI (ICH10 Family) USB UHCI Controller 
/0/100/1a.2                      bus         82801JI (ICH10 Family) USB UHCI Controller 
/0/100/1a.7                      bus         82801JI (ICH10 Family) USB2 EHCI Controller
/0/100/1c                        bridge      82801JI (ICH10 Family) PCI Express Root Por
/0/100/1c.4                      bridge      82801JI (ICH10 Family) PCI Express Root Por
/0/100/1c.4/0        scsi5       storage     88SE6121 SATA II Controller
/0/100/1c.4/0/0.0.0  /dev/sdc    disk        8589MB Config   Disk 0
/0/100/1c.5                      bridge      82801JI (ICH10 Family) PCI Express Root Por
/0/100/1c.5/0        eth0        network     88E8056 PCI-E Gigabit Ethernet Controller
/0/100/1d                        bus         82801JI (ICH10 Family) USB UHCI Controller 
/0/100/1d.1                      bus         82801JI (ICH10 Family) USB UHCI Controller 
/0/100/1d.2                      bus         82801JI (ICH10 Family) USB UHCI Controller 
/0/100/1d.7                      bus         82801JI (ICH10 Family) USB2 EHCI Controller
/0/100/1e                        bridge      82801 PCI Bridge
/0/100/1e/0                      multimedia  SB Audigy
/0/100/1e/0.2                    bus         SB Audigy FireWire Port
/0/100/1e/2          eth1        network     88E8001 Gigabit Ethernet Controller
/0/100/1e/3                      bus         FW322/323
/0/100/1f                        bridge      82801JIR (ICH10R) LPC Interface Controller
/0/100/1f.2          scsi0       storage     82801JI (ICH10 Family) 4 port SATA IDE Cont
/0/100/1f.2/0        /dev/sda    disk        500GB ST3500320NS
/0/100/1f.2/0/1      /dev/sda1   volume      195GiB Windows NTFS volume
/0/100/1f.2/0/2      /dev/sda2   volume      270GiB Windows NTFS volume
/0/100/1f.2/1        /dev/sdb    disk        500GB ST3500320NS
/0/100/1f.2/1/1      /dev/sdb1   volume      436GiB Windows NTFS volume
/0/100/1f.2/1/2      /dev/sdb2   volume      29GiB Extended partition
/0/100/1f.2/1/2/5    /dev/sdb5   volume      25GiB Linux filesystem partition
/0/100/1f.2/1/2/6    /dev/sdb6   volume      3814MiB Linux swap / Solaris partition
/0/100/1f.3                      bus         82801JI (ICH10 Family) SMBus Controller
/0/100/1f.5          scsi3       storage     82801JI (ICH10 Family) 2 port SATA IDE Cont
/0/100/1f.5/0.0.0    /dev/cdrom  disk        DRW-2014L1T
/0/1                 scsi6       storage     
/0/1/0.0.0           /dev/sdd    disk        SCSI Disk
/0/1/0.0.1           /dev/sde    disk        SCSI Disk
/0/1/0.0.2           /dev/sdf    disk        SCSI Disk
/0/1/0.0.3           /dev/sdg    disk        SCSI Disk
total 0
drwxr-xr-x   2 root root       80 2011-05-01 07:40 .
crw-rw----+  1 root audio 116, 33 2011-05-01 07:40 timer
crw-rw----+  1 root audio 116,  1 2011-05-01 07:40 seq
drwxr-xr-x  17 root root     4940 2011-05-01 07:52 ..
cat: /dev/sndstat: No such file or directory
00:00.0 Host bridge [0600]: Intel Corporation 4 Series Chipset DRAM Controller [8086:2e20] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation 4 Series Chipset PCI Express Root Port [8086:2e21] (rev 03)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4 [8086:3a37]
00:1a.1 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5 [8086:3a38]
00:1a.2 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6 [8086:3a39]
00:1a.7 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2 [8086:3a3c]
00:1c.0 PCI bridge [0604]: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1 [8086:3a40]
00:1c.4 PCI bridge [0604]: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 5 [8086:3a48]
00:1c.5 PCI bridge [0604]: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 6 [8086:3a4a]
00:1d.0 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1 [8086:3a34]
00:1d.1 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2 [8086:3a35]
00:1d.2 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3 [8086:3a36]
00:1d.7 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1 [8086:3a3a]
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 90)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller [8086:3a16]
00:1f.2 IDE interface [0101]: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller #1 [8086:3a20]
00:1f.3 SMBus [0c05]: Intel Corporation 82801JI (ICH10 Family) SMBus Controller [8086:3a30]
00:1f.5 IDE interface [0101]: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller #2 [8086:3a26]
01:00.0 VGA compatible controller [0300]: nVidia Corporation G84 [GeForce 8600 GT] [10de:0402] (rev a1)
02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller [11ab:4364] (rev 12)
03:00.0 IDE interface [0101]: Marvell Technology Group Ltd. 88SE6121 SATA II Controller [11ab:6121] (rev b2)
05:00.0 Multimedia audio controller [0401]: Creative Labs SB Audigy [1102:0004] (rev 03)
05:00.2 FireWire (IEEE 1394) [0c00]: Creative Labs SB Audigy FireWire Port [1102:4001] (rev 01)
05:02.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller [11ab:4320] (rev 14)
05:03.0 FireWire (IEEE 1394) [0c00]: Agere Systems FW322/323 [11c1:5811] (rev 70)
/sbin/alsactl
Specified filename /dev/dsp does not exist.
dpkg-query: no path found matching pattern *bin/slmodemd*.
[    0.000000] No AGP bridge found
[    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
[    0.000000] No NUMA configuration found
[    0.000000] No AGP bridge found
[    0.719078] ACPI: No dock devices found.
[    0.719082] HEST: Table not found.
[    0.779567] pnp: PnP ACPI: found 17 devices
[    0.792633] audit: initializing netlink socket (disabled)
[    0.792646] type=2000 audit(1304235621.790:1): initialized
[    0.810161] ERST: Table is not found!
[    1.117713] Fixed MDIO Bus: probed
[    1.210183] hub 1-0:1.0: USB hub found
[    1.230178] hub 2-0:1.0: USB hub found
[    1.230512] hub 3-0:1.0: USB hub found
[    1.230765] hub 4-0:1.0: USB hub found
[    1.240202] hub 5-0:1.0: USB hub found
[    1.240455] hub 6-0:1.0: USB hub found
[    1.240697] hub 7-0:1.0: USB hub found
[    1.240949] hub 8-0:1.0: USB hub found
[    1.242139] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.243565] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    5.455409] lp: driver loaded but no devices found
[    5.992010] type=1400 audit(1304228427.242:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=499 comm="apparmor_parser"
[    5.992052] type=1400 audit(1304228427.242:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=567 comm="apparmor_parser"
[    5.992200] type=1400 audit(1304228427.242:4): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=649 comm="apparmor_parser"
[    5.992808] type=1400 audit(1304228427.242:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=499 comm="apparmor_parser"
[    5.992848] type=1400 audit(1304228427.242:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=567 comm="apparmor_parser"
[    5.993009] type=1400 audit(1304228427.242:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=649 comm="apparmor_parser"
[    5.993338] type=1400 audit(1304228427.242:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=499 comm="apparmor_parser"
[    5.993360] type=1400 audit(1304228427.242:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=567 comm="apparmor_parser"
[    5.993565] type=1400 audit(1304228427.242:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=649 comm="apparmor_parser"
[    7.401568] type=1400 audit(1304228428.652:11): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=786 comm="apparmor_parser"
[    7.508185] EMU10K1_Audigy 0000:05:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    7.508247] emu1010: Special config.
[    7.508334] emu1010: EMU_HANA_ID = 0x7f
[    7.508336] emu1010: filename emu/hana.fw testing
[    7.598639] firmware: emu/hana.fw not found. Err = -2
[    7.598643] emu1010: Loading Firmware file emu/hana.fw failed
[    7.603347] EMU10K1_Audigy 0000:05:00.0: PCI INT A disabled
[    7.603363] EMU10K1_Audigy: probe of 0000:05:00.0 failed with error -2
sudo: /etc/init.d/sl-modem-daemon: command not found
    Product Name: System Product Name
    Product Name: P5Q DELUXE
snd_seq_dummy          12798  0 
snd_emu10k1_synth      17244  0 
snd_emux_synth         42834  1 snd_emu10k1_synth
snd_seq_virmidi        13525  1 snd_emux_synth
snd_seq_midi_emul      13706  1 snd_emux_synth
snd_emu10k1           156895  1 snd_emu10k1_synth
snd_ac97_codec        134270  1 snd_emu10k1
ac97_bus               12730  1 snd_ac97_codec
snd_pcm                96625  2 snd_emu10k1,snd_ac97_codec
snd_page_alloc         18529  2 snd_emu10k1,snd_pcm
snd_util_mem           14074  2 snd_emux_synth,snd_emu10k1
snd_hwdep              13604  2 snd_emux_synth,snd_emu10k1
snd_seq_midi           13324  0 
snd_rawmidi            30486  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq_midi_event     14899  2 snd_seq_virmidi,snd_seq_midi
snd_seq                61621  6 snd_seq_dummy,snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_midi,snd_seq_midi_event
snd_timer              29602  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device         14462  6 snd_seq_dummy,snd_emu10k1_synth,snd_emu10k1,snd_seq_midi,snd_rawmidi,snd_seq
snd                    67382  10 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_pcm,snd_hwdep,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
usbhid                 46956  0 
usb_storage            53538  0 
hid                    91020  1 usbhid
aplay: device_list:240: no soundcards found...
  *-multimedia UNCLAIMED  
       description: Multimedia audio controller
       product: SB Audigy
       vendor: Creative Labs
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=64 maxlatency=20 mingnt=2
       resources: ioport:ec00(size=32)

```

Also i i type alsamixer, amixer or anything like this, nothing comes up.

```
If i try jakubholovsky@Jakub-Ubuntu-PC:~$ pavucontrol

(pavucontrol:2503): Gtk-CRITICAL **: IA__gtk_main_quit: assertion `main_loops != NULL' failed
jakubholovsky@Jakub-Ubuntu-PC:~$ gnome-alsamixer
```

I dont know if there is a problem with my integrated sound card that is disabled via bios and havent been enabled for very long time. But if the system sees the card I think there is some hope to get it working(the emu card).

Thank you for any help

---

### Post by Kubatko on 2011-05-01
Seems that here is a problem:
```

[    7.508185] EMU10K1_Audigy 0000:05:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 [    7.508247] emu1010: Special config. [    7.508334] emu1010: EMU_HANA_ID = 0x7f [    7.508336] emu1010: filename emu/hana.fw testing [    7.598639] firmware: emu/hana.fw not found. Err = -2 [    7.598643] emu1010: Loading Firmware file emu/hana.fw failed [    7.603347] EMU10K1_Audigy 0000:05:00.0: PCI INT A disabled [    7.603363] EMU10K1_Audigy: probe of 0000:05:00.0 failed with error -2
```

---

### Post by Kubatko on 2011-05-01
Superb, so after googling the last lines from my most recent post, i found out that there is no firmware loaded, so i downloaded the firmware from alsa, did 

./configure
make
make install

reboot

and now there is the sound, great! 
Thanks for the help Lidex!

Jakub

---

### Post by lidex on 2011-05-01
Nicely done. If all is well, please mark the thread solved using 'Thread Tools' up top.

---

