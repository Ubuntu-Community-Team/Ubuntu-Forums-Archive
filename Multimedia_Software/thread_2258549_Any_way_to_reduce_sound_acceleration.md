---
title: "Any way to reduce sound acceleration?"
date: 2014-12-28
forum: Multimedia Software
---

### Post by fall2 on 2014-12-28
I would like to reduce the acceleration on my sound driver to around 2/5 of full. My sound comes in fine, I want to free up CPU while watching videos. I already got support for my graphics driver. In XP when I reduced my sound acceleration to the second or third notch it made streamed videos preform a little better. Thanks.

My computer details below:
```
computer
    description: Notebook
    product: Gateway 400VTX
    vendor: Gateway
    version: Rev 1
    serial: [REMOVED]
    width: 32 bits
    capabilities: smbios-2.31 dmi-2.31
    configuration: boot=oem-specific chassis=notebook uuid=[REMOVED]
  *-core
       description: Motherboard
       product: Gateway 400VTX
       vendor: Gateway
       physical id: 0
       version: Rev 1.0
     *-firmware
          description: BIOS
          vendor: Gateway
          physical id: 0
          version: 38.00.35
          date: 03/12/2003
          size: 108KiB
          capacity: 448KiB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing escd cdboot int13floppy720 int5printscreen int9keyboard int14serial int17printer acpi usb agp smartbattery biosbootspecification
     *-cpu
          description: CPU
          product: Mobile Intel(R) Celeron(R) CPU 2.20GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.2.7
          slot: uFCPGA2
          size: 2200MHz
          capacity: 3GHz
          width: 32 bits
          clock: 400MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: L1 Cache
             size: 8KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: L2 Cache
             size: 256KiB
             capacity: 512KiB
             capabilities: burst external write-back
     *-memory
          description: System Memory
          physical id: 10
          slot: System board or motherboard
          size: 1GiB
          capacity: 3GiB
        *-bank:0
             description: DIMM SRAM Synchronous 200 MHz (5.0 ns)
             physical id: 0
             slot: DIMM 0
             size: 512MiB
             width: 64 bits
             clock: 200MHz (5.0ns)
        *-bank:1
             description: DIMM SRAM Synchronous 200 MHz (5.0 ns)
             physical id: 1
             slot: DIMM 1
             size: 512MiB
             width: 64 bits
             clock: 200MHz (5.0ns)
     *-pci
          description: Host bridge
          product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 01
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-generic:0 UNCLAIMED
             description: System peripheral
             product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller
             vendor: Intel Corporation
             physical id: 0.1
             bus info: pci@0000:00:00.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: latency=0
        *-generic:1 UNCLAIMED
             description: System peripheral
             product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller
             vendor: Intel Corporation
             physical id: 0.3
             bus info: pci@0000:00:00.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: latency=0
        *-display:0
             description: VGA compatible controller
             product: 82852/855GM Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:11 memory:e8000000-efffffff memory:e0000000-e007ffff ioport:1800(size=8)
        *-display:1 UNCLAIMED
             description: Display controller
             product: 82852/855GM Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:f0000000-f7ffffff memory:e0080000-e00fffff
        *-usb:0
             description: USB controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:11 ioport:1820(size=32)
        *-usb:1
             description: USB controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:11 ioport:1840(size=32)
        *-usb:2
             description: USB controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:10 memory:e0100000-e01003ff
        *-pci
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 83
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:3000(size=4096) memory:e0200000-e02fffff memory:40000000-43ffffff
           *-pcmcia
                description: CardBus bridge
                product: OZ601/6912/711E0 CardBus/SmartCardBus Controller
                vendor: O2 Micro, Inc.
                physical id: 2
                bus info: pci@0000:02:02.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=128
                resources: irq:11 memory:48000000-48000fff ioport:3400(size=256) ioport:3800(size=256) memory:40000000-43ffffff memory:4c000000-4fffffff
           *-network:0 DISABLED
                description: Wireless interface
                product: PRO/Wireless 2915ABG [Calexico2] Network Connection
                vendor: Intel Corporation
                physical id: 4
                bus info: pci@0000:02:04.0
                logical name: eth1
                version: 05
                serial: [REMOVED]
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=64 link=no maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11abg
                resources: irq:11 memory:e0200000-e0200fff
           *-network:1
                description: Ethernet interface
                product: 82801DB PRO/100 VE (MOB) Ethernet Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:02:08.0
                logical name: eth0
                version: 83
                serial: [REMOVED]
                size: 100Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full ip=[REMOVED] latency=66 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100Mbit/s
                resources: irq:11 memory:e0201000-e0201fff ioport:3000(size=64)
        *-isa
             description: ISA bridge
             product: 82801DBM (ICH4-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide
             description: IDE interface
             product: 82801DBM (ICH4-M) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:10 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:1810(size=16) memory:44000000-440003ff
        *-serial UNCLAIMED
             description: SMBus
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:1600(size=32)
        *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_intel8x0 latency=0
             resources: irq:10 ioport:1c00(size=256) ioport:1880(size=64) memory:e0100c00-e0100dff memory:e0100800-e01008ff
        *-communication UNCLAIMED
             description: Modem
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm generic cap_list
             configuration: latency=0
             resources: ioport:2400(size=256) ioport:2000(size=128)
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: FUJITSU MHV2040A
             vendor: Fujitsu
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 0000
             serial: [REMOVED]
             size: 37GiB (40GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=000c4b5b
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: [REMOVED]
                size: 36GiB
                capacity: 36GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2014-12-26 18:33:30 filesystem=ext4 lastmountpoint=/ modified=2014-12-27 09:59:51 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2014-12-27 09:59:51 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 1013MiB
                capacity: 1013MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 1013MiB
                   capabilities: nofs
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD reader
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             capabilities: audio cd-r cd-rw dvd
             configuration: status=nodisc
     *-scsi:2
          physical id: 3
          bus info: usb@1:3
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             product: CardReader CF RW
             vendor: USB2.0
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
             version: 0.0>
             capabilities: removable
             configuration: sectorsize=512
           *-medium
                physical id: 0
                logical name: /dev/sdb
        *-disk:1
             description: SCSI Disk
             product: CardReader Combo
             vendor: USB2.0
             physical id: 0.0.1
             bus info: scsi@2:0.0.1
             logical name: /dev/sdc
             version: 0.0>
             capabilities: removable
             configuration: sectorsize=512
           *-medium
                physical id: 0
                logical name: /dev/sdc

```

---

### Post by Yellow Pasque on 2014-12-29
I'm unsure what you mean by "sound acceleration" unless you're talking about accelerating 3D/positional audio calculations. When playing stereo sound, such as music or video, the sound system is going to use the CPU to mix and posssibly resample the audio. Unless you're unnecessarily resampling the audio or you're willing to give up the ability to play multiple sounds at the same time, there's little you can do to cut down in CPU usage.

Is this system running pulseaudio or not? I can't remember if Lubuntu still uses plain ALSA by default (and you may have installed it as a dependency of something else, so give info if you can: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo) ).

---

### Post by fall2 on 2014-12-29
[IMG]http://community.prometheanplanet.com/cfs-filesystemfile.ashx/__key/CommunityServer-Components-ImageFileViewer/CommunityServer-Discussions-Components-Files-27/5037.HardwareAcceleration.png_2D00_550x0.png[/IMG]
I could not find the exact setup meaning of what the above setup is but thats what I want.
[IMG]http://www.techspot.com/tweaks/metal_gear/index.1.gif[/IMG]
[SIZE=3][SIZE=3]0 Emulation Forces emulation.
--->***1 Basic Disables hardware acceleration of DirectSound secondary buffers.*** <---
2 Standard Enables hardware acceleration of DirectSound secondary buffers but disables vendor-specific property-set extensions.
3 Full Enables hardware acceleration of DirectSound secondary buffers and enables vendor-specific property-set extensions.

[/SIZE][/SIZE]

---

### Post by fall2 on 2014-12-29
> **Temüjin said:**
> 
Is this system running pulseaudio or not? I can't remember if Lubuntu still uses plain ALSA by default (and you may have installed it as a dependency of something else, so give info if you can: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo) ).

I downloaded pulseaudio through a command and removed it through a command.

```

#!/bin/bash

SCRIPT_VERSION=0.4.64
CHANGELOG="http://www.alsa-project.org/alsa-info.sh.changelog"

#################################################################################
#Copyright (C) 2007 Free Software Foundation.

#This program is free software; you can redistribute it and/or modify
#it under the terms of the GNU General Public License as published by
#the Free Software Foundation; either version 2 of the License, or
#(at your option) any later version.

#This program is distributed in the hope that it will be useful,
#but WITHOUT ANY WARRANTY; without even the implied warranty of
#MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#GNU General Public License for more details.

#You should have received a copy of the GNU General Public License
#along with this program; if not, write to the Free Software
#Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA  02110-1301, USA.

##################################################################################

#The script was written for 2 main reasons:
# 1. Remove the need for the devs/helpers to ask several questions before we can easily help the user.
# 2. Allow newer/inexperienced ALSA users to give us all the info we need to help them.

#Set the locale (this may or may not be a good idea.. let me know)
export LC_ALL=C

#Change the PATH variable, so we can run lspci (needed for some distros)
PATH=$PATH:/bin:/sbin:/usr/bin:/usr/sbin
BGTITLE="ALSA-Info v $SCRIPT_VERSION"
PASTEBINKEY="C9cRIO8m/9y8Cs0nVs0FraRx7U0pHsuc"
#Define some simple functions

pbcheck(){
    [[ $UPLOAD = "no" ]] && return

    if [[ -z $PASTEBIN ]]; then
        [[ $(ping -c1 www.alsa-project.org) ]] || KEEP_FILES="yes" UPLOAD="no" PBERROR="yes"
    else
        [[ $(ping -c1 www.pastebin.ca) ]] || KEEP_FILES="yes" UPLOAD="no" PBERROR="yes"
    fi
}

update() {
    SHFILE=`mktemp -t alsa-info.XXXXXXXXXX` || exit 1
    wget -O $SHFILE "http://www.alsa-project.org/alsa-info.sh" >/dev/null 2>&1
    REMOTE_VERSION=`grep SCRIPT_VERSION $SHFILE |head -n1 |sed 's/.*=//'`
    if [ "$REMOTE_VERSION" != "$SCRIPT_VERSION" ]; then
        if [[ -n $DIALOG ]]
        then
            OVERWRITE=
            if [ -w $0 ]; then
                dialog --yesno "Newer version of ALSA-Info has been found\n\nDo you wish to install it?\nNOTICE: The original file $0 will be overwritten!" 0 0
                DIALOG_EXIT_CODE=$?
                if [[ $DIALOG_EXIT_CODE = 0 ]]; then
                  OVERWRITE=yes
                fi
            fi
            if [ -z "$OVERWRITE" ]; then
                dialog --yesno "Newer version of ALSA-Info has been found\n\nDo you wish to download it?" 0 0
                DIALOG_EXIT_CODE=$?
            fi
            if [[ $DIALOG_EXIT_CODE = 0 ]]
            then
                echo "Newer version detected: $REMOTE_VERSION"
                echo "To view the ChangeLog, please visit $CHANGELOG"
                if [ "$OVERWRITE" = "yes" ]; then
                    cp $SHFILE $0
                    echo "ALSA-Info script has been updated to v $REMOTE_VERSION"
                    echo "Please re-run the script"
                    rm $SHFILE 2>/dev/null
                else
                    echo "ALSA-Info script has been downloaded as $SHFILE."
                    echo "Please re-run the script from new location."
                fi
                exit
            else
                rm $SHFILE 2>/dev/null
            fi
        else
            echo "Newer version detected: $REMOTE_VERSION"
            echo "To view the ChangeLog, please visit $CHANGELOG"
            if [ -w $0 ]; then
                echo "The original file $0 will be overwritten!"
                echo -n "If you do not like to proceed, press Ctrl-C now.." ; read inp
                cp $SHFILE $0
                echo "ALSA-Info script has been updated. Please re-run it."
                rm $SHFILE 2>/dev/null
            else
                echo "ALSA-Info script has been downloaded $SHFILE."
                echo "Please, re-run it from new location."
            fi
            exit
        fi
    else
        rm $SHFILE 2>/dev/null
    fi
}

cleanup() {
    if [ -n "$TEMPDIR" -a "$KEEP_FILES" != "yes" ]; then
        rm -rf "$TEMPDIR" 2>/dev/null
    fi
    test -n "$KEEP_OUTPUT" || rm -f "$NFILE"
}


withaplay() {
        echo "!!Aplay/Arecord output" >> $FILE
        echo "!!--------------------" >> $FILE
        echo "" >> $FILE
           echo "APLAY" >> $FILE
    echo "" >> $FILE 
    aplay -l >> $FILE 2>&1
        echo "" >> $FILE
           echo "ARECORD" >> $FILE
    echo "" >> $FILE
    arecord -l >> $FILE 2>&1
    echo "" >> $FILE
}

withlsmod() {
    echo "!!All Loaded Modules" >> $FILE
    echo "!!------------------" >> $FILE
    echo "" >> $FILE
    lsmod |awk {'print $1'} >> $FILE
    echo "" >> $FILE
    echo "" >> $FILE
}

withamixer() {
        echo "!!Amixer output" >> $FILE
        echo "!!-------------" >> $FILE
        echo "" >> $FILE
    for i in `grep "]: " /proc/asound/cards | awk -F ' ' '{ print $1} '` ; do
    CARD_NAME=`grep "^ *$i " $TEMPDIR/alsacards.tmp|awk {'print $2'}`
    echo "!!-------Mixer controls for card $i $CARD_NAME]" >> $FILE
    echo "" >>$FILE
    amixer -c$i info>> $FILE 2>&1
    amixer -c$i>> $FILE 2>&1
        echo "" >> $FILE
    done
    echo "" >> $FILE
}

withalsactl() {
    echo "!!Alsactl output" >> $FILE
        echo "!!--------------" >> $FILE
        echo "" >> $FILE
        exe=""
        if [ -x /usr/sbin/alsactl ]; then
            exe="/usr/sbin/alsactl"
        fi
        if [ -x /usr/local/sbin/alsactl ]; then
            exe="/usr/local/sbin/alsactl"
        fi
        if [ -z "$exe" ]; then
            exe=`whereis alsactl | cut -d ' ' -f 2`
        fi
    $exe -f $TEMPDIR/alsactl.tmp store
    echo "--startcollapse--" >> $FILE
    cat $TEMPDIR/alsactl.tmp >> $FILE
    echo "--endcollapse--" >> $FILE
    echo "" >> $FILE
    echo "" >> $FILE
}

withdevices() {
        echo "!!ALSA Device nodes" >> $FILE
        echo "!!-----------------" >> $FILE
        echo "" >> $FILE
        ls -la /dev/snd/* >> $FILE
        echo "" >> $FILE
        echo "" >> $FILE
}

withconfigs() {
if [[ -e $HOME/.asoundrc ]] || [[ -e /etc/asound.conf ]] || [[ -e $HOME/.asoundrc.asoundconf ]]
then
        echo "!!ALSA configuration files" >> $FILE
        echo "!!------------------------" >> $FILE
        echo "" >> $FILE

        #Check for ~/.asoundrc
        if [[ -e $HOME/.asoundrc ]]
        then
                echo "!!User specific config file (~/.asoundrc)" >> $FILE
                echo "" >> $FILE
                cat $HOME/.asoundrc >> $FILE
                echo "" >> $FILE
                echo "" >> $FILE
        fi
    #Check for .asoundrc.asoundconf (seems to be Ubuntu specific)
    if [[ -e $HOME/.asoundrc.asoundconf ]]
    then
        echo "!!asoundconf-generated config file" >> $FILE
        echo "" >> $FILE
        cat $HOME/.asoundrc.asoundconf >> $FILE
        echo "" >> $FILE
        echo "" >> $FILE
    fi
        #Check for /etc/asound.conf
        if [[ -e /etc/asound.conf ]]
        then
                echo "!!System wide config file (/etc/asound.conf)" >> $FILE
                echo "" >> $FILE
                cat /etc/asound.conf >> $FILE
                echo "" >> $FILE
                echo "" >> $FILE
        fi
fi
}

withsysfs() {
    local i f
    local printed=""
    for i in /sys/class/sound/*; do
    case "$i" in
        */hwC?D?)
        if [ -f $i/init_pin_configs ]; then
            if [ -z "$printed" ]; then
            echo "!!Sysfs Files" >> $FILE
            echo "!!-----------" >> $FILE
            echo "" >> $FILE
            fi
            for f in init_pin_configs driver_pin_configs user_pin_configs init_verbs hints; do
            echo "$i/$f:" >> $FILE
            cat $i/$f >> $FILE
            echo >> $FILE
            done
            printed=yes
        fi
        ;;
        esac
    done
    if [ -n "$printed" ]; then
    echo "" >> $FILE
    fi
}

withdmesg() {
    echo "!!ALSA/HDA dmesg" >> $FILE
    echo "!!--------------" >> $FILE
    echo "" >> $FILE
    dmesg | grep -C1 -E 'ALSA|HDA|HDMI|snd[_-]|sound|hda.codec|hda.intel' >> $FILE
    echo "" >> $FILE
    echo "" >> $FILE
}

withall() {
    withdevices
    withconfigs
    withaplay
    withamixer
    withalsactl
    withlsmod
    withsysfs
    withdmesg
    WITHALL="no"
}

get_alsa_library_version() {
    ALSA_LIB_VERSION=`grep VERSION_STR /usr/include/alsa/version.h 2>/dev/null|awk {'print $3'}|sed 's/"//g'`

    if [ -z "$ALSA_LIB_VERSION" ]; then
        if [ -f /etc/lsb-release ]; then
            . /etc/lsb-release
            case "$DISTRIB_ID" in
                Ubuntu)
                    if which dpkg > /dev/null ; then
                        ALSA_LIB_VERSION=`dpkg -l libasound2 | tail -1 | awk '{print $3}' | cut -f 1 -d -`
                    fi

                    if [ "$ALSA_LIB_VERSION" = "<none>" ]; then
                        ALSA_LIB_VERSION=""
                    fi
                    return
                    ;;
                *)
                    return
                    ;;
            esac
        elif [ -f /etc/debian_version ]; then
            if which dpkg > /dev/null ; then
                ALSA_LIB_VERSION=`dpkg -l libasound2 | tail -1 | awk '{print $3}' | cut -f 1 -d -`
            fi

            if [ "$ALSA_LIB_VERSION" = "<none>" ]; then
                ALSA_LIB_VERSION=""
            fi
            return
        fi
    fi
}


#Run checks to make sure the programs we need are installed.
LSPCI=$(which lspci 2>/dev/null| sed 's|^[^/]*||' 2>/dev/null);
TPUT=$(which tput 2>/dev/null| sed 's|^[^/]*||' 2>/dev/null);
DIALOG=$(which dialog 2>/dev/null | sed 's|^[^/]*||' 2>/dev/null);

#Check to see if sysfs is enabled in the kernel. We'll need this later on
SYSFS=$(mount |grep sysfs|awk {'print $3'});

#Check modprobe config files for sound related options
SNDOPTIONS=$(modprobe -c|sed -n 's/^options \(snd[-_][^ ]*\)/\1:/p')

KEEP_OUTPUT=
NFILE=""

PASTEBIN=""
WWWSERVICE="www.alsa-project.org"
WELCOME="yes"
PROCEED="yes"
UPLOAD="ask"
REPEAT=""
while [ -z "$REPEAT" ]; do
REPEAT="no"
case "$1" in
    --update|--help|--about)
        WELCOME="no"
        PROCEED="no"
        ;;
    --upload)
        UPLOAD="yes"
        WELCOME="no"
        ;;
    --no-upload)
        UPLOAD="no"
        WELCOME="no"
        ;;
    --pastebin)
        PASTEBIN="yes"
        WWWSERVICE="pastebin"
        ;;
    --no-dialog)
        DIALOG=""
        REPEAT=""
        shift
        ;;
    --stdout)
        DIALOG=""
        UPLOAD="no"
        WELCOME="no"
        TOSTDOUT="yes"
        ;;
esac
done


#Script header output.
if [ "$WELCOME" = "yes" ]; then
greeting_message="\

This script visits the following commands/files to collect diagnostic
information about your ALSA installation and sound related hardware.

  dmesg
  lspci
  lsmod
  aplay
  amixer
  alsactl
  /proc/asound/
  /sys/class/sound/
  ~/.asoundrc (etc.)

See '$0 --help' for command line options.
"
if [ -n "$DIALOG" ]; then
    dialog  --backtitle "$BGTITLE" \
        --title "ALSA-Info script v $SCRIPT_VERSION" \
        --msgbox "$greeting_message" 20 80
else
    echo "ALSA Information Script v $SCRIPT_VERSION"
    echo "--------------------------------"
    echo "$greeting_message"
fi # dialog
fi # WELCOME

#Set the output file
TEMPDIR=`mktemp -t -d alsa-info.XXXXXXXXXX` || exit 1
FILE="$TEMPDIR/alsa-info.txt"
if [ -z "$NFILE" ]; then
    NFILE=`mktemp -t alsa-info.txt.XXXXXXXXXX` || exit 1
fi

trap cleanup 0

if [ "$PROCEED" = "yes" ]; then

if [ -z "$LSPCI" ]; then
    if [ -d /sys/bus/pci ]; then
        echo "This script requires lspci. Please install it, and re-run this script."
        exit 0
    fi
fi

#Fetch the info and store in temp files/variables
DISTRO=`grep -ihs "buntu\|SUSE\|Fedora\|PCLinuxOS\|MEPIS\|Mandriva\|Debian\|Damn\|Sabayon\|Slackware\|KNOPPIX\|Gentoo\|Zenwalk\|Mint\|Kubuntu\|FreeBSD\|Puppy\|Freespire\|Vector\|Dreamlinux\|CentOS\|Arch\|Xandros\|Elive\|SLAX\|Red\|BSD\|KANOTIX\|Nexenta\|Foresight\|GeeXboX\|Frugalware\|64\|SystemRescue\|Novell\|Solaris\|BackTrack\|KateOS\|Pardus" /etc/{issue,*release,*version}`
KERNEL_VERSION=`uname -r`
KERNEL_PROCESSOR=`uname -p`
KERNEL_MACHINE=`uname -m`
KERNEL_OS=`uname -o`
[[ `uname -v | grep SMP`  ]] && KERNEL_SMP="Yes" || KERNEL_SMP="No" 
ALSA_DRIVER_VERSION=`cat /proc/asound/version |head -n1|awk {'print $7'} |sed 's/\.$//'`
get_alsa_library_version
ALSA_UTILS_VERSION=`amixer -v |awk {'print $3'}`
LAST_CARD=$((`grep "]: " /proc/asound/cards | wc -l` - 1 ))

ESDINST=$(which esd 2>/dev/null| sed 's|^[^/]*||' 2>/dev/null)
PAINST=$(which pulseaudio 2>/dev/null| sed 's|^[^/]*||' 2>/dev/null)
ARTSINST=$(which artsd 2>/dev/null| sed 's|^[^/]*||' 2>/dev/null)
JACKINST=$(which jackd 2>/dev/null| sed 's|^[^/]*||' 2>/dev/null)
ROARINST=$(which roard 2>/dev/null| sed 's|^[^/]*||' 2>/dev/null)
DMIDECODE=$(which dmidecode 2>/dev/null| sed 's|^[^/]*||' 2>/dev/null)

#Check for DMI data
if [ -d /sys/class/dmi/id ]; then
    # No root privileges are required when using sysfs method
    DMI_SYSTEM_MANUFACTURER=$(cat /sys/class/dmi/id/sys_vendor 2>/dev/null)
    DMI_SYSTEM_PRODUCT_NAME=$(cat /sys/class/dmi/id/product_name 2>/dev/null)
    DMI_SYSTEM_PRODUCT_VERSION=$(cat /sys/class/dmi/id/product_version 2>/dev/null)
    DMI_SYSTEM_FIRMWARE_VERSION=$(cat /sys/class/dmi/id/bios_version 2>/dev/null)
elif [ -x $DMIDECODE ]; then
    DMI_SYSTEM_MANUFACTURER=$($DMIDECODE -s system-manufacturer 2>/dev/null)
    DMI_SYSTEM_PRODUCT_NAME=$($DMIDECODE -s system-product-name 2>/dev/null)
    DMI_SYSTEM_PRODUCT_VERSION=$($DMIDECODE -s system-version 2>/dev/null)
    DMI_SYSTEM_FIRMWARE_VERSION=$($DMIDECODE -s bios-version 2>/dev/null)
fi

cat /proc/asound/modules 2>/dev/null|awk {'print $2'}>$TEMPDIR/alsamodules.tmp
cat /proc/asound/cards >$TEMPDIR/alsacards.tmp
if [[ ! -z "$LSPCI" ]]; then
lspci |grep -i "multi\|audio">$TEMPDIR/lspci.tmp
fi

#Check for HDA-Intel cards codec#*
cat /proc/asound/card*/codec\#* > $TEMPDIR/alsa-hda-intel.tmp 2> /dev/null

#Check for AC97 cards codec
cat /proc/asound/card*/codec97\#0/ac97\#0-0 > $TEMPDIR/alsa-ac97.tmp 2> /dev/null
cat /proc/asound/card*/codec97\#0/ac97\#0-0+regs > $TEMPDIR/alsa-ac97-regs.tmp 2> /dev/null

#Check for USB mixer setup
cat /proc/asound/card*/usbmixer > $TEMPDIR/alsa-usbmixer.tmp 2> /dev/null

#Fetch the info, and put it in $FILE in a nice readable format.
if [[ -z $PASTEBIN ]]; then
echo "upload=true&script=true&cardinfo=" > $FILE
else
echo "name=$USER&type=33&description=/tmp/alsa-info.txt&expiry=&s=Submit+Post&content=" > $FILE
fi
echo "!!################################" >> $FILE
echo "!!ALSA Information Script v $SCRIPT_VERSION" >> $FILE
echo "!!################################" >> $FILE
echo "" >> $FILE
echo "!!Script ran on: `LANG=C TZ=UTC date`" >> $FILE
echo "" >> $FILE
echo "" >> $FILE
echo "!!Linux Distribution" >> $FILE
echo "!!------------------" >> $FILE
echo "" >> $FILE
echo $DISTRO >> $FILE
echo "" >> $FILE
echo "" >> $FILE
echo "!!DMI Information" >> $FILE
echo "!!---------------" >> $FILE
echo "" >> $FILE
echo "Manufacturer:      $DMI_SYSTEM_MANUFACTURER" >> $FILE
echo "Product Name:      $DMI_SYSTEM_PRODUCT_NAME" >> $FILE
echo "Product Version:   $DMI_SYSTEM_PRODUCT_VERSION" >> $FILE
echo "Firmware Version:  $DMI_SYSTEM_FIRMWARE_VERSION" >> $FILE
echo "" >> $FILE
echo "" >> $FILE
echo "!!Kernel Information" >> $FILE
echo "!!------------------" >> $FILE
echo "" >> $FILE
echo "Kernel release:    $KERNEL_VERSION" >> $FILE
echo "Operating System:  $KERNEL_OS" >> $FILE
echo "Architecture:      $KERNEL_MACHINE" >> $FILE
echo "Processor:         $KERNEL_PROCESSOR" >> $FILE
echo "SMP Enabled:       $KERNEL_SMP" >> $FILE
echo "" >> $FILE
echo "" >> $FILE
echo "!!ALSA Version" >> $FILE
echo "!!------------" >> $FILE
echo "" >> $FILE
echo "Driver version:     $ALSA_DRIVER_VERSION" >> $FILE
echo "Library version:    $ALSA_LIB_VERSION" >> $FILE
echo "Utilities version:  $ALSA_UTILS_VERSION" >> $FILE
echo "" >> $FILE
echo "" >> $FILE
echo "!!Loaded ALSA modules" >> $FILE
echo "!!-------------------" >> $FILE
echo "" >> $FILE
cat $TEMPDIR/alsamodules.tmp >> $FILE
echo "" >> $FILE
echo "" >> $FILE
echo "!!Sound Servers on this system" >> $FILE
echo "!!----------------------------" >> $FILE
echo "" >> $FILE
if [[ -n $PAINST ]];then
[[ `pgrep '^(.*/)?pulseaudio$'` ]] && PARUNNING="Yes" || PARUNNING="No"
echo "Pulseaudio:" >> $FILE
echo "      Installed - Yes ($PAINST)" >> $FILE
echo "      Running - $PARUNNING" >> $FILE
echo "" >> $FILE
fi
if [[ -n $ESDINST ]];then
[[ `pgrep '^(.*/)?esd$'` ]] && ESDRUNNING="Yes" || ESDRUNNING="No"
echo "ESound Daemon:" >> $FILE
echo "      Installed - Yes ($ESDINST)" >> $FILE
echo "      Running - $ESDRUNNING" >> $FILE
echo "" >> $FILE
fi
if [[ -n $ARTSINST ]];then
[[ `pgrep '^(.*/)?artsd$'` ]] && ARTSRUNNING="Yes" || ARTSRUNNING="No"
echo "aRts:" >> $FILE
echo "      Installed - Yes ($ARTSINST)" >> $FILE
echo "      Running - $ARTSRUNNING" >> $FILE
echo "" >> $FILE
fi
if [[ -n $JACKINST ]];then
[[ `pgrep '^(.*/)?jackd$'` ]] && JACKRUNNING="Yes" || JACKRUNNING="No"
echo "Jack:" >> $FILE
echo "      Installed - Yes ($JACKINST)" >> $FILE
echo "      Running - $JACKRUNNING" >> $FILE
echo "" >> $FILE
fi
if [[ -n $ROARINST ]];then
[[ `pgrep '^(.*/)?roard$'` ]] && ROARRUNNING="Yes" || ROARRUNNING="No"
echo "RoarAudio:" >> $FILE
echo "      Installed - Yes ($ROARINST)" >> $FILE
echo "      Running - $ROARRUNNING" >> $FILE
echo "" >> $FILE
fi
if [[ -z "$PAINST" && -z "$ESDINST" && -z "$ARTSINST" && -z "$JACKINST" && -z "$ROARINST" ]];then
echo "No sound servers found." >> $FILE
echo "" >> $FILE
fi
echo "" >> $FILE
echo "!!Soundcards recognised by ALSA" >> $FILE
echo "!!-----------------------------" >> $FILE
echo "" >> $FILE
cat $TEMPDIR/alsacards.tmp >> $FILE
echo "" >> $FILE
echo "" >> $FILE

if [[ ! -z "$LSPCI" ]]; then
echo "!!PCI Soundcards installed in the system" >> $FILE
echo "!!--------------------------------------" >> $FILE
echo "" >> $FILE
cat $TEMPDIR/lspci.tmp >> $FILE
echo "" >> $FILE
echo "" >> $FILE
echo "!!Advanced information - PCI Vendor/Device/Subsystem ID's" >> $FILE
echo "!!-------------------------------------------------------" >> $FILE
echo "" >> $FILE
lspci -vvn |grep -A1 040[1-3] >> $FILE
echo "" >> $FILE
echo "" >> $FILE
fi

if [ "$SNDOPTIONS" ]
then
echo "!!Modprobe options (Sound related)" >> $FILE
echo "!!--------------------------------" >> $FILE
echo "" >> $FILE
modprobe -c|sed -n 's/^options \(snd[-_][^ ]*\)/\1:/p' >> $FILE
echo "" >> $FILE
echo "" >> $FILE
fi

if [ -d "$SYSFS" ]
then
echo "!!Loaded sound module options" >> $FILE
echo "!!---------------------------" >> $FILE
echo "" >> $FILE
for mod in `cat /proc/asound/modules|awk {'print $2'}`;do
echo "!!Module: $mod" >> $FILE
for params in `echo $SYSFS/module/$mod/parameters/*`; do
    echo -ne "\t";
    echo "$params : `cat $params`" | sed 's:.*/::';
done >> $FILE
echo "" >> $FILE
done
echo "" >> $FILE
fi

if [ -s "$TEMPDIR/alsa-hda-intel.tmp" ]; then
    echo "!!HDA-Intel Codec information" >> $FILE
    echo "!!---------------------------" >> $FILE
    echo "--startcollapse--" >> $FILE
    echo "" >> $FILE
    cat $TEMPDIR/alsa-hda-intel.tmp >> $FILE
    echo "--endcollapse--" >> $FILE
    echo "" >> $FILE
    echo "" >> $FILE
fi

if [ -s "$TEMPDIR/alsa-ac97.tmp" ]; then
        echo "!!AC97 Codec information" >> $FILE
        echo "!!----------------------" >> $FILE
        echo "--startcollapse--" >> $FILE
        echo "" >> $FILE
        cat $TEMPDIR/alsa-ac97.tmp >> $FILE
        echo "" >> $FILE
        cat $TEMPDIR/alsa-ac97-regs.tmp >> $FILE
        echo "--endcollapse--" >> $FILE
    echo "" >> $FILE
    echo "" >> $FILE
fi

if [ -s "$TEMPDIR/alsa-usbmixer.tmp" ]; then
        echo "!!USB Mixer information" >> $FILE
        echo "!!---------------------" >> $FILE
        echo "--startcollapse--" >> $FILE
        echo "" >> $FILE
        cat $TEMPDIR/alsa-usbmixer.tmp >> $FILE
        echo "--endcollapse--" >> $FILE
    echo "" >> $FILE
    echo "" >> $FILE
fi

#If no command line options are specified, then run as though --with-all was specified
if [ -z "$1" ]; then
    update
    pbcheck    
fi

fi # proceed

#loop through command line arguments, until none are left.
if [ -n "$1" ]; then
    until [ -z "$1" ]
    do
    case "$1" in
        --pastebin)
                update
                pbcheck
            ;;
        --update)
            update
            exit
            ;;
        --upload)
            UPLOAD="yes"
            ;;
        --no-upload)
            UPLOAD="no"
            ;;
        --output)
            shift
            NFILE="$1"
            KEEP_OUTPUT="yes"
            ;;
        --debug)
            echo "Debugging enabled. $FILE and $TEMPDIR will not be deleted"
            KEEP_FILES="yes"
            echo ""
            ;;
        --with-all)
            withall
            ;;
        --with-aplay)
            withaplay
            WITHALL="no"
            ;;
        --with-amixer)
            withamixer
            WITHALL="no"
            ;;
        --with-alsactl)
            withalsactl
            WITHALL="no"
            ;;
        --with-devices)
            withdevices
            WITHALL="no"
            ;;
        --with-dmesg)
            withdmesg
            WITHALL="no"
            ;;
        --with-configs)
            WITHALL="no"
            if [[ -e $HOME/.asoundrc ]] || [[ -e /etc/asound.conf ]]
            then
                echo "!!ALSA configuration files" >> $FILE
                echo "!!------------------------" >> $FILE
                echo "" >> $FILE

                #Check for ~/.asoundrc
                if [[ -e $HOME/.asoundrc ]]
                then
                    echo "!!User specific config file ($HOME/.asoundrc)" >> $FILE
                    echo "" >> $FILE
                    cat $HOME/.asoundrc >> $FILE
                    echo "" >> $FILE
                    echo "" >> $FILE
                fi

                #Check for /etc/asound.conf
                if [[ -e /etc/asound.conf ]]
                then
                    echo "!!System wide config file (/etc/asound.conf)" >> $FILE
                    echo "" >> $FILE
                    cat /etc/asound.conf >> $FILE
                    echo "" >> $FILE
                    echo "" >> $FILE
                fi
            fi
            ;;
        --stdout)
            UPLOAD="no"
            if [ -z "$WITHALL" ]; then
                withall
            fi
            cat $FILE
            rm $FILE
            ;;
        --about)
            echo "Written/Tested by the following users of #alsa on irc.freenode.net:"
            echo ""
            echo "    wishie - Script author and developer / Testing"
            echo "    crimsun - Various script ideas / Testing"
            echo "    gnubien - Various script ideas / Testing"
            echo "    GrueMaster - HDA Intel specific items / Testing"
            echo "    olegfink - Script update function"
            echo "  TheMuso - display to stdout functionality"
            exit 0
            ;;
        *)
            echo "alsa-info.sh version $SCRIPT_VERSION"
            echo ""
            echo "Available options:"
            echo "    --with-aplay (includes the output of aplay -l)"
            echo "    --with-amixer (includes the output of amixer)"
            echo "    --with-alsactl (includes the output of alsactl)"
            echo "    --with-configs (includes the output of ~/.asoundrc and"
            echo "        /etc/asound.conf if they exist)" 
            echo "    --with-devices (shows the device nodes in /dev/snd/)"
            echo "    --with-dmesg (shows the ALSA/HDA kernel messages)"
            echo ""
            echo "    --output FILE (specify the file to output for no-upload mode)"
            echo "    --update (check server for script updates)"
            echo "    --upload (upload contents to remote server)"
            echo "    --no-upload (do not upload contents to remote server)"
            echo "    --pastebin (use http://pastebin.ca) as remote server"
            echo "        instead www.alsa-project.org"
            echo "    --stdout (print alsa information to standard output"
            echo "        instead of a file)"
            echo "    --about (show some information about the script)"
            echo "    --debug (will run the script as normal, but will not"
            echo "         delete $FILE)"
            exit 0
            ;;
    esac
    shift 1
    done
fi

if [ "$PROCEED" = "no" ]; then
    exit 1
fi

if [ -z "$WITHALL" ]; then
    withall
fi

if [ "$UPLOAD" = "ask" ]; then
    if [ -n "$DIALOG" ]; then
        dialog --backtitle "$BGTITLE" --title "Information collected" --yes-label " UPLOAD / SHARE " --no-label " SAVE LOCALLY " --defaultno --yesno "\n\nAutomatically upload ALSA information to $WWWSERVICE?" 10 80
        DIALOG_EXIT_CODE=$?
        if [ $DIALOG_EXIT_CODE != 0 ]; then
            UPLOAD="no"
        else
            UPLOAD="yes"
        fi
    else
        echo -n "Automatically upload ALSA information to $WWWSERVICE? [y/N] : "
        read -e CONFIRM
        if [ "$CONFIRM" != "y" ]; then
            UPLOAD="no"
        else
            UPLOAD="yes"
        fi
    fi

fi

if [ "$UPLOAD" = "no" ]; then

    if [ -z "$TOSTDOUT" ]; then
        mv -f $FILE $NFILE || exit 1
        KEEP_OUTPUT="yes"
    fi

    if [[ -n $DIALOG ]]
    then
        if [[ -n $PBERROR ]]; then
            dialog --backtitle "$BGTITLE" --title "Information collected" --msgbox "An error occurred while contacting the $WWWSERVICE.\n Your information was NOT automatically uploaded.\n\nYour ALSA information is in $NFILE" 10 100
        else
            dialog --backtitle "$BGTITLE" --title "Information collected" --msgbox "\n\nYour ALSA information is in $NFILE" 10 60
        fi
    else
        echo

        if [[ -n $PBERROR ]]; then
            echo "An error occurred while contacting the $WWWSERVICE."
            echo "Your information was NOT automatically uploaded."
            echo ""
            echo "Your ALSA information is in $NFILE"
            echo ""
        else
            if [ -z "$TOSTDOUT" ]; then
                echo ""
                echo "Your ALSA information is in $NFILE"
                echo ""
            fi
        fi
    fi

    exit

fi # UPLOAD

#Test that wget is installed, and supports --post-file. Upload $FILE if it does, and prompt user to upload file if it doesnt. 
if
WGET=$(which wget 2>/dev/null| sed 's|^[^/]*||' 2>/dev/null); [[ -n "${WGET}" ]] && [[ -x "${WGET}" ]] && [[ `wget --help |grep post-file` ]]
then

if [[ -n $DIALOG ]]
then

if [[ -z $PASTEBIN ]]; then
    wget -O - --tries=5 --timeout=60 --post-file=$FILE "http://www.alsa-project.org/cardinfo-db/" &>$TEMPDIR/wget.tmp || echo "Upload failed; exit"
    { for i in 10 20 30 40 50 60 70 80 90; do
        echo $i
        sleep 0.2
    done
    echo; } |dialog --backtitle "$BGTITLE" --guage "Uploading information to www.alsa-project.org ..." 6 70 0
else
    wget -O - --tries=5 --timeout=60 --post-file=$FILE "http://pastebin.ca/quiet-paste.php?api=$PASTEBINKEY&encrypt=t&encryptpw=blahblah" &>$TEMPDIR/wget.tmp || echo "Upload failed; exit"
    { for i in 10 20 30 40 50 60 70 80 90; do
        echo $i
        sleep 0.2
    done
    echo; } |dialog --backtitle "$BGTITLE" --guage "Uploading information to www.pastebin.ca ..." 6 70 0
fi

dialog --backtitle "$BGTITLE" --title "Information uploaded" --yesno "Would you like to see the uploaded information?" 5 100 
DIALOG_EXIT_CODE=$?
if [ $DIALOG_EXIT_CODE = 0 ]; then
    grep -v "alsa-info.txt" $FILE >$TEMPDIR/uploaded.txt
    dialog --backtitle "$BGTITLE" --textbox $TEMPDIR/uploaded.txt 0 0
fi

clear

# no dialog
else

if [[ -z $PASTEBIN ]]; then
    echo -n "Uploading information to www.alsa-project.org ... " 
    wget -O - --tries=5 --timeout=60 --post-file=$FILE http://www.alsa-project.org/cardinfo-db/ &>$TEMPDIR/wget.tmp &
else
    echo -n "Uploading information to www.pastebin.ca ... " 
    wget -O - --tries=5 --timeout=60 --post-file=$FILE http://pastebin.ca/quiet-paste.php?api=$PASTEBINKEY &>$TEMPDIR/wget.tmp &
fi

#Progess spinner for wget transfer.
i=1
sp="/-\|"
echo -n ' '
while pgrep wget &>/dev/null
do
    echo -en "\b${sp:i++%${#sp}:1}"
done

echo -e "\b Done!"
echo ""

fi #dialog

#See if tput is available, and use it if it is.    
if [ -n "$TPUT" ]; then
    if [[ -z $PASTEBIN ]]; then
        FINAL_URL=`tput setaf 1; grep "SUCCESS:" $TEMPDIR/wget.tmp | cut -d ' ' -f 2 ; tput sgr0`
    else
        FINAL_URL=`tput setaf 1; grep "SUCCESS:" $TEMPDIR/wget.tmp | sed -n 's/.*\:\([0-9]\+\).*/http:\/\/pastebin.ca\/\1/p';tput sgr0`
    fi
else
    if [[ -z $PASTEBIN ]]; then
        FINAL_URL=`grep "SUCCESS:" $TEMPDIR/wget.tmp | cut -d ' ' -f 2`
    else
        FINAL_URL=`grep "SUCCESS:" $TEMPDIR/wget.tmp | sed -n 's/.*\:\([0-9]\+\).*/http:\/\/pastebin.ca\/\1/p'`
    fi
fi

# Output the URL of the uploaded file.    
echo "Your ALSA information is located at $FINAL_URL"
echo "Please inform the person helping you."
echo ""

# We couldnt find a suitable wget, so tell the user to upload manually.
else
    mv -f $FILE $NFILE || exit 1
    KEEP_OUTPUT="yes"
    if [[ -z $DIALOG ]]
    then
        if [[ -z $PASTEBIN ]]; then
        echo ""
        echo "Could not automatically upload output to http://www.alsa-project.org"
        echo "Possible reasons are:"
        echo "    1. Couldnt find 'wget' in your PATH"
        echo "    2. Your version of wget is less than 1.8.2"
        echo ""
        echo "Please manually upload $NFILE to http://www.alsa-project.org/cardinfo-db/ and submit your post."
        echo ""
        else
        echo ""
        echo "Could not automatically upload output to http://www.pastebin.ca"
        echo "Possible reasons are:"
        echo "    1. Couldnt find 'wget' in your PATH"
        echo "    2. Your version of wget is less than 1.8.2"
        echo ""
        echo "Please manually upload $NFILE to http://www.pastebin.ca/upload.php and submit your post."
        echo ""
        fi
    else
        if [[ -z $PASTEBIN ]]; then
            dialog --backtitle "$BGTITLE" --msgbox "Could not automatically upload output to http://www.alsa-project.org.\nPossible reasons are:\n\n    1. Couldn't find 'wget' in your PATH\n    2. Your version of wget is less than 1.8.2\n\nPlease manually upload $NFILE to http://www.alsa-project,org/cardinfo-db/ and submit your post." 25 100
        else
            dialog --backtitle "$BGTITLE" --msgbox "Could not automatically upload output to http://www.pastebin.ca.\nPossible reasons are:\n\n    1. Couldn't find 'wget' in your PATH\n    2. Your version of wget is less than 1.8.2\n\nPlease manually upload $NFILE to http://www.pastebin.ca/upload.php and submit your post." 25 100
        fi
    fi
fi

```

---

### Post by Rob Sayer on 2014-12-29
I'm not familiar with that audio hardware feature, and I don't think it's there in linux.  I just did a quick search on "ubuntu audio hardware acceleration" and got many pages on video accel but nothing on audio.  I suspect in windows it's just a kludgy way of working around bugs in DirectX etc.

As mentioned it's probably better to make sure your video playback is optimized.  SOme players are faster than others.  You didn't mention which programs you're using.  But certain settings can make a big difference, depending on your hardware.

---

### Post by fall2 on 2014-12-29
Its mainly for adobe flash in Lubuntu 14.04, my guess is buffering is the same thing as mixing but Is says "secondary buffers". I have put in a /etc/X11/xorg.conf file for graphics. I'm willing to try anything that could reduce the workload while streaming online videos. If there is a audio program that has less intensive CPU or if I can cut/edit one of the audio/video files commands without noticing a change in flash video stream lets try.

---

### Post by fall2 on 2014-12-29
pulse audio is in my task manager, so I guess I have it.

---

### Post by Yellow Pasque on 2014-12-29
```
gksu leafpad /etc/pulse/daemon.conf
```

If you're primarily interested in playing video, I would change the default-sample-rate to 48000 because that's what most videos use. Optionally, you can enable alternate-sample-rate=44100 if you don't want your music getting resampled. The other setting you may want to look at changing is resample-method to resample-method=trivial for lowest CPU usage.
Remember that you have to remove the leading ';' from a line to uncomment/activate it. After you make changes, you can save the file, exit leafpad and restart pulseaudio:
```
pulseaudio -k
```

---

### Post by Yellow Pasque on 2014-12-29
As for the Windows setting, I don't think there's an equivalent in Linux. It also doesn't make sense why turning down DirectSound buffer acceleration would use less CPU, unless you have a poor audio device/driver.

---

### Post by fall2 on 2014-12-29
Just because I'm a little confused this is the file.

```

# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify
# it under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307
# USA.

## Configuration file for the PulseAudio daemon. See pulse-daemon.conf(5) for
## more information. Default values are commented out.  Use either ; or # for
## commenting.

; daemonize = no
; fail = yes
; allow-module-loading = yes
; allow-exit = yes
; use-pid-file = yes
; system-instance = no
; local-server-type = user
; enable-shm = yes
; shm-size-bytes = 0 # setting this 0 will use the system-default, usually 64 MiB
; lock-memory = no
; cpu-limit = no

; high-priority = yes
; nice-level = -11

; realtime-scheduling = yes
; realtime-priority = 5

; exit-idle-time = 20
; scache-idle-time = 20

; dl-search-path = (depends on architecture)

; load-default-script-file = yes
; default-script-file = /etc/pulse/default.pa

; log-target = auto
; log-level = notice
; log-meta = no
; log-time = no
; log-backtrace = 0

resample-method = speex-float-1
; enable-remixing = yes
; enable-lfe-remixing = no

flat-volumes = no

; rlimit-fsize = -1
; rlimit-data = -1
; rlimit-stack = -1
; rlimit-core = -1
; rlimit-as = -1
; rlimit-rss = -1
; rlimit-nproc = -1
; rlimit-nofile = 256
; rlimit-memlock = -1
; rlimit-locks = -1
; rlimit-sigpending = -1
; rlimit-msgqueue = -1
; rlimit-nice = 31
; rlimit-rtprio = 9
; rlimit-rttime = 1000000

; default-sample-format = s16le
; default-sample-rate = 44100
; alternate-sample-rate = 48000
; default-sample-channels = 2
; default-channel-map = front-left,front-right

default-fragments = 8
default-fragment-size-msec = 10

; enable-deferred-volume = yes
deferred-volume-safety-margin-usec = 1
; deferred-volume-extra-delay-usec = 0 
```


and is this how it should look?

```

# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify
# it under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307
# USA.

## Configuration file for the PulseAudio daemon. See pulse-daemon.conf(5) for
## more information. Default values are commented out.  Use either ; or # for
## commenting.

; daemonize = no
; fail = yes
; allow-module-loading = yes
; allow-exit = yes
; use-pid-file = yes
; system-instance = no
; local-server-type = user
; enable-shm = yes
; shm-size-bytes = 0 # setting this 0 will use the system-default, usually 64 MiB
; lock-memory = no
; cpu-limit = no

; high-priority = yes
; nice-level = -11

; realtime-scheduling = yes
; realtime-priority = 5

; exit-idle-time = 20
; scache-idle-time = 20

; dl-search-path = (depends on architecture)

; load-default-script-file = yes
; default-script-file = /etc/pulse/default.pa

; log-target = auto
; log-level = notice
; log-meta = no
; log-time = no
; log-backtrace = 0

resample-method = trivial
; enable-remixing = yes
; enable-lfe-remixing = no

flat-volumes = no

; rlimit-fsize = -1
; rlimit-data = -1
; rlimit-stack = -1
; rlimit-core = -1
; rlimit-as = -1
; rlimit-rss = -1
; rlimit-nproc = -1
; rlimit-nofile = 256
; rlimit-memlock = -1
; rlimit-locks = -1
; rlimit-sigpending = -1
; rlimit-msgqueue = -1
; rlimit-nice = 31
; rlimit-rtprio = 9
; rlimit-rttime = 1000000

; default-sample-format = s16le
; default-sample-rate = 48000
; alternate-sample-rate = 44100
; default-sample-channels = 2
; default-channel-map = front-left,front-right

default-fragments = 8
default-fragment-size-msec = 10

; enable-deferred-volume = yes
deferred-volume-safety-margin-usec = 1
; deferred-volume-extra-delay-usec = 0

```

Then save it. I'm a little unsure what "Remember that you have to remove the leading ';' from a line to uncomment/activate it." is. So ; means not active and nothing means active. I have to delete the ; before the default-sample-rate and alternate-sample-rate or those are not active?

---

### Post by Yellow Pasque on 2014-12-29
> So ; means not active and nothing means active. I have to delete the ; before the default-sample-rate and alternate-sample-rate or those are not active? 

Correct and correct. The ';' indicates a comment (either text that's meant for a human reading the code or in this case, examples of potential settings).

---

### Post by fall2 on 2014-12-29
Well any way I saved the file and ran a couple tests on a 2:42 youtube video in 480p that I have been using for months now on my old XP OS and my new OS. The first run was 973 frames lost and the second was 575 frames lost. 575 is the best I ever had in my new OS(around 40 frames better than my best old time). Some times the frames lost gets close to 1000 because I think background processes are working. In any case, still sounds good and I didn't loose anything.

---

### Post by fall2 on 2014-12-29
deleted the ; and I didn't notice any change. I got a 581, 592 and 573 frames lost but both well below what I used to get.

---

### Post by fall2 on 2014-12-30
I gained 15-20 frames per minute in a 480p video.

---

