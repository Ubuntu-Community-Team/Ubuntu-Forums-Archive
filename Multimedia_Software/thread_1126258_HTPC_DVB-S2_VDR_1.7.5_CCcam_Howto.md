---
title: "HTPC DVB-S2 VDR 1.7.5 CCcam Howto"
date: 2009-04-15
forum: Multimedia Software
---

### Post by art2003 on 2009-04-15
**_LATEST NEWS:_** 

[Here ]("http://www.ziddu.com/download/18475717/vdr_1.7.21.rar.html")you can download vdr-1.7.21 sources with common plugins already patched to work with vdr-1.7.21. It is ready for 64 bits.

I still use Ubuntu 10.04 on my desktop, but for a dedicated HTPC if you can get it working, Archlinux will yield better performance.

So I've rebuilt my system with exactly the same hardware but using a recent Archlinux 64bits installation cd and the results are impressive:

a) Just X server running, no Gnome or KDE which makes it very fast and responsive
b) Zap time is less than a second
c) BBC HD for example works perfectly 
d) CCcam 2.1.4 working fine (this would also be true if you installed for example ubuntu 10.04)
e) [ Aesthetically very slick]("http://mymediasystem.org/") as TV, Videos, DVD are all more integrated 
f) Rock-solid stable
g) Hard drive usage: 2.7GB
h) Archlinux is a rolling release, so no need to reinstall in order to upgrade EVER
i) I've built a 32bits (Pentium 4 or celeron) and a 64bits (Any 64bits AMD or Intel cpus) release
j) For XMBC user the xvdr addon and matching vdr plugin xvdr

I've abandoned oxine because it is basically a dead project, a serious bug was reported back in January and no effort has been made to fix it.
So I am using MMS (My media system) exclusively as a frontend as I discovered the Game menu can be used to launch bash scripts.

**_Contact me if you would like a dvd or download link_** of a restore image with [vdr 1.7.15]("http://www.tvdr.de/"), [mms]("http://mymediasystem.org/") and CCcam 2.1.4 fully working (if your DVB card is supported by linux all you would need to do is setup your remote if it is not the one used in this tutorial or an Opera DVB USB)

This image would need to be installed on the first partition of your hard drive (/dev/sda1) or alternatively modify /etc/fstab to account for the different location.


Note: If you have Ubuntu 8.x or 9x the latest CCcam version that will work is: CCcam 2.1.2 

FOREWORD: This tutorial is for Ubuntu 8.10 
It should work with Ubuntu 8.04 but with Ubuntu 9.04 or 9.10 you may face problems (for example the skinenigma plugin will fail to compile although if you use the one on my binaries should be fine)
If you are running ubuntu 9.10 then you might want to make your life easier by simply adding these 2 repositories:
(thanks to hotzenplotz5 (see page 19 of this thread)
You can find there: vdr-1.7.9 + plugins (120) + xine-vdpau etc

[https://launchpad.net/~hotzenplotz5/+archive/ppa](https://launchpad.net/~hotzenplotz5/+archive/ppa)
```

deb http://ppa.launchpad.net/hotzenplotz5/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/hotzenplotz5/ppa/ubuntu karmic main

```


The background.
I had a Dreambox 7020 and was happy enough with it but one day HD finally came in the horizon.
I looked at a Dreambox 800, ipbox revo, and a couple of other linux based HD sat receivers. None was satisfying.
So I set out to build my own. If this tutorial intimidates you or time is precios to you, drop me a private message and I can send you a bootable restore dvd that is all up and running.

The goal of this howto is to build a functional HTPC with HD satellite tv and HDMI output at 1080p (1920×1080 	16:9). The idea is for a dedicated machine. We assume a brand-new installation and given the complexity of the tutorial the reasonable way to undo all the changes is to reinstall Ubuntu.
VDR 1.7.10 ([see screenshots]("http://www.kuba4u.de/vdr/pics/page_01.htm")) is the heart of this project (thanks to Klaus.Schmidinger for his tremendous work and for his patience answering my questions, thanks to Shalafi for his own tutorial and for moderating an excellent satellite forum, and to Winfried for his channels scanning and rotor coding for VDR)

If you rather use VDR 1.7.0 then see my other thread


```

NOTICE: By popular demand I have placed vdr-1.7.9 with the extensions patch,
 setup, teletext, subtitles and other usefull plugins together with most of 
the config files in this tutorial in a .rar file 
[DOWNLOAD IT HERE]("http://www.ziddu.com/download/6526879/vdr-1.7.9PLUSconfig.rar.html")
You still need to setup ffmpeg, xine-lib, xine-ui and the oxine binaries 
but the rest should be working fine and save lots of time and efforts.


```


The hardware I chose:
- Motherboard: Abit A-N78HD with the Geforce 8200 IGP
 or ASUS M3N78-VM AM2 (both work fine with OSS but the Abit can not do HDMI sound with ALSA)
- CPU : AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
- Thermalite silent fan
- Memory : 2 GB DDR2-800 (2X 1 GB)
- DVD-drive : LG GGC-H20LRB (DVD-RW, Blu-Ray and HDDVD)
- Harddisk : 160GB
- Budgetcard : Hauppauge WinTV NOVA-HD-S2 

All this, is connected to a Panasonic FullHD LCD-TV using the onboard HDMI connector with the nvidia closed sources driver 180.53

VDR has many plugins, some more frequently maintained than others. 
The exact set of plugins you use is up to you and your needs.
This is my current set of VDR plugins:
 [DOWNLOAD HERE]("http://www.ziddu.com/download/6518674/vdr-1.7.9-art2003.rar.html") my /usr/local/src/vdr-1.7.9 with all the plugins and patches listed below:	(just do sudo make install )

vdr (1.7.10/1.7.10) - The Video Disk Recorder
femon (1.7.4) - DVB Signal Information Monitor (OSD)
osdteletext (0.8.3) - Displays teletext on the OSD
pluginsetup (0.0.6) - Plugin Setup
timeline (1.0.141-kw001) - Show timer overview and collisions
imdbsearch (0.3.6) - Searches the IMDb
skinenigmang (0.1.0) - EnigmaNG skin
quickepgsearch (0.0.1) - Quick search for broadcasts
satlist (0.0.2) - Channel list for satellite sorting
premiereepg (0.2.0) - Parses extended Premiere EPG data
epgsearchonly (0.0.1) - Direct access to epgsearch's search menu
systeminfo (0.1.1) - Display various system informations
control (0.0.2a-kw3) - Control VDR over terminal or telnet
epgsearch (0.9.25.beta13) - search the EPG for repeats and more
mplayer (0.10.1) - Media replay via MPlayer
conflictcheckonly (0.0.1) - Direct access to epgsearch's conflict check menu
osdadjust (0.0.3) - Adjust OSD Size and Position
setup (0.3.1-zulu-edition) - VDR-Setup Extension
chanman (0.0.8) - Channel manager plugin
wirbelscan (0.0.5-pre08) - DVB and pvrinput channel scan for VDR
ttxtsubs (0.1.0) - Teletext subtitles
sc (1.0.0pre-HG-85fce21e5440+) - A software emulated CAM
skinreel (0.0.1) - Reel Skin-Plugin
xine (0.9.3) - Software based playback using xine


**1. The Sound of Music: [ALSA]("http://ubuntuforums.org/showthread.php?p=6589810") or OSS**
[I]Note: I use OSS as with ALSA couldn't get sound over HDMI.
 Current OSS as of 2th July 2009 is OSS 4.1-1052 [/I]

You need to edit /etc/modprobe.d/blacklist-local and blacklist nv and nvidia-new drivers to avoid conflicts in the next step. If you have decided to install OSS then you need to blacklist snd_hda_intel as well

sudo gedit /etc/modprobe.d/blacklist-local 
```
# It is mandatory to blacklist nvidia_new and nv to avoid conflicts
blacklist nvidia_new
blacklist nv
# If you are going to use OSS instead of ALSA also blacklist snd_hda_intel
blacklist snd_hda_intel


```


**2. NVIDIA drivers**
NVIDIA drivers as of 180.50 or earlier do not work with this motherboard (I have tried the beta 185.18.10 driver and it did not work for me but 185.18.08 works)
If somebody can confirm they make a difference please let me know version and motherboard you have.

Instead [download NVIDIA 177.82]("http://www.nvidia.com/object/linux_display_ia32_177.82.html") and install it.  Reboot and you should have 1080p resolution

Note: If you want VDPAU accelearation and your NVIDIA card supports it (8xxx or 9xxx series) then you can install
[NVIDIA 185.18.10]("ftp://download.nvidia.com/XFree86/Linux-x86/185.18.10/NVIDIA-Linux-x86-185.18.10-pkg1.run") instead

**3.  [ALSA]("http://ubuntuforums.org/showthread.php?t=1046137&highlight=vdr+dvb") OR [OSS]("http://ubuntuforums.org/showthread.php?p=6881221#post6881221")**


To the best of my knowledge if you want the audio output through the HDMI connector straight to your TV you will need to install OSS and disable ALSA.
But this is not without problems as OSS will work for 6 months and will require reinstallation every 6 months (unless you purchase a licence from them)
So if you want audio over HDMI install OSS, otherwise stick with ALSA for simplicity

Installing OSS:

We go to the oss website and download oss:

[http://www.opensound.com/download.cgi](http://www.opensound.com/download.cgi)

We choose linux 2.6 - deb - x86

```

sudo apt-get install linux-headers-generic linux-source build-essential
sudo dpkg -i oss-linux-4.2-2002_i386.deb
sudo soundon
osstest
ossinfo -x
ossxmix -dX

```

Once you have followed the above guide to install OSS modify /usr/lib/oss/soundon.user
so it looks like this:

```

sudo rm /usr/lib/oss/soundon.user
sudo touch /usr/lib/oss/soundon.user
sudo chmod 755 /usr/lib/oss/soundon.user
sudo gedit /usr/lib/oss/soundon.user


```


```
#!/bin/sh
# For HDMI sound output on motherboards with chipset ALC883 or ALC888 
# This script can be used to run programs every time OSS is started.
# By default, this script is disabled, and contains no commands.
# To enable, add executable permissions to this file, and edit below
# commands to be run. 
rm /dev/dsp
ln -s /dev/oss/oss_hdaudio0/spdout1 /dev/dsp
#vmixctl attach /dev/oss/oss_hdaudio0/spdout1 /dev/oss/oss_hdaudio0/pcmin0 

rm /dev/dsp dsp_ac3
ln -s /dev/oss/oss_hdaudio0/spdout1 /dev/dsp_ac3


exit 0


```


Click on System, Preferences, Sound and select OSS all over.
Reboot and you should have 1920x1080 with audio over HDMI by default

**or ALSA**:

To upgrade to the latest ALSA drivers do the following:

```
sudo -s
cd /usr/local/src
touch alsaupg.sh
chmod +x alsaupg.sh
sudo gedit alsaupg.sh

```

copy and paste the following text, save the file

```

#!/bin/bash 
#
# AlsaUpgrade-1.0.x-rev-1.X.sh 
# Note: As usual  I'd like to recommend that you make a backup of your drive first. I don't guarantee for anything!
#  Rev: 1.16  01-21-2009 soundcheck Changelog: added kernel-headers compile option to alsa-driver/ support of 1.0.19
#  Rev: 1.17  05-10-2009 soundcheck Changelog: Added 1.0.20 support, added 2.6.29 support

##--------------------------------------------------------------------------------------------------------------------------------------
# Below package variables need to be adapted according to available package ids at  http://www.alsa-project.org/main/index.php/Download 
# otherwise the script execution will fail!
##--------------------------------------------------------------------------------------------------------------------------------------

PACKAGE=1.0.20

alsa1020 () {
DRIVER=alsa-driver-1.0.20
FIRMWARE=alsa-firmware-1.0.20
LIB=alsa-lib-1.0.20
PLUGINS=alsa-plugins-1.0.20
UTILS=alsa-utils-1.0.20
TOOLS=alsa-tools-1.0.20
OSS=alsa-oss-1.0.17
}


#------------Ususally NO Changes to be done below this line-----------------------------------------------------------------------------------------

# script revision
REV="1.17"

#----supported kernels-----------------------------------------------------------------------------------------------------------------

KERNEL1="2.6.24" # Ubuntu kernel family
KERNEL2="2.6.26" # kernel family
KERNEL3="2.6.27" # kernel family
KERNEL4="2.6.28" # kernel family
KERNEL5="2.6.29" # kernel family

#TOOLSRC =" ac3dec as10k1 envy24control hdsploader hdspconf hdspmixer \
#	  mixartloader pcxhrloader rmedigicontrol sb16_csp seq sscape_ctl \
#	  us428control usx2yloader vxloader echomixer ld10k1 qlo10k1"
#


SRCDIR=/usr/src          # Sources will be stored here
ALSASRCDIR=${SRCDIR}/alsa  # Packages will be stored here
NOW=`date '+%m%d%y-%H.%M'`
DATE=`date`
LOGFILE=/var/log/AlsaUpgradeRev-$REV-$NOW.log
KERNEL=`uname -r` 
CURRENTPACKAGE=`cat /proc/asound/version | awk '{ print $7 }'`
ALSAPACKS=" alsa-base  alsa-oss  alsa-utils alsa-tools alsa-tools-gui libasound2 libasound2-dev libasound2-plugins aconnectgui "
KERNELPACKS=" `dpkg -l |  awk '{print $2}' | grep -e ${KERNEL}` "



#---------------------------------------------------------------------------------------------------------------------------------

#---You need to have root permissions to run the script----

if [ "$UID" -ne 0  ]
 then
 echo "Must be root to run this script..."
 exit 0
fi  

package () {
echo -n "Choose Alsa Package (1) $PACKAGE default[1]: " 
   read PACK
   case $PACK in
       		""  	) alsa1020 ;;
       		[1]     ) alsa1020 ;;
       		*	) alsa1020 ;;
esac

ALSASRCDIR=${SRCDIR}/Alsa-${PACKAGE}

}


header () {
echo
echo "-------------------------------------------------------------"
echo "-  ${1}"
echo "-------------------------------------------------------------"
echo

}

die () {
  echo "$1"
  exit 1 #error
}

greet () {
clear
echo
echo "--$DATE----Alsa-Upgrade-Script-$REV -----------------" 
echo "-  "
echo "- You'll be upgraded from $CURRENTPACKAGE to $PACKAGE. "
echo "- "
echo "- All script output is routed to $LOGFILE" 
echo "- Run tail -f <logfile> in a seperate terminal to follow the upgrade"
echo "- "
echo "- Reboot your machine afterwards."
echo "- "
echo "- Enjoy - meet you at ubuntuforums.org or diy-audio.com"
echo "- soundcheck"
echo "---------------------------------------------------------------------------"
echo
echo "Upgrade in progress..The process can take up to 15minutes.....Be patient!"

}


bye () {
header "Installation successfully finished!"
header "Your new ALSA version will be loaded after the next reboot..."

}

prep () {

header "Working on following Alsa packages..."
echo "Driver: $DRIVER"
echo "Library: $LIB"
echo "Plugins: $PLUGINS"
echo "Utils: $UTILS"
echo "Firmware: $FIRMWARE"
echo "OSS: $OSS"
#echo "Installing tools: $TOOLS"

#install necessary Linux packages
header "Installing packages required to build ALSA..."

apt-get install -y $ALSAPACKS
apt-get install -y build-essential libsysfs-dev libncurses5-dev gettext python-all-dev xmlto libpulse-dev libspeex-dev
apt-get install -y libavcodec-dev libavformat-dev libavutil-dev libmpeg4ip-dev liba52-0.7.4-dev
apt-get install -y linux-headers-$KERNEL  

}

download () {

cd $SRCDIR

header "Downloading and extracting ALSA packages..."
wget ftp://ftp.alsa-project.org/pub/driver/$DRIVER.tar.bz2 && tar -xjf $DRIVER.tar.bz2 
wget ftp://ftp.alsa-project.org/pub/firmware/$FIRMWARE.tar.bz2 && tar -xjf $FIRMWARE.tar.bz2 
wget ftp://ftp.alsa-project.org/pub/lib/$LIB.tar.bz2 && tar -xjf $LIB.tar.bz2 
wget ftp://ftp.alsa-project.org/pub/plugins/$PLUGINS.tar.bz2 && tar -xvf $PLUGINS.tar.bz2 
wget ftp://ftp.alsa-project.org/pub/utils/$UTILS.tar.bz2 && tar -xjf $UTILS.tar.bz2 
wget ftp://ftp.alsa-project.org/pub/tools/$TOOLS.tar.bz2 && tar -xjf $TOOLS.tar.bz2 
wget ftp://ftp.alsa-project.org/pub/oss-lib/$OSS.tar.bz2 && tar -xvf $OSS.tar.bz2 

rm alsa*.tar.bz2
rm -rf $ALSASRCDIR
mkdir -p $ALSASRCDIR && mv alsa-* $ALSASRCDIR

}


compile () {

header "Prepare for compilation and installation..."

test -d $ALSASRCDIR || die "$ALSASRCDIR not found"

cd $ALSASRCDIR

test -d $DRIVER || die "$DRIVER  not found"
test -d $FIRMWARE || die "$FIRMWARE not found"
test -d $LIB || die "$LIB not found"
test -d $PLUGINS || die "$PLUGINS not found"
test -d $UTILS || die "$UTILS not found" 
test -d $TOOLS || die "$TOOLS not found"
test -d $OSS || die "$OSS not found"


#alsa-driver Note: Driver to be installed before library
header "Compiling drivers..."
cd $ALSASRCDIR/$DRIVER
make clean
./configure --with-kernel=/usr/src/linux-headers-$KERNEL --with-cards=all --with-card-options=all --with-sequencer=yes --with-oss=yes --prefix=/usr || die "$DRIVER configure failed"
#./configure --with-cards=usb-audio,hda-intel,emu10k1,hrtimer,rtctimer,hpet --with-card-options=all --with-sequencer=yes --with-oss=yes --with-kernel=/usr/src/linux --prefix=/usr || die "$DRIVER configure failed"
make || die "$DRIVER make failed"

#alsa-lib
header "Compiling library..."
cd $ALSASRCDIR/$LIB
make clean
./configure --prefix=/usr || die "$LIB configure failed"
make || die "$LIB make failed"

#alsa-plugins
header "Compiling plugins..."
cd $ALSASRCDIR/$PLUGINS
make clean
./configure  --prefix=/usr || die "$PLUGINS configure failed"
make || die "$PLUGINS make failed"

#alsa-firmware
header "Compiling firmware..."
cd $ALSASRCDIR/$FIRMWARE
make clean
./configure --prefix=/usr || die "$FIRMWARE configure failed"
make || die "$FIRMWARE make failed"

## utils will be compiled and installed later on, since lib needs to be installed first

#alsa-oss
header "Compiling OSS..."
cd $ALSASRCDIR/$OSS
make clean
./configure --prefix=/usr || die "$OSS configure failed"
make || die "$OSS make failed"


#alsa-tools if you need any of the tools you need to select and install them one by one manually - look up the respective directory within /usr/src/alsa/alsa-tools*/
#header "Compiling tools..."

#
#cd $ALSASRCDIR/$TOOLS
#for i in $TOOLSRC ; do
# cd $i
# if [ -x ./configure ]; then \
#  make clean   
#  ./configure --prefix=/usr ||  die "$Tools $i configure failed"
#  make ||  die "$Tools $i make failed"
# fi


}

installation () {

header "Installing all modules..."

header "Installing driver..."
cd $ALSASRCDIR/$DRIVER
make install
header "Installing library..."
cd $ALSASRCDIR/$LIB
make install
header "Installing plugins..."
cd $ALSASRCDIR/$PLUGINS
make install
header "Installing firmware..."
cd $ALSASRCDIR/$FIRMWARE
make install
header "Installing OSS..."
cd $ALSASRCDIR/$OSS
make install

#
#alsa-utils need to be compiled after lib installation!!
#

header "Compiling utils..."
cd $ALSASRCDIR/$UTILS
make clean
header "Compiling utils..."
./configure --prefix=/usr 
make
header "Installing utils..."
make install

#
#alsa-tools not yet ready!!
#

#cd $ALSASRCDIR/$TOOLS
#for j in $TOOLSRC ; do
# cd $j
#  header "Installing tool $i"
#  make install
# fi

#
#copy modules to respective kernel!!
#


cd ${ALSASRCDIR}/${DRIVER}/

find ./ -name ''*.ko'' > /tmp/alsa_manifest

header "Copy modules to target directories..."

#This block of code works with 2.6.24-x Ubuntu standard kernels
if [ "`uname -a| grep ${KERNEL1} `" != "" ] ; then
 tar -cv -T /tmp/alsa_manifest -f /lib/modules/`uname -r`/ubuntu/sound/alsa-driver/${DRIVER}.tar
 cd /lib/modules/`uname -r`/ubuntu/sound/alsa-driver
fi

#This block of code works with 2.6.26-x kernels
if [ "`uname -a| grep ${KERNEL2} `" != "" ] ; then
 tar -cv -T /tmp/alsa_manifest -f /lib/modules/`uname -r`/kernel/sound/${DRIVER}.tar
 cd /lib/modules/`uname -r`/kernel/sound/
fi

#This block of code works with 2.6.27 kernels 
if [ "`uname -a| grep ${KERNEL3} `" != "" ] ; then
 tar -cv -T /tmp/alsa_manifest -f /lib/modules/`uname -r`/kernel/sound/${DRIVER}.tar
 cd /lib/modules/`uname -r`/kernel/sound/
fi

#This block of code works with 2.6.28 kernels 
if [ "`uname -a| grep ${KERNEL4} `" != "" ] ; then
 tar -cv -T /tmp/alsa_manifest -f /lib/modules/`uname -r`/kernel/sound/${DRIVER}.tar
 cd /lib/modules/`uname -r`/kernel/sound/
fi

#This block of code works with 2.6.29 kernels 
if [ "`uname -a| grep ${KERNEL5} `" != "" ] ; then
 tar -cv -T /tmp/alsa_manifest -f /lib/modules/`uname -r`/kernel/sound/${DRIVER}.tar
 cd /lib/modules/`uname -r`/kernel/sound/
fi

#Extract new modules, overwriting old ones
tar -xvf ${DRIVER}.tar
rm *.tar

depmod -a

chmod a+rw /dev/dsp /dev/mixer /dev/sequencer /dev/midi /dev/snd/*

####alsa-utils patch for asound.state to avoid patching alsa-utils, see below debian patch - ####
##http://svn.debian.org/wsvn/pkg-alsa/trunk/alsa-utils/debian/patches/move_asound_state_to_var.patch?op=file&rev=0&sc=0

cd /var/lib/alsa
rm asound.state
ln -s /etc/asound.state asound.state

}


restorealsa () {
for y in ${KERNELPACKS} ; do
header "Package ${y} will be reinstalled" 
apt-get -y --reinstall install $y
done

for k in ${ALSAPACKS} ; do 
header "Package ${k} will be reinstalled" 
apt-get -y --reinstall install $k
done
depmod -a
}

downloadsnapshot () {
test -d $ALSASRCDIR || die "$ALSASRCDIR not found"
cd $ALSASRCDIR
test -d $DRIVER || die "$DRIVER  not found"
mv $DRIVER $DRIVER.old
wget ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/alsa-driver-snapshot.tar.gz
test -f  alsa-driver-snapshot.tar.gz || die "Download of snapshot didn't work"
tar xvvf alsa-driver-snapshot.tar.gz
mv alsa-driver $DRIVER
rm alsa-driver-snapshot.tar.gz
}

usage() {
    echo "
Usage: $0 [OPTION]...

Available options:
   -di    Download (to /usr/src), compile and install the packages
          This option will compeletely upgrade your ALSA in one step
   -d     Download the packages only
          In case you want to tweak/patch the official packages or 
          you'd like to install the snapshot on top of the official 
          packages prior to compiling and installating them   
   -c     Compilation only 
          Kind of dry-run option to see if the configuration and compilation 
          works
   -i     Compilation and installation of packages
          Sources must exist under /usr/src. Run script with -d or -di options first.
          The option is useful to speed up your installation in case Ubuntu upgrades 
          have overwritten your ALSA installation. It is also useful if you want to 
          keep your patched version or snapshot version, when reinstalling the packages
   -r     Restore ALSA 
          Kernel and all ALSA relevant Ubuntu packages will be restored
          (done by re-installation of relevant packages)
   -snap  Download, compile and install of latest ALSA driver-sources-snapshot 
          Please run script using -d option first. Recommended for troubleshooting.
          (The snapshot is not an offical ALSA release or even pre-release,
           it is the latest snapshot taken from the design-tree!) 
   -h     Help - this page 

Please visit http://ubuntuforums.org/showthread.php?t=962695 
to report any issues you might encounter by using this script.
"
    exit 1;
}


#--- main ----

case "$1" in
  -di)
        header "Alsa will be downloaded and installed"
        package  
        greet
        exec 1>${LOGFILE} 2>&1
        prep
        download
        compile
        installation
        bye     
        ;;
  -d)
        header "Alsa will be downloaded only"
        package
        greet
        exec 1>${LOGFILE} 2>&1
        prep
        download    
        ;;
  -c)
        header "Alsa will be compiled"
        package
        greet
        exec 1>${LOGFILE} 2>&1
        prep
        compile
        ;;

  -i)
        header "Alsa will be compiled and installed"
        package
        greet
        exec 1>${LOGFILE} 2>&1
        prep
        compile
        installation
        bye
        ;;

  -r)   
        header "Alsa will be restored. You'll get a maiden version from Ubuntu repositories"
        exec 1>${LOGFILE} 2>&1
        restorealsa
        ;;
  
  -snap)
        header "The latest Alsa-driver snapshot will be downloaded,compiled and installed"
        package
        greet
        exec 1>${LOGFILE} 2>&1
        downloadsnapshot
        compile
        installation
        bye
        ;;
    
  -h)
        usage
        exit 1
        ;;
  *)
        usage
        exit 1
        ;;
esac

exit 0


##----Script End ----



```
```

./alsaupg.sh -di
reboot
```

Now to test audio over HDMI is working type this:

```
 speaker-test -Dplughw:0,3 -c2
```
You should hear some static noise (that means it works)
You could also try

wget [http://www.vorbis.com/music/Epoq-Lepidoptera.ogg](http://www.vorbis.com/music/Epoq-Lepidoptera.ogg)
 aplay -Dplughw:0,3 Epoq-Lepidoptera.ogg

```
sudo gedit ~/.asound.asound.conf
```

```
defaults.pcm.device 3
```



[B]
4. Install this driver and firmware ONLY if you have a Hauppauge WinTV NOVA-HD-S2 
S2-API is the driver standard that will work out of the box starting with kernels 2.6.28.

```

WARNING: VDR 1.7.10 supports S2-API natively (if for some reason you want multiproto instead of S2-API, install VDR 1.7.0 instead)

```
[/B]
First the firmware... (thanks to Ahmed Y Shaheem for the tip)
```

sudo -s
apt-get install unrar -y
rm /lib/firmware/dvb-fe-c*
cd /usr/local/src
wget http://www.hauppauge.de/software/mce/88x_2_122_26109_WHQL.zip
unzip -jo 88x_2_122_26109_WHQL.zip Driver88/hcw88bda.sys
dd if=hcw88bda.sys of=dvb-fe-cx26109.fw skip=75504 bs=1 count=32501
cp dvb-fe-cx26109.fw /lib/firmware/
rm /lib/firmware/dvb-fe-cx24116.fw
ln -s /lib/firmware/dvb-fe-cx26109.fw /lib/firmware/dvb-fe-cx24116.fw


```
And now the driver...
```

apt-get install build-essential
apt-get install mercurial cvs subversion libncurses-dev
cd /usr/local/src
hg clone http://mercurial.intuxication.org/hg/s2-liplianin/
cd s2-liplianin
cd linux/include/linux
ln -s /usr/src/linux-headers-`uname -r`/include/linux/compiler.h ./
cd ../../../
make distclean
make
make install
depmod -a
reboot

```


You know you have the drivers installed and running when under
/dev/dvb/adapter0/ you see:

```
crw-rw----+ 1 root video 212, 1 2009-03-15 16:22 demux0
crw-rw----+ 1 root video 212, 2 2009-03-15 16:22 dvr0
crw-rw----+ 1 root video 212, 0 2009-03-15 16:22 frontend0
crw-rw----+ 1 root video 212, 3 2009-03-15 16:22 net0

```

**5. w_scan: Scan util**
Time to test your hardware is so far all working
Open the terminal

```
cd Desktop
download from here preferably:
http://www.ziddu.com/download/6797072/w_scan-20091004.tar.rar.html

wget http://wirbel.htpc-forum.de/w_scan/w_scan-20091004.tar.bz2
tar jxvf w_scan-20090528.tar.bz2
cd w_scan-20090528.tar.bz2
cp w_scan /usr/local/bin/
mkdir /etc/vdr
# Next line will scan dvb-s and dvb-s2 channels on Astra1
w_scan -fs -s S19E2 -o7 >> /etc/vdr/channels.conf


```


NOTE: wierbel scan is the best satellite scanner,current versions support Cable, Terrestrial even rotors and DVB-S2 channels!
An English Howto for w_scan can be found [here ]("http://edafe.org/vdr/w_scan/")
The latest w_scan can be found [here]("http://wirbel.htpc-forum.de/w_scan/index2.html")

open the newly created channels.conf and check it does contain lots of channels

**6. FFmpeg**
This little piece of software is part or the better known VLC
We are about to compile our own. You can find more info on [HOWTO: Install and use the latest FFmpeg and x264]("http://ubuntuforums.org/showthread.php?t=786095") 
but for vdr we also need --enable-postproc which is not part of that ffmpeg Howto, but otherwise a useful reference guide if you need
more info on compiling x264

```

cd /usr/local/src
sudo -s
apt-get build-dep ffmpeg
rm -rf /usr/include/ffmpeg
sudo rm /usr/local/bin/ffmpeg
apt-get install build-essential libx264-dev libmp3lame-dev libfaad-dev libxvidcore4-dev 
apt-get install mercurial cvs subversion libncurses-dev 
apt-get install autoconf libtool automake pkg-config gettext libfaac-dev 
apt-get install liba52-0.7.4-dev libvorbis-dev zlib1g-dev libpng12-dev libx11-dev libxv-dev libasound2-dev
svn checkout svn://svn.mplayerhq.hu/ffmpeg/trunk ffmpeg
cd ffmpeg/
#in next line if you have trouble compiling it try removing --enable-shared
./configure --prefix=/usr --enable-gpl --enable-nonfree --enable-postproc --enable-libmp3lame --enable-libvorbis --enable-pthreads --enable-libx264 --enable-libtheora --enable-libfaac --enable-libfaad --enable-libxvid --enable-shared

make
sudo checkinstall --fstrans=no --install=yes --pkgname=ffmpeg --pkgversion "3:0.svn`date +%Y%m%d`-12ubuntu3" --default
ldconfig -v

```

**7. Xine-Lib 1.2 CVS:**
[Here ]("http://www.ziddu.com/download/4995962/libxine2-dev_svn20090601ubuntuBUFFERFIXEDx386.rar.html")is my patched xine-lib1.2.deb package
[http://www.ziddu.com/download/4995962/libxine2-dev_svn20090601ubuntuBUFFERFIXEDx386.rar.html](http://www.ziddu.com/download/4995962/libxine2-dev_svn20090601ubuntuBUFFERFIXEDx386.rar.html)
with vdpau and faster zapping.
If it works for you great, else compile your own as per the instructions following.

NOTE:
Don't download the vdpau patch for xinelib directly from the wget line.
The maintainer keeps the patch update with the xinelib main version. Just have a look to his page:
[http://www.jusst.de/vdpau/files/xine-lib-1.2/?C=M;O=D](http://www.jusst.de/vdpau/files/xine-lib-1.2/?C=M;O=D)
and download the latest patch.
```

cd /usr/local/src
apt-get install libcdio-dev libvcdinfo-dev

hg clone http://hg.debian.org/hg/xine-lib/xine-lib-1.2-vdpau

cd xine-lib-1.2-vdpau

#Next 5 lines are optional, only if you want windows codecs in 
#which case append --enable-w32dll --with-w32-path=/usr/local/lib/win32 to the xine-lib autogen line
wget http://www8.mplayerhq.hu/MPlayer/releases/codecs/essential-20071007.tar.bz2
tar xivf essential-20071007.tar.bz2
mv essential-20071007 /usr/local/lib/win32
ln -s /usr/local/lib/win32 /usr/local/lib/codecs
#end of optional code, if you followed the optional lines append the parameters to the next line
./autogen.sh --prefix=/usr --with-external-ffmpeg --disable-dxr3 
make -j6
checkinstall --fstrans=no --install=yes --pkgname=libxine2-dev --pkgversion "1.2.svn`date +%Y%m%d`-12ubuntu3"
ldconfig -v
```

If make fails then edit gedit /usr/local/src/xine-lib-1.2/src/audio_dec Look for -ldts_pic and add -lm after it.

**8. Xine-UI-cvs**

```
cd /usr/local/src
apt-get install libxt-dev
# WARNING! We're going to install LIRCD and with this you can configure your remote if you want it used through LIRCD
apt-get install lirc lirc-modules-source lirc-x liblircclient-dev
wget http://home.vrweb.de/~rnissl/xine-ui-cvs-20090617220000.tar.bz2
tar jxvf xine-ui-cvs-20090617220000.tar.bz2
cd xine-ui
# in the next line personally I don´t use --enable-vdr-keys but you can add it if you need it
./autogen.sh --prefix=/usr 
make
make install
```
 
To configure the Hauppauge remote control that comes with the NOVA HD-S2

```
sudo dpkg-reconfigure lirc
```
[LIST=1]
[*]Select Hauppauge Nova-T 500, press next
[*]Select None, press next
[*]Select something ending with --event-ir, press ENTER
[/LIST]
 * mine looks like this:*
/dev/input/by-path/pci-0000:01:0a.0--event-ir 
 
Either the Nova-T 500 remote is not identical to the Nova-HD-S2 one
or the config files for the Nova-T 500 are buggy, but some 10 keys were dead.
Create the next 5 files to have a fully working Hauppaugge Nova-HD-S2 RCU 

The following file is ONLY for the Hauppaugge Remote that comes with the NOVA-HD-S2.If your remote is not the one that comes with the Hauppagge S2-HD check [this ]("http://shalafi.wiki.xs4all.nl/index.php?title=Resolving_the_/dev/input_change_with_Hauppauge_WinTV_NOVA-HD-S2/HVR-4000_-_Dutch")for help
```

sudo gedit /etc/udev/rules.d/55-local.rules

```
```

KERNEL=="event*", ATTRS{vendor}=="0x14f1", SYMLINK="input/irremote"

```

[/p]
The next file will ensure lirc has full access to your Hauppaugge Remote

```

sudo gedit /usr/share/hal/fdi/preprobe/20thirdparty/10-ignore-cx88-ir.fdi

```

```

<deviceinfo version="0.2">
&#8722;
<device>
&#8722;
<match key="info.product" contains_ncase="cx88 IR">
<merge key="info.ignore" type="bool">true</merge>
</match>
</device>
</deviceinfo>

```

The next 4 files will basically leave the remote that came with your Hauppaugge NOVA-HD-S2 fully configured
with all keys working as they should 
```

mkdir -p /etc/vdr/plugins
sudo gedit /etc/vdr/keymacros.conf

```
```

# Remote control key macros for VDR
# Format:
# macrokey  key1 key2 key3...
# macrokey  @plugin key1 key2 key3...
# See man vdr(5)

Red       Recordings
Green     Schedule
Yellow    Info
Blue      Timers

```

```

sudo gedit /etc/vdr/remote.conf

```

```

LIRC.Ok         Enter
LIRC.0          0
LIRC.1          1
LIRC.2          2
LIRC.3          3
LIRC.4          4
LIRC.5          5
LIRC.6          6
LIRC.7          7
LIRC.8          8
LIRC.9          9
LIRC.Menu       NextSong
LIRC.Back       BackExit
LIRC.Red        Red
LIRC.Green      Green
LIRC.Yellow     Yellow
LIRC.Blue       Blue
LIRC.Info       Menu
LIRC.Stop       Stop
LIRC.Record     Record
LIRC.Play       Play
LIRC.Pause      Pause
LIRC.FastFwd    Fwdwind
LIRC.FastRew    Rewind
LIRC.PrevChannel PrevCh
LIRC.Volume+    VolumeUp
LIRC.Volume-    VolumeDown
LIRC.Mute       Mute
LIRC.Audio      Text
LIRC.Subtitles  Sub
LIRC.Channels   TV
LIRC.Schedule   Guide
LIRC.Recordings Pictures
LIRC.Setup      PrevSong
KBD.Up         00000000001B5B41
KBD.Down       00000000001B5B42
KBD.Menu       000000000000006D
KBD.Ok         000000000000000D
KBD.Back       000000000000007F
KBD.Left       00000000001B5B44
KBD.Right      00000000001B5B43
KBD.Red        000000001B5B5B41
KBD.Green      000000001B5B5B42
KBD.Yellow     000000001B5B5B43
KBD.Blue       000000001B5B5B44
KBD.0          0000000000000030
KBD.1          0000000000000031
KBD.2          0000000000000032
KBD.3          0000000000000033
KBD.4          0000000000000034
KBD.5          0000000000000035
KBD.6          0000000000000036
KBD.7          0000000000000037
KBD.8          0000000000000038
KBD.9          0000000000000039
KBD.Play       000000001B5B5B45
KBD.Pause      0000001B5B31377E
KBD.Stop       0000001B5B31387E
KBD.Record     0000001B5B31397E
KBD.FastFwd    0000001B5B32307E
KBD.FastRew    0000001B5B32317E
KBD.Power      000000000000000A
KBD.Channel+   000000000000002B
KBD.Channel-   000000000000002D
KBD.Volume+    000000001B5B317E
KBD.Volume-    000000001B5B347E
KBD.Mute       0000000000000073
KBD.Audio      0000000000000061


```

```

sudo gedit /etc/lirc/lircd.conf

```

```

# brand:                       Hauppauge NOVA-HD-S2
# model no. of remote control: Hauppage NOVA-HD-S2 Snowboard Shape Silver over Black
#

begin remote

 name  NOVA-HD-S2
  bits           16
 eps            30
 aeps          100

 one             0     0
 zero            0     0
  pre_data_bits   16
  pre_data       0x8001
  gap          133325
  toggle_bit_mask 0x8001001C

    begin codes
         Pictures                 0x016F
         Go                       0x0161
         Text                     0x0184
         TV                       0x0179
         Videos                   0x0189
         Music                    0x0188
         Guide                    0x016D
         Radio                    0x0181
         ArrowUp                  0x0067
         ArrowDown                0x006C
         ArrowLeft                0x0069
         ArrowRight               0x006A
         Enter                    0x001C
         BackExit                 0x00AE
         Menu                     0x008B
         PrevCh                   0x019C
         Mute                     0x0071
         VolumeUp                 0x0073
         VolumeDown               0x0072
         ChannelUp                0x0192
         ChannelDown              0x0193
        Record                   0x00A7
         Stop                     0x0080
         Play                     0x00CF
         Pause                    0x0077
         Sub                      0x0172
         Power                    0x0074
         Rewind                   0x00A8
         Fwdwind                  0x00D0
         Sleep                    0x008E
         NextSong                 0x00A3
         PrevSong                 0x00A5
         1                        0x0002
         2                        0x0003
         3                        0x0004
         4                        0x0005
         5                        0x0006
         6                        0x0007
         7                        0x0008
         8                        0x0009
         9                        0x000A
         0                        0x000B
         Red                      0x018E
         Green                    0x018F
         Yellow                   0x0190
         Blue                     0x0191

 
 end codes

end remote

```


```

sudo gedit /etc/lirc/hardware.conf

```


```

REMOTE="Hauppauge NOVA-HD-S2"
REMOTE_MODULES=""
REMOTE_DRIVER="devinput"
# Next 2 lines will work as long as you have just 1 remote 
#Both the event and the by-path value can change so this way works fine
#TEMPIREVENT=`ls /dev/input/by-path/ |grep event-ir`
#REMOTE_DEVICE="/dev/input/by-path/$TEMPIREVENT"
#Next line ONLY if you have the Hauppage NOVA-S2-HD remote control otherwise # and un# the other two before
REMOTE_DEVICE="/dev/input/irremote"
REMOTE_LIRCD_CONF="/etc/lircd.conf"
REMOTE_LIRCD_ARGS=""
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""
START_LIRCD="true"
START_LIRCMD=""
LOAD_MODULES=""
LIRCMD_CONF=""
FORCE_NONINTERACTIVE_RECONFIGURATION="false"

```

From the terminal run irw
and press keys on your remote control, if you see stuff on the terminal as you press keys, you are doing very well indead.

Test xine works by typing xine in the terminal or create a launcher to that effect

**9. VDR 1.7.10 **

First we create the daemon script
/etc/init.d/vdr

```

sudo -s
touch /etc/init.d/vdr
chmod 755 /etc/init.d/vdr
gedit /etc/init.d/vdr


```

Paste the following text and save

```

#!/bin/sh
### BEGIN INIT INFO
# Provides:          VDR
# Required-Start:    $network
# Required-Stop:     $network
# Default-Start:     3 5
# Default-Stop:      0 1 2 6
# Description:       Start, Stop or Restart VDR
### END INIT INFO 

# Shell functions sourced from /etc/rc.status:
set -e

# Reset status of this service
# rc_reset

# 
case "$1" in
    start)
        echo -n "Starting VDR "
		/var/bin/runvdr >> /var/log/vdr.log &
        # Remember status and be verbose
        ;;
    stop)
        echo -n "Shutting down VDR "
		killall runvdr
		killall vdr
        # Remember status and be verbose
        ;;
    restart)
        echo -n "Restart VDR "
        $0 stop
        $0 start 

        # Remember status and be quiet
        ;;
    *)
        echo "Usage: $0 {start|stop|restart}"
        exit 1
        ;;
esac
# rc_exit
exit 0


```



Now we will download and compile VDR 1.7.10 with Extensions-Patch-72b 

```

cd /usr/local/src
apt-get install libfreetype6-dev libfontconfig1-dev libjpeg62-dev libcap-dev libncurses5-dev libncursesw5-dev liba52-0.7.4-dev libasound2-dev
wget ftp://ftp.tvdr.de/vdr/Developer/vdr-1.7.10.tar.bz2
tar xivf vdr-1.7.10.tar.bz2
ln -s vdr-1.7.10 vdr
#wget http://www.zulu-entertainment.de/page/klick.php?d=VDR+Extensions+Patch

mkdir VDR-Extentions-Patch-72
cd VDR-Extentions-Patch-72
wget http://wbreu.htpc-forum.de/downloads/vdr1.7.10extensions.zip
unzip vdr1.7.10extensions.zip
cd ../vdr
patch -p1 < ../VDR-Extensions-Patch-72/vdr-1.7.10_extensions.diff
# Next line is just in case you just updated your kernel,do not worry if you get an error saying ´files are the same´
sudo cp /usr/src/linux-headers-`uname -r`/include/linux/compiler.h /usr/local/src/s2-liplianin/linux/include/linux/compiler.h 
sudo gedit /usr/local/src/vdr/Make.config

```


Next copy and paste the following Make.config

```

# $Id: Make.config by Art2003  April 2009

### The C compiler and options:

CC       = gcc
CFLAGS   = -g -O2 -Wall

CXX      = g++
CXXFLAGS = -g -O2 -Wall -Woverloaded-virtual -Wno-parentheses

ifdef PLUGIN
CFLAGS   += -fPIC
CXXFLAGS += -fPIC
DEFINES += -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_LARGEFILE64_SOURCE
endif

### The directory environment:
DVBDIR   = /usr/local/src/s2-liplianin/linux
MANDIR   = /usr/local/man
BINDIR   = /usr/bin

LOCDIR   = /usr/share/locale
PLUGINDIR= ./PLUGINS
PLUGINLIBDIR=  /usr/lib/vdr/plugins
VDRSCRIPTDIR = /usr/lib/vdr/scripts
VIDEODIR = /media/video/vdr
CONFDIR  = /etc/vdr

### The remote control:

LIRC_DEVICE = /dev/lircd
RCU_DEVICE  = /dev/input/ttyS1

## Define if you want vdr to not run as root
#VDR_USER = vdr
### VDR-Extensions:
# Comment the patches you don't need
# DVDCHAPJUMP needs DVDARCHIVE enabled
# DVDARCHIVE needs LIEMIEXT enabled
# SORTRECORDS needs LIEMIEXT enabled
# you can only enable MENUORG or SETUP

#DVBSETUP = 1
SETUP = 1

### You don't need to touch the following:

ifdef DVBDIR
INCLUDES += -I$(DVBDIR)/include
endif

ifdef ANALOGTV
DEFINES += -DUSE_ANALOGTV
endif
ifdef ATSC
DEFINES += -DUSE_ATSC
endif

ifdef CHANNELSCAN
DEFINES += -DUSE_CHANNELSCAN
endif

ifdef CMDRECCMDI18N
DEFINES += -DUSE_CMDRECCMDI18N
endif

ifdef CMDSUBMENU
DEFINES += -DUSE_CMDSUBMENU
endif

ifdef CUTTERLIMIT
DEFINES += -DUSE_CUTTERLIMIT
endif
ifdef CUTTERQUEUE
DEFINES += -DUSE_CUTTERQUEUE
endif

ifdef CUTTIME
DEFINES += -DUSE_CUTTIME
endif

ifdef DDEPGENTRY
DEFINES += -DUSE_DDEPGENTRY
endif

ifdef DELTIMESHIFTREC
DEFINES += -DUSE_DELTIMESHIFTREC
endif

ifdef DOLBYINREC
DEFINES += -DUSE_DOLBYINREC
endif

ifdef DVBSETUP
DEFINES += -DUSE_DVBSETUP
endif
ifdef DVDARCHIVE
ifdef LIEMIEXT
DEFINES += -DUSE_DVDARCHIVE
endif
endif

ifdef DVLRECSCRIPTADDON
DEFINES += -DUSE_DVLRECSCRIPTADDON
endif

ifdef DVLVIDPREFER
DEFINES += -DUSE_DVLVIDPREFER
endif

ifdef DVLFRIENDLYFNAMES
DEFINES += -DUSE_DVLFRIENDLYFNAMES
endif

ifdef EM84XX
DEFINES += -DUSE_EM84XX
endif
ifdef GRAPHTFT
DEFINES += -DUSE_GRAPHTFT
endif

ifdef HARDLINKCUTTER
DEFINES += -DUSE_HARDLINKCUTTER
endif

ifdef JUMPPLAY
DEFINES += -DUSE_JUMPPLAY
endif

ifdef LIEMIEXT
DEFINES += -DUSE_LIEMIEXT
endif

ifdef LIRCSETTINGS
DEFINES += -DUSE_LIRCSETTINGS
endif
ifdef LNBSHARE
DEFINES += -DUSE_LNBSHARE
endif

ifdef MAINMENUHOOKS
DEFINES += -DUSE_MAINMENUHOOKS
endif

ifdef MENUORG
DEFINES += -DUSE_MENUORG
else
ifdef SETUP
DEFINES += -DUSE_SETUP
endif
endif

ifdef NOEPG
DEFINES += -DUSE_NOEPG
endif

ifdef OSDMAXITEMS
DEFINES += -DUSE_OSDMAXITEMS
endif

ifdef PINPLUGIN
DEFINES += -DUSE_PINPLUGIN
endif

ifdef PLUGINMISSING
DEFINES += -DUSE_PLUGINMISSING
endif

ifdef PLUGINPARAM
DEFINES += -DUSE_PLUGINPARAM
endif

ifdef ROTOR
DEFINES += -DUSE_ROTOR
endif

ifdef SETTIME
DEFINES += -DUSE_SETTIME
endif
ifdef SOFTOSD
DEFINES += -DUSE_SOFTOSD
endif

ifdef SOURCECAPS
DEFINES += -DUSE_SOURCECAPS
endif

ifdef SORTRECORDS
ifdef LIEMIEXT
DEFINES += -DUSE_SORTRECORDS
endif
endif

ifdef TIMERCMD
DEFINES += -DUSE_TIMERCMD
endif

ifdef TIMERINFO
DEFINES += -DUSE_TIMERINFO
endif
ifdef VALIDINPUT
DEFINES += -DUSE_VALIDINPUT
endif

ifdef VOLCTRL
DEFINES += -DUSE_VOLCTRL
endif

ifdef WAREAGLEICON
DEFINES += -DUSE_WAREAGLEICON
endif

ifdef YAEPG
DEFINES += -DUSE_YAEPG
endif

ifdef PARENTALRATING
DEFINES += -DUSE_PARENTALRATING
endif

ifdef STREAMDEVEXT
DEFINES += -DUSE_STREAMDEVEXT
endif


```

And final bunch of commands for VDR1.7.8
```

sudo -s
mkdir -p /media/video/vdr
mkdir -p /usr/lib/vdr/plugins
mkdir -p /usr/lib/vdr/scripts
mkdir -p /etc/vdr/plugins
make
make install
cp -a svdrpsend.pl /usr/bin
cp *.conf /etc/vdr/

```

**10. VDR Plugins and automation (including CCcam scripts)**

Have a look [here]("http://www.linuxtv.org/vdrwiki/index.php/Patches") for patches:

and [here in German]("http://www.vdr-wiki.de/wiki/index.php/Patches") (many more plugins)

Back to the terminal!!:

```
sudo -s
gedit /var/bin/runvdr
```

```
export LANG=en_EN
export LC_COLLATE=en_EN

PATH=/usr/local/bin:$PATH

VDRPRG="/usr/bin/vdr"
VDRCMD="/usr/bin/vdr -c /etc/vdr --lirc --no-kbd -E /var/vdr -l 3 \
        -P sc \
        -P femon \
        -P setup \
        -P skinreel \
        -P xine \
        -P wirbelscan \
        -u root \
        $*"

KILL="/usr/bin/killall -q -TERM"

# Detect whether the DVB driver is already loaded
# and return 0 if it *is* loaded, 1 if not:
DriverLoaded()
{
  return 1
}

# Load all DVB driver modules needed for your hardware:
LoadDriver ()
{

  return 0

}

# Unload all DVB driver modules loaded in LoadDriver():
UnloadDriver ()
{

  return 0

}

# Load driver if it hasn't been loaded already:
if ! DriverLoaded; then
   LoadDriver
   fi

while (true) do
      eval "$VDRCMD"
      if test $? -eq 0 -o $? -eq 2; then exit; fi
      echo "`date` reloading DVB driver"
      $KILL $VDRPRG
      sleep 10
      UnloadDriver
      LoadDriver
      echo "`date` restarting VDR"
      done
```

```
chmod 755 /var/bin/runvdr
```


(optional)Femon - Signal Information plugin [http://www.linuxtv.org/vdrwiki/index.php/Femon-plugin]("http://www.linuxtv.org/vdrwiki/index.php/Femon-plugin")
```

cd /usr/local/src/vdr/PLUGINS/src
wget http://www.saunalahti.fi/~rahrenbe/vdr/femon/files/vdr-femon-1.7.2.tgz
tar xzvf vdr-femon-1.7.2.tgz
ln -s femon-1.7.2 femon
cd /usr/local/src/vdr/
make plugins
make install

```

(optional)Streamdev plugin (needed only if you plan to use XBMC) [http://streamdev.vdr-developer.org/]("http://streamdev.vdr-developer.org/") 
Add to Make.config above the following line (after SETUP = 1 )
```
STREAMDEVEXT = 1
```
Now recompile VDR with this extension support:

```

cd /usr/local/src/vdr
sudo make clean && make 
cd /usr/local/src/vdr/PLUGINS/src
cvs -d:pserver:anoncvs@vdr-developer.org:/var/cvsroot login
###Simply hit ENTER when asked for a password.
cvs -d:pserver:anoncvs@vdr-developer.org:/var/cvsroot co -D 2/18/09 streamdev
sudo mkdir -p /etc/vdr/plugins/streamdev
cd streamdev
sudo cp streamdev/streamdevhosts.conf /etc/vdr/plugins/streamdev
sudo cp streamdev/streamdevhosts.conf /etc/vdr/vdrsvdrphosts.conf
cd /usr/local/src/vdr/
make plugins
make install

```

(optional)Enigma skin (looking a bit like a Dreambox with picon...)
```

cd /usr/local/src/vdr/PLUGINS/src
wget http://andreas.vdr-developer.org/enigmang/download/vdr-skinenigmang-0.0.6.tgz
tar xivf vdr-skinenigmang-0.0.6.tgz
ln -s skinenigmang-0.0.6 skinenigmang
cd /usr/local/src/vdr/
make plugins
make install
mkdir -p /etc/vdr/plugins/skinenigmang
cd /etc/vdr/plugins
wget http://andreas.vdr-developer.org/enigmang/download/skinenigmang-logos-xpm-hi-20070702.tgz
wget http://andreas.vdr-developer.org/enigmang/download/skinenigmang-channellogos-xpm-hi-20070702.tgz
wget http://andreas.vdr-developer.org/enigmang/download/skinenigmang-fonts-20080225.tgz
tar xzvf skinenigmang-logos-xpm-hi-20070702.tgz
tar xzvf skinenigmang-channellogos-xpm-hi-20070702.tgz
tar xzvf skinenigmang-fonts-20080225.tgz

```

**Optional - Rotor Plugin - To move a dish and store positions, gotoX, etc**
REMOVE in Make.config (if it exists)the line with: * see note at foot of page
ROTOR = 1

```

cd /usr/local/src/vdr
#patch -p1 < ../VDR-Extensions-Patch-72/vdr-1.7.8-ext_gotox.diff
cd PLUGINS/src
wget http://ubuntuforums.org/attachment.php?attachmentid=109895&stc=1&d=1239814342
mv attachment.php?attachmentid=109895 rotor-0.1.4S2API.tar.gz
tar zxvf rotor-0.1.4S2API.tar.gz
ln -s rotor-0.1.4S2API rotor
cd ../../
make plugins
make install


```


**sc TRUNK - softcam plugin (Needed for CCcam)**
```

cd /usr/local/src/vdr/PLUGINS/src
apt-get install libssl-dev 
hg clone -r trunk http://85.17.209.13:6100/sc
cd /usr/local/src/vdr/
make plugins
make install
mkdir -p /etc/vdr/plugins/sc

```

**(Optional) Setup plugin ** (needed if you want CCcam info or ecm.info or to be able to run bash scripts from VDR)
Make sure you have applied the Extensions patch (tested with 70) to VDR and that there is a line in Make.config
that reads:
SETUP = 1

```

cd /usr/local/src/vdr/PLUGINS/src
sudo wget http://www.zulu-entertainment.de/files/vdr-setup/vdr-setup-0.3.1-zulu-edition.tgz
sudo tar zxvf vdr-setup-0.3.1-zulu-edition.tgz
sudo ln -s setup-0.3.1-zulu-edition setup
cd setup
sudo mkdir /etc/vdr/plugins/setup
cd /usr/local/src/vdr
sudo make plugins
sudo make install



```

Now we create a sample menu configuration file
```

sudo gedit /etc/vdr/plugins/setup/vdr-menu.xml

```

```

<menus suffix="...">
    <system name="Schedule" />
    <system name="Channels" />
    <system name="Timers" />
    <system name="Recordings" />
    <menu name="System">
        <plugin name="systeminfo" />
        <system name="Setup" />
        <system name="Commands" />
        <plugin name="setup" />
    </menu>
    <menu name="CCcam Info">
        <command name="EMC info" execute="cat /tmp/ecm0.info" />
        <command name="CCcam smartcard info" execute="echo entitlements | nc localhost 16000" />
        <command name="CCcam provider info" execute="echo providers | nc localhost 16000" />
        <command name="CCcam online servers" execute="echo servers | nc localhost 16000" />
        <command name="CCcam online shares" execute="echo shares | nc localhost 16000" />
        <command name="CCcam active clients" execute="echo activeclients | nc localhost 16000" />
        <command name="CCcam online clients" execute="echo clients | nc localhost 16000" />
        <command name="QUIT vdr" execute="/etc/init.d/vdr stop" />
        <command name="RESTART CCcam" execute="/etc/init.d/cccam restart" />
        <command name="STOP CCcam" execute="/etc/init.d/cccam stop" />
        <command name="START CCcam" execute="/etc/init.d/cccam start" />
        <command name="Whose card?" execute="cat /tmp/ecm0.info|grep address:" />
        <command name="CCcam info" execute="echo info | nc localhost 16000" />
        <command name="CCcam config" execute="cat /var/etc/CCcam.cfg" />
    </menu>
    <plugin name="satlist" />
    <plugin name="femon" />
</menus>

```

And ...

```

sudo gedit /etc/vdr/plugins/setup/vdr-setup.xml


```

```

<setup sysconfigFile="/etc/sysconfig" bootLinux="sudo /sbin/reboot" VDRlibDir="/usr/lib/vdr/plugins">
    <plugins sysconfig="PLUGINLIST">
        <plugin name="setup" info="setup" active="yes" />
    </plugins>
    <menus>
        <menu name="VDR">
            <menu name="OSD" help2="setup_osd.hlp" system="OSD" />
            <menu name="EPG" help2="setup_epg.hlp" system="EPG" />
            <menu name="DVB" help2="setup_dvb.hlp" system="DVB" />
            <menu name="LNB" help2="setup_lnb.hlp" system="LNB" />
            <menu name="CAM" help2="setup_cicam.hlp" system="CAM" />
            <menu name="Menu Edit" help2="setup_editmenu.hlp" system="VDRMenu" />
            <menu name="Recording" help2="setup_record.hlp" system="Record" />
            <menu name="Replay" help2="setup_replay.hlp" system="Replay" />
            <menu name="Miscellaneous" help2="setup_misc.hlp" system="Misc" />
            <menu name="Plugins" system="Plugins" />
        </menu>
        <menu name="Plugins">
            <menu name="Plugins" system="Plugins" />
            <menu name="Plugins activate / deactivate" help2="setup_actplugins.hlp" system="ActPlugins" />
        </menu>
        <menu name="System">
            <entry name="Use Sysconfig" sysconfig="USE_SYSCONFIG" type="bool" value="off" />
        </menu>
    </menus>
</setup>

```


**(Optional) Skin Reel - VDR Skin**
```

cd /usr/local/src/vdr/PLUGINS/src
wget http://rsync16.de.gentoo.org/files/vdr-skinreel/vdr-skinreel-0.0.1.tgz
tar xzvf vdr-skinreel-0.0.1.tgz
ln -s skinreel-0.0.1 skinreel
cd skinreel
sed -i Makefile -e 's/VDRVERSION/APIVERSION/g'
cp -r skinreel /etc/vdr/plugins/
cd /usr/local/src/vdr/
make plugins
make install

```

**WIRBEL SCAN - PLUGIN to scan channels VDR**
Download vdr-wirbelscan-0.0.4b_20090416.tgz  to /usr/local/src/vdr/PLUGINS/src
(The file is available as an attachment in this thread)
```

cd /usr/local/src/vdr/PLUGINS/src
# It does not scan DVB-S2 channels
tar zxvf vdr-wirbelscan-0.0.4b_20090416.tgz 
ln -s wirbelscan-0.0.4b_20090416  wirbelscan 
cd /usr/local/src/vdr/
make plugins
make install
# Next line verifies the plugin is in its place it if shows no file then copy it
ls /usr/lib/vdr/plugins/libvdr-wirbelscan.so.1.7.8
#manually from /usr/locar/src/vdr/PLUGINGS/src/wirbelscan adding the suffix .1.7.8

```

**XINE - VDR Xine plugin, needed for OXINE to connect to VDR**
```

cd /usr/local/src/vdr/PLUGINS/src
# vdr-xine-0.9.3 or later are compatible with VDR 1.7.8
wget http://home.vrweb.de/rnissl/vdr-xine-0.9.3.tgz
tar zxvf vdr-xine-0.9.3.tgz
ln -s xine-0.9.3 xine
cd /usr/local/src/vdr/PLUGINS/xine/data
mkdir -p /etc/vdr/plugins/xine/
cp *.mpg /etc/vdr/plugins/xine/
cd /usr/local/src/vdr/
make plugins
make install

```

For CCcam first lets create the scripts that will run it (DO NOT RUN CCcam.x86 from the command line!)

```

sudo -s
touch /etc/init.d/cccam
chmod 755 /etc/init.d/cccam
gedit /etc/init.d/cccam


```

```

#!/bin/sh
### BEGIN INIT INFO
# Provides:          CCcam
# Required-Start:    $network
# Required-Stop:     $network
# Default-Start:     3 5
# Default-Stop:      0 1 2 6
# Description:       Start, Stop or Restart the CCcam softcam
### END INIT INFO 

# Shell functions sourced from /etc/rc.status:
set -e

# Reset status of this service
# rc_reset

# 
case "$1" in
    start)
        echo -n "Starting CCcam "
	/var/bin/run.sh &
        # Remember status and be verbose
        ;;
    stop)
        echo -n "Shutting down CCcam "
		killall run.sh
		killall CCcam.x86
        # Remember status and be verbose
        ;;
    restart)
        echo -n "Restart CCcam "
        $0 stop
        $0 start 
        # Remember status and be quiet
        ;;
    *)
        echo "Usage: $0 {start|stop|restart}"
        exit 1
        ;;
esac
# rc_exit
exit 0

```

You will need CCcam.x86 in /var/bin  but this tutorial will not cover where to obtain such a file if it really exists!

```

touch /var/bin/run.sh
chmod 755 /var/bin/run.sh
gedit /var/bin/run.sh

```

And paste there the following code (and save it)
```

#!/bin/sh
cd /var/bin
gcc -march=pentium -mmmx -fomit-frame-pointer -fexpensive-optimizations -funroll-loops -fPIC -shared -o ca.so ca.c -ldl
LD_PRELOAD=./ca.so ; export LD_PRELOAD
while [ 1 ];
do
 ./CCcam.x86 -d > /var/log/CCcam.log
done

```


Finally the CCcam wrapper and setting CCcam to start automatically upon booting, especially handy if you are running a server
as if the process CCcam.x86 dies it will be automatically restarted

```

touch /var/bin/ca.c
chmod 755 /var/bin/ca.c
ln -s /etc/init.d/cccam /etc/rc2.d/S50cccam
sudo cp /usr/local/src/vdr/PLUGINS/src/sc/contrib/cccam_ca.c /var/bin/ca.c


```


[B]
11. OXINE - The cherry on the cake
[/B]
OXINE can be used as a VDR FRONTEND (able to play DVDs, Music, Video files) already patched for VDR and in a .deb format (tested under Ubuntu 8.10) Make sure you installed the XINE plugin before (see instructions above in the VDR-plugins section)
Bear in mind oxine has no vdpau support as such but since it can launch external commands (like bash scripts) it is possible to configure oxine to call mplayer or xine with the right set of parameters to use vdpau. I have written a few 
scripts that make all this work transparently but they are not part of this tutorial.

The basic script to have xine with vdpau using oxine as the frontend is:
sudo gedit /usr/sbin/tvoxi.sh
```

#!/bin/sh
sudo /etc/init.d/oxine stop
/usr/bin/xine -f --no-splash --no-gui -V vdpau --post vdr_video --post vdr_audio "vdr:/tmp/vdr-xine/stream#demux:mpeg_pes"
while pidof xine >/dev/null;do
pidof vdr >/dev/null || killall -9 xine ;
sleep 10;
done
sudo killall Thunar nautilus

sudo /etc/init.d/oxine start


```
sudo touch /etc/init.d/oxine
sudo chmod 755 /etc/init.d/oxine
sudo gedit /etc/init.d/oxine 

```


#!/bin/sh
### BEGIN INIT INFO
# Provides:          oxine
# Required-Start:    $network
# Required-Stop:     $network
# Default-Start:     2
# Default-Stop:      0 1 2 6
# Description:       Start, Stop or Restart the oxine softcam
### END INIT INFO 

# Shell functions sourced from /etc/rc.status:
set -e

# Reset status of this service
# rc_reset

# 
case "$1" in
    start)
        echo -n "Starting Oxine "
	oxine &
        ;;
    stop)
        echo -n "Shutting down Oxine "
		killall oxine
        ;;
    restart)
        echo -n "Restart Oxine "
        $0 stop
        $0 start 
        ;;
    *)
        echo "Usage: $0 {start|stop|restart}"
        exit 1
        ;;
esac
# rc_exit
exit 0

```

For vdpau in mainmenu.xml replace later on the Watch TV command with the following:
```

    <title>Watch TV</title>
    <action type="shellcommand" parameter="/usr/sbin/tvoxi.sh >/dev/null" />
 </button>

```



Now, we are going to install a special oxine.deb patched with VDR support (but not vdpau other than as external commands)
Download [oxine-vdr-patched_0.7.1-1_i386.deb]("http://www.ziddu.com/download/3959648/oxine-vdr-patched_0.7.1-1_i386.rar.html")
NOTE:These config files assume you are logged on as user tv
If this is different please amend accordingly!!
```

sudo apt-get install vorbis-tools flac mount
sudo apt-get build-dep oxine
sudo dpkg -i oxine-vdr-patched_0.7.1-1_i386.deb
mkdir ~/.oxine
cd /usr/local/src/ffmpeg
sudo make install

```

**Alternative installation for oxine is the .deb does not work for you, compile your own**:
```

cd /usr/local/src
sudo -s
apt-get install libfaac-dev libfaad-dev curl imagemagick
wget http://downloads.sourceforge.net/project/oxine/oxine/0.7.1/oxine-0.7.1.tar.gz?use_mirror=switch
tar zxvf oxine-0.7.1.tar.gz
cd oxine-0.7.1
./configure --prefix=/usr --enable-vdr --disable-joystick --without-imagemagick --disable-dependency-tracking --disable-weather --disable-shoutcast --disable-youtube --without-curl     
make
make install

```
Notes: 

a) If oxine gives you an error about PNG files then you probably need a different ffmpeg version. This is the thing with downloading SVN sources
sometimes something is broken temporarily. </p>
b) If you are trying this on Ubuntu 9.04 save yourself a lot of hassle and try kaffeine first, if you can get any free to air channels to work there, <BR>
then this guide for VDR is for you, otherwise do not bother.
```

Oxine config files (to be placed in ~/.oxine/ )
Are an attachment to this post.

```

[VDR screenshots]("http://www.kuba4u.de/vdr/pics/page_01.htm")

 [DOWNLOAD HERE]("http://www.ziddu.com/download/6518674/vdr-1.7.9-art2003.rar.html") my /usr/local/src/vdr-1.7.9 with all the plugins and patches you (probably) need

NOTES:
If you have freezing with HD channels check the following:
a) in /etc/X11/xorg.conf make sure     Option         "Composite" "Disabled"
b) swith to a SD channel, run this command and then try again the HD channel:

```

sudo sh -c "echo performance > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor"

```

[COLOR="Blue"][B]
[Do you want to own a house in the Spanish Tuscany?]("http://goo.gl/p84d8")[/B][/COLOR]

---

### Post by phjr on 2009-04-24
when I try to build vdr (i.e. run make in /usr/local/src/vdr) I get the error below; note that I'm running Ubuntu 9.04 64bit - anybody has idea what could be wrong?

```
g++ -g -O2 -Wall -Woverloaded-virtual -Wno-parentheses -c -DUSE_SETUP -DREMOTE_KBD -DLIRC_DEVICE=\"/dev/lircd\" -DRCU_DEVICE=\"/dev/input/ttyS1\" -D_GNU_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_LARGEFILE64_SOURCE -DVIDEODIR=\"/media/video/vdr\" -DCONFDIR=\"/etc/vdr\" -DPLUGINDIR=\"/usr/lib/vdr/plugins\" -DLOCDIR=\"/usr/share/locale\" -I/usr/include/freetype2 -I/usr/local/src/s2-liplianin/linux/include dvbdevice.c
In file included from /usr/include/netinet/in.h:24,
                 from /usr/include/arpa/inet.h:23,
                 from config.h:13,
                 from channels.h:13,
                 from device.h:13,
                 from dvbdevice.h:15,
                 from dvbdevice.c:10:
/usr/include/stdint.h:41: error: conflicting declaration &#8216;typedef long int int64_t&#8217;
/usr/include/linux/types.h:98: error: &#8216;int64_t&#8217; has a previous declaration as &#8216;typedef __s64 int64_t&#8217;
/usr/include/stdint.h:56: error: conflicting declaration &#8216;typedef long unsigned int uint64_t&#8217;
/usr/include/linux/types.h:96: error: &#8216;uint64_t&#8217; has a previous declaration as &#8216;typedef __u64 uint64_t&#8217;
In file included from /usr/include/sys/uio.h:24,
                 from /usr/include/sys/socket.h:28,
                 from /usr/include/netinet/in.h:25,
                 from /usr/include/arpa/inet.h:23,
                 from config.h:13,
                 from channels.h:13,
                 from device.h:13,
                 from dvbdevice.h:15,
                 from dvbdevice.c:10:
/usr/include/sys/types.h:46: error: conflicting declaration &#8216;typedef __loff_t loff_t&#8217;
/usr/include/linux/types.h:30: error: &#8216;loff_t&#8217; has a previous declaration as &#8216;typedef __kernel_loff_t loff_t&#8217;
/usr/include/sys/types.h:62: error: conflicting declaration &#8216;typedef __dev_t dev_t&#8217;
/usr/include/linux/types.h:13: error: &#8216;dev_t&#8217; has a previous declaration as &#8216;typedef __kernel_dev_t dev_t&#8217;
In file included from /usr/include/sys/types.h:133,
                 from /usr/include/sys/uio.h:24,
                 from /usr/include/sys/socket.h:28,
                 from /usr/include/netinet/in.h:25,
                 from /usr/include/arpa/inet.h:23,
                 from config.h:13,
                 from channels.h:13,
                 from device.h:13,
                 from dvbdevice.h:15,
                 from dvbdevice.c:10:
/usr/include/time.h:105: error: conflicting declaration &#8216;typedef void* timer_t&#8217;
/usr/include/linux/types.h:22: error: &#8216;timer_t&#8217; has a previous declaration as &#8216;typedef __kernel_timer_t timer_t&#8217;
In file included from /usr/include/sys/uio.h:24,
                 from /usr/include/sys/socket.h:28,
                 from /usr/include/netinet/in.h:25,
                 from /usr/include/arpa/inet.h:23,
                 from config.h:13,
                 from channels.h:13,
                 from device.h:13,
                 from dvbdevice.h:15,
                 from dvbdevice.c:10:
/usr/include/sys/types.h:204: error: conflicting declaration &#8216;typedef long unsigned int u_int64_t&#8217;
/usr/include/linux/types.h:97: error: &#8216;u_int64_t&#8217; has a previous declaration as &#8216;typedef __u64 u_int64_t&#8217;
In file included from /usr/include/sys/types.h:220,
                 from /usr/include/sys/uio.h:24,
                 from /usr/include/sys/socket.h:28,
                 from /usr/include/netinet/in.h:25,
                 from /usr/include/arpa/inet.h:23,
                 from config.h:13,
                 from channels.h:13,
                 from device.h:13,
                 from dvbdevice.h:15,
                 from dvbdevice.c:10:
/usr/include/sys/select.h:78: error: conflicting declaration &#8216;typedef struct fd_set fd_set&#8217;
/usr/include/linux/types.h:12: error: &#8216;fd_set&#8217; has a previous declaration as &#8216;typedef struct __kernel_fd_set fd_set&#8217;
In file included from /usr/include/sys/uio.h:24,
                 from /usr/include/sys/socket.h:28,
                 from /usr/include/netinet/in.h:25,
                 from /usr/include/arpa/inet.h:23,
                 from config.h:13,
                 from channels.h:13,
                 from device.h:13,
                 from dvbdevice.h:15,
                 from dvbdevice.c:10:
/usr/include/sys/types.h:248: error: conflicting declaration &#8216;typedef __blkcnt64_t blkcnt_t&#8217;
/usr/include/linux/types.h:124: error: &#8216;blkcnt_t&#8217; has a previous declaration as &#8216;typedef long unsigned int blkcnt_t&#8217;
make: *** [dvbdevice.o] Error 1

```EDIT: seems that this is a known bug in a debian package, see [http://www.mail-archive.com/debian-kernel@lists.debian.org/msg44521.html](http://www.mail-archive.com/debian-kernel@lists.debian.org/msg44521.html)

I don't know how to solve it though :-(

---

### Post by art2003 on 2009-04-28
You don't really need 64bits for this project, once you install vdpau cpu utilization on 32bits ubuntu is about 15% watching encrypted hd channels... I will add a vdpau chapter to this howto when I get the time

---

### Post by boba23 on 2009-04-29
Hey man, great howto! I am gonna try this tomorrow on my 9.04 box with xbmc already running on it. Only thing is, that I do have a KNC ONE DVB-C card instead of DVB-S. Is there anything special or important to consider when running VDR for DVB-C. I guess the main difference is the channel scan section .... anything else I need to adjust?

boba

---

### Post by art2003 on 2009-04-30
Should work ok, obviously you need to get your own card drivers so that you have /dev/dvb/adapter0 and those drivers be S2-API compliant.

You can use wierbel-scan to scan for DVB-C channels. The attachment is on this thread

Good luck!

---

### Post by boba23 on 2009-04-30
> **art2003 said:**
> Should work ok, obviously you need to get your own card drivers so that you have /dev/dvb/adapter0 and those drivers be S2-API compliant.

You can use wierbel-scan to scan for DVB-C channels. The attachment is on this thread

Good luck!

hey art, 

thanks for the reply.
I got vdr now basically up and running. I got trouble compiling ca.c though. I am on Jaunty, and get the following error when trying to compile:

$ gcc -O -fbuiltin -fomit-frame-pointer -fPIC -shared -o ca.so ca.c -ldl
ca.c:106: error: expected â,â or â;â before â{â token
ca.c: In function âcactlâ:
ca.c:233: error: expected expression before â<â token

any ideas?

boba

---

### Post by montenis on 2009-04-30
Awsome tutorial, i have one problem that i could not sort out though , maybe someone has a solution: xine-lib has no png support, but ffmpeg is able to open png's. I've been trying to find a solution but with no luck yet.

---

### Post by serkan61 on 2009-04-30
Hi All,

I will try to install this vdr 1.7.5 with Cccam to share with my dreambox 500-s..

[LIST]
my config:
[*]- Motherboard: Asus P5N7A-VM: Geforce 9300 IGP
[*]- CPU : Intel Core 2 Duo E5200
[*]- Cpu-koeler: Scythe Ninja Mini 
[*]- Memory : Kingston 2GB PC2-6400 
[*]- DVD-drive : Samsung only DVD player/writer
[*]- Harddisk : Samsung Spinpoint F1 DT HD103UJ, 1TB (only for UBUNTU 9.04)
[*]- Harddisk: Western digital Caviar Green WD10EACS 1Tb (only for Vista/windows7)
[*]- Budgetcard : Hauppauge WinTV NOVA-HD-S2 
[*]- Case: Silverstone SST-LC17B 
[*]- Power: Corsair CMPSU-450VX
[/LIST]

my target is on linux (Ubuntu 9.04) to create a system to watch HD channels from satelite and watch .mkv films with XvMC ....

This is my first pc with linux... :D

++ ubuntu 9.04 has been installed...
++ now try to install vdr 1.7.5

---

### Post by serkan61 on 2009-04-30
I cannot install Xine-lib, if I type "make" I get error see below...

If make fails then edit gedit /usr/local/src/xine-lib-1.2/src/audio_dec Look for -ldts_pic and add -lm after it.

This is a directory /usr/local/src/xine-lib-1.2/src/audio_dec ???

any idea???

7. Xine-Lib 1.2 CVS:

```

cd /usr/local/src
apt-get install libcdio-dev libvcdinfo-dev
hg clone http://hg.debian.org/hg/xine-lib/xine-lib-1.2
#You could instead download a tar ball, see next line but then you need patching or vdr-xine won´t compile
#wget http://home.vrweb.de/~rnissl/xine-lib-cvs-20090412200000.tar.bz2
tar jxvf xine-lib-cvs-20090412200000.tar.bz2
wget http://www8.mplayerhq.hu/MPlayer/releases/codecs/essential-20071007.tar.bz2
tar xivf essential-20071007.tar.bz2
mv essential-20071007 /usr/local/lib/win32
ln -s /usr/local/lib/win32 /usr/local/lib/codecs
cd xine-lib
./autogen.sh --prefix=/usr --with-external-ffmpeg --disable-dxr3 --enable-w32dll --with-w32-path=/usr/local/lib/win32
make
make install
ldconfig -v
```



```

collect2: ld returned 1 exit status
make[4]: *** [xineplug_decode_ff.la] Error 1
make[4]: Leaving directory `/usr/local/src/xine-lib/src/combined/ffmpeg'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/usr/local/src/xine-lib/src/combined/ffmpeg'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/usr/local/src/xine-lib/src/combined'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/usr/local/src/xine-lib/src'
make: *** [all-recursive] Error 1
root@htpc-desktop:/usr/local/src/xine-lib#


```

---

### Post by Sav on 2009-05-03
@Art2003
Did you patch xinelib to have vdpau support?

I tried this version:

svn co svn://jusst.de/xine-vdpau #it includes the win32 codecs

With tis package I don't need ffmpeg at all, but vdr-xine plugin doesn't compile.

I'm looking forward to know how you managed vdpau.

---

### Post by art2003 on 2009-05-03
This is the recipe:

a) Nvidia drivers 185.8.4
a) ffmpeg as per in this thread
b) xine-lib-1.2 from svn + vdpau patch for xine-lib-1.2
  in configure do use --prefix=/usr and --enable-external-ffmpeg

voila, vdpau!

---

### Post by Sav on 2009-05-03
> **art2003 said:**
> This is the recipe:

a) Nvidia drivers 185.8.4
a) ffmpeg as per in this thread
b) xine-lib-1.2 from svn + vdpau patch for xine-lib-1.2
  in configure do use --prefix=/usr and --enable-external-ffmpeg

voila, vdpau!

As Mr. Burns always says, excellent!

I tried with xine-ui and it works perfectly. Now I'll give a shot to oxine.

By the way, I don't undertstand this:
> sudo apt-get install vorbis-tools ffmpeg flac mount

ffmpeg is installed before. Could be dangerous reinstalling it from apt?

My steps in addition to your how-to are:

for ffmpeg
> 
sudo -s
apt-get install libx264-dev libmp3lame-dev # these dependencies are missing in your tutorial
./configure --enable-shared --enable-gpl --enable-postproc --enable-libmp3lame --enable-libvorbis --enable-pthreads --enable-swscale --enable-libx264 --enable-libtheora --enable-libfaac --enable-libfaad --enable-libxvid

for xinelib
> 
cd /usr/local/src
apt-get install libcdio-dev libvcdinfo-dev
hg clone [http://hg.debian.org/hg/xine-lib/xine-lib-1.2](http://hg.debian.org/hg/xine-lib/xine-lib-1.2)
wget [http://www.jusst.de/vdpau/files/xine-lib-1.2/xine-lib-1.2-vdpau-r261.diff.bz2](http://www.jusst.de/vdpau/files/xine-lib-1.2/xine-lib-1.2-vdpau-r261.diff.bz2)
bunzip2 xine-lib-1.2-vdpau-r261.diff.bz2
cd xine-lib-1.2
patch -p1 < ../xine-lib-1.2-vdpau-r261.diff
cd ..
wget [http://www8.mplayerhq.hu/MPlayer/releases/codecs/essential-20071007.tar.bz2](http://www8.mplayerhq.hu/MPlayer/releases/codecs/essential-20071007.tar.bz2)
tar xivf essential-20071007.tar.bz2
mv essential-20071007 /usr/local/lib/win32
ln -s /usr/local/lib/win32 /usr/local/lib/codecs
cd xine-lib
./autogen.sh --prefix=/usr --with-external-ffmpeg --disable-dxr3 --enable-w32dll --with-w32-path=/usr/local/lib/win32
make -j6
checkinstall --fstrans=no --install=yes --pkgname=libxine2-dev --pkgversion "1.2.svn`date +%Y%m%d`-12ubuntu3"
ldconfig -v

I used checkinstall, because it builds a deb package, so everything could be easly uninstalled.

@everyone
Don't download the vdpau patch for xinelib directly from the link above.
The manteiner keeps the patch update with the xinelib main version. Just have a look to his page:
[http://www.jusst.de/vdpau/files/xine-lib-1.2/?C=M;O=D](http://www.jusst.de/vdpau/files/xine-lib-1.2/?C=M;O=D)
and download the latest patch.

---

### Post by Sav on 2009-05-03
> **boba23 said:**
> hey art, 

thanks for the reply.
I got vdr now basically up and running. I got trouble compiling ca.c though. I am on Jaunty, and get the following error when trying to compile:

$ gcc -O -fbuiltin -fomit-frame-pointer -fPIC -shared -o ca.so ca.c -ldl
ca.c:106: error: expected â,â or â;â before â{â token
ca.c: In function âcactlâ:
ca.c:233: error: expected expression before â<â token

any ideas?

boba

try

gcc -march=pentium -mmmx -fomit-frame-pointer -fexpensive-optimizations -funroll-loops -fPIC -shared -o ca.so ca.c -ldl

---

### Post by art2003 on 2009-05-03
Thanks for your input, I have added your contributions to the first page

Yes, no point in installing ffmpeg, that was a typo.

As a front-end I found near perfection using [mms]("http://mymediasystem.org/") and [oxine]("http://oxine.sourceforge.net/")

The main menu is oxine
The entries are:
Play TV (replaced internal viewer with external script for vdpau)
DVD Menu->
           1) Use Internal DVD player (no volume control in OSS)
           2) Use MPLAYER as external DVD player (no subtitles)
Play Movie-> External script calling on MMS
Other
System
Shutdown

> **Sav said:**
> As Mr. Burns always says, excellent!

I tried with xine-ui and it works perfectly. Now I'll give a shot to oxine.



---

### Post by caladeira on 2009-05-07
Hello!

Very good post, I hope I can complete it by the weekend.

I've already started and found some problems with lirc.
With the button mapping shown in first post, I have several dead keys:

Go, Pictures, Back/Exit, Ok, Prev.Ch, FFwd, FRew, * and #

If I use the configuration file found at linuxtv.org for HVR-4000, every button works.

Here how it looks:

[PHP]

begin remote

  name  Hauppauge-HVR4000-Remote
  bits           16
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  pre_data_bits   16
  pre_data       0x8001
  gap          133325
  toggle_bit_mask 0x8001001C

      begin codes
          Power                    0x0074
          Go                       0x0161
          TV                       0x0179
          Video                    0x0189
          Music                    0x0188
          Pictures                 0x016F
          Guide                    0x016D
          Radio                    0x0181
          Up                       0x0067
          Down                     0x006C
          Left                     0x0069
          Right                    0x006A
          OK                       0x001C
          Back/Exit                0x00AE
          Menu                     0x008B
          PrevCh                   0x019C
          Mute                     0x0071
          Vol+                     0x0073
          Vol-                     0x0072
          Ch+                      0x0192
          Ch-                      0x0193
          Rec                      0x00A7
          Stop                     0x0080
          Play                     0x00CF
          Pause                    0x0077
          Rewind                   0x00A8
          Forward                  0x00D0
          Replay                   0x00A5
          Skip                     0x00A3
          1                        0x0002
          2                        0x0003
          3                        0x0004
          4                        0x0005
          5                        0x0006
          6                        0x0007
          7                        0x0008
          8                        0x0009
          9                        0x000A
          0                        0x000B
          Text                     0x0184
          Sub/CC                   0x0172
          Red                      0x018E
          Green                    0x018F
          Yellow                   0x0190
          Blue                     0x0191
      end codes

end remote

[/PHP]

---

### Post by art2003 on 2009-05-08
Thank you Caladeira for your contribution! That's the spirit, to share your findings so together we make a cracking howto that helps others

I have added your lircd.conf after changing the name of the buttons to preserve the naming I had employed so the name of the buttons match those used in the lirc application config files

Indeed I had experience odd behaviour with * and # and now I see why and should be working fine.

> **caladeira said:**
> Hello!

Very good post, I hope I can complete it by the weekend.

I've already started and found some problems with lirc.
With the button mapping shown in first post, I have several dead keys:



---

### Post by art2003 on 2009-05-08
Follow the guide, compile your own ffmpeg, xine-lib and xine-ui staying away for this from debian packages...


> **phjr said:**
> when I try to build vdr (i.e. run make in /usr/local/src/vdr) I get the error below; note that I'm running Ubuntu 9.04 64bit - anybody has i
[/code]EDIT: seems that this is a known bug in a debian package, see [http://www.mail-archive.com/debian-kernel@lists.debian.org/msg44521.html](http://www.mail-archive.com/debian-kernel@lists.debian.org/msg44521.html)

I don't know how to solve it though :-(

---

### Post by caladeira on 2009-05-08
I'm glad to help.

I've had only a few moments to test this setup, but one thing I noticed was that the speed of key repeating.
If you press a key for more than a little touch, you get multiple key presses.

I'm testing with xubuntu 9.04 that already have drivers for the nova-hd-s2.
My motherboard is a Giga-Byte GA-MA78GM-DS2H with the onboard graphics disabled and added a nvidia pcix GIGABYTE GF 8400 GS 512MB GDDR2 (GV-NX84S512HP).
CPU is an Athlon BE-2400 and 2GB DDR2 800.
As capture card, I only have a Hauppauge WinTV NOVA-HD-S2.

In the first post, you mention "wierbel".
Is this scan utility already available?

You have chose Oxine as front end.
I didn't know it, neither MMS.
But for what I've seen, MMS looks better and have been updated more recently.
Have you tested MMS?

Another difference from my setup to yours is related to the softcam.
I'm planning to use MBOX instead of CCCam.
I just haven't found yet a good tutorial.

I'll post my progress here.

---

### Post by art2003 on 2009-05-08
1)try my updated lircd.conf
No multiple key presses and all keys working...

2)wierbelscan is available, it is attached to my first post, though it scans only a handful of satellites (astra1, astra2, hotbird, sirius, 23e)
and not dvb-s2 channels. It is mainly a DVB-S and DVB-T scanner but it supports same satellites as well as per above.

Best scanner is w_scan by the same author, but for now from the command line

Here you can find some channels lists produced by w_scan:
[http://www.vdr-wiki.de/wiki/index.php/Kategorie:Channels.conf_DVBS](http://www.vdr-wiki.de/wiki/index.php/Kategorie:Channels.conf_DVBS)

I tried ubuntu 9.04 64bits and the native drivers for the nova-hd-s2 were a complete disaster, everything compiled ok but no data ever communicated between applications (vdr, w_scan) and the drivers.

The sc plugin should help you with mbox but I think you will need to edit a config file for that purpose, but sorry, never used mbox although I have heard about it.

Oxine or MMS?
I use both
Oxine as a frontend is more flexible, you can make it run any command you like, including a script that kills oxine and launches MMS for a particular task (I like MMS for playing movies from the hard drive)

Keep us updated on your progress, it is a wonderful adventure! (and a brave thing to buy hardware you don´t know it works for certain, but hopefully it will all have a happy ending)

---

### Post by Sav on 2009-05-09
> **art2003 said:**
> Thanks for your input, I have added your contributions to the first page

Yes, no point in installing ffmpeg, that was a typo.

As a front-end I found near perfection using [mms]("http://mymediasystem.org/") and [oxine]("http://oxine.sourceforge.net/")

The main menu is oxine
The entries are:
Play TV (replaced internal viewer with external script for vdpau)
DVD Menu->
           1) Use Internal DVD player (no volume control in OSS)
           2) Use MPLAYER as external DVD player (no subtitles)
Play Movie-> External script calling on MMS
Other
System
Shutdown

Using the internal player, are subtitles enabled?

---

### Post by SeanCorky on 2009-05-09
Hi,

I get the following error at the ffmpeg stage

```
./configure --prefix=/usr --enable-gpl --enable-postproc --enable-libmp3lame --enable-libvorbis --enable-pthreads --enable-libx264 --enable-libtheora --enable-libfaac --enable-libfaad --enable-libxvid
libfaac is nonfree and --enable-nonfree is not specified.

If you think configure made a mistake, make sure you are using the latest
version from SVN.  If the latest version fails, report the problem to the
ffmpeg-user@mplayerhq.hu mailing list or IRC #ffmpeg on irc.freenode.net.
Include the log file "config.err" produced by configure as this will help
solving the problem.

```

---

### Post by caladeira on 2009-05-09
Hello again.

I'm going to install w_scan.
It's not a problem being a command line.

[EDIT] I found this on the README file:
- it works *only* for cable and terrestrial DVB/ATSC, sat is removed

So it'll not work for satellite users!
I have to go for another one.

I live in Portugal and have a diseqc with: Hispasat 30W, Hotbird 13E and Astra 19.2E.

Because I've heard of some problems with 64bits versions, I've chose the 32bits.

But before I continue, I'm going to create a backup image of the partition where I've installed to. Just in case...

About the front ends, I'm a user of MythTV (Mythbuntu to be more precise).
However, the current version doesn't support DVB-S2 and to go to SVN then I have to patch lots of things...

I have to dig about mbox.
Most of my friends are switching from CCCam to mbox because of stability and much lower network traffic.

Best regards.


> **art2003 said:**
> 1)try my updated lircd.conf
No multiple key presses and all keys working...

2)wierbelscan is available, it is attached to my first post, though it scans only a handful of satellites (astra1, astra2, hotbird, sirius, 23e)
and not dvb-s2 channels. It is mainly a DVB-S and DVB-T scanner but it supports same satellites as well as per above.

Best scanner is w_scan by the same author, but for now from the command line

Here you can find some channels lists produced by w_scan:
[http://www.vdr-wiki.de/wiki/index.php/Kategorie:Channels.conf_DVBS](http://www.vdr-wiki.de/wiki/index.php/Kategorie:Channels.conf_DVBS)

I tried ubuntu 9.04 64bits and the native drivers for the nova-hd-s2 were a complete disaster, everything compiled ok but no data ever communicated between applications (vdr, w_scan) and the drivers.

The sc plugin should help you with mbox but I think you will need to edit a config file for that purpose, but sorry, never used mbox although I have heard about it.

Oxine or MMS?
I use both
Oxine as a frontend is more flexible, you can make it run any command you like, including a script that kills oxine and launches MMS for a particular task (I like MMS for playing movies from the hard drive)

Keep us updated on your progress, it is a wonderful adventure! (and a brave thing to buy hardware you don´t know it works for certain, but hopefully it will all have a happy ending)

---

### Post by art2003 on 2009-05-09
> **Sav said:**
> Using the internal player, are subtitles enabled?

Yes, using the internal oxine player, subtitles are enabled but no volume control is possible (you have to use the TV´s remote control for that)

This I believe is because /dev/mixer and /dev/mixer0 exist but are not really functional so ´hardware´ volume control fails, where ´software´ volume control works.

vdr allows for both hardware and software volume control, so no problems there.

mplayer and xine too so fine there too.

But oxine has only hardware volume control.

---

### Post by emmanneil on 2009-05-10
hi i am reading this thread with great detail, i am going through the tut , just one thing i want to ask is , you said that wierbel scan can scan for dvb-s2(HD) channels, is there any chance you could put the tut for this up ?
thanks so far

---

### Post by emmanneil on 2009-05-10
hi i have following the guide and i have got to the installing  ffmpeg but this error comes up  any idea ?

desktop:/usr/local/src/ffmpeg# ./configure --prefix=/usr --enable-gpl --enable-postproc --enable-libmp3lame --enable-libvorbis --enable-pthreads --enable-libx264 --enable-libtheora --enable-libfaac --enable-libfaad --enable-libxvid
FAAD test failed.

If you think configure made a mistake, make sure you are using the latest
version from SVN.  If the latest version fails, report the problem to the
[email]ffmpeg-user@mplayerhq.hu[/email] mailing list or IRC #ffmpeg on irc.freenode.net.
Include the log file "config.err" produced by configure as this will help
solving the problem.

---

### Post by caladeira on 2009-05-10
Hello!

I've been through this too.

I've changes a little bit the original post like this:

```

apt-get install -y libx264-dev libmp3lame-dev autoconf libtool automake pkg-config gettext liba52-0.7.4-dev libvorbis-dev zlib1g-dev libpng12-dev libx11-dev libxv-dev libasound2-dev libfaad-dev libfaac-dev libxvidcore4-dev libdts-dev
apt-get build-dep ffmpeg
svn checkout svn://svn.mplayerhq.hu/ffmpeg/trunk ffmpeg
cd ffmpeg/
./configure --prefix=/usr --enable-gpl --enable-postproc --enable-libmp3lame --enable-libvorbis --enable-pthreads --enable-libx264 --enable-libtheora --enable-libfaac --enable-libfaad --enable-libxvid --enable-nonfree
make
make install
cp ffmpeg /usr/local/bin/ffmpeg
ldconfig -v

``` 

As you can see I've added the packages "libfaad-dev libfaac-dev libxvidcore4-dev libdts-dev" and add also some options to ffmpeg "--enable-libfaac --enable-libfaad --enable-libxvid --enable-nonfree".

However, now I'm stuck in the Xine-Lib 1.2 CVS.

I get always this error when I try to make (with and without vdpau support):

```

(...)
/usr/local/src/ffmpeg/libavcodec/libxvid_rc.c:127: undefined reference to `xvid_plugin_2pass2'
/usr/local/src/ffmpeg/libavcodec/libxvid_rc.c:119: undefined reference to `xvid_plugin_2pass2'
/usr/lib/gcc/i486-linux-gnu/4.3.3/../../../../lib/libavcodec.a(libxvid_rc.o): In function `ff_xvid_rate_control_init':
/usr/local/src/ffmpeg/libavcodec/libxvid_rc.c:80: undefined reference to `xvid_plugin_2pass2'
collect2: ld returned 1 exit status
make[4]: ** [xineplug_decode_ff.la] Erro 1
make[4]: Saindo do diretÃ³rio `/usr/local/src/xine-lib-1.2/src/combined/ffmpeg'
make[3]: ** [all] Erro 2
make[3]: Saindo do diretÃ³rio `/usr/local/src/xine-lib-1.2/src/combined/ffmpeg'
make[2]: ** [all-recursive] Erro 1
make[2]: Saindo do diretÃ³rio `/usr/local/src/xine-lib-1.2/src/combined'
make[1]: ** [all-recursive] Erro 1
make[1]: Saindo do diretÃ³rio `/usr/local/src/xine-lib-1.2/src'
make: ** [all-recursive] Erro 1

```

I've also made the suggested change to "/usr/local/src/xine-lib-1.2/src/audio_dec/Makefile" without success.

Since I'm using xubuntu 9.04, I'm considering restarting all again with xubuntu 8.04

I'm just going to wait 1 day or two to see if someone have any clue.

Regards.

> **emmanneil said:**
> hi i have following the guide and i have got to the installing  ffmpeg but this error comes up  any idea ?

desktop:/usr/local/src/ffmpeg# ./configure --prefix=/usr --enable-gpl --enable-postproc --enable-libmp3lame --enable-libvorbis --enable-pthreads --enable-libx264 --enable-libtheora --enable-libfaac --enable-libfaad --enable-libxvid
FAAD test failed.

If you think configure made a mistake, make sure you are using the latest
version from SVN.  If the latest version fails, report the problem to the
[email]ffmpeg-user@mplayerhq.hu[/email] mailing list or IRC #ffmpeg on irc.freenode.net.
Include the log file "config.err" produced by configure as this will help
solving the problem.

---

### Post by emmanneil on 2009-05-10
i am using 8.04 and its no better on there too, dont waste your time on 8.04

---

### Post by art2003 on 2009-05-10
w_scan in its latest version can scan dvb-s2 
but from the terminal

[http://wirbel.htpc-forum.de/w_scan/index2.html](http://wirbel.htpc-forum.de/w_scan/index2.html)


> **emmanneil said:**
> hi i am reading this thread with great detail, i am going through the tut , just one thing i want to ask is , you said that wierbel scan can scan for dvb-s2(HD) channels, is there any chance you could put the tut for this up ?
thanks so far

---

### Post by art2003 on 2009-05-10
looks like you should try to drop --enable-xvid from your ffmpeg build
It is not needed for vdr...

> **caladeira said:**
> Hello!

I've been through this too.

I've changes a little bit the original post like this:

```

apt-get install -y libx264-dev libmp3lame-dev autoconf libtool automake pkg-config gettext liba52-0.7.4-dev libvorbis-dev zlib1g-dev libpng12-dev libx11-dev libxv-dev libasound2-dev libfaad-dev libfaac-dev libxvidcore4-dev libdts-dev
apt-get build-dep ffmpeg
svn checkout svn://svn.mplayerhq.hu/ffmpeg/trunk ffmpeg
cd ffmpeg/
./configure --prefix=/usr --enable-gpl --enable-postproc --enable-libmp3lame --enable-libvorbis --enable-pthreads --enable-libx264 --enable-libtheora --enable-libfaac --enable-libfaad --enable-libxvid --enable-nonfree
make
make install
cp ffmpeg /usr/local/bin/ffmpeg
ldconfig -v

``` 

As you can see I've added the packages "libfaad-dev libfaac-dev libxvidcore4-dev libdts-dev" and add also some options to ffmpeg "--enable-libfaac --enable-libfaad --enable-libxvid --enable-nonfree".

However, now I'm stuck in the Xine-Lib 1.2 CVS.

I get always this error when I try to make (with and without vdpau support):

```

(...)
/usr/local/src/ffmpeg/libavcodec/libxvid_rc.c:127: undefined reference to `xvid_plugin_2pass2'
/usr/local/src/ffmpeg/libavcodec/libxvid_rc.c:119: undefined reference to `xvid_plugin_2pass2'
/usr/lib/gcc/i486-linux-gnu/4.3.3/../../../../lib/libavcodec.a(libxvid_rc.o): In function `ff_xvid_rate_control_init':
/usr/local/src/ffmpeg/libavcodec/libxvid_rc.c:80: undefined reference to `xvid_plugin_2pass2'
collect2: ld returned 1 exit status
make[4]: ** [xineplug_decode_ff.la] Erro 1
make[4]: Saindo do diretÃ³rio `/usr/local/src/xine-lib-1.2/src/combined/ffmpeg'
make[3]: ** [all] Erro 2
make[3]: Saindo do diretÃ³rio `/usr/local/src/xine-lib-1.2/src/combined/ffmpeg'
make[2]: ** [all-recursive] Erro 1
make[2]: Saindo do diretÃ³rio `/usr/local/src/xine-lib-1.2/src/combined'
make[1]: ** [all-recursive] Erro 1
make[1]: Saindo do diretÃ³rio `/usr/local/src/xine-lib-1.2/src'
make: ** [all-recursive] Erro 1

```

I've also made the suggested change to "/usr/local/src/xine-lib-1.2/src/audio_dec/Makefile" without success.

Since I'm using xubuntu 9.04, I'm considering restarting all again with xubuntu 8.04

I'm just going to wait 1 day or two to see if someone have any clue.

Regards.

---

### Post by art2003 on 2009-05-10
[http://edafe.org/vdr/w_scan/](http://edafe.org/vdr/w_scan/)

Here is a howto for w_scan

---

### Post by emmanneil on 2009-05-10
thanks for the link but i am having problems with the installation of the following also, i can get the card working and i have just u8sed the link that you gave me to get the Hdchannels and its great, can you help in this area , i get this error
hi after getting a bit further along the line i come across this problem , this is when i am ready to make or make install the VDR
 
g++: tinystr.c: No such file or directory
g++: tinyxml.c: No such file or directory
g++: tinyxmlerror.c: No such file or directory
g++: tinyxmlparser.c: No such file or directory
g++: submenu.c: No such file or directory
make: *** Deleting file `.dependencies'
g++ -g -O2 -Wall -Woverloaded-virtual -Wno-parentheses -c -DUSE_SETUP -DREMOTE_KBD -DLIRC_DEVICE=\"/dev/lircd\" -DRCU_DEVICE=\"/dev/input/ttyS1\" -D_GNU_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_LARGEFILE64_SOURCE -DVIDEODIR=\"/media/video/vdr\" -DCONFDIR=\"/etc/vdr\" -DPLUGINDIR=\"/usr/lib/vdr/plugins\" -DLOCDIR=\"/usr/share/locale\" -I/usr/include/freetype2 -I/usr/local/src/s2-liplianin/linux/include menu.c
In file included from menu.c:10:
menu.h:22:21: error: submenu.h: No such file or directory
In file included from menu.c:10:
menu.h:87: error: ‘cSubMenu’ does not name a type
osdbase.h: In constructor ‘cMenuMain::cMenuMain(eOSState)’:
osdbase.h:107: error: ‘cOsdMenu* cOsdMenu::subMenu’ is private
menu.c:4010: error: within this context
menu.c:4010: error: request for member ‘LoadXml’ in ‘((cMenuMain*)this)->cMenuMain::<anonymous>.cOsdMenu::subMenu’, which is of non-class type ‘cOsdMenu*’
menu.c: In member function ‘void cMenuMain::Set(int)’:
menu.c:4140: error: ‘cSubMenuNode’ was not declared in this scope
menu.c:4140: error: ‘node’ was not declared in this scope
osdbase.h:107: error: ‘cOsdMenu* cOsdMenu::subMenu’ is private
menu.c:4140: error: within this context
menu.c:4140: error: request for member ‘GetMenuTree’ in ‘((cMenuMain*)this)->cMenuMain::<anonymous>.cOsdMenu::subMenu’, which is of non-class type ‘cOsdMenu*’
osdbase.h:107: error: ‘cOsdMenu* cOsdMenu::subMenu’ is private
menu.c:4140: error: within this context
menu.c:4140: error: request for member ‘GetMenuTree’ in ‘((cMenuMain*)this)->cMenuMain::<anonymous>.cOsdMenu::subMenu’, which is of non-class type ‘cOsdMenu*’
menu.c:4141: error: ‘cSubMenuNode’ is not a class or namespace
menu.c:4141: error: expected `;' before ‘type’
menu.c:4142: error: ‘type’ was not declared in this scope
menu.c:4142: error: ‘cSubMenuNode’ is not a class or namespace
menu.c:4151: error: ‘cSubMenuNode’ is not a class or namespace
osdbase.h:107: error: ‘cOsdMenu* cOsdMenu::subMenu’ is private
menu.c:4152: error: within this context
menu.c:4152: error: request for member ‘GetMenuSuffix’ in ‘((cMenuMain*)this)->cMenuMain::<anonymous>.cOsdMenu::subMenu’, which is of non-class type ‘cOsdMenu*’
menu.c:4160: error: ‘cSubMenuNode’ is not a class or namespace
menu.c:4160: error: ‘cSubMenuNode’ is not a class or namespace
menu.c:4168: error: ‘cSubMenuNode’ is not a class or namespace
osdbase.h:107: error: ‘cOsdMenu* cOsdMenu::subMenu’ is private
menu.c:4184: error: within this context
menu.c:4184: error: request for member ‘GetMenuSuffix’ in ‘((cMenuMain*)this)->cMenuMain::<anonymous>.cOsdMenu::subMenu’, which is of non-class type ‘cOsdMenu*’
osdbase.h:107: error: ‘cOsdMenu* cOsdMenu::subMenu’ is private
menu.c:4188: error: within this context
menu.c:4188: error: request for member ‘GetMenuSuffix’ in ‘((cMenuMain*)this)->cMenuMain::<anonymous>.cOsdMenu::subMenu’, which is of non-class type ‘cOsdMenu*’
osdbase.h: In member function ‘bool cMenuMain::Update(bool)’:
osdbase.h:107: error: ‘cOsdMenu* cOsdMenu::subMenu’ is private
menu.c:4261: error: within this context
menu.c:4261: error: request for member ‘isTopMenu’ in ‘((cMenuMain*)this)->cMenuMain::<anonymous>.cOsdMenu::subMenu’, which is of non-class type ‘cOsdMenu*’
osdbase.h:107: error: ‘cOsdMenu* cOsdMenu::subMenu’ is private
menu.c:4266: error: within this context
menu.c:4266: error: request for member ‘isTopMenu’ in ‘((cMenuMain*)this)->cMenuMain::<anonymous>.cOsdMenu::subMenu’, which is of non-class type ‘cOsdMenu*’
osdbase.h:107: error: ‘cOsdMenu* cOsdMenu::subMenu’ is private
menu.c:4289: error: within this context
menu.c:4289: error: request for member ‘GetParentMenuTitel’ in ‘((cMenuMain*)this)->cMenuMain::<anonymous>.cOsdMenu::subMenu’, which is of non-class type ‘cOsdMenu*’
osdbase.h: In member function ‘virtual eOSState cMenuMain::ProcessKey(eKeys)’:
osdbase.h:107: error: ‘cOsdMenu* cOsdMenu::subMenu’ is private
menu.c:4470: error: within this context
menu.c:4470: error: request for member ‘Up’ in ‘((cMenuMain*)this)->cMenuMain::<anonymous>.cOsdMenu::subMenu’, which is of non-class type ‘cOsdMenu*’
menu.c:4538: error: ‘cSubMenuNode’ was not declared in this scope
menu.c:4538: error: ‘node’ was not declared in this scope
osdbase.h:107: error: ‘cOsdMenu* cOsdMenu::subMenu’ is private
menu.c:4538: error: within this context
menu.c:4538: error: request for member ‘GetNode’ in ‘((cMenuMain*)this)->cMenuMain::<anonymous>.cOsdMenu::subMenu’, which is of non-class type ‘cOsdMenu*’
menu.c:4542: error: ‘cSubMenuNode’ is not a class or namespace
osdbase.h:107: error: ‘cOsdMenu* cOsdMenu::subMenu’ is private
menu.c:4546: error: within this context
menu.c:4546: error: request for member ‘Down’ in ‘((cMenuMain*)this)->cMenuMain::<anonymous>.cOsdMenu::subMenu’, which is of non-class type ‘cOsdMenu*’
menu.c:4549: error: ‘cSubMenuNode’ is not a class or namespace
osdbase.h:107: error: ‘cOsdMenu* cOsdMenu::subMenu’ is private
menu.c:4556: error: within this context
menu.c:4556: error: request for member ‘ExecuteCommand’ in ‘((cMenuMain*)this)->cMenuMain::<anonymous>.cOsdMenu::subMenu’, which is of non-class type ‘cOsdMenu*’
menu.c:4562: error: ‘cSubMenuNode’ is not a class or namespace
menu.c:4570: error: ‘cExecCmdThread’ was not declared in this scope
menu.c:4570: error: ‘execcmd’ was not declared in this scope
menu.c:4570: error: expected type-specifier before ‘cExecCmdThread’
menu.c:4570: error: expected `;' before ‘cExecCmdThread’
make: *** [menu.o] Error 1 			

this happens in this stage
cd /usr/local/src
apt-get install libfreetype6-dev libfontconfig1-dev libjpeg62-dev libcap-dev libncurses5-dev libncursesw5-dev liba52-0.7.4-dev libasound2-dev
wget [ftp://ftp.cadsoft.de/pub/people/kls/vdr/Developer/vdr-1.7.7.tar.bz2](ftp://ftp.cadsoft.de/pub/people/kls/vdr/Developer/vdr-1.7.7.tar.bz2)
tar xivf vdr-1.7.7.tar.bz2
ln -s vdr-1.7.7 vdr
wget [http://www.zulu-entertainment.de/page/klick.php?d=VDR+Extensions+Patch](http://www.zulu-entertainment.de/page/klick.php?d=VDR+Extensions+Patch)
tar xivf VDR-Extensions-Patch-72.tar.bz2
cd VDR-Extentions-Patch-72
cd ../vdr
patch -p1 < ../VDR-Extensions-Patch-72/vdr-1.7.7_extensions.diff
#Next patch is optional but I am using it and seems to be fine and indeed speed things up a little bit...
#patch -p1 < ../VDR-Extensions-Patch-72/extras/vdr-1.7.5-ext_speedup.diff
# Next line is just in case you just updated your kernel,do not worry if you get an error saying ´files are the same´
sudo cp /usr/src/linux-headers-`uname -r`/include/linux/compiler.h /usr/local/src/s2-liplianin/linux/include/linux/compiler.h 
sudo gedit /usr/local/src/vdr/Make.config

sudo -s
mkdir -p /media/video/vdr
mkdir -p /usr/lib/vdr/plugins
mkdir -p /usr/lib/vdr/scripts
mkdir -p /etc/vdr/plugins
make
make install
cp -a svdrpsend.pl /usr/bin
cp *.conf /etc/vdr/




any help would be appreciated

---

### Post by art2003 on 2009-05-10
looks like you don´t have libtinyxml...

[http://sourceforge.net/project/showfiles.php?group_id=13559](http://sourceforge.net/project/showfiles.php?group_id=13559)

---

### Post by caladeira on 2009-05-10
> **art2003 said:**
> looks like you should try to drop --enable-xvid from your ffmpeg build
It is not needed for vdr...

Well, I've removed that and now I get a diferente error:

```
/usr/lib/gcc/i486-linux-gnu/4.3.3/../../../../lib/libavcodec.a(libx264.o): In function `encode_nals':
/usr/local/src/ffmpeg/libavcodec/libx264.c:60: undefined reference to `x264_nal_encode'
collect2: ld returned 1 exit status
make[4]: ** [xineplug_decode_ff.la] Erro 1
make[4]: Saindo do diretÃ³rio `/usr/local/src/xine-lib-1.2/src/combined/ffmpeg'
make[3]: ** [all] Erro 2
make[3]: Saindo do diretÃ³rio `/usr/local/src/xine-lib-1.2/src/combined/ffmpeg'
make[2]: ** [all-recursive] Erro 1
make[2]: Saindo do diretÃ³rio `/usr/local/src/xine-lib-1.2/src/combined'
make[1]: ** [all-recursive] Erro 1
make[1]: Saindo do diretÃ³rio `/usr/local/src/xine-lib-1.2/src'
make: ** [all-recursive] Erro 1

```

If I disable libx264, I get other error!

Any idea?

Thanks.

---

### Post by caladeira on 2009-05-10
> **art2003 said:**
> [http://edafe.org/vdr/w_scan/](http://edafe.org/vdr/w_scan/)

Here is a howto for w_scan

I'm in a bad weekend!

w_scan doesn't compile too!

Following the guide, when I reach to the make, I get this error:

```

root@htpc-desktop:/usr/local/src/w_scan# make
cc -MD -g -Wall -O2 --static -c scan.c -o scan.o
scan.c: In function âset_frontendâ:
scan.c:1552: error: âFE_CAN_2G_MODULATIONâ undeclared (first use in this function)
scan.c:1552: error: (Each undeclared identifier is reported only once
scan.c:1552: error: for each function it appears in.)
scan.c: In function âinitial_tuneâ:
scan.c:2039: error: âFE_CAN_2G_MODULATIONâ undeclared (first use in this function)
scan.c: In function âdevice_is_preferredâ:
scan.c:2233: error: âFE_CAN_2G_MODULATIONâ undeclared (first use in this function)
scan.c: In function âmainâ:
scan.c:3015: error: âFE_CAN_2G_MODULATIONâ undeclared (first use in this function)
make: ** [scan.o] Erro 1

```

Thanks for your attention.

---

### Post by boba23 on 2009-05-11
Hey art,

got VDR basically working following your guide, and well ... adding a few other guides ;-) Anyway. Do you have any advice or a little small addon howto, on how to get the best picture quality out of xineliboutput as a frontend? 
I was kinda disappointed with the picture that I got via HDMI on my Panasonic 46PZ80 1080p Panel. Compared to the Scart Output of my years old DBOX2 Cable Receiver, the VDR picture is really noisy plus I got very light stuttering. Gotta say that 95% of the content I tried is of course 576i PAL. So I guess I need to teach VDR first to output an interlaced signal, right? 
Anyway, it would be great if you could point me into the right direction. Been looking for xineliboutput howtos regarding picture quality/interlacing etc. but couldn't find anything really useful.

thanks,

boba

---

### Post by emmanneil on 2009-05-11
@art2003

you say that i need to drop the --enable-libxvid but this is not the error the error is FFAD when i put this line in

./configure --prefix=/usr --enable-gpl --enable-postproc --enable-libmp3lame --enable-libvorbis --enable-pthreads --enable-libx264 --enable-libtheora --enable-libfaac --enable-libfaad --enable-libxvid

when i do remove the --enable- libxvid it has the FFAD Error and when i9 remove the FFAD part it has this error

./configure --prefix=/usr --enable-gpl --enable-postproc --enable-libmp3lame --enable-libvorbis --enable-pthreads --enable-libx264 --enable-libtheora --enable-libfaac
libfaac is nonfree and --enable-nonfree is not specified.

are you able to point me in the right direction ?

Thanks

---

### Post by art2003 on 2009-05-11
try simply this

./configure --prefix=/usr --enable-gpl --enable-postproc --enable-libmp3lame --enable-libvorbis --enable-pthreads --enable-libx264


> **emmanneil said:**
> @art2003

you say that i need to drop the --enable-libxvid but this is not the error the error is FFAD when i put this line in

./configure --prefix=/usr --enable-gpl --enable-postproc --enable-libmp3lame --enable-libvorbis --enable-pthreads --enable-libx264 --enable-libtheora --enable-libfaac --enable-libfaad --enable-libxvid

when i do remove the --enable- libxvid it has the FFAD Error and when i9 remove the FFAD part it has this error

./configure --prefix=/usr --enable-gpl --enable-postproc --enable-libmp3lame --enable-libvorbis --enable-pthreads --enable-libx264 --enable-libtheora --enable-libfaac
libfaac is nonfree and --enable-nonfree is not specified.

are you able to point me in the right direction ?

Thanks

---

### Post by emmanneil on 2009-05-11
hi i cleaned it  and started again as i think i went wrong somewhere all went ok until this error now i know i need what it says in the error but i dont know how to do it any help would be great

 
can any one help ?
 
root@tefal-desktop:/usr/local/src/vdr-1.7.0# make
In file included from audio.c:12:
dvbdevice.h:19:2: error: #error VDR requires Linux DVB driver API version 5.0!
In file included from dvbdevice.c:10:
dvbdevice.h:19:2: error: #error VDR requires Linux DVB driver API version 5.0!
In file included from dvbosd.c:15:
dvbdevice.h:19:2: error: #error VDR requires Linux DVB driver API version 5.0!
In file included from eitscan.c:13:
dvbdevice.h:19:2: error: #error VDR requires Linux DVB driver API version 5.0!
In file included from vdr.c:45:
dvbdevice.h:19:2: error: #error VDR requires Linux DVB driver API version 5.0!
make: *** Deleting file `.dependencies'
g++ -g -O2 -Wall -Woverloaded-virtual -Wno-parentheses -c -DREMOTE_KBD -DVDR_USER=\"root\" -DLIRC_DEVICE=\"/dev/lircd\" -DRCU_DEVICE=\"/dev/ttyS1\" -D_GNU_SOURCE -DVIDEODIR=\"/media/video\" -DCONFDIR=\"/etc/vdr\" -DPLUGINDIR=\"/usr/lib/vdr/plugins\" -DLOCDIR=\"/usr/share/locale\" -I/usr/include/freetype2 -I/usr/local/src/s2-liplianin/linux/include audio.c
In file included from audio.c:12:
dvbdevice.h:19:2: error: #error VDR requires Linux DVB driver API version 5.0!
In file included from audio.c:12:
dvbdevice.h:38: error: ‘fe_delivery_system’ does not name a type
make: *** [audio.o] Error

---

### Post by art2003 on 2009-05-12
what does 
uname -r

show?

---

### Post by emmanneil on 2009-05-12
tefal@tefal-desktop:/dev/dvb/adapter0$ uname -r
2.6.24-24-generic

---

### Post by emmanneil on 2009-05-13
i have managed to get it all done, onlt two things that dont seem to work, no errors just i can not create the Symbolic link for wireelscan

this part

# Next line verifies the plugin is in its place it if shows no file then copy it
ls /usr/lib/vdr/plugins/libvdr-wirbelscan.so.1.7.7

---

### Post by art2003 on 2009-05-13
that's an easy one... the plugin has to be copied manually to its place

sudo cp /usr/local/src/vdr/PLUGINS/src/wirbelscan/libvdr-wirbelscan.so /usr/lib/vdr/plugins/libvdr-wirbelscan.so.1.7.7


> **emmanneil said:**
> i have managed to get it all done, onlt two things that dont seem to work, no errors just i can not create the Symbolic link for wireelscan

this part

# Next line verifies the plugin is in its place it if shows no file then copy it
ls /usr/lib/vdr/plugins/libvdr-wirbelscan.so.1.7.7

---

### Post by emmanneil on 2009-05-13
thanks i will try it, [I]oh i when i reboot this is doing the autoboot part , it does not open the oxine 
what i am trying to say is i want to watch the TV and as far as i understand it, with the oxine part and the bit under this , it should open up when i start it up , but mine does not
any hints ?
Ps
thanks for your help so far, it is a good tut, just need the right things in place to compile everything
:P
[/I]

---

### Post by art2003 on 2009-05-13
for oxine to run on startup, simplest way is from X (Gnome, KDE or xfce) go system preferences, autostart or something like that
and have a oxine run automatically when you login

> **emmanneil said:**
> thanks i will try it, [I]oh i when i reboot this is doing the autoboot part , it does not open the oxine 
what i am trying to say is i want to watch the TV and as far as i understand it, with the oxine part and the bit under this , it should open up when i start it up , but mine does not
any hints ?
Ps
thanks for your help so far, it is a good tut, just need the right things in place to compile everything
:P
[/I]

---

### Post by emmanneil on 2009-05-13
yeah i did that auto start part of the tut and i added myself as a tv user etc but it wont start for some reason, i can get my card to work in kaffeine and it picks up channels although not S2 ones and i am looking into to how to get Cccam to clear my subscription using CCcam, dunno why yet, but what i want in the end of all this is to have a dvb-s/s2 card which can clear my channels using CCcam with the card that i have, and with the possibility of recording some channels

---

### Post by art2003 on 2009-05-13
run this
cat /etc/sudoers

it should look like this:
(if it doesn't run sudo visudo and make it be like that)
you know it is ok when you can type sudo -s from a terminal and become root without typing a password


# User privilege specification
#root	ALL=(ALL) ALL

# Uncomment to allow members of group sudo to not need a password
# (Note that later entries override this, so you might need to move
# it further down)
%admin ALL=NOPASSWD: ALL

# Members of the admin group may gain root privileges
#%admin ALL=(ALL) ALL

---

### Post by emmanneil on 2009-05-13
yeah it is like that is visudo with the # removed , i have rebuilt it again in case i missed anything which i dont think i did but i will make sure, just on more thing do i need all of these as it does not work with them all in there
./configure --prefix=/usr --enable-gpl --enable-postproc --enable-libmp3lame --enable-libvorbis --enable-pthreads --enable-libx264 --enable-libtheora --enable-libfaac --enable-libfaad --enable-libxvid

---

### Post by art2003 on 2009-05-14
running sudo visudo

the only line you actually need there is
%admin ALL=NOPASSWD: ALL

exactly like above
try to run sudo oxine from the terminal
if you are asked for a password, then it won't work automatically even if you add it to autostart programs, run sudo visudo 

and for ffmpeg you need only
./configure --prefix=/usr --enable-postproc --enable-libmp3lame --enable-pthreads --enable-libx264 

good luck!


> **emmanneil said:**
> yeah it is like that is visudo with the # removed , i have rebuilt it again in case i missed anything which i dont think i did but i will make sure, just on more thing do i need all of these as it does not work with them all in there
./configure --prefix=/usr --enable-gpl --enable-postproc --enable-libmp3lame --enable-libvorbis --enable-pthreads --enable-libx264 --enable-libtheora --enable-libfaac --enable-libfaad --enable-libxvid

---

### Post by emmanneil on 2009-05-14
hi i am doing it as per your instructions, 3rd time lucky now,

i am going to stop at every point unless i know what to do, here is the error i get at this point, any ideas
Thanks once AGAIN! 

root@tefal-desktop:/usr/local/src# cd ffmpeg/
root@tefal-desktop:/usr/local/src/ffmpeg# ./configure --prefix=/usr --enable-postproc --enable-libmp3lame --enable-pthreads --enable-libx264 
libx264 is gpl and --enable-gpl is not specified.

so i added 

./configure --prefix=/usr --enable-postproc --enable-libmp3lame --enable-pthreads --enable-libx264 --enable-gpl

and this came uproot@tefal-desktop:/usr/local/src/ffmpeg# ./configure --prefix=/usr --enable-postproc --enable-libmp3lame --enable-pthreads --enable-libx264 --enable-gpl
ERROR: libx264 version must be >= 0.65

uname -r is

root@tefal-desktop:/usr/local/src/ffmpeg# uname -r
2.6.27-14-generic

---

### Post by art2003 on 2009-05-14
try sudo apt-get install libx264-dev
and run again:
./configure --prefix=/usr --enable-postproc --enable-libmp3lame --enable-pthreads --enable-libx264 --enable-gpl

Let me know how it goes

If you already have it installed but the ubuntu repo version is not new enough your choices are:

a) get an older ffmpeg that doesn't have such a high requirement for libx264
b) remove the --enable-libx264 and live with it
c) download libx264.tar.gz and compile that by hand (it is easy)
d) edit the ffmpeg Makefile so that it tolerates a lower version of libx264, this last is dangerous

> **emmanneil said:**
> hi i am doing it as per your instructions, 3rd time lucky now,

i am going to stop at every point unless i know what to do, here is the error i get at this point, any ideas
Thanks once AGAIN! 



and this came uproot@tefal-desktop:/usr/local/src/ffmpeg# ./configure --prefix=/usr --enable-postproc --enable-libmp3lame --enable-pthreads --enable-libx264 --enable-gpl
ERROR: libx264 version must be >= 0.65

uname -r is

root@tefal-desktop:/usr/local/src/ffmpeg# uname -r
2.6.27-14-generic

---

### Post by emmanneil on 2009-05-14
Hi thanks, i got the libx264 installed this from here 

[ftp://ftp.videolan.org/pub/videolan/x264/snapshots/](ftp://ftp.videolan.org/pub/videolan/x264/snapshots/)
then did cd /ffmpeg/x264 etc etc
./configure --enable-shared
make
make install
ldconfig
 but after i did the ./configure --enable -shared it still said the same error so i removed this from the ./configure part and it did the make bit ok

---

### Post by emmanneil on 2009-05-14
right this is where i am now
i got to the end , with a bit of luck and searching the net for how to install things like x264 but i am at the end and i get more than last time but still errors here they are
any ideas ?

[2009-05-14 20:23:28] [        oxine.c: 697]  INFO:     oxine version: 0.7.1
[2009-05-14 20:23:28] [        oxine.c: 698]  INFO:  xine-lib version: 1.1.90hg
[2009-05-14 20:23:28] [        oxine.c: 699]  INFO:          language: en_US.UTF-8
[2009-05-14 20:23:28] [        oxine.c: 700]  INFO:           codeset: UTF-8
[2009-05-14 20:23:28] [    scheduler.c:  72]  INFO: Successfully started scheduler thread.
[2009-05-14 20:23:28] [          odk.c:1592] ERROR: Failed to create window using video driver 'vidix'!
[2009-05-14 20:23:28] [      odk_x11.c: 405]  INFO: Found 1 Xinerama screens:
[2009-05-14 20:23:28] [      odk_x11.c: 410]  INFO:     screen[ 0]: 1024x768, +0+0
[2009-05-14 20:23:28] [      odk_x11.c: 214]  INFO: The current window manager supports 'Extended Window Manager Hints'.
[2009-05-14 20:23:29] [      odk_osd.c:2163]  INFO: The current video driver supports unscaled OSD!
[2009-05-14 20:23:29] [     odk_lirc.c: 134]  WARN: Could not find /home/tefal/.oxine/lircrc, trying to use default configuration file /usr/share/oxine/lircrc.
[2009-05-14 20:23:29] [     odk_lirc.c:  69]  INFO: Successfully started the LIRC input plugin.
[2009-05-14 20:23:29] [     menulist.c: 316]  INFO: Loading menu file '/home/tefal/.oxine/mainmenu.xml'...
[2009-05-14 20:23:29] [    xmlparser.c: 200] ERROR: Lexer error.
[2009-05-14 20:23:29] [     menulist.c: 281] ERROR: Parsing '/home/tefal/.oxine/mainmenu.xml' failed!
[2009-05-14 20:23:29] [     menulist.c: 316]  INFO: Loading menu file '/usr/share/oxine/skins/oxinetic/mainmenu.xml'...
[2009-05-14 20:23:29] [          odk.c: 965]  INFO:     main MRL: '/usr/share/oxine/skins/oxinetic/backgrounds/menu_main_music.png'
[2009-05-14 20:23:29] [          odk.c: 966]  INFO: subtitle MRL: 'no subtitle'
[2009-05-14 20:23:29] [          odk.c:1000] ERROR: Could not open '/usr/share/oxine/skins/oxinetic/backgrounds/menu_main_music.png': Could not find demuxer plugin!
[2009-05-14 20:23:29] [    utils_gui.c: 200] ERROR: Could not open or play menu background image!
[2009-05-14 20:23:29] [    utils_gui.c: 202] FATAL: Please make sure that your version of xine-lib supports playback of PNG files.
[2009-05-14 20:23:29] [    utils_gui.c: 202] FATAL: A fatal error occurred! Printing backtrace:
[2009-05-14 20:23:29] [    utils_gui.c: 202] FATAL:      oxine(_log+0x123) [0x805bd53]
[2009-05-14 20:23:29] [    utils_gui.c: 202] FATAL:      oxine(show_menu_background+0x160) [0x8084a00]
[2009-05-14 20:23:29] [    utils_gui.c: 202] FATAL:      oxine [0x807b13a]
[2009-05-14 20:23:29] [    utils_gui.c: 202] FATAL:      oxine [0x807badf]
[2009-05-14 20:23:29] [    utils_gui.c: 202] FATAL:      oxine(otk_draw+0xb2) [0x8077f82]
[2009-05-14 20:23:29] [    utils_gui.c: 202] FATAL:      oxine(show_user_interface+0x1b) [0x8084b4b]
[2009-05-14 20:23:29] [    utils_gui.c: 202] FATAL:      oxine [0x80540d0]
[2009-05-14 20:23:29] [    utils_gui.c: 202] FATAL:      oxine(oxine_event_handler+0x2d9) [0x8055349]
[2009-05-14 20:23:29] [    utils_gui.c: 202] FATAL:      oxine(odk_oxine_event_send+0x3c) [0x806f80c]
[2009-05-14 20:23:29] [    utils_gui.c: 202] FATAL:      oxine(main+0x1906) [0x807fdc6]
Aborted

---

### Post by art2003 on 2009-05-14
I take it you are using my .deb?
It was compiled for ubuntu 8.10 may or may not work for you.

try this
sudo apt-get build-dep oxine
and in ~/.oxine/config
change vidix to xv
finally from a terminal run sudo oxine

If that fails download oxine and compile with --enable-vdr

> **emmanneil said:**
> right this is where i am now
i got to the end , with a bit of luck and searching the net for how to install things like x264 but i am at the end and i get more than last time but still errors here they are
any ideas ?

[2009-05-14 20:23:29] [    utils_gui.c: 202] FATAL: Please make sure that your version of xine-lib supports playback of PNG files.
[2009-05-14 20:23:29] [    utils_gui.c: 202] FATAL: A fatal error occurred! Printing backtrace:
[2009-05-14 20:23:29] [    utils_gui.c: 202] FATAL:      oxine(_log+0x123) [0x805bd53]
[2009-05-14 20:23:29] [    utils_gui.c: 202] FATAL:      oxine(show_menu_background+0x160) [0x8084a00]
[2009-05-14 20:23:29] [    utils_gui.c: 202] FATAL:      oxine [0x807b13a]
[2009-05-14 20:23:29] [    utils_gui.c: 202] FATAL:      oxine [0x807badf]
[2009-05-14 20:23:29] [    utils_gui.c: 202] FATAL:      oxine(otk_draw+0xb2) [0x8077f82]
[2009-05-14 20:23:29] [    utils_gui.c: 202] FATAL:      oxine(show_user_interface+0x1b) [0x8084b4b]
[2009-05-14 20:23:29] [    utils_gui.c: 202] FATAL:      oxine [0x80540d0]
[2009-05-14 20:23:29] [    utils_gui.c: 202] FATAL:      oxine(oxine_event_handler+0x2d9) [0x8055349]
[2009-05-14 20:23:29] [    utils_gui.c: 202] FATAL:      oxine(odk_oxine_event_send+0x3c) [0x806f80c]
[2009-05-14 20:23:29] [    utils_gui.c: 202] FATAL:      oxine(main+0x1906) [0x807fdc6]
Aborted

---

### Post by Mr Cool Span on 2009-05-25
First of all I like to say than x for this great guide
But I have rand in to some problems and I relay like to have some help.

I have fresh Ubuntu 8.10 Intrepid install and I have update the kernel to 2.6.29.4-ultimate, be cures it have the support for my dvb-s cards, Hauppauge Hvr 4000 and  Firedtv -s2. wits work great in Kaffeine. 
1)skip the firmware and driver set-up
2)skip  the Audio chapter to
3)I follow the vdr 1.7.7 set-up steps, but when I came to the compile I need-et to install the liplianin ore ells I cut not compile
4)download and compile VDR 1.7.7 with Extensions-Patch-71[/b]
5)did the Cccam thing
6)plug-ins/skins 
Femon - Signal Information plugin
Streamdev plugin
Enigma skin
sc TRUNK - softcam plugin 
CCcam info or ecm.info
had to install Skin Reel - VDR Skin
WIRBEL SCAN
XINE - VDR Xine plugin
7)create a sample menu configuration file
8)create the Cccam start thing

okay I thing that's it
the problem is when I type sudo /etc/init.d/vdr start I get this
:~$ vdr-xine: error: couldn't open '/etc/vdr/plugins/xine/noSignal4x3.mpg'!

vdr-xine: error: couldn't open '/etc/vdr/plugins/xine/noSignal.mpg'!

vdr-xine: error: couldn't open '/etc/vdr/plugins/xine/noSignal16x9.mpg'!

vdr-xine: error: couldn't open '/etc/vdr/plugins/xine/noSignal.mpg'!


I realy hope you guys/girls can help me

Ps I also new in linux

---

### Post by penove on 2009-05-25
```

VDR_source
wget http://heanet.dl.sourceforge.net/sourceforge/xineliboutput/vdr-xineliboutput-1.0.3.tar.bz2
tar xivf vdr-xineliboutput-1.0.3.tar.bz2
mv xineliboutput-1.0.3 xineliboutput
cd xineliboutput
make
make install
[B]mkdir -p /etc/vdr/plugins/xineliboutput
cp *.mpg /etc/vdr/plugins/xineliboutput/[/B]
cd ../../../
make plugins
make install

```

You must copy mpg files for xinelibout


:D

---

### Post by art2003 on 2009-05-26
Sounds like you are almost there:

You are using xine plugin right? (that's what I use)
so try:
cd /usr/local/src/vdr/PLUGINS/xine/data
mkdir -p /etc/vdr/plugins/xine/
cp *.mpg /etc/vdr/plugins/xine/


> **Mr Cool Span said:**
> First of all I like to say than x for this great guide
But I have rand in to some problems and I relay like to have some help.
okay I thing that's it
the problem is when I type sudo /etc/init.d/vdr start I get this
:~$ vdr-xine: error: couldn't open '/etc/vdr/plugins/xine/noSignal4x3.mpg'!

vdr-xine: error: couldn't open '/etc/vdr/plugins/xine/noSignal.mpg'!

vdr-xine: error: couldn't open '/etc/vdr/plugins/xine/noSignal16x9.mpg'!

vdr-xine: error: couldn't open '/etc/vdr/plugins/xine/noSignal.mpg'!


I realy hope you guys/girls can help me

Ps I also new in linux

---

### Post by Mr Cool Span on 2009-05-26
> **penove said:**
> ```

VDR_source
wget http://heanet.dl.sourceforge.net/sourceforge/xineliboutput/vdr-xineliboutput-1.0.3.tar.bz2
tar xivf vdr-xineliboutput-1.0.3.tar.bz2
mv xineliboutput-1.0.3 xineliboutput
cd xineliboutput
make
make install
[B]mkdir -p /etc/vdr/plugins/xineliboutput
cp *.mpg /etc/vdr/plugins/xineliboutput/[/B]
cd ../../../
make plugins
make install

```

You must copy mpg files for xinelibout


:D

no nop cant make it :(


root@htpc:/usr/local/src/vdr/xineliboutput# make
sed: kan ikke læse ../../../config.h: No such file or directory
Makefile:157: ********************************************************
Makefile:158: VDR not detected ! VDR plugin will not be compiled.     
Makefile:159: ********************************************************
sed: kan ikke læse ../../../config.h: No such file or directory
Makefile:157: ********************************************************
Makefile:158: VDR not detected ! VDR plugin will not be compiled.     
Makefile:159: ********************************************************
cc -O3 -pipe -Wall -fPIC -g    -c -D_GNU_SOURCE -DPLUGIN_NAME_I18N='"xineliboutput"' -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -DXINELIBOUTPUT_VERSION='"1.0.3"' -DHAVE_XRENDER=1 -DHAVE_XDPMS=1 -DHAVE_XINERAMA=1 -DUSE_ICONV=1 -Wall -DFE_STANDALONE -I../../../include  xine_sxfe_frontend.c -o xine_sxfe_frontend_standalone.o
In file included from xine_sxfe_frontend.c:204:
xine_frontend.c: In function ‘fe_frame_output_cb’:
xine_frontend.c:288: advarsel: ignoring return value of ‘system’, declared with attribute warn_unused_result
xine_frontend.c: In function ‘fe_xine_open’:
xine_frontend.c:728: advarsel: ignoring return value of ‘asprintf’, declared with attribute warn_unused_result
xine_frontend.c:749: advarsel: ignoring return value of ‘asprintf’, declared with attribute warn_unused_result
In file included from xine_frontend_main.c:56,
                 from xine_frontend.c:1665,
                 from xine_sxfe_frontend.c:204:
xine_frontend_lirc.c: In function ‘lirc_receiver_thread’:
xine_frontend_lirc.c:105: advarsel: ignoring return value of ‘nice’, declared with attribute warn_unused_result
In file included from xine_frontend.c:1665,
                 from xine_sxfe_frontend.c:204:
xine_frontend_main.c: In function ‘kbd_receiver_thread’:
xine_frontend_main.c:143: advarsel: ignoring return value of ‘system’, declared with attribute warn_unused_result
xine_frontend_main.c:144: advarsel: ignoring return value of ‘system’, declared with attribute warn_unused_result
xine_frontend_main.c:193: advarsel: ignoring return value of ‘system’, declared with attribute warn_unused_result
xine_frontend_main.c: In function ‘kbd_stop’:
xine_frontend_main.c:258: advarsel: ignoring return value of ‘system’, declared with attribute warn_unused_result
xine_frontend_main.c: In function ‘main’:
xine_frontend_main.c:550: advarsel: ignoring return value of ‘asprintf’, declared with attribute warn_unused_result
xine_frontend_main.c:553: advarsel: ignoring return value of ‘asprintf’, declared with attribute warn_unused_result
xine_frontend_main.c:566: advarsel: ignoring return value of ‘asprintf’, declared with attribute warn_unused_result
xine_sxfe_frontend.c: In function ‘set_above’:
xine_sxfe_frontend.c:312: advarsel: ignoring return value of ‘asprintf’, declared with attribute warn_unused_result
cc -O3 -pipe -Wall -fPIC -g    -c -D_GNU_SOURCE -DPLUGIN_NAME_I18N='"xineliboutput"' -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -DXINELIBOUTPUT_VERSION='"1.0.3"' -DHAVE_XRENDER=1 -DHAVE_XDPMS=1 -DHAVE_XINERAMA=1 -DUSE_ICONV=1 -Wall -I../../../include  xine/post.c -o xine/post.o
cc -O3 -pipe -Wall -fPIC -g    -c -D_GNU_SOURCE -DPLUGIN_NAME_I18N='"xineliboutput"' -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -DXINELIBOUTPUT_VERSION='"1.0.3"' -DHAVE_XRENDER=1 -DHAVE_XDPMS=1 -DHAVE_XINERAMA=1 -DUSE_ICONV=1 -Wall -DFE_STANDALONE -I../../../include  tools/vdrdiscovery.c -o tools/vdrdiscovery_standalone.o
tools/vdrdiscovery.c: In function ‘udp_discovery_search’:
tools/vdrdiscovery.c:141: advarsel: ignoring return value of ‘asprintf’, declared with attribute warn_unused_result
cc -g xine_sxfe_frontend_standalone.o xine/post.o tools/vdrdiscovery_standalone.o -L/usr/X11R6/lib -lX11 -lXv -lXext -lXrender -ljpeg -lxine   -o vdr-sxfe
cc -O3 -pipe -Wall -fPIC -g    -c -D_GNU_SOURCE -DPLUGIN_NAME_I18N='"xineliboutput"' -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -DXINELIBOUTPUT_VERSION='"1.0.3"' -DHAVE_XRENDER=1 -DHAVE_XDPMS=1 -DHAVE_XINERAMA=1 -DUSE_ICONV=1 -Wall -DFE_STANDALONE -I../../../include  xine_fbfe_frontend.c -o xine_fbfe_frontend_standalone.o
In file included from xine_fbfe_frontend.c:120:
xine_frontend.c: In function ‘fe_frame_output_cb’:
xine_frontend.c:288: advarsel: ignoring return value of ‘system’, declared with attribute warn_unused_result
xine_frontend.c: In function ‘fe_xine_init’:
xine_frontend.c:549: advarsel: ignoring return value of ‘asprintf’, declared with attribute warn_unused_result
xine_frontend.c:552: advarsel: ignoring return value of ‘asprintf’, declared with attribute warn_unused_result
xine_frontend.c:558: advarsel: ignoring return value of ‘asprintf’, declared with attribute warn_unused_result
xine_frontend.c: In function ‘fe_xine_open’:
xine_frontend.c:728: advarsel: ignoring return value of ‘asprintf’, declared with attribute warn_unused_result
In file included from xine_frontend_main.c:56,
                 from xine_frontend.c:1665,
                 from xine_fbfe_frontend.c:120:
xine_frontend_lirc.c: In function ‘lirc_receiver_thread’:
xine_frontend_lirc.c:105: advarsel: ignoring return value of ‘nice’, declared with attribute warn_unused_result
In file included from xine_frontend.c:1665,
                 from xine_fbfe_frontend.c:120:
xine_frontend_main.c: In function ‘kbd_receiver_thread’:
xine_frontend_main.c:143: advarsel: ignoring return value of ‘system’, declared with attribute warn_unused_result
xine_frontend_main.c:144: advarsel: ignoring return value of ‘system’, declared with attribute warn_unused_result
xine_frontend_main.c:193: advarsel: ignoring return value of ‘system’, declared with attribute warn_unused_result
xine_frontend_main.c: In function ‘kbd_stop’:
xine_frontend_main.c:258: advarsel: ignoring return value of ‘system’, declared with attribute warn_unused_result
xine_frontend_main.c: In function ‘main’:
xine_frontend_main.c:550: advarsel: ignoring return value of ‘asprintf’, declared with attribute warn_unused_result
xine_frontend_main.c:553: advarsel: ignoring return value of ‘asprintf’, declared with attribute warn_unused_result
xine_frontend_main.c:566: advarsel: ignoring return value of ‘asprintf’, declared with attribute warn_unused_result
cc -g xine_fbfe_frontend_standalone.o xine/post.o tools/vdrdiscovery_standalone.o -lxine   -ljpeg -o vdr-fbfe
cc mpg2c.c -o mpg2c
cc -O3 -pipe -Wall -fPIC -g    -c -D_GNU_SOURCE -DPLUGIN_NAME_I18N='"xineliboutput"' -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -DXINELIBOUTPUT_VERSION='"1.0.3"' -DHAVE_XRENDER=1 -DHAVE_XDPMS=1 -DHAVE_XINERAMA=1 -DUSE_ICONV=1 -Wall -I../../../include  xine_input_vdr.c
xine_input_vdr.c: In function ‘queue_nosignal’:
xine_input_vdr.c:1224: advarsel: ignoring return value of ‘asprintf’, declared with attribute warn_unused_result
xine_input_vdr.c: In function ‘send_meta_info’:
xine_input_vdr.c:2716: advarsel: ignoring return value of ‘asprintf’, declared with attribute warn_unused_result
xine_input_vdr.c: In function ‘slave_track_maps_changed’:
xine_input_vdr.c:4015: advarsel: formatering er ikke en strengkonstant og der er ingen formateringsparametre
xine_input_vdr.c: In function ‘vdr_data_thread’:
xine_input_vdr.c:4756: advarsel: ignoring return value of ‘nice’, declared with attribute warn_unused_result
cc -O3 -pipe -Wall -fPIC -g    -shared -fvisibility=hidden  xine_input_vdr.o -lxine   -o xineplug_inp_xvdr.so
cc -O3 -pipe -Wall -fPIC -g    -c -D_GNU_SOURCE -DPLUGIN_NAME_I18N='"xineliboutput"' -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -DXINELIBOUTPUT_VERSION='"1.0.3"' -DHAVE_XRENDER=1 -DHAVE_XDPMS=1 -DHAVE_XINERAMA=1 -DUSE_ICONV=1 -Wall -I../../../include  xine_post_autocrop.c
cc -O3 -pipe -Wall -fPIC -g    -shared -fvisibility=hidden  xine_post_autocrop.o -lxine   -o xineplug_post_autocrop.so
cc -O3 -pipe -Wall -fPIC -g    -c -D_GNU_SOURCE -DPLUGIN_NAME_I18N='"xineliboutput"' -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -DXINELIBOUTPUT_VERSION='"1.0.3"' -DHAVE_XRENDER=1 -DHAVE_XDPMS=1 -DHAVE_XINERAMA=1 -DUSE_ICONV=1 -Wall -I../../../include  xine_post_swscale.c
cc -O3 -pipe -Wall -fPIC -g    -shared -fvisibility=hidden  xine_post_swscale.o -lxine   -o xineplug_post_swscale.so
cc -O3 -pipe -Wall -fPIC -g    -c -D_GNU_SOURCE -DPLUGIN_NAME_I18N='"xineliboutput"' -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -DXINELIBOUTPUT_VERSION='"1.0.3"' -DHAVE_XRENDER=1 -DHAVE_XDPMS=1 -DHAVE_XINERAMA=1 -DUSE_ICONV=1 -Wall -I../../../include  xine_post_audiochannel.c
cc -O3 -pipe -Wall -fPIC -g    -shared -fvisibility=hidden  xine_post_audiochannel.o -lxine   -o xineplug_post_audiochannel.so
xgettext -C -cTRANSLATORS --no-wrap --no-location -k -ktr -ktrNOOP --msgid-bugs-address='<phintuka@users.sourceforge.net>' -o po/xineliboutput.pot config.c device.c dummy_player.c equalizer.c frontend.c frontend_local.c frontend_svr.c i18n.c media_player.c menu.c menuitems.c mpg2c.c osd.c setup_menu.c tools.c vdrlogo_32x32.c xine_fbfe_frontend.c xine_frontend.c xine_frontend_lirc.c xine_frontend_main.c xine_input_vdr.c xineliboutput.c xine_post_audiochannel.c xine_post_autocrop.c xine_post_swscale.c xine_sxfe_frontend.c
msgmerge -U --no-wrap --no-location --backup=none -q po/cs_CZ.po po/xineliboutput.pot
msgfmt -c -o po/cs_CZ.mo po/cs_CZ.po
cp po/cs_CZ.mo ../../../locale/cs_CZ/LC_MESSAGES/vdr-xineliboutput.mo
msgmerge -U --no-wrap --no-location --backup=none -q po/de_DE.po po/xineliboutput.pot
msgfmt -c -o po/de_DE.mo po/de_DE.po
cp po/de_DE.mo ../../../locale/de_DE/LC_MESSAGES/vdr-xineliboutput.mo
msgmerge -U --no-wrap --no-location --backup=none -q po/fi_FI.po po/xineliboutput.pot
msgfmt -c -o po/fi_FI.mo po/fi_FI.po
cp po/fi_FI.mo ../../../locale/fi_FI/LC_MESSAGES/vdr-xineliboutput.mo
msgmerge -U --no-wrap --no-location --backup=none -q po/it_IT.po po/xineliboutput.pot
msgfmt -c -o po/it_IT.mo po/it_IT.po
cp po/it_IT.mo ../../../locale/it_IT/LC_MESSAGES/vdr-xineliboutput.mo
msgmerge -U --no-wrap --no-location --backup=none -q po/ru_RU.po po/xineliboutput.pot
msgfmt -c -o po/ru_RU.mo po/ru_RU.po
cp po/ru_RU.mo ../../../locale/ru_RU/LC_MESSAGES/vdr-xineliboutput.mo
Makefile:461: *********************** xineliboutput ***************************
Makefile:461: Xine plugins and frontends will not be installed automatically. 
Makefile:461: To install files execute "make install" in                      
Makefile:461: /usr/local/src/vdr/xineliboutput
Makefile:461: *****************************************************************
root@htpc:/usr/local/src/vdr/xineliboutput#

---

### Post by art2003 on 2009-05-27
forget about xineliboutput, make xine plugin instead

---

### Post by Mr Cool Span on 2009-05-27
> **art2003 said:**
> forget about xineliboutput, make xine plugin instead

is it posiball for you to tell me how, im lost now

---

### Post by penove on 2009-05-27
[HTML]Makefile:158: VDR not detected ! VDR plugin will not be compiled. [/HTML]

You must compile first VDR and next complile the plugin.
Try vdr-xineliboutput-1.0.4.tar.bz2 
You must compile in vdr/PLUGINS/src
make plugins

---

### Post by art2003 on 2009-05-27
xineliboutput is said to have problems with many HD channels, xine plugin is the best option other than forking out 140 EUR on a eHD card.

Do these steps (they are before step in the first page of this thread, the main tutorial)


cd /usr/local/src/vdr/PLUGINS/src
wget [http://home.vrweb.de/rnissl/vdr-xine-0.9.1.tgz](http://home.vrweb.de/rnissl/vdr-xine-0.9.1.tgz)
tar zxvf vdr-xine-0.9.1.tgz
ln -s xine-0.9.1 xine
cd /usr/local/src/vdr/PLUGINS/xine/data
mkdir -p /etc/vdr/plugins/xine/
cp *.mpg /etc/vdr/plugins/xine/
cd /usr/local/src/vdr/
make plugins
make install

> **Mr Cool Span said:**
> is it posiball for you to tell me how, im lost now

---

### Post by Mr Cool Span on 2009-05-27
> **penove said:**
> [HTML]Makefile:158: VDR not detected ! VDR plugin will not be compiled. [/HTML]

You must compile first VDR and next complile the plugin.
Try vdr-xineliboutput-1.0.4.tar.bz2 
You must compile in vdr/PLUGINS/src
make plugins

I thing i have it now, But yes ther is a but 
when i type sudo /etc/init.d/vdr start i see
MakePrimaryDevice: 1
=========================
SetVideoFormat: 0
SetVolumeDevice: 255
SetAudioChannelDevice: 0
SetVolumeDevice: 255
SetPlayMode: 1
SetDigitalAudioDevice: 0
frame: (0, 0)-(-1, -1), zoom: (1.00, 1.00)

and so one
No Gui???

---

### Post by art2003 on 2009-05-27
vdr is a backend,
follow the howto's instructions for oxine and then open oxine
it will connect to vdr and you will have

> **Mr Cool Span said:**
> I thing i have it now, But yes ther is a but 
when i type sudo /etc/init.d/vdr start i see
MakePrimaryDevice: 1
=========================
SetVideoFormat: 0
SetVolumeDevice: 255
SetAudioChannelDevice: 0
SetVolumeDevice: 255
SetPlayMode: 1
SetDigitalAudioDevice: 0
frame: (0, 0)-(-1, -1), zoom: (1.00, 1.00)

and so one
No Gui???

---

### Post by Mr Cool Span on 2009-05-27
> **art2003 said:**
> vdr is a backend,
follow the howto's instructions for oxine and then open oxine
it will connect to vdr and you will have

Okay new problem
In Totem i have 2 dvb devises
Dvb adapter 0 and Dvb adapter 1, no Mather withs on i takes i getting this erroer
that Totem don't have the necessary plug-in to handel it

---

### Post by FakeOutdoorsman on 2009-05-27
> **art2003 said:**
> 

**6. FFmpeg**
This little piece of software is part or the better known VLC
We are about to compile our own

```

cd /usr/local/src
sudo -s
apt-get build-dep ffmpeg
rm -rf /usr/include/ffmpeg
apt-get install build-essential libx264-dev libmp3lame-dev libfaad-dev libxvidcore4-dev 
apt-get install mercurial cvs subversion libncurses-dev 
apt-get install autoconf libtool automake pkg-config gettext libfaac-dev 
apt-get install liba52-0.7.4-dev liblame-dev libvorbis-dev zlib1g-dev libpng12-dev libx11-dev libxv-dev libasound2-dev
svn checkout svn://svn.mplayerhq.hu/ffmpeg/trunk ffmpeg
cd ffmpeg/
./configure --prefix=/usr --enable-gpl --enable-postproc --enable-libmp3lame --enable-libvorbis --enable-pthreads --enable-libx264 --enable-libtheora --enable-libfaac --enable-libfaad --enable-libxvid
make
make install
sudo cp ffmpeg /usr/local/bin/ffmpeg
ldconfig -v
```

FFmpeg SVN doesn't need *liba52-0.7.4-dev* anymore because it now has a native implementation of AC-3 (Dolby Digital).  Also, using *apt-get build-dep ffmpeg* will bring in a bunch of extra non-required packages and is designed for older FFmpeg revisions in the repository (< Jaunty).  Using *ldconfig -v* is probably only necessary if you use *--enable-shared*.  Feel free to link to my guide, modify, or take sections from it:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

**Update:** Perhaps you can skip compiling FFmpeg altogether:
[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

---

### Post by jimbo99 on 2009-05-27
Way out of range of a large number of people.  The reliance on almost all cli commands makes it easy to get tasks done, but even for an knowledgeable linux user it can be daunting.

Need to optimize it and remove features and steps that are not necessary.  Maybe create a simplified version of it which just addresses the major feature set.

How does this compare to boxed solutions like XBMC or even myth tv?

---

### Post by art2003 on 2009-05-27
For those who find this project too technical, or too time consuming I stated I offer to send a restore DVD for a resonable amount. It can be argued what parts are essential and what not, but the fact is that this tutorial is sub-set of what I have implemented. For example I have not covered the installation of mplayer with vdpau and mms as a frontend to watch HD recordings. What this project compares to is a Dreambox 8000 or a Reelbox Avantgarde. Those boxes cost over 1000 euro and this project on the other side the hardware costs less than 400.

> **jimbo99 said:**
> 
Need to optimize it and remove features and steps that are not necessary.  Maybe create a simplified version of it which just addresses the major feature set.

How does this compare to boxed solutions like XBMC or even myth tv?

---

### Post by Mr Cool Span on 2009-05-27
> **art2003 said:**
> For those who find this project too technical, or too time consuming I stated I offer to send a restore DVD for a resonable amount. It can be argued what parts are essential and what not, but the fact is that this tutorial is sub-set of what I have implemented. For example I have not covered the installation of mplayer with vdpau and mms as a frontend to watch HD recordings. What this project compares to is a Dreambox 8000 or a Reelbox Avantgarde. Those boxes cost over 1000 euro and this project on the other side the hardware costs less than 400.

yes im trying to built a htpc to replace my dreambox 800

---

### Post by art2003 on 2009-05-28
Thanks for your input, I modified the ffmpeg instalation a little bit after reading your guide.
I would be happy to 'outsource' the ffmpeg guide if you included the  --enable-postproc  as it is needed for the xine pluging to scale vdr's osd

> **FakeOutdoorsman said:**
> FFmpeg SVN doesn't need *liba52-0.7.4-dev* anymore because it now has a native implementation of AC-3 (Dolby Digital).  Also, using *apt-get build-dep ffmpeg* will bring in a bunch of extra non-required packages and is designed for older FFmpeg revisions in the repository (< Jaunty).  Using *ldconfig -v* is probably only necessary if you use *--enable-shared*.  Feel free to link to my guide, modify, or take sections from it:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

**Update:** Perhaps you can skip compiling FFmpeg altogether:
[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

---

### Post by FakeOutdoorsman on 2009-05-28
> **art2003 said:**
> Thanks for your input, I modified the ffmpeg instalation a little bit after reading your guide.
I would be happy to 'outsource' the ffmpeg guide if you included the  --enable-postproc  as it is needed for the xine pluging to scale vdr's osd

I want to keep the guide as simple as possible, so I think I'd like to keep out *--enable-postproc* unless I get some more requests to include it.

---

### Post by koenieboy on 2009-05-29
Hello guys,

I have follow the hole how to but at the final i have problems.

when i type sudo oxine than are this the errors.

What must i do for fixing this errors?

[2009-05-30 02:45:02] [          odk.c:1000] ERROR: Could not open '/usr/share/oxine/skins/oxinetic/backgrounds/menu_main_music.png': Could not find demuxer plugin!
[2009-05-30 02:45:02] [    utils_gui.c: 200] ERROR: Could not open or play menu background image!
[2009-05-30 02:45:02] [    utils_gui.c: 202] FATAL: Please make sure that your version of xine-lib supports playback of PNG files.
[2009-05-30 02:45:02] [    utils_gui.c: 202] FATAL: A fatal error occurred! Printing backtrace:
[2009-05-30 02:45:02] [    utils_gui.c: 202] FATAL:      oxine(_log+0x123) [0x805bd53]
[2009-05-30 02:45:02] [    utils_gui.c: 202] FATAL:      oxine(show_menu_background+0x160) [0x8084a00]
[2009-05-30 02:45:02] [    utils_gui.c: 202] FATAL:      oxine [0x807b13a]
[2009-05-30 02:45:02] [    utils_gui.c: 202] FATAL:      oxine [0x807badf]
[2009-05-30 02:45:02] [    utils_gui.c: 202] FATAL:      oxine(otk_draw+0xb2) [0x8077f82]
[2009-05-30 02:45:02] [    utils_gui.c: 202] FATAL:      oxine(show_user_interface+0x1b) [0x8084b4b]
[2009-05-30 02:45:02] [    utils_gui.c: 202] FATAL:      oxine [0x80540d0]
[2009-05-30 02:45:02] [    utils_gui.c: 202] FATAL:      oxine(oxine_event_handler+0x2d9) [0x8055349]
[2009-05-30 02:45:02] [    utils_gui.c: 202] FATAL:      oxine(odk_oxine_event_send+0x3c) [0x806f80c]
[2009-05-30 02:45:02] [    utils_gui.c: 202] FATAL:      oxine(main+0x1906) [0x807fdc6]

---

### Post by art2003 on 2009-05-30
What is the output of
ls /usr/share/oxine/skins/oxinetic/backgrounds/

> **koenieboy said:**
> Hello guys,

I have follow the hole how to but at the final i have problems.

when i type sudo oxine than are this the errors.

What must i do for fixing this errors?

[2009-05-30 02:45:02] [          odk.c:1000] ERROR: Could not open '/usr/share/oxine/skins/oxinetic/backgrounds/menu_main_music.png': Could not find demuxer plugin!
[2009-05-30 02:45:02] [    utils_gui.c: 200] ERROR: Could not open or play menu background image!
[2009-05-30 02:45:02] [    utils_gui.c: 202] FATAL: Please make sure that your version of xine-lib supports playback of PNG files.


---

### Post by koenieboy on 2009-05-30
> **art2003 said:**
> What is the output of
ls /usr/share/oxine/skins/oxinetic/backgrounds/

I think my output is okay

menu_extractor.png       menu_music.png
menu_help.png            menu_playback.png
menu_image.png           menu_playlist.png
menu_main_cdda.png       menu_settings_list.png
menu_main_dvd.png        menu_settings.png
menu_main_extractor.png  menu_subtitle.png
menu_main_help.png       menu_video.png
menu_main_image.png      menu_weather_clear_night.png
menu_main_music.png      menu_weather_clear.png
menu_main_playback.png   menu_weather_few_clouds_night.png
menu_main.png            menu_weather_few_clouds.png
menu_main_quit.png       menu_weather_overcast.png
menu_main_settings.png   menu_weather.png
menu_main_tv.png         menu_weather_severe_alert.png
menu_main_vcd.png        menu_weather_showers.png
menu_main_video.png      menu_weather_showers_scattered.png
menu_main_weather.png    menu_weather_snow.png
menu_media.png           menu_weather_storm.png

---

### Post by art2003 on 2009-05-30
Yes, it looks ok
It seems my oxine.deb does not work in your system, do a manual installation of oxine
I have updated the oxine section on the first post to explain how to do this, not really difficult if you have got
this far.

> **koenieboy said:**
> I think my output is okay

menu_main_video.png      menu_weather_showers_scattered.png
menu_main_weather.png    menu_weather_snow.png
menu_media.png           menu_weather_storm.png

---

### Post by Mr Cool Span on 2009-05-30
i have startet all over and finish But
when typing oxine in command line i get this
[2009-05-30 15:10:04] [        oxine.c: 697]  INFO:     oxine version: 0.7.1
[2009-05-30 15:10:04] [        oxine.c: 698]  INFO:  xine-lib version: 1.1.90hg
[2009-05-30 15:10:04] [        oxine.c: 699]  INFO:          language: da_DK.UTF-8
[2009-05-30 15:10:04] [        oxine.c: 700]  INFO:           codeset: UTF-8
[2009-05-30 15:10:05] [    scheduler.c:  72]  INFO: Successfully started scheduler thread.
[2009-05-30 15:10:05] [          odk.c:1592] ERROR: Failed to create window using video driver 'vidix'!
[2009-05-30 15:10:05] [      odk_x11.c: 405]  INFO: Found 1 Xinerama screens:
[2009-05-30 15:10:05] [      odk_x11.c: 410]  INFO:     screen[ 0]: 1152x864, +0+0
[2009-05-30 15:10:05] [      odk_x11.c: 214]  INFO: The current window manager supports 'Extended Window Manager Hints'.
[2009-05-30 15:10:05] [      odk_osd.c:2163]  INFO: The current video driver supports unscaled OSD!
[2009-05-30 15:10:05] [     odk_lirc.c: 134]  WARN: Could not find /home/martin/.oxine/lircrc, trying to use default configuration file /usr/share/oxine/lircrc.
[2009-05-30 15:10:05] [     odk_lirc.c:  69]  INFO: Successfully started the LIRC input plugin.
[2009-05-30 15:10:05] [  utils_files.c: 249] ERROR: Could not open '/home/martin/.oxine/playlist_rw.oxp': No such file or directory!
[2009-05-30 15:10:05] [ playlist_xml.c:  48] ERROR: Could not open '/home/martin/.oxine/playlist_rw.oxp': Permission denied!
[2009-05-30 15:10:05] [     menulist.c: 316]  INFO: Loading menu file '/home/martin/.oxine/mainmenu.xml'...
[2009-05-30 15:10:05] [     menulist.c: 316]  INFO: Loading menu file '/home/tv/.oxine/othermenu.xml'...
[2009-05-30 15:10:05] [  utils_files.c: 249] ERROR: Could not open '/home/tv/.oxine/othermenu.xml': No such file or directory!
[2009-05-30 15:10:05] [          odk.c: 965]  INFO:     main MRL: '/usr/share/oxine/skins/oxinetic/backgrounds/menu_main_tv.png'
[2009-05-30 15:10:05] [          odk.c: 966]  INFO: subtitle MRL: 'no subtitle'
[2009-05-30 15:10:05] [          odk.c:1000] ERROR: Could not open '/usr/share/oxine/skins/oxinetic/backgrounds/menu_main_tv.png': Could not find demuxer plugin!
[2009-05-30 15:10:05] [    utils_gui.c: 200] ERROR: Could not open or play menu background image!
[2009-05-30 15:10:05] [    utils_gui.c: 202] FATAL: Please make sure that your version of xine-lib supports playback of PNG files.
[2009-05-30 15:10:05] [    utils_gui.c: 202] FATAL: A fatal error occurred! Printing backtrace:
[2009-05-30 15:10:05] [    utils_gui.c: 202] FATAL:      oxine(_log+0x123) [0x805bd53]
[2009-05-30 15:10:05] [    utils_gui.c: 202] FATAL:      oxine(show_menu_background+0x160) [0x8084a00]
[2009-05-30 15:10:05] [    utils_gui.c: 202] FATAL:      oxine [0x807b13a]
[2009-05-30 15:10:05] [    utils_gui.c: 202] FATAL:      oxine [0x807badf]
[2009-05-30 15:10:05] [    utils_gui.c: 202] FATAL:      oxine(otk_draw+0xb2) [0x8077f82]
[2009-05-30 15:10:05] [    utils_gui.c: 202] FATAL:      oxine(show_user_interface+0x1b) [0x8084b4b]
[2009-05-30 15:10:05] [    utils_gui.c: 202] FATAL:      oxine [0x80540d0]
[2009-05-30 15:10:05] [    utils_gui.c: 202] FATAL:      oxine(oxine_event_handler+0x2d9) [0x8055349]
[2009-05-30 15:10:05] [    utils_gui.c: 202] FATAL:      oxine(odk_oxine_event_send+0x3c) [0x806f80c]
[2009-05-30 15:10:05] [    utils_gui.c: 202] FATAL:      oxine(main+0x1906) [0x807fdc6]
Aborted

---

### Post by art2003 on 2009-05-30
Have you compiled your own oxine as per the instructions I added to the first post 2 hours ago?

> **Mr Cool Span said:**
> i have startet all over and finish But
when typing oxine in command line i get this
[2009-05-30 15:10:04] [        oxine.c: 697]  INFO:     oxine version: 0.7.1
[2009-05-30 15:10:04] [        oxine.c: 698]  INFO:  xine-lib version: 

---

### Post by Mr Cool Span on 2009-05-30
> **art2003 said:**
> Have you compiled your own oxine as per the instructions I added to the first post 2 hours ago?

Okay I have done that now. Now i get this Error

[2009-05-30 16:37:32] [        oxine.c: 697]  INFO:     oxine version: 0.7.1
[2009-05-30 16:37:32] [        oxine.c: 698]  INFO:  xine-lib version: 1.1.90hg
[2009-05-30 16:37:32] [        oxine.c: 699]  INFO:          language: da_DK.UTF-8
[2009-05-30 16:37:32] [        oxine.c: 700]  INFO:           codeset: UTF-8
[2009-05-30 16:37:32] [    scheduler.c:  72]  INFO: Successfully started scheduler thread.
[2009-05-30 16:37:32] [          odk.c:1592] ERROR: Failed to create window using video driver 'vidix'!
[2009-05-30 16:37:32] [      odk_x11.c: 405]  INFO: Found 1 Xinerama screens:
[2009-05-30 16:37:32] [      odk_x11.c: 410]  INFO:     screen[ 0]: 1152x864, +0+0
[2009-05-30 16:37:32] [      odk_x11.c: 214]  INFO: The current window manager supports 'Extended Window Manager Hints'.
[2009-05-30 16:37:32] [      odk_osd.c:2163]  INFO: The current video driver supports unscaled OSD!
[2009-05-30 16:37:32] [     odk_lirc.c: 134]  WARN: Could not find /home/martin/.oxine/lircrc, trying to use default configuration file /usr/share/oxine/lircrc.
[2009-05-30 16:37:32] [     odk_lirc.c:  69]  INFO: Successfully started the LIRC input plugin.
[2009-05-30 16:37:32] [  utils_files.c: 249] ERROR: Could not open '/home/martin/.oxine/playlist_rw.oxp': No such file or directory!
[2009-05-30 16:37:32] [ playlist_xml.c:  48] ERROR: Could not open '/home/martin/.oxine/playlist_rw.oxp': Permission denied!
[2009-05-30 16:37:32] [     menulist.c: 316]  INFO: Loading menu file '/home/martin/.oxine/mainmenu.xml'...
[2009-05-30 16:37:32] [     menulist.c: 316]  INFO: Loading menu file '/home/tv/.oxine/othermenu.xml'...
[2009-05-30 16:37:32] [  utils_files.c: 249] ERROR: Could not open '/home/tv/.oxine/othermenu.xml': No such file or directory!
[2009-05-30 16:37:33] [          odk.c: 965]  INFO:     main MRL: '/usr/share/oxine/skins/oxinetic/backgrounds/menu_main_tv.png'
[2009-05-30 16:37:33] [          odk.c: 966]  INFO: subtitle MRL: 'no subtitle'
[2009-05-30 16:37:33] [          odk.c:1000] ERROR: Could not open '/usr/share/oxine/skins/oxinetic/backgrounds/menu_main_tv.png': Could not find demuxer plugin!
[2009-05-30 16:37:33] [    utils_gui.c: 200] ERROR: Could not open or play menu background image!
[2009-05-30 16:37:33] [    utils_gui.c: 202] FATAL: Please make sure that your version of xine-lib supports playback of PNG files.
[2009-05-30 16:37:33] [    utils_gui.c: 202] FATAL: A fatal error occurred! Printing backtrace:
[2009-05-30 16:37:33] [    utils_gui.c: 202] FATAL:      oxine(_log+0x123) [0x805bd53]
[2009-05-30 16:37:33] [    utils_gui.c: 202] FATAL:      oxine(show_menu_background+0x160) [0x8084a00]
[2009-05-30 16:37:33] [    utils_gui.c: 202] FATAL:      oxine [0x807b13a]
[2009-05-30 16:37:33] [    utils_gui.c: 202] FATAL:      oxine [0x807badf]
[2009-05-30 16:37:33] [    utils_gui.c: 202] FATAL:      oxine(otk_draw+0xb2) [0x8077f82]
[2009-05-30 16:37:33] [    utils_gui.c: 202] FATAL:      oxine(show_user_interface+0x1b) [0x8084b4b]
[2009-05-30 16:37:33] [    utils_gui.c: 202] FATAL:      oxine [0x80540d0]
[2009-05-30 16:37:33] [    utils_gui.c: 202] FATAL:      oxine(oxine_event_handler+0x2d9) [0x8055349]
[2009-05-30 16:37:33] [    utils_gui.c: 202] FATAL:      oxine(odk_oxine_event_send+0x3c) [0x806f80c]
[2009-05-30 16:37:33] [    utils_gui.c: 202] FATAL:      oxine(main+0x1906) [0x807fdc6]
Aborted

---

### Post by art2003 on 2009-05-30
replace any reference to /home/tv/ with /home/martin/
replace vidix in oxines config file with xv

do this:
ls /usr/share/oxine/skins/ -l

what do you get?

> **Mr Cool Span said:**
> Okay I have done that now. Now i get this Error
[2009-05-30 16:37:32] [          odk.c:1592] ERROR: Failed to create window using video driver 'vidix'!
[2009-05-30 16:37:32] [     menulist.c: 316]  INFO: Loading menu file '/home/tv/.oxine/othermenu.xml'...
[2009-05-30 16:37:32] [  utils_files.c: 249] ERROR: Could not open '/home/tv/.oxine/othermenu.xml': No such file or directory!
[2009-05-30 16:37:33] [          odk.c: 965]  INFO:     main MRL: '/usr/share/oxine/skins/oxinetic/backgrounds/menu_main_tv.png'
[2009-05-30 16:37:33] [          odk.c: 966]  INFO: subtitle MRL: 'no subtitle'
[2009-05-30 16:37:33] [          odk.c:1000] ERROR: Could not open '/usr/share/oxine/skins/oxinetic/backgrounds/menu_main_tv.png': Could not find demuxer plugin!
Aborted

---

### Post by Mr Cool Span on 2009-05-30
> **art2003 said:**
> replace any reference to /home/tv/ with /home/martin/
replace vidix in oxines config file with xv

do this:
ls /usr/share/oxine/skins/ -l

what do you get?

martin@htpc:~$ ls /usr/share/oxine/skins/ -l
totalt 4
drwxr-xr-x 3 root root 4096 2009-05-30 14:48 oxinetic
martin@htpc:~$



I come back later to day thanx m8

---

### Post by art2003 on 2009-05-30
for oxine try:

ln -s /usr/share/oxine/skins/oxinetic /usr/share/oxine/skins/default

---

### Post by Mr Cool Span on 2009-05-30
> **art2003 said:**
> for oxine try:

ln -s /usr/share/oxine/skins/oxinetic /usr/share/oxine/skins/default

okay have done everything you ask me to so now i get his and nothing more happens
martin@htpc:~$ sudo oxine
[2009-05-30 19:08:30] [        oxine.c: 697]  INFO:     oxine version: 0.7.1
[2009-05-30 19:08:30] [        oxine.c: 698]  INFO:  xine-lib version: 1.1.90hg
[2009-05-30 19:08:30] [        oxine.c: 699]  INFO:          language: da_DK.UTF-8
[2009-05-30 19:08:30] [        oxine.c: 700]  INFO:           codeset: UTF-8
[2009-05-30 19:08:30] [    scheduler.c:  72]  INFO: Successfully started scheduler thread.
[2009-05-30 19:08:30] [      odk_x11.c: 405]  INFO: Found 1 Xinerama screens:
[2009-05-30 19:08:30] [      odk_x11.c: 410]  INFO:     screen[ 0]: 1152x864, +0+0
[2009-05-30 19:08:30] [      odk_x11.c: 214]  INFO: The current window manager supports 'Extended Window Manager Hints'.
[2009-05-30 19:08:31] [      odk_osd.c:2163]  INFO: The current video driver supports unscaled OSD!
[2009-05-30 19:08:31] [     odk_lirc.c: 134]  WARN: Could not find /home/martin/.oxine/lircrc, trying to use default configuration file /usr/share/oxine/lircrc.
[2009-05-30 19:08:31] [     odk_lirc.c:  69]  INFO: Successfully started the LIRC input plugin.
[2009-05-30 19:08:31] [     menulist.c: 316]  INFO: Loading menu file '/home/martin/.oxine/mainmenu.xml'...
[2009-05-30 19:08:31] [     menulist.c: 316]  INFO: Loading menu file '/home/martin/.oxine/othermenu.xml'...

---

### Post by art2003 on 2009-05-31
Do you launch oxine from a terminal on your desktop?
what happens if you launch it without sudo?

> **Mr Cool Span said:**
> okay have done everything you ask me to so now i get his and nothing more happens
martin@htpc:~$ sudo oxine
[2009-05-30 19:08:30] [        oxine.c: 697]  INFO:     oxine version: 0.7.1
[2009-05-30 19:08:30] [        oxine.c: 698]  INFO:  xine-lib version: 1.1.90hg
[2009-05-30 19:08:30] [        oxine.c: 699]  INFO:          language: da_DK.UTF-8
[2009-05-30 19:08:30] [        oxine.c: 700]  INFO:           codeset: UTF-8
[2009-05-30 19:08:30] [    scheduler.c:  72]  INFO: Successfully started scheduler thread.
[2009-05-30 19:08:30] [      odk_x11.c: 405]  INFO: Found 1 Xinerama screens:
[2009-05-30 19:08:30] [      odk_x11.c: 410]  INFO:     screen[ 0]: 1152x864, +0+0
[2009-05-30 19:08:30] [      odk_x11.c: 214]  INFO: The current window manager supports 'Extended Window Manager Hints'.
[2009-05-30 19:08:31] [      odk_osd.c:2163]  INFO: The current video driver supports unscaled OSD!
[2009-05-30 19:08:31] [     odk_lirc.c: 134]  WARN: Could not find /home/martin/.oxine/lircrc, trying to use default configuration file /usr/share/oxine/lircrc.
[2009-05-30 19:08:31] [     odk_lirc.c:  69]  INFO: Successfully started the LIRC input plugin.
[2009-05-30 19:08:31] [     menulist.c: 316]  INFO: Loading menu file '/home/martin/.oxine/mainmenu.xml'...
[2009-05-30 19:08:31] [     menulist.c: 316]  INFO: Loading menu file '/home/martin/.oxine/othermenu.xml'...

---

### Post by Mr Cool Span on 2009-05-31
> **art2003 said:**
> Do you launch oxine from a terminal on your desktop?
what happens if you launch it without sudo?

martin@htpc:~$ oxine
[2009-05-31 12:52:48] [        oxine.c: 697]  INFO:     oxine version: 0.7.1
[2009-05-31 12:52:48] [        oxine.c: 698]  INFO:  xine-lib version: 1.1.90hg
[2009-05-31 12:52:48] [        oxine.c: 699]  INFO:          language: da_DK.UTF-8
[2009-05-31 12:52:48] [        oxine.c: 700]  INFO:           codeset: UTF-8
[2009-05-31 12:52:48] [    scheduler.c:  72]  INFO: Successfully started scheduler thread.
[2009-05-31 12:52:48] [      odk_x11.c: 405]  INFO: Found 1 Xinerama screens:
[2009-05-31 12:52:48] [      odk_x11.c: 410]  INFO:     screen[ 0]: 1152x864, +0+0
[2009-05-31 12:52:48] [      odk_x11.c: 214]  INFO: The current window manager supports 'Extended Window Manager Hints'.
Xlib:  extension "NV-GLX" missing on display ":0.0".
vo_vdpau: Can't create vdp device : No vdpau implementation.
Segmentation fault
martin@htpc:~$

You have a pm m8

---

### Post by art2003 on 2009-05-31
Oxine does not support vdpau, but to get around there I have a setup with mms, oxine and a bunch of scripts so the right thing is automatically used for the right job, it is all part of my restore dvd but really too much to cover on this howto, which addresses the basics

In the meantime you can edit .oxine/config
# video driver to use
# { auto  vdpau  xv  raw  opengl  xshm  aa  none  sdl  vidix  vidixfb  fb }, default: 0
video.driver:xv

try xv, raw, etc until one works.


> **Mr Cool Span said:**
> martin@htpc:~$ oxine

Xlib:  extension "NV-GLX" missing on display ":0.0".
vo_vdpau: Can't create vdp device : No vdpau implementation.
Segmentation fault
martin@htpc:~$

You have a pm m8

---

### Post by koenieboy on 2009-05-31
**Alternative installation for oxine is the .deb does not work for you, compile your own**:
cd /usr/local/src
sudo -s
wget [http://oxine.sourceforge.net/oxine-snapshot.tar.gz](http://oxine.sourceforge.net/oxine-snapshot.tar.gz)
tar zxvf oxine-snapshot.tar.gz
cd oxine-snapshot
./configure --prefix=/usr --disable-joystick --enable-vdr      
make
make install

I have this done but the configure file was named configure.ac and i cant get "
./configure --prefix=/usr --disable-joystick --enable-vdr" dit not done.

en more presis the prefix=/usr colt not 

What kan i do now?

For all my problems thnx art2003 i tink that he my prolems can solved

---

### Post by uub on 2009-05-31
I just came accross this thread and was wondering if this would work if I bought one of the new ION boards with the Atom N330 and Nvidia 9400 GFX, would the cpu be able to handle decoding h264 from say SkyHD? or does the GPU handle it, I know not all Windows programs can take advantage of using the GPU to decode content.

Also any chance of some screenshots or photos of this up and running :)

---

### Post by steefjeqv on 2009-06-01
> **uub said:**
> I just came accross this thread and was wondering if this would work if I bought one of the new ION boards with the Atom N330 and Nvidia 9400 GFX, would the cpu be able to handle decoding h264 from say SkyHD? or does the GPU handle it, I know not all Windows programs can take advantage of using the GPU to decode content.

Also any chance of some screenshots or photos of this up and running :)

Hi,

The Ion supports the use of VDPAU, so yes it handles H264 through its GPU.

At the moment, I haven't heard of VDR running on it but it should be possible. There's certainly a lot of interest from people using VDR because it is indeed a great base for a small VDR client.

This shows the Ion running Ubuntu - XBMC with VDPAU (and experimental VDR TV).
[http://www.youtube.com/watch?v=rv1Q_DWieAQ]("http://www.youtube.com/watch?v=rv1Q_DWieAQ")

If you're interested in using VDR with VDPAU and H.264 support (and experimental XBMC compatability) and if you don't need ccam then you might consider using GDA's ppa-launchpad (thank you Gerald) :

[https://launchpad.net/~gda-dachsweb/+archive/vdr]("https://launchpad.net/~gda-dachsweb/+archive/vdr")

Greetings,
Steven

---

### Post by art2003 on 2009-06-01
replace the ./configure line with this:  (the first post is already updated)

./autogen.sh --prefix=/usr --disable-joystick --enable-vdr  

> **koenieboy said:**
> **Alternative installation for oxine is the .deb does not work for you, compile your own**:
cd /usr/local/src
sudo -s
wget [http://oxine.sourceforge.net/oxine-snapshot.tar.gz](http://oxine.sourceforge.net/oxine-snapshot.tar.gz)
tar zxvf oxine-snapshot.tar.gz
cd oxine-snapshot
./configure --prefix=/usr --disable-joystick --enable-vdr      
make
make install

I have this done but the configure file was named configure.ac and i cant get "
./configure --prefix=/usr --disable-joystick --enable-vdr" dit not done.

en more presis the prefix=/usr colt not 

What kan i do now?

For all my problems thnx art2003 i tink that he my prolems can solved

---

### Post by uub on 2009-06-01
steefjeqv: thanks for your reply, I was hoping to use CCcam, I was originally looking at the DM800,IPBOX like the OP but for the money it seems I can build a rather nice HTPC for the same price that would be able to do more.

Are you saying VDR doesnt have complete VDPAU support at the moment then with CCcam support?

---

### Post by steefjeqv on 2009-06-01
> **uub said:**
> steefjeqv: thanks for your reply, I was hoping to use CCcam, I was originally looking at the DM800,IPBOX like the OP but for the money it seems I can build a rather nice HTPC for the same price that would be able to do more.

Are you saying VDR doesnt have complete VDPAU support at the moment then with CCcam support?

Hi,

Basically, the stable version (1.6.0) doesn't do h.264.
The ppa I mentioned is a patched 1.6.0, ready for HDTV with VDPAU (using libxine-vdpau and xineliboutput) without DVB-S2.
You just have to use this nice howto to add the CCcam support.

This  VDR howto should work, and do all you recquire. 

Greetings,
Steven

---

### Post by koenieboy on 2009-06-02
Okay one step forwards

In the how to is a line:

This is my ~/.oxine/othermenu.xml

But what is the code of this menu, there is no code that working

thanks for all m8

---

### Post by specher on 2009-06-04
hello,
thanks for this howto.
I try to follow it, but I am stuck at the make of libxine-1.2
this is my error message, and I have no idea how to solve it 

xmmx.c: Assembler messages:
xmmx.c:79: Error: suffix or operands invalid for `movq'
xmmx.c:80: Error: suffix or operands invalid for `movq'
make[3]: *** [libpost_goom_asm_la-xmmx.lo] Error 1
make[3]: Leaving directory `/usr/local/src/xine-lib-1.2/src/post/goom'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/usr/local/src/xine-lib-1.2/src/post'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/usr/local/src/xine-lib-1.2/src'
make: *** [all-recursive] Error 1

thanks for your help
sp

---

### Post by art2003 on 2009-06-04
Try these commands one by one:
sudo -s
./autogen.sh --prefix=/usr --with-external-ffmpeg --disable-dxr3 
make -j6
checkinstall --fstrans=no --install=yes --pkgname=libxine2-dev --pkgversion "1.2.svn`date +%Y%m%d`-12ubuntu3"

> **specher said:**
> hello,
thanks for this howto.
I try to follow it, but I am stuck at the make of libxine-1.2
this is my error message, and I have no idea how to solve it 

xmmx.c: Assembler messages:
xmmx.c:79: Error: suffix or operands invalid for `movq'
xmmx.c:80: Error: suffix or operands invalid for `movq'
make[3]: *** [libpost_goom_asm_la-xmmx.lo] Error 1
make[3]: Leaving directory `/usr/local/src/xine-lib-1.2/src/post/goom'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/usr/local/src/xine-lib-1.2/src/post'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/usr/local/src/xine-lib-1.2/src'
make: *** [all-recursive] Error 1

thanks for your help
sp

---

### Post by specher on 2009-06-04
that is exactly what I did.
I first tried with the vdpau patch and w32 codecs, and afterwards without both. 
The lines I gave is the result of the make command. (in both cases)

sp

---

### Post by art2003 on 2009-06-04
Install the xine-dev.deb package in this thread...

> **specher said:**
> that is exactly what I did.
I first tried with the vdpau patch and w32 codecs, and afterwards without both. 
The lines I gave is the result of the make command. (in both cases)

sp

---

### Post by specher on 2009-06-04
QUOTE]Install the xine-dev.deb package in this thread...
[/QUOTE]

Which package do you mean. In synaptic I have a libxine-dev package, but that is version 1.1.16.3. Is that compatible with libxine-1.2 ?
I did a search in the thread but can't find a xine-dev.deb package ?

thanks,

sp

---

### Post by art2003 on 2009-06-04
It is the third line in point 7 (7. xine-lib installation)
 just click on the ziddu download link...

> **specher said:**
> QUOTE]Install the xine-dev.deb package in this thread...


Which package do you mean. In synaptic I have a libxine-dev package, but that is version 1.1.16.3. Is that compatible with libxine-1.2 ?
I did a search in the thread but can't find a xine-dev.deb package ?

thanks,

sp[/QUOTE]

---

### Post by art2003 on 2009-06-04
If you search ziddu you find it but here it is anyways...

[http://www.ziddu.com/download/4995962/libxine2-dev_svn20090601ubuntuBUFFERFIXEDx386.rar.html](http://www.ziddu.com/download/4995962/libxine2-dev_svn20090601ubuntuBUFFERFIXEDx386.rar.html)

unpack the .rar and you will find the .deb inside 

> **art2003 said:**
> It is the third line in point 7 (7. xine-lib installation)
 just click on the ziddu download link...



Which package do you mean. In synaptic I have a libxine-dev package, but that is version 1.1.16.3. Is that compatible with libxine-1.2 ?
I did a search in the thread but can't find a xine-dev.deb package ?

thanks,

sp

---

### Post by specher on 2009-06-04
Ok, thanks.
I did install the .deb package.
Afterwards I tried to compile xine-ui and I got error messages with 64 in it, so I presume it is due to the fact you have a 64 bits machine and I have a 32 bits.
I also retried to compile xinelib-1.2, but still the same error.
so still stuck ...

sp

---

### Post by art2003 on 2009-06-05
No, I have 32bits Ubuntu 8.10.
Somewhere along the road you must have done something wrong or combined different tutorials. Perhaps you would benefit from my restore DVD that has everything working out of the box?

> **specher said:**
> Ok, thanks.
I did install the .deb package.
Afterwards I tried to compile xine-ui and I got error messages with 64 in it, so I presume it is due to the fact you have a 64 bits machine and I have a 32 bits.
I also retried to compile xinelib-1.2, but still the same error.
so still stuck ...

sp

---

### Post by specher on 2009-06-05
thanks for your proposal, but I don't like things working out of the box ;)
Do you use 8.10 or 9.04 ?
The package you ask me to install, does it replace the complete compile procedure of xine-lib-1.2, or it contains only headers to make the compilation possible ?
I will look further this Week-end

thanks
sp

---

### Post by art2003 on 2009-06-05
Answering your questions

a) I use 8.10, 32bits
b) If you follow the compile process succesfully you end up with a .deb package that contains the library binaries and dev headers. That is the .deb I posted (within the .rar) What this .deb does not do is check you have all the dependencies installed.

Good luck!

> **specher said:**
> 
Do you use 8.10 or 9.04 ?
The package you ask me to install, does it replace the complete compile procedure of xine-lib-1.2, or it contains only headers to make the compilation possible ?
I will look further this Week-end

thanks
sp

---

### Post by penove on 2009-06-12
hi art2003
::system
MB asus P5K
Core 2 E660
3GB RAM
Skystar HD 2 
Geforce 9200
	
I already have the VDR to work with xine, but I have some problems with HD channels, especially with the sound ... failure much time.
I use OSS and increased the buffer in the config $ HOME / .xine;

[HTML]# Number of audio buffers
# Numeric, default: 230
engine.buffers.audio_num_buffers: 2500

# Number of video buffers
# Numeric, default: 500
engine.buffers.video_num_buffers: 1500[/HTML]

But still without success.
You have this problem?

---

### Post by art2003 on 2009-06-13
Hi, these are my current settings:

$ HOME / .xine

audio.synchronization.av_sync_method:resample
audio.synchronization.force_rate:48000
engine.buffers.audio_num_buffers:230
engine.buffers.video_num_buffers:1500
engine.buffers.video_num_frames:22

and in /etc/vdr/setup.conf
xine.modeLiveTV.prebufferFrames = 16
xine.modeLiveTV.prebufferHysteresis = 0


I am told the next version of xine-plugin will allow to specify different buffer for SD and HD


> **penove said:**
> hi art2003
::system
MB asus P5K
Core 2 E660
3GB RAM
Skystar HD 2 
Geforce 9200
	
I already have the VDR to work with xine, but I have some problems with HD channels, especially with the sound ... failure much time.
I use OSS and increased the buffer in the config $ HOME / .xine;

[HTML]# Number of audio buffers
# Numeric, default: 230
engine.buffers.audio_num_buffers: 2500

# Number of video buffers
# Numeric, default: 500
engine.buffers.video_num_buffers: 1500[/HTML]

But still without success.
You have this problem?

---

### Post by penove on 2009-06-13
Like you say "- The cherry on the cake" 
perfect... thanks a lot... 

	
Now I am trying to get to work because the oxine your configs and your *. deb not work on my PC.
But is already taking shape ... WoW.

---

### Post by coolercooler on 2009-06-13
Whats the cause of this error when install Xine-Lib 1.2 CVS, I've tried to shorten the ffmpeg, as well as tried another version of ffmpeg, but can't seem to get past this.

Xine-Lib 1.2 CVS
```
/usr/local/src/ffmpeg/libavcodec/libxvidff.c:271: undefined reference to `xvid_plugin_lumimasking'
/usr/local/src/ffmpeg/libavcodec/libxvidff.c:349: undefined reference to `xvid_encore'
/usr/local/src/ffmpeg/libavcodec/libxvidff.c:264: undefined reference to `xvid_plugin_single'
/usr/local/src/ffmpeg/libavcodec/libxvidff.c:255: undefined reference to `xvid_plugin_2pass2'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libavcodec.a(libxvid_rc.o): In function `ff_xvid_rate_control_uninit':
/usr/local/src/ffmpeg/libavcodec/libxvid_rc.c:146: undefined reference to `xvid_plugin_2pass2'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libavcodec.a(libxvid_rc.o): In function `ff_xvid_rate_estimate_qscale':
/usr/local/src/ffmpeg/libavcodec/libxvid_rc.c:127: undefined reference to `xvid_plugin_2pass2'
/usr/local/src/ffmpeg/libavcodec/libxvid_rc.c:119: undefined reference to `xvid_plugin_2pass2'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libavcodec.a(libxvid_rc.o): In function `ff_xvid_rate_control_init':
/usr/local/src/ffmpeg/libavcodec/libxvid_rc.c:80: undefined reference to `xvid_plugin_2pass2'
collect2: ld returned 1 exit status
make[4]: *** [xineplug_decode_ff.la] Error 1
make[4]: Leaving directory `/usr/local/src/xine-lib-1.2/src/combined/ffmpeg'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/usr/local/src/xine-lib-1.2/src/combined/ffmpeg'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/usr/local/src/xine-lib-1.2/src/combined'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/usr/local/src/xine-lib-1.2/src'
make: *** [all-recursive] Error 1
 
```

Thanks

---

### Post by art2003 on 2009-06-14
Try:
sudo apt-get install libxvidcore4-dev

> **coolercooler said:**
> Whats the cause of this error when install Xine-Lib 1.2 CVS, I've tried to shorten the ffmpeg, as well as tried another version of ffmpeg, but can't seem to get past this.

Xine-Lib 1.2 CVS
```
/usr/local/src/ffmpeg/libavcodec/libxvidff.c:271: undefined reference to `xvid_plugin_lumimasking'
/usr/local/src/ffmpeg/libavcodec/libxvidff.c:349: undefined reference to `xvid_encore'
/usr/local/src/ffmpeg/libavcodec/libxvidff.c:264: undefined reference to `xvid_plugin_single'
/usr/local/src/f 
```

Thanks

---

### Post by coolercooler on 2009-06-14
> **art2003 said:**
> Try:
sudo apt-get install libxvidcore4-dev

Hi, thanks.

```
 libxvidcore4-dev is already the newest version.

```

But still the same problem.

---

### Post by art2003 on 2009-06-14
well, don´t enable libxvid support, you don´t really need it for this project.
x264 is for HD TV but xvid is not necessary

> **coolercooler said:**
> Hi, thanks.

```
 libxvidcore4-dev is already the newest version.

```

But still the same problem.

---

### Post by coolercooler on 2009-06-14
> **art2003 said:**
> well, don´t enable libxvid support, you don´t really need it for this project.
x264 is for HD TV but xvid is not necessary

Hi Art, Yes I did read your earlier post suggesting that, I simply use this line. ```
 ./configure --prefix=/usr --enable-gpl --enable-postproc --enable-libmp3lame --enable-libvorbis --enable-pthreads --enable-libx264 
```

But stil get this error. ```
 collect2: ld returned 1 exit status
make[4]: *** [xineplug_decode_ff.la] Error 1
make[4]: Leaving directory `/usr/local/src/xine-lib-1.2/src/combined/ffmpeg'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/usr/local/src/xine-lib-1.2/src/combined/ffmpeg'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/usr/local/src/xine-lib-1.2/src/combined'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/usr/local/src/xine-lib-1.2/src'
make: *** [all-recursive] Error 1

```  

and I've tried a complete reinstall of ubuntu.

---

### Post by art2003 on 2009-06-14
To compile xine-lib

just do:

sudo -s
make clean
./autogen.sh --prefix=/usr --with-external-ffmpeg --disable-dxr3 
make 
make install
> **coolercooler said:**
> Hi Art, Yes I did read your earlier post suggesting that, I simply use this line. ```
 ./configure --prefix=/usr --enable-gpl --enable-postproc --enable-libmp3lame --enable-libvorbis --enable-pthreads --enable-libx264 
```

But stil get this error. ```
 collect2: ld returned 1 exit status
make[4]: *** [xineplug_decode_ff.la] Error 1
make[4]: Leaving directory `/usr/local/src/xine-lib-1.2/src/combined/ffmpeg'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/usr/local/src/xine-lib-1.2/src/combined/ffmpeg'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/usr/local/src/xine-lib-1.2/src/combined'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/usr/local/src/xine-lib-1.2/src'
make: *** [all-recursive] Error 1

```  

and I've tried a complete reinstall of ubuntu.

---

### Post by coolercooler on 2009-06-14
Yes make clean, make, make install. and then at the end.

```
collect2: ld returned 1 exit status
make[4]: *** [xineplug_decode_ff.la] Error 1
make[4]: Leaving directory `/usr/local/src/xine-lib-1.2/src/combined/ffmpeg'
make[3]: *** [install] Error 2
make[3]: Leaving directory `/usr/local/src/xine-lib-1.2/src/combined/ffmpeg'
make[2]: *** [install-recursive] Error 1
make[2]: Leaving directory `/usr/local/src/xine-lib-1.2/src/combined'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/usr/local/src/xine-lib-1.2/src'
make: *** [install-recursive] Error 1

****  Installation failed. Aborting package creation.
 
```

---

### Post by art2003 on 2009-06-15
the ffmpeg version you might be downloading from svn could currently be broken with regards to xine-lib, either get a working snapshot or wait a few days for the svn to update

> **coolercooler said:**
> Yes make clean, make, make install. and then at the end.

```
collect2: ld returned 1 exit status
make[4]: *** [xineplug_decode_ff.la] Error 1
make[4]: Leaving directory `/usr/local/src/xine-lib-1.2/src/combined/ffmpeg'
make[3]: *** [install] Error 2
make[3]: Leaving directory `/usr/local/src/xine-lib-1.2/src/combined/ffmpeg'
make[2]: *** [install-recursive] Error 1
make[2]: Leaving directory `/usr/local/src/xine-lib-1.2/src/combined'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/usr/local/src/xine-lib-1.2/src'
make: *** [install-recursive] Error 1

****  Installation failed. Aborting package creation.
 
```

---

### Post by penove on 2009-06-15
Where did my installation I had this error. And solved with reinstall the drivers of the NVIDIA ... test this repository.
[HTML]
https://launchpad.net/~brandonsnider/+archive/ppa[/HTML]

	
I use the nvidia-graphics-drivers-180-opengl3 - 180.37.05-0ubuntu1~ppa1 



P,

---

### Post by coolercooler on 2009-06-16
The problem was with configure part of ffmpeg and I used another tutorial on the web to get around and fix.

Since then rest of the install went fine, but for some reason can't launch xine now even though it was working, when I tested after install.

This is the error.

```
xine: error while loading shared libraries: libxine.so.2: cannot open shared object file: No such file or directory
 
```

---

### Post by penove on 2009-06-16
> **coolercooler said:**
> The problem was with configure part of ffmpeg and I used another tutorial on the web to get around and fix.

Since then rest of the install went fine, but for some reason can't launch xine now even though it was working, when I tested after install.

This is the error.

```
xine: error while loading shared libraries: libxine.so.2: cannot open shared object file: No such file or directory
 
```

	
you install the VDR-xine-0.9.2 ?
runvdr you have -P xine \
?

---

### Post by coolercooler on 2009-06-16
Yes I have that plugin installed and and enabled in the runvdr file.

the backend seems to start ok, it's the front end, even if I simply type xine at the command line comes with that error.

However I've gone back to start, deleted all files and restarted again, lets see if it works, but this time I will try it without oxine first.

Thanks

---

### Post by daouid on 2009-06-16
Hi, thx for the great tutorial !

im running into a few problems:

Here is my setup:

dvb-c Full Feature Dvb-ttpci siemens card
nvidia 9800 serie gfx
ubuntu 9.04

uname -a =>
Linux daouid-desktop 2.6.28.9-custom #1 SMP Sun Jun 7 20:00:42 CEST 2009 i686 GNU/Linux

FFMPEG => OK
V4l-dvb    => OK
VDR         => OK 
Sound over SPDIF => OK
VDPAU drivers => OK
VDR PLUGINS  (SC, => OK 
DVB-CARD FIRMWARE => Latest from [http://www.escape-edv.de/endriss/firmware/](http://www.escape-edv.de/endriss/firmware/)
xineliboutput & streamdev => 

[B]Free To Air HD channel wont work

Display bug (squares, green frames, bad rendering) on many SD channels[/B]

I've managed to overcome most bugs, using info from this thread

&

[http://xbmc.org/forum/showthread.php?p=346179](http://xbmc.org/forum/showthread.php?p=346179)

&

trying different PPA repositories like:

[https://launchpad.net/~mirak-mirak/+archive/ppa]("https://launchpad.net/%7Emirak-mirak/+archive/ppa")

[https://launchpad.net/~gda-dachsweb/+archive/vdr]("https://launchpad.net/%7Egda-dachsweb/+archive/vdr")

[https://launchpad.net/~henningpingel/+archive/xbmc]("https://launchpad.net/%7Ehenningpingel/+archive/xbmc")

but i cannot solve the above described problem

Here is the complete output of 

root@daouid-desktop:/usr/local/src/vdr/PLUGINS/src/xineliboutput# 

```
./vdr-sxfe --audio=alsa --verbose
```

```
vdr-sxfe 1.0.4  (build with xine-lib 1.1.90, using xine-lib 1.1.90)

Audio driver: alsa
Verbose mode

VDR server not given, searching ...
[16896] [discovery] Reveived broadcast: 66 bytes from 192.168.1.198 
VDR xineliboutput DISCOVERY 1.0
Client: 255.255.255.255:37890


[16896] [discovery] NOT valid discovery message
[16896] [discovery] Reveived broadcast: 92 bytes from 192.168.1.198 
VDR xineliboutput DISCOVERY 1.0
Server port: 37890
Server version: xineliboutput-1.0.4


[16896] [discovery] Valid discovery message
Found VDR server: host 192.168.1.198, port 37890
[16896] [vdr-fe]    sxfe_display_open(width=720, height=576, fullscreen=0, display=(null))
[16896] [vdr-fe]    Display size : 524 x 331 mm
[16896] [vdr-fe]                   1920 x 1200 pixels
[16896] [vdr-fe]                   92dpi / 93dpi
[16896] [vdr-fe]    Display ratio: 3625.000000/3664.000000 = 0.989356
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_sputext.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_sputext.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_vo_out_none.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_image.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_inp_vcd.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_real.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_real.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_vdpau_vc1.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_lpcm.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_xiph.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_xiph.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_xiph.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_xiph.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_xiph.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_inp_net.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_ao_out_file.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_vo_out_opengl.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_inp_rtp.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_rgb.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_mpeg_ts.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_matroska.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_inp_xvdr.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_mad.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_inp_http.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_real.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_vdr.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_vdr.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_vdr.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_vdr.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_vo_out_raw.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_nsv.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_bitplane.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_inp_file.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_ao_out_none.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_inp_stdin_fifo.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_inp_dvd.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_vo_out_vdpau.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_vo_out_fb.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_slave.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_nsf.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_nsf.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_inp_pvr.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_gsm610.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/post/xineplug_post_tvtime.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/post/xineplug_post_swscale.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/post/xineplug_post_swscale.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/post/xineplug_post_autocrop.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/post/xineplug_post_switch.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/post/xineplug_post_audiochannel.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/post/xineplug_post_visualizations.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/post/xineplug_post_visualizations.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/post/xineplug_post_visualizations.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/post/xineplug_post_audio_filters.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/post/xineplug_post_audio_filters.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/post/xineplug_post_audio_filters.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/post/xineplug_post_audio_filters.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/post/xineplug_post_goom.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/post/xineplug_post_mosaico.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_vo_out_xv.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_vo_out_xv.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_playlist.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_spucc.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_dts.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_mpeg_pes.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_vdpau_mpeg12.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_w32dll.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_w32dll.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_ao_out_pulseaudio.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_iff.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_mpeg2.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_spudvb.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_mpc.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_inp_vcdo.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_flv.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_vo_out_aa.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_ao_out_oss.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_asf.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_faad.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_yuv.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_a52.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_rawdv.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_ao_out_alsa.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_inp_v4l.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_inp_v4l.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_mpeg_elem.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_ff.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_ff.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_ff.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_ff.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_mpeg_block.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_mng.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_dvaudio.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_yuv_frames.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_mpeg.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_avi.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_spucmml.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_pva.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_spu.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_inp_mms.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_vo_out_xshm.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_vo_out_xshm.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_yuv4mpeg2.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_inp_cdda.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_gdk_pixbuf.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_inp_dvb.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_vc1_es.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_fli.so found
load_plugins: cannot open plugin lib /usr/lib/xine/plugins/2.0/xineplug_decode_image.so:
libWand.so.10: cannot open shared object file: No such file or directory
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_inp_pnm.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_qt.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_qt.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_ao_out_esd.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_inp_rtsp.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_vdpau_h264.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_vo_out_vidix.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_vo_out_vidix.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_vo_out_sdl.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_qt.so found
vo_vdpau: vdpau API version : 0
vo_vdpau: vdpau implementation description : Unknown
vo_vdpau: vdpau_alloc_frame
vo_vdpau: vdpau_alloc_frame
vo_vdpau: vdpau_alloc_frame
vo_vdpau: vdpau_alloc_frame
vo_vdpau: vdpau_alloc_frame
vo_vdpau: vdpau_alloc_frame
vo_vdpau: vdpau_alloc_frame
vo_vdpau: vdpau_alloc_frame
vo_vdpau: vdpau_alloc_frame
vo_vdpau: vdpau_alloc_frame
vo_vdpau: vdpau_alloc_frame
vo_vdpau: vdpau_alloc_frame
vo_vdpau: vdpau_alloc_frame
vo_vdpau: vdpau_alloc_frame
vo_vdpau: vdpau_alloc_frame
vo_vdpau: vdpau_alloc_frame
vo_vdpau: vdpau_alloc_frame
vo_vdpau: vdpau_alloc_frame
vo_vdpau: vdpau_alloc_frame
vo_vdpau: vdpau_alloc_frame
vo_vdpau: vdpau_alloc_frame
vo_vdpau: vdpau_alloc_frame
vo_vdpau: vdpau_alloc_frame
vo_vdpau: vdpau_alloc_frame
vo_vdpau: vdpau_alloc_frame
vo_vdpau: vdpau_alloc_frame
vo_vdpau: vdpau_alloc_frame
vo_vdpau: vdpau_alloc_frame
vo_vdpau: vdpau_alloc_frame
vo_vdpau: vdpau_alloc_frame
audio_alsa_out : supported modes are 8bit 16bit 24bit 32bit mono stereo (4-channel not enabled in xine config) (4.1-channel not enabled in xine config) (5-channel not enabled in xine config) 5.1-channel (a/52 and DTS pass-through not enabled in xine config)
[16896] [vdr-fe]    Detected 2 CPUs
[16896] [vdr-fe]    Enabling multithreaded video decoding
Available video drivers: vdpau xv raw opengl xshm aa none sdl vidix vidixfb fb
Available audio drivers: pulseaudio alsa oss esd none file
Available post plugins:  vdr tvtime warp swscale autocrop switch audiochannel oscope fftscope fftgraph upmix upmix_mono stretch volnorm expand fill invert eq denoise3d boxblur eq2 unsharp pp noise goom mosaico vdr_video vdr_audio
Available input plugins: rtp XVDR http VDR FILE stdin DVD pvr VCDO v4l_radio v4l_tv mms CD DVB pnm rtsp tcp VCD
Available demux plugins: anx image mpeg-ts matroska real nsv wve idcin ipmovie vqa wc3movie roq str film smjpeg fourxm vmd slave nsfdemux aiff flac realaudio snd tta voc vox playlist mpeg_pes iff flashvideo asf mpeg_block mng avi pva yuv4mpeg2 fli quicktime ogg mpeg ac3 dts cdda wav rawdv mpc shn mp3 elem yuv_frames vc1es sputext aac aud
Available audio decoder plugins: gsm610 mad ffmpegaudio realadec vorbis nsfdec mpc a/52 dvaudio speex win32a faad qta dts pcm
Available video decoder plugins: vdpau_mpeg12 vdpau_vc1 mpeg2 gdkpixbuf vdpau_h264 realvdec ffmpegvideo theora win32v yuv bitplane qtv rgb ffmpeg-wmv8 ffmpeg-wmv9
Available SPU decoder plugins:   spudec spudvb spucmml spucc sputext


Press Esc to exit

[16896] [input_vdr] Symbol SysLogLevel found : value 3
[16896] [input_vdr] Symbol LogToSysLog found : value no
[16896] [input_vdr] init class succeeded
[16896] [input_vdr] vdr_class_get_instance
[16896] [input_vdr] fifo_buffer_new...
[16896] [input_vdr] fifo_buffer_new done.
[16896] [input_vdr] vdr_class_get_instance done.
xine: found input plugin  : VDR (Video Disk Recorder) input plugin
[16896] [input_vdr] vdr_plugin_open_net xvdr://192.168.1.198:37890
[16896] [input_vdr] Connecting (control) to tcp://192.168.1.198:37890 ...
[16896] [input_vdr] setsockopt(SO_RCVBUF): got 262142 bytes
[16896] [input_vdr] Server greeting: VDR-1.6.0 xineliboutput-1.0.4 READY
[16896] [input_vdr] Got Client-ID: 0
[16896] [input_vdr] Connected (control) to tcp://192.168.1.198:37890
[16896] [input_vdr] Connecting (data) to pipe:///video/vdrconf/plugins/xineliboutput/pipes.14709/pipe.0
[16896] [input_vdr] Data stream connected (PIPE)
[16913] [input_vdr] Control thread started
[16914] [input_vdr] Data thread started
input cache plugin disabled
xine: found demuxer plugin: DVD/VOB demux plugin
[16896] [vdr-fe]    re-wiring post plugins
prebuffer=14400 pts
[16913] [vdr-fe]    closing post plugin: tvtime
av_offset=0 pts
vdpau_set_property: property=8, value=100
vdpau_set_property: property=2, value=0
vo_vdpau: vdpau_update_csc: hue=0.000000, saturation=1.000000, contrast=1.000000, brightness=0.000000, color_standard=0
vdpau_set_property: property=3, value=100
vo_vdpau: vdpau_update_csc: hue=0.000000, saturation=1.000000, contrast=1.000000, brightness=0.000000, color_standard=0
vdpau_set_property: property=5, value=0
vo_vdpau: vdpau_update_csc: hue=0.000000, saturation=1.000000, contrast=1.000000, brightness=0.000000, color_standard=0
vdpau_set_property: property=4, value=100
vo_vdpau: vdpau_update_csc: hue=0.000000, saturation=1.000000, contrast=1.000000, brightness=0.000000, color_standard=0
vdpau_set_property: property=1, value=3
[16913] [vdr-fe]    closing post plugin: upmix
[16913] [vdr-fe]    closing post plugin: autocrop
[16913] [vdr-fe]    closing post plugin: swscale
[16913] [vdr-fe]    closing post plugin: pp
[16913] [vdr-fe]    closing post plugin: unsharp
[16913] [vdr-fe]    closing post plugin: denoise3d
vo_vdpau: recreate mixer to match frames: width=704, height=576, chroma=0
vo_vdpau: enabled features: temporal=0, temporal_spatial=0
vo_vdpau: enabled features: inverse_telecine=0
vo_vdpau: disable noise reduction.
vo_vdpau: disable sharpness.
vo_vdpau: vdpau_update_csc: hue=0.000000, saturation=1.000000, contrast=1.000000, brightness=0.000000, color_standard=0
vo_vdpau: skip_chroma = 0
vo_vdpau: output_surface size update
prebuffer=14400 pts
video_out: throwing away image with pts 129146 because it's too old (diff : 62009).
vo_vdpau: soft_surface size update
vo_vdpau: output_surface size update
prebuffer=14400 pts
[16915] [input_vdr] H.264 scanner: Possible MPEG2 start code (0xb3)
vo_vdpau: recreate mixer to match frames: width=528, height=576, chroma=0
vo_vdpau: enabled features: temporal=0, temporal_spatial=0
vo_vdpau: enabled features: inverse_telecine=0
vo_vdpau: disable noise reduction.
vo_vdpau: disable sharpness.
vo_vdpau: vdpau_update_csc: hue=0.000000, saturation=1.000000, contrast=1.000000, brightness=0.000000, color_standard=0
vo_vdpau: skip_chroma = 0
[16915] [input_vdr] VIDEO pts wrap before AUDIO, ignoring audio pts 2440290308
200 frames delivered, 0 frames skipped, 1 frames discarded
vo_vdpau: update_frame - destroy surface
vo_vdpau: update_frame - destroy surface
vo_vdpau: update_frame - destroy surface
vo_vdpau: recreate mixer to match frames: width=541, height=1959, chroma=0
vo_vdpau: enabled features: temporal=0, temporal_spatial=0
vo_vdpau: enabled features: inverse_telecine=0
vo_vdpau: disable noise reduction.
vo_vdpau: disable sharpness.
vo_vdpau: vdpau_update_csc: hue=0.000000, saturation=1.000000, contrast=1.000000, brightness=0.000000, color_standard=0
vo_vdpau: skip_chroma = 0
vo_vdpau: recreate mixer to match frames: width=528, height=576, chroma=0
vo_vdpau: enabled features: temporal=0, temporal_spatial=0
vo_vdpau: enabled features: inverse_telecine=0
vo_vdpau: disable noise reduction.
vo_vdpau: disable sharpness.
vo_vdpau: vdpau_update_csc: hue=0.000000, saturation=1.000000, contrast=1.000000, brightness=0.000000, color_standard=0
vo_vdpau: skip_chroma = 0
[16906] [vdr-fe]    Keyboard thread terminated
[16896] [vdr-fe]    unwiring audio post plugins
[16896] [vdr-fe]    unwiring video post plugins
[16896] [vdr-fe]    unloading post plugins
[16896] [input_vdr] vdr_plugin_dispose
[16914] [input_vdr] Data stream disconnected
[16914] [input_vdr] Data thread terminated
[16896] [input_vdr] Shutdown control
[16896] [input_vdr] Cancel control thread ...
[16913] [input_vdr] Control thread terminated
[16896] [input_vdr] Cancel data thread ...
[16896] [input_vdr] Threads joined
[16896] [input_vdr] Disposing event queues
[16896] [input_vdr] Destroying mutexes
[16896] [input_vdr] Closing data connection
[16896] [input_vdr] Closing control connection
[16896] [input_vdr] Connections closed.
vdpau_set_property: property=2, value=0
vo_vdpau: vdpau_update_csc: hue=0.000000, saturation=1.000000, contrast=1.000000, brightness=0.000000, color_standard=0
vdpau_set_property: property=3, value=100
vo_vdpau: vdpau_update_csc: hue=0.000000, saturation=1.000000, contrast=1.000000, brightness=0.000000, color_standard=0
vdpau_set_property: property=5, value=0
vo_vdpau: vdpau_update_csc: hue=0.000000, saturation=1.000000, contrast=1.000000, brightness=0.000000, color_standard=0
vdpau_set_property: property=4, value=100
vo_vdpau: vdpau_update_csc: hue=0.000000, saturation=1.000000, contrast=1.000000, brightness=0.000000, color_standard=0
vdpau_set_property: property=1, value=0
```

and the output of 
```

root@daouid-desktop:/usr/local/src/vdr/PLUGINS/src/xineliboutput# ./vdr-sxfe --audio=alsa --video=xv --verbose
```

```
vdr-sxfe 1.0.4  (build with xine-lib 1.1.90, using xine-lib 1.1.90)

Audio driver: alsa
Video driver: xv
Verbose mode

VDR server not given, searching ...
[17148] [discovery] Reveived broadcast: 66 bytes from 192.168.1.198 
VDR xineliboutput DISCOVERY 1.0
Client: 255.255.255.255:37890


[17148] [discovery] NOT valid discovery message
[17148] [discovery] Reveived broadcast: 92 bytes from 192.168.1.198 
VDR xineliboutput DISCOVERY 1.0
Server port: 37890
Server version: xineliboutput-1.0.4


[17148] [discovery] Valid discovery message
Found VDR server: host 192.168.1.198, port 37890
[17148] [vdr-fe]    sxfe_display_open(width=720, height=576, fullscreen=0, display=(null))
[17148] [vdr-fe]    Display size : 524 x 331 mm
[17148] [vdr-fe]                   1920 x 1200 pixels
[17148] [vdr-fe]                   92dpi / 93dpi
[17148] [vdr-fe]    Display ratio: 3625.000000/3664.000000 = 0.989356
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_sputext.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_sputext.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_vo_out_none.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_image.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_inp_vcd.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_real.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_real.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_vdpau_vc1.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_lpcm.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_xiph.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_xiph.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_xiph.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_xiph.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_xiph.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_inp_net.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_ao_out_file.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_vo_out_opengl.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_inp_rtp.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_rgb.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_mpeg_ts.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_matroska.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_inp_xvdr.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_mad.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_inp_http.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_real.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_vdr.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_vdr.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_vdr.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_vdr.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_vo_out_raw.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_nsv.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_bitplane.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_inp_file.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_ao_out_none.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_inp_stdin_fifo.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_inp_dvd.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_vo_out_vdpau.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_vo_out_fb.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_slave.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_nsf.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_nsf.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_inp_pvr.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_gsm610.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/post/xineplug_post_tvtime.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/post/xineplug_post_swscale.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/post/xineplug_post_swscale.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/post/xineplug_post_autocrop.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/post/xineplug_post_switch.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/post/xineplug_post_audiochannel.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/post/xineplug_post_visualizations.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/post/xineplug_post_visualizations.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/post/xineplug_post_visualizations.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/post/xineplug_post_audio_filters.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/post/xineplug_post_audio_filters.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/post/xineplug_post_audio_filters.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/post/xineplug_post_audio_filters.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/post/xineplug_post_goom.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/post/xineplug_post_mosaico.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_vo_out_xv.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_vo_out_xv.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_playlist.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_spucc.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_dts.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_mpeg_pes.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_vdpau_mpeg12.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_w32dll.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_w32dll.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_ao_out_pulseaudio.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_iff.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_mpeg2.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_spudvb.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_mpc.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_inp_vcdo.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_flv.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_vo_out_aa.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_ao_out_oss.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_asf.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_faad.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_yuv.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_a52.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_rawdv.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_ao_out_alsa.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_inp_v4l.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_inp_v4l.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_mpeg_elem.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_ff.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_ff.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_ff.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_ff.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_mpeg_block.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_mng.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_dvaudio.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_yuv_frames.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_mpeg.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_avi.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_spucmml.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_pva.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_spu.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_inp_mms.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_vo_out_xshm.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_vo_out_xshm.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_yuv4mpeg2.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_inp_cdda.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_gdk_pixbuf.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_inp_dvb.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_vc1_es.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_fli.so found
load_plugins: cannot open plugin lib /usr/lib/xine/plugins/2.0/xineplug_decode_image.so:
libWand.so.10: cannot open shared object file: No such file or directory
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_inp_pnm.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_qt.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_qt.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_ao_out_esd.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_inp_rtsp.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_vdpau_h264.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_vo_out_vidix.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_vo_out_vidix.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_vo_out_sdl.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_qt.so found
video_out_xv: using Xv port 280 from adaptor NV17 Video Texture for hardware colour space conversion and scaling.
video_out_xv: ignoring broken XV_HUE settings on NVidia cards
video_out_xv: this adaptor supports the YUY2 format.
video_out_xv: this adaptor supports the YV12 format.
audio_alsa_out : supported modes are 8bit 16bit 24bit 32bit mono stereo (4-channel not enabled in xine config) (4.1-channel not enabled in xine config) (5-channel not enabled in xine config) 5.1-channel (a/52 and DTS pass-through not enabled in xine config)
[17148] [vdr-fe]    Detected 2 CPUs
[17148] [vdr-fe]    Enabling multithreaded video decoding
Available video drivers: vdpau xv raw opengl xshm aa none sdl vidix vidixfb fb
Available audio drivers: pulseaudio alsa oss esd none file
Available post plugins:  vdr tvtime warp swscale autocrop switch audiochannel oscope fftscope fftgraph upmix upmix_mono stretch volnorm expand fill invert eq denoise3d boxblur eq2 unsharp pp noise goom mosaico vdr_video vdr_audio
Available input plugins: rtp XVDR http VDR FILE stdin DVD pvr VCDO v4l_radio v4l_tv mms CD DVB pnm rtsp tcp VCD
Available demux plugins: anx image mpeg-ts matroska real nsv wve idcin ipmovie vqa wc3movie roq str film smjpeg fourxm vmd slave nsfdemux aiff flac realaudio snd tta voc vox playlist mpeg_pes iff flashvideo asf mpeg_block mng avi pva yuv4mpeg2 fli quicktime ogg mpeg ac3 dts cdda wav rawdv mpc shn mp3 elem yuv_frames vc1es sputext aac aud
Available audio decoder plugins: gsm610 mad ffmpegaudio realadec vorbis nsfdec mpc a/52 dvaudio speex win32a faad qta dts pcm
Available video decoder plugins: vdpau_mpeg12 vdpau_vc1 mpeg2 gdkpixbuf vdpau_h264 realvdec ffmpegvideo theora win32v yuv bitplane qtv rgb ffmpeg-wmv8 ffmpeg-wmv9
Available SPU decoder plugins:   spudec spudvb spucmml spucc sputext


Press Esc to exit

[17148] [input_vdr] Symbol SysLogLevel found : value 3
[17148] [input_vdr] Symbol LogToSysLog found : value no
[17148] [input_vdr] init class succeeded
[17148] [input_vdr] vdr_class_get_instance
[17148] [input_vdr] fifo_buffer_new...
[17148] [input_vdr] fifo_buffer_new done.
[17148] [input_vdr] vdr_class_get_instance done.
xine: found input plugin  : VDR (Video Disk Recorder) input plugin
[17148] [input_vdr] vdr_plugin_open_net xvdr://192.168.1.198:37890
[17148] [input_vdr] Connecting (control) to tcp://192.168.1.198:37890 ...
[17148] [input_vdr] setsockopt(SO_RCVBUF): got 262142 bytes
[17148] [input_vdr] Server greeting: VDR-1.6.0 xineliboutput-1.0.4 READY
[17148] [input_vdr] Got Client-ID: 0
[17148] [input_vdr] Connected (control) to tcp://192.168.1.198:37890
[17148] [input_vdr] Connecting (data) to pipe:///video/vdrconf/plugins/xineliboutput/pipes.16947/pipe.0
[17148] [input_vdr] Data stream connected (PIPE)
[17165] [input_vdr] Control thread started
[17166] [input_vdr] Data thread started
input cache plugin disabled
xine: found demuxer plugin: DVD/VOB demux plugin
[17148] [vdr-fe]    re-wiring post plugins
[17165] [vdr-fe]    closing post plugin: tvtime
av_offset=0 pts
xv_set_property: property=8, value=100
video_out_xv: VO_PROP_ZOOM_X = 100
xv_set_property: property=2, value=0
xv_set_property: property=3, value=4096
xv_set_property: property=5, value=0
xv_set_property: property=4, value=4096
xv_set_property: property=1, value=3
video_out_xv: VO_PROP_ASPECT_RATIO(3)
[17165] [vdr-fe]    closing post plugin: upmix
[17165] [vdr-fe]    closing post plugin: autocrop
[17165] [vdr-fe]    closing post plugin: swscale
[17165] [vdr-fe]    closing post plugin: pp
[17165] [vdr-fe]    closing post plugin: unsharp
[17165] [vdr-fe]    closing post plugin: denoise3d
prebuffer=14400 pts
[17167] [input_vdr] H.264 scanner: Possible MPEG2 start code (0xb3)
Not multiplexed? 0xd9
200 frames delivered, 54 frames skipped, 0 frames discarded
[17167] [input_vdr] VIDEO pts wrap before AUDIO, ignoring audio pts 5625089653
[17167] [input_vdr] VIDEO pts wrap before AUDIO, ignoring audio pts 1095143381
200 frames delivered, 58 frames skipped, 0 frames discarded
Not multiplexed? 0xff
[17167] [input_vdr] VIDEO pts wrap before AUDIO, ignoring audio pts 1221068303
[17148] [vdr-fe]    Keypress: XKeySym 4  
[17148] [vdr-fe]    Keypress: XKeySym 5  
[17166] [input_vdr] data_stream_parse_control: waiting for engine_flushed condition 0<18231830
prebuffer=14400 pts
[17166] [input_vdr] data_stream_parse_control: streams synced at 18231830/18231830
video_out: throwing away image with pts -145528307 because it's too old (diff : 147619881).
prebuffer=14400 pts
[17167] [input_vdr] H.264 scanner: Possible MPEG2 start code (0xb3)
Not multiplexed? 0xbd
Not multiplexed? 0xdb
Not multiplexed? 0xff
Not multiplexed? 0xf5
Not multiplexed? 0xc1
video_out: throwing away image with pts -108055847 because it's too old (diff : 110367851).
video_out: throwing away image with pts -108052247 because it's too old (diff : 110364251).
Not multiplexed? 0xfa
200 frames delivered, 78 frames skipped, 3 frames discarded
[17167] [input_vdr] VIDEO pts wrap before AUDIO, ignoring audio pts 6238840841
[17167] [input_vdr] VIDEO pts wrap before AUDIO, ignoring audio pts 2294633103
Not multiplexed? 0xca
Not multiplexed? 0xcc
Not multiplexed? 0xda
Not multiplexed? 0xbf
video_out: throwing away image with pts 2568518 because it's too old (diff : 84641).
video_out: throwing away image with pts 2630454 because it's too old (diff : 22705).
video_out: throwing away image with pts 2634054 because it's too old (diff : 19105).
video_out: throwing away image with pts 2637654 because it's too old (diff : 15505).
video_out: throwing away image with pts 2644837 because it's too old (diff : 8322).
video_out: throwing away image with pts 2648315 because it's too old (diff : 4844).
video_out: throwing away image with pts 2831996 because it's too old (diff : 45176).
video_out: throwing away image with pts 2839196 because it's too old (diff : 37976).
video_out: throwing away image with pts 2846036 because it's too old (diff : 31136).
video_out: throwing away image with pts 2861766 because it's too old (diff : 15406).
video_out: throwing away image with pts 2867781 because it's too old (diff : 9391).
video_out: throwing away image with pts 2870801 because it's too old (diff : 6371).
200 frames delivered, 90 frames skipped, 12 frames discarded
[17158] [vdr-fe]    Keyboard thread terminated
[17148] [vdr-fe]    unwiring audio post plugins
[17148] [vdr-fe]    unwiring video post plugins
[17148] [vdr-fe]    unloading post plugins
[17148] [input_vdr] vdr_plugin_dispose
[17166] [input_vdr] Data stream disconnected
[17148] [input_vdr] Shutdown control
[17148] [input_vdr] Cancel control thread ...
[17166] [input_vdr] Data thread terminated
[17165] [input_vdr] Control thread terminated
[17148] [input_vdr] Cancel data thread ...
[17148] [input_vdr] Threads joined
[17148] [input_vdr] Disposing event queues
[17148] [input_vdr] Destroying mutexes
[17148] [input_vdr] Closing data connection
[17148] [input_vdr] Closing control connection
[17148] [input_vdr] Connections closed.
xv_set_property: property=2, value=0
xv_set_property: property=3, value=4096
xv_set_property: property=5, value=0
xv_set_property: property=4, value=4096
xv_set_property: property=1, value=0
video_out_xv: VO_PROP_ASPECT_RATIO(0)
[17148] [input_vdr] Disposing fifos
[17148] [input_vdr] dispose done.
Terminating...
[17148] [vdr-fe]    unloading post plugins

```

im am running a compiled from source version of vdr obtained from this repository:

[https://launchpad.net/~gda-dachsweb/+archive/vdr]("https://launchpad.net/%7Egda-dachsweb/+archive/vdr")

description: 

```
My VDR packages for Jaunty are heavily based on e-tobis with the following differences:
 - Zulus extension patch 72 for Graphttf plugin >= 0.3.1 and for XBMC integration
 - Hires OSD patch
 - Graphtft plugin >= 0.3.1 with X support and graphtft-fe
 - VDPAU support
 - h.264 support
 - crop patches from durchflieger
```

any idea or tips i should try?

firmware / vdr version ?

xine-lib / xineliboutput

---

### Post by daouid on 2009-06-16
BTW,

to im sure my OS can decode HD content, i've run some test using 1080p and lower res files

both in H264 or MP4 format (mov, mkv & avi's)

and AC3 works fine also

---

### Post by coolercooler on 2009-06-17
Almost there, most of the things are working now, accept can't get the remote to work, I get this error when I try to install lirc.

```
 Error!  Build of lirc_pvr150.ko failed for: 2.6.27-14-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/lirc/0.8.4a/build/ for more information.
Installing initial module

Error! Could not locate lirc_atiusb.ko for module lirc in the DKMS tree.
You must run a dkms build for kernel 2.6.27-14-generic (i686) first.
Done.

```

And on startup lirc fails.  Any ideas guys?

---

### Post by steefjeqv on 2009-06-17
Hi,

@ daouid :

I'm also using the gda repo, which works for me watching SD. When I watch HD channels I get the same issues you've described (only on HD).

If you're using xineliboutput as a frontend then you can try replacing the xineliboutput part of your /etc/vdr/setup.conf by this (point 2.2 in the wiki). Change the conf to your resolution (it's set up for 1920x1080) :

[http://www.vdr-wiki.de/wiki/index.php/VDPAU]("http://www.vdr-wiki.de/wiki/index.php/VDPAU")

Greetings,
Steven

---

### Post by walterav on 2009-06-17
Hi,

What's the difference between the VDR and the kaffeine way? 

The last one looks more simple to me with sc-plugin. I have no experience yet with both, but I do know my DVB-s works out of the box with kaffeine...

Any screenshots maybe?

---

### Post by daouid on 2009-06-17
> **steefjeqv said:**
> Hi,

@ daouid :

I'm also using the gda repo, which works for me watching SD. When I watch HD channels I get the same issues you've described (only on HD).

If you're using xineliboutput as a frontend then you can try replacing the xineliboutput part of your /etc/vdr/setup.conf by this (point 2.2 in the wiki). Change the conf to your resolution (it's set up for 1920x1080) :

[http://www.vdr-wiki.de/wiki/index.php/VDPAU](http://www.vdr-wiki.de/wiki/index.php/VDPAU)

Greetings,
Steven

Hi Steven,

my screen resolution is 1920x1080 ;)

i've try using vdr without VDPAU patches, same for xinelib, but i still had the same issues, so my guess is that the problem doenst come from VDPAU or h264.

I'll give it a try tonight anyways thx for the tip.

daouid

---

### Post by coolercooler on 2009-06-17
> **walterav said:**
> Hi,

What's the difference between the VDR and the kaffeine way? 

The last one looks more simple to me with sc-plugin. I have no experience yet with both, but I do know my DVB-s works out of the box with kaffeine...

Any screenshots maybe?

Hi vdr is much better and alot more flexable, when things work that is, I wouldn't recommend this project for newbies, unless you want to learn and like to mess about.

It works and looks like dreambox, if you ever had one.

---

### Post by walterav on 2009-06-17
> **coolercooler said:**
> 

It works and looks like dreambox, if you ever had one.

Well I heard a lot about it, so vdr is something that needs a lot of tweaking and customizing and will not work or give some kind of a gui, unless you build it yourself am I right?

---

### Post by steefjeqv on 2009-06-18
Hi,

@ walterav :

you don't need to build it yourself.
It does recquire some configuring.

The stable VDR (1.6.x) doesn't support DVB-S2 and HDTV. CCcam is never included in VDR (although there are deb packages and sources available).

The devel VDR (1.7.x) does support HDTV, DVB-S2 and ATSC, so the next stable release will have these features.

If you need CCcam then this Howto is very helpful.

The ppa of Gerald Dachs (gda) gives you a VDR which runs out of box.
It's set up to use Nvidia's VDPAU (you need an Nvidia 8xxx or 9xxx series).

Some images :
[http://www.kuba4u.de/vdr/pics/page_01.htm]("http://www.kuba4u.de/vdr/pics/page_01.htm")

Greetings,
Steven

---

### Post by walterav on 2009-06-20
art2003
>  Re: HTPC DVB-S2 VDR 1.7.5 CCcam Howto
the ffmpeg version you might be downloading from svn could currently be broken with regards to xine-lib, either get a working snapshot or wait a few days for the svn to update

Quote:
Originally Posted by coolercooler View Post
Yes make clean, make, make install. and then at the end.

Code:

collect2: ld returned 1 exit status
make[4]: *** [xineplug_decode_ff.la] Error 1
make[4]: Leaving directory `/usr/local/src/xine-lib-1.2/src/combined/ffmpeg'
make[3]: *** [install] Error 2
make[3]: Leaving directory `/usr/local/src/xine-lib-1.2/src/combined/ffmpeg'
make[2]: *** [install-recursive] Error 1
make[2]: Leaving directory `/usr/local/src/xine-lib-1.2/src/combined'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/usr/local/src/xine-lib-1.2/src'
make: *** [install-recursive] Error 1

****  Installation failed. Aborting package creation.



coolercooler
>  Re: HTPC DVB-S2 VDR 1.7.5 CCcam Howto
The problem was with configure part of ffmpeg and I used another tutorial on the web to get around and fix.

Since then rest of the install went fine, but for some reason can't launch xine now even though it was working, when I tested after install.

This is the error.

Code:

xine: error while loading shared libraries: libxine.so.2: cannot open shared object file: No such file or directory



I also have a problem getting further with this error at step7.

collect2: ld returned 1 exit status
	make[4]: *** [xineplug_decode_ff.la] Error 1
	make[4]: Leaving directory `/usr/local/src/xine-lib-1.2/src/combined/ffmpeg'
	make[3]: *** [all] Error 2
	make[3]: Leaving directory `/usr/local/src/xine-lib-1.2/src/combined/ffmpeg'
	make[2]: *** [all-recursive] Error 1
	make[2]: Leaving directory `/usr/local/src/xine-lib-1.2/src/combined'
	make[1]: *** [all-recursive] Error 1
	make[1]: Leaving directory `/usr/local/src/xine-lib-1.2/src'
	make: *** [all-recursive] Error 1

Coolercooler can you post your solution?

I started this tutorial/howto at step5. This because I could not get cccam working with kaffeine...

step5 #channel search went fine
step6 #went fine no errors
step7 #error when doing make see this post

hardware:
p4b-533e , p4 2,4ghz, 1gig ram
nvidia fx5200 agp
satcard ¨Hauppauge nova pci¨
02:0a.0 Multimedia controller: Philips Semiconductors SAA7146 (rev 01)
	Subsystem: Technotrend Systemtechnik GmbH Device 1003
	Flags: bus master, medium devsel, latency 64, IRQ 22
	Memory at d5000000 (32-bit, non-prefetchable) [size=512]
	Kernel driver in use: budget dvb
	Kernel modules: budget

ubuntu 9.04 / linux mint 7 glora

---

### Post by coolercooler on 2009-06-20
walterav, this what I did to make lib part work, ```
1 go to ffmpeg dir. 
2 make clean, 
3. use this line "./configure --prefix=/usr --enable-shared --enable-gpl --enable-postproc --enable-libmp3lame --enable-libvorbis --enable-pthreads --enable-libx264 --enable-libtheora --enable-libfaac --enable-libfaad --enable-libxvid --enable-nonfree" 
4 make 
5 make install, 
6 ldconfig -v
```
Then go to xine-lib dir and make clean, then continue from configure part.

But now I have everthing up and running,but I get this error.
@Art2003, do you know whats the cause  of this error.
```
 [8253] [input_vdr] TCP: Buffer too small (8192 ; incoming frame 304666722 bytes)
[8253] [input_vdr] TCP: Buffer too small (8192 ; incoming frame 803865020 bytes)
[8253] [input_vdr] TCP: Buffer too small (8192 ; incoming frame 18868551 bytes)
[8253] [input_vdr] TCP: Buffer too small (8192 ; incoming frame 2079601282 bytes)
[8253] [input_vdr] TCP: Buffer too small (8192 ; incoming frame 2103569677 bytes)
[8253] [input_vdr] TCP: Buffer too small (8192 ; incoming frame 1426004308 bytes)
[8253] [input_vdr] TCP: Delay too long, disconnecting
[8254] [input_vdr] read_block: no data source, returning NULL
[8244] [vdr-fe]    xine_event_cb: XINE_EVENT_UI_PLAYBACK_FINISHED
[8251] [input_vdr] XINE_EVENT_UI_PLAYBACK_FINISHED
[8236] [input_vdr] write_control aborted
[8236] [input_vdr]    (ERROR (xine_input_vdr.c,1024): Resource temporarily unavailable)
[8236] [input_vdr] Connections closed.
Terminating...

```

Thanks

---

### Post by steefjeqv on 2009-06-20
> **coolercooler said:**
> walterav, this what I did to make lib part work, ```
1 go to ffmpeg dir. 
2 make clean, 
3. use this line "./configure --prefix=/usr --enable-shared --enable-gpl --enable-postproc --enable-libmp3lame --enable-libvorbis --enable-pthreads --enable-libx264 --enable-libtheora --enable-libfaac --enable-libfaad --enable-libxvid --enable-nonfree" 
4 make 
5 make install, 
6 ldconfig -v
```
Then go to xine-lib dir and make clean, then continue from configure part.

But now I have everthing up and running,but I get this error.
@Art2003, do you know whats the cause  of this error.
```
 [8253] [input_vdr] TCP: Buffer too small (8192 ; incoming frame 304666722 bytes)
[8253] [input_vdr] TCP: Buffer too small (8192 ; incoming frame 803865020 bytes)
[8253] [input_vdr] TCP: Buffer too small (8192 ; incoming frame 18868551 bytes)
[8253] [input_vdr] TCP: Buffer too small (8192 ; incoming frame 2079601282 bytes)
[8253] [input_vdr] TCP: Buffer too small (8192 ; incoming frame 2103569677 bytes)
[8253] [input_vdr] TCP: Buffer too small (8192 ; incoming frame 1426004308 bytes)
[8253] [input_vdr] TCP: Delay too long, disconnecting
[8254] [input_vdr] read_block: no data source, returning NULL
[8244] [vdr-fe]    xine_event_cb: XINE_EVENT_UI_PLAYBACK_FINISHED
[8251] [input_vdr] XINE_EVENT_UI_PLAYBACK_FINISHED
[8236] [input_vdr] write_control aborted
[8236] [input_vdr]    (ERROR (xine_input_vdr.c,1024): Resource temporarily unavailable)
[8236] [input_vdr] Connections closed.
Terminating...

```

Thanks

Hi,

Try increasing your videobuffer.

There should be a .xine dir in your home directory (it's a hidden dir).
In this directory there's a config file were you can edit :

Decoder.PesBuffers = 900

and/or

buffer.video_num_buffers (set it to 5000)

Greetings,
Steven

---

### Post by coolercooler on 2009-06-20
> **steefjeqv said:**
> Hi,

Try increasing your videobuffer.

There should be a .xine dir in your home directory (it's a hidden dir).
In this directory there's a config file were you can edit :

Decoder.PesBuffers = 900

and/or

buffer.video_num_buffers (set it to 5000)

Greetings,
Steven

Thanks steefjeqv, still the same problem, it was set to 500, I've increased to 5000, but still keep getting that error.

---

### Post by art2003 on 2009-06-20
You may have mismatching versions of xine-lib, xine-ui and vdr-xine

if you use vdr 1.7.8 
ten use vdr-xine 0.9.3 (the lastest)
and its companion xine-lib and xine-ui

[http://home.vrweb.de/rnissl/](http://home.vrweb.de/rnissl/)

> **coolercooler said:**
> Thanks steefjeqv, still the same problem, it was set to 500, I've increased to 5000, but still keep getting that error.

---

### Post by coolercooler on 2009-06-20
> **art2003 said:**
> You may have mismatching versions of xine-lib, xine-ui and vdr-xine

if you use vdr 1.7.8 
ten use vdr-xine 0.9.3 (the lastest)
and its companion xine-lib and xine-ui

[http://home.vrweb.de/rnissl/](http://home.vrweb.de/rnissl/)

Hi Art2003, once again thanks, up till now I had redone ffmpeg, xine-lib, xine-ui, and as well as deleted vdr folder and redone all of these without success, since in your post you mentioned vdr-xine 0.9.3, otherwise I would not have thought of that, guess must have been some error with it, downloaded again remade the plugin and it started up fine.

Thanks to all the guys who put time in to it, and shearing it.

Now I only have last few question.

1 Once everything is running and am happy with it how do I make backup dvd so to avoid all the problem and pain of doing it again when it breaks, cus it will sooner or later.  Even the network card is working good and I want backup this ubuntu.

2. I used this line in the runvdr file for remote, but it still won't work. ```
-P'remote -l /dev/lircd' \ 
```

3.  Before I lost everything, with remote I added a line to a file somewhere to shutdown pc when green power was pressed on remote, but I can't remember how.  Can you please refresh me.

Thanks

---

### Post by art2003 on 2009-06-21
>>Thanks to all the guys who put time in to it, and shearing it.
You welcome!


>>Now I only have last few question.
>>
>>1 Once everything is running and am happy with it how do I make backup >>dvd so to avoid all the problem and pain of doing it again when it >>breaks, cus it will sooner or later.  Even the network card is working >>good and I want backup this ubuntu.
I use clonezilla, a free download, very easy to use and superior to Norton Ghost since a) It does not install any software anywhere (it is all within the bootable cd) and b) it supports linux (and windows too)


>>2. I used this line in the runvdr file for remote, but it still won't >>work. ```
-P'remote -l /dev/lircd' \ 
```
This tutorial does not use the remote plugin, it is not needed (and I don´t use it), but if you want to play with it then you need to download the source to /usr/local/src/vdr/PLUGINS/src and unpack it plus rename it removing the numbers at the end.


>>3.  Before I lost everything, with remote I added a line to a file >>somewhere to shutdown pc when green power was pressed on remote, but I >>can't remember how.  Can you please refresh me.

In this Howto the intended behaviour of the Green power button on the remote control is as follows: (that is how it is working for me)

a) Within vdr; it closes the xine frontend and returns to the oxine main screen
b) Within the oxine frontend; It displays a shutdown menu where the options are: Shutdown, Reboot or Close oxine
Whatever you select last will be the default option

Also within the oxine frontend main screen at the button there is the option Shutdown which immediately will initiate a halt sequence

---

### Post by daouid on 2009-06-21
Hi again, 

i've tryed many things, but i cannot solve my problem:

i'm experiencing the following on some SD channels:

Green Frames, stuttering, and squares (blocks of video), unwatchable quality

I've tryed using the following plugins with vdr

Streamdev
xine
xineliboutput

i experience the same problem with all of them , so i figured the prob comes from VDR,

i've tryed many versions (1.60 with HD and AC3 patches, 1.7.0 br pack, 1.7.7 from your tutorial, 1.7.8 from your tutorial, 1.7.5 from PPA, 1.60 patched sources for VDPAU and HD support, etc...)

with all of them i experience the same issue,

i've tryed many firmware revision for my card 

i've tryed v4l-dvb from endriss

i've tryed different sc/firmware combination

i dont know what to try next

here is my adapter info:

hwinfo --pci

```
11: PCI 500.0: 11100 Multimedia controller
  [Created at pci.314]
  UDI: /org/freedesktop/Hal/devices/pci_1131_7146
  Unique ID: Ddhb.rUp6vmVfEjA
  Parent ID: 6NW+.two+GgbUMg7
  SysFS ID: /devices/pci0000:00/0000:00:1e.0/0000:05:00.0
  SysFS BusID: 0000:05:00.0
  Hardware Class: dvb card
  Model: "Siemens Nixdorf Fujitsu/Siemens DVB-C card rev1.5"
  Vendor: pci 0x1131 "Philips Semiconductors"
  Device: pci 0x7146 "SAA7146"
  SubVendor: pci 0x110a "Siemens Nixdorf AG"
  SubDevice: pci 0x0000 "Fujitsu/Siemens DVB-C card rev1.5"
  Revision: 0x01
  Driver: "dvb"
  Driver Modules: "saa7146"
  Memory Range: 0xfebffc00-0xfebffdff (rw,non-prefetchable)
  IRQ: 16 (12080012 events)
  Module Alias: "pci:v00001131d00007146sv0000110Asd00000000bc04sc80i00"
  Driver Info #0:
    Driver Status: dvb-ttpci is active
    Driver Activation Cmd: "modprobe dvb-ttpci"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #19 (PCI bridge)

```

lspci -vv

```
05:00.0 Multimedia controller: Philips Semiconductors SAA7146 (rev 01)
    Subsystem: Siemens Nixdorf AG Device 0000
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64 (3750ns min, 9500ns max)
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at febffc00 (32-bit, non-prefetchable) [size=512]
    Kernel driver in use: dvb
    Kernel modules: dvb-ttpci

```

dmesg

```
[ 6497.381000] dvb 0000:05:00.0: PCI INT A disabled
[ 6519.444012] Linux video capture interface: v2.00
[ 6519.457700] saa7146: register extension 'dvb'.
[ 6519.457738] dvb 0000:05:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 6519.458365] saa7146: found saa7146 @ mem f809cc00 (revision 1, irq 16) (0x110a,0x0000).
[ 6519.458374] dvb 0000:05:00.0: firmware: requesting dvb-ttpci-01.fw
[ 6519.471703] DVB: registering new adapter (Fujitsu Siemens DVB-C)
[ 6519.472713] adapter has MAC addr = 00:d0:5c:01:83:72
[ 6519.808088] dvb-ttpci: info @ card 0: firm f0240009, rtsl b0250018, vid 71010068, app 80f22623
[ 6519.808090] dvb-ttpci: firmware @ card 0 supports CI link layer interface
[ 6519.980059] dvb-ttpci: DVB-C w/o analog module @ card 0 detected
[ 6519.988076] saa7146_vv: saa7146 (0): registered device video0 [v4l2]
[ 6519.988090] saa7146_vv: saa7146 (0): registered device vbi0 [v4l2]
[ 6520.048452] DVB: registering adapter 0 frontend 0 (VLSI VES1820 DVB-C)...
[ 6520.048588] input: DVB on-card IR receiver as /devices/pci0000:00/0000:00:1e.0/0000:05:00.0/input/input8
[ 6520.060623] dvb-ttpci: found av7110-0.

```


here is the output vdr-sxfe 

```

vdr-sxfe --audio=alsa  --post tvtime:method=Linear --hud --aspect=16:10 --verbose
vdr-sxfe 1.0.90-cvs  (build with xine-lib 1.1.90, using xine-lib 1.1.90)

Audio driver: alsa
Post plugins: tvtime:method=Linear
HUD OSD mode
Aspect ratio: 16:10
Verbose mode

VDR server not given, searching ...
[7244] [discovery] Reveived broadcast: 66 bytes from 192.168.1.198 
VDR xineliboutput DISCOVERY 1.0
Client: 255.255.255.255:37890


[7244] [discovery] NOT valid discovery message
[7244] [discovery] Reveived broadcast: 97 bytes from 192.168.1.198 
VDR xineliboutput DISCOVERY 1.0
Server port: 37890
Server version: xineliboutput-1.0.90-cvs


[7244] [discovery] Valid discovery message
Found VDR server: host 192.168.1.198, port 37890
[7244] [vdr-sxfe]  sxfe_display_open(width=720, height=576, fullscreen=0, display=(null))
[7244] [vdr-sxfe]  sxfe_display_open: Enabling HUD OSD
[7244] [vdr-sxfe]  Display size : 524 x 331 mm
[7244] [vdr-sxfe]                 1920 x 1200 pixels
[7244] [vdr-sxfe]                 92dpi / 93dpi
[7244] [vdr-sxfe]  Display ratio: 3625.377644/3664.122137 = 0.989426
[7244] [vdr-fe]    Error: The name org.gnome.ScreenSaver was not provided by any .service files
[7244] [vdr-fe]       (ERROR (tools/gnome_screensaver.c,119): Resource temporarily unavailable)
[7244] [vdr-sxfe]  opening HUD OSD window...
[7244] [vdr-sxfe]  find_argb_visual: iteration 0 of 28
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_vo_out_xcbxv.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_sputext.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_sputext.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_vo_out_none.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_image.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_inp_vcd.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_real.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_real.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_vdpau_vc1.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_lpcm.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_xiph.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_xiph.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_xiph.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_xiph.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_xiph.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_inp_net.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_ao_out_file.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_vo_out_opengl.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_inp_rtp.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_rgb.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_mpeg_ts.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_matroska.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_inp_xvdr.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_inp_xvdr.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_mad.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_inp_http.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_real.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_vdr.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_vdr.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_vdr.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_vdr.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_vo_out_raw.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_nsv.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_bitplane.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_inp_file.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_ao_out_none.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_games.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_inp_stdin_fifo.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_inp_dvd.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_vo_out_vdpau.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_vo_out_fb.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_slave.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_nsf.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_nsf.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_inp_pvr.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_gsm610.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/post/xineplug_post_tvtime.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/post/xineplug_post_swscale.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/post/xineplug_post_swscale.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/post/xineplug_post_autocrop.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/post/xineplug_post_switch.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/post/xineplug_post_audiochannel.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/post/xineplug_post_visualizations.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/post/xineplug_post_visualizations.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/post/xineplug_post_visualizations.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/post/xineplug_post_audio_filters.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/post/xineplug_post_audio_filters.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/post/xineplug_post_audio_filters.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/post/xineplug_post_audio_filters.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/post/xineplug_post_planar.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/post/xineplug_post_goom.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/post/xineplug_post_mosaico.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_vo_out_xv.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_vo_out_xv.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_audio.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_inp_smb.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_playlist.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_spucc.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_dts.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_mpeg_pes.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_vdpau_mpeg12.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_w32dll.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_w32dll.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_ao_out_pulseaudio.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_iff.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_inp_gnome_vfs.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_mpeg2.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_spudvb.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_mpc.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_inp_vcdo.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_flv.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_vo_out_aa.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_ao_out_oss.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_vo_out_xcbshm.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_asf.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_faad.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_yuv.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_vo_out_xvmc.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_a52.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_rawdv.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_ao_out_alsa.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_inp_v4l.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_inp_v4l.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_mpeg_elem.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_ff.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_ff.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_ff.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_ff.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_mpeg_block.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_mng.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_dvaudio.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_yuv_frames.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_mpeg.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_avi.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_spucmml.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_pva.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_spu.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_vo_out_xxmc.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_inp_mms.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_vo_out_xshm.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_vo_out_xshm.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_yuv4mpeg2.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_inp_cdda.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_gdk_pixbuf.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_inp_dvb.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_vc1_es.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_fli.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_image.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_vo_out_caca.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_inp_pnm.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_qt.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_qt.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_modplug.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_ao_out_esd.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_inp_rtsp.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_decode_vdpau_h264.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_vo_out_vidix.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_vo_out_vidix.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_vo_out_sdl.so found
load_plugins: plugin /usr/lib/xine/plugins/2.0/xineplug_dmx_qt.so found
vo_vdpau: vdpau API version : 0
vo_vdpau: vdpau implementation description : Unknown
audio_alsa_out : supported modes are 8bit 16bit 24bit 32bit mono stereo (4-channel not enabled in xine config) (4.1-channel not enabled in xine config) (5-channel not enabled in xine config) (5.1-channel not enabled in xine config) (a/52 and DTS pass-through not enabled in xine config)
[7244] [vdr-fe]    Detected 2 CPUs
[7244] [vdr-fe]    Enabling FFmpeg multithreaded video decoding
[7244] [vdr-fe]    static post plugins (from command line): tvtime:method=Linear
[7244] [xine-post]     loaded plugins (type 1.0): tvtime 
Available video drivers: vdpau xv raw opengl xshm caca aa xxmc none sdl vidix vidixfb fb xvmc
Available audio drivers: pulseaudio alsa oss esd none file
Available post plugins:  vdr tvtime warp swscale autocrop switch audiochannel oscope fftscope fftgraph upmix upmix_mono stretch volnorm expand fill invert eq denoise3d boxblur eq2 unsharp pp noise goom mosaico vdr_video vdr_audio
Available input plugins: gnomevfs rtp xvdr http VDR FILE stdin DVD pvr smb VCDO v4l_radio v4l_tv mms CD DVB pnm rtsp tcp VCD
Available demux plugins: xvdr anx image mpeg-ts matroska real nsv wve idcin ipmovie vqa wc3movie roq str film smjpeg fourxm vmd slave nsfdemux aiff flac realaudio snd tta voc vox playlist mpeg_pes iff flashvideo asf mpeg_block mng avi pva yuv4mpeg2 fli modplug quicktime ogg mpeg ac3 dts cdda wav rawdv mpc shn mp3 elem yuv_frames vc1es sputext aac aud
Available audio decoder plugins: gsm610 mad ffmpegaudio realadec vorbis nsfdec mpc a/52 dvaudio speex win32a faad qta dts pcm
Available video decoder plugins: vdpau_mpeg12 vdpau_vc1 mpeg2 gdkpixbuf vdpau_h264 realvdec image ffmpegvideo theora win32v yuv bitplane qtv rgb ffmpeg-wmv8 ffmpeg-wmv9
Available SPU decoder plugins:   spudec spudvb spucmml spucc sputext
[7244] [input_vdr] Symbol SysLogLevel found : value 3
[7244] [input_vdr] Symbol LogToSysLog found : value no
[7244] [input_vdr] init class succeeded
[7244] [input_vdr] vdr_class_get_instance
[7244] [input_vdr] vdr_class_get_instance done.
xine: found input plugin  : VDR (Video Disk Recorder) input plugin
[7244] [input_vdr] vdr_plugin_open_net xvdr://192.168.1.198:37890
[7244] [input_vdr] Connecting (control) to tcp://192.168.1.198:37890 ...
[7244] [input_vdr] setsockopt(SO_RCVBUF): got 262142 bytes
[7244] [input_vdr] Server greeting: VDR-1.7.8 xineliboutput-1.0.90-cvs READY
[7244] [input_vdr] Got Client-ID: 0
[7244] [input_vdr] Connected (control) to tcp://192.168.1.198:37890
[7244] [input_vdr] Connecting (data) to pipe:///video/vdrconf/plugins/xineliboutput/pipes.7158/pipe.0
[7244] [input_vdr] Data stream connected (PIPE)
[7244] [input_vdr] fifo_buffer_new...
[7244] [input_vdr] fifo_buffer_new done.
[7257] [input_vdr] Control thread started
[7258] [input_vdr] Data thread started
input cache plugin disabled
[7244] [demux_vdr] Using decoder "libmpeg2" for mpeg2 video
[7244] [demux_vdr] Using decoder "FFmpeg" for H.264 video
xine: found demuxer plugin: XVDR demux plugin
[7244] [vdr-fe]    re-wiring post plugins
[7244] [xine-post]         wiring     tvtime[out] -> [in]video_out
[7244] [xine-post]         wiring     stream[out] -> [in]tvtime    
[7259] [mpeg-ts  ] PAT acquired count=0 programNumber=0x0084 pmtPid=0x0084
[7259] [demux_vdr] Got PAT, PMT pid = 132, program = 132
[7259] [mpeg-ts  ] PMT: section_syntax: 1
[7259] [mpeg-ts  ]      section_length: 29
[7259] [mpeg-ts  ]      program_number: 0x0084
[7259] [mpeg-ts  ]      version_number: 0
[7259] [mpeg-ts  ]      c/n indicator:  1
[7259] [mpeg-ts  ]      section_number: 0
[7259] [mpeg-ts  ]      last_section_number: 0
[7259] [mpeg-ts  ] parse_pmt: have all TS packets for the PMT section
[7259] [mpeg-ts  ] parse_pmt: new PMT, parsing...
[7259] [mpeg-ts  ] parse_pmt: PMT video pid 0x01f0 type 02
[7259] [mpeg-ts  ] parse_pmt: PMT audio pid 0x01f1 type 04
[7259] [mpeg-ts  ] parse_pmt: PMT pcr pid changed 0x01f0
[7259] [demux_vdr] PMT changed
[7244] [vdr-sxfe]  sxfe_xine_play: Enabling HUD OSD


Press Esc to exit

vo_vdpau: enabled features: inverse_telecine=0
vo_vdpau: disable noise reduction.
vo_vdpau: disable sharpness.
vo_vdpau: vdpau_update_csc: hue=0.000000, saturation=1.000000, contrast=1.000000, brightness=0.000000, color_standard=0
vo_vdpau: skip_chroma = 0
prebuffer=14400 pts
[7257] [vdr-fe]    closing post plugin: tvtime
[7257] [xine-post] Unload tvtime failed: plugin enabled and in use
av_offset=0 pts
vdpau_set_property: property=8, value=100
vdpau_set_property: property=2, value=0
vo_vdpau: vdpau_update_csc: hue=0.000000, saturation=1.000000, contrast=1.000000, brightness=0.000000, color_standard=0
vdpau_set_property: property=3, value=100
vo_vdpau: vdpau_update_csc: hue=0.000000, saturation=1.000000, contrast=1.000000, brightness=0.000000, color_standard=0
vdpau_set_property: property=5, value=0
vo_vdpau: vdpau_update_csc: hue=0.000000, saturation=1.000000, contrast=1.000000, brightness=0.000000, color_standard=0
vdpau_set_property: property=24, value=0
vo_vdpau: disable sharpness.
vdpau_set_property: property=25, value=0
vo_vdpau: disable noise reduction.
vdpau_set_property: property=4, value=100
vo_vdpau: vdpau_update_csc: hue=0.000000, saturation=1.000000, contrast=1.000000, brightness=0.000000, color_standard=0
vdpau_set_property: property=1, value=0
[7257] [vdr-fe]    closing post plugin: upmix
[7257] [vdr-fe]    closing post plugin: autocrop
[7257] [vdr-fe]    closing post plugin: swscale
[7257] [vdr-fe]    closing post plugin: pp
[7257] [vdr-fe]    closing post plugin: unsharp
[7257] [vdr-fe]    closing post plugin: denoise3d
prebuffer=14400 pts
[7259] [input_vdr] BLANK in middle of stream! bufs queue 0 , video_fifo 0
prebuffer=14400 pts
[7259] [mpeg-ts  ] PAT acquired count=0 programNumber=0x0084 pmtPid=0x0084
[7259] [demux_vdr] Got PAT, PMT pid = 132, program = 132
[7259] [mpeg-ts  ] PMT: section_syntax: 1
[7259] [mpeg-ts  ]      section_length: 29
[7259] [mpeg-ts  ]      program_number: 0x0084
[7259] [mpeg-ts  ]      version_number: 0
[7259] [mpeg-ts  ]      c/n indicator:  1
[7259] [mpeg-ts  ]      section_number: 0
[7259] [mpeg-ts  ]      last_section_number: 0
[7259] [mpeg-ts  ] parse_pmt: have all TS packets for the PMT section
[7259] [mpeg-ts  ] parse_pmt: PMT with CRC32=-1951927860 already parsed. Skipping.
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] audio stream changed: 00000000 -> 03010000
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error
[7259] [demux_vdr] ts2es: transport error


```

---

### Post by dado483 on 2009-06-24
> **daouid said:**
> 

[B]Free To Air HD channel wont work

Display bug (squares, green frames, bad rendering) on many SD channels[/B]


Hi, i've same issues using mythtv.
What DVB drivers are you using?!?

I'm using s2-liplianin rev.10341 from mercurial repo, if i use head revision, i've your same issues.
With rev.10341 all work great!

Hope to help you!

dado483

---

### Post by steefjeqv on 2009-06-24
Hi,

@ daouid

When you combine VDPAU with xineliboutput, start your frontend like this :

vdr-sxfe --audio=alsa --post tvtime:method=use_vo_driver --hud --aspect=16:10 --verbose

It may be possible that your primary DVB card is setup to use your hardware mpeg2 decoder.
Try changing this in your /etc/vdr/setup.conf. Look for a line called :

PrimaryDVB = 1

Try changing this to 0 or 2.

Greetings,
Steven

---

### Post by daouid on 2009-06-24
> **dado483 said:**
> Hi, i've same issues using mythtv.
What DVB drivers are you using?!?

I'm using s2-liplianin rev.10341 from mercurial repo, if i use head revision, i've your same issues.
With rev.10341 all work great!

Hope to help you!

dado483

Thx for the advice, but im using the following DVB driver "v4l-dvb" from endriss

i had the same issue with v4l-dvb from linuxtv.

---

### Post by daouid on 2009-06-24
> **steefjeqv said:**
> Hi,

@ daouid

When you combine VDPAU with xineliboutput, start your frontend like this :

vdr-sxfe --audio=alsa --post tvtime:method=use_vo_driver --hud --aspect=16:10 --verbose

It may be possible that your primary DVB card is setup to use your hardware mpeg2 decoder.
Try changing this in your /etc/vdr/setup.conf. Look for a line called :

PrimaryDVB = 1

Try changing this to 0 or 2.

Greetings,
Steven


Hi Steven, 

I've tried using doing the changes you suggested,

```
--post tvtime:method=use_vo_driver
```and i've tried setting 

```
PrimaryDVB = 2
```That didnt work, 

and i tried setting 

```
PrimaryDVB = 0
```but everytime i checked back setup.conf, 

it would reverse to 

```
PrimaryDVB = 1
```maybe this is the problem, 

that im using my DVB internal MPEG chip to decode the stream, instead of software method,

any ideas how i could "fix" this, and force VDR / vdr-sxfe to use only SOFTWARE DECODING

i dont realy need VDPAU support, i just hope to fix my problem first, then after maybe tweak it.

Thx for the help, and looking forward more answers :KS

Edit:  i'm currently looking at 

[http://softdevice.berlios.de/](http://softdevice.berlios.de/)

[http://www.vdr-wiki.de/wiki/index.php/Softdevice-plugin](http://www.vdr-wiki.de/wiki/index.php/Softdevice-plugin)

maybe this is what i need

---

### Post by steefjeqv on 2009-06-25
Hi,

daouid, these FF cards sometimes have trouble with QAM256 modulation.

Check your /etc/vdr/channels.conf. Any line that mentions M256 may give you trouble.

Greetings.
Steven

---

### Post by ashaheen on 2009-06-25
dear [art2003]("http://ubuntuforums.org/member.php?u=33454")
i have smae HW but i have ATI radion 4350 and did instalation on ubentu V 8.4  every thing working  but sound canot come via HDMA on VDR  but it work in normal media player

---

### Post by art2003 on 2009-07-03
The config files here are for OSS but you are using ALSA right?
In OSS /dev/oss/oss_hdaudio0/spdout1  is the HDMI output for the motherboard used in this tutorial (the one I have) and possibly for others with similar chipset

I never managed to get HDMI sound output to work with ALSA and my motherboard (I am considering replacing my motherboard with an ASUS one which I hear has HDMI sound working out of the box with ALSA) 

> **ashaheen said:**
> dear [art2003]("http://ubuntuforums.org/member.php?u=33454")
i have smae HW but i have ATI radion 4350 and did instalation on ubentu V 8.4  every thing working  but sound canot come via HDMA on VDR  but it work in normal media player

---

### Post by Sav on 2009-07-03
Hi, I experienced some freezes with xine-liboutput plugin and with the xine plugin.
The number of freezes increase with the sc plugin.
I use the latest s2-liplain drivers with a clone of the skystar hd 2 card and a geforce 9400 with vdpau enabled.

---

### Post by art2003 on 2009-07-04
I hear the skystart 2 HD is not very good...

> **Sav said:**
> Hi, I experienced some freezes with xine-liboutput plugin and with the xine plugin.
The number of freezes increase with the sc plugin.
I use the latest s2-liplain drivers with a clone of the skystar hd 2 card and a geforce 9400 with vdpau enabled.

---

### Post by Sav on 2009-07-07
In the windows environment all seems fine, without freezes.
In the linux box, with the softplugin I had no problems.
The issue is with xine or xine liboutput.

---

### Post by art2003 on 2009-07-07
or possibly the sky star hd hasn´t got very good linux drivers?
You could try the irc channel #xine-vdpau for help 
but I am sorry I am not a xine developer nor did I write the drivers for the sky star HD

> **Sav said:**
> In the windows environment all seems fine, without freezes.
In the linux box, with the softplugin I had no problems.
The issue is with xine or xine liboutput.

---

### Post by Earthfinder on 2009-07-08
@ Art2003: It seems like a great walkthrough!
But I'm wondering. How stable is this setup, of yours? Because you're using VDR 1.7.8. I thought, that was not yet a stable release...

---

### Post by Sav on 2009-07-08
I upgraded to 1.7.8 (maybe your xinelib is faster), but now the CCcam won't start, without any errors!

---

### Post by art2003 on 2009-07-08
Only vdr 1.7.x support HD channels.
But from vdr 1.7.7 onwards the author himself uses it on a daily basis so must be close to a stable release

> **Earthfinder said:**
> @ Art2003: It seems like a great walkthrough!
But I'm wondering. How stable is this setup, of yours? Because you're using VDR 1.7.8. I thought, that was not yet a stable release...

---

### Post by art2003 on 2009-07-08
may be the sc plugin did not recompile? check vdr -V

> **Sav said:**
> I upgraded to 1.7.8 (maybe your xinelib is faster), but now the CCcam won't start, without any errors!

---

### Post by Sav on 2009-07-10
> **art2003 said:**
> may be the sc plugin did not recompile? check vdr -V

SC plugin recompile just fine.
The issue is with the CCcam daemon: it doesn't start, but apparently it does. I don't know what it can be: there is nothing in the log file of the CCcam.

---

### Post by malakudi on 2009-07-13
First of all, one question. Where can I get the plugin chanman 0.0.8 which is referenced in the 1st post?

The guide is really good, but I have some problems.

Problem number 1: If I use the alsa upgrade script to upgrade my alsa version to 1.0.20 , then the s2-liplianin v4l does not build correctly. I even changed the alsa headers in the linux-headers path but it still doesn't build correctly (all alsa related modules fail). I must say here that in 2.6.30 which has 1.0.20 already in the kernel, s2-liplianin builds fine. But i don't want to change kernel for now, unless I have to.

Problem number 2 (fixed): In the first post, the ffmpeg building command is wrong. It should include --enable-shared, or else xine-lib-1.2 does not build. This is mentioned in page 13 of this thread, but it would be nice to update first post to save people time.

Problem number 3: I am not using VDPAU. I downloaded latest sources for x264, ffmpeg, xine-lib 1.2 and xine-ui. xine-vdr works, but for most H.264 streams found in european DVB-S2 transmitions, it can't decode multithreaded. When decoding starts, in the log I get:
Cannot parallelize deblocking type 1, decoding such frames in sequential order
and then only one core is used, thus droping frames. Is there any workaround for this?

---

### Post by Asxetos on 2009-07-20
Hi All,

I am practically a newbie in linux when it comes to compiling stuff, but experienced enough to get around problems. 
My system is: Asus PQ5 mb with a Core2duo 2,66 cpu and Ubuntu Jaunty 9.04 desktop installed, Asus 9400gt graphics with HDMI out and a Hauppauge HVR-4000.

Sound over HDMI works fine with this setup, with default ALSA and only some audio settings adjustment.


Anyway, i am trying to built my system following the guide, and in this point i am stuck:

1.
Ffmpeg building does not complete successfully (build a deb). Instead if i:

make
make install
ldconfig -v

it completes with no error (is that OK, or will it cause problems later?).

2.
Softcam plugin does not build.

When i "make plugins", the "failed plugins: sc" comes up.
Perhaps something is broken in the latest trunk of sc?
I am thinking of trying version 0.9.2 - 0.9.1 etc until it builds.


Any help would be greatly appreciated.

Asxetos...

---

### Post by walterav on 2009-07-28
I was able to make VDR run with the HOWTO from the following link, I do had to compile vdr with dvb-S2 even though I have a old budget card!

[http://www.eurocardsharing.com/f273/howto-vdr-1-7-8-hdtv-vdpau-cccam-budget-cards-ubuntu-9-04-using-s2api-142317](http://www.eurocardsharing.com/f273/howto-vdr-1-7-8-hdtv-vdpau-cccam-budget-cards-ubuntu-9-04-using-s2api-142317)

I just don't know howto zap/change channels, because I don't have a remote, anyone suggestions?

---

### Post by art2003 on 2009-07-29
1. ffmpeg: yes, make && make install && ldconfig -v
is ok 

2. sc 0.9.2 compiled fine for me

3. try cursors (up and down arrows) to zap channels

---

### Post by kicker4748 on 2009-08-18
Hello, 

I've followed your tutorial and almost everything is working for me, besides Xine-UI. Although I have a keymap-file in my .xine directory the xine-vdr plugin does not respond to keystrokes in regard to the vdr functions. The commands for the xine-ui itself are functional though. 

Do you have an idea what could possibly fit that problem?

Thanks,

kicker4748

--------------------
P.S. Okay, I found the solution. I just forgot the single quotes for the plugin xine. -P 'xine -r' worked for me.

---

### Post by art2003 on 2009-08-18
first, check that lirc is running
ps -A |grep lirc

if it isn't then run
sudo /etc/init.d/lirc start

---

### Post by b3t0n on 2009-08-18
Hi there.
I've got problem while compiling sc plugin. I'm using 9.04 - 32-bit version.

Here's the log.```
Plugin sc:
make[1]: Entering directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/sc'
make[2]: Entering directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/sc/systems/cardclient'
make[2]: Leaving directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/sc/systems/cardclient'
make[2]: Entering directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/sc/systems/conax'
make[2]: Leaving directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/sc/systems/conax'
make[2]: Entering directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/sc/systems/constcw'
make[2]: Leaving directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/sc/systems/constcw'
make[2]: Entering directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/sc/systems/cryptoworks'
make[2]: Leaving directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/sc/systems/cryptoworks'
make[2]: Entering directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/sc/systems/irdeto'
make[2]: Leaving directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/sc/systems/irdeto'
make[2]: Entering directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/sc/systems/nagra'
make[2]: Leaving directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/sc/systems/nagra'
make[2]: Entering directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/sc/systems/nds'
make[2]: Leaving directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/sc/systems/nds'
make[2]: Entering directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/sc/systems/sc-conax'
make[2]: Leaving directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/sc/systems/sc-conax'
make[2]: Entering directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/sc/systems/sc-cryptoworks'
make[2]: Leaving directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/sc/systems/sc-cryptoworks'
make[2]: Entering directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/sc/systems/sc-irdeto'
make[2]: Leaving directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/sc/systems/sc-irdeto'
make[2]: Entering directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/sc/systems/sc-nagra'
make[2]: Leaving directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/sc/systems/sc-nagra'
make[2]: Entering directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/sc/systems/sc-seca'
make[2]: Leaving directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/sc/systems/sc-seca'
make[2]: Entering directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/sc/systems/sc-viaccess'
make[2]: Leaving directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/sc/systems/sc-viaccess'
make[2]: Entering directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/sc/systems/sc-videoguard2'
make[2]: Leaving directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/sc/systems/sc-videoguard2'
make[2]: Entering directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/sc/systems/seca'
make[2]: Leaving directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/sc/systems/seca'
make[2]: Entering directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/sc/systems/shl'
make[2]: Leaving directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/sc/systems/shl'
make[2]: Entering directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/sc/systems/viaccess'
make[2]: Leaving directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/sc/systems/viaccess'
make[2]: Entering directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/sc/contrib'
gcc -O3 -o bsdiff bsdiff.c -lbz2
bsdiff.c:33:19: error: bzlib.h: No such file or directory
bsdiff.c: In function &#8216;main&#8217;:
bsdiff.c:213: error: &#8216;BZFILE&#8217; undeclared (first use in this function)
bsdiff.c:213: error: (Each undeclared identifier is reported only once
bsdiff.c:213: error: for each function it appears in.)
bsdiff.c:213: error: &#8216;pfbz2&#8217; undeclared (first use in this function)
bsdiff.c:336: error: &#8216;BZ_OK&#8217; undeclared (first use in this function)
make[2]: *** [bsdiff] Error 1
make[2]: Leaving directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/sc/contrib'
make[1]: *** [contrib] Error 2
make[1]: Leaving directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/sc'
Plugin servicedemo:
make[1]: Entering directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/servicedemo'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/servicedemo'
Plugin setup:
make[1]: Entering directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/setup-0.3.1-zulu-edition'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/setup-0.3.1-zulu-edition'
Plugin skincurses:
make[1]: Entering directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/skincurses'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/skincurses'
Plugin sky:
make[1]: Entering directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/sky'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/sky'
Plugin status:
make[1]: Entering directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/status'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/status'
Plugin streamdev:
make[1]: Entering directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/streamdev'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/streamdev'
Plugin svdrpdemo:
make[1]: Entering directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/svdrpdemo'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/svdrpdemo'

*** failed plugins: sc

make: *** [plugins] Error 1


```Anyone knows what may be causing this?

---

### Post by mitsus on 2009-08-19
> **b3t0n said:**
> Hi there.
I've got problem while compiling sc plugin. I'm using 9.04 - 32-bit version.

Here's the log.```
Plugin sc:
make[1]: Entering directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/sc'
make[2]: Entering directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/sc/systems/cardclient'
make[2]: Leaving directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/sc/systems/cardclient'
make[2]: Entering directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/sc/systems/conax'
make[2]: Leaving directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/sc/systems/conax'
make[2]: Entering directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/sc/systems/constcw'
make[2]: Leaving directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/sc/systems/constcw'
make[2]: Entering directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/sc/systems/cryptoworks'
make[2]: Leaving directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/sc/systems/cryptoworks'
make[2]: Entering directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/sc/systems/irdeto'
make[2]: Leaving directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/sc/systems/irdeto'
make[2]: Entering directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/sc/systems/nagra'
make[2]: Leaving directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/sc/systems/nagra'
make[2]: Entering directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/sc/systems/nds'
make[2]: Leaving directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/sc/systems/nds'
make[2]: Entering directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/sc/systems/sc-conax'
make[2]: Leaving directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/sc/systems/sc-conax'
make[2]: Entering directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/sc/systems/sc-cryptoworks'
make[2]: Leaving directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/sc/systems/sc-cryptoworks'
make[2]: Entering directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/sc/systems/sc-irdeto'
make[2]: Leaving directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/sc/systems/sc-irdeto'
make[2]: Entering directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/sc/systems/sc-nagra'
make[2]: Leaving directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/sc/systems/sc-nagra'
make[2]: Entering directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/sc/systems/sc-seca'
make[2]: Leaving directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/sc/systems/sc-seca'
make[2]: Entering directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/sc/systems/sc-viaccess'
make[2]: Leaving directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/sc/systems/sc-viaccess'
make[2]: Entering directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/sc/systems/sc-videoguard2'
make[2]: Leaving directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/sc/systems/sc-videoguard2'
make[2]: Entering directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/sc/systems/seca'
make[2]: Leaving directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/sc/systems/seca'
make[2]: Entering directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/sc/systems/shl'
make[2]: Leaving directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/sc/systems/shl'
make[2]: Entering directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/sc/systems/viaccess'
make[2]: Leaving directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/sc/systems/viaccess'
make[2]: Entering directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/sc/contrib'
gcc -O3 -o bsdiff bsdiff.c -lbz2
bsdiff.c:33:19: error: bzlib.h: No such file or directory
bsdiff.c: In function ‘main’:
bsdiff.c:213: error: ‘BZFILE’ undeclared (first use in this function)
bsdiff.c:213: error: (Each undeclared identifier is reported only once
bsdiff.c:213: error: for each function it appears in.)
bsdiff.c:213: error: ‘pfbz2’ undeclared (first use in this function)
bsdiff.c:336: error: ‘BZ_OK’ undeclared (first use in this function)
make[2]: *** [bsdiff] Error 1
make[2]: Leaving directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/sc/contrib'
make[1]: *** [contrib] Error 2
make[1]: Leaving directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/sc'
Plugin servicedemo:
make[1]: Entering directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/servicedemo'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/servicedemo'
Plugin setup:
make[1]: Entering directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/setup-0.3.1-zulu-edition'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/setup-0.3.1-zulu-edition'
Plugin skincurses:
make[1]: Entering directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/skincurses'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/skincurses'
Plugin sky:
make[1]: Entering directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/sky'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/sky'
Plugin status:
make[1]: Entering directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/status'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/status'
Plugin streamdev:
make[1]: Entering directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/streamdev'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/streamdev'
Plugin svdrpdemo:
make[1]: Entering directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/svdrpdemo'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/usr/local/src/vdr-1.7.8/PLUGINS/src/svdrpdemo'

*** failed plugins: sc

make: *** [plugins] Error 1


```Anyone knows what may be causing this?

Try to install:
```

apt-get install libssl-dev 
apt-get install libbz2-dev

```


...i think that you don't have these libraries.

Regards

---

### Post by mocha on 2009-08-20
> **coolercooler said:**
> [COLOR="Red"]The problem was with configure part of ffmpeg and I used another tutorial on the web to get around and fix.[/COLOR]

Since then rest of the install went fine, but for some reason can't launch xine now even though it was working, when I tested after install.

This is the error.

```
xine: error while loading shared libraries: libxine.so.2: cannot open shared object file: No such file or directory
 
```


Care to share what you did?  I'm having the same problem trying to compile xine-vdpau on a Ubuntu system that I compiled my own ffmpeg on.  Thanks.

---

### Post by b3t0n on 2009-08-20
> **mitsus said:**
> Try to install:
```

apt-get install libssl-dev 
apt-get install libbz2-dev

```
...i think that you don't have these libraries.

Regards

Thanks. Somehow I missed libbz2-dev.

---

### Post by phelin4 on 2009-08-23
Anyone tried to run vdr + sc-plugin on Karmic (Ubuntu 9.10) yet? I have everything else regarding vdr running smoothly, but cannot get the sc-plugin to work. I have the exact same version of the plugin and vdr (minus some gcc 4.4 required fixes on vdr source) on Ubuntu 9.04, which is working splendidly. On 9.10 all I get on an encrypted channel is black video, audio and subtitles work though. 

I have my subscription card in a phoenix card reader, which is connected via USB as /dev/ttyUSB0. The sc-plugin recognizes the card and that it is of type Conax. When tuning to an encrypted channel, the sc-plugin tells that it has found a correct key and everything else in the log looks ok also. But, as I said, I get no picture.

---

### Post by SeanCorky on 2009-09-03
Would you not consider posting the image to Usenet or a Torrent?

---

### Post by art2003 on 2009-09-03
I have a very slow internet connection at home, torrents are out of question.

if somebody has a rapidshare premium account or something like that...
we are talking of a 2Gbytes .rar file which can of course be split in chunks

---

### Post by maidiremaik on 2009-09-06
I've got many many problems with plugin rotor on my vdr 1.7.9. can U help me?

---

### Post by Sav on 2009-09-06
> **phjr said:**
> when I try to build vdr (i.e. run make in /usr/local/src/vdr) I get the error below; note that I'm running Ubuntu 9.04 64bit - anybody has idea what could be wrong?

```
g++ -g -O2 -Wall -Woverloaded-virtual -Wno-parentheses -c -DUSE_SETUP -DREMOTE_KBD -DLIRC_DEVICE=\"/dev/lircd\" -DRCU_DEVICE=\"/dev/input/ttyS1\" -D_GNU_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_LARGEFILE64_SOURCE -DVIDEODIR=\"/media/video/vdr\" -DCONFDIR=\"/etc/vdr\" -DPLUGINDIR=\"/usr/lib/vdr/plugins\" -DLOCDIR=\"/usr/share/locale\" -I/usr/include/freetype2 -I/usr/local/src/s2-liplianin/linux/include dvbdevice.c
In file included from /usr/include/netinet/in.h:24,
                 from /usr/include/arpa/inet.h:23,
                 from config.h:13,
                 from channels.h:13,
                 from device.h:13,
                 from dvbdevice.h:15,
                 from dvbdevice.c:10:
/usr/include/stdint.h:41: error: conflicting declaration ‘typedef long int int64_t’
/usr/include/linux/types.h:98: error: ‘int64_t’ has a previous declaration as ‘typedef __s64 int64_t’
/usr/include/stdint.h:56: error: conflicting declaration ‘typedef long unsigned int uint64_t’
/usr/include/linux/types.h:96: error: ‘uint64_t’ has a previous declaration as ‘typedef __u64 uint64_t’
In file included from /usr/include/sys/uio.h:24,
                 from /usr/include/sys/socket.h:28,
                 from /usr/include/netinet/in.h:25,
                 from /usr/include/arpa/inet.h:23,
                 from config.h:13,
                 from channels.h:13,
                 from device.h:13,
                 from dvbdevice.h:15,
                 from dvbdevice.c:10:
/usr/include/sys/types.h:46: error: conflicting declaration ‘typedef __loff_t loff_t’
/usr/include/linux/types.h:30: error: ‘loff_t’ has a previous declaration as ‘typedef __kernel_loff_t loff_t’
/usr/include/sys/types.h:62: error: conflicting declaration ‘typedef __dev_t dev_t’
/usr/include/linux/types.h:13: error: ‘dev_t’ has a previous declaration as ‘typedef __kernel_dev_t dev_t’
In file included from /usr/include/sys/types.h:133,
                 from /usr/include/sys/uio.h:24,
                 from /usr/include/sys/socket.h:28,
                 from /usr/include/netinet/in.h:25,
                 from /usr/include/arpa/inet.h:23,
                 from config.h:13,
                 from channels.h:13,
                 from device.h:13,
                 from dvbdevice.h:15,
                 from dvbdevice.c:10:
/usr/include/time.h:105: error: conflicting declaration ‘typedef void* timer_t’
/usr/include/linux/types.h:22: error: ‘timer_t’ has a previous declaration as ‘typedef __kernel_timer_t timer_t’
In file included from /usr/include/sys/uio.h:24,
                 from /usr/include/sys/socket.h:28,
                 from /usr/include/netinet/in.h:25,
                 from /usr/include/arpa/inet.h:23,
                 from config.h:13,
                 from channels.h:13,
                 from device.h:13,
                 from dvbdevice.h:15,
                 from dvbdevice.c:10:
/usr/include/sys/types.h:204: error: conflicting declaration ‘typedef long unsigned int u_int64_t’
/usr/include/linux/types.h:97: error: ‘u_int64_t’ has a previous declaration as ‘typedef __u64 u_int64_t’
In file included from /usr/include/sys/types.h:220,
                 from /usr/include/sys/uio.h:24,
                 from /usr/include/sys/socket.h:28,
                 from /usr/include/netinet/in.h:25,
                 from /usr/include/arpa/inet.h:23,
                 from config.h:13,
                 from channels.h:13,
                 from device.h:13,
                 from dvbdevice.h:15,
                 from dvbdevice.c:10:
/usr/include/sys/select.h:78: error: conflicting declaration ‘typedef struct fd_set fd_set’
/usr/include/linux/types.h:12: error: ‘fd_set’ has a previous declaration as ‘typedef struct __kernel_fd_set fd_set’
In file included from /usr/include/sys/uio.h:24,
                 from /usr/include/sys/socket.h:28,
                 from /usr/include/netinet/in.h:25,
                 from /usr/include/arpa/inet.h:23,
                 from config.h:13,
                 from channels.h:13,
                 from device.h:13,
                 from dvbdevice.h:15,
                 from dvbdevice.c:10:
/usr/include/sys/types.h:248: error: conflicting declaration ‘typedef __blkcnt64_t blkcnt_t’
/usr/include/linux/types.h:124: error: ‘blkcnt_t’ has a previous declaration as ‘typedef long unsigned int blkcnt_t’
make: *** [dvbdevice.o] Error 1

```EDIT: seems that this is a known bug in a debian package, see [http://www.mail-archive.com/debian-kernel@lists.debian.org/msg44521.html](http://www.mail-archive.com/debian-kernel@lists.debian.org/msg44521.html)

I don't know how to solve it though :-(

I manage to compile vdr in a 64 bit environment thanks to Shdo, user of [http://vdr-portal.de](http://vdr-portal.de) board.

The Makefile needs some changes, after the vdr patches are applied.
So, in the vdr folder
> sudo gedit Makefile

Search for this lines
> DEFINES += -D_GNU_SOURCE
 
DEFINES += -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_LARGEFILE64_SOURCE

Insert riht after
> DEFINES += -D__KERNEL_STRICT_NAMES
Save and exit gedit

Then, you can compile vdr

---

### Post by maidiremaik on 2009-09-07
> **maidiremaik said:**
> I've got many many problems with plugin rotor on my vdr 1.7.9. can U help me?

up

---

### Post by SeanCorky on 2009-09-07
PM'ed regarding FTP server ;)

---

### Post by eiki2 on 2009-09-08
Found the solution: the ** Setup plugin** (I did not include it)....


I get the following error when i run /etc/init.d/vdr start:
vdr: /usr/lib/vdr/plugins/libvdr-setup.so.1.7.8: cannot open shared object file: No such file or directory

When i disable the sc plugin I get no error messages and vdr starts.

---

### Post by coolercooler on 2009-09-14
Are you guys when scanning 28.2E get lock on S2 channels? using w_scan, I can't find or lock on to S2 channels.  I keep getting this error message.

```
tune to: S2 f = 12324 kHz V SR = 29500  3/4 0,35  QPSK 
(time: 33:00) ----------no signal----------
tune to: S2 f = 12324 kHz V SR = 29500  3/4 0,35  QPSK  (no signal)
(time: 33:05) ----------no signal----------
tune to: S2 f = 11797 kHz H SR = 29500  3/4 0,35  QPSK 
(time: 33:09) ----------no signal----------
tune to: S2 f = 11797 kHz H SR = 29500  3/4 0,35  QPSK  (no signal)
(time: 33:14) ----------no signal----------
tune to: S2 f = 12343 kHz H SR = 29500  3/4 0,35  QPSK 
(time: 33:18) ----------no signal----------
tune to: S2 f = 12343 kHz H SR = 29500  3/4 0,35  QPSK  (no signal)
(time: 33:23) ----------no signal----------
tune to: S2 f = 11719 kHz H SR = 29500  3/4 0,35  QPSK 
(time: 33:28) ----------no signal----------
tune to: S2 f = 11719 kHz H SR = 29500  3/4 0,35  QPSK  (no signal)
(time: 33:32) ----------no signal----------

```

I've even tried using this line ```
 w_scan -F -t3 -fs -s S28E2 -o7 >> /to/where/Desktop/channels.conf
```to gave it extra time, but still get the same error message. But if I download and add channels to vdr they lock and work.  Just can't seem to scan them.

Thanks

---

### Post by art2003 on 2009-09-15
I wrote to the author of w_scan and his reply was:

I see three possibilities:
- some rotor or diseqc switch in between and tuning will fail at all without correct settings
- this dvb card cannot handle symbolrate 29500
- rolloff 0.35 is wrong

---

### Post by art2003 on 2009-09-15
check the first post for a link to download my vdr-1.7.9 with patches and plugins just ready to do make install

---

### Post by coolercooler on 2009-09-16
> **art2003 said:**
> I wrote to the author of w_scan and his reply was:

I see three possibilities:
- some rotor or diseqc switch in between and tuning will fail at all without correct settings
- this dvb card cannot handle symbolrate 29500
- rolloff 0.35 is wrong

Hi, am inclining to think it maybe rolloff 0.35, as when I add channels manually I have to go and edit rolloff from auto to 0.35 to get a lock.  So how would one go about and add that in the w_scan line?

If the card could not handle symbolrate 29500 then they should not work when manually added?

---

### Post by faunk on 2009-09-23
> **art2003 said:**
> check the first post for a link to download my vdr-1.7.9 with patches and plugins just ready to do make install

could you please upload it in another online server because from ziddu starts downloading very slow and then fails to download the file.thank you very much.

OK: i downloaded the file.thank you very much for all the good job!!

---

### Post by eiki2 on 2009-09-25
Great job!! I downloaded the 1.7.9 with all the plugins. Fantastic job and thanks for sharing.

I am not able get the skinenigmang to work. I get the following error message:
vdr: libMagick++.so.10: cannot open shared object file: No such file or directory

Can you please provide your /var/bin/runvdr file with all the plugins loaded? Some might start with spesial options...?

Also, how can I make the remote repeat when I want to scroll down ex. channel list? I prefer not to tap the up button for each time I would like to go up in a list... I am using the same remote as in the tutorial.

---

### Post by leechguy on 2009-09-29
> **boba23 said:**
> hey art, 
 
thanks for the reply.
I got vdr now basically up and running. I got trouble compiling ca.c though. I am on Jaunty, and get the following error when trying to compile:
 
$ gcc -O -fbuiltin -fomit-frame-pointer -fPIC -shared -o ca.so ca.c -ldl
ca.c:106: error: expected â,â or â;â before â{â token
ca.c: In function âcactlâ:
ca.c:233: error: expected expression before â<â token
 
any ideas?
 
boba
 
 
This is caused by some html code in ca.c:
 
```

#ifdef DEBUG
  printf ("hijacking ca%d ioctl,"
       "(%d : %x - %p): ",card, fd, request, argp);
  switch (request) {
  case CA_RESET:
    printf ("CA_RESET\n");
    break;
  case CA_GET_CAP:
    printf ("CA_GET_CAP\n"); [COLOR=red]<button>[/COLOR]
[COLOR=red] <title>Shutdown VDR</title>[/COLOR]
[COLOR=red] <action type="shellcommand" parameter="/etc/init.d/vdr stop"/>[/COLOR]
[COLOR=red]</button>[/COLOR]
    break;
  case CA_GET_SLOT_INFO:
    printf ("CA_GET_SLOT_INFO\n");
    break;
 

```
 
 
Simply remove the html code at lines 233-236.

---

### Post by art2003 on 2009-09-30
About the remote repeat, I don't know and wish I did. I read it is a hardware limitation? If anybody has some idea how to get this working I would be the first one interested.

Here is my /var/bin/runvdr , notice that I use the pluginsetup which allows you to easily turn on and off plugins. So I hope you downloaded my 1.7.9 WITH config files ( most of them on /etc/vdr )

About the libmagick error with skinenigma, yes I saw that error too, it happens only in Jaunty. I am sure there is a patch somewhere...

```

#!/bin/sh
export LANG=en_EN
export LC_COLLATE=en_EN

PATH=/usr/local/bin:$PATH

VDRPRG="/usr/bin/vdr"
VDRCMD="/usr/bin/vdr -c /etc/vdr -E /var/epgvdr --lirc --no-kbd -l 1 -P sc -P'xine -r' -P setup "
ALL_PLUGINS="-P pluginsetup `grep -s - /etc/vdr/plugins/plugin_setup_runvdr.conf`"


KILL="/usr/bin/killall -q -TERM"

# Detect whether the DVB driver is already loaded
# and return 0 if it *is* loaded, 1 if not:
DriverLoaded()
{
  return 1
}
# Load all DVB driver modules needed for your hardware:
LoadDriver ()
{

  return 0

}

# Unload all DVB driver modules loaded in LoadDriver():
UnloadDriver ()
{

  return 0

}



```

> **eiki2 said:**
> Great job!! I downloaded the 1.7.9 with all the plugins. Fantastic job and thanks for sharing.

I am not able get the skinenigmang to work. I get the following error message:
vdr: libMagick++.so.10: cannot open shared object file: No such file or directory

Can you please provide your /var/bin/runvdr file with all the plugins loaded? Some might start with spesial options...?

Also, how can I make the remote repeat when I want to scroll down ex. channel list? I prefer not to tap the up button for each time I would like to go up in a list... I am using the same remote as in the tutorial.

---

### Post by eiki2 on 2009-09-30
Thanks! I´ll give that a try.

About the repeating. I changed the settings in /etc/lirc/lircd.conf. These setting works perfectly with repeatitions;

```

begin remote

  name  Hauppauge-HVR4000-Remote
  bits           16
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  pre_data_bits   16
  pre_data       0x8001
  gap          133325
  toggle_bit_mask 0x8001001C

      begin codes
          Power                    0x0074
          Go                       0x0161
          TV                       0x0179
          Video                    0x0189
          Music                    0x0188
          Pictures                 0x016F
          Guide                    0x016D
          Radio                    0x0181
          Up                       0x0067
          Down                     0x006C
          Left                     0x0069
          Right                    0x006A
          OK                       0x001C
          Back/Exit                0x00AE
          Menu                     0x008B
          PrevCh                   0x019C
          Mute                     0x0071
          Vol+                     0x0073
          Vol-                     0x0072
          Ch+                      0x0192
          Ch-                      0x0193
          Rec                      0x00A7
          Stop                     0x0080
          Play                     0x00CF
          Pause                    0x0077
          Rewind                   0x00A8
          Forward                  0x00D0
          Replay                   0x00A5
          Skip                     0x00A3
          1                        0x0002
          2                        0x0003
          3                        0x0004
          4                        0x0005
          5                        0x0006
          6                        0x0007
          7                        0x0008
          8                        0x0009
          9                        0x000A
          0                        0x000B
          Text                     0x0184
          Sub/CC                   0x0172
          Red                      0x018E
          Green                    0x018F
          Yellow                   0x0190
          Blue                     0x0191
      end codes

end remote

```

---

### Post by art2003 on 2009-10-01
eiki2, thanks a lot for your contribution,

I works fine and I have updated the first thread so now key repeat (notably holding down the volume up/down keys)
works just fine

---

### Post by anis745 on 2009-10-02
> **art2003 said:**
> eiki2, thanks a lot for your contribution,

I will test tonight if it works fine (I see no reason why not)

[COLOR="Red"]Thank you for this excellent tutorial.
I already installed vdr1.6.0. help me to run CCcam with vdr1.6.0.car I tried several times without success and how to configure cccam.cfg. step by step[/COLOR]

---

### Post by Wilb on 2009-10-03
> **coolercooler said:**
> Are you guys when scanning 28.2E get lock on S2 channels? using w_scan, I can't find or lock on to S2 channels.  I keep getting this error message.


Similar for me - ended up building scan-s2 [http://mercurial.intuxication.org/hg/scan-s2](http://mercurial.intuxication.org/hg/scan-s2) and using that to scan my S2 transponders and then combined the output with my S1 channel list.

---

### Post by faunk on 2009-10-04
Hi to all.I 'm about to finish my vdr pc and i would like to ask about what DVB-S2 card you advise me. With my budget i can buy this:
TechnoTrend TT-budget S2-3200 + CI 
TERRATEC Cinergy S2 HD + CI
Technisat SkyStar HD2 + CI 

i'm waiting for your help.thank you.

---

### Post by art2003 on 2009-10-06
Here is a revised w_scan that should pickup the DVB-S2 channels on 28e

[http://www.ziddu.com/download/6797072/w_scan-20091004.tar.rar.html](http://www.ziddu.com/download/6797072/w_scan-20091004.tar.rar.html)

---

### Post by Wilb on 2009-10-06
> **art2003 said:**
> Here is a revised w_scan that should pickup the DVB-S2 channels on 28e

[http://www.ziddu.com/download/6797072/w_scan-20091004.tar.rar.html](http://www.ziddu.com/download/6797072/w_scan-20091004.tar.rar.html)

Not for me - just done a quick scan using:
> 
w_scan -fs -s S28E2 -o7 > channels.conf

but if I 
> 
grep HD channels.conf 

then all I get is the DVB-S stuff:
> 
Luxe TV HD;BSkyB:12643:hC23M2O0S0:S28.2E:27500:2316:2317=eng;2318:0:0:54206:2:2603:0
BBC HD;BSkyB:10847:vC56M2O0S0:S28.2E:22000:5500:5502=NAR;5501:5503:0:6940:2:2050:0
Rush HD;BSkyB:12606:vC23M2O0S0:S28.2E:27500:2305:0;2306:0:0:55355:2:2614:0


These are the results that I got back with scan-s2 that w_scan doesn't seem to be picking up on:

> 
3DTV;BSkyB:12382:hC34M2O35S1:S28.2E:29500:513=27:641=NAR;661=eng:2306:960,961,963:1302:2:2035:0
Channel 4 HD;BSkyB:11797:hC34M2O35S1:S28.2E:29500:513=27:641=NAR;661=eng:0:960,961,963:3875:2:2005:0
Crime HD;BSkyB:12246:vC34M2O35S1:S28.2E:29500:515=27:0;663=eng:0:960,961,963:3888:2:2028:0
Discovery HD;BSkyB:12324:vC34M2O35S1:S28.2E:29500:514=27:0;662=eng:0:960,961,963:3803:2:2032:0
Disney Cine HD;BSkyB:12324:vC34M2O35S1:S28.2E:29500:515=27:643=NAR;663=eng:0:960,961,963:3873:2:2032:0
ESPN HD;BSkyB:12343:hC34M2O35S1:S28.2E:29500:514=27:0;662=eng:0:960,961,963:3840:2:2033:0
ESPN HD;BSkyB:12343:hC34M2O35S1:S28.2E:29500:514=27:0;662=eng:0:960,961,963:3841:2:2033:0
Eurosport HD;BSkyB:11856:vC34M2O35S1:S28.2E:29500:514=27:0;662=eng:0:960,961,963:3804:2:2008:0
FX HD;BSkyB:11856:vC34M2O35S1:S28.2E:29500:513=27:0;661=eng:0:960,961,963:3823:2:2008:0
History HD;BSkyB:12246:vC34M2O35S1:S28.2E:29500:513=27:641=NAR;661=eng:0:960,961,963:3886:2:2028:0
MTVN HD;BSkyB:11719:hC34M2O35S1:S28.2E:29500:514=27:0;662=eng:0:960,961,963:3806:2:2001:0
Nat Geo HD;BSkyB:12343:hC34M2O35S1:S28.2E:29500:513=27:641=NAR;661=eng:0:960,961,963:3831:2:2033:0
NatGeoWild HD;BSkyB:12246:vC34M2O35S1:S28.2E:29500:514=27:0;662=eng:0:960,961,963:3885:2:2028:0
SBO HD1;BSkyB:12363:vC34M2O35S1:S28.2E:29500:514=27:642=NAR;662=eng:2305:960,961,963:3879:2:2034:0
SBO HD2;BSkyB:12363:vC34M2O35S1:S28.2E:29500:512=27:640=NAR;660=eng:2317:960,961,963:3811:2:2034:0
SCI FI HD;BSkyB:12324:vC34M2O35S1:S28.2E:29500:512=27:0;660=eng:0:960,961,963:3874:2:2032:0
Sky1 HD;BSkyB:12343:hC34M2O35S1:S28.2E:29500:512=27:640=NAR;660=eng:2305:960,961,963:3861:2:2033:0
Sky Action HD;BSkyB:12246:vC34M2O35S1:S28.2E:29500:512=27:640=NAR;660=eng:2311:960,961,963:3814:2:2028:0
Sky Arts 1 HD;BSkyB:12324:vC34M2O35S1:S28.2E:29500:513=27:0;661=eng:0:960,961,963:3863:2:2032:0
Sky Arts 2 HD;BSkyB:11856:vC34M2O35S1:S28.2E:29500:512=27:0;660=eng:0:960,961,963:3864:2:2008:0
Sky Comedy HD;BSkyB:12168:vC34M2O35S1:S28.2E:29500:513=27:641=NAR;661=eng:2314:960,961,963:3819:2:2024:0
Sky Drama HD;BSkyB:12168:vC34M2O35S1:S28.2E:29500:514=27:642=NAR;662=eng:2312:960,961,963:3816:2:2024:0
Sky Family HD;BSkyB:12012:vC34M2O35S1:S28.2E:29500:513=27:641=NAR;661=eng:2312:960,961,963:3818:2:2016:0
Sky MdnGrtsHD;BSkyB:12168:vC34M2O35S1:S28.2E:29500:515=27:643=NAR;663=eng:2311:960,961,963:3815:2:2024:0
SkyPremiereHD;BSkyB:12012:vC34M2O35S1:S28.2E:29500:512=27:640=NAR;660=eng:2313:960,961,963:3821:2:2016:0
SkyRealLiveHD;BSkyB:11797:hC34M2O35S1:S28.2E:29500:512=27:640=NAR;660=eng:2316:960,961,963:3813:2:2005:0
Sky ScFi/HorHD;BSkyB:12168:vC34M2O35S1:S28.2E:29500:512=27:640=NAR;660=eng:2313:960,961,963:3817:2:2024:0
Sky Screen 1HD;BSkyB:11719:hC34M2O35S1:S28.2E:29500:513=27:641=NAR;661=eng:2305:960,961,963:3833:2:2001:0
Sky Screen 2HD;BSkyB:12012:vC34M2O35S1:S28.2E:29500:515=27:643=NAR;663=eng:2314:960,961,963:3862:2:2016:0
Sky Sports HD1;BSkyB:11797:hC34M2O35S1:S28.2E:29500:514=27:642=NAR;662=eng:2305:960,961,963:3802:2:2005:0
Sky Sports HD1;BSkyB:11797:hC34M2O35S1:S28.2E:29500:514=27:642=NAR;662=eng:2305:960,961,963:3877:2:2005:0
Sky Sports HD2;BSkyB:11719:hC34M2O35S1:S28.2E:29500:512=27:640=NAR;660=eng:2312:960,961,963:3878:2:2001:0
Sky Sports HD2;BSkyB:11719:hC34M2O35S1:S28.2E:29500:512=27:640=NAR;660=eng:2312:960,961,963:3881:2:2001:0
Sky Sports HD3;BSkyB:12363:vC34M2O35S1:S28.2E:29500:513=27:641=NAR;661=eng:2308:960,961,963:3822:2:2034:0
Sky Sports HD3;BSkyB:12363:vC34M2O35S1:S28.2E:29500:513=27:641=NAR;661=eng:2308:960,961,963:3824:2:2034:0


These are the errors that w_scan gave when trying to scan S2:

> 
tune to: S2 f = 12324 kHz V SR = 29500  3/4 0,35  QPSK
(time: 09:09) ----------no signal----------
tune to: S2 f = 12324 kHz V SR = 29500  3/4 0,35  QPSK  (no signal)
(time: 09:11) ----------no signal----------
tune to: S2 f = 11797 kHz H SR = 29500  3/4 0,35  QPSK
(time: 09:14) ----------no signal----------
tune to: S2 f = 11797 kHz H SR = 29500  3/4 0,35  QPSK  (no signal)
(time: 09:17) ----------no signal----------
tune to: S2 f = 12343 kHz H SR = 29500  3/4 0,35  QPSK
(time: 09:20) ----------no signal----------
tune to: S2 f = 12343 kHz H SR = 29500  3/4 0,35  QPSK  (no signal)
(time: 09:23) ----------no signal----------
tune to: S2 f = 11719 kHz H SR = 29500  3/4 0,35  QPSK
(time: 09:26) ----------no signal----------
tune to: S2 f = 11719 kHz H SR = 29500  3/4 0,35  QPSK  (no signal)
(time: 09:29) ----------no signal----------
tune to: S2 f = 12363 kHz V SR = 29500  3/4 0,35  QPSK
(time: 09:31) ----------no signal----------
tune to: S2 f = 12363 kHz V SR = 29500  3/4 0,35  QPSK  (no signal)
(time: 09:34) ----------no signal----------
tune to: S2 f = 12012 kHz V SR = 29500  3/4 0,35  QPSK
(time: 09:37) ----------no signal----------
tune to: S2 f = 12012 kHz V SR = 29500  3/4 0,35  QPSK  (no signal)
(time: 09:40) ----------no signal----------
tune to: S2 f = 12246 kHz V SR = 29500  3/4 0,35  QPSK
(time: 09:43) ----------no signal----------
tune to: S2 f = 12246 kHz V SR = 29500  3/4 0,35  QPSK  (no signal)
(time: 09:46) ----------no signal----------
tune to: S2 f = 12168 kHz V SR = 29500  3/4 0,35  QPSK
(time: 09:48) ----------no signal----------
tune to: S2 f = 12168 kHz V SR = 29500  3/4 0,35  QPSK  (no signal)
(time: 09:51) ----------no signal----------   


---

### Post by coolercooler on 2009-10-08
Thanks willb, was beginning to think it was my hardware at fault, have you tried itv2 hd?  I can only manage sound but no picture.

@Art2003 whats the rar password for new uploaded vdr?

---

### Post by art2003 on 2009-10-08
to the chaps on 28E (Astra2)

May be it simply takes too long to get lock with s2, try to add the switch "-t 3" may help to the w_scan (and use the new version that contains the new HD transponders on Astra2, if so.

My 28E signal is pretty weak so I only get a handfull of channels there and can't really test

---

### Post by Wilb on 2009-10-08
> **coolercooler said:**
> Thanks willb, was beginning to think it was my hardware at fault, have you tried itv2 hd?  I can only manage sound but no picture.

Not tried ITV HD but I believe it uses some custom details to obfuscate itself, I know it doesn't show up as ITV HD on my STB - it identifies itself as "10510". It broadcasts on the following:

 Frequency (GHz): 11.427
 Polarisation: H
 Symbol Rate (Mbaud): 27.5
 FEC: 2/3

You're not missing much on there anyway, most of the time it just broadcasts a holding screen!

---

### Post by Wilb on 2009-10-08
Out of interest, I have my system up and running pretty much as the tutorial states but I'm finding channel clearing to be much slower than the equivalent channels and packages on my DM500. Has anyone else found this? My VDR box is more than up to spec - Q6600 @ 3.0 Ghz with a Nvidia 8400 doing VDPAU, but there just seems to be a bit of a bottleneck somewhere. Internet and server connection is absolutely fine.

Might try to get Kaffeine up and running tonight with the SC plugin to see how that fares.

---

### Post by art2003 on 2009-10-09
By all means tell us how it goes with kaffeine!

I find that xine-lib r262 with a special patch is faster for clearing channels. I would upload the source if there is enough interest.

> **Wilb said:**
> Out of interest, I have my system up and running pretty much as the tutorial states but I'm finding channel clearing to be much slower than the equivalent channels and packages on my DM500. Has anyone else found this? My VDR box is more than up to spec - Q6600 @ 3.0 Ghz with a Nvidia 8400 doing VDPAU, but there just seems to be a bit of a bottleneck somewhere. Internet and server connection is absolutely fine.

Might try to get Kaffeine up and running tonight with the SC plugin to see how that fares.

---

### Post by Wilb on 2009-10-10
Yes I would be most grateful if you could upload the source. So far my tests with Kaffeine have been much more successful than VDR - things are clearing much quicker and I even have it driving my motor. Unfortunately though I don't want to use Kaffeine long term - VDR is much better.

---

### Post by hotzenplotz5 on 2009-10-10
(offtopic)
unsupported (dont speak good english)
but look here : vdr-1.7.9 + plugins (120) + xine-vdpau etc etc

[https://launchpad.net/~hotzenplotz5/+archive/ppa](https://launchpad.net/~hotzenplotz5/+archive/ppa)

> 
deb [http://ppa.launchpad.net/hotzenplotz5/ppa/ubuntu](http://ppa.launchpad.net/hotzenplotz5/ppa/ubuntu) karmic main 
deb-src [http://ppa.launchpad.net/hotzenplotz5/ppa/ubuntu](http://ppa.launchpad.net/hotzenplotz5/ppa/ubuntu) karmic main


---

### Post by speed32219 on 2009-10-10
kinda of a stupid question, but what will a DVB-S2 do for you?  Like, do you need a free to air receiver.  Couldn't you just take a capture card and feed the output of cable, Dish, Dtv into it?

I am going to start on this project, just wanted to know the type of hardware I should get a HD DVB-C/S/T card or just a plain capture HD card. Actually I do have a hd pctv (Cable) card from pinnacle, I almost forgot, I've had it for 8 months and have not used it yet.
Oh, yeah, because I have DTV that's why and realized I would only get composite and no HD. Waiting for my DTV contract to end, I do not like them (Actually it is there HW, it sux), prefer Dish or cable.

Also, how do you connect it so you get the HD stuff?  

Like I said, stupid questions.

---

### Post by m00anj00 on 2009-10-12
I dont know if you are aware but ffmpeg cvs and git tree now wont compile without the svn x264 libraries.  The issue then lies that ffmpeg wont work as the developers have changed something crucial.  When you compile ffmpeg git tree now, you get undefined symbol errors with libavcodec.

---

### Post by Wilb on 2009-10-12
I'm now also suspecting I'm seeing an issue with my card WinTV Nova HD) that others have reported - not being able to tune to certain channels due to a hi band switching problem. Unfortunately I've done so much build / rebuild / trash / build / rebuilding on my system in the last week or so that I'm now tempted to start with a clean fresh install (I'm still on 8.10 anyway) and see how things go from there.

---

### Post by art2003 on 2009-10-14
Check the 1st page for updated cccam instructions, basically there is an updated wrapper (which you get from the sc plugin contributions) that speeds up initial channel tunning

> **Wilb said:**
> Out of interest, I have my system up and running pretty much as the tutorial states but I'm finding channel clearing to be much slower than the equivalent channels and packages on my DM500. Has anyone else found this? My VDR box is more than up to spec - Q6600 @ 3.0 Ghz with a Nvidia 8400 doing VDPAU, but there just seems to be a bit of a bottleneck somewhere. Internet and server connection is absolutely fine.

Might try to get Kaffeine up and running tonight with the SC plugin to see how that fares.

---

### Post by art2003 on 2009-10-14
I got passed those errors last night(undefined symbol errors with libavcodec) (with fresh cvs downloads)
Had to uninstall 3 packages that were conflicting with ffmpeg with the --enable-shared option

BTW I will personally stick with Ubuntu 8.10 until Ubuntu 10.04 LTS comes out in April.

> **m00anj00 said:**
> I dont know if you are aware but ffmpeg cvs and git tree now wont compile without the svn x264 libraries.  The issue then lies that ffmpeg wont work as the developers have changed something crucial.  When you compile ffmpeg git tree now, you get undefined symbol errors with libavcodec.

---

### Post by art2003 on 2009-10-14
With a DVB-S2 card you need no external receivers, just connect it to your LNB and hardware-wise you are all up and running (after following this tutorial carefully)

> **speed32219 said:**
> kinda of a stupid question, but what will a DVB-S2 do for you?  Like, do you need a free to air receiver.  Couldn't you just take a capture card and feed the output of cable, Dish, Dtv into it?

I am going to start on this project, just wanted to know the type of hardware I should get a HD DVB-C/S/T card or just a plain capture HD card. Actually I do have a hd pctv (Cable) card from pinnacle, I almost forgot, I've had it for 8 months and have not used it yet.
Oh, yeah, because I have DTV that's why and realized I would only get composite and no HD. Waiting for my DTV contract to end, I do not like them (Actually it is there HW, it sux), prefer Dish or cable.

Also, how do you connect it so you get the HD stuff?  

Like I said, stupid questions.

---

### Post by Wilb on 2009-10-14
> **art2003 said:**
> Check the 1st page for updated cccam instructions, basically there is an updated wrapper (which you get from the sc plugin contributions) that speeds up initial channel tunning

I only discovered that updated preload last night,  used it and noticed an immediate improvement. Since then I've screwed something else up though! I'm getting there though, going to spend some more time on it later.

---

### Post by art2003 on 2009-10-14
Frequent backups are a very good idea.
I recommend to use a clonezilla live cd

[http://sourceforge.net/projects/clonezilla/files/clonezilla_live_stable/clonezilla-live-1.2.2-31.iso/download](http://sourceforge.net/projects/clonezilla/files/clonezilla_live_stable/clonezilla-live-1.2.2-31.iso/download)

It will backup your whole hardrive or just a partition.

> **Wilb said:**
> I only discovered that updated preload last night,  used it and noticed an immediate improvement. Since then I've screwed something else up though! I'm getting there though, going to spend some more time on it later.

---

### Post by Wilb on 2009-10-14
Unfortunately I'm a sysadmin by trade so know that all too well - sometimes I just like to hammer at a problem until I solve it though so don't back up as often as I should. Anyhoo, I'm back to where I was last night and I can confirm that things clear much quicker with the new preload, my main problem now is that the channel lists that I've generated with the scan don't actually seem to be 100% correct. Corrected the settings for some channels manually and now they are working too - this could be a bit tedious though to know what is correct and what isn't so I need to work on that a bit more. 

Does anyone fancy sharing their channels.conf files for comparison and testing? I downloaded some files from [http://www.linowsat.co.uk/](http://www.linowsat.co.uk/) to test but unfortunately they didn't seem much use at all - I think probably because they are in VDR 1.3x format so no DVB-S2 stuff is configured properly.

---

### Post by steefjeqv on 2009-10-15
> **Wilb said:**
> Unfortunately I'm a sysadmin by trade so know that all too well - sometimes I just like to hammer at a problem until I solve it though so don't back up as often as I should. Anyhoo, I'm back to where I was last night and I can confirm that things clear much quicker with the new preload, my main problem now is that the channel lists that I've generated with the scan don't actually seem to be 100% correct. Corrected the settings for some channels manually and now they are working too - this could be a bit tedious though to know what is correct and what isn't so I need to work on that a bit more. 

Does anyone fancy sharing their channels.conf files for comparison and testing? I downloaded some files from [http://www.linowsat.co.uk/](http://www.linowsat.co.uk/) to test but unfortunately they didn't seem much use at all - I think probably because they are in VDR 1.3x format so no DVB-S2 stuff is configured properly.

The stable VDR version (1.6.0) only needs one channel in its channels.conf. After that it will "find" all other available channels.
I don't know wether this also applies for the 1.7.x dev versions.

---

### Post by art2003 on 2009-10-15
Here is my channels.conf, far from perfect/complete but a good starting point and of course I would welcome corrections/additions
(It would be really nice if we had a community maintained channel list since the automatically scanned lists one finds easily contains error and are rather impersonal.


[http://www.ziddu.com/download/6928415/channels.conf.rar.html](http://www.ziddu.com/download/6928415/channels.conf.rar.html)


> **Wilb said:**
> Unfortunately I'm a sysadmin by trade so know that all too well - sometimes I just like to hammer at a problem until I solve it though so don't back up as often as I should. Anyhoo, I'm back to where I was last night and I can confirm that things clear much quicker with the new preload, my main problem now is that the channel lists that I've generated with the scan don't actually seem to be 100% correct. Corrected the settings for some channels manually and now they are working too - this could be a bit tedious though to know what is correct and what isn't so I need to work on that a bit more. 

Does anyone fancy sharing their channels.conf files for comparison and testing? I downloaded some files from [http://www.linowsat.co.uk/](http://www.linowsat.co.uk/) to test but unfortunately they didn't seem much use at all - I think probably because they are in VDR 1.3x format so no DVB-S2 stuff is configured properly.

---

### Post by Wilb on 2009-10-15
Thanks for posting - shall have a play shortly. Just been looking at the new experimental cccam client that is built into the latest version of vdr-sc. From the example:

> 
# (the real) cccam client
# 'nodeid' is your node ID (16 characters). Optional, defaults to use random ID
# 'version/build' is the version and build string send to the server (each max.
#  31 characters). Optional, defaults to 2.0.11/2892
# If you want to specify version/build but you don't want to specify a node ID,
# put a * to the node ID field.
#
# NOTE: this is a real client. You don't need to have CCcam running on local
# machine.
cccam2:hostname:port:emm/caid/mask:username:password[:nodeid][:version/build]


Tested and it works - not done any long testing to see how it compares though.

---

### Post by art2003 on 2009-10-16
Wilb: Thanks for sharing your finding with us, it is encouraging to see people sharing back, let us know your impressions on the cccam2 built-in client

---

### Post by Wilb on 2009-10-20
Has anyone tried to get 4:2:2 feeds working under VDR / with VDR Xine or with any other DVB software under Linux?

---

### Post by Wilb on 2009-11-05
Just for reference I did a clean build of Karmic and had a nice setup running using hotzenplotz5's repos but had issues with the sc plugin giving me a black screen and not clearing anything even though the logs suggested everything should have been coming through fine. Ended up going back to Intrepid for now.

---

### Post by SeanCorky on 2009-11-06
Did you have any luck with 4:2:2 ?

---

### Post by grosMario on 2009-11-11
> **hotzenplotz5 said:**
> (offtopic)
unsupported (dont speak good english)
but look here : vdr-1.7.9 + plugins (120) + xine-vdpau etc etc

[https://launchpad.net/~hotzenplotz5/+archive/ppa]("https://launchpad.net/%7Ehotzenplotz5/+archive/ppa")

Hi, thanks for this priceless information !
These packages worked almost out of the box on my computer. Now I need to add one little plugin but how shall I compile it ??
I tried to copy a binary version of this plugin, wich was created on the same computer with a "stock" 1.7.9 vdr source tree but it makes vdr crash ..

Help needed please !
(my wife is going mad due to the time I spend fooling around with the computer)

Edit: I've pulled the src package for vdr, compiled the sc plugin within this source tree, manually installed all the libs in correct place. Now the SC plugin crashes in cam.c line 3147 in the call "new cScDvbDevice(i,DvbOpen(DEV_DVB_CA,i,O_RDWR));" .. Any suggestion ?

---

### Post by Wilb on 2009-11-11
> **SeanCorky said:**
> Did you have any luck with 4:2:2 ?

Not yet, but still have it on my radar - will post back when I get something sorted!

---

### Post by Wilb on 2009-11-11
> **grosMario said:**
> Hi, thanks for this priceless information !
These packages worked almost out of the box on my computer. Now I need to add one little plugin but how shall I compile it ??
I tried to copy a binary version of this plugin, wich was created on the same computer with a "stock" 1.7.9 vdr source tree but it makes vdr crash ..

Help needed please !
(my wife is going mad due to the time I spend fooling around with the computer)

Edit: I've pulled the src package for vdr, compiled the sc plugin within this source tree, manually installed all the libs in correct place. Now the SC plugin crashes in cam.c line 3147 in the call "new cScDvbDevice(i,DvbOpen(DEV_DVB_CA,i,O_RDWR));" .. Any suggestion ?

Did you make sure that the sc plugin was the one loaded first when starting VDR? If I remember correctly there is a config file that lets you define the priority of plugins so that yo ucan load sc first. However like I mentioned above, when I did this I still couldn't get it to clear any channels I was entitled to - everything logged suggested it should have worked but I was just presented with a black screen.

---

### Post by Wilb on 2009-11-11
PS - I seem to recall those packages log to syslog so don't forget to check in there - if you don't have sc first in your plugins list you will see a no "DVB device found" error or similar.

---

### Post by steefjeqv on 2009-11-11
Maybe this will help :

[https://launchpad.net/~mirak-mirak/+archive/ppa]("https://launchpad.net/~mirak-mirak/+archive/ppa")

Greetings,
Steven

---

### Post by Wilb on 2009-11-11
> **steefjeqv said:**
> Maybe this will help :

[https://launchpad.net/~mirak-mirak/+archive/ppa]("https://launchpad.net/~mirak-mirak/+archive/ppa")

Greetings,
Steven

When I was building I looked at that PPA and it only had opensc, also there were no karmic build for x86 at the time. Has anyone got that working with the debs above?

---

### Post by Sav on 2009-11-22
> **Wilb said:**
> When I was building I looked at that PPA and it only had opensc, also there were no karmic build for x86 at the time. Has anyone got that working with the debs above?

I was unable to use Mirak's vdr-sc-plugin under karmic 64 bit. It doesn't connect to the CCcam server, no matter how I set-up the cardclient.conf file.
From the vdr karmic team repository I downloaded only the lib-xine2 (binaries and sources) and the xine player. I had to compile my self vdr and the plugins.

---

### Post by tx8090 on 2009-12-22
Hi,

i bought a Atom 330 + Nvidia Ion system and i'd like to install a ubuntu system with vdr and cccam (cccam as client) running on it.

Is this tutorial uptodate, or are there any problems with ION Systems? 

I've got the Asrock Ion 330HT with a extern USB Technotrend S2-3600 DVB-S2 adapter. I'd like to run on this system a nice frontend with cccam as client running on it.

I'd like to use ubuntu, because if i use a Windows-Program, it is not soo fast if i am watching Full-HD Channels.

You would help me alot if you only can answer one question...

---

### Post by Wilb on 2010-01-15
Well just to update on my 4:2:2 quest, so far it's completely unsuccessful. Been playing With DVBlast which is from the VLC people, but I cannot for the life of me get it to pick up anything that is DVB-S2 so far. Even done a clean install of Karmic to try it on but still no avail.

Starting to consider a Windows install for 4:4:2 stuff but that is a ridiculous thought and one that I only want to go down as an absolute last resort.

---

### Post by steefjeqv on 2010-01-16
Hi,

I'm not an expert on 4:2:2, but I'm just wondering if you're using the VDR-Team repo or did you compile all the VDR stuff from scratch.

Are there 4:2:2 transmissions on Astra 28.2 ? I'd be happy to test wether they work on my VDR setup (ppa from the VDR-team).

Greetings,
Steven

---

### Post by Wilb on 2010-01-16
> **steefjeqv said:**
> Hi,

I'm not an expert on 4:2:2, but I'm just wondering if you're using the VDR-Team repo or did you compile all the VDR stuff from scratch.

Are there 4:2:2 transmissions on Astra 28.2 ? I'd be happy to test wether they work on my VDR setup (ppa from the VDR-team).

Greetings,
Steven

At the minute I'm not even using VDR, from what I gather 4:2:2 support isn't big in VDR - or at least its not very well documented. It would probably be able to receive it if you give it the right tuning data, but thats the problem I'm getting stuck on at the moment - finding something that will scan a transponder for feeds and pull out the tuning data. DVBlast should theoretically do the trick, but its not behaving well on stuff that I believe to be DVB-S2. I've got it to pick up some standard DVB-S 4:2:0 stuff but no more than that yet.

If you want to see some active feeds then look here:

[http://www.satelliweb.com/index.php?section=livef](http://www.satelliweb.com/index.php?section=livef)

Its unlikely you'll find anything on 28.2e though.

---

### Post by steefjeqv on 2010-01-16
Hi,

If you haven't tried it yet, then maybe vdr-plugin-reelchannelscan will be the plugin you're looking for.

I've just installed it on my VDR 1.7.10 and I'm scanning for DVB-T channels right now. DVB-S shoud work too but I'm not sure about DVB-S2 as my sat card only does DVB-S.

Greetings,
Steven

---

### Post by art2003 on 2010-01-17
Wilb: Look on my first post, there are links to download some files.
One of them contains a plugin that does DVB-S2 scanning from within vdr (it is in beta stage but works fine, for best results start with a blank channels.conf)

Others: I try to keep the tutorial reasonably uptodate but I have not tried yet with an ION motherboard although I plan to eventually purchase one, probably in spring when ubuntu 10.04 LTS is released.

---

### Post by mofd on 2010-01-17
Hi, i've installed the latest xbmc live cd, and after that followed your instructions.
Firmware and drivers seems to load ok:
 
```

[EMAIL="xbmc@XBMCLive:/dev/dvb/adapter0$"]xbmc@XBMCLive:/dev/dvb/adapter0$[/EMAIL] ls -als
total 0
0 drwxr-xr-x 2 root root     120 2010-01-17 04:45 .
0 drwxr-xr-x 3 root root      60 2010-01-17 04:45 ..
0 crw-rw---- 1 root video 212, 1 2010-01-17 04:45 demux0
0 crw-rw---- 1 root video 212, 2 2010-01-17 04:45 dvr0
0 crw-rw---- 1 root video 212, 0 2010-01-17 04:45 frontend0
0 crw-rw---- 1 root video 212, 3 2010-01-17 04:45 net0

```
 
```

[EMAIL="xbmc@XBMCLive:/dev/dvb/adapter0$"]xbmc@XBMCLive:/dev/dvb/adapter0$[/EMAIL] sudo dmesg | grep -i dvb
[    5.426678] cx88[0]: subsystem: 0070:6906, board: Hauppauge WinTV-HVR4000(Lite) DVB-S/S2 [card=69,autodetected], frontend(s): 1

```
 
but when i try to update my channels:
```

sudo w_scan -fs -s S19E2 -o7 >> /etc/vdr/channels.conf
w_scan version 20091230 (compiled for DVB API 5.0)
using settings for 19.2 east Astra 1F/1G/1H/1KR/1L
frontend_type DVB-S, channellist 6
output format vdr-1.7
Info: using DVB adapter auto detection.
main:2911: FATAL: ***** NO USEABLE DVB CARD FOUND. *****
Please check wether dvb driver is loaded and
verify that no dvb application (i.e. vdr) is running.

```
 
yes i did sudo /etc/init.d/vdr stop

any help would be appriciated!

---

### Post by mofd on 2010-01-17
lsof /dev/dvb/adapter0/frontend0
did the trick --> killed running pid 'tvheadend'
thnx

---

### Post by Wilb on 2010-01-17
> **art2003 said:**
> Wilb: Look on my first post, there are links to download some files.
One of them contains a plugin that does DVB-S2 scanning from within vdr (it is in beta stage but works fine, for best results start with a blank channels.conf)

Thanks, will give it a go - so far I've had a lot of trouble with scanning in Linux, a lot of the results generated have been problematic. Currently I'm using pre scanned files downloaded from vdr-settings.com but it would be nice if the plugin gave me a reliable way of scanning things myself.

As for 4:2:2, even if I do get VDR to scan and pick up the feed then I'm still going to be having problems displaying it - xine doesn't seem to support 4:2:2 properly and just crashes when it tries to play material. I've successfully scanned in 4:2:2 content in Kaffeine but playback fails and the app crashes with xinelib giving an "Invalid extension" error. Theoretically I should be able to use streamdev to send the output to VLC I suppose - we shall see.

I've temporarily set up my machine to dual boot so I've at least got a workaround for 4:2:2 stuff (its pretty straightforward with ProgDVB). Still having problems with DVBlast too - posted to the support lists for help on that so will report back if I make any progress.

---

### Post by Wilb on 2010-01-17
Do you just mean the Wirbelscan plugin?

---

### Post by Wilb on 2010-01-25
My 8.10 system was becoming increasingly annoying to maintain for various reasons, primarily due to me installing many mismatched packages along with source compiled stuff in a hurry but also the fact that packages were somewhat out of date. The final straw was realising that the xine-vdpau combo I was using had some bugs which were responsible for artefacts and glitches when watching HD content - I only realised this when switching to a software deinterlacer and playback was perfect (but slow occasionally, depending on what I was watching).

So anyway, I did a clean install of Karmic last night with the aim of keeping things as clean as possible, with using packages wherever I could. Surprisingly, this time round I've had a lot of success. I've primarily used packages from the VDR Karmic repository, built the sc plugin against it, packaged it and got things working. Not got everything anywhere near perfect yet, but the key bits are there so the rest can be configured to personal preferences.

I'm going to try and tidy up what I've done so I can post it up here tonight, but it might prove helpful to others. Virtually every plugin you will ever need is available from that PPA so it means a lot less compiling in the future.

---

### Post by art2003 on 2010-01-25
Yes, that´s right. It can scan DVB-S2 and the author is helpful if we point out a bug

On another note congratulations on your setup and of course it will be good to see your postings and it might help others...

> **Wilb said:**
> Do you just mean the Wirbelscan plugin?

---

### Post by Wilb on 2010-01-25
So, I've done something like this on a clean install of Karmic.

Add VDR PPAs:
```

sudo -s 
echo "deb http://ppa.launchpad.net/the-vdr-team/vdr-ubuntu-karmic/ubuntu karmic main" >> /etc/apt/sources.list
echo "deb-src http://ppa.launchpad.net/the-vdr-team/vdr-ubuntu-karmic/ubuntu karmic main" >> /etc/apt/sources.list
apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 4650EDF56CF20474
apt-get update

```

Install VDR and dependencies for the plugin:
```

apt-get install build-essential vdr vdr-dev dpatch libssl-dev fakeroot mercurial cdbs libbz2-dev dpkg-dev devscripts expect wget gettext dpatch libjpeg62-dev
apt-get build-dep vdr

```

Compile, package, install and enable the plugin:
```

# download the attachment to your preferred build location such as /usr/local/src
tar xjvf sc.tar.bz2 
dpkg-source -x vdr-plugin-sc_0.9~1hg.dsc
cd vdr-plugin-sc-0.9~1hg/
fakeroot ./debian/rules update
ln -s /usr/include/vdr/Make.config .
sed -i 's/CSAFLAGS   ?= -Wall -fPIC -g -O3 -mmmx -fomit-frame-pointer -fexpensive-optimizations -funroll-loops/CSAFLAGS   ?= -Wall -fPIC -g -O2 -mmmx -fomit-frame-pointer -fexpensive-optimizations -funroll-loops/' Makefile
dpkg-buildpackage -rfakeroot -sa
cd ..
dpkg -i vdr-plugin-sc_0.9~1hg_i386.deb
sed -i 's/firstplugin/firstplugin sc/' /etc/vdr/plugins/order.conf 
invoke-rc.d vdr restart

```

The plugin should now be ready to use in the same way that Art2003 has previously described.

---

### Post by Homer314 on 2010-02-04
> **Wilb said:**
> So, I've done something like this on a clean install of Karmic.

Add VDR PPAs:
```

sudo -s 
echo "deb http://ppa.launchpad.net/the-vdr-team/vdr-ubuntu-karmic/ubuntu karmic main" >> /etc/apt/sources.list
echo "deb-src http://ppa.launchpad.net/the-vdr-team/vdr-ubuntu-karmic/ubuntu karmic main" >> /etc/apt/sources.list
apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 4650EDF56CF20474
apt-get update

```

Install VDR and dependencies for the plugin:
```

apt-get install build-essential vdr vdr-dev dpatch libssl-dev fakeroot mercurial cdbs libbz2-dev dpkg-dev devscripts expect wget gettext dpatch libjpeg62-dev
apt-get build-dep vdr

```

Compile, package, install and enable the plugin:
```

# download the attachment to your preferred build location such as /usr/local/src
tar xjvf sc.tar.bz2 
dpkg-source -x vdr-plugin-sc_0.9~1hg.dsc
cd vdr-plugin-sc-0.9~1hg/
fakeroot ./debian/rules update
ln -s /usr/include/vdr/Make.config .
sed -i 's/CSAFLAGS   ?= -Wall -fPIC -g -O3 -mmmx -fomit-frame-pointer -fexpensive-optimizations -funroll-loops/CSAFLAGS   ?= -Wall -fPIC -g -O2 -mmmx -fomit-frame-pointer -fexpensive-optimizations -funroll-loops/' Makefile
dpkg-buildpackage -rfakeroot -sa
cd ..
dpkg -i vdr-plugin-sc_0.9~1hg_i386.deb
sed -i 's/firstplugin/firstplugin sc/' /etc/vdr/plugins/order.conf 
invoke-rc.d vdr restart

```

The plugin should now be ready to use in the same way that Art2003 has previously described.

Following these steps i obtain this error running vdr:

[general.error] init of cardclient 'cccam2' failed

My cardclient.conf looks like this

cccam2:[ip]:12000:0:/0000/0000:[user]:[pw]

with 

cccam2:[ip]:12000:0:[user]:[pw]

instated i've no errors, but no cccam (another machine in the lan working fine) server connection


Any ideas ? Thanks !

---

### Post by Wilb on 2010-02-04
From memory it looks OK - I assume you don't actually have the square brackets in the config file do you?

---

### Post by Homer314 on 2010-02-04
> **Wilb said:**
> From memory it looks OK - I assume you don't actually have the square brackets in the config file do you?

Thank's for reply, can you explain this with an example, i don't understand the example file provided with sc :( 

cccam2:hostname:port:emm/caid/mask:username:password[:param=value[,param=value]]

?

Thank's

---

### Post by Wilb on 2010-02-04
```

cccam2:127.0.0.1:12000:1:/0000/0000:username:password

```

Replacing:

 127.0.0.1 with the IP or hostname of the server you want to connect to
 12000 with the port the server you want to connect to runs on
 username with your username
 password with your password

Don't use any square brackets - they're not needed.

---

### Post by Homer314 on 2010-02-04
> **Wilb said:**
> ```

cccam2:127.0.0.1:12000:1:/0000/0000:username:password

```

Replacing:

 127.0.0.1 with the IP or hostname of the server you want to connect to
 12000 with the port the server you want to connect to runs on
 username with your username
 password with your password

Don't use any square brackets - they're not needed.

My cardclient.conf looks like you suggest but...

```


Feb  4 21:26:09 VDR-BOX vdr: [13143] [general.info] SC version 1.0.0pre-Unknown starting (VDR 1.7.10)
Feb  4 21:26:09 VDR-BOX vdr: [13143] [general.info] loading cardclient config from /var/lib/vdr/plugins/sc/cardclient.conf
Feb  4 21:26:09 VDR-BOX vdr: [13143] [general.error] init of cardclient 'cccam2' failed
Feb  4 21:26:09 VDR-BOX vdr: [13143] [general.error] file /var/lib/vdr/plugins/sc/cardclient.conf has error in line #1
Feb  4 21:26:09 VDR-BOX vdr: [13143] [general.error] failed open /var/lib/vdr/plugins/sc/SoftCam.Key: Nessun file o directory
Feb  4 21:26:09 VDR-BOX vdr: [13143] [general.error] failed open /var/lib/vdr/plugins/sc/smartcard.conf: Nessun file o directory
Feb  4 21:26:09 VDR-BOX vdr: [13143] [general.error] failed open /var/lib/vdr/plugins/sc/cardslot.conf: Nessun file o directory
Feb  4 21:26:09 VDR-BOX vdr: [13143] [general.error] failed open /var/lib/vdr/plugins/sc/override.conf: Nessun file o directory
Feb  4 21:26:09 VDR-BOX vdr: [13143] [general.error] no keys loaded for softcam!
Feb  4 21:26:09 VDR-BOX vdr: [13150] CI adapter on device 0 thread started (pid=13143, tid=13150)
Feb  4 21:26:09 VDR-BOX vdr: [13152] SC housekeeper thread started (pid=13143, tid=13152)

```

---

### Post by Homer314 on 2010-02-04
Removing mask...

```

Feb  4 21:36:42 VDR-BOX vdr: [13244] starting plugin: sc
Feb  4 21:36:42 VDR-BOX vdr: [13244] [general.info] SC version 1.0.0pre-Unknown starting (VDR 1.7.10)
Feb  4 21:36:42 VDR-BOX vdr: [13244] [general.info] loading cardclient config from /var/lib/vdr/plugins/sc/cardclient.conf
Feb  4 21:36:42 VDR-BOX vdr: [13250] Netwatcher thread started (pid=13244, tid=13250)
Feb  4 21:36:42 VDR-BOX vdr: [13244] [general.error] socket: EOF on read
Feb  4 21:36:42 VDR-BOX vdr: [13244] [general.error] failed open /var/lib/vdr/plugins/sc/SoftCam.Key: Nessun file o directory
Feb  4 21:36:42 VDR-BOX vdr: [13244] [general.error] failed open /var/lib/vdr/plugins/sc/smartcard.conf: Nessun file o directory
Feb  4 21:36:42 VDR-BOX vdr: [13244] [general.error] failed open /var/lib/vdr/plugins/sc/cardslot.conf: Nessun file o directory
Feb  4 21:36:42 VDR-BOX vdr: [13244] [general.error] failed open /var/lib/vdr/plugins/sc/override.conf: Nessun file o directory
Feb  4 21:36:42 VDR-BOX vdr: [13244] [general.error] no keys loaded for softcam!
Feb  4 21:36:42 VDR-BOX vdr: [13251] CI adapter on device 0 thread started (pid=13244, tid=13251)
Feb  4 21:36:42 VDR-BOX vdr: [13252] SC-CI adapter on device 0 thread started (pid=13244, tid=13252)
Feb  4 21:36:42 VDR-BOX vdr: [13253] SC housekeeper thread started (pid=13244, tid=13253)
Feb  4 21:36:42 VDR-BOX vdr: [13244] starting plugin: xineliboutput
Feb  4 21:36:42 VDR-BOX vdr: [13254] Remote decoder/display server (cXinelibServer) thread started (pid=13244, tid=13254)
Feb  4 21:36:42 VDR-BOX vdr: [13254] [xine..put] cXinelibServer priority set successful SCHED_RR 2 [1,99]
Feb  4 21:36:42 VDR-BOX vdr: [13254] [xine..put] Binding server to 127.0.0.1:37890
Feb  4 21:36:42 VDR-BOX vdr: [13254] [xine..put] Listening on port 37890
Feb  4 21:36:42 VDR-BOX vdr: [13254] [xine..put] Listening for UDP broadcasts on port 37890
Feb  4 21:36:42 VDR-BOX vdr: [13254] [discovery] BROADCAST: VDR xineliboutput DISCOVERY 1.0#015#012Server port: 37890#015#012Server address: 127.0.0.1#015#012Server version: xineliboutput-1.0.90-cvs#015#012#015
Feb  4 21:36:42 VDR-BOX vdr: [13244] [xine..put] cXinelibDevice::StartDevice(): Device started
Feb  4 21:36:42 VDR-BOX vdr: [13244] ERROR: /dev/lircd: Nessun file o directory
Feb  4 21:36:42 VDR-BOX vdr: [13244] ERROR: remote control LIRC not ready!


```

---

### Post by Homer314 on 2010-02-04
also with mirak ppa opensc no connection to server on a clean amd64 karmic installation

---

### Post by Wilb on 2010-02-04
Sorry, just realised there was an extra : in there that shouldn't have been. Try again:

```

cccam2:127.0.0.1:12000:1/0000/0000:username:password

```

---

### Post by Homer314 on 2010-02-05
Removing ":" now i see the connection to the server, but black screen and....

```

Feb  5 12:43:54 VDR-BOX vdr: [6988] ERROR: /var/lib/vdr/plugins/sc/ecm.cache.$$$: Access denied
Feb  5 12:44:00 VDR-BOX vdr: [6988] ERROR: /var/lib/vdr/plugins/sc/ecm.cache.$$$: Access denied


```


ecm.cache.$$$ don't exists 

Any idea? Thank's !

---

### Post by Wilb on 2010-02-05
That just looks like a permissions thing. I'm not sure what user things are running under so just do:

```

 sudo chmod ugo+rwX -R /var/lib/vdr/plugins/sc/

```

---

### Post by Homer314 on 2010-02-05
giving new permissions...

```

Feb  5 14:34:12 VDR-BOX vdr: [7701] [general.error] CA_SET_DESCR failed (Argomento non valido). Expect a black screen.
Feb  5 14:34:22 VDR-BOX vdr: [7701] [general.error] CA_SET_DESCR failed (Argomento non valido). Expect a black screen.
Feb  5 14:34:32 VDR-BOX vdr: [7701] [general.error] CA_SET_DESCR failed (Argomento non valido). Expect a black screen.
Feb  5 14:34:42 VDR-BOX vdr: [7701] [general.error] CA_SET_DESCR failed (Argomento non valido). Expect a black screen.
Feb  5 14:34:52 VDR-BOX vdr: [7701] [general.error] CA_SET_DESCR failed (Argomento non valido). Expect a black screen.
Feb  5 14:35:02 VDR-BOX vdr: [7701] [general.error] CA_SET_DESCR failed (Argomento non valido). Expect a black screen.
Feb  5 14:35:12 VDR-BOX vdr: [7701] [general.error] CA_SET_DESCR failed (Argomento non valido). Expect a black screen.
Feb  5 14:35:22 VDR-BOX vdr: [7701] [general.error] CA_SET_DESCR failed (Argomento non valido). Expect a black screen.
Feb  5 14:35:32 VDR-BOX vdr: [7701] [general.error] CA_SET_DESCR failed (Argomento non valido). Expect a black screen.


```

---

### Post by Homer314 on 2010-02-05
Googoling i found the solution:

delete the ca0 file in /dev/dvb/adapterN 

:)

Really thank's !

---

### Post by Wilb on 2010-02-05
Excellent, glad you're all sorted :-)

---

### Post by scubidoo on 2010-02-06
try this


vdr -P´sc -B 0´


thats the right solutions for that problem

---

### Post by johnnytoxic on 2010-02-09
Nvidia GT210, GT210 and GT240 cards working with HDMI Audio.

Found this great guide that worked for me.

[http://xbmc.org/wiki/?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210%2C_GT220%2C_or_GT240](http://xbmc.org/wiki/?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210%2C_GT220%2C_or_GT240)

from the thread.

[http://xbmc.org/forum/showthread.php?t=69601](http://xbmc.org/forum/showthread.php?t=69601)


Great VDR guide. thank you very much.

---

### Post by coolercooler on 2010-02-09
Does anyone know how to make vdr work with XvBa?  Thats amd's version of vdpau equivalent or there about.

---

### Post by eiki2 on 2010-02-10
@wilb. I used your guide to install sc and it worked like a charm, but this plugin causes vdr and xine to use much cpu. On free to air channels both vdr and xine use very little cpu. on encrypted hd channels both vdr and xine use very much cpu. Is there a way to install the latest sc maybe that will work out better?

---

### Post by Wilb on 2010-02-10
> **coolercooler said:**
> Does anyone know how to make vdr work with XvBa?  Thats amd's version of vdpau equivalent or there about.

I don't think you will need to do anything different to VDR - its just whether the relevant patches exist for Xine with XvBA that will be the problem.

---

### Post by Wilb on 2010-02-10
> **eiki2 said:**
> @wilb. I used your guide to install sc and it worked like a charm, but this plugin causes vdr and xine to use much cpu. On free to air channels both vdr and xine use very little cpu. on encrypted hd channels both vdr and xine use very much cpu. Is there a way to install the latest sc maybe that will work out better?

Are you using VDPAU for the playback of your HD channels? Otherwise it will be very CPU intensive. Similarly if you're using any software deinterlacers it will be causing Xine to use quite a bit of CPU time.

As for the softcam, it will use up some CPU time unfortunately - its using software emulation to decrypt data that would otherwise be carried out by a dedicated hardware cam. As there is more data to decrypt on a HD channel then it is expected that it will need more CPU time to decrypt that data.

---

### Post by eiki2 on 2010-02-10
I use vdpau. When I playback 1080p mkv in xine-ui cpu is just about 2%. So I guess vdpau works, but I do not know if I have to enable vdpau in vdr somehow?

I start xine with the following command:
xine -f -D -V vdpau --post vdr --post vdr_video --post vdr_audio --aspect-ratio=anamorphic --verbose=2 --no-logo --no-splash "vdr:/tmp/vdr-xine/stream#demux:mpeg_pes" -A alsa

On Free to air SD channels vdr use about 2% cpu and xine 7%
SD encrypted: vdr 20% and xine 20%
HD encrypted: vdr 40% and xine 20%

I tried without -D option, but it is about the same.

What do we make of that? I would like to test free to air hd channels, but there are not any on the satelites I get.

---

### Post by batman76 on 2010-02-13
[COLOR=black][SIZE=3][FONT=Times New Roman]Hi,[/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3] [/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]I have build a htpc with ubuntu 9.10 and VDR ppa packages from vdr team. I have picture on bbc news ( open channel ) when I use vdr-plugin-xine, so I am wonder which vdr-sc plugin as the most steady against cccam and how can I install sc-plugin when vdr are install against ppa packages. (apt-get install)[/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3] [/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]Can some one help å linux newbe here?[/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3] [/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3]Sorry fore my bade English [/SIZE][/FONT][/COLOR]

---

### Post by Wilb on 2010-02-14
You just need to follow my instructions from the previous couple of pages and use vdr-sc's built in client.

---

### Post by coolercooler on 2010-02-17
The new patch failed.

```
Hunk #1 FAILED at 1028.
1 out of 1 hunk FAILED -- saving rejects to file po/et_EE.po.rej
patching file po/fi_FI.po
Hunk #1 succeeded at 42 with fuzz 2.
patching file po/fr_FR.po
Hunk #2 FAILED at 1035.
1 out of 2 hunks FAILED -- saving rejects to file po/fr_FR.po.rej
patching file po/it_IT.po
Hunk #4 succeeded at 629 with fuzz 2.
patching file po/nl_NL.po
patching file po/ru_RU.po
Hunk #1 FAILED at 1029.
1 out of 1 hunk FAILED -- saving rejects to file po/ru_RU.po.rej
patching file README.cmdsubmenu


```

and when compailing 

```
msgmerge -U --no-wrap --no-location --backup=none -q po/hu_HU.po po/vdr.pot
msgfmt -c -o po/hu_HU.mo po/hu_HU.po
cp po/hu_HU.mo locale/hu_HU/LC_MESSAGES/vdr.mo
msgmerge -U --no-wrap --no-location --backup=none -q po/it_IT.po po/vdr.pot
po/it_IT.po:101:29: invalid multibyte sequence
po/it_IT.po:218:15: invalid multibyte sequence
po/it_IT.po:245:15: invalid multibyte sequence
po/it_IT.po:272:18: invalid multibyte sequence
po/it_IT.po:297:39: invalid multibyte sequence
po/it_IT.po:753:27: invalid multibyte sequence
po/it_IT.po:953:16: invalid multibyte sequence
po/it_IT.po:1052:16: invalid multibyte sequence
po/it_IT.po:1156:16: invalid multibyte sequence
po/it_IT.po:1280:23: invalid multibyte sequence
po/it_IT.po:1458:11: invalid multibyte sequence
po/it_IT.po:1500:47: invalid multibyte sequence
msgmerge: found 12 fatal errors
make: *** [po/it_IT.po] Error 1
 
```

---

### Post by Wilb on 2010-02-17
Which patch is that? Where did you install VDR from, standard Ubuntu repo or the VDR-Team PPA?

---

### Post by coolercooler on 2010-02-18
> **Wilb said:**
> Which patch is that? Where did you install VDR from, standard Ubuntu repo or the VDR-Team PPA?

Hi, that's the patch described in the first page of this tut section, it's with the vdr 1.7.10 with it's respective patch, using 8.10.

---

### Post by Wilb on 2010-02-19
> **coolercooler said:**
> Hi, that's the patch described in the first page of this tut section, it's with the vdr 1.7.10 with it's respective patch, using 8.10.

My personal recommendation now would probably be to build a 9.10 system using the vdr ppa repo, you get all the vdpau stuff as well as the latest vdr. If you need the sc plugin then its easy to build that against it. Alternatively you could give YAVDR a try - a custom VDR distro that looks pretty nice albeit in its early stages.

See my post here:

[http://ubuntuforums.org/showpost.php?p=8724259&postcount=226](http://ubuntuforums.org/showpost.php?p=8724259&postcount=226)

---

### Post by coolercooler on 2010-02-20
Only problem with that is am using ATI based card and that freezes the keyboard and or starts in low graphical mode.

I tried it with the latest 9.10 and updated current modules.

I think perhaps we need a check list of errors and how to fix them, a reference for all possible errors.

---

### Post by Wilb on 2010-02-20
ATI drivers under Linux are a pain. However you should still be able to get things up and running even if its without hardware acceleration. It might be worth trying the open source drivers as an alternative?

---

### Post by johnnytoxic on 2010-02-22
I've spent weeks trying to get my box running stable.

I have tried everything, I keep getting jerky images and in the Xine log : 

**video_out: throwing away image with pts 362162 because it's too old**

I have tried vdr versions 1.7.8 / 9 / 10 / 11 and 12
I've used video buffers from 500 to 3000
Enabled / Disabled V syncs on Open GL
Many different xorg.conf configurations


The most i've had is around 1 minute wiithout any video jerking. The SC plugin is working fine. I just don't know what else to try.

I've got a Geforce GT240 with the latest beta nvidia drivers. 

When it is running properly for that small minute, it's great and runs like a standalone box. Any suggestions?

---

### Post by Wilb on 2010-02-22
Yep, sounds like you're having the same pain I had. Thought it was many other issues and eventually tracked it down to some sort of bug in Xine that not that many people seem to be having. Do

Do you use the Xine plugin or the Xinelibout one? I ended up switching to Xinelibout, using VDR-SXFE as my frontend and rolling my own latest libxine2 deb. I'm not at home right now so can't post it up, but will do later if you aren't able to roll your own. After months of fiddling I've only just this weekend started to get things how I really want them, quite satisfying now I'm getting there though.

---

### Post by johnnytoxic on 2010-02-22
> **Wilb said:**
> Yep, sounds like you're having the same pain I had. Thought it was many other issues and eventually tracked it down to some sort of bug in Xine that not that many people seem to be having. Do

Do you use the Xine plugin or the Xinelibout one? I ended up switching to Xinelibout, using VDR-SXFE as my frontend and rolling my own latest libxine2 deb. I'm not at home right now so can't post it up, but will do later if you aren't able to roll your own. After months of fiddling I've only just this weekend started to get things how I really want them, quite satisfying now I'm getting there though.

xine 0.9.3 plugin for vdr.

Do you mean xine-lib-vdpau ? Thats what I've been using.

I have a gigabyte g41-es2h motherboard. If you could post what you have installed I would be very grateful.

---

### Post by Wilb on 2010-02-22
I use vdr-plugin-xineliboutput rather than vdr-plugin-xine (although both seem to happily install alongside each other), along with that install libxineliboutput-sxfe and xineliboutput-sxfe and then you will have a program called vdr-sxfe which will work as a frontend to vdr. All of my packages are installed from tha vdr-team repositoriy.

Installing that will install libxine2 which vdr-sxfe uses for playback, replace it with my version and start up vdr-sxfe and *hopefully* you will suddenly be glitch free.

The command I use to invoke vdr-sxfe is:
```

vdr-sxfe --fullscreen --video vdpau --post tvtime:method=use_vo_driver
```

The xine parameters can be configured in the following config file:
```

~/.xine/config_xineliboutput

```

You can also configure various parameters in the plugin menu.

File was too big to attach so I've uploaded it here:

[http://www.megaupload.com/?d=TXXG6XC0]("http://www.megaupload.com/?d=TXXG6XC0")

If that works then you will want to hold the package:
```

sudo -s
echo libxine2 hold | dpkg --set-selections

```

I also have a libxine-dev package that was built as part of this but you shouldn't need that, shout up if you do.

Just so that you can see all of the xine related packages I have installed, here is a filtered output from dpkg:
```

hi  libxine-dev                           1.2.0~hg-0                                  the xine video player library, development p
ii  libxine1-xvdr                         1.0.4+cvs20091013.1200-7tvt1                Xine input plugin for vdr-plugin-xineliboutp
hi  libxine2                              1.2.0~hg-0                                  the xine video/media player library, binary 
ii  libxineliboutput-sxfe                 1.0.4+cvs20091013.1200-7tvt1                Local X-Server frontend for the xineliboutpu
ii  vdr-plugin-xineliboutput              1.0.4+cvs20091013.1200-7tvt1                VDR plugin for Xine based sofdevice frontend
ii  xineliboutput-sxfe
```

PS - make sure you have Desktop Effects turned off as I found that broke VSync.

---

### Post by johnnytoxic on 2010-02-23
Thanks Wilb.

When trying to install it says xineliboutput only works upto vdr 1.7.0.

I think I'm all mixed up now :). Am I best starting from scratch and use a 1.7.0 guide.

---

### Post by steefjeqv on 2010-02-23
@ johnnytoxic

As Wilb mentioned, use the repo created by the VDR-team :

[https://launchpad.net/~the-vdr-team/+archive/vdr-ubuntu-karmic]("https://launchpad.net/~the-vdr-team/+archive/vdr-ubuntu-karmic")

Or their Ubuntu based distro :

[http://www.yavdr.org/]("http://www.yavdr.org/")

Greetings,
Steven

---

### Post by Wilb on 2010-02-23
Yep, exactly that - just make sure you have the following in /etc/apt/sources.list
```

deb http://ppa.launchpad.net/the-vdr-team/vdr-ubuntu-karmic/ubuntu karmic main 
deb-src http://ppa.launchpad.net/the-vdr-team/vdr-ubuntu-karmic/ubuntu karmic main 

```


If your system is really confused then maybe starting afresh is what you need, but you should be able to reverse the things you've done easily enough.

I know I've said it already, but my latest rebuild was so straightforward as the majority of it was just apt-getable so if you're still struggling and you don't have anything to lose then just start afresh with 9.10 32bit and use the packages and instructions I've provided over the last few of pages.

---

### Post by Wilb on 2010-02-24
Any further progress mate?

---

### Post by johnnytoxic on 2010-02-26
> **Wilb said:**
> Any further progress mate?

I reinstalled 9.10, installed the nvidia drivers, the Team VDR packages:

Just not getting any output. I'm not sure how to put it all together. I tried to use the vdr-sxfe command and I get no signal.

Am I missing any steps. If you could post a quick bulletpoint list of what to install would be great.

This is what I've done so far.

9.10
Installed firmware for the HVR4000 DVB card
195 Nvidia Drivers
Added the Team VDR sources

Installed:

libxine-dev  
libxine1-xvdr                         
vdr-plugin-xineliboutp
libxine2 
libxineliboutput-sxfe                 
xineliboutput
vdr-plugin-xineliboutput              
xineliboutput-sxfe

I get no signal when running 
vdr-sxfe --fullscreen --video vdpau --post tvtime:method=use_vo_driver

Any configuration steps I'm missing?

---

### Post by steefjeqv on 2010-02-27
Hi,

No signal is good. You just need the correct channels.conf now.
You can use w_scan to do this.

sudo apt-get install w-scan

Then scan for channels :

sudo w_scan > /var/lib/vdr/channels.conf

The above command is pretty basic, so you may need to set some additional parameters. You can list all available possibilities by the following :

sudo w_scan --help

Greetings,
Steven

---

### Post by Wilb on 2010-02-27
Yep, sounds like you're making good progress now. No signal is a good thing, your VDR is running and VDR-SXFE is talking to it.

I have had all sorts of problems with scanning and it threw me off track for a while. Thought I had a problematic setup when it just turned out to be my channels.conf being screwed up. I mainly download my channel lists from here now:

[http://www.vdr-settings.com/download/channels/]("http://www.vdr-settings.com/download/channels/") 

Do you have a fixed dish or motorised? If motorised then it may be worth focusing on getting one location up and running first before installing the rotor addon. Have you got as far as configuring your keyboard or remote so you can use it to control VDR?

---

### Post by johnnytoxic on 2010-02-27
I'm sorted with the channels.conf 

I always put a FTA channel at the top to test.

I'm guessing it still looks at /etc/vdr/channels.conf

---

### Post by Wilb on 2010-02-27
Should do yes. Anything useful in syslog? Can you confirm your card is configured & working ok by testing in Kaffeine or similar?

---

### Post by johnnytoxic on 2010-03-03
Just to update.

I'm now using the latest yavdr distribution.

I've managed to add SC to the install and all is working (fingers crossed) :) Through this distro all channels are working without stutter on xine 0.9.3. Must be some configuration setting I was missing when I was setting it up myself.

yavdr has XBMC installed as well which is a nice extra.

This is was I changed/added:

SC
edited xorg.conf.yavdr so my display is now at 50hz
upgraded alsa to the latest version and patched so I get audio through HDMI on my GT240.


Anyone know if there is a way to configure my vbox2 diseqc motor with vdr 1.7.10 ? Not sure if this can be done.

---

### Post by Sav on 2010-03-04
> **johnnytoxic said:**
> Just to update.

I'm now using the latest yavdr distribution.

I've managed to add SC to the install and all is working (fingers crossed) :) Through this distro all channels are working without stutter on xine 0.9.3. Must be some configuration setting I was missing when I was setting it up myself.

yavdr has XBMC installed as well which is a nice extra.

This is was I changed/added:

SC
edited xorg.conf.yavdr so my display is now at 50hz
upgraded alsa to the latest version and patched so I get audio through HDMI on my GT240.


Anyone know if there is a way to configure my vbox2 diseqc motor with vdr 1.7.10 ? Not sure if this can be done.

Can you write a little how-to ad add the sc plugin? Thanks in advance

---

### Post by johnnytoxic on 2010-03-04
> **Sav said:**
> Can you write a little how-to ad add the sc plugin? Thanks in advance

**Howto: Install SC into yavdr**

I got the package from a german message board.

I've uploaded it here [[COLOR="Red"]vdr-plugin-sc_0.9.x~hg2_i386.deb[/COLOR]]("http://www.filedropper.com/vdr-plugin-sc09xhg2i386")

Load up yavdr and go into Applications > Internet
Navigate to the link above
Save vdr-plugin-sc_0.9.x~hg2_i386.deb to VDR home directory
Exit the browser
Applications > Terminal
sudo passwd
su
cd /var/lib/vdr
cp vdr-plugin-sc_0.9.x~hg2_i386.deb /usr/local/src
cd /usr/local/src
./vdr-plugin-sc_0.9.x~hg2_i386.deb
chown vdr:vdr /etc/vdr/plugins/sc
cd /etc/vdr/plugins
apt-get install nano
nano order.conf
replace firstplugin with sc
ctrl+x
y to save
enter
cd /etc/vdr/plugins/sc
nano cardclient.conf

This is the template I use. Paste this in and edit the relevent information.

The example is for a cccam connection on the bottom line.

ctrl+x
y to save
enter

Restart the box and all should be working.

```
#
# Comment lines can start with # or ;
#
# every client line starts with the client name, followed by some arguments:
# 'hostname' is the name of the server
# 'port'     is the port on the server
# 'emm'      is a flag to allow EMM transfers to the server
#            (0=disabled 1=enabled)
# 'caid'     (optional) caid on which this client should work
# 'mask'     (optional) mask for caid e.g. caid=1700 mask=FF00 would allow
#            anything between 1700 & 17FF.
#            Default is 1700 & FF00. If only caid is given mask is FFFF.
#            You may give multiple caid/mask values comma separated
#            (e.g. 1702,1722,0d0c/ff00).
# 'username' is the login username
# 'password' is the login password
#
# radegast client
# radegast:hostname:port:emm/caid/mask
#
# aroureos client
# 'hexbase'
# 'hexserial' card data for which EMM updates should be send
# aroureos:hostname:port:emm/caid/mask:hexbase:hexserial
#
# camd33 client (tcp protocol)
# 'aeskey'   is the AES key (32bytes), disable encryption if missing
# camd33:hostname:port:emm/caid/mask:username:password:aeskey
#
# camd35 client (udp protocol)
# camd35:hostname:port:emm/caid/mask:username:password
#
# cardd client
# cardd:hostname:port:emm/caid/mask:username:password
#
# buffy client
# 'aeskey'   is the AES key (32bytes), disable encryption if missing
# buffy:hostname:port:emm:username:password:aeskey
#
# newcamd client
# 'cfgkey' is the config key (28bytes)
# newcamd:hostname:port:emm/caid/mask:username:password:cfgKey
#
# gbox client
#
# NOTE: hostname & port will be ignore. GBOX must be runnning on the local
# machine. For convinience you should choose localhost:8004
# gbox:hostname:port:emm/caid/mask
#
# ccam client
#
# NOTE: hostname will be ignore. CCcam must be runnning on the local machine
# 'socket' is the name of the camd socket file. For multiple cards add %d
# into the string. This will be replaced with the number 0-3.
# e.g. /var/emu/chroot%d/tmp/camd.socket
cccam2:server.here.org:17000:1/0000/0000:username:password
```

---

### Post by Sav on 2010-03-04
Thanks a lot

---

### Post by Wilb on 2010-03-04
> **johnnytoxic said:**
> Just to update.

I'm now using the latest yavdr distribution.

I've managed to add SC to the install and all is working (fingers crossed) :) Through this distro all channels are working without stutter on xine 0.9.3. Must be some configuration setting I was missing when I was setting it up myself.

yavdr has XBMC installed as well which is a nice extra.

This is was I changed/added:

SC
edited xorg.conf.yavdr so my display is now at 50hz
upgraded alsa to the latest version and patched so I get audio through HDMI on my GT240.


Anyone know if there is a way to configure my vbox2 diseqc motor with vdr 1.7.10 ? Not sure if this can be done.

Glad you've made progress. How you finding YaVDR in general? Tempted to give it a try but I think I've got my installation somewhere near where I want it to be now anyway so probably wouldn't get much benefit from it.

If your vbox is a disecq motor then you should just be able to control it with the rotor plugin.

---

### Post by johnnytoxic on 2010-03-04
> **Wilb said:**
> Glad you've made progress. How you finding YaVDR in general? Tempted to give it a try but I think I've got my installation somewhere near where I want it to be now anyway so probably wouldn't get much benefit from it.

If your vbox is a disecq motor then you should just be able to control it with the rotor plugin.

I'm really impressed with it especially the XBMC which allows me to stream mkvs from my main computer.

Didn't work out of the box but all the backend was there. Few modifications and it now has more functionality than a dreambox.

Just installed the rotor plugin from TeamVDR which seems to be working. Just got to configure it.

---

### Post by Wilb on 2010-03-04
> **johnnytoxic said:**
> I'm really impressed with it especially the XBMC which allows me to stream mkvs from my main computer.

Didn't work out of the box but all the backend was there. Few modifications and it now has more functionality than a dreambox.

Just installed the rotor plugin from TeamVDR which seems to be working. Just got to configure it.

Excellent news. One thing I'm really impressed with is the PearlHD skins, makes it seem much more polished than the old style VDR look.

---

### Post by steefjeqv on 2010-03-04
Glad to see everything is working.

And yes, the yaVDR boys have done a great job (together with the e-Tobi Debian team, all the plugin devs, the VDR Portal, Klaus Schmidinger and ...).

Great open-source software !

Can't wait for a Lucid yaVDR to try out.

Greetings,
Steven

---

### Post by Sav on 2010-03-04
Hi, I'm unable to get the new sc plugin working as client for CCcam server.
My cardclient.conf looks like this:
> cccam2:IP:PORT:1/0000/0000:USER:PASSWORD:NODEID=XXXXXXXXXXXXXXXX
vdr crashes with a buffer overflow error, with this backtrace:
> Feb 28 17:53:11.154 [general.info] SC version 1.0.0pre-HG-a851247855bc+ starting (VDR 1.7.10)
Feb 28 17:53:11.154 [core.load] ** Plugin config:
Feb 28 17:53:11.154 [core.load] ** Key updates (AU) are enabled (all CAIDs) (no prestart)
Feb 28 17:53:11.154 [core.load] ** Local systems DON'T take priority over cached remote
Feb 28 17:53:11.154 [core.load] ** Concurrent FF recordings are allowed
Feb 28 17:53:11.154 [core.load] ** Force transfermode with digital audio
Feb 28 17:53:11.154 [core.load] ** ECM cache is set to enabled
Feb 28 17:53:11.154 [core.load] ** ScCaps are 1 2 3 0 0 0 0 0 0 0
Feb 28 17:53:11.154 [general.info] loading cardclient config from /etc/vdr/plugins/sc/cardclient.conf
Feb 28 17:53:11.154 [cardclient.cccam2] logout from server initiated
Feb 28 17:53:11.154 [cardclient.cccam2extra] reader thread stopped
Feb 28 17:53:11.154 [cardclient.cccam2extra] network shut down
Feb 28 17:53:11.154 [cardclient.cccam2extra] logout done
Feb 28 17:53:11.154 [cardclient.core] hostname=IP port=xxxx emm=1 emmCaids 0000/0000
Feb 28 17:53:11.154 [cardclient.core] cccam2: username=XXXXX password=XXXXXX
Feb 28 17:53:11.155 [cardclient.core] our nodeid: XXXXXXXXXX
Feb 28 17:53:11.155 [cardclient.core] pretended CCcam version '2.0.11' build '2892'
Feb 28 17:53:11.155 [cardclient.core] client 'cccam2' ready
Feb 28 17:53:11.155 [cardclient.cccam2] logout from server initiated
Feb 28 17:53:11.155 [cardclient.cccam2extra] reader thread stopped
Feb 28 17:53:11.155 [cardclient.cccam2extra] network shut down
Feb 28 17:53:11.155 [cardclient.cccam2extra] logout done
Feb 28 17:53:11.155 [core.net] connecting to IP:PORT/tcp (IP)
Feb 28 17:53:11.506 [cardclient.cccam2extra] welcome checksum correct
Feb 28 17:53:11.856 [cardclient.login] CCcam login succeed
*** buffer overflow detected ***: /usr/bin/vdr terminated
======= Backtrace: =========
/lib/libc.so.6(__fortify_fail+0x37)[0x7f7b3be72647]
/lib/libc.so.6[0x7f7b3be715f0]
/usr/lib/vdr/plugins/libsc-cardclient-29.so.1.7.10(_ZN17cCardClientCCcam25LoginEv+0x2f9)[0x7f7b38c72889]
/usr/lib/vdr/plugins/libsc-cardclient-29.so.1.7.10(_ZN21cSystemLinkCardClient14ParseLine PlainEPKc+0x13c)[0x7f7b38c6720c]
/usr/lib/vdr/plugins/libvdr-sc.so.1.7.10(_ZN18cStructLoaderPlain4LoadEb+0x19c)[0x7f7b3a8e14ac]
/usr/lib/vdr/plugins/libvdr-sc.so.1.7.10(_ZN14cStructLoaders4LoadEb+0x3d)[0x7f7b3a8df57d]
/usr/lib/vdr/plugins/libvdr-sc.so.1.7.10(_ZN8cSoftCAM4LoadEPKc+0x3a)[0x7f7b3a8da13a]
/usr/lib/vdr/plugins/libvdr-sc.so.1.7.10(_ZN9cScPlugin5StartEv+0x6e)[0x7f7b3a8dac5e]
/usr/bin/vdr(_ZN14cPluginManager12StartPluginsEv+0x40)[0x4b3a90]
/usr/bin/vdr(main+0x1fe5)[0x4e91a5]
/lib/libc.so.6(__libc_start_main+0xfd)[0x7f7b3bd99abd]
/usr/bin/vdr[0x458329]
======= Memory map: ========
00400000-00541000 r-xp 00000000 08:07 12443 /usr/bin/vdr
00740000-00741000 r--p 00140000 08:07 12443 /usr/bin/vdr
00741000-00743000 rw-p 00141000 08:07 12443 /usr/bin/vdr
00743000-00750000 rw-p 00000000 00:00 0
024a3000-028ba000 rw-p 00000000 00:00 0 [heap]
7f7b30000000-7f7b30f8f000 rw-p 00000000 00:00 0
7f7b30f8f000-7f7b34000000 ---p 00000000 00:00 0
7f7b3539e000-7f7b3539f000 ---p 00000000 00:00 0
7f7b3539f000-7f7b35b9f000 rw-p 00000000 00:00 0
7f7b35b9f000-7f7b35bab000 r-xp 00000000 08:07 2253 /lib/libnss_files-2.10.1.so
7f7b35bab000-7f7b35daa000 ---p 0000c000 08:07 2253 /lib/libnss_files-2.10.1.so
7f7b35daa000-7f7b35dab000 r--p 0000b000 08:07 2253 /lib/libnss_files-2.10.1.so
7f7b35dab000-7f7b35dac000 rw-p 0000c000 08:07 2253 /lib/libnss_files-2.10.1.so
7f7b35dc8000-7f7b35df5000 rw-p 00000000 00:00 0
7f7b35df5000-7f7b35df6000 ---p 00000000 00:00 0
7f7b35df6000-7f7b365f7000 rw-p 00000000 00:00 0
7f7b365f7000-7f7b365f8000 ---p 00000000 00:00 0
7f7b365f8000-7f7b36df8000 rw-p 00000000 00:00 0
7f7b36df8000-7f7b36df9000 ---p 00000000 00:00 0
7f7b36df9000-7f7b375f9000 rw-p 00000000 00:00 0
7f7b375f9000-7f7b375fa000 r--s 00000000 08:07 101531 /var/cache/fontconfig/48fef66b76e7de9c5c56a6dcc7723c04-x86-64.cache-2
7f7b375fa000-7f7b375fb000 r--s 00000000 08:07 101530 /var/cache/fontconfig/cb7d13eeb0521c8bf38f4717320dc78b-x86-64.cache-2
7f7b375fb000-7f7b375fc000 r--s 00000000 08:07 101529 /var/cache/fontconfig/26de28bc8622bbc1fb67fd234c21975f-x86-64.cache-2
7f7b375fc000-7f7b375fd000 r--s 00000000 08:07 119876 /var/cache/fontconfig/c05880de57d1f5e948fdfacc138775d9-x86-64.cache-2
7f7b375fd000-7f7b37606000 r--s 00000000 08:07 119873 /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86-64.cache-2
7f7b37606000-7f7b37608000 r--s 00000000 08:07 119874 /var/cache/fontconfig/99e8ed0e538f840c565b6ed5dad60d56-x86-64.cache-2
7f7b37608000-7f7b3760b000 r--s 00000000 08:07 119884 /var/cache/fontconfig/f24b2111ab8703b4e963115a8cf14259-x86-64.cache-2
7f7b3760b000-7f7b3760e000 r--s 00000000 08:07 119882 /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86-64.cache-2
7f7b3760e000-7f7b37612000 r--s 00000000 08:07 88591 /var/cache/fontconfig/6eb3985aa4124903f6ff08ba781cd364-x86-64.cache-2
7f7b37612000-7f7b37613000 r--s 00000000 08:07 119868 /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86-64.cache-2
7f7b37613000-7f7b37618000 r--s 00000000 08:07 119861 /var/cache/fontconfig/062808c12e6e608270f93bb230aed730-x86-64.cache-2
7f7b37618000-7f7b3761c000 r--s 00000000 08:07 119875 /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86-64.cache-2
7f7b3761c000-7f7b37620000 r--s 00000000 08:07 119870 /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86-64.cache-2
7f7b37620000-7f7b37630000 r--s 00000000 08:07 119862 /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86-64.cache-2
7f7b37630000-7f7b37631000 r--s 00000000 08:07 1546 /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86-64.cache-2
7f7b37631000-7f7b3765f000 r--s 00000000 08:07 101525 /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-x86-64.cache-2
7f7b3765f000-7f7b376c2000 r-xp 00000000 08:07 292405 /usr/lib/vdr/plugins/libvdr-streamdev-server.so.1.7.10
7f7b376c2000-7f7b378c1000 ---p 00063000 08:07 292405 /usr/lib/vdr/plugins/libvdr-streamdev-server.so.1.7.10
7f7b378c1000-7f7b378c4000 r--p 00062000 08:07 292405 /usr/lib/vdr/plugins/libvdr-streamdev-server.so.1.7.10
7f7b378c4000-7f7b378c6000 rw-p 00065000 08:07 292405 /usr/lib/vdr/plugins/libvdr-streamdev-server.so.1.7.10
7f7b378c6000-7f7b378f7000 r-xp 00000000 08:07 292425 /usr/lib/vdr/plugins/libvdr-femon.so.1.7.10
7f7b378f7000-7f7b37af6000 ---p 00031000 08:07 292425 /usr/lib/vdr/plugins/libvdr-femon.so.1.7.10
7f7b37af6000-7f7b37af9000 r--p 00030000 08:07 292425 /usr/lib/vdr/plugins/libvdr-femon.so.1.7.10
7f7b37af9000-7f7b37afa000 rw-p 00033000 08:07 292425 /usr/lib/vdr/plugins/libvdr-femon.so.1.7.10
7f7b37afa000-7f7b37b04000 rw-p 00000000 00:00 0
7f7b37b04000-7f7b37b43000 r-xp 00000000 08:07 292411 /usr/lib/vdr/plugins/libvdr-xine.so.1.7.10/usr/bin/runvdr: line 62: 9580 Aborted /usr/bin/vdr -c /etc/vdr --lirc --no-kbd -E /var/vdr -l 3 -P sc -P skinreel -P xine -P femon -P streamdev-server -u root
Sun Feb 28 17:53:11 CET 2010 reloading DVB driver 

There aren't any problems running the "classic" LD preload 

Any ideas?

---

### Post by Wilb on 2010-03-04
Did you install the packaged one posted or did you roll your own? I'd try and build your own to make sure its built against all the stuff you've got installed on your system, the packaged version might be built against a different version of a library or something which may be causing it to crash.

---

### Post by johnnytoxic on 2010-03-04
This is the place I got the plugin from.

[http://www.4freeboard.to/board/thread.php?threadid=31425&threadview=0&hilight=&hilightuser=0&page=3]("http://www.4freeboard.to/board/thread.php?threadid=31425&threadview=0&hilight=&hilightuser=0&page=3")

They mention about a buffer overflow problem that is resolved, which is the version I downloaded.

Are you using the latest yavdr release 0.1.1 ? 

The only difference I can think of is that I did an apt-get update & apt-get upgrade when I updated Alsa. Maybe this fixed an issue for me. Also I don't have a NODEID at the end of my entry in cardclient.conf

---

### Post by Sav on 2010-03-05
> **Wilb said:**
> Did you install the packaged one posted or did you roll your own? I'd try and build your own to make sure its built against all the stuff you've got installed on your system, the packaged version might be built against a different version of a library or something which may be causing it to crash.

I compiled it by my self, against vdr.1.7.10, in karmic 64bit. I still have to to try yavdr.

---

### Post by Sav on 2010-03-08
Compiled again, under karmic 32, using packages from vdr karmic team.
Again, it crashes using the cccam2 option. No problems with the old fashioned cccam and LD preload.

---

### Post by Wilb on 2010-03-08
I compiled a fresh version of the plugin over the weekend and had some problems with it so rolled back, I've still not experienced the crashes that you're mentioning though I'm afraid.

---

### Post by Sav on 2010-03-08
I hate this.
Now that I switched to karmic 32bit, everything is wrong.
The CCcam server crashes with this:
> 21:19:12.781 CCcam: ======================================================================
21:19:12.781 CCcam: starting CCcam 2.1.3 compiled on Nov 14 2009@00:48:18
21:19:12.781 CCcam: ======================================================================
21:19:12.782 CCcam: online using nodeId 71f1aea394ba36aa
21:19:12.782 CCcam: dvb api3 detected
21:19:12.782 CCcam: DM8000 detected
21:19:12.782 CCcam: create 8 cam device(s)
21:19:12.794 CCcam: readKeyfile: cannot open /var/keys/SoftCam.Key or not found
21:19:12.794 CCcam: readKeyfile: cannot open /var/keys/AutoRoll.Key or not found
21:19:12.794 CCcam: static cw not found or bad
21:19:12.794 CCcam: parsed 0 entries from /var/etc/CCcam.prio
21:19:12.794 CCcam: readProviderfile: cannot open /var/etc/CCcam.providers or not found
21:19:12.794 CCcam: readChannelList: cannot open /var/etc/CCcam.channelinfo or not found
21:19:12.794 CCcam: server started on port 12000
21:19:14.614 CCcam: no working cam devices, no need to start pmthandler

---

### Post by Wilb on 2010-03-08
What version are you using? Try going back to .11 rather than .14...

---

### Post by Sav on 2010-03-09
> **Wilb said:**
> What version are you using? Try going back to .11 rather than .14...

I use the 2.1.3. What makes me mad is that the same version worked under the old environment (karmic 64bit)

---

### Post by Wilb on 2010-03-09
> **Sav said:**
> I use the 2.1.3. What makes me mad is that the same version worked under the old environment (karmic 64bit)

Sorry,  I meant 2.1.1 rather than 2.1.4.

---

### Post by Sav on 2010-03-10
Solved, rolling back to 2.1.2
Strange that the newer version works in a 64bit environment.
By the way, the client part of the sc plugin still doesn't work.

Long live to LD preload

---

### Post by m00anj00 on 2010-03-12
I disagree with the above, cccam2 in cardclient.conf works fine. my question is: why do I have to wait 56seconds for the ecm.cache to populate on an unseen channel.  its fine after but for the first time it delays.

---

### Post by banditnew on 2010-05-13
/usr/local/src/vdr# make
menu.c:2278:2: error: #endif without #if
make: *** Deleting file `.dependencies'
g++ -g -O2 -Wall -Woverloaded-virtual -Wno-parentheses -c -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_LARGEFILE64_SOURCE -DUSE_CMDRECCMDI18N -DUSE_CMDSUBMENU -DUSE_CUTTIME -DUSE_DDEPGENTRY -DUSE_DOLBYINREC -DUSE_LIEMIEXT -DUSE_PLUGINMISSING -DUSE_ROTOR -DUSE_SETTIME -DUSE_STREAMDEVEXT -DUSE_WAREAGLEICON -DUSE_YAEPG -DREMOTE_KBD -DVDR_USER=\"root\" -DLIRC_DEVICE=\"/dev/null\" -DRCU_DEVICE=\"/dev/ttyS1\" -D_GNU_SOURCE -DVIDEODIR=\"/media/video\" -DCONFDIR=\"/etc/vdr\" -DPLUGINDIR=\"/usr/lib/vdr/plugins\" -DLOCDIR=\"/usr/share/locale\" -DUSE_PLUGINAPI -I/usr/include/freetype2 -I/usr/local/src/s2-liplianin/linux/include/linux//include audio.c
In file included from channels.h:13,
                 from device.h:13,
                 from dvbdevice.h:16,
                 from audio.c:12:
config.h:328: error: ‘cCommands’ was not declared in this scope
config.h:328: error: ‘cmds’ was not declared in this scope
config.h:328: error: expected primary-expression before ‘const’
config.h:328: error: expected primary-expression before ‘bool’
config.h:328: error: expected primary-expression before ‘bool’
config.h:328: error: initializer expression list treated as compound expression
make: *** [audio.o] Error 1

i get this error.please help me.

---

### Post by art2003 on 2010-05-14
Is this error with vanilla vdr?
You have to give more info on what lead to that error, vdr version, patches, etc

---

### Post by banditnew on 2010-05-14
> **banditnew said:**
> /usr/local/src/vdr# make
menu.c:2278:2: error: #endif without #if
make: *** Deleting file `.dependencies'
g++ -g -O2 -Wall -Woverloaded-virtual -Wno-parentheses -c -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_LARGEFILE64_SOURCE -DUSE_CMDRECCMDI18N -DUSE_CMDSUBMENU -DUSE_CUTTIME -DUSE_DDEPGENTRY -DUSE_DOLBYINREC -DUSE_LIEMIEXT -DUSE_PLUGINMISSING -DUSE_ROTOR -DUSE_SETTIME -DUSE_STREAMDEVEXT -DUSE_WAREAGLEICON -DUSE_YAEPG -DREMOTE_KBD -DVDR_USER=\"root\" -DLIRC_DEVICE=\"/dev/null\" -DRCU_DEVICE=\"/dev/ttyS1\" -D_GNU_SOURCE -DVIDEODIR=\"/media/video\" -DCONFDIR=\"/etc/vdr\" -DPLUGINDIR=\"/usr/lib/vdr/plugins\" -DLOCDIR=\"/usr/share/locale\" -DUSE_PLUGINAPI -I/usr/include/freetype2 -I/usr/local/src/s2-liplianin/linux/include/linux//include audio.c
In file included from channels.h:13,
                 from device.h:13,
                 from dvbdevice.h:16,
                 from audio.c:12:
config.h:328: error: &#8216;cCommands&#8217; was not declared in this scope
config.h:328: error: &#8216;cmds&#8217; was not declared in this scope
config.h:328: error: expected primary-expression before &#8216;const&#8217;
config.h:328: error: expected primary-expression before &#8216;bool&#8217;
config.h:328: error: expected primary-expression before &#8216;bool&#8217;
config.h:328: error: initializer expression list treated as compound expression
make: *** [audio.o] Error 1

i get this error.please help me.


sorry 
my machine amd phenom
9600 gt
vdr 1.7.10 and 1.7.14 give me same error
ubuntu karmic and jaunty give me same error too

following your guide

---

### Post by coolercooler on 2010-06-20
This is my channels list if anyone's interested.

Mainly 28.2.e with HD's a few other too.

I couldn't get these to work in hd if anyone can please let us know how.
```
 :->7.0E EUTELSAT All HD#######################################################
Nat Geo HD;Digital Platform:10928:hC34M2O0S0:S7.0E:30000:2100=2:2300=TUR,2301=ORJ:0:664,D00:7806:126:21000:0
Nat Geo Turk HD;Digital Platform:10886:hC34M2O0S0:S7.0E:30000:5001=2:5002=TUR,5001=ORJ:0:664,D00:7901:0:0:0
DiziMax More HD;Digital Platform:10886:hC34M2O0S0:S7.0E:30000:3000=2:3001=TUR,3002=ORJ:0:664,D00:7902:0:0:0
DiziMax More HD;Digital Platform:10886:hC34M2O0S0:S7.0E:30000:2100=2:2101=TUR,2102=ORJ:0:664,D00:7912:0:0:0
Lig TV HD;Digital Platform:10886:vC34M2O0S0:S7.0E:30000:202=2:302=TUR,304=ORJ:0:664,D00:202:126:21100:0
MovieMax HD;Digital Platform:10886:vC34M2O0S0:S7.0E:30000:205=2:305=TUR,306=ORJ:0:664,D00:205:126:21100:0
Eurosport HD;Digital Platform:10886:vC34M2O0S0:S7.0E:30000:201=2:301=TUR,311=ORJ:0:664,D00:206:126:21100:0
SporMax HD;Digital Platform:10886:vC34M2O0S0:S7.0E:30000:210=2:309=TUR,310=ORJ:0:664,D00:208:126:21100:0
Dizimax HD;Digital Platform:10886:vC34M2O0S0:S7.0E:30000:211=2:355=TUR,356=ORJ:0:664,D00:210:126:21100:0
```

---

### Post by art2003 on 2010-06-20
coolercooler,

Thaniks for your contribution!

I suggest you post the list of non working HD channels to the vdr developers list (you need to register first, it is free)

[email]vdr@linuxtv.org[/email]

come to think of it, I will do this on your behalf

---

### Post by rulet on 2010-07-19
What gives better quality of the sound -- OSS or Alsa? Or it is the same quality?

---

### Post by art2003 on 2010-07-22
OSS is for example what a dreambox uses, not ALSA.
OSS is supposed to have better quality, although my ears (which are not the sharpest as a result of industrial injury) can not tell the difference.
The down side with OSS is you need to install a new version every 6 months as it expires. It is free as long as you keep upgrading every 6 months or you can pay them some 50US$ for a licence (which in my opinion is excessive)

---

### Post by Wilb on 2010-07-22
ALSA is fine.

Question - has anyone else started having problems with EPG data from 28.2E? I use the EEPG plugin to grab my data, previously from 11778 vertical but I've just noticed that I don't seem to get any valid data when tuning to there any more. 

Looking at [http://en.kingofsat.net/packages.php?&id=2&standard=All&ordre=date_maj&filtre=no](http://en.kingofsat.net/packages.php?&id=2&standard=All&ordre=date_maj&filtre=no) I can see a couple of new "EPG Data" streams have been added recently on different transponders, but I don't believe EEPG is picking up any data from there either.

So - anyone else having any problems? Also has anyone done exciting with their setups in the last few months or have you all just been letting them tick along?

---

### Post by art2003 on 2010-07-22
I use the freesat patch for the 28E epg which gives me 7 days epg (on the freesat channels, not on the sky uk ones, but since I do not have a sky uk subscription, I can not watch those channels anyways, so little harm in not having the epg) I take it you have sky uk?

---

### Post by Wilb on 2010-07-23
Yeah I'm a Sky subscriber but hate the HD box they give so eventually aim to do away with it completely and just have a number of tuners in my VDR box & then distribute it around the house.

My setup is still not perfect though, and even less so now I've lost that EPG data. Not sure if its something I've done or something they've changed at their end, thats all. Getting tempted to upgraded my box to 10.04 now though, or maybe even YaVDR 0.2.  I'm so bloody picky with my setup.

---

### Post by steefjeqv on 2010-07-24
Hi,

eep-plugin is working fine here. I'm using Lucid 64bit and the yaVDR repo (stable version) without the CCcam stuff.

Maybe lowering the EPG correction level will help ?

Greetings,
Steven

---

### Post by Wilb on 2010-07-24
Could I ask what channel you use for your EPG for 28.2E? Could you possibly post the line from your channels.conf? The plugin still seems to be functioning OK - for example if I tune to a Sky IT channel @13e that broadcasts EPG data then it picks up and populates fine.

---

### Post by steefjeqv on 2010-07-24
Hi Wilb,

How do I know which channel is used for obtaining EPG ? We're mostly watching BBC, ITV and Channel4.

I've attached my channels.conf, hope it helps.

Greetings,
Steven

---

### Post by Wilb on 2010-07-24
Aah, thanks for the channels.conf anyway. On 28.2E there are two sets of EEPG data transmitted - that on the Freesat channels such as the BBC ones, and the Sky UK EPG data which according to [http://www.linuxtv.org/vdrwiki/index.php/Eepg-plugin](http://www.linuxtv.org/vdrwiki/index.php/Eepg-plugin) is transmitted on 11778V. My system is still happily picking up EPG data from the Freesat channels, its just 11778V that it no longer seems to be picking data up from.

---

### Post by je11y on 2010-09-04
I know this is an old thread,
but I was wondering if anyone had the restore image available for download?

I've tried to contact the OP with no reply, I'm guessing he's busy.

Would appreciate a reply.

Regards

---

### Post by Wilb on 2010-09-10
> **je11y said:**
> I know this is an old thread,
but I was wondering if anyone had the restore image available for download?

I've tried to contact the OP with no reply, I'm guessing he's busy.

Would appreciate a reply.

Regards

No restore image here I'm afraid, but you could give yavdr a try for an easy to use starter image.

---

### Post by vbnm74 on 2011-01-04
Dec 27 22:55:21 sputnik CCcam: starting CCcam 2.2.1 compiled on Nov 21 2010@02:35:58
Dec 27 22:55:21 sputnik CCcam: ================================================== ====================
Dec 27 22:55:21 sputnik CCcam: online using nodeId 6a1d99f1774e0f05
Dec 27 22:55:22 sputnik CCcam: static cw not found or bad
Dec 27 22:55:22 sputnik CCcam: login at 192.168.1.3:12000 failed, server message: client 192.168.1.3 already connected
Dec 27 22:55:22 sputnik CCcam: server started on port 12000
Dec 27 22:55:22 sputnik CCcam: login at 192.168.1.3:12000 failed, server message: client 192.168.1.3 already connected

In what there can be a problem?

---

### Post by coolercooler on 2011-03-19
Update, w_scan now scans HD channels without any problem.

Attached is the latest scan for 28.2E.

An updated guide here with hd skin

[http://ubuntuforums.org/showthread.php?t=1742287](http://ubuntuforums.org/showthread.php?t=1742287)

---

### Post by Tony007 on 2011-12-04
Hi all . is there any live linux cd made that has ccam and engima pre installed ? If any one know of such thing please point me toward it.Thanks

---

### Post by adetheprince on 2012-01-18
> **Tony007 said:**
> Hi all . is there any live linux cd made that has ccam and engima pre installed ? If any one know of such thing please point me toward it.Thanks

thats what am talking about.
I have been looking for such projecy for long time.
But i am sure is doable.
Please help here is will save a lot of time and money for a custom linux reciever. just like dm800hd

---

### Post by art2003 on 2012-01-19
You have openpli enigma2 for ubuntu

[http://www.youtube.com/watch?v=ip9YPOt2oAM](http://www.youtube.com/watch?v=ip9YPOt2oAM)

[http://openpli.org/forums/topic/20871-build-script-for-openpli-enigma2-on-ubuntu-104-32-bit/](http://openpli.org/forums/topic/20871-build-script-for-openpli-enigma2-on-ubuntu-104-32-bit/)

There is no live cd but there are instruction on how to compile openpli enigma2 for ubuntu

CCcam works like in a dreambox, you just need to run /var/bin/CCcam and have a /var/etc/CCcam.cfg config

Mind you IMHO vdr´s code is less flashy but a lot more mature

---

### Post by adetheprince on 2012-01-19
> **art2003 said:**
> You have openpli enigma2 for ubuntu

[http://www.youtube.com/watch?v=ip9YPOt2oAM](http://www.youtube.com/watch?v=ip9YPOt2oAM)

[http://openpli.org/forums/topic/20871-build-script-for-openpli-enigma2-on-ubuntu-104-32-bit/](http://openpli.org/forums/topic/20871-build-script-for-openpli-enigma2-on-ubuntu-104-32-bit/)

There is no live cd but there are instruction on how to compile openpli enigma2 for ubuntu

CCcam works like in a dreambox, you just need to run /var/bin/CCcam and have a /var/etc/CCcam.cfg config

Mind you IMHO vdr´s code is less flashy but a lot more mature

Thank you soo much for the quick reply.
You Are Diamond.
Ok I have another question.
1- I am trying to do this method but i dont have all the requirement yet. I wanted to know if this will work with a normal standard motherboard with 64mb graphic memory (not HD ) and 500mb ram ,30gb HDD, DVB-S2 TV Tuner Card (without remote) and a pentium 4 2.0 GHZ.
just a cheap one i only need this for educational and testing purposes.
2- you said ( There is no live cd but there are instruction on how to compile 1) isnt this Tutorial the same as the open pli for ubuntu. if not what is the difference? 
All what i wanted is to install something like enigma on my pc and scan the channels and  add my own plugin and compile/install. the most important for my project is to add Streamdev /XBMC/VDR and IPTV pluging ( client ) to connect to a IPTV server and stream video online. or even youtube plugin/justinTV etc 
I would really appreciate your help.
I maybe dreaming to do this project. But i am sure is doable
Many thanks and keep up the good work.

---

### Post by adetheprince on 2012-01-20
OOh sorry forget to ask lol

can we just get a montherboard with hdmi connector with a 512mb graphic and follow this tutorial? (skipping Graphic card installation)
this motherboard with hdmi connectors will it do the job? 
ABIT F-I90HD,ATI RX1250,HDMI 1080i

---

### Post by art2003 on 2012-01-20
This tutorial is about vdr, it can do all the things you mention (there is a plugin vnsiserver for vdr and a matching xbmc plugin so they talk to each other. there is a vdr iptv plugin, streamdev, etc

And... there is a vdr ready distro (all that it is missing is CCcam which you have to install by hand, and the sc plugin which you can use the instructions here)

[http://www.yavdr.org/](http://www.yavdr.org/)

But if you do not have nvidia/vdpau you better have a fast cpu (2Ghz or more) if you want HD 1080p

On the other side if your graphics card is got only 64megs you are looking at 1280x768 maximum which a 1Ghz cpu can do

---

### Post by adetheprince on 2012-01-21
> **art2003 said:**
> This tutorial is about vdr, it can do all the things you mention (there is a plugin vnsiserver for vdr and a matching xbmc plugin so they talk to each other. there is a vdr iptv plugin, streamdev, etc

And... there is a vdr ready distro (all that it is missing is CCcam which you have to install by hand, and the sc plugin which you can use the instructions here)

[http://www.yavdr.org/](http://www.yavdr.org/)

But if you do not have nvidia/vdpau you better have a fast cpu (2Ghz or more) if you want HD 1080p

On the other side if your graphics card is got only 64megs you are looking at 1280x768 maximum which a 1Ghz cpu can do

Thank you soo much again!!

very informative links you provided.

So an Intel dual core 3.0 ghz, 512mb pci graphic, 2gb ram, 120gb HDD, dvb s2 tuner card will be enough? ( SD Channel Only )

I will first get all the bits and peace's together then decide which one to go for, I only asked coz i wanted for experiment only and see how cheap can i make this machine. but the final version i will definitely get the best processor/motherboard/ even wireless network/camera/game controller/ sim card reader/ for mobile broadband if possible.and so on.
But i will test it on my lowest budget for experiment purposes for now and see how it goes.
cccam  will play a big roll in this project i was wondering how stable and which version to chose when dealing ubuntu? I am currently using 2.2.1 in my dm600pvr with PLI.
one final question.
what hardware here does the hd scan? sorry for the noob question but i mean does the dvb s2 card have to be hd compatible or is the graphic card here scan for hd channel? i doubt it is the Graphic? lol or is it just w_scan scans all channels including HD even if you tuner is a old one?
i am not thinking about HD at the moment, but just wonder 
Thank you again for your help m8.

---

### Post by art2003 on 2012-01-21
The hardware you quote will be more than enough
I´ve had the latest vdr running with 256megs of RAM and a 700Mhz Pentium3 (SD only) 

I hear CCccam version 2.1.4 works best for pcs

the dvb-s (or s2) card does the scan
w_scan works fine with dvb-s cards. It only scans HD channels if it detects the card can tune to them

> **adetheprince said:**
> 

So an Intel dual core 3.0 ghz, 512mb pci graphic, 2gb ram, 120gb HDD, dvb s2 tuner card will be enough? ( SD Channel Only )

I will first get all the bits and peace's together then decide which one to go for, I only asked coz i wanted for experiment only and see how cheap can i make this machine. but the final version i will definitely get the best processor/motherboard/ even wireless network/camera/game controller/ sim card reader/ for mobile broadband if possible.and so on.
But i will test it on my lowest budget for experiment purposes for now and see how it goes.
cccam  will play a big roll in this project i was wondering how stable and which version to chose when dealing ubuntu? I am currently using 2.2.1 in my dm600pvr with PLI.
one final question.
what hardware here does the hd scan? sorry for the noob question but i mean does the dvb s2 card have to be hd compatible or is the graphic card here scan for hd channel? i doubt it is the Graphic? lol or is it just w_scan scans all channels including HD even if you tuner is a old one?
i am not thinking about HD at the moment, but just wonder 
Thank you again for your help m8.

---

### Post by adetheprince on 2012-01-21
> **art2003 said:**
> The hardware you quote will be more than enough
I´ve had the latest vdr running with 256megs of RAM and a 700Mhz Pentium3 (SD only) 

I hear CCccam version 2.1.4 works best for pcs

the dvb-s (or s2) card does the scan
w_scan works fine with dvb-s cards. It only scans HD channels if it detects the card can tune to them

Thanks body i am going to test it with amd phonon quad or intel core dual this week when i get my dvb s2 card posted, just ordered one. I will first install the yavdr and install cccam manual with the softcam setup plugin.
how about the enigma 2 plugin? does the yavdr have the enigma 2 for linux? or i have to do that later i mean the pli skin where do i find it?

I am looking for similar thing that you post the links for youtube
that guy had vdr, xbmc, telephone, enigma, Games, IPTV etc/
any ways i really appreciate all your help and i will let you know how its goes.

---

### Post by blendzior on 2012-01-26
does anyone have working rotor plugin ? i have tried many different version and all the time same problems with compiling rotor plugin. 

missing function senddiseqcmd etc

---

### Post by art2003 on 2012-01-27
forget about the rotor plugin, it is extremely busy.

Get instead the rotorng plugin (it is heavily based on the actuator plugin)

It works fine and does not make vdr unstable.

I have sources working (with vdr 1.7.21 at least)

---

### Post by blendzior on 2012-01-29
do i have to install any patches ? or it's just vdr 1.7.21 + plain rotorng plugin ?

i get errors compiling plugin :
```

Plugin rotor:
make[1]: Entering directory `/usr/local/src/vdr-1.7.21/PLUGINS/src/rotorng-0.1.0'
g++ -O2 -Wall -Woverloaded-virtual -Wno-parentheses -c -D_GNU_SOURCE -DPLUGIN_NAME_I18N='"rotorng"' -I../../../include -I/usr/local/src/linux-tbs-sources/linux/include rotorng.c
rotorng.c: In function &#8216;void DiseqcCommand(int, int, int)&#8217;:
rotorng.c:209:23: error: &#8216;class cDevice&#8217; has no member named &#8216;SendDiseqcCmd&#8217;
rotorng.c: In member function &#8216;virtual eOSState cMainMenuActuator::ProcessKey(eKeys)&#8217;:
rotorng.c:1308:5: warning: case value &#8216;16387&#8217; not in enumerated type &#8216;eKeys&#8217;
rotorng.c:1093:5: warning: case value &#8216;32769&#8217; not in enumerated type &#8216;eKeys&#8217;
rotorng.c:1313:5: warning: case value &#8216;32771&#8217; not in enumerated type &#8216;eKeys&#8217;
rotorng.c:870:5: warning: case value &#8216;32773&#8217; not in enumerated type &#8216;eKeys&#8217;
rotorng.c:977:5: warning: case value &#8216;32774&#8217; not in enumerated type &#8216;eKeys&#8217;
rotorng.c: In member function &#8216;void cMainMenuActuator::DisplayOsd()&#8217;:
rotorng.c:1491:69: warning: format not a string literal and no format arguments
rotorng.c:1491:69: warning: format not a string literal and no format arguments
rotorng.c:1506:69: warning: format not a string literal and no format arguments
rotorng.c:1506:69: warning: format not a string literal and no format arguments
rotorng.c:1512:69: warning: format not a string literal and no format arguments
rotorng.c:1512:69: warning: format not a string literal and no format arguments
rotorng.c:1519:68: warning: format not a string literal and no format arguments
rotorng.c:1519:68: warning: format not a string literal and no format arguments
rotorng.c:1539:68: warning: format not a string literal and no format arguments
rotorng.c:1539:68: warning: format not a string literal and no format arguments
rotorng.c: In member function &#8216;void cMainMenuActuator::StopScan()&#8217;:
rotorng.c:1662:135: warning: format &#8216;%lld&#8217; expects type &#8216;long long int&#8217;, but argument 2 has type &#8216;uint64_t&#8217;
make[1]: *** [rotorng.o] Error 1
make[1]: Leaving directory `/usr/local/src/vdr-1.7.21/PLUGINS/src/rotorng-0.1.0'

```

---

### Post by art2003 on 2012-01-29
Yes you need a patch or two

with git download the archvdr repo and you will find the patches there neatly organized
apply these two patches and you will be good to go:
opt-42-x_MainMenuHooks
opt-44_rotor


> **blendzior said:**
> do i have to install any patches ? or it's just vdr 1.7.21 + plain rotorng plugin ?

i get errors compiling plugin :
[code]
Plugin rotor:
make[1]: Entering directory `/usr/local/src/vdr-1.7.21/PLUGINS/src/rotorng-0.1.0'
g++ -O2 -Wall -Woverloaded-virtual -Wno-parentheses -c -

---

### Post by blendzior on 2012-01-29
thanks !

finaly i could compile vdr + rotor !

but unfortunately  now i got problem with xbmc

i got channel list in Live Tv, but anytime when i try to play some channel i get error "channel could not be played" or just crash of xbmc.

logs :

```

04:15:44 T:2888817520 M:3827351552   ERROR: AddOnLog: xbmc.pvrclient/VDR Streamdev Client: CVTPTransceiver::SendCommand - Failed with code: 500 (Unknown Command "LSTQ")
04:15:44 T:2888817520 M:3827351552   ERROR: PVR: VDR Streamdev Client/127.0.0.1:2004 - Client returns bad error (-3) after SignalQuality

```
any ideas ?

---

### Post by adetheprince on 2012-01-30
hello art2003

I am now ready to go and i have very reasonable pc to test it with.
amd phenon quad 2.8, 2gb ram, 1gb nvida gt520 pci-E, 120GB HDD, and a TBS6981 DVB 2s dual tuner that support linux.

oK, Long story short, I first had problem installing the driver for my dvb s2 card, but finaly i have manged to install it and its showing the channels ( some HD are freezing or not showing at all).

I have installed the yavdr you told me and its very good but 2 days of work( problem after problem ) and i am very new to linux.
lol


any ways the only issues i have is XBMC shows the channel but takes forever to load , and the main problem is CCcam.
how do you really insert the c line, lol i mean just like CCcam.cfg or its totaly different on cardcleint.conf.
I can connect to the server but no channel and ecm+emm is 0.
Means no picture even when is connected to my local host.
I thought i am missing some configuration on the cardcleint.conf.

here how mine looks like after i tried every format but didnt work.

server my dm600 with nds card.

F: user pass

client (HTPC Yavdr ) cardclient.conf

cccam2:192.168.1.100:12000:1/0000/0000:user:pass.

I also tried just like CCcam.cfg but didnt work.
i tried cccam, cccam1 i tried using localhost or the host server address.
thing is i am connected to my server but with no picture??
i thought to install it manualy but ur tutorial didnt work for me to install just cccam. i have installed SC plugin i can it on the menue saying ready. i reset it but still didnt work.

how to restart cccam on yavdr? manualy since i tried cam rest on the menue but didnt work.

many thanks art2003.

---

### Post by art2003 on 2012-01-30
Instead of streamdev use xvdr plugin for vdr and the corresponding addon for XBMC.

> **blendzior said:**
> thanks !

finaly i could compile vdr + rotor !

but unfortunately  now i got problem with xbmc

i got channel list in Live Tv, but anytime when i try to play some channel i get error "channel could not be played" or just crash of xbmc.

logs :

```

04:15:44 T:2888817520 M:3827351552   ERROR: AddOnLog: xbmc.pvrclient/VDR Streamdev Client: CVTPTransceiver::SendCommand - Failed with code: 500 (Unknown Command "LSTQ")
04:15:44 T:2888817520 M:3827351552   ERROR: PVR: VDR Streamdev Client/127.0.0.1:2004 - Client returns bad error (-3) after SignalQuality

```
any ideas ?

---

### Post by art2003 on 2012-01-30
vdr+sc need a cccam wrapper compiled to work. it is in the contrib folder in the sc plugin

I could set it up remotely for you via ssh but I would charge you a reasonable fee for my time...


> **adetheprince said:**
> hello art2003

I am now ready to go and i have very reasonable pc to test it with.
amd phenon quad 2.8, 2gb ram, 1gb nvida gt520 pci-E, 120GB HDD, and a TBS6981 DVB 2s dual tuner that support linux.

oK, Long story short, I first had problem installing the driver for my dvb s2 card, but finaly i have manged to install it and its showing the channels ( some HD are freezing or not showing at all).

I have installed the yavdr you told me and its very good but 2 days of work( problem after problem ) and i am very new to linux.
lol


any ways the only issues i have is XBMC shows the channel but takes forever to load , and the main problem is CCcam.
how do you really insert the c line, lol i mean just like CCcam.cfg or its totaly different on cardcleint.conf.
I can connect to the server but no channel and ecm+emm is 0.
Means no picture even when is connected to my local host.
I thought i am missing some configuration on the cardcleint.conf.

here how mine looks like after i tried every format but didnt work.

server my dm600 with nds card.

F: user pass

client (HTPC Yavdr ) cardclient.conf

cccam2:192.168.1.100:12000:1/0000/0000:user:pass.

I also tried just like CCcam.cfg but didnt work.
i tried cccam, cccam1 i tried using localhost or the host server address.
thing is i am connected to my server but with no picture??
i thought to install it manualy but ur tutorial didnt work for me to install just cccam. i have installed SC plugin i can it on the menue saying ready. i reset it but still didnt work.

how to restart cccam on yavdr? manualy since i tried cam rest on the menue but didnt work.

many thanks art2003.

---

### Post by adetheprince on 2012-01-30
ok art2003 i dont mind to pay you for your effort.
BUT!! As i said i am doing this for educational purposes and want to learn more about vdr in linux. so i will pay you for fixing it but i still want to know why this is happening and what is causing.?
I rather pay you for tell me how to fix it then pay you for fixing it for me.
please tell me how much?:D
If its reasonable i will pay. but i need some one to explain an easy way to make the cccam the only cam running.

---

### Post by art2003 on 2012-02-01
Hello,

I´ve updated the first post to include a link to download working vdr-1.7.21 sources with plugins such as the favourites, rotorng and menuorg that are hard to come by in a way that works with a modern vdr.

---

### Post by blendzior on 2012-02-03
> **art2003 said:**
> Hello,

I´ve updated the first post to include a link to download working vdr-1.7.21 sources with plugins such as the favourites, rotorng and menuorg that are hard to come by in a way that works with a modern vdr.

thanks

i hope this one works,  otherwise i will start thinking about buying a dreambox 

can u please tell me witch version of xbmc do you use with that package ?

---

### Post by art2003 on 2012-02-03
I don´t find xbmd stable or fast enough so I use mms instead

[http://mymediasystem.org/](http://mymediasystem.org/)

so I use vdr+vdr-xine plugin + xine + mms
From mms I can also run xbmc and even enigma2 (the games section allows you to run not only games but any bash scripts)

If you insist on using xbmc then you need the xvdr addon for xbmc and the xdr plugin for vdr

If you need direct help to get it working I can offer you consultancy services for a modest fee for my time. Still a lot cheaper than paying 400 euro for dreambox HD

> **blendzior said:**
> thanks

i hope this one works,  otherwise i will start thinking about buying a dreambox 

can u please tell me witch version of xbmc do you use with that package ?

---

