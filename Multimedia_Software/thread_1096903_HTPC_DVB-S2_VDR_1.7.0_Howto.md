---
title: "HTPC DVB-S2 VDR 1.7.0 Howto"
date: 2009-03-15
forum: Multimedia Software
---

### Post by art2003 on 2009-03-15
NOTE: This Howto will not be updated any more as of 15th of April 2009 as I do not use vdr 1.7.0
I will strive to keep updating my vdr 1.7.5 tutorial
For my VDR 1.7.5 Howto [click here]("http://ubuntuforums.org/showthread.php?t=1126258")

[http://ubuntuforums.org/showthread.php?t=1126258](http://ubuntuforums.org/showthread.php?t=1126258)

The goal of this howto is to build a functional HTPC with HD satellite tv and HDMI output at 1020p. The idea is for a dedicated machine. We assume a brand-new installation and given the complexity of the tutorial the reasonable way to undo all the changes is to reinstall Ubuntu.

The hardware I chose:
- Motherboard: Abit A-N78HD with the Geforce 8200 IGP
- CPU : AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
- Thermalite silent fan
- Memory : 2 GB DDR2-800 (2X 1 GB)
- DVD-drive : LG GGC-H20LRB (DVD-RW, Blu-Ray and HDDVD)
- Harddisk : 160GB
- Budgetcard : Hauppauge WinTV NOVA-HD-S2 

All this, is connected to a Panasonic FullHD LCD-TV using the onboard HDMI connector with the nvidia closed sources drivers 177.82

**1. Decision time: ALSA or OSS**
*Note: I use OSS 4.1051 (1052 is buggy)*

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
NVIDIA drivers as of 180.32 or earlier do not work with this motherboard.
Instead [download NVIDIA 177.82]("http://www.nvidia.com/object/linux_display_ia32_177.82.html") and install it.  Reboot and you should have 1080p resolution

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
sudo dpkg -i oss-linux-4.1-1052_i386.deb
sudo soundon
osstest
ossinfo -x
ossxmix -dX

```

Once you have followed the above guide to install OSS modify /etc/rc.local
so it looks like this:

sudo gedit /etc/rc.local

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
rm /dev/dsp
ln -s /dev/oss/oss_hdaudio0/spdout1 /dev/dsp

exit 0

```


Click on System, Preferences, Sound and select OSS all over.
Reboot and you should have 1920x1020 with audio over HDMI by default

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
# Provided under the GNU General Public License version 2 or later or the GNU Free Documentation License version 1.2 or later, at your option.

# This script upgrades ALSA on Ubuntu systems with 2.6.24-28 (non)-ubuntu kernels and is not following 
# official Ubuntu/Debian Package handling rules

# This script is not compliant to Ubuntu official package handling. This script overwrites the existing files and modules.
# You won't see any changes on the revisions if you run e.g. Synaptics..
# If there are official ALSA updates supplied by Ubuntu repositories or kernel changes, these will overwrite your manual ALSA installation - 
# you need to re-run this script in this case.
# You can check the Alsa revision by typing "cat /proc/asound/version" or "alsactl --version" or the utils by "aplay --version" 
#
##--------------------------------------------------------------------------------------------------------------------------------------
# Below package variables need to be adapted according to available package ids at  http://www.alsa-project.org/main/index.php/Download 
# otherwise the script execution will fail!
##--------------------------------------------------------------------------------------------------------------------------------------

alsa1019 () {
PACKAGE=1.0.19
DRIVER=alsa-driver-1.0.19
FIRMWARE=alsa-firmware-1.0.19
LIB=alsa-lib-1.0.19
PLUGINS=alsa-plugins-1.0.19
UTILS=alsa-utils-1.0.19
TOOLS=alsa-tools-1.0.19
OSS=alsa-oss-1.0.17
}


#------------Ususally NO Changes to be done below this line-----------------------------------------------------------------------------------------

# script revision
REV="1.16"

#----supported kernels-----------------------------------------------------------------------------------------------------------------

KERNEL1="2.6.24" # Ubuntu kernel family
KERNEL2="2.6.26" # kernel family
KERNEL3="2.6.27" # kernel family
KERNEL4="2.6.28" # kernel family

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
echo -n "Choose Alsa Package (1) 1.0.19 default[1]: " 
   read PACK
   case $PACK in
       		""  	) alsa1019 ;;
       		[1]     ) alsa1019 ;;
       		*	) alsa1019 ;;
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
4. [Multiproto]("http://www.eurocardsharing.com/f273/howto-getting-hvr-4000-nova-hd-cards-working-linux-using-multiproto-63073") or [S2-API]("http://www.eurocardsharing.com/f273/howto-getting-hvr-4000-nova-hd-cards-working-linux-using-s2api-105681") take your pick.[/B]

For S2-API
First the firmware...
```

apt-get install unrar -y
cd /usr/local/src
wget http://tevii.com/Tevii_linuxdriver_0815.rar
unrar x Tevii_linuxdriver_0815.rar
cp tevii_linuxdriver_0815/fw/dvb-fe-cx24116.fw /lib/firmware/dvb-fe-cx24116-1.23.86.1.fw
ln -s /lib/firmware/dvb-fe-cx24116-1.23.86.1.fw /lib/firmware/dvb-fe-cx24116.fw

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

**5. Scan util**
Time to test your hardware is so far all working
Open the terminal

```
cd Desktop
wget http://linuxtv.org/hg/dvb-apps/archive/tip.tar.gz
tar zxvf tip.tar.gz
cd dvb-apps-fe5a6f79468e
make
sudo make install
cd util/scan/dvb-s

scan -o vdr -s 0 Astra-19.2E > channels.conf


```
Here the -s switch is for "-s N use DiSEqC switch position N (DVB-S only)"

The -s value should be 0 if you have no diseqc or if it is connected to the first plug if to the second switch then the value should be 1, if the third then 2, etc

Of course if you have a different satellite replace Astra-19.2E with the correct one
type ls to see the ones available

open the newly created channels.conf and check it does contain lots of channels

**6. FFmpeg**
This little piece of software is part or the better known VLC
We need to compile our own

```

cd /usr/local/src
sudo -s
rm -rf /usr/include/ffmpeg
apt-get install build-essential
apt-get install mercurial cvs subversion libncurses-dev
apt-get install autoconf libtool automake pkg-config gettext
apt-get install liba52-0.7.4-dev liblame-dev libvorbis-dev zlib1g-dev libpng12-dev libx11-dev libxv-dev libasound2-dev
apt-get build-dep ffmpeg
svn checkout svn://svn.mplayerhq.hu/ffmpeg/trunk ffmpeg
cd ffmpeg/
./configure --prefix=/usr --enable-shared --enable-gpl --enable-postproc --enable-libmp3lame --enable-libvorbis --enable-pthreads --enable-libx264 --enable-libtheora --enable-nonfree
make
make install
ldconfig -v
```

**7. Xine-Lib 1.2 CVS:**
```

cd /usr/local/src
apt-get install libcdio-dev libvcdinfo-dev
hg clone http://hg.debian.org/hg/xine-lib/xine-lib-1.2
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

If make fails then edit gedit /usr/local/src/xine-lib-1.2/src/audio_dec Look for -ldts_pic and add -lm after it.

**8. Xine-UI-cvs**

```
cd /usr/local/src
apt-get install libxt-dev
# WARNING! We're going to install LIRCD and with this you can configure your remote if you want it used through LIRCD
apt-get install lirc lirc-modules-source lirc-x liblircclient-dev
wget http://home.vrweb.de/~rnissl/xine-ui-cvs-20090412200000.tar.bz2
tar jxvf xine-ui-cvs-20090412200000.tar.bz2
cd xine-ui
./autogen.sh --prefix=/usr --enable-vdr-keys
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

LIRC.Up         ArrowUp
LIRC.Down       ArrowDown
LIRC.Menu       Menu
LIRC.Ok         Enter
LIRC.Back       BackExit
LIRC.Left       ArrowLeft
LIRC.Right      ArrowRight
LIRC.Red        Red
LIRC.Green      Green
LIRC.Yellow     Yellow
LIRC.Blue       Blue
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
LIRC.Info       ChannelUp
LIRC.Play       Play
LIRC.Pause      Pause
LIRC.Stop       Stop
LIRC.Record     Record
LIRC.FastFwd    Fwdwind
LIRC.FastRew    Rewind
LIRC.Next       NextSong
LIRC.Prev       PrevSong
LIRC.Power      Power
LIRC.PrevChannel PrevCh
LIRC.Volume+    VolumeUp
LIRC.Volume-    VolumeDown
LIRC.Mute       Mute
LIRC.Audio      ChannelDown
LIRC.Subtitles  Sub
LIRC.Schedule   Pictures
LIRC.Channels   TV
LIRC.Timers     Guide
LIRC.Recordings Videos
LIRC.Setup      Music

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
 pre_data       0x1
 gap          199999
 min_repeat 1
 toggle_bit      0


     begin codes
         test1                    0x0174
         Pictures                 0x016F
         Go                       0x0161
         Text                     0x0184
         Sub                      0x0172
         Power                    0x0074
         TV                       0x0179
         Videos                   0x0189
         Music                    0x0188
         Pictures                 0x00E2
         Guide                    0x016D
         Radio                    0x0181
         ArrowUp                  0x0067
         ArrowLeft                0x0069
         Enter                    0x001C
         ArrowRight               0x006A
         ArrowDown                0x006C
         BackExit                 0x00AE
         Menu                     0x008B
         VolumeUp                 0x0073
         VolumeDown               0x0072
         Mute                     0x0071
         ChannelUp                0x0192
         ChannelDown              0x0193
         Record                   0x00A7
         Rewind                   0x00A8
         SkipBack                 0x0195
         Play                     0x00CF
         Pause                    0x0077
         Stop                     0x0080
         Fwdwind                  0x00D0
         SkipFwd                  0x0197
         Sleep                    0x008E
         NextSong                 0x00A3
         PrevSong                 0x00A5
         Sorpre1                  0x00D0
         PrevCh                  0x019C
         1                        0x0002
         2                        0x0003
         3                        0x0004
         4                        0x0005
         5                        0x0006
         6                        0x0007
         7                        0x0008
         8                        0x0009
         9                        0x000A
         *                        0x0037
         0                        0x000B
         #                        0x0029
         one                      0x004F
         two                      0x0050
         three                    0x0051
         four                     0x004B
         five                     0x004C
         six                      0x004D
         seven                    0x0047
         eight                    0x0048
         nine                     0x0049
         ten                      0x0052
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
TEMPIREVENT=`ls /dev/input/by-path/ |grep event-ir`
REMOTE_DEVICE="/dev/input/by-path/$TEMPIREVENT"
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

**9. VDR **

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

```

sudo -s
mkdir -p /media/video/vdr
mkdir -p /usr/lib/vdr/plugins
mkdir -p /usr/lib/vdr/scripts
mkdir /var/bin
cd /usr/local/src
apt-get install libfreetype6-dev libfontconfig1-dev libjpeg62-dev libcap-dev libncurses5-dev libncursesw5-dev
wget ftp://ftp.cadsoft.de/vdr/Developer/vdr-1.7.0.tar.bz2
tar xivf vdr-1.7.0.tar.bz2
ln -s vdr-1.7.0 vdr
wget http://www.linuxtv.org/pipermail/vdr/attachments/20080413/1054bcfb/attachment-0001.bin
mv attachment-0001.bin vdr-1.7.0-h264-syncearly-framespersec-audioindexer-fielddetection-speedup.diff.bz2
bzip2 -d vdr-1.7.0-h264-syncearly-framespersec-audioindexer-fielddetection-speedup.diff.bz2

```

Now ONLY if you installed Multiproto drivers...
```
cd vdr-1.7.0
patch -p1 < ../vdr-1.7.0-h264-syncearly-framespersec-audioindexer-fielddetection-speedup.diff


```

Or ONLY if you installed S2-API drivers
```
wget http://www.linuxtv.org/pipermail/vdr/attachments/20081007/edcd3fcc/attachment-0001.obj
mv attachment-0001.obj vdr-1.7.0-s2api-07102008-h264-clean.patch.gz
gzip -d vdr-1.7.0-s2api-07102008-h264-clean.patch.gz
cd vdr-1.7.0
patch -p1 < ../vdr-1.7.0-h264-syncearly-framespersec-audioindexer-fielddetection-speedup.diff
patch -p1 < ../vdr-1.7.0-s2api-07102008-h264-clean.patch

```

Now for both S2-API and multi proto we are going to create Make.config 
with the code next:

sudo gedit /usr/local/src/vdr-1.7.0/Make.config

```
#
# User defined Makefile options for the Video Disk Recorder
#
# Copy this file to 'Make.config' and change the parameters as necessary.
#
# See the main source file 'vdr.c' for copyright information and
# how to reach the author.
#
# $Id: Make.config.template 2.0 2008/01/13 12:54:09 kls Exp $

### The C compiler and options:

CC       = gcc
CFLAGS   = -g -O2 -Wall

CXX      = g++
CXXFLAGS = -g -O2 -Wall -Woverloaded-virtual -Wno-parentheses

ifdef PLUGIN
CFLAGS   += -fPIC
CXXFLAGS += -fPIC
endif

### The directory environment:

DVBDIR   = /usr/local/src/s2-liplianin/linux
MANDIR   = /usr/man
BINDIR   = /usr/bin

LOCDIR   = /usr/share/locale
PLUGINDIR= ./PLUGINS
PLUGINLIBDIR= /usr/lib/vdr/plugins
VIDEODIR = /media/video/vdr
CONFDIR  = /etc/vdr

### The remote control:

LIRC_DEVICE = /dev/lircd
RCU_DEVICE  = /dev/ttyS1

## Define if you want vdr to not run as root
VDR_USER = root

### You don't need to touch the following:

ifdef DVBDIR
INCLUDES += -I$(DVBDIR)/include
endif
```

and now the last lot of commands:

```
make
make plugins
make install
cp -a svdrpsend.pl /usr/bin
cp *.conf /etc/vdr/
```
/usr/bin/vdr --help

If the last command shows an overview of the options of VDR and it's plugins, VDR is installed but you still need to add a few usefull plugins and to set the vdr backend to run on start


[B]9.B ALTERNATIVE [VDR 1.7.5]("http://ubuntuforums.org/showthread.php?t=1126258")

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
        -P'xineliboutput -l none -r 37890 -p' \
        -P xine \
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


Xineliboutput 1.0.4 [http://sourceforge.net/projects/xineliboutput/](http://sourceforge.net/projects/xineliboutput/)

```

cd /usr/local/src/vdr/PLUGINS/src
apt-get install libextractor-dev
wget http://heanet.dl.sourceforge.net/sourceforge/xineliboutput/vdr-xineliboutput-1.0.4.tar.bz2
tar xivf vdr-xineliboutput-1.0.4.tar.bz2
ln -s xineliboutput-1.0.4 xineliboutput
cd xineliboutput
make
make install
mkdir -p /etc/vdr/plugins/xineliboutput
cp *.mpg /etc/vdr/plugins/xineliboutput/
cd /usr/local/src/vdr/
make plugins
make install

```

(optional)Femon - Signal Information plugin [http://www.linuxtv.org/vdrwiki/index.php/Femon-plugin]("http://www.linuxtv.org/vdrwiki/index.php/Femon-plugin")
```

cd /usr/local/src/vdr/PLUGINS/src
wget http://www.saunalahti.fi/~rahrenbe/vdr/femon/files/vdr-femon-1.7.1.tgz
tar xzvf vdr-femon-1.7.1.tgz
ln -s femon-1.7.1 femon
cd /usr/local/src/vdr/
make plugins
make install

```

(optional)Streamdev plugin (needed only if you plan to use XBMC) [http://streamdev.vdr-developer.org/]("http://streamdev.vdr-developer.org/")
```

cd /usr/local/src/vdr/PLUGINS/src
cvs -d:pserver:anoncvs@vdr-developer.org:/var/cvsroot login
###Simply hit ENTER when asked for a password.
cvs -d:pserver:anoncvs@vdr-developer.org:/var/cvsroot co -D 2/18/09 streamdev
wget http://www.xbmc.org/trac/raw-attachment/ticket/5595/streamdev-cvs180209-vdr-1.7.4_xbmc-v4.patch.gz
gunzip streamdev-cvs180209-vdr-1.7.4_xbmc-v4.patch.gz
patch -p0 < streamdev-cvs180209-vdr-1.7.4_xbmc-v4.patch
sudo mkdir -p /etc/vdr/plugins/streamdev
cd streamdev
sudo cp streamdev/streamdevhosts.conf /etc/vdr/plugins/streamdev
sudo cp streamdev/streamdevhosts.conf /etc/vdr/vdrsvdrphosts.conf
cd /usr/local/src/vdr/
make plugins
make install

```

(optional)Enigma skin
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


sc TRUNK - softcam plugin
```

cd /usr/local/src/vdr/PLUGINS/src
apt-get install libssl-dev 
hg clone -r trunk http://85.17.209.13:6100/sc
cd /usr/local/src/vdr/
make plugins
make install
mkdir -p /etc/vdr/plugins/sc

```

setup plugin (needed if you want CCcam info or ecm.info or to be able to run bash scripts from VDR)
Make sure you have applied the Extensions patch (tested with 70) to VDR and add a line to Make.config
that says:
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
cd /etc/vdr/plugins/setup
sudo mv help /etc/vdr/plugins/setup

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
    <plugin name="xineliboutput" />
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


Skin Reel - VDR Skin
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

XINE - VDR Xine plugin, needed for OXINE to connect to VDR
```

cd /usr/local/src/vdr/PLUGINS/src
# vdr-xine-0.9.1 or later is compatible with VDR 1.7.5
wget http://home.vrweb.de/rnissl/vdr-xine-0.9.1.tgz
tar zxvf vdr-xine-0.9.1.tgz
ln -s xine-0.9.1 xine
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
gedit /var/bin/ca.c

```

```

/* Evil evil evil hack  - lets newcamd write CWs to a file..
 *
 * Compile as follows:
 * gcc -O -fbuiltin -fomit-frame-pointer -fPIC -shared -o ca.so ca.c -ldl
 *
 * then run newcamd with:
 *
 * LD_PRELOAD=./ca.so ./newcamd.i386 newcamd.conf
 *
 * Will then write CWs to /tmp/newcamhack.cw. A patched (vdr) sc will read
 * these codewords to decode a stream.
 *
 * This library is free software; you can redistribute it and/or
 * modify it under the terms of the GNU Library General Public
 * License as published by the Free Software Foundation; either
 * version 2 of the License, or (at your option) any later version.
 *
 * This library is distributed in the hope that it will be useful,
 * but WITHOUT ANY WARRANTY; without even the implied warranty of
 * MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU
 * Library General Public License for more details.
 *
 * You should have received a copy of the GNU Library General Public
 * License along with this library; if not, write to the
 * Free Software Foundation, Inc., 59 Temple Place - Suite 330,
 * Boston, MA 02111-1307, USA.
 */

#define DEBUG

#if defined(__GNUC__) && !defined(__STRICT_ANSI__)

#include <dlfcn.h>
#include <stdarg.h>
#include <stdlib.h>
#include <string.h>
#include <unistd.h>
#include <fcntl.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <linux/dvb/ca.h>
#include <linux/dvb/dmx.h>
#include <linux/dvb/frontend.h>
#include <linux/ioctl.h>
#include <stdio.h>
#include <sys/socket.h>
#include <netinet/in.h>
#include <arpa/inet.h>



/* BSDI has this functionality, but not define :() */
#if defined(RTLD_NEXT)
#define REAL_LIBC RTLD_NEXT
#else
#define REAL_LIBC ((void *) -1L)
#endif

static int cafd = -1;
/*static int cafd1 = -1;
static int cafd2 = -1;
static int cafd3 = -1;*/
static int ecm0 = -1;
static int ecm1 = -1;
static int ecm2 = -1;
static int ecm3 = -1;
static int caf;
static char filename[25];
static unsigned char scw[16];
static int gotcw = 0;
static int pids[64];

int sendcw(pid)
{
		
  unsigned char buffer[18];
   struct sockaddr_in saddr;
   int len;
 
   buffer[0]= pid & 0xff;
   buffer[1]= ((pid >> 8) & 0xFF);
   memcpy(&buffer[2], scw, 16);
 
   int ecmso = socket(PF_INET,SOCK_DGRAM,IPPROTO_UDP);
   
   fcntl(ecmso,F_SETFL,O_NONBLOCK);
   bzero(&saddr,sizeof(saddr));
   saddr.sin_family = AF_INET;
   saddr.sin_port = htons(9000);
   saddr.sin_addr.s_addr = inet_addr("127.0.0.1");
   len = connect(ecmso,(struct sockaddr *) &saddr,sizeof(saddr));
    if (len<0)
    	{
     printf("ca.so: Cannot connect UDP socket\n");
     close(ecmso);
     return 0;
   }
     printf("ca.so: Sendcw \n");
   if ( send(ecmso,buffer, 18, 0) == -1 ) { 
     printf("ca.so: Sendcw Error sending cw\n");
   }
   close(ecmso);
 	return 1;
}

ssize_t write (int __fd, __const void *__buf, size_t __n) __wur
{
static int (*func) (int __fd, __const void *__buf, size_t __n) = NULL;
   // printf ("write buffer %s \n",__buf);
  if (!func)
    func = (int (*) (int __fd, __const void *__buf, size_t __n)) dlsym (REAL_LIBC, "write");

//  if (__fd == ecm0) 
// god this is horrible but I can work out why I cant hook the /tmp/ecm0.info open...
  	{
  		if ((!strncmp(__buf,"pid:",4)) && (gotcw))
  			{
  				int pid;
  				 sscanf(__buf+8,"%x",&pid);
  				// we have pid and cw, cool we are ready to gooo...
  				//sendcw(pid);
  				
  				
  			}
  				
  	}
  return (*func) (__fd,__buf,__n);
}	
	



int
open (const char *pathname, int flags, ...)
{
  static int (*func) (const char *, int, mode_t) = NULL;
  va_list args;
  mode_t mode;
	char buffer[255];
 printf ("%s open...\n",pathname);
  if (!func)
    func = (int (*) (const char *, int, mode_t)) dlsym (REAL_LIBC, "open");

  va_start (args, flags);
  mode = va_arg (args, mode_t);
  va_end (args);

  if (strlen(pathname) > 40)
	exit(0);

  if (!strcmp (pathname, "/dev/dvb/adapter0/ca0"))
    {
#ifdef DEBUG
      printf ("hijacking ca0 open...\n");
#endif
		  cafd = (*func) ("/dev/zero", flags, mode);
		  printf("ca0 fd  = %d",cafd);
      return (cafd);
    }
/*  if (!strcmp (pathname, "/dev/dvb/adapter0/ca1"))
    {
#ifdef DEBUG
      printf ("hijacking ca1 open...\n");
#endif
		  cafd1 = (*func) ("/dev/zero", flags, mode);
		  printf("ca1 fd  = %d",cafd1);
      return (cafd1);
    }
  if (!strcmp (pathname, "/dev/dvb/adapter0/ca2"))
    {
#ifdef DEBUG
      printf ("hijacking ca2 open...\n");
#endif
		  cafd2 = (*func) ("/dev/zero", flags, mode);
		  printf("ca2 fd  = %d",cafd2);
      return (cafd2);
    }
  if (!strcmp (pathname, "/dev/dvb/adapter0/ca2"))
    {
#ifdef DEBUG
      printf ("hijacking ca2 open...\n");
#endif
		  cafd3 = (*func) ("/dev/zero", flags, mode);
		  printf("ca3 fd  = %d",cafd2);
      return (cafd3);
    }*/
    if (!strcmp (pathname, "/dev/dvb/adapter0/demux1"))
    {
	return(*func) ("/dev/dvb/adapter1/demux0", flags, mode);
    	//strcpy(pathname,"/dev/dvb/adapter1/demux0");
    }
    if (!strcmp (pathname, "/dev/dvb/adapter0/demux2"))
    {
	return(*func) ("/dev/dvb/adapter2/demux0", flags, mode);

    	//strcpy(pathname,"/dev/dvb/adapter2/demux0");
    }
    if (!strcmp (pathname, "/dev/dvb/adapter0/demux3"))
    {
	return(*func) ("/dev/dvb/adapter3/demux0", flags, mode);
    	//strcpy(pathname,"/dev/dvb/adapter3/demux0");
    }
  if (!strcmp(pathname,"/tmp/ecm.info"))
  	{
  		 printf ("hijacking /tmp/ecm.info open...\n");
  	return (ecm0 = (*func) (pathname,flags,mode));
  }
 
    return (*func) (pathname, flags, mode);
}

static int
cactl (int fd, int request, void *argp)
{
  ca_descr_t *ca = argp;
  ca_caps_t *cp = argp;
  ca_pid_t  *cpd = argp;
  static unsigned char cw[16];
  unsigned char *c;
  char buf[16];
int card =0;
//if (fd == cafd1) card = 1;
//if (fd == cafd2) card = 2;
//if (fd == cafd3) card = 3;	

#ifdef DEBUG
  printf ("hijacking ca%d ioctl,"
	   "(%d : %x - %p): ",card, fd, request, argp);
  switch (request) {
  case CA_RESET:
    printf ("CA_RESET\n");
    break;
  case CA_GET_CAP:
    printf ("CA_GET_CAP\n");
    break;
  case CA_GET_SLOT_INFO:
    printf ("CA_GET_SLOT_INFO\n");
    break;
  case CA_GET_DESCR_INFO:
    printf ("CA_GET_DESCR_INFO\n");
    break;
  case CA_GET_MSG:
    printf ("CA_GET_MSG\n");
    break;
  case CA_SEND_MSG:
    printf ("CA_SEND_MSG\n");
    break;
  case CA_SET_DESCR:
    printf ("CA_SET_DESCR\n");
    break;
  }
#endif

  switch (request)
    {
    case CA_GET_CAP:
      cp->slot_num = 2;
      cp->slot_type = CA_CI|CA_CI_LINK;
      cp->descr_num = 1;
      cp->descr_type = CA_ECD|CA_NDS|CA_DSS;
      return 0;
      
      case CA_SET_PID:
    printf ("CA_SET_PID\n");
    printf ("CA_SET_PID ahha here we are some decent data....\n");
    printf ("CS_SET_PID pid = %d, index = %d\n",cpd->pid, cpd->index);
    if (cpd->index >=0) 
    pids[cpd->index] = cpd->pid;
    return 1;
    case CA_SET_DESCR:
    	sprintf(filename,"/tmp/cw%d",card);
      caf = open(filename, O_WRONLY|O_CREAT,S_IROTH|S_IRUSR);
      c = &(ca->cw[0]);
#ifdef DEBUG
      printf("Parity: %d, Index: %d, CW: %02hhx%02hhx%02hhx%02hhx%02hhx%02hhx%02hhx%02hhx(%d)\n", ca->parity, ca->index, ca->cw[0], ca->cw[1], ca->cw[2], ca->cw[3], ca->cw[4],
		      ca->cw[5], ca->cw[6], ca->cw[7]);
#endif
      if (!ca->parity)
	 memcpy(&cw, c, 8);
      else
	 memcpy(&cw[8], c, 8);
#ifdef DEBUG
      printf("Wrote: %02hhx%02hhx%02hhx%02hhx%02hhx%02hhx%02hhx%02hhx:%02hhx%02hhx%02hhx%02hhx%02hhx%02hhx%02hhx%02hhx\n",
		      cw[0], cw[1], cw[2], cw[3], 
		      cw[4], cw[5], cw[6], cw[7], 
		      cw[8], cw[9], cw[10], cw[11], 
		      cw[12], cw[13], cw[14], cw[15]);
#endif
      write (caf, &cw, 16);
      memcpy(scw,cw,16);
      gotcw = 1;
      close (caf);
      sendcw(pids[ca->index]);
    //  rename("/tmp/.canewcamdev", "/tmp/newcamhack.cw");
      break;
    }
  return 0;
}

int
ioctl (int fd, int request, void *a)
{
  static int (*func) (int, int, void *) = NULL;

  if (!func)                                                                    
    func = (int (*) (int, int, void *)) dlsym (REAL_LIBC, "ioctl");             

  if (fd == cafd) {
    return cactl (fd, request, a);
  } 
  
 /* if (fd == cafd1) {
  		return cactl (fd, request, a);
  	}
  if (fd == cafd2) {
  		return cactl (fd, request, a);
  	}
  	*/
  
    return (*func) (fd, request, a); 
  
  return 0;
}

int
close (int fd)
{
  static int (*func) (int) = NULL;
    printf ("Closing %d\n",fd);
  if (!func)
    func = (int (*) (int)) dlsym (REAL_LIBC, "close");

  if (fd == cafd)
  	{
    cafd = -1;
    printf ("Closing ca0...\n");
  }
  if (fd == ecm0)
  	{
  		ecm0 = -1;
  		printf ("Closing ecm0...\n");
  	}
#ifdef DEBUG
  
#endif
  return (*func) (fd);
}

#endif

```

[B]
11. OXINE - The cherry on the cake
[/B]
OXINE can be used as a VDR FRONTEND (able to play DVDs, Music, Video files) already patched for VDR and in a .deb format (tested under Ubuntu 8.10) Make sure you installed the XINE plugin before (see instructions above in the VDR-plugins section)

Now, we are going to install a special oxine.deb patched with VDR support
Download [oxine-vdr-patched_0.7.1-1_i386.deb]("http://www.ziddu.com/download/3959648/oxine-vdr-patched_0.7.1-1_i386.rar.html")
```

sudo apt-get install vorbis-tools ffmpeg flac mount
sudo dpkg -i oxine-vdr-patched_0.7.1-1_i386.deb
mkdir ~/.oxine
cd /usr/local/src/ffmpeg
sudo make install
cp /usr/share/oxine/mainmenu.xml ~/.oxine/
# Next line is to edit the Oxine menus, add or remove stuff. It is pretty straight forward..
gedit ~/.oxine/mainmenu.xml

```

lirc mappings follow: ~/.oxine/lirc

```

begin
    prog   = oxine
    button = Pause
    config = toggle_pause_play
end

begin
    prog   = oxine
    button = ArrowLeft
    config = left
end

begin
    prog   = oxine
    button = ArrowRight
    config = right
end

begin
    prog   = oxine
    button = ArrowUp
    config = up
end

begin
    prog   = oxine
    button = ArrowDown
    config = down
end

begin
    prog   = oxine
    button = Play
    config = select
end

begin
    prog   = oxine
    button = Enter
    config = activate
end
begin
    prog   = oxine
    button = BackExit
    config = back
end

begin
    prog   = oxine
    button = Power
    config = shutdown
end

begin
    prog   = oxine
    button = menu
    config = show_osd
end

begin
    prog   = oxine
    button = Stop
    config = stop
end

begin
    prog   = oxine
    button = TV
    config = television
end
begin
    prog   = oxine
    button = Radio
    config = menu_main
end

begin
    prog   = oxine
    button = SkipFwd
    config = menu_playback
end
begin
    prog   = oxine
    button = SkipBack
    config = quit
end
begin
    prog   = oxine
    button = Rewind
    config = skip-30
end
begin
    prog   = oxine
    button = Fwdwind
    config = skip+30
end

begin
    prog   = oxine
    button = Videos
    config = menu_video
end
begin
    prog   = oxine
    button = ChannelUp
    config = zoom+1
end
begin
    prog   = oxine
    button = ChannelDown
    config = zoom-1
end
begin
    prog   = oxine
    button = VolumeUp
    config = volume+5
end
begin
    prog   = oxine
    button = VolumeDown
    config = volume-5
end
begin
    prog   = oxine
    button = Mute
    config = toggle_mute
end
begin
    prog   = oxine
    button = Sub
    config = spu_channel+1
end
begin
    prog   = oxine
    button = Music 
    config = audio_channel+1
end
begin
    prog   = oxine
    button = 0
    config = 0
end
begin
    prog   = oxine
    button = 1
    config = 1
endd
begin
    prog   = oxine
    button = 2
    config = 2
end
begin
    prog   = oxine
    button = 3
    config = 3
end
begin
    prog   = oxine
    button = 4
    config = 4
end
begin
    prog   = oxine
    button = 5
    config = 5
end
begin
    prog   = oxine
    button = 6
    config = 6
end
begin
    prog   = oxine
    button = 7
    config = 7
end
begin
    prog   = oxine
    button = 8
    config = 8
end
begin
    prog   = oxine
    button = 9
    config = 9
end

```

This is my ~/.oxine/mainmenu.xml
```

<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE oxine_menu SYSTEM "http://oxine.sf.net/DTD/menu.dtd">

<!--
*****************************************************************************

This is the standard menu file for oxine's main menu.

The following parameters are used to define the action:

=======================================================================
| parameter name | valid values
=======================================================================
| type           | see menu.dtd
| parameter      | for sub_menu: the name of a file containing a menu
|                | for auto_play: tv, dvd, vcd, cdda
|                | for mrl_play: a valid xine MRL
|                | for shellcommand: a valid shell command
=======================================================================

*****************************************************************************
-->
<oxine_menu x="40" w="380">
  <button>
    <title>Watch Television</title>
    <action type="auto_play" parameter="tv"/>
  </button>
  <button>
    <title>Watch Films</title>
    <action type="video_menu"/>
  </button>
  <button>
    <title>Play a DVD</title>
    <action type="auto_play" parameter="dvd"/>
  </button>
  <button>
    <title>Browse your media</title>
    <action type="media_menu"/>
  </button>
  <button>
    <title>Other</title>
    <action type="sub_menu" parameter="/home/tv/.oxine/othermenu.xml" />
  </button>
  <button>
    <title>Shutdown</title>
    <action type="shutdown"/>
  </button>
</oxine_menu>


```


This is my ~/.oxine/othermenu.xml  (which I made)
```

<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE oxine_menu SYSTEM "http://oxine.sf.net/DTD/menu.dtd">

<!--
*****************************************************************************

This is the standard menu file for oxine's main menu.

The following parameters are used to define the action:

=======================================================================
| parameter name | valid values
=======================================================================
| type           | see menu.dtd
| parameter      | for sub_menu: the name of a file containing a menu
|                | for auto_play: tv, dvd, vcd, cdda
|                | for mrl_play: a valid xine MRL
|                | for shellcommand: a valid shell command
=======================================================================

*****************************************************************************
-->
<oxine_menu x="40" w="380">
  <button>
    <title>Go back to the main menu</title>
    <action type="main_menu" />
  </button>
  <button>
    <title>Shutdown</title>
    <action type="shutdown"/>
  </button>
  <button>
    <title>Current title</title>
    <action type="playback_menu"/>
  </button>
  <button>
    <title>CD / DVD Extractor</title>
    <action type="extractor_menu"/>
  </button>
  <button>
    <title>Edit Settings</title>
    <action type="settings_menu"/>
  </button>
  <button>
    <title>View Images</title>
    <action type="image_menu"/>
  </button>
  <button>
    <title>Show Help</title>
    <action type="help_menu"/>
  </button>
  <button>
    <title>Listen to Music</title>
    <action type="music_menu"/>
  </button>
  <button>
    <title>Go back to the main menu</title>
    <action type="main_menu" />
  </button>
</oxine_menu>


```
For a dedicated HTPC I have oxine running on startup

This last step varies according to what you use: Gnome, KDE, xfce

In Ubuntu (gnome) just click on System, Preferences, Sessions, StartUp Programs
Click on add
and the command is 
```

sudo oxine

```
also add another entry for
```

sudo /etc/init.d/vdr start

```
Now finally you need to enable autologin
System, Administration, Security, tick 'Enable Automatic Login'
and select the user that will login automatically (I created for this purpose a user called tv)

Click on System, Administration, Users & Groups, Unlock, Manage groups, Add group: sudo
tick the tv user to be part of this group

Final step, from the terminal
```

sudo visudo

```
uncomment (delete the # in front) the line saying %sudo ALL=NOPASSWRD: ALL
Delete all the lines coming after that one
save and exist (CTRL+X)

Reboot and oxine should eventually show up
choose 'Watch Television' (if it fails try again after 10 seconds)

Enjoy!

**(OPTIONAL) Rotor Control DiSeqc 1.2**
xdipo allows moving a motor, storing positions, gotoX etc.
I has a GUI and can also be run from a script to go to particular position
It is independent from VDR of Kaffeine and since the VDR rotor plugin doesn't currently compile with S2-API drivers...
```

wget http://panteltje.com/panteltje/satellite/xdipo-0.7.3.tgz
tar zxvf xdip-0.7.3.tgz
cd xdip-0.7.3
gedit xdipo.h

```
Find a line that reads:
```

# include <forms.h>

```
and replace with:
```

# include </usr/include/X11/forms.h>

```
Save the change and now:
```

./configure
make
sudo make install

```

to run it type:
xdipo

(The End)

For my VDR 1.7.5 Howto [click here]("http://ubuntuforums.org/showthread.php?t=1126258")

[http://ubuntuforums.org/showthread.php?t=1126258](http://ubuntuforums.org/showthread.php?t=1126258)

---

### Post by coolercooler on 2009-03-26
Excellent tutorial, Couple of errors could have been corrected, but no big to modify. 

I do however have a question, how could this be used with 780g chipset rather than the nvidia?

Has anyone got it to work with Ati-780g, and what are the different commands?

---

### Post by art2003 on 2009-03-26
Hi,
About the errors, please point them out and I will be delighted to correct them.

As for a different chipset, well ignore point two and find some other way to get 1920x1080 screen resolution and then you can follow the rest of the tutorial without any problems.

---

### Post by coolercooler on 2009-03-27
When using this command 
```
 ffmpeg# ./configure --prefix=/usr --enable-shared --enable-gpl --enable-postproc --enable-libmp3lame --enable-libvorbis --enable-pthreads --enable-libx264 --enable-libtheora --enable-libfaac --enable-libfaad --enable-libxvid --enable-nonfree

```

I get this error```
FAAD test failed.
If you think configure made a mistake, make sure you are using the latest
version from SVN.  If the latest version fails, report the problem to the
ffmpeg-user@mplayerhq.hu mailing list or IRC #ffmpeg on irc.freenode.net.
Include the log file "config.err" produced by configure as this will help
solving the problem.
 
```


Configuring lircd remote should be after the installation of vdr since the file saving directory's are not yet created and files can't be saved.

also vdr with s2ap section when downloading obj file, then you are moving bin file, should the obj be renamed to bin or should it remain as an obj?

```
 wget http://www.linuxtv.org/pipermail/vdr/attachments/20081007/edcd3fcc/attachment-0001.obj
mv attachment-0001.bin vdr-1.7.0-s2api-07102008-h264-clean.patch.gz
```


also when I did this command ```
gedit /var/bin/runvdr
``` I could not save it so I assumme we have to create /var/bin folder first? so I did ```
 mkdir /var/bin 
```

This command ```
 cd /usr/local/src/vdr/PLUGINS/src 
``` for me was like this, as I used older vdr. ```
 cd /usr/local/src/vdr-1.7.0/PLUGINS/src 
``` 

For the remote section ```
 wget http://www.escape-edv.de/endriss/vdr...mote-0.4.0.tgz
``` should be ```
wget http://www.escape-edv.de/endriss/vdr/vdr-remote-0.4.0.tgz
```  But am still getting this error,  I don't know what to do here! ```
/usr/local/src/vdr-1.7.0/PLUGINS# make plugins
make: *** No rule to make target `plugins'. Stop.

```

is there a way to test each item after install before moving to next?  This could eliminate lots of errors at the end which am sure a going to get, when I run vdr.

Also, kind of a request, can you please make a tut in word and attach all the needed files including cccam and scripts, and upload em somewhere? Files get deleted or sites get shutdown, and becomes difficult to get hold of.

Thanks

---

### Post by art2003 on 2009-03-27
I have applied all the necessary corrections, thanks for the feedback. When I have time I will upload files to ziddu.com I have one or two there already.

Now, it seems you are doing fine just type this:

```
sudo ln -s /usr/local/src/vdr-1.7.0 /usr/local/src/vdr
```

and then

```
cd /usr/local/src/vdr
```

followed by

```
sudo make plugins
```

and

```
sudo make install
```

If you get no errors there then your plugins should be fine (at least they have compiled

(the tutorial is now amended so regardless of what version of vdr you want to install you will have the vdr directory (really a symlink to your chosen vdr)

In truth you only need to do make plugins and make install once, if you have all plugins in their place, but by doing it one by one it is easier to stop errors

ALWAYS  run make plugins from /usr/local/src/vdr 
NEVER from /usr/local/src/vdr/PLUGINS

Let me know how you get on...

---

### Post by coolercooler on 2009-03-28
OK thanks, now thats alot better.:P

Just to add if anyone has 780g chipset that you need to download latest driver from amd, the driver that comes in ubuntu 8.04, has a bug and you will get flicker on picture, thanks to a special person who helped me debug this issue. :)  You might still get a bug with new drivers and firmware, which you will have to deal with first.

now I only have couple of issues, could be bugs with my system, that need fixing, or more likely something is not right in the script.

1. When I give command to shutdown vdr-backend I get this error ```
 #/etc/init.d/vdr stop
Shutting down VDR Killed
killall: no process killed
/var/bin/runvdr: no process killed
 
```  This is a problem as my systems hangs on shutdown with that error and have to remove power to reboot.

2 I get black screen on hd channels the others work fine, but nothing on hd.


P.s that oxine looks good,\\:D/ can't wait for nxt part of the tut.

---

### Post by art2003 on 2009-03-30
Hello CoolerCooler,

Actually from oxine (assuming you run it as root or else add it to the sudoers group) you can shutdown your computer, just choose SHUTDOWN and then change the default 'close oxine' to 'shutdown computer'

What happens when from the terminal you type:

sudo halt


does that close your computer?

---

### Post by art2003 on 2009-03-30
> 
1. When I give command to shutdown vdr-backend I get this error ```
 #/etc/init.d/vdr stop
Shutting down VDR Killed
killall: no process killed
/var/bin/runvdr: no process killed
 
```  This is a problem as my systems hangs on shutdown with that error and have to remove power to reboot.

Edit /etc/init.d/vdr
and where it says killall vdr and killall runvdr
replace with halt
or with shutdown now
Then you should get what you wanted...

> 
2 I get black screen on hd channels the others work fine, but nothing on hd.

Are these FreetoAir channels you are trying? If they are not then there is a chance your card is not meant to clear them and you need to update your subscription

---

### Post by coolercooler on 2009-04-01
Hi, Art2003.

With halt I still get the same problem, system stuck, at the same level and have to keep hold of power switch to shut it down or cut power, modifying vdr script gives me the same error.  I know it must be something with the vdr script, if I however type killall vdr in the command it cuts the power to my lnb.  But if I then switch off the system still hungs at the same place.

Yes the hd channles are free to air, and I've tried changing the modulation to all the options in the vdr, but still not picture, but I do get broken sound.

On a plus side I've managed to make sound work through Hdmi, as posted here in the last post ```
 http://ubuntuforums.org/archive/index.php/t-1033620.html 
``` Here is the post ```
lglenn
February 6th, 2009, 08:37 PM
OK, I have just been through this dance as well, here are the steps that I took to get audio to work over HDMI. I hope this saves someone else a few hours!

I have a Gigabyte GA-MA78GM-S2H motherboard, BTW.

1. Installed Mythbuntu 8.10 (Ubunto 8.10)

2. Installed the proprietary ATI driver, via the Hardware Drivers control panel.

3. From the command line, ran aticonfig --initial --input=/etc/X11/xorg.conf

(** steps 2 & 3 were really just to get X windows working properly with the ATI driver, but I'm pretty sure you need to have the full-on ATI driver going to make all this work. Most probably, you've already gotten that far. **)

3. aplay -l lists audio devices:

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC883 Analog [ALC883 Analog]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC883 Digital [ALC883 Digital]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
Subdevices: 0/1
Subdevice #0: subdevice #0

...from this, you can see that determine that HDMI out will be plughw:1,3 (that is, card 1, device 3). As mentioned above, it has to be plughw, not just hw.

4. Run sudo alsamixer -c 1

5. There's no option to raise/lower volume, but you can un-mute by hitting 'm'. If you see a box at the bottom of the terminal window with 'mm' in it, you're muted. If it contains '00', you're un-muted.

6. Hit esc to quit.

7. Run aplay on a .wav file to test, like so: sudo aplay -D plughw:1,3 <soundfile>. If your device number was different, use that.

8. Assuming that all works, edit /etc/asound.conf (which may not exist yet), put this in it:

pcm.!default {
type hw
card 1
device 3
}

Again, use your device numbers. Now the 3200 HDMI is your default audio out.

The Alsa wiki page on Digital Out (http://alsa.opensrc.org/index.php/DigitalOut#MythTV) was super-helpful.
```
but that also has couple of side effects, like I can't mute sound with vdr or volume down has no effect either, also on start up there is no sound and I have to change it every time I reboot with this command. ```
sudo alsamixer -c 1
```

---

### Post by art2003 on 2009-04-08
I think you have to modify /boot/grub/menu.lst so your kernel loads with -noacpi or some other option like that as it is not 'normal' that sudo halt and sudo shutdown now 
do not work from you from the terminal (that has nothing to do with VDR or OXINE)

---

### Post by la5zl on 2009-04-11
When running #make in VDR 1.70 I get this error msg:

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
g++ -g -O2 -Wall -Woverloaded-virtual -Wno-parentheses -c -DREMOTE_KBD -DLIRC_DEVICE=\"/dev/lircd\" -DRCU_DEVICE=\"/dev/ttyS1\" -D_GNU_SOURCE -DVIDEODIR=\"/video\" -DCONFDIR=\"/video\" -DPLUGINDIR=\"./PLUGINS/lib\" -DLOCDIR=\"./locale\" -I/usr/include/freetype2 audio.c
In file included from audio.c:12:
dvbdevice.h:19:2: error: #error VDR requires Linux DVB driver API version 5.0!
In file included from audio.c:12:
dvbdevice.h:38: error: ‘fe_delivery_system’ does not name a type
make: *** [audio.o] Error 1

S2-liplianin driver installed without error msg.

Any clue
Thanks

---

### Post by art2003 on 2009-04-11
Hi, in order to try and help you can you paste here

the output of the following 5 commands:

1)
ls /dev/dvb

2)
cat /usr/local/src/vdr/Make.config |grep DVBDIR

3)
uname -r

4)
ls /usr/src/linux-headers-`uname -r`/include/linux/compiler.h 

5)
ls /usr/local/src/s2-liplianin/linux/include/linux -l

---

### Post by la5zl on 2009-04-11
1)
ls /dev/dvb

adapter0




2)
cat /usr/local/src/vdr/Make.config |grep DVBDIR


cat: /usr/local/src/vdr/Make.config: No such file or directory


3) uname -r


2.6.27-14-generic


4)
ls /usr/src/linux-headers-`uname -r`/include/linux/compiler.h

/usr/src/linux-headers-2.6.27-14-generic/include/linux/compiler.h


5)
ls /usr/local/src/s2-liplianin/linux/include/linux -l

total 112
lrwxrwxrwx 1 root root    65 2009-04-11 13:30 compiler.h -> /usr/src/linux-headers-2.6.27-14-generic/include/linux/compiler.h
drwxr-xr-x 2 root root  4096 2009-04-11 13:29 dvb
-rw-r--r-- 1 root root  5229 2009-04-11 13:29 i2c-id.h
-rw-r--r-- 1 root root  1230 2009-04-11 13:29 ivtvfb.h
-rw-r--r-- 1 root root  2675 2009-04-11 13:29 ivtv.h
-rw-r--r-- 1 root root  2544 2009-04-11 13:29 meye.h
-rw-r--r-- 1 root root  1879 2009-04-11 13:29 video_decoder.h
-rw-r--r-- 1 root root 54941 2009-04-11 13:29 videodev2.h
-rw-r--r-- 1 root root 11040 2009-04-11 13:29 videodev.h
-rw-r--r-- 1 root root  4249 2009-04-11 13:29 videotext.h

art2003 is offline   	Reply With Quote

---

### Post by la5zl on 2009-04-11
Hi..,

2)cat /usr/local/src/vdr/make.config |grep DVBDIR
DVBDIR   = /usr/local/src/s2-liplianin/linux
ifdef DVBDIR
INCLUDES += -I$(DVBDIR)/include

---

### Post by art2003 on 2009-04-11
In step 9 you missed something

try this
```

cd /usr/local/src
sudo -s
apt-get install libfreetype6-dev libfontconfig1-dev libjpeg62-dev libcap-dev libncurses5-dev libncursesw5-dev
wget ftp://ftp.cadsoft.de/vdr/Developer/vdr-1.7.0.tar.bz2
tar xivf vdr-1.7.0.tar.bz2
ln -s vdr-1.7.0 vdr
cd vdr

```
Now create Make.config as per instructions
do nothing else (no patching)
and just type
```

make

```

Does that compile?

---

### Post by la5zl on 2009-04-12
Hi..,

make:

root@msi:/usr/local/src/vdr# make
In file included from audio.c:12:
dvbdevice.h:19:2: error: #error VDR requires Linux DVB driver API version 3.3!
In file included from dvbdevice.c:10:
dvbdevice.h:19:2: error: #error VDR requires Linux DVB driver API version 3.3!
In file included from dvbosd.c:15:
dvbdevice.h:19:2: error: #error VDR requires Linux DVB driver API version 3.3!
In file included from eitscan.c:13:
dvbdevice.h:19:2: error: #error VDR requires Linux DVB driver API version 3.3!
In file included from vdr.c:45:
dvbdevice.h:19:2: error: #error VDR requires Linux DVB driver API version 3.3!
make: *** Deleting file `.dependencies'
g++ -g -O2 -Wall -Woverloaded-virtual -Wno-parentheses -c -DREMOTE_KBD -DVDR_USER=\"root\" -DLIRC_DEVICE=\"/dev/lircd\" -DRCU_DEVICE=\"/dev/ttyS1\" -D_GNU_SOURCE -DVIDEODIR=\"/media/video\" -DCONFDIR=\"/etc/vdr\" -DPLUGINDIR=\"/usr/lib/vdr/plugins\" -DLOCDIR=\"/usr/share/locale\" -I/usr/include/freetype2 -I/usr/local/src/s2-liplianin/linux/include audio.c
In file included from audio.c:12:
dvbdevice.h:19:2: error: #error VDR requires Linux DVB driver API version 3.3!
In file included from audio.c:12:
dvbdevice.h:38: error: ‘dvbfe_delsys’ does not name a type
make: *** [audio.o] Error 1

---

### Post by art2003 on 2009-04-12
Looks like  mistmatch between multiproto and S2-API

Can you follow the instructions for 1.7.4 (S2-API ready) ?

Does that work?

---

### Post by la5zl on 2009-04-12
Hi..,
Thanks - will give that a tray later,
seems others have problems too:
[http://dvbn.happysat.org/viewtopic.php?f=17&t=50423&start=120](http://dvbn.happysat.org/viewtopic.php?f=17&t=50423&start=120)

---

### Post by art2003 on 2009-04-12
In truth I am running 1.7.4 myself (had 1.7.0 working fine before)
I currently have 1.7.4 with just 2 patches; the extensions 68 patch (with just SETUP=1 in Make.config) and a little bug fix. I generally avoid plugins that require patching VDR unless they are short of essential.

---

### Post by la5zl on 2009-04-12
Hi..,

tried to compile VDR 1.7.4 without patches,
same error msg as before.

Also gave v4l-dvb a try, no joy here either..,

Channel scan works, as well as the remote control.

Thanks again!

---

### Post by art2003 on 2009-04-12
Have you installed the Multiproto drivers or the S2-API drivers?

1.7.4 uses S2-API and I got that error once when I had vdr-1.7.4 pointing to the multiproto drivers rather than the S2-API

---

### Post by la5zl on 2009-04-12
Hi..,

S2-API installed.

root@msi:/dev/dvb/adapter0# ls -l
total 0
crw-rw----+ 1 root video 212, 1 2009-04-12 18:59 demux0
crw-rw----+ 1 root video 212, 2 2009-04-12 18:59 dvr0
crw-rw----+ 1 root video 212, 0 2009-04-12 18:59 frontend0
crw-rw----+ 1 root video 212, 3 2009-04-12 18:59 net0

---

### Post by coolercooler on 2009-04-13
Hi Art2003

When downloading patches for vdr-1.7.4, this patch has changed to VDR-Extensions-Patch-70 from 68.

And when I patch this I get this error as follows, #patch -p1 < ../vdr-1.7.2_GetRecordingEvent.patch
patching file recording.h
Hunk #1 FAILED at 55.
1 out of 1 hunk FAILED -- saving rejects to file recording.h.rej

And for this  patch -p1 < ../VDR-Extensions-Patch-70/extras/vdr-1.6.0-2-ext_parentalrating-content.diff, I get no such file or directory 

Any clues please, and is that important to have?

la5zl, 

If things are still not working for you go back to start and try again, what version of ubuntu are you using?  Try 8.04, and when you install ubuntu make sure you delete the data and then format and install.

---

### Post by la5zl on 2009-04-13
Hi Coolercooler..,

Started with a fresh install of Ubuntu 9.04 RC1,
VDR 1.7.0 compiled fine.

A few problems though:

FFmpeg
./configure 
had to remove --enable-libx264 

do I need x264.git to build x264 first?

In order to install Plugin Setup do I need to
apply patch 68 to VDR ?

(tiny.h missing)

---

### Post by la5zl on 2009-04-13
Error msg installing Plugin Setup

#No rule to make target `tinystr.h', needed by `setup.o

---

### Post by coolercooler on 2009-04-13
You are fine to just remove that, thats what I do to compile ffmpeg,  also I think further on in oxine there is a problem with menus as I can't start oxine.

You don't need to patch anything since you are using vdr 1.7.0, but this time around I've gone for the 1.7.4 method and I need to apply the patch.

Also for me the remote control method didn't work so I did a different method, if it don't' work for you then let us know here, and will tell you how to do that.

---

### Post by coolercooler on 2009-04-14
Thanks for changing to vdr-2.7.5 art2003, but I still get this error on the last command of vdr. ```
 sudo cp /usr/src/linux-headers-`uname -r`/include/linux/compiler.h /usr/local/src/s2-liplianin/linux/include/linux/compiler.h 
cp: `/usr/src/linux-headers-2.6.24-23-generic/include/linux/compiler.h' and `/usr/local/src/s2-liplianin/linux/include/linux/compiler.h' are the same file
```

---

### Post by la5zl on 2009-04-14
Coolercooler..,

when running  - in /vdr

#make plugins

Plugin setup:
make[1]: Entering directory `/usr/local/src/vdr-1.7.0/PLUGINS/src/setup-0.3.1-zulu-edition'
make[1]: *** No rule to make target `tinystr.h', needed by `setup.o'.  Stop.
make[1]: Leaving directory `/usr/local/src/vdr-1.7.0/PLUGINS/src/setup-0.3.1-zulu-edition'

*** failed plugins: setup


Seems I am the only one getting this error?

Since using VDR 1.7.0 I have not applied any patches
to VDR.

---

### Post by coolercooler on 2009-04-14
Hi la5zl.

Am also having problem with that part, you can leave that bit as it's only for information from your cccam, just use the sc-trunk bit and move on to next.

I however am now on a 6th or 7th reinstall of ubuntu, the vdr does not have make uninstall file with it.

I also have problems with my display drivers, if I use the drivers provided from ubuntu, I get flicker in the picture, but if I use latest ATI ones then I loose sound and my sound hardware is not seen.

Maybe art2003 or someone else can do deb packages for us newbies.

---

### Post by art2003 on 2009-04-15
For the setup plugin you NEED to apply the extensions patch and add SETUP =1 to Make.config
If you are using 1.7.0 then the patch you apply is the 1.7.0 not the 1.7.4 just thats the only change.
But yes you can leave the setup plugin out if you don´t want the customized menus to see CCcam info and ecm.info Another lovely plugin I use is system info (which I allows to see the cpu utilization, hard drive temperature and space left, etc)

Can´t help with ATI drivers my mobo has NVIDIA and sound can be tricky, OSS_4.1.1051 works great for me, ALSA doesn´t (any version) and the latest OSS (4.1.1052 does not work so well (stops working suddenly after a few hours, not a one off thingy but rather kept happening so I had to downgrade.

As for .deb packages, if anybody has a place I could upload them to...

> **coolercooler said:**
> Hi la5zl.

Am also having problem with that part, you can leave that bit as it's only for information from your cccam, just use the sc-trunk bit and move on to next.

I however am now on a 6th or 7th reinstall of ubuntu, the vdr does not have make uninstall file with it.

I also have problems with my display drivers, if I use the drivers provided from ubuntu, I get flicker in the picture, but if I use latest ATI ones then I loose sound and my sound hardware is not seen.

Maybe art2003 or someone else can do deb packages for us newbies.

---

### Post by art2003 on 2009-04-15
They are meant to be the same file, this is just to make sure it is so, so you can safely ignore that error.

> **coolercooler said:**
> Thanks for changing to vdr-2.7.5 art2003, but I still get this error on the last command of vdr. ```
 sudo cp /usr/src/linux-headers-`uname -r`/include/linux/compiler.h /usr/local/src/s2-liplianin/linux/include/linux/compiler.h 
cp: `/usr/src/linux-headers-2.6.24-23-generic/include/linux/compiler.h' and `/usr/local/src/s2-liplianin/linux/include/linux/compiler.h' are the same file
```

---

### Post by ltrinh on 2009-04-15
Great tutorial  Art2003,

My setup is somewhat similar to yours in that I am also using a dual core AMD processor and have an nvidia chipset on my asus A8NSLI32 motherboard.  However, the thing that is different for me is the DVB-S card.  I am using a technisat skystar2.  It is non-HD.  I know it is working with Ubuntu 8.10 because I am able to view the free channels from Dishnetwork through Kaffeine.  

This is by far the most thorough tutorial related to this topic that I have been able to find so far.

Will this guide work for me?  And if so, which parts of it do I need to skip or add to get this to work?  I've tried to go through most of it already on my setup and at some point I started to get make errors with the softcam sc stuff.  I'm wondering if it has to do with the fact that I compiled the S2-API stuff even though I don't have an HD DVB-S card.  I plan on starting over with a fresh Ubuntu install.

Any feedback would be greatly appreciated.

---

### Post by art2003 on 2009-04-15
Thanks, I have put lots of time and effort into this tutorial and as you said other tutorials cover a bit less.
I would suggest you start with a fresh ubuntu install, get to the point where kaffeine works with free channels and ignore completely the section about the driver and firmware, that is only relevant to the specific card I am using and may indeed be interfering with your setup. The rest should be helpful but for the US you need evocam instead of CCcam, I believe.

Since you don´t need HD it might be easier for you to get the script x-vdr and install VDR 1.6 (stable)

> **ltrinh said:**
> Great tutorial  Art2003,

My setup is somewhat similar to yours in that I am also using a dual core AMD processor and have an nvidia chipset on my asus A8NSLI32 motherboard.  However, the thing that is different for me is the DVB-S card.  I am using a technisat skystar2.  It is non-HD.  I know it is working with Ubuntu 8.10 because I am able to view the free channels from Dishnetwork through Kaffeine.  

This is by far the most thorough tutorial related to this topic that I have been able to find so far.

Will this guide work for me?  And if so, which parts of it do I need to skip or add to get this to work?  I've tried to go through most of it already on my setup and at some point I started to get make errors with the softcam sc stuff.  I'm wondering if it has to do with the fact that I compiled the S2-API stuff even though I don't have an HD DVB-S card.  I plan on starting over with a fresh Ubuntu install.

Any feedback would be greatly appreciated.

---

### Post by coolercooler on 2009-04-16
> **art2003 said:**
> They are meant to be the same file, this is just to make sure it is so, so you can safely ignore that error.

Thanks for clearing that up, and keeping on top of the changes.

Can you please have a look at this error, what is the cause of this error?  Is it ffmpeg or vdr problem?  This is only on one of the hd channels that works for short time before vdr stops with error, all the other hd's I get no signal, even then I sometimes get no sginal on this as well as broken picture and sound just keeps breaking up. ```
[h264 @ 0x8642120]concealing 0 DC, 0 AC, 0 MV errors
[h264 @ 0x8642120]Reference 2 >= 2
[h264 @ 0x8642120]error while decoding MB 42 20, bytestream (24678)
[h264 @ 0x8642120]concealing 1447 DC, 1447 AC, 1447 MV errors
[h264 @ 0x8642120]error while decoding MB 43 32, bytestream (-9)
[h264 @ 0x8642120]concealing 366 DC, 366 AC, 366 MV errors
[h264 @ 0x8642120]concealing 1389 DC, 1389 AC, 1389 MV errors
[h264 @ 0x8642120]left block unavailable for requested intra mode at 0 26
[h264 @ 0x8642120]error while decoding MB 0 26, bytestream (30435)
[h264 @ 0x8642120]left block unavailable for requested intra4x4 mode -1 at 0 52
[h264 @ 0x8642120]error while decoding MB 0 52, bytestream (1442)
[h264 @ 0x8642120]concealing 1718 DC, 1718 AC, 1718 MV errors
[h264 @ 0x8642120]top block unavailable for requested intra mode at 73 12
[h264 @ 0x8642120]error while decoding MB 73 12, bytestream (19427)
Segmentation fault
 
```

All the rest of the channels work fine.

Thanks

---

### Post by art2003 on 2009-04-16
Hi coolercooler

It looks like a vdr error there but you should check /var/vdr and /var/logs/

Bear in mind that in 1.7.0 the HD implementation is not complete
I would suggest you give 1.7.5, it runs very nicely and even Klaus (the vdr author) uses it instead of 1.7.0

---

### Post by steefjeqv on 2009-04-21
> **art2003 said:**
> For the setup plugin you NEED to apply the extensions patch and add SETUP =1 to Make.config
If you are using 1.7.0 then the patch you apply is the 1.7.0 not the 1.7.4 just thats the only change.
But yes you can leave the setup plugin out if you don´t want the customized menus to see CCcam info and ecm.info Another lovely plugin I use is system info (which I allows to see the cpu utilization, hard drive temperature and space left, etc)

Can´t help with ATI drivers my mobo has NVIDIA and sound can be tricky, OSS_4.1.1051 works great for me, ALSA doesn´t (any version) and the latest OSS (4.1.1052 does not work so well (stops working suddenly after a few hours, not a one off thingy but rather kept happening so I had to downgrade.

As for .deb packages, if anybody has a place I could upload them to...

Hi,

If you prefer deb packages :

[COLOR="black"][COLOR="Red"]Option 1 (doesn't work at the moment!) If any one can help please do - Unmet build dependencies: dvb-s2api-liplianin-headers | linux-libc-dev (>= 2.6.29) :[/COLOR][/COLOR]

Use e-tobi's sources for debian lenny. You can build them from source (thanks to Tomg + Tobi).

sudo gedit /etc/apt/sources.list

Add this line to your sources.list :

deb-src  [http://e-tobi.net/vdrdevel-experimental](http://e-tobi.net/vdrdevel-experimental) lenny vdr-multipatch

Then type in terminal :

sudo gedit /etc/apt/preferences

And add the following to this file (which is blank) :

# /etc/apt/preferences
Package: *
Pin: release o=e-tobi.net
Pin-Priority: 1001

You'll need the s2api DVB driver to (as art2003 describes in this howto).

It's time to build your deb package :

sudo apt-get update

cd /usr/local/src

sudo apt-get source vdr 

cd vdr-1.7.5

sudo apt-get build-dep vdr

sudo PATCHVARIANT=multipatch dpkg-buildpackage -tc -uc -us -rfakeroot

That's it.


To build a plugin (example):

sudo apt-get build-dep vdr-plugin-live=0.2.0-4

sudo PATCHVARIANT=multipatch apt-get source -b vdr-plugin-live=0.2.0-4 

cd vdr-plugin-live=0.2.0-4

sudo PATCHVARIANT=multipatch dpkg-buildpackage -tc -uc -us -rfakeroot

You should have a deb.



Option 2

det from FreeVDR has made his own packages for Ubuntu 8.10 :

[http://www.freevdr.de/download/index.php?dir=ubuntu/]("http://www.freevdr.de/download/index.php?dir=ubuntu/")

Greetings,
Steven

---

