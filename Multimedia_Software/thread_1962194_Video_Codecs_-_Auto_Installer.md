---
title: "Video Codecs - Auto Installer"
date: 2012-04-20
forum: Multimedia Software
---

### Post by for.i.am.root on 2012-04-20
Seeing a lot of posts on this topic. Thought I might be able to help with an auto installer.

Hopefully none of the code is a violation of the forum rules.

Some code borrowed from FakeOutdoorsman here:
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

Copy code.
Paste into gedit.
Save somewhere.
Right Click - Mark as executable.
Double Click.
Run in Terminal.

This also installs VirtualBox as well as a ton of other not needed stuff for most people. You should remove what you aren't going to use to help with security / system resources.

It's good practice to read ALL CODE before you run it.

```

#! /bin/bash
# As of 19-APR-2012 this script works to download and install just about every codec needed for video as well as a bunch of extra stuff I use.
# This script was written for lucid (10.04), however, as long as the package names/versions didn't change it will work for newer systems.
# For troubleshooting tips / issues drop me a line.
#
# for.i.am.root
#
# Install lsb to get rid of the stupid no modules error
sudo apt-get -y update && sudo apt-get -y install lsb
# Backup sources.list
sudo mv /etc/apt/sources.list /etc/apt/sources.list.backup
# Get the codename of the current version
varcode=`lsb_release -a | grep Codename | sed 's/Codename://' | sed -e 's/^[ \t]*//'`
# Add medibuntu / multivers / universe / restricted / virtualbox
sudo cat << EOF >> /etc/apt/sources.list
# Comment below to disable restricted
deb http://us.archive.ubuntu.com/ubuntu/ $varcode main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ $varcode main restricted
deb http://us.archive.ubuntu.com/ubuntu/ $varcode-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ $varcode-updates main restricted
# Comment below to disable univrese
deb http://us.archive.ubuntu.com/ubuntu/ $varcode universe
deb-src http://us.archive.ubuntu.com/ubuntu/ $varcode universe
deb http://us.archive.ubuntu.com/ubuntu/ $varcode-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ $varcode-updates universe
# Comment below to disable multiverse
deb http://us.archive.ubuntu.com/ubuntu/ $varcode multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ $varcode multiverse
deb http://us.archive.ubuntu.com/ubuntu/ $varcode-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ $varcode-updates multiverse
# medibuntu is needed for this script
deb http://packages.medibuntu.org/ $varcode free non-free
deb-src http://packages.medibuntu.org/ $varcode free non-free
# Comment below to disable Virtualbox repo
deb http://download.virtualbox.org/virtualbox/debian $varcode contrib non-free
EOF
# Add PS3MediaServer
sudo add-apt-repository ppa:happy-neko/ps3mediaserver
# Add Virtualbox
cd && wget -q http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc -O- | sudo apt-key add -
# This line merges the two sources files
# You will end up with a bunch doubles in source.list
# After the second run of update it will fix itself
# But you will still have doubles in your /etc/apt/sources.list
# They will just be ignored
sudo cat /etc/apt/sources.list.backup >> /etc/apt/sources.list
# Update and install keyring
sudo apt-get -y update
sudo apt-get -y update
sudo apt-get -y --allow-unauthenticated install medibuntu-keyring
sudo apt-get -y update
sudo apt-get -y install libx11-dev libogg-dev libfaac-dev libvdpau-dev libsdl1.2-dev libvorbis-dev libxfixes-dev libtheora-dev libvorbis-dev libxvidcore-dev libjack0 libopencore-amrnb-dev libopencore-amrwb-dev libxvidcore4 build-essential checkinstall doxygen git-core lynx nasm subversion texi2html wget zlib1g-dev libgtk2.0-dev
# Depending on your system one of these will work. The other will fail
sudo apt-get -y install w64codecs
sudo apt-get -y install w32codecs
# Get ready for the new stuff
sudo apt-get -y remove ffmpeg x264 libx264-dev libmp3lame-dev libvpx-dev
# Install yasm ubuntu 10.04 uses 0.8 need >1.0
cd && wget http://www.tortall.net/projects/yasm/releases/yasm-1.2.0.tar.gz && tar -zxvf ./yasm-1.2.0.tar.gz && cd ./yasm-1.2.0 && ./configure && make && checkinstall --pkgname=yasm --pkgversion=1.2.0 --backup=no --deldoc=yes --fstrans=no --default && cd
# Make sure the installation was successful
if [ $? -ne 0 ]
then
echo "error yasm"
exit 1
else
sudo rm -frv ./yasm-1.2.0
fi
# Install x264
cd && git clone git://git.videolan.org/x264 && cd x264 && ./configure --enable-static && make && sudo checkinstall --pkgname=x264 --pkgversion="3:$(./#version.sh | awk -F'[" "]' '/POINT/{print $4"+git"$5}')" --backup=no --deldoc=yes --fstrans=no --default && cd
# Make sure the installation was successful
if [ $? -ne 0 ]
then
echo "error x264"
exit 1
fi
# Install lame
cd && wget http://downloads.sourceforge.net/project/lame/lame/3.99/lame-3.99.5.tar.gz && tar xzvf lame-3.99.5.tar.gz && cd ./lame-3.99.5 && sudo ./configure --enable-nasm --disable-shared && sudo make && sudo checkinstall --pkgname=lame-ffmpeg --pkgversion="3.99.5" --backup=no --deldoc=yes --install=yes --fstrans=no --default && cd
# Make sure the installation was successful
if [ $? -ne 0 ]
then
echo "error lame-ffmpeg"
exit 1
else
sudo rm -frv ./lame-3.99.5
fi
# Install opencore amr
cd && wget http://downloads.sourceforge.net/project/opencore-amr/opencore-amr/opencore-amr-0.1.3.tar.gz && tar -zxvf opencore-amr-0.1.3.tar.gz && cd ./opencore-amr-0.1.3 && sudo ./configure --disable-shared && sudo make && sudo checkinstall --pkgname="libopencore-amr" --pkgversion="0.1.3" --backup=no --fstrans=no --install=yes --default && cd
# Make sure the installation was successful
if [ $? -ne 0 ]
then
echo "error opencore"
exit 1
else
sudo rm -frv ./opencore-amr-0.1.3
fi
# Install theora
cd && wget http://downloads.xiph.org/releases/theora/libtheora-1.1.1.tar.gz && tar xzvf libtheora-1.1.1.tar.gz && cd ./libtheora-1.1.1 && sudo ./configure --disable-shared && sudo make && sudo checkinstall --pkgname=libtheora --pkgversion "1.1.1" --backup=no --fstrans=no --install=yes --default && cd
# Make sure the installation was successful
if [ $? -ne 0 ]
then
echo "error theora"
exit 1
else
sudo rm -frv ./libtheora-1.1.1
fi
# Install libvpx-dev
cd && git clone http://git.chromium.org/webm/libvpx.git && cd ./libvpx && ./configure && make && sudo checkinstall --pkgname=libvpx --pkgversion="1:$(date +%Y%m%d%H%M)-git" --backup=no --deldoc=yes --fstrans=no --default && cd
# Make sure the installation was successful
if [ $? -ne 0 ]
then
echo "error libvpx"
exit 1
else
sudo rm -frv ./libvpx
fi
# Install ffmpeg
cd && git clone --depth 1 git://source.ffmpeg.org/ffmpeg && cd ffmpeg && ./configure --enable-libvpx --enable-gpl --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libx264 --enable-nonfree --enable-version3 --enable-x11grab --enable-version3 --enable-postproc --enable-libxvid && make && sudo checkinstall --pkgname=ffmpeg --pkgversion="5:$(date +%Y%m%d%H%M)-git" --backup=no --deldoc=yes --fstrans=no --default && cd
# Make sure the installation was successful
if [ $? -ne 0 ]
then
echo "error ffmpeg"
exit 1
fi
# Install qt-faststart
cd ~/ffmpeg && make tools/qt-faststart && sudo checkinstall --pkgname=qt-faststart --pkgversion="$(date +%Y%m%d%H%M)-git" --backup=no --deldoc=yes --fstrans=no --default install -Dm755 tools/qt-faststart /usr/local/bin/qt-faststart && cd
# Make sure the installation was successful
if [ $? -ne 0 ]
then
echo "error faststart"
exit 1
fi
# re-install x264
cd ~/x264 && make distclean && ./configure --enable-static && make && sudo checkinstall --pkgname=x264 --pkgversion="3:$(./version.sh | awk -F'[" "]' '/POINT/{print $4"+git"$5}')" --backup=no --deldoc=yes --fstrans=no --default && cd
# Make sure the installation was successful
if [ $? -ne 0 ]
then
echo "error x264"
exit 1
else
sudo rm -frv ./x264
sudo rm -frv ./ffmpeg
fi
# Make sure nothing gets replaced
hash x264 ffmpeg ffplay
echo "ffmpeg hold" | sudo dpkg --set-selections
echo "x264 hold" | sudo dpkg --set-selections
echo "lame-ffmpeg hold" | sudo dpkg --set-selections
echo "libopencore-amr hold" | sudo dpkg --set-selections
echo "libtheora hold" | sudo dpkg --set-selections
# Update and install the good stuff
# This is all the stuff that I use on my rigs and that I like having enabled
# A lot to dig through, but you should only install what you need / use
sudo apt-get -y install ubuntu-restricted-extras mencoder mplayer vlc arista avidemux gettext debian-keyring konqueror-nsplugins msttcorefonts ttf-xfree86-nonfree xfs g++-multilib g++-4.3-multilib gcc-4.3-doc libstdc++6-4.3-dbg git-doc git-arch git-cvs git-svn git-email git-daemon-run git-gui gitk gitweb equivs libasound2-doc nas debhelper fakeroot libfftw3-dev libggi-target-emu libggi-target-monotext libggimisc2 jackd liblrdf0-dev libqt4-dev sidplay-base xsidplay libstdc++6-4.3-doc lynx-cur-wrapper mplayer-doc ladspa-sdk diff-doc subversion-tools db4.6-util latex2html libmyodbc odbc-postgresql mozilla-plugin-vlc videolan-doc cryptsetup k3b gparted devede linux-generic linux-headers-generic linux-image-generic compiz compiz-plugins compiz-gnome compiz-core emerald compiz-fusion-plugins-main compiz-fusion-plugins-extra fusion-icon compizconfig-settings-manager msttcorefonts reiser4progs libdvdcss2 openssh-server ssh wine vsftpd unixodbc debconf java-common locales gsfonts-x11 flashplugin-nonfree dkms ps3mediaserver libwxbase2.8-dev libcurl4-gnutls-dev liblua5.1-curl-dev ubufox transmission-cli libcurl3 libcurl3-gnutls lm-sensors stress pi rcconf computertemp sensors-applet tightvncserver acpidump gimp
# Install sun-java6-jre
cd && wget http://mirror.pnl.gov/ubuntu//pool/multiverse/s/sun-java6/sun-java6-bin_6.24-1build0.8.04.1_amd64.deb && dpkg -i ./sun-java6-bin_6.24-1build0.8.04.1_amd64.deb
# Make sure the installation was successful
if [ $? -ne 0 ]
then
echo "error sun-java6-bin"
exit 1
else
sudo rm ./sun-java6-bin_6.24-1build0.8.04.1_amd64.deb
fi
cd && wget http://mirror.pnl.gov/ubuntu//pool/multiverse/s/sun-java6/sun-java6-jre_6.24-1build0.8.04.1_all.deb && dpkg -i sun-java6-jre_6.24-1build0.8.04.1_all.deb
# Make sure the installation was successful
if [ $? -ne 0 ]
then
echo "error sun-java6-jre"
exit 1
else
sudo rm ./sun-java6-jre_6.24-1build0.8.04.1_all.deb
fi
# Install VirtualBox
sudo apt-get -y install virtualbox-4.1
cd && wget http://download.virtualbox.org/virtualbox/4.1.12/Oracle_VM_VirtualBox_Extension_Pack-4.1.12-77245.vbox-extpack
# Final update and clean up
sudo apt-get -y update && sudo apt-get -y upgrade && sudo apt-get -y clean && sudo apt-get -y autoremove
# Update boot files/images
sudo update-initramfs -u ALL && sudo update-grub

```

---

