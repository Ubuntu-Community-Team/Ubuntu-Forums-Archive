---
title: "Script to check for new nVidia releases"
date: 2009-04-25
forum: Multimedia Software
---

### Post by loomsen on 2009-04-25
Hey folks.

Just created one, so I thought I could share it...

Should work on either 32bit or amd64 machines for all cards as of the GeForce 6 series and above (so obviously all cards which are supported by the newest releases (180.++)

Current:
Direct download: [HERE](http://omploader.org/vMzY1Mw)

---

### Post by loomsen on 2009-04-28
- reviewed and added user interaction 
   will inform about newly available version and ask before downloading.

---

### Post by loomsen on 2009-04-28
- another review, now asks the user which version to look for

Pre-release versions now also included...

---

### Post by loomsen on 2009-09-01
Hello.

Although obviously nobody uses it, I've been bored and completely rewritten it.
Should be a lot better now, so I gonna remove the old version.

Here's 0.0.2:
*outdated*
Enjoy.

---

### Post by loomsen on 2009-09-11
Thx to coz_ who told me uname -m isn't working for 32bit archs.
Here's the updated version (if anybody is using ia64, i would appreciate if you would let me know what `uname -m` returns so I can add it too)

*outdated*

---

### Post by -=hazard=- on 2009-09-11
Simple question. 
This script just search and download the newest driver for nvidia? Or it install it too with the appropriate headers etcetera?

---

### Post by loomsen on 2009-09-11
Nope, just checks for new drivers. Useful if you get stuck in a shell and don't like lynx or w3m or so to figure out how the download url is.

Actually, the nVidia driver doesn't have to many dependencies, kernel-headers, glibc and make should be it.

---

### Post by -=hazard=- on 2009-09-12
I have nVidia GeForce 6200 and I use 180 driver version on Ubunut 9.04. There is a driver update on nvidia website. Do you use the updated driver? And if yes, is there any big change or fixes on the new one?

---

### Post by loomsen on 2009-09-12
I'm usually using the latest drivers available, at the moment this is 190.32
But I'm not running ubuntu, so I don't know which fix or improvement your hoping for.

But, as altering the driver takes about 2 minutes (drop to a shell, change runlevel - or on ubuntu make X stop somehow like for example
/etc/init.d/gdm stop
and then run sh NVIDIA-xxx.run --uninstall
and finally sh NVIDIA-xxx.run 
to remove your current and build another one.

A final 
/etc/init.d/gdm start
will bump you back into gnome (or whichever DM you're running)

---

### Post by -=hazard=- on 2009-09-12
> **loomsen said:**
> I'm usually using the latest drivers available, at the moment this is 190.32
But I'm not running ubuntu, so I don't know which fix or improvement your hoping for.

But, as altering the driver takes about 2 minutes (drop to a shell, change runlevel - or on ubuntu make X stop somehow like for example
/etc/init.d/gdm stop
and then run sh NVIDIA-xxx.run --uninstall
and finally sh NVIDIA-xxx.run 
to remove your current and build another one.

A final 
/etc/init.d/gdm start
will bump you back into gnome (or whichever DM you're running)

Can you tell me where I can find the kernel headers? Or at least where do you get them for your box.

---

### Post by -=hazard=- on 2009-09-12
Ok found them.. sorry for posting something out of the topic and thnx :)

---

### Post by loomsen on 2009-09-12
Ahh, it's ok, actually, I even have to thank you :D

There hasn't been too much going on in here anyway ^^

---

### Post by loomsen on 2010-01-05
Here's the most recent review:

```

#!/bin/bash
set +x
#	-------------------------------------------------------------------
#
#	Shell program to check for new nvidia drivers.
#
#	Copyright 2009, Norbert Varzariu <loomsen@googlemail.com>						
#
#	This program is free software; you can redistribute it and/or
#	modify it under the terms of the GNU General Public License as
#	published by the Free Software Foundation; either version 2 of the
#	License, or (at your option) any later version. 
#
#	This program is distributed in the hope that it will be useful, but
#	WITHOUT ANY WARRANTY; without even the implied warranty of
#	MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
#	General Public License for more details.
#
#	Revision History:
#
#	09/01/2009	File created by new_script ver. 2.1.0
## ================================================================
# If you add something, please update the ChangeLog accordingly. 
# You may want to add support for legacy versions for instance.
# Draft on how the header should look:
# * $(date +'%a %b %d %Y') Name Mail - %version
## ================================================================
#
#	 ChangeLog:
#	* Wed Jan 06 2010 Norbert Varzariu <loomsen@googlemail.com>
#	- some minor fixes
#	* Sat Sep 12 2009 Norbert Varzariu <loomsen@googlemail.com> - 0.0.3
#	- fixed x86 download
#	* Tue Sep 01 2009 Norbert Varzariu <loomsen@googlemail.com> - 0.0.2
#	- added check for currently running driver 
#	- added check for locally available binary 
#
#
#	-------------------------------------------------------------------
#	Constants
#	-------------------------------------------------------------------

	PROGNAME=$(basename $0)
	VERSION="0.0.2"
	DRVINFO=http://people.freedesktop.org/~aplattner/nvidia-versions
#	REPO="ftp://download.nvidia.com/XFree86/`uname`-$__UNAME"
## only call if new driver download requested, not if dump version only
	LOCALVER="`nvidia-settings -q  NvidiaDriverVersion --terse`"

# ================== common functions ============================

if [ "`uname -m`" != "x86_64" ]; then
	export __UNAME="x86"
else
	export __UNAME="x86_64"
fi
export REPO="ftp://download.nvidia.com/XFree86/`uname`-$__UNAME"

function clean_up
{
	rm -f ${TEMP_FILE1}
}
function error_exit
{
	echo "${PROGNAME}: ${1:-"Unknown Error"}" >&2
	clean_up
	exit 1
}
function graceful_exit
{
	clean_up
	exit
}
function signal_exit
{
	case $1 in
		INT)	echo "$PROGNAME: Program aborted by user" >&2
			clean_up
			exit
			;;
		TERM)	echo "$PROGNAME: Program terminated" >&2
			clean_up
			exit
			;;
		*)	error_exit "$PROGNAME: Terminating on unknown signal"
			;;
	esac
}
function make_temp_files
{
	if [ -d ~/tmp ]; then
		TEMP_DIR=~/tmp
	else
		TEMP_DIR=/tmp
	fi
	TEMP_FILE1=$(mktemp -q "${TEMP_DIR}/${PROGNAME}.$$.XXXXXX")
	if [ "$TEMP_FILE1" = "" ]; then
		error_exit "cannot create temp file!"
	fi
}
function usage
{
	echo -e "Usage: ${PROGNAME} [-h | --help] [-b] [-B dest_dir] [-a] [-A dest_dir]\n 
	\t     [-s] [-S dest_dir]"
}
function helptext
{
	local tab=$(echo -en "\t\t")

	cat <<- -EOF-
	${PROGNAME} ver. ${VERSION}
	This is a program to check for currently available nVidia drivers.

	$(usage)

	Options:
	-s              	list current stable
	-S  download_dir	get current stable
	-b              	list current beta
	-B  download_dir	get current beta
	-a              	list all available
	-A  download_dir	get all available

	-h, --help		Display this help message and exit.

-EOF-
}

# ====================== program specific functions ==========

function get_latest_driver_listing 
{
	echo -e "Checking for update"
	wget -q "$DRVINFO" --output-document=$TEMP_FILE1
	LATEST=$TEMP_FILE1
}
function getopts_version
{
	VER_NUM=`grep "$VER" < $LATEST | awk '{print $3}'`
	PKG="NVIDIA-`uname`-$__UNAME-$VER_NUM-pkg2.run"
	echo "your choice: Driver $VER_NUM"
	if [ "$LOCALVER" == "$VER_NUM" ]; then
		if ! ask_yes_no "you already have that driver installed, do you want me to download the binary regardless? [y/N] "; then
			signal_exit INT
		fi
	fi

	if [ -f $OPTARG/$VER_NUM/$PKG ]; then
		echo -e "you already have the source available on your local machine, \nlook into $OPTARG/$VER_NUM/"
		echo "nothing to do, exiting..."
		graceful_exit
	fi
}
function download_driver
{
	
	echo "downloading, hold on..."
	mkdir -p $OPTARG/$VER_NUM
	wget -q $REPO/$VER_NUM/$PKG --output-document=$TEMP_DIR/$PKG || error_exit "couldnt download driver file"
	mv $TEMP_DIR/$PKG $OPTARG/$VER_NUM || error_exit "couldnt move package to specified dir, do you have proper permissions?"
	echo -e "done! your files are in \n$OPTARG/$VER_NUM"
}
function ask_yes_no
{
	local yn=
	while [ "$yn" = "" ]; do
		echo -en "$1"
		read yn
		case $yn in
			y|Y)	yn=0 ;;
			n|N)	yn=1 ;;
			*)	yn=
				echo "Invalid response - please answer y or n"
				;;
		esac
	done
	return $yn
}

function get_them_all
{
	if ! ask_yes_no "this will download all files, are you sure?  [y/n] "; then
		signal_exit INT
	else
	echo "downloading, hold on..."
		PKG=
		grep -v '#' $LATEST | head -n 2 > $TEMP_DIR/TEMP_FILE2
		for i in `awk '{print $3}' $TEMP_DIR/TEMP_FILE2`; do
			mkdir -p $OPTARG/$i
			PKG="NVIDIA-`uname`-$__UNAME-$i-pkg2.run"
			wget -q $REPO/$i/$PKG --output-document=$TEMP_DIR/$PKG ; mv $TEMP_DIR/$PKG $OPTARG/$i/
		done
	echo -e "Your files are in $OPTARG/"
	rm $TEMP_DIR/TEMP_FILE2
	fi
}
#	Program starts here
# Set file creation mask so that all files are created with 600 permissions.
umask 066

# Trap TERM, HUP, and INT signals and properly exit
trap "signal_exit TERM" TERM HUP
trap "signal_exit INT"  INT

# Create temporary file(s)
make_temp_files

##### Command Line Processing #####
## prevent download when usage or help message is to be displayed
if [ "$1" = "--help" -o "$1" = "-h" ]; then
	helptext
	graceful_exit
elif [ "$1" = "" ]; then
	usage
	graceful_exit
else
	get_latest_driver_listing
fi

while getopts ":hbB:aA:oO:sS:" opt; do
	case $opt in
		b )	awk /'current beta'/ $LATEST
			echo -e "\nYour local version is: $LOCALVER"
			graceful_exit
			;;
		B )	VER='current beta'
			download_dir=$OPTARG
			getopts_version
			download_driver
			graceful_exit
			;;
		a )	grep -v '#' $LATEST | head -n 2
			echo -e "\nYour local version is: $LOCALVER"
			graceful_exit
			;;
		A )	download_dir=$OPTARG
			get_them_all
			graceful_exit
			;;
		s )	awk /'current official'/ $LATEST
			echo -e "\nYour local version is: $LOCALVER"
			graceful_exit
			;;
		S )	VER='current official'
			download_dir=$OPTARG
			getopts_version
			download_driver
			graceful_exit
			;;
		*|? )	usage
			clean_up
			exit 1
	esac
done

unset __UNAME REPO
graceful_exit


```

Enjoy, direct download &#8594; first post

---

