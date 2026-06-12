---
title: "No sound on Sony Vaio"
date: 2010-12-30
forum: Multimedia Software
---

### Post by joetheplumber67 on 2010-12-30
Hey everyone,

I just installed Ubuntu on my Sony Vaio VPCEB23FM. However, when I tried to watch videos, there was no sound coming out. I went to [http://ubuntuforums.org/showthread.php?t=1467628](http://ubuntuforums.org/showthread.php?t=1467628) and tried out the link in post #5, but that completely got rid of my sound card and I no longer have any version of ALSA.

```

[anurag@Anurag-Vaio:~$ aplay -l
aplay: device_list:223: no soundcards found...
anurag@Anurag-Vaio:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
	Subsystem: Sony Corporation Device 9071
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
	Subsystem: Sony Corporation Device 9071
	Flags: bus master, fast devsel, latency 0, IRQ 36
	Memory at f0000000 (64-bit, non-prefetchable) [size=4M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at e080 [size=8]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
	Subsystem: Sony Corporation Device 9071
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at f600a000 (64-bit, non-prefetchable) [size=16]
	Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05) (prog-if 20)
	Subsystem: Sony Corporation Device 9071
	Flags: bus master, medium devsel, latency 0, IRQ 16
	Memory at f6008000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
	Subsystem: Sony Corporation Device 9071
	Flags: bus master, fast devsel, latency 0, IRQ 5
	Memory at f6000000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: f4c00000-f5ffffff
	Prefetchable memory behind bridge: 00000000f6100000-00000000f62fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: f3800000-f4bfffff
	Prefetchable memory behind bridge: 00000000f6300000-00000000f64fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: f2400000-f37fffff
	Prefetchable memory behind bridge: 00000000f6500000-00000000f66fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 05)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=0c, sec-latency=0
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: f0400000-f23fffff
	Prefetchable memory behind bridge: 00000000f6700000-00000000f68fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05) (prog-if 20)
	Subsystem: Sony Corporation Device 9071
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at f6007000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0d, subordinate=0d, sec-latency=32
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
	Subsystem: Sony Corporation Device 9071
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05) (prog-if 01)
	Subsystem: Sony Corporation Device 9071
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 33
	I/O ports at e070 [size=8]
	I/O ports at e060 [size=4]
	I/O ports at e050 [size=8]
	I/O ports at e040 [size=4]
	I/O ports at e020 [size=32]
	Memory at f6006000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
	Subsystem: Sony Corporation Device 9071
	Flags: medium devsel, IRQ 4
	Memory at f6005000 (64-bit, non-prefetchable) [size=256]
	I/O ports at e000 [size=32]
	Kernel modules: i2c-i801

00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
	Subsystem: Sony Corporation Device 9071
	Flags: bus master, fast devsel, latency 0, IRQ 4
	Memory at f6004000 (64-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

02:00.0 Network controller: Intel Corporation WiFi Link 6000 Series (rev 35)
	Subsystem: Intel Corporation Device 1301
	Flags: bus master, fast devsel, latency 0, IRQ 35
	Memory at f4c00000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: iwlagn
	Kernel modules: iwlagn

03:00.0 SD Host controller: Ricoh Co Ltd Device e822
	Subsystem: Sony Corporation Device 9071
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at f3802000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

03:00.1 System peripheral: Ricoh Co Ltd Device e230
	Subsystem: Sony Corporation Device 9071
	Flags: bus master, fast devsel, latency 0, IRQ 4
	Memory at f3801000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

03:00.4 SD Host controller: Ricoh Co Ltd Device e822
	Subsystem: Sony Corporation Device 9071
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at f3800000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

04:00.0 Ethernet controller: Marvell Technology Group Ltd. Device 4381 (rev 11)
	Subsystem: Sony Corporation Device 9071
	Flags: bus master, fast devsel, latency 0, IRQ 34
	Memory at f2420000 (64-bit, non-prefetchable) [size=16K]
	I/O ports at b000 [size=256]
	Expansion ROM at f2400000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: sky2
	Kernel modules: sky2

3f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
	Subsystem: Sony Corporation Device 9071
	Flags: bus master, fast devsel, latency 0

3f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
	Subsystem: Sony Corporation Device 9071
	Flags: bus master, fast devsel, latency 0

3f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
	Subsystem: Sony Corporation Device 9071
	Flags: bus master, fast devsel, latency 0

3f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
	Subsystem: Sony Corporation Device 9071
	Flags: bus master, fast devsel, latency 0

3f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
	Subsystem: Sony Corporation Device 9071
	Flags: bus master, fast devsel, latency 0

3f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
	Subsystem: Sony Corporation Device 9071
	Flags: bus master, fast devsel, latency 0

anurag@Anurag-Vaio:~$ cat /proc/asound/version
cat: /proc/asound/version: No such file or directory

```

These are the results when I try to find my sound card and which version of ALSA I have. It doesn't make sense because the sound works fine when I boot into Windows 7.

---

### Post by lidex on 2010-12-30
Try this to re-install alsa:
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```
Next reboot and run the alsa-info script. 
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by joetheplumber67 on 2010-12-30
```
anurag@Anurag-Vaio:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
anurag@Anurag-Vaio:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.
anurag@Anurag-Vaio:~$ wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh
--2010-12-30 23:21:20--  http://www.alsa-project.org/alsa-info.sh
Resolving www.alsa-project.org... 77.48.224.243
Connecting to www.alsa-project.org|77.48.224.243|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh [following]
--2010-12-30 23:21:23--  http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh
Resolving git.alsa-project.org... 77.48.224.243
Reusing existing connection to www.alsa-project.org:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/plain]
Saving to: `alsa-info.sh'

    [  <=>                                  ] 27,026      69.2K/s   in 0.4s    

2010-12-30 23:21:27 (69.2 KB/s) - `alsa-info.sh' saved [27026]

WARNING: All config files need .conf: /etc/modprobe.d/also-base.conf.save, it will be ignored in a future release.
WARNING: Failed to open config file also-base.conf.save: Permission denied
ALSA Information Script v 0.4.59
--------------------------------

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

See 'alsa-info.sh --help' for command line options.

WARNING: All config files need .conf: /etc/modprobe.d/also-base.conf.save, it will be ignored in a future release.
WARNING: Failed to open config file also-base.conf.save: Permission denied

Automatically upload ALSA information to www.alsa-project.org? [y/N] : 


Your ALSA information is in /tmp/alsa-info.txt.iT1agrxJVi

```

Should I upload the "/tmp/alsa-info.txt.iT1agrxJVi"?

Also, if that is right, then where would I find it?

---

### Post by joetheplumber67 on 2010-12-30
Also, is the "permission denied" a problem? If so, how do I get around it?

---

### Post by joetheplumber67 on 2010-12-30
I think I found the alsa-text file, but I'm not sure.

The file is too big to upload, so I'm just putting it in code.

```
#!/bin/bash

SCRIPT_VERSION=0.4.59
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
        echo "!!------------" >> $FILE
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
        echo "!!-------------" >> $FILE
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
		    for f in init_pin_configs driver_pin_configs user_pin_configs init_verbs; do
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
	echo "!!------------------" >> $FILE
	echo "" >> $FILE
	dmesg | grep -C1 -E 'ALSA|HDA|HDMI|sound|hda.codec|hda.intel' >> $FILE
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
if [[ -n "$DIALOG" ]]; then
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

if [[ -z "$LSPCI" ]] 
then
	echo "This script requires lspci. Please install it, and re-run this script."
	exit 0
fi

#Fetch the info and store in temp files/variables
DISTRO=`grep -ihs "buntu\|SUSE\|Fedora\|PCLinuxOS\|MEPIS\|Mandriva\|Debian\|Damn\|Sabayon\|Slackware\|KNOPPIX\|Gentoo\|Zenwalk\|Mint\|Kubuntu\|FreeBSD\|Puppy\|Freespire\|Vector\|Dreamlinux\|CentOS\|Arch\|Xandros\|Elive\|SLAX\|Red\|BSD\|KANOTIX\|Nexenta\|Foresight\|GeeXboX\|Frugalware\|64\|SystemRescue\|Novell\|Solaris\|BackTrack\|KateOS\|Pardus" /etc/{issue,*release,*version}`
KERNEL_VERSION=`uname -r`
KERNEL_PROCESSOR=`uname -p`
KERNEL_MACHINE=`uname -m`
KERNEL_OS=`uname -o`
[[ `uname -v |grep SMP`  ]] && KERNEL_SMP="Yes" || KERNEL_SMP="No" 
ALSA_DRIVER_VERSION=`cat /proc/asound/version |head -n1|awk {'print $7'} |sed 's/\.$//'`
get_alsa_library_version
ALSA_UTILS_VERSION=`amixer -v |awk {'print $3'}`
VENDOR_ID=`lspci -vn |grep 040[1-3] | awk -F':' '{print $3}'|awk {'print substr($0, 2);}' >$TEMPDIR/vendor_id.tmp`
DEVICE_ID=`lspci -vn |grep 040[1-3] | awk -F':' '{print $4}'|awk {'print $1'} >$TEMPDIR/device_id.tmp`
LAST_CARD=$((`grep "]: " /proc/asound/cards | wc -l` - 1 ))

ESDINST=$(which esd 2>/dev/null| sed 's|^[^/]*||' 2>/dev/null)
PAINST=$(which pulseaudio 2>/dev/null| sed 's|^[^/]*||' 2>/dev/null)
ARTSINST=$(which artsd 2>/dev/null| sed 's|^[^/]*||' 2>/dev/null)
JACKINST=$(which jackd 2>/dev/null| sed 's|^[^/]*||' 2>/dev/null)
DMIDECODE=$(which dmidecode 2>/dev/null| sed 's|^[^/]*||' 2>/dev/null)

#Check for DMI data
if [ -d /sys/class/dmi/id ]; then
    # No root privileges are required when using sysfs method
    DMI_SYSTEM_MANUFACTURER=$(cat /sys/class/dmi/id/sys_vendor 2>/dev/null)
    DMI_SYSTEM_PRODUCT_NAME=$(cat /sys/class/dmi/id/product_name 2>/dev/null)
elif [ -x $DMIDECODE ]; then
    DMI_SYSTEM_MANUFACTURER=$($DMIDECODE -s system-manufacturer 2>/dev/null)
    DMI_SYSTEM_PRODUCT_NAME=$($DMIDECODE -s system-product-name 2>/dev/null)
fi

cat /proc/asound/modules 2>/dev/null|awk {'print $2'}>$TEMPDIR/alsamodules.tmp
cat /proc/asound/cards >$TEMPDIR/alsacards.tmp
lspci |grep -i "multi\|audio">$TEMPDIR/lspci.tmp

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
if [[ -z "$PAINST" && -z "$ESDINST" && -z "$ARTSINST" && -z "$JACKINST" ]];then
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
echo "!!PCI Soundcards installed in the system" >> $FILE
echo "!!--------------------------------------" >> $FILE
echo "" >> $FILE
cat $TEMPDIR/lspci.tmp >> $FILE
echo "" >> $FILE
echo "" >> $FILE
echo "!!Advanced information - PCI Vendor/Device/Susbsystem ID's" >> $FILE
echo "!!--------------------------------------------------------" >> $FILE
echo "" >> $FILE
lspci -vvn |grep -A1 040[1-3] >> $FILE
echo "" >> $FILE
echo "" >> $FILE

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
echo "!!--------------------------" >> $FILE
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

if [ -s "$TEMPDIR/alsa-hda-intel.tmp" ] 
then
	echo "!!HDA-Intel Codec information" >> $FILE
	echo "!!---------------------------" >> $FILE
	echo "--startcollapse--" >> $FILE
	echo "" >> $FILE
	cat $TEMPDIR/alsa-hda-intel.tmp >> $FILE
	echo "--endcollapse--" >> $FILE
	echo "" >> $FILE
	echo "" >> $FILE
fi

if [ -s "$TEMPDIR/alsa-ac97.tmp" ]
then
        echo "!!AC97 Codec information" >> $FILE
        echo "!!---------------------------" >> $FILE
        echo "--startcollapse--" >> $FILE
        echo "" >> $FILE
        cat $TEMPDIR/alsa-ac97.tmp >> $FILE
        echo "" >> $FILE
        cat $TEMPDIR/alsa-ac97-regs.tmp >> $FILE
        echo "--endcollapse--" >> $FILE
	echo "" >> $FILE
	echo "" >> $FILE
fi

if [ -s "$TEMPDIR/alsa-usbmixer.tmp" ]
then
        echo "!!USB Mixer information" >> $FILE
        echo "!!---------------------------" >> $FILE
        echo "--startcollapse--" >> $FILE
        echo "" >> $FILE
        cat $TEMPDIR/alsa-usbmixer.tmp >> $FILE
        echo "--endcollapse--" >> $FILE
	echo "" >> $FILE
	echo "" >> $FILE
fi

#If no command line options are specified, then run as though --with-all was specified
if [[ -z "$1" ]]
then
	update
	withall
	pbcheck	
fi

fi # proceed

#loop through command line arguments, until none are left.
if [[ -n "$1" ]]
then
	until [ -z "$1" ]
	do
	case "$1" in
		--pastebin)
		        update
			withall
        		pbcheck
			;;
		--update)
			update
			exit
			;;
		--upload)
			UPLOAD="yes"
			withall
			;;
		--no-upload)
			UPLOAD="no"
			withall
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
			withall
			;;
		--with-all)
			withall
			;;
		--with-aplay)
			withaplay
			;;
		--with-amixer)
			withamixer
			;;
		--with-alsactl)
			withalsactl
			;;
		--with-devices)
			withdevices
			;;
		--with-dmesg)
			withdmesg
			;;
		--with-configs)
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
			withall
			cat $FILE
			rm $FILE
			;;
		--about)
			echo "Written/Tested by the following users of #alsa on irc.freenode.net:"
			echo ""
			echo "	wishie - Script author and developer / Testing"
			echo "	crimsun - Various script ideas / Testing"
			echo "	gnubien - Various script ideas / Testing"
			echo "	GrueMaster - HDA Intel specific items / Testing"
			echo "	olegfink - Script update function"
			echo "  TheMuso - display to stdout functionality"
			exit 0
			;;
		*)
			echo "alsa-info.sh version $SCRIPT_VERSION"
			echo ""
			echo "Available options:"
			echo "	--with-aplay (includes the output of aplay -l)"
			echo "	--with-amixer (includes the output of amixer)"
			echo "	--with-alsactl (includes the output of alsactl)"
			echo "	--with-configs (includes the output of ~/.asoundrc and"
			echo "	    /etc/asound.conf if they exist)" 
			echo "	--with-devices (shows the device nodes in /dev/snd/)"
			echo "	--with-dmesg (shows the ALSA/HDA kernel messages)"
			echo ""
			echo "	--output FILE (specify the file to output for no-upload mode)"
			echo "	--update (check server for script updates)"
			echo "	--upload (upload contents to remote server)"
			echo "	--no-upload (do not upload contents to remote server)"
			echo "	--pastebin (use http://pastebin.ca) as remote server"
			echo "	    instead www.alsa-project.org"
			echo "	--stdout (print alsa information to standard output"
			echo "	    instead of a file)"
			echo "	--about (show some information about the script)"
			echo "	--debug (will run the script as normal, but will not"
			echo "	     delete $FILE)"
			exit 0
			;;
	esac
	shift 1
	done
fi

if [ "$PROCEED" = "no" ]; then
	exit 1
fi

if [ "$UPLOAD" = "ask" ]; then
	if [[ -n "$DIALOG" ]]; then
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
if [[ -n "$TPUT" ]]
then
	if [[ -z $PASTEBIN ]]; then
		FINAL_URL=`tput setaf 1; grep "SUCCESS:" $TEMPDIR/wget.tmp | cut -d ' ' -f 2 ; tput sgr0`
	else
		FINAL_URL=`tput setaf 1; grep "SUCCESS:" $TEMPDIR/wget.tmp |sed -n 's/.*\:\([0-9]\+\).*/http:\/\/pastebin.ca\/\1/p';tput sgr0`
	fi
else
	if [[ -z $PASTEBIN ]]; then
		FINAL_URL=`grep "SUCCESS:" $TEMPDIR/wget.tmp | cut -d ' ' -f 2`
	else
		FINAL_URL=`grep "SUCCESS:" $TEMPDIR/wget.tmp |sed -n 's/.*\:\([0-9]\+\).*/http:\/\/pastebin.ca\/\1/p'`
	fi
fi

#Output the URL of the uploaded file.	
echo "Your ALSA information is located at $FINAL_URL"
echo "Please inform the person helping you."
echo ""

#We couldnt find a suitable wget, so tell the user to upload manually.
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

### Post by lidex on 2010-12-31
Probably easier just to run it again. This time when it comes to this point:
```
Automatically upload ALSA information to www.alsa-project.org? [y/N] : 
```
key in the letter y and press enter. The terminal will then provide the url of your uploaded file.

---

### Post by joetheplumber67 on 2010-12-31
[http://www.alsa-project.org/db/?f=50ba758362207cc50643684d15b768c6ecebc284](http://www.alsa-project.org/db/?f=50ba758362207cc50643684d15b768c6ecebc284)

---

### Post by joetheplumber67 on 2010-12-31
Do I need to upgrade to ALSA 1.0.23? Right now I have 1.0.21

```


anurag@Anurag-Vaio:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.


```

---

### Post by lidex on 2010-12-31
Something weird with your alsa install. If you have installed alsa backports, uninstall it. Make sure your kernel is up to date:
```
sudo apt-get update
sudo apt-get upgrade
sudo update-grub
```
Reboot.
Now open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=auto 
```
Save. Close.
Now reset alsa.
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```
**Reboot.**

---

### Post by joetheplumber67 on 2010-12-31
how can I check if I have alsa-backports installed?

---

### Post by lidex on 2010-12-31
In a terminal:
```
dpkg -l | grep "alsa"
```

---

### Post by joetheplumber67 on 2010-12-31
I did that and it still didn't work.

---

### Post by lidex on 2010-12-31
Can you run the alsa info script again?

---

### Post by joetheplumber67 on 2010-12-31
I have Alsa 1.0.21, but it doesn't recognize any sound cards. 
```

anurag@anurag-vaio:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.

anurag@anurag-vaio:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
    Subsystem: Sony Corporation Device 9071
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
    Subsystem: Sony Corporation Device 9071
    Flags: bus master, fast devsel, latency 0, IRQ 36
    Memory at f0000000 (64-bit, non-prefetchable) [size=4M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at e080 [size=8]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
    Subsystem: Sony Corporation Device 9071
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at f600a000 (64-bit, non-prefetchable) [size=16]
    Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05) (prog-if 20)
    Subsystem: Sony Corporation Device 9071
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at f6008000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
    Subsystem: Sony Corporation Device 9071
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at f6000000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: f4c00000-f5ffffff
    Prefetchable memory behind bridge: 00000000f6100000-00000000f62fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: f3800000-f4bfffff
    Prefetchable memory behind bridge: 00000000f6300000-00000000f64fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 0000b000-0000bfff
    Memory behind bridge: f2400000-f37fffff
    Prefetchable memory behind bridge: 00000000f6500000-00000000f66fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 05)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=0c, sec-latency=0
    I/O behind bridge: 0000a000-0000afff
    Memory behind bridge: f0400000-f23fffff
    Prefetchable memory behind bridge: 00000000f6700000-00000000f68fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05) (prog-if 20)
    Subsystem: Sony Corporation Device 9071
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at f6007000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5) (prog-if 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=0d, subordinate=0d, sec-latency=32
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
    Subsystem: Sony Corporation Device 9071
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05) (prog-if 01)
    Subsystem: Sony Corporation Device 9071
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 34
    I/O ports at e070 [size=8]
    I/O ports at e060 [size=4]
    I/O ports at e050 [size=8]
    I/O ports at e040 [size=4]
    I/O ports at e020 [size=32]
    Memory at f6006000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
    Subsystem: Sony Corporation Device 9071
    Flags: medium devsel, IRQ 4
    Memory at f6005000 (64-bit, non-prefetchable) [size=256]
    I/O ports at e000 [size=32]
    Kernel modules: i2c-i801

00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
    Subsystem: Sony Corporation Device 9071
    Flags: bus master, fast devsel, latency 0, IRQ 4
    Memory at f6004000 (64-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>

02:00.0 Network controller: Intel Corporation WiFi Link 6000 Series (rev 35)
    Subsystem: Intel Corporation Device 1301
    Flags: bus master, fast devsel, latency 0, IRQ 35
    Memory at f4c00000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: iwlagn
    Kernel modules: iwlagn

03:00.0 SD Host controller: Ricoh Co Ltd Device e822
    Subsystem: Sony Corporation Device 9071
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at f3802000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci

03:00.1 System peripheral: Ricoh Co Ltd Device e230
    Subsystem: Sony Corporation Device 9071
    Flags: bus master, fast devsel, latency 0, IRQ 4
    Memory at f3801000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>

03:00.4 SD Host controller: Ricoh Co Ltd Device e822
    Subsystem: Sony Corporation Device 9071
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at f3800000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci

04:00.0 Ethernet controller: Marvell Technology Group Ltd. Device 4381 (rev 11)
    Subsystem: Sony Corporation Device 9071
    Flags: bus master, fast devsel, latency 0, IRQ 33
    Memory at f2420000 (64-bit, non-prefetchable) [size=16K]
    I/O ports at b000 [size=256]
    Expansion ROM at f2400000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: sky2
    Kernel modules: sky2

3f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
    Subsystem: Sony Corporation Device 9071
    Flags: bus master, fast devsel, latency 0

3f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
    Subsystem: Sony Corporation Device 9071
    Flags: bus master, fast devsel, latency 0

3f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
    Subsystem: Sony Corporation Device 9071
    Flags: bus master, fast devsel, latency 0

3f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
    Subsystem: Sony Corporation Device 9071
    Flags: bus master, fast devsel, latency 0

3f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
    Subsystem: Sony Corporation Device 9071
    Flags: bus master, fast devsel, latency 0

3f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
    Subsystem: Sony Corporation Device 9071
    Flags: bus master, fast devsel, latency 0

anurag@anurag-vaio:~$ aplay -l
aplay: device_list:223: no soundcards found...

```The alsa info script is at [http://www.alsa-project.org/db/?f=1de153ceade49137c26826a57fe03b76f6057611](http://www.alsa-project.org/db/?f=1de153ceade49137c26826a57fe03b76f6057611)

Also, would upgrading to 1.0.23 possibly work?

---

### Post by lidex on 2011-01-01
> **joetheplumber67 said:**
> I have Alsa 1.0.21, but it doesn't recognize any sound cards. 
[/CODE]The alsa info script is at [http://www.alsa-project.org/db/?f=1de153ceade49137c26826a57fe03b76f6057611](http://www.alsa-project.org/db/?f=1de153ceade49137c26826a57fe03b76f6057611)
Also, would upgrading to 1.0.23 possibly work?
Yeah, that's next. Follow the link in my sig.

---

### Post by joetheplumber67 on 2011-01-01
How do I get the script?

---

### Post by lidex on 2011-01-01
> **joetheplumber67 said:**
> How do I get the script?

If you click the link in my sig and read through the initial post it explains the procedure there.

---

### Post by joetheplumber67 on 2011-01-05
It worked!

Thank you very much!!!

---

