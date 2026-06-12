---
title: "perfectubuntu crashed my movie playing."
date: 2009-11-30
forum: Multimedia Software
---

### Post by Oldbones on 2009-11-30
Along comes a [tweet that I want to try]("http://twitter.com/newcastlenerd/status/6192413727").... 	:-s

this script called, [perfectubuntu]("http://www.category5.tv/linux_scripts/perfectbuntu.php") claims to
[INDENT]Install tons of extras into Ubuntu / Kubuntu / Xubuntu / etc. [/INDENT]

So I was learning Ruby on Rails using Miro to play screencasts from the website learningrails.org.  After running that script, everything broke. :icon_frown:

I was using [ubuntu-tweak]("http://ubuntu-tweak.com/") for all my multiverse needs.  I haven't been having any problems with it, but I thought if perfectbuntu knew wanted to install what I already didn't have, then more power to it...

I am able to produce this error from VLC:

 ```
$ vlc ~/.miro/Movies/Learning-Rails/learningrails-9.mov 
VLC media player 1.0.2 Goldeneye
[0x25b9868] main interface error: no interface module matched "globalhotkeys,none"
[0x25b9868] main interface error: no suitable interface module
[0x24a5888] main libvlc error: interface "globalhotkeys,none" initialization failed
[0x24a5888] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x363bb78] avcodec decoder error: cannot open codec (Apple QuickTime RLE Video)
[0x363bb78] main decoder error: no suitable decoder module for fourcc `rle '.
VLC probably does not support this sound or video format.
[0x363e2a8] pulse audio output: No. of Audio Channels: 1

```

Now, I know better than to trust strange code without inspecting it first. But, I need some help reversing what it has done to my computer so I can get back to learning.  By the way, I am using ubuntu exclusively as a means to become a web developer to make cash in this recession.  

```
#!/bin/bash
# To install this file:  download it by saving it to your desktop, or wherever.
# Then, right-click the file, click Properties, and choose the Permissions tab.
# Check off "Allow Executing File as Program".
# Now, just run the file in terminal.

# For example:
# cd ~/Desktop
# ./perfectbuntu

# Accepted changes by Berry van der Linden - www.madberry.org
# Implemented in version 3.0
# -----------------------------------------------------------
# - Added colors to make some text stand out
# - Added -o so we can check for "Y" and "y" in one action.
# - Removed the "GO" if it's not necessary anymore now that we use "exit 1" on line 134
# - Only retrieve GPG keys when the repository has to be added the first time

# Added some color to make certain things jump out more
# Define some colors using terminal save colors
WHITE="\033[1;37m"
GREEN="\033[1;32m"
CYAN="\033[1;36m"
GRAY="\033[1;37m"
BLUE="\033[1;34m"
BBLUE="\033[1;34m"
BPINK="\033[1;35m"

# Set the color scheme
trap 'reset' 0
echo -en "\E[40;$32m"
clear

# Now for the code.  Don't worry about any of this stuff.  It's just nonsense.  ;)
echo
echo -en $WHITE
echo perfectbuntu
echo SCRIPT VERSION 3.2
echo -en $GRAY"By "$BBLUE"Robbie Ferguson "$GRAY"("$CYAN"www.Category5.TV"$GRAY")"
echo
echo
echo -en "With additional contributions by:"
echo
echo -en " - "$BBLUE"Berry van der Linden "$GRAY"("$CYAN"www.madberry.org"$GRAY")" 
echo
echo
echo -en "This script was originally based on "$CYAN"http://www.category5.tv/content/view/77/38/"$GRAY
echo
echo

# Detect version of Ubuntu
grep "DISTRIB_RELEASE=8.04" /etc/lsb-release > /dev/null 2>&1
if [ $? = 0 ]; then
OSVER="hardy"
fi
grep "DISTRIB_RELEASE=8.10" /etc/lsb-release > /dev/null 2>&1
if [ $? = 0 ]; then
OSVER="intrepid"
fi
grep "DISTRIB_RELEASE=9.04" /etc/lsb-release > /dev/null 2>&1
if [ $? = 0 ]; then
OSVER="jaunty"
fi
grep "DISTRIB_RELEASE=9.10" /etc/lsb-release > /dev/null 2>&1
if [ $? = 0 ]; then
OSVER="karmic"
fi

# Detect if you're running KDE or Gnome
grep "DISTRIB_ID=Ubuntu" /etc/lsb-release > /dev/null 2>&1
if [ $? = 0 ]; then
ENVIRONMENT="gnome"
fi
grep "DISTRIB_ID=Kubuntu" /etc/lsb-release > /dev/null 2>&1
if [ $? = 0 ]; then
ENVIRONMENT="kde"
fi

# set default bit to 32
BIT="32"

if [[ `uname -m` == 'amd64' || `uname -m` == 'x86_64' ]]; then
BIT="64"
fi

echo "Detected version:" $OSVER, $BIT"-bit"

if [[ $OSVER != 'hardy' && $OSVER != 'intrepid' && $OSVER != 'jaunty' && $OSVER != 'karmic' ]]; then
   echo "Your version of Linux is not supported."
   echo
   exit
fi

# Running a supported version of *buntu.  Move on.

echo
echo This script requires super-user access to continue.
echo Checking for super-user access...
#sleep 5
sudo echo -en $WHITE"Access Granted."$GRAY
echo
echo Please note: I might have to ask for your password again...
echo
echo Now, I\'ll ask you a bunch of questions, and then get right to work.
echo

# Ask all the questions...

echo -en $GREEN
read -p "Would you like to enhance your multimedia experience? (Y/N) "
echo -en $WHITE
if [ "$REPLY" = "y" -o "$REPLY" = "Y" ] ; then 
# -------
	echo
	echo -en $BLUE"=== "$WHITE"IMPORTANT"$BLUE" ==="$WHITE
	echo
	echo "Installing restricted multimedia codecs might violate"
	echo "patent and/or other laws.  Please make sure you have"
	echo "the right to use these codecs."
	echo
	echo -en $GREEN
	read -p "Install Multimedia Codecs and Restricted Extras? (Y/N) "
	echo -en $WHITE
	if [ "$REPLY" = "y" -o "$REPLY" = "Y" ] ; then 
	  MULTIMEDIA="1"
	fi
	echo

	echo -en $GREEN
	read -p "Does your computer have a DVD player? (Y/N) "
	echo -en $WHITE
	if [ "$REPLY" = "y" -o "$REPLY" = "Y" ] ; then 
	  DVD="1"
	fi

echo
echo -----

# -------
fi

echo
echo -en $GREEN
read -p "Would you like to enhance your Internet experience? (Y/N) "
echo -en $WHITE
if [ "$REPLY" = "y" -o "$REPLY" = "Y" ] ; then 
# -------
	echo
	echo Please note: I will have to close Firefox if you have it open.
	echo You may close it now if you prefer, or simply request Firefox
	echo load your previously loaded pages the next time you start it.
	echo
	echo -en $GREEN
	read -p "Would you like Firefox 3.5? (Y/N) "
	echo -en $WHITE
	if [ "$REPLY" = "y" -o "$REPLY" = "Y" ] ; then 
	  FIREFOX="1"
	fi
	echo

	echo -en $GREEN
	read -p "Do you want me to install/update the Flash plugin for you? (Y/N) "
	echo -en $WHITE
	if [ "$REPLY" = "y" -o "$REPLY" = "Y" ] ; then 
	  FLASH="1"
	fi
	echo

	echo -en $GREEN
	read -p "Should I install Skype for you? (Y/N) "
	echo -en $WHITE
	if [ "$REPLY" = "y" -o "$REPLY" = "Y" ] ; then 
	  SKYPE="1"
	fi
	echo

	echo -en $GREEN
	read -p "Do you want spam filters for Evolution? (Y/N) "
	echo -en $WHITE
	if [ "$REPLY" = "y" -o "$REPLY" = "Y" ] ; then 
	  SPAM="1"
	fi
echo
echo -----

# -------
fi

echo
echo -en $GREEN
read -p "Would you like to enhance the overall look of your *buntu system? (Y/N) "
echo -en $WHITE
if [ "$REPLY" = "y" -o "$REPLY" = "Y" ] ; then 
# -------
	echo
	echo Compiz Config Settings Manager \(CCSM\) lets you
	echo control the advanced features of Compiz-Fusion.
	echo -en $GREEN
	read -p "Should I install this for you? (Y/N) "
	echo -en $WHITE
	if [ "$REPLY" = "y" -o "$REPLY" = "Y" ] ; then 
	  CCSM="1"
	fi

	echo
	echo Avant Window Navigator is a very nice
	echo "Mac OS"-style dockbar for Linux.
	echo It requires a compositor, such as Compiz-Fusion.
	echo -en $GREEN
	read -p "Should I install avant-window-navigator for you? (Y/N) "
	echo -en $WHITE
	if [ "$REPLY" = "y" -o "$REPLY" = "Y" ] ; then 
	  AWN="1"
	fi
echo
echo -----

# -------
fi


echo
echo -en $GREEN
read -p "Would you like to improve *buntu functionality? (Y/N) "
echo -en $WHITE
if [ "$REPLY" = "y" -o "$REPLY" = "Y" ] ; then 
# -------
	echo
	echo Would you like to pre-load your most commonly used
	echo applications into memory so they load faster?
	echo Note: It can take up to a week for this to take effect.
	echo -en $GREEN
	read -p "Should I setup preload for you? (Y/N) "
	echo -en $WHITE
	if [ "$REPLY" = "y" -o "$REPLY" = "Y" ] ; then 
	  PRELOAD="1"
	fi

	echo
	echo After rebooting your *buntu system a number of times, you are
	echo forced to run a disk check on your hard drive. That means you
	echo have to wait a long time for your computer to boot. Instead,
	echo let\'s run the disk check at shutdown, so you can walk away.
	echo -en $GREEN
	read -p "Should I set this up for you? (Y/N) "
	echo -en $WHITE
	if [ "$REPLY" = "y" -o "$REPLY" = "Y" ] ; then 
	  AUTOFSCK="1"
	fi
echo
echo -----

# -------
fi




echo
echo Back in Time is like a time machine for your files.
echo Create backups that let you go back to previous versions.
if [ "$ENVIRONMENT" = "kde" ]; then
 echo Note: Make sure you have >= KDE 4.1
fi
echo -en $GREEN
read -p "Would you like me to install this? (Y/N) "
echo -en $WHITE
if [ "$REPLY" = "y" -o "$REPLY" = "Y" ] ; then 
  BACKINTIME="1"
fi
echo

echo
echo I can install a huge number of fonts which you can use in
echo your word processor, or even in programs like The GIMP.
echo -en $GREEN
read -p "Would you like a bunch of new fonts? (Y/N) "
echo -en $WHITE
if [ "$REPLY" = "y" -o "$REPLY" = "Y" ] ; then 
  FONTS="1"
fi
echo

echo wine is an application that allows you to run some
echo Windows programs directly in Linux \(.exe files\).
echo -en $GREEN
read -p "Should I install this for you? (Y/N) "
echo -en $WHITE
if [ "$REPLY" = "y" -o "$REPLY" = "Y" ] ; then 
  WINE="1"
fi
echo

echo "I can make it so you can use 7z, ZIP, Zip64, CAB, RAR, ARJ,"
echo "GZIP, BZIP2, TAR, CPIO, RPM, ISO and DEB archives in file-roller."
echo -en $GREEN
read -p "Do you want me to do this? (Y/N) "
echo -en $WHITE
if [ "$REPLY" = "y" -o "$REPLY" = "Y" ] ; then 
  COMPRESSION="1"
fi
echo


echo This script does not come with or even imply any kind of warranty.
echo If your system breaks, you take full responsibility.
echo -en $CYAN
echo
read -p "I am about to modify your system.  Are you sure this is okay? (Y/N) "
echo -en $WHITE
if [ "$REPLY" = "y" -o "$REPLY" = "Y" ] ; then 
  GO="1" #deprecated, but still here
else
  echo Exiting.
  echo
  sleep 5
  exit 1
fi
echo

# End of questions

cd ~
if [ ! -e ".perfectbuntu/datafile30" ]       # Check if file exists.
  then
    echo This is apparently the first time you have run this script.
    echo
    echo Backing up your APT sources.list file to /etc/apt/sources.list.backup...
    sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
    echo Done.
    echo
    echo Creating your APT entries now.
    mkdir ~/.perfectbuntu
    echo "Do not delete this file." >> ~/.perfectbuntu/datafile30
    echo "" >> ~/.perfectbuntu/sources30
    echo "# Added by perfectbuntu - www.category5.tv" >> ~/.perfectbuntu/sources30

# Avoid duplicates by using grep
    if grep 'main restricted universe multiverse'$ /etc/apt/sources.list > /dev/null; then
	echo "Omitting duplicate..."
    else
    echo "deb http://ca.archive.ubuntu.com/ubuntu/ "$OSVER" main restricted universe multiverse" >> ~/.perfectbuntu/sources30       
    fi 

    if grep 'main restricted'$ /etc/apt/sources.list > /dev/null; then
	echo "Omitting duplicate..."
    else
    echo "deb-src http://ca.archive.ubuntu.com/ubuntu/ "$OSVER" main restricted" >> ~/.perfectbuntu/sources30
    fi 

    if grep 'free non-free'$ /etc/apt/sources.list > /dev/null; then
	echo "Omitting duplicate..."
    else
    echo "deb http://packages.medibuntu.org/ "$OSVER" free non-free" >> ~/.perfectbuntu/sources30
	echo Retrieving GPG Signature...
	// Medibuntu
	sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update
	echo Done.
	echo
    fi 

    if grep 'deb http://ppa.launchpad.net/reacocard-awn/ubuntu '$OSVER' main'$ /etc/apt/sources.list > /dev/null; then
	echo "Omitting duplicate..."
    else
    echo "deb http://ppa.launchpad.net/reacocard-awn/ubuntu "$OSVER" main" >> ~/.perfectbuntu/sources30
    fi 

    if grep 'deb-src http://ppa.launchpad.net/reacocard-awn/ubuntu '$OSVER' main'$ /etc/apt/sources.list > /dev/null; then
	echo "Omitting duplicate..."
    else
    echo "deb-src http://ppa.launchpad.net/reacocard-awn/ubuntu "$OSVER" main" >> ~/.perfectbuntu/sources30
    fi 

# Back in Time
    if grep 'deb http://le-web.org/repository stable main'$ /etc/apt/sources.list > /dev/null; then
	echo "Omitting duplicate..."
    else
    echo "deb http://le-web.org/repository stable main" >> ~/.perfectbuntu/sources30
    wget http://le-web.org/repository/le-web.key
    sudo apt-key add le-web.key
    rm le-web.key
    fi 

# Firefox in Launchpad
    if grep 'deb http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu '$OSVER' main'$ /etc/apt/sources.list > /dev/null; then
	echo "Omitting duplicate..."
    else
    echo "deb http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu "$OSVER" main" >> ~/.perfectbuntu/sources30
	echo Retrieving GPG Signature...
	// Firefox
	sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 247510BE
	echo Done.
	echo
    fi 
    if grep 'deb-src http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu '$OSVER' main'$ /etc/apt/sources.list > /dev/null; then
	echo "Omitting duplicate..."
    else
    echo "deb-src http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu "$OSVER" main" >> ~/.perfectbuntu/sources30
    fi 


	cat ~/.perfectbuntu/sources30 | sudo tee -a /etc/apt/sources.list
    echo Done.
    echo
   fi

echo Cleaning up apt...
sudo apt-get clean
echo Done.
echo

echo Updating apt...
sudo apt-get update
echo Done.
echo



#Run the installers

if [ "$FLASH" = "1" ]; then
	echo Closing your browser windows...
	killall -9 firefox
	echo Removing your old Flash plugin...

	sudo apt-get --force-yes -y -f -m --purge remove flashplugin-nonfree adobe-flashplugin flashplugin-installer

	echo Installing Flash plugin installer...
	sudo apt-get --force-yes -y -f -m install flashplugin-installer
	echo Done.
	echo
fi

if [ "$MULTIMEDIA" = "1" ]; then
	echo Installing multimedia codecs...
	sudo apt-get --force-yes -y -f -m install ubuntu-restricted-extras
	sudo apt-get --force-yes -y -f -m install gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly gstreamer0.10-ffmpeg libxine1-ffmpeg libdvdread3
	sudo apt-get -y -f -m install "w"$BIT"codecs"
	echo Done.
	echo
fi

if [ "$FONTS" = "1" ]; then
	echo Installing roughly a billion fonts...
	sudo apt-get -y -f -m install msttcorefonts
	echo
	echo NOTE: That should be the last EULA you\'ll have to deal with.
	echo You can go get a coffee now while I finish up.
	echo It\'s going to take a while.
	echo
	echo Continuing with font installations...
	sudo apt-get -y -f -m install ttf-gentium ttf-dustin ttf-georgewilliams ttf-sjfonts sun-java6-fonts ttf-larabie-deco ttf-larabie-straight ttf-larabie-uncommon ttf-linux-libertine ttf-mgopen ttf-sil-charis ttf-sil-doulos ttf-ubuntu-title gsfonts-x11 ttf-fifthhorseman-dkg-handwriting ttf-alee ttf-alee ttf-ancient-fonts ttf-arhangai ttf-arphic-bkai00mp ttf-arphic-bsmi00lp ttf-arphic-gbsn00lp ttf-arphic-gkai00mp ttf-arphic-ukai ttf-atarismall ttf-baekmuk ttf-bengali-fonts ttf-beteckna ttf-bpg-georgian-fonts ttf-breip ttf-devanagari-fonts ttf-dzongkha ttf-ecolier-court ttf-essays1743 ttf-f500 ttf-farsiweb ttf-freefarsi ttf-gfs-artemisia ttf-gfs-bodoni-classic ttf-gfs-complutum ttf-gfs-didot-classic ttf-gfs-gazis ttf-gfs-neohellenic ttf-gfs-solomos ttf-gfs-theokritos ttf-gujarati-fonts ttf-inconsolata ttf-indic-fonts ttf-isabella ttf-junicode ttf-kacst ttf-kannada-fonts ttf-khmeros ttf-kiloji ttf-kochi-gothic-naga10 ttf-kochi-mincho-naga10 ttf-konatu ttf-liberation ttf-manchufont ttf-marvosym ttf-mikachan ttf-mona ttf-mph-2b-damase ttf-nafees ttf-ocr-a ttf-oflb-euterpe ttf-oriya-fonts ttf-paktype ttf-punjabi-fonts ttf-radisnoir ttf-sazanami-gothic ttf-sazanami-mincho ttf-sil-abyssinica ttf-sil-andika ttf-sil-ezra ttf-sil-padauk ttf-sil-scheherazade ttf-sil-yi ttf-staypuft ttf-summersby ttf-tamil-fonts ttf-tmuni ttf-tuffy ttf-unfonts ttf-unfonts-extra ttf-uralic ttf-vlgothic ttf-wqy-zenhei ttf-xfree86-nonfree ttf-xfree86-nonfree-syriac
	echo Done.
	echo
fi

if [ "$DVD" = "1" ]; then
	echo Installing DVD decoders and support files...
	sudo apt-get -y -f -m install libdvdcss2 libdvdread3 ffmpeg "w"$BIT"codecs"
	echo Done.
	echo
fi

if [ "$PRELOAD" = "1" ]; then
	echo Installing preload...
	sudo apt-get -y -f -m install preload
	echo Done.
	echo
fi

if [ "$AUTOFSCK" = "1" ]; then
	echo Installing AutoFsck \(disk check at shutdown\)...
	sudo apt-get -y -f -m install autofsck
	echo Done.
	echo
fi

if [ "$AWN" = "1" ]; then
	echo Installing avant-window-navigator Dockbar...
	# Used to install the BZR, but now the stable version has been updated so it's not necessary
	#sudo apt-get --force-yes -y -f -m install awn-manager-bzr
	#sudo apt-get --force-yes -y -f -m install avant-window-navigator-bzr avant-window-navigator-data
	# Install the stable version instead
	sudo apt-get --force-yes -y -f -m install avant-window-navigator awn-applets-c-extras awn-manager
	echo Done.
	echo
fi

if [ "$COMPRESSION" = "1" ]; then
	echo Installing support for multiple archive types in file-roller...
	sudo apt-get -y -f -m install lzma unrar rar p7zip p7zip-full p7zip-rar
	echo Done.
	echo
fi

if [ "$WINE" = "1" ]; then
	echo Installing wine...
	sudo apt-get -y -f -m install wine
	echo Done.
	echo
fi

if [ "$SKYPE" = "1" ]; then
	echo Installing Skype...
	sudo apt-get -y -f -m install skype
	echo Done.
	echo
fi

if [ "$SPAM" = "1" ]; then
	echo Installing SPAM filters...
	sudo apt-get -y -f -m install spamassassin
	echo Done.
	echo
fi

if [ "$FIREFOX" = "1" ]; then
	echo Closing your browser windows...
	killall -9 firefox
	echo Installing Firefox...
	sudo apt-get -y -f -m install firefox-3.5
	echo Done.
	echo
	echo Creating symbolic link to Firefox 3.5
	cd /usr/bin
	# notice, this command also creates a backup of your original firefox symlink
	sudo ln -b -f -s firefox-3.5 firefox
	echo Done.
	echo
fi

# CCSM allows you to customize your special effects and all settings in Compiz.
if [ "$CCSM" = "1" ]; then
	echo Installing CCSM advanced visual effects for Compiz Fusion...
	sudo apt-get -y -f -m install compizconfig-settings-manager
	echo Done.
	echo
fi

if [ "$BACKINTIME" = "1" ]; then
		echo Installing Back In Time backup software...
	if [ "$ENVIRONMENT" = "kde" ]; then
		sudo apt-get -y -f -m install backintime-common backintime-kde4
		echo Done.
	else if [ "$ENVIRONMENT" = "gnome" ]; then
		sudo apt-get -y -f -m install backintime-common backintime-gnome
		echo Done.
	else
		echo Sorry; You need either KDE or Gnome for this one :\(
	fi
		echo
fi

# Install stuff that everyone should have (no prompt)
# xnest updates Terminal Server Client to support the XDMCP protocol allowing you to connect to other Linux machines.  It's strange this isn't included out-of-the-box.
echo "I'm going to install some things that everyone should have..."
echo
echo "Installing support for XDMCP (remote desktop for Linux, essentially)..."
sudo apt-get -y -f -m install xnest
echo Done.
echo


echo All done.  Enjoy the Perfect *buntu!
echo Visit www.category5.tv/content/view/164/77

fi

sleep 5

```

Thanks to anyone out there who might be able to lend a hand.

Doug

---

