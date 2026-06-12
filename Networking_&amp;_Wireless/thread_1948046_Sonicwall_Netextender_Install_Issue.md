---
title: "Sonicwall Netextender Install Issue"
date: 2012-03-27
forum: Networking &amp; Wireless
---

### Post by abeg on 2012-03-27
I'm having trouble installing the netextender client on  Ubuntu 11.10 x64.

The error I'm getting is:
"--- SonicWALL NetExtender 5.5.707 Installer ---
Checking library dependencies...
  Missing library: libssl.so.6
  No compatible version found."

Originally I was trying to install version 4.0.665 and was getting the same error as above and another about libcrypto.so.6.  I followed a forum post to create a symlink using these two commands:
sudo ln -s /usr/lib/i386-linux-gnu/libssl.so.1.0.0 /usr/lib/libssl.so.6

sudo ln -s /usr/lib/i386-linux-gnu/libcrypto.so.1.0.0 /usr/lib/libcrypto.so.6

Running these commands fixed the issue on that version, but then I realized there's a problem with this version of netextender, java and ubuntu 11.10 so another forum post said that the latest version works.

What I don't understand is why the command fixed the libssl.so.6 for one version and not the other?  

I'm new to Linux but I know a bit of powershell and I was hoping maybe I could make some sense of the code being used, so I looked through the install script and found that the section of the code that is attempting to find the libraries is different.  Since one works and the other doesn't, I was hoping maybe I could get some help here in modifying the one that doesn't work to match the one that does work.

**Here's a section of the one that works:**

function check_library_dependencies
{
	echo "Checking library dependencies..."
	MISSINGLIBS=`ldd netExtender | grep 'not found' | awk '{print $1}'`

	if [ "$MISSINGLIBS" != "" ]
	then
		for i in $MISSINGLIBS
		do
			echo "  Missing library: $i"
			FULLNAME="$i"
			LIBNAME=`echo $i | awk -F. '{print $1 }'`
			ALT=`find /lib -maxdepth 1 -name "$LIBNAME.so*" -type f | sed 's/\*//g' | sort -r | head -1`

			if [ "$ALT" == "" ]
			then
				# Didn't find anything in /lib ; try /usr/lib
				ALT=`find /usr/lib -maxdepth 1 -name "$LIBNAME.so*" -type f | sed 's/\*//g' | sort -r | head -1`
			fi

			if [ "$ALT" != "" ]
			then
				echo "  Found likely compatible version: $ALT"
				REPLY='0'

				while [ "$REPLY" != "y" -a "$REPLY" != "n" -a "$REPLY" != "Y" -a "$REPLY" != "N" ]
				do
					read -p '  Attempt auto-repair [Y/n]? ' -n1
					if [ "$REPLY" == "" ]
					then
						REPLY='y'
					else
						echo ""
					fi
				done

				if [ "$REPLY" == 'y' -o "$REPLY" == 'Y' ]
				then
					ln -s $ALT /lib/$FULLNAME
				else
					exit_dependency_failure
				fi
			else
				# No compatible version found
				echo "  No compatible version found."
				exit_dependency_failure

**Here's a section of the one that does not work:**

function check_library_dependencies
{
	echo "Checking library dependencies..."
	MISSINGLIBS=`ldd netExtender | grep 'not found' | awk '{print $1}'`

	if [ "$MISSINGLIBS" != "" ]
	then
		for i in $MISSINGLIBS
		do
			echo "  Missing library: $i"
			FULLNAME="$i"
			LIBNAME=`echo $i | awk -F. '{print $1 }'`
			ALT=`find $LIB -maxdepth 1 -name "$LIBNAME.so*" -type f | sed 's/\*//g' | sort -r | head -1`

			if [ "$ALT" == "" ]
			then
				# Didn't find anything in $LIB ; try $USRLIB
				ALT=`find $USRLIB -maxdepth 1 -name "$LIBNAME.so*" -type f | sed 's/\*//g' | sort -r | head -1`
			fi

			if [ "$ALT" != "" ]
			then
				echo "  Found likely compatible version: $ALT"
				REPLY='0'

				while [ "$REPLY" != "y" -a "$REPLY" != "n" -a "$REPLY" != "Y" -a "$REPLY" != "N" ]
				do
					read -p '  Attempt auto-repair [Y/n]? ' -n1
					if [ "$REPLY" == "" ]
					then
						REPLY='y'
					else
						echo ""
					fi
				done

				if [ "$REPLY" == 'y' -o "$REPLY" == 'Y' ]
				then
					pushd . >/dev/null
					cd `dirname $ALT`
					ln -sv `basename $ALT` $FULLNAME
					popd >/dev/null
				else
					exit_dependency_failure
				fi
			else
				# No compatible version found
				echo "  No compatible version found."
				exit_dependency_failure

---

