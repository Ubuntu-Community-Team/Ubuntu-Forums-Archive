---
title: "Ubuntu Muncrief RealPlayer Package - Instructions"
date: 2007-04-25
forum: Multimedia &amp; Video
---

### Post by muncrief on 2007-04-25
[B]~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Ubuntu Muncrief RealPlayer Package - Instructions
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~[/B]

While open source alternatives exist for the viewing of Real Media in mozilla/firefox browsers they don't implement fast forward/rewind/pause/play stream controls. Since open source Windows Media and Quicktime alternatives also lack this functionality many Ubuntu users are limited to Flash multimedia unless they wish to start a media stream from the beginning and view it to the end. However, using the official RealPlayer plugin provides Ubuntu users with the ability to view both Flash and Real Media with full stream controls, and use open source alternatives for viewing Windows Media and Quicktime without stream controls. The only disadvantage to the RealPlayer plugin is that it usually can't play fullscreen video, while the MPlayer open source plugin can.

Unfortunately though, a substantial number of Ubuntu/Ubuntu derivative users haven't been able to use the official RealPlayer plugin to view Real Media because of jerky/corrupted video playback and/or conflict with win32codecs. The following guide provides instructions on how to create a script that allows an alternative Ubuntu RealPlayer package to be built that may allow these users to enjoy the fully functional RealPlayer multimedia browser plugin alongside open source codecs and programs. Installation instructions and tips are also included at the end of this instruction.

Note: For commands that must be run with root privileges the examples use "sudo". This is fine for most Ubuntu users. However, for some derivative users "su" must be used to switch to super user mode before executing the commands, without "sudo" of course.

1. Create Package Build Script
~~~~~~~~~~~~~~~~~~

cd

For Gnome users:
**sudo gedit build-muncrief-realplayer**

For KDE users:
**sudo kwrite build-muncrief-realplayer**

Copy the script from the following "Ubuntu Muncrief RealPlayer Package - Script" post into this file.

Now save the file and make it executable:
**sudo chmod a+x build-muncrief-realplayer**


2. Install Dependencies and Download Alternative RealPlayer RPM
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Note: If you can't download the RealPlayer version specified in these instructions then browse to the Suse i586 directory to find the new RealPlayer version and adjust the instructions accordingly. However, it would be wise to save the version stated in these instructions if it's available because future versions may not work.

**sudo apt-get install alien alsa-oss**
**wget [http://download.opensuse.org/distribution/10.2/repo/non-oss/suse/i586/RealPlayer-10.0.8-33.i586.rpm](http://download.opensuse.org/distribution/10.2/repo/non-oss/suse/i586/RealPlayer-10.0.8-33.i586.rpm)**


3. Creating, Installing, and Uninstalling the RealPlayer Package
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

_Package Creation_
The script creates the RealPlayer package and usually requires no user interaction. It outputs the name of the created package and places it in the current directory if successful. The package extension will always be ".muncrief.deb".

**sudo ./build-muncrief-realplayer RealPlayer-10.0.8-33.i586.rpm**

_Package Installation_
**sudo dpkg -i realplayer_10.0.8-33_i386.muncrief.deb**

_Package Uninstallation_
**sudo dpkg -r realplayer**


4. Compatibility and Performance
~~~~~~~~~~~~~~~~~~~~
This final section contains information on how to make MPlayer compatible with the RealPlayer plugin, and addresses some ways to remedy common problems when using media players in general. You will have to experiment to decide which open source media player plugin works best for you - MPlayer, Totem-Xine, or Totem-Gstreamer (the VLC plugin is not recognized by most multimedia sites). It has been my experience that MPlayer and Totem-Xine appear to play more types of Windows Media, while Totem-Gstreamer appears to play more types of Quicktime media.

Note that with the exception of disabling IPV6 and setting up MPlayer (if you use it) to not conflict with RealPlayer, you shouldn't change anything else in your multimedia system unless you're having problems. The old adage "If it ain't broke don't fix it" is quite apropos here.


_Disable IPV6 for faster and more reliable connections_
IPV6 is a newer internet protocol with security, and hopefully in the future performance, benefits over the older and more widely use IPV4 protocol. However, at this time it more often than not causes connectivity and performance degradation because of its sparse support. It is one of the major reasons that MPlayer, and to a lesser degree Totem, sometimes have difficulty connecting to video streams.

There are two ways to disable IPV6. One is to disable it for Firefox only, and the other is to disable it system wide. However, depending upon your distribution, IPV6 may not be enabled at all, and if it is disabling it system wide may cause other networking problems. However, disabling it in Firefox is always safe, so it is recommended you try this as a minimum. It's up to you if you want to try the system wide change. I wouldn't do it unless you have problems with applications other than Firefox and its plugins connecting to the Internet.

Disable Firefox IPV6:
1. Open Firefox and type about:config.
2. Type "ipv6" in the "Filter" box.
3. You will see an option to disable ipv6. Click on it to set the value to true.
4. Close and restart all Firefox browsers.


Disable IPV6 System Wide:
There are actually many ways to do this, but the following two are the easiest and most compatible I have found. You should try Method A first. The first thing is to see if IPV6 is running at all though.

Check if IPV6 is running:

**ip a | grep inet6**

If there is any output from this command then IPV6 is running. If there isn't any output then don't continue, there's nothing to disable.


IPV6 Disable Method A -

For Gnome users:
**sudo gedit /etc/modprobe.d/bad_list**

For KDE users:
**sudo kwrite /etc/modprobe.d/bad_list**

Add this line to the file:

alias net-pf-10 off

Save the file and exit, and reboot. Check if IPV6 is running after reboot. Remove the line from bad_list and try Method B if it is.


IPV6 Disable Method B -

For Gnome users:
**sudo gedit /etc/modprobe.d/aliases**

For KDE users:
**sudo kwrite /etc/modprobe.d/aliases**

Change this line in the file:

"alias net-pf-10 ipv6" To "alias net-pf-10 off ipv6"

Save the file and exit, and reboot. Check if IPV6 is running after reboot. If it is you will have to look for other solutions beyond the scope of this instruction.


_For MPlayer users - Change plugin configuration for compatibility and better performance_
MPlayer plugin settings may be changed by right clicking over any video MPlayer is playing in a browser and changing them via the pop up menu. For compatibility with the RealPlayer plugin you must disable MPlayers Real Media support. 

1. Go to any site that plays Windows Media, cnn.com is a good one to start with.
2. Start playing any video on the site.
3. Right click over the Mplayer video window, even if the video doesn't start. A settings menu will pop up.
4. Uncheck "Enable RealMedia Support" and "Enable Helix Emulation". Make sure "Enable SMIL Support" is checked. Note that when using a normal RealPlayer package you would actually need to uncheck this option, which is one of the things that in the past has caused incompatibility between MPlayer and RealPlayer.
5. Close the pop up menu and restart the video to see if it will play. If it won't try the following steps, otherwise stop now.

6. Right click over the Mplayer video window and open the settings menu again.
7. Set "Video Output:" to "X11", "Audio Output:" to "alsa", and "Minimum Cache Size" to 1024 or greater (anything over 2048 probably won't help though).
8. Close the pop up menu and restart the video to see if it will play. If it won't try the following steps, otherwise stop now.

9. Right click over the Mplayer video window and open the settings menu again.
10. Check "Connect to RTSP Media over TCP".
11. Close the pop up menu and restart the video to see if it will play. If it won't you will have to look for other solutions beyond the scope of this instruction.

_For Totem-Gstreamer users - Hidden Gstreamer Settings_
There are actually extra Gstreamer settings that don't appear in the Totem GUI that can sometimes be used to remedy Gstreamer problems. Just open a terminal and type:

1. **gstreamer-properties**
2. A GUI will pop up that allows you to change Gstreamer Audio and Video settings. Going to the "Video" tab and changing the "Default Output" "Plugin:" to "X Window System (no XV)" will solve most problems. If it doesn't you will have to look for other solutions beyond the scope of this instruction.


_For Totem-Xine users_
I haven't really found anything to adjust Totem-Xine beyond the basic GUI settings. If anyone knows of any other settings please let me know and I'll add it to this instruction.


_Green flickering or other weird artifacts in RealPlayer video_

1. Open RealPlayer
2. Go to Tools->Preferences->Hardware
3. Uncheck "Use XVideo".
4. Click OK, close RealPlayer and everything should be fine.

Note that since this setting is easy to change, you should only uncheck it when necessary, and change it back to checked under normal circumstances since XV provides higher quality video.

---

### Post by muncrief on 2007-04-25
#!/bin/bash
#
# Alternate Muncrief RealPlayer Package Build Script for Ubuntu Systems
# Author: Mitch Muncrief
# V1.0
#
# Usage: build-muncrief-realplayer filename.rpm
#
E_NOTROOT=65					# Set exit status values
E_BADARGS=66
E_NOEXIST=67
E_DIREXIST=68
E_PKGEXIST=69
E_PKGMOVEFAIL=70
E_DEBPARSE=71
E_RAWFAIL=72
E_RAWPARSE=73
E_RAWEXTRACTFAIL=74
E_PKGFAIL=75
EXITSTAT=0

# ~~~~~~~~~
# Functions
# ~~~~~~~~~
function err_exit				# Exit with error status and usage message
{
  echo "Muncrief RealPlayer Package Build Script Failed."
  exit $EXITSTAT
}

function err_usage_exit				# Exit with error status and usage message
{
  echo "Usage (run with root privileges): `basename $0` filename.rpm"
  err_exit
}

function err_clean_exit				# Remove build dir and do error exit
{
  rm -r muncrief-realplayer-build
  err_exit
}

function ok_exit				# Remove build dir and exit with OK status
{
  rm -r muncrief-realplayer-build
  echo "Muncrief RealPlayer Package Build Script Succeeded - Package name: '$DEB_FILENAME'."
  exit $EXITSTAT
}

# ~~~~
# Main
# ~~~~
echo ""						# Sign on message
echo "Muncrief RealPlayer Package Builder for Ubuntu Systems V1.0"
echo ""

if [ `id -nu` != "root" ]; then			# Make sure we have root privileges
  echo "ERROR: This script must be run with root privileges (sudo or su)"
  EXITSTAT=$E_NOTROOT
  err_usage_exit  
fi

#
# Check for Valid Arguments
# -------------------------
if [ ! -n "$1" ] || [ -n "$2" ]; then		# Make sure we only have 1 argument
  echo "ERROR: Wrong number of arguments"
  EXITSTAT=$E_BADARGS
  err_usage_exit  
fi  

BASE_DIR=`dirname $1`				# Get the directory from the argument
RPM_FILENAME=`basename $1`			# Get the file name without the directory
RPM_FILEBASE=${RPM_FILENAME%.*}			# Get the file name without the extension
RPM_FILEEXT=${RPM_FILENAME:(-4)}		# Get the file extension
						# Make sure we have an RPM file argument
if [ "$RPM_FILEEXT" != ".rpm" ] && [ "$RPM_FILEEXT" != ".RPM" ]; then
  echo "ERROR: Argument is not an RPM file"
  EXITSTAT=$E_BADARGS
  err_usage_exit  
fi

if [ ! -e "$1" ]; then				# Make sure the RPM file exists
  echo "ERROR: RPM file doesn't exist"
  EXITSTAT=$E_NOEXIST
  err_exit  
fi

#
# Create Temporary Build Directory
# --------------------------------
if [ -e "muncrief-realplayer-build" ]; then	# Check for an existing build directory
						# Offer to delete it if it exists
  echo "A previous muncrief-realplayer-build directory exists. If you continue it will be deleted."
  echo -n "Would you like to continue? (Y/n): "
  read INP_STR
						# Exit if the user doesn't want it deleted
  if [ "$INP_STR" != "" ] && [ "$INP_STR" != "y" ] && [ "$INP_STR" != "Y" ]; then
    echo "ERROR: Build directory muncrief-realplayer-build already exists. Please move or delete the directory."
    EXITSTAT=$E_DIREXIST
    err_exit  
  fi

  if [ -d "muncrief-realplayer-build" ]; then	# If it's a directory
	rm -r muncrief-realplayer-build		# Delete directory
  else						# If it's a file
	rm muncrief-realplayer-build		# Delete file
  fi
fi

mkdir muncrief-realplayer-build			# Create build directory
cp $1 muncrief-realplayer-build			# Copy RPM to it
cd muncrief-realplayer-build			# Change to build directory

#
# Build Raw Debian Package
# ------------------------
echo "Converting RPM to raw debian RealPlayer package (this can take a few minutes) ..."
						
# Use alien to create raw package and save return string
INP_STR=`alien --to-deb --scripts --keep-version $1`
if [ "$?" != "0" ]; then			# If alien failed clean up and exit with bad status
    EXITSTAT=$E_RAWFAIL
    echo "ERROR: Alien raw package build failed."
    err_clean_exit  
fi
						# We need to get debian file name from return string
TMP_INT=`expr index "$INP_STR" " "`		# Find first space in return string
DEB_FILERAW=${INP_STR:0:TMP_INT-1}		# Get the filename before it
if [ ! -e "$DEB_FILERAW" ]; then		# If we screwed up apologize, clean up and exit
  echo "ERROR: Internal script failure, couldn't parse raw debian package name."
  echo "       Please report this error where you received this script and I will fix it ASAP. Sorry for the inconvenience."
  EXITSTAT=$E_RAWPARSE
  err_clean_exit  
fi

DEB_FILENAME="${DEB_FILERAW%.*}.muncrief.deb"	# Create Muncrief RealPlayer package name
if [ -e "../$DEB_FILENAME" ]; then		# Check for an existing package
						# Offer to move it if it exists
  echo "A previous $DEB_FILENAME package already exists. If you continue it will be moved."
  echo -n "Would you like to continue? (Y/n): "
  read INP_STR
						# Exit if the user doesn't want it moved
  if [ "$INP_STR" != "" ] && [ "$INP_STR" != "y" ] && [ "$INP_STR" != "Y" ]; then
    echo "ERROR: $DEB_FILENAME package already exists. Package creation aborted."
    EXITSTAT=$E_PKGEXIST
    err_exit  
  fi
						# Get name to move existing package to
  echo -n "Please enter a new name for the existing package: "
  read INP_STR
  mv "../$DEB_FILENAME" "../$INP_STR" 		# Move the package
  if [ "$?" != "0" ]; then			# If move failed clean up and exit with bad status
    EXITSTAT=$E_PKGMOVEFAIL
    echo "ERROR: Couldn't move existing $DEB_FILENAME package."
    err_clean_exit  
  fi
fi


#
# Build Ubuntu Debian Package
# ---------------------------
echo "Extracting raw debian RealPlayer package ..."
mkdir pkg
dpkg -x "$DEB_FILERAW" pkg
if [ "$?" != "0" ]; then			# If data extraction failed clean up and exit with bad status
    EXITSTAT=$E_RAWEXTRACTFAIL
    echo "ERROR: Raw package data extraction failed."
    err_clean_exit  
fi
dpkg -e "$DEB_FILERAW" pkg/DEBIAN
if [ "$?" != "0" ]; then			# If control extraction failed clean up and exit with bad status
    EXITSTAT=$E_RAWEXTRACTFAIL
    echo "ERROR: Raw package control extraction failed."
    err_clean_exit  
fi
						# Move everything around so it will work with Ubuntu
echo "Converting raw debian RealPlayer package data structure to Ubuntu format ..."
cd pkg/DEBIAN/
mv conffiles conffiles.orig
sed -e 's:/etc/opt/kde3/share:/usr/share:g' conffiles.orig > conffiles
rm conffiles.orig
mv conffiles conffiles.orig
sed -e '/\/usr\/share\/mimelnk\/application\/vnd.rn-realmedia.desktop/d' conffiles.orig > conffiles
rm conffiles.orig
mv conffiles conffiles.orig
sed -e '/\/usr\/share\/mimelnk\/video\/vnd.rn-realvideo.desktop/d' conffiles.orig > conffiles
rm conffiles.orig
mv conffiles conffiles.orig
sed -e '/\/usr\/share\/mimelnk\/audio\/x-pn-realaudio.desktop/d' conffiles.orig > conffiles
rm conffiles.orig
mv conffiles conffiles.orig
sed -e '/\/usr\/share\/mimelnk\/audio\/vnd.rn-realaudio.desktop/d' conffiles.orig > conffiles
rm conffiles.orig
mv md5sums md5sums.orig
sed -e 's:opt/gnome/share:usr/share:g' md5sums.orig > md5sums
rm md5sums.orig
mv md5sums md5sums.orig
sed -e 's:opt/kde3/share:usr/share:g' md5sums.orig > md5sums
rm md5sums.orig
mv preinst preinst.orig
sed -e 's:opt/gnome2/share:usr/share:g' preinst.orig > preinst
rm preinst.orig
chmod a+x preinst
cd ..
mv etc/opt/kde3/share/icons usr/share
mv etc/opt/kde3/share/mimelnk usr/share
rm usr/share/mimelnk/application/vnd.rn-realmedia.desktop
rm usr/share/mimelnk/video/vnd.rn-realvideo.desktop
rm usr/share/mimelnk/audio/x-pn-realaudio.desktop
rm usr/share/mimelnk/audio/vnd.rn-realaudio.desktop
mv opt/gnome/share/application-registry usr/share
mv opt/gnome/share/icons/hicolor usr/share/icons
mv opt/gnome/share/mime-info usr/share
mv opt/kde3/share/applications/kde usr/share/applications
rm -r etc
rm -r opt
mkdir usr/lib/mozilla
mv usr/lib/browser-plugins usr/lib/mozilla/plugins
mkdir usr/lib/firefox
mkdir usr/lib/firefox/plugins
cd usr/lib/firefox/plugins
ln -s ../../mozilla/plugins/nphelix.so .
ln -s ../../mozilla/plugins/nphelix.xpt .
cd ../../../../../
						# Create final Ubuntu package
echo "Creating Muncrief RealPlayer package (this can take a few minutes) ..."
INP_STR=`dpkg-deb -b pkg "$DEB_FILENAME"`
TMP_INT="$?"					# Save build exit status
cd ../						# Go back to head directory
if [ "$TMP_INT" != "0" ]; then			# If package creation failed clean up and exit with bad status
    EXITSTAT=$E_PKGFAIL
    echo "ERROR: Muncrief RealPlayer package creation failed."
    err_clean_exit  
fi
						# Otherwise move final package to head directory
mv "muncrief-realplayer-build/$DEB_FILENAME" "."
ok_exit

---

