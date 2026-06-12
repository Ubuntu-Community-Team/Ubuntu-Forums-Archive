---
title: "Nortel CVC Installer"
date: 2008-12-31
forum: Networking &amp; Wireless
---

### Post by suilix on 2008-12-31
The shell script below implements hints and suggestions from contributors to the Ubuntu and Fedora forums. To use this script, download the evaluation version or the purchased version of the CVC distribution from Apani's web site to a new folder on your Desktop. In the same folder, copy and paste this script into a file named cvc-ubuntu-installer.sh and use the pop-up properties to change permissions to allow executing it as a program. Run the script in a terminal window. The script will step you through the installation.  
```

#!/bin/sh
## CONFIGURATION #############################################################
URL_APANI_VPN="http://www.apani.com/vpn/"
URL_UBUNTU_FORUM1="http://ubuntuforums.org/showthread.php?t=110843"
URL_UBUNTU_FORUM2="http://ubuntuforums.org/showthread.php?t=441042"
URL_FEDORA_FORUM="http://fedoraforum.org/"
URL_LINUX_WRAPPER_TAR="http://forums.fedoraforum.org/attachment.php?attachmentid=15806&d=1209555182"
URL_NLVCARD_TAR="http://forums.fedoraforum.org/attachment.php?attachmentid=15807&d=1209555190"
LINUX_WRAPPER_TAR="linux_wrapper.tar"
NLVCARD_TAR="nvlcard.tar"
DEFAULT_ACTION="N"
MAX_STEP=19
STEP=0
QUIT="false"
UNDO="false"
DEFAULT_APANI_CVC_TAR_GZ=cvc_linux-rh-gcc3-3.5e.tar.gz
APANI_CVC_TAR_GZ=$DEFAULT_APANI_CVC_TAR_GZ
APANI_CVC_SCRIPTS="install.sh netlock uninstall.sh scripts/netlock scripts/start_cvc"

## FUNCTIONS #################################################################
setApaniNames()
{
	APANI_CVC_TAR_GZ_BACKUP=$APANI_CVC_TAR_GZ.backup
	APANI_CVC_TAR=${APANI_CVC_TAR_GZ%.gz}
	if [ $(expr "$APANI_CVC_TAR_GZ" : ".*e.tar.gz") -ne 0 ]; then
		APANI_CVC_DIR=${APANI_CVC_TAR_GZ%e.tar.gz}
	else
		APANI_CVC_DIR=${APANI_CVC_TAR_GZ%tar.gz}
	fi
}

getAction()
{
	echo ""
	read -p "ENTER [N]ext, [P]revious, [R]epeat, [S]kip, [Q]uit (Default=$DEFAULT_ACTION): " RESPONSE
	echo ""
	ACTION=$(echo $RESPONSE | tr "[:lower:]" "[:upper:]")
	if [ $(expr "$ACTION" : "[NPRSQ]") -eq 0 ]; then
		ACTION=$DEFAULT_ACTION
	fi
	case $ACTION in
		N) # Next
			if [ $STEP -lt $MAX_STEP ]; then
				STEP=$(expr $STEP + 1); 
			fi
			UNDO="false"
			;;
		P) # Previous
			if [ $STEP -gt 0 ]; then
				STEP=$(expr $STEP - 1); 
			fi
			UNDO="true"
			;;
		R) # Repeat
			;;
		S) # Skip
			if [ $STEP -lt $MAX_STEP ]; then
				STEP=$(expr $STEP + 2); 
			fi
			UNDO="false"
			;;
		Q) # Quit
			STEP=$MAX_STEP
			UNDO="false"
			;;
	esac
}

intro()
{
cat <<TEXT
=========== Install Apani's Continuity VPN Client (CVC) to Ubuntu. ===========

This shell script implements hints and suggestions from contributers to the
Ubuntu and Fedora forums. To use this script, download the evaluation version
or the purchased version of the CVC distribution from Apani's web site to a new
folder on your Desktop. In the same folder, copy and paste this script into a
file named cvc-ubuntu-installer.sh and use the pop-up properties to change
permissions to allow executing it as a program. Run the script in a terminal
window. This script will step you through the installation.

Links:
	$URL_APANI_VPN
	$URL_UBUNTU_FORUM1
	$URL_UBUNTU_FORUM2
	$URL_FEDORA_FORUM
	$URL_LINUX_WRAPPER_TAR
	$URL_NLVCARD_TAR
TEXT
}

viewVerifyApaniDistributionExists()
{
cat <<TEXT
This script depends on an evaluation or purchased distribution of the CVC
software from Apani. This next step will prompt for the name of the CVC
distribution file and verify that it can be found and is readable.
TEXT
}

doVerifyApaniDistributionExists()
{
	APANI_CVC_TAR_GZ=$DEFAULT_APANI_CVC_TAR_GZ
	read -p "Enter Apani CVC distribution name (Default=$APANI_CVC_TAR_GZ): " RESPONSE
	if [ $RESPONSE ]; then
		APANI_CVC_TAR_GZ=$RESPONSE
		setApaniNames
	fi
	if [ -r "$APANI_CVC_TAR_GZ" ]; then
		echo "SUCCESS: The file is readable."
	else
		echo "ERROR: The file is not readable or it does not exist!!!"
	fi
}

viewUncompressApaniDistribution()
{
cat <<TEXT
The distribution file will be backed up and uncompressed ...
TEXT
}

doUncompressApaniDistribution()
{
	if [ $UNDO = "true" ]; then
		rm $APANI_CVC_TAR
	else
		cp $APANI_CVC_TAR_GZ $APANI_CVC_TAR_GZ_BACKUP
		gunzip $APANI_CVC_TAR_GZ
		if [ $? -eq 0 ]; then
			echo "SUCCESS: Uncompressed file to $APANI_CVC_TAR"
			mv $APANI_CVC_TAR_GZ_BACKUP $APANI_CVC_TAR_GZ
		else
			echo "ERROR: Cannot uncompress $APANI_CVC_TAR_GZ"
		fi
	fi
}

viewGetModifiedSourceFiles()
{
cat <<TEXT
Contributers to the forums have modified linux_wrapper.c and nlvcard.c to work
with more recent Linux kernals. The next step will download the packed (tar)
files from the forums.
TEXT
}

doGetModifiedSourceFiles()
{
	if [ $UNDO = "true" ]; then
		rm $LINUX_WRAPPER_TAR
		rm $NLVCARD_TAR
	else
		wget $URL_LINUX_WRAPPER_TAR -O $LINUX_WRAPPER_TAR
		if [ -f $LINUX_WRAPPER_TAR ]; then
			echo "SUCCESS: Downloaded $LINUX_WRAPPER_TAR"
		fi
		wget $URL_NLVCARD_TAR -O $NLVCARD_TAR
		if [ -f $NLVCARD_TAR ]; then
			echo "SUCCESS: Downloaded $NLVCARD_TAR"
		fi
	fi
}

viewUnpackArchives()
{
cat <<TEXT
The distribution file and forum downloads will be unpacked ...
TEXT
}

doUnpackArchives()
{
	if [ $UNDO = "true" ]; then
		rm -fR $APANI_CVC_DIR
	else
		tar -xf $APANI_CVC_TAR
		if [ $? -eq 0 ]; then
			echo "SUCCESS: Unpacked file to $APANI_CVC_DIR"
		else
			echo "ERROR: Cannot unpack $APANI_CVC_TAR"
		fi

		tar -C $APANI_CVC_DIR -xf $LINUX_WRAPPER_TAR
		if [ $? -eq 0 ]; then
			echo "SUCCESS: Unpacked file in $APANI_CVC_DIR"
		else
			echo "ERROR: Cannot unpack $LINUX_WRAPPER_TAR"
		fi

		tar -C $APANI_CVC_DIR -xf $NLVCARD_TAR
		if [ $? -eq 0 ]; then
			echo "SUCCESS: Unpacked file in $APANI_CVC_DIR"
		else
			echo "ERROR: Cannot unpack $NLVCARD_TAR"
		fi
	fi
}

viewChangeDeclaredShell()
{
cat <<TEXT
The distribution scripts use the default shell. For Ubuntu, the default shell
is dash. Contributers to the forums state that the bash shell works better. The
next step changes the script declarations from dash to bash.
TEXT
}

doChangeDeclaredShell()
{
	OLDSHELL="sh"
	NEWSHELL="bash"
	if [ $UNDO = "true" ]; then
		OLDSHELL="bash"
		NEWSHELL="sh"
	fi
	THISDIR=$(pwd)
	cd $APANI_CVC_DIR
	for SCRIPT in $APANI_CVC_SCRIPTS
		do
			sed -i "1,1s|#!/bin/${OLDSHELL}|#!/bin/${NEWSHELL}|" $SCRIPT
			if [ $? -eq 0 ]; then
				echo "SUCCESS: Changed the declared shell for $SCRIPT from $OLDSHELL to $NEWSHELL."
			else
				echo "ERROR: Cannot change the declared shell for $SCRIPT to $NEWSHELL."
			fi
		done
	cd $THISDIR
}

viewFixInstallScript()
{
cat <<TEXT
There is a bug in the distribution's install.sh script. The next step fixes the
bug by inserting a space character in the offending 'elif' statement.
TEXT
}

doFixInstallScript()
{
	THISDIR=$(pwd)
	cd $APANI_CVC_DIR
    sed -i "1,\$s|elif \[-d|elif [ -d|" install.sh
	if [ $? -eq 0 ]; then
		echo "SUCCESS: Fixed bug in install.sh."
	else
		echo "ERROR: Cannt fix bug in install.sh."
	fi
	cd $THISDIR
}

viewMakeAll()
{
cat <<TEXT
The distribution has been updated as recommended by contributers on the forums.
The next step will compile the source code and prepare the distribution for
installation.
TEXT
}

doMakeAll()
{
	THISDIR=$(pwd)
	cd $APANI_CVC_DIR
	if [ $UNDO = "true" ]; then
		sudo make clean
	else
		sudo make all
	fi
	cd $THISDIR
}

viewUninstall()
{
cat <<TEXT
The distribution is ready for installation. Before you install it, this step
gives you the option to uninstall a previous version. Enter 'S' to skip this
optional step. If you choose to uninstall a previous version, then you need
to restart Ubuntu to avoid latent weirdness.
TEXT
}

doUninstall()
{
	THISDIR=$(pwd)
	cd $APANI_CVC_DIR
	sudo make uninstall
	cd $THISDIR
}

viewInstall()
{
cat <<TEXT
Install the distribution then open your web browser to http://localhost:9161.
TEXT
}

doInstall()
{
	THISDIR=$(pwd)
	cd $APANI_CVC_DIR
	sudo make install
	cd $THISDIR
}

## MAIN ######################################################################
setApaniNames
while [ $QUIT = "false" ]; do
	case $STEP in
		0) intro;;
		1) viewVerifyApaniDistributionExists;;
		2) doVerifyApaniDistributionExists;;
		3) viewUncompressApaniDistribution;;
		4) doUncompressApaniDistribution;;
		5) viewGetModifiedSourceFiles;;
		6) doGetModifiedSourceFiles;;
		7) viewUnpackArchives;;
		8) doUnpackArchives;;
		9) viewChangeDeclaredShell;;
		10) doChangeDeclaredShell;;
		11) viewFixInstallScript;;
		12) doFixInstallScript;;
		13) viewMakeAll;;
		14) doMakeAll;;
		15) viewUninstall;;
		16) doUninstall;;
		17) viewInstall;;
		18) doInstall;;
		19) exit 0;;
	esac
	getAction
done
# vi:set tabstop=4 hardtabs=4 shiftwidth=4:

```

---

### Post by Zeratul7 on 2009-01-04
This still crashes my Hardy completely after a while.

---

### Post by suilix on 2009-02-07
My fortune has been better. After using the above script to install the trial version of the Nortel VPN client from Apani, I decided to buy the licensed version. The licensed download is an archive that contains distributions for RedHat, Suse, etc.; thus, there is an extra step to select one of the distributions before running the above script. I selected the RedHat version again because that was the one referenced in the forums. I found two bugs in the above script. The value for APANI_CVC_DIR omitted a dot and Apani's uninstall.sh script contained the same bug as their install.sh script. I corrected the script shown in the first posting above by adding the 'dot' and by repeating fix for the 'install' script to also fix the 'uninstall' script. I ran the above script to first uninstall the evaluation version, rebooted, then installed the licensed version. I have been using the Nortel VPN client under Ubuntu V8.04 (Hardy Heron) for about two weeks, reliably.

Below is a patch to prepare the above script for uninstallation of the evaluation version and installation of the licensed version. Copy and paste it to a file named 'cvc-ubuntu-installer.sh.patch' then apply the patch like this:
```

patch cvc-ubuntu-installer.sh cvc-ubuntu-installer.sh.patch

```
```

16c16,17
< DEFAULT_APANI_CVC_TAR_GZ=cvc_linux-rh-gcc3-3.5e.tar.gz
---
> # DEFAULT_APANI_CVC_TAR_GZ=cvc_linux-rh-gcc3-3.5e.tar.gz
> DEFAULT_APANI_CVC_TAR_GZ=cvc_linux-rh-gcc3-3.5.tar.gz
28c29
< 		APANI_CVC_DIR=${APANI_CVC_TAR_GZ%tar.gz}
---
> 		APANI_CVC_DIR=${APANI_CVC_TAR_GZ%.tar.gz}
35c36
< 	read -p "ENTER [N]ext, [P]revious, [R]epeat, [s]kip, [Q]uit (Default=$DEFAULT_ACTION): " RESPONSE
---
> 	read -p "ENTER [N]ext, [P]revious, [R]epeat, [S]kip, [Q]uit (Default=$DEFAULT_ACTION): " RESPONSE
248a250,255
>     sed -i "1,\$s|elif \[-d|elif [ -d|" uninstall.sh
> 	if [ $? -eq 0 ]; then
> 		echo "SUCCESS: Fixed bug in uninstall.sh."
> 	else
> 		echo "ERROR: Cannt fix bug in uninstall.sh."
> 	fi

```

If anyone has experience with the Nortel VPN client from Apani on Ubuntu V8.10 (Intepid Ibex), I would like to learn about your results!

---

### Post by suilix on 2009-02-07
The Nortel VPN client for Linux uses a web page as its user interface. Ubuntu has a lightweight browser called w3m that can be used from the shell as a text based browser. You can create a launcher in your task bar by:

1) Right click on the task bar.
2) Select 'Add to Panel...'
3) Select 'Custom Apllication Launcher'
4) Select 'Application in Terminal'
5) Name: Nortel VPN
6) Command: w3m [http://localhost:9161](http://localhost:9161)

To get started first configure and test your VPN settings using a full featured Web Browser like FireFox, etc. Then you can use w3m to connect, monitor and disconnect your VPN session. I found that the password field is best used by clicking on it then hit enter, you will get a prompt where you can enter your password and hit enter again. Good luck!

---

### Post by kyle12345 on 2009-03-13
I have tried the installer but am receiving some compile errors.
I did copied cvc_linux-rh-gcc3-3.5e.tar.gz to cvc_linux-rh-gcc3-3.5.tar.gz
so that the script would work...
System: Ubuntu 8.10 - the Intrepid Ibex - released in October 2008.
uname: Linux laptop 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686 GNU/Linux
				
  Any help would be appreciated:

cd src && make all
make[1]: Entering directory `/home/kyle12345/cvc/cvc_linux-rh-gcc3-3.5/src'
cd k2.6 && make
make[2]: Entering directory `/home/kyle12345/cvc/cvc_linux-rh-gcc3-3.5/src/k2.6'
make -C /lib/modules/2.6.27-11-generic/build SUBDIRS=/home/kyle12345/cvc/cvc_linux-rh-gcc3-3.5/src/k2.6 modules
make[3]: Entering directory `/usr/src/linux-headers-2.6.27-11-generic'
  CC [M]  /home/kyle12345/cvc/cvc_linux-rh-gcc3-3.5/src/k2.6/linux_wrapper.o
/home/kyle12345/cvc/cvc_linux-rh-gcc3-3.5/src/k2.6/linux_wrapper.c: In function ‘ip_route_output’:
/home/kyle12345/cvc/cvc_linux-rh-gcc3-3.5/src/k2.6/linux_wrapper.c:129: [COLOR="Red"]error: too few arguments to function ‘ip_route_output_key’[/COLOR]
/home/kyle12345/cvc/cvc_linux-rh-gcc3-3.5/src/k2.6/linux_wrapper.c: In function ‘register_nl_netfilter’:
/home/kyle12345/cvc/cvc_linux-rh-gcc3-3.5/src/k2.6/linux_wrapper.c:267: [COLOR="Red"]error: ‘NF_IP_LOCAL_IN’ undeclared (first use in this function)
[/COLOR]/home/kyle12345/cvc/cvc_linux-rh-gcc3-3.5/src/k2.6/linux_wrapper.c:267: error: (Each undeclared identifier is reported only once
/home/kyle12345/cvc/cvc_linux-rh-gcc3-3.5/src/k2.6/linux_wrapper.c:267: error: for each function it appears in.)
/home/kyle12345/cvc/cvc_linux-rh-gcc3-3.5/src/k2.6/linux_wrapper.c:274: error: ‘NF_IP_LOCAL_OUT’ undeclared (first use in this function)
/home/kyle12345/cvc/cvc_linux-rh-gcc3-3.5/src/k2.6/linux_wrapper.c: At top level:
[COLOR="Red"]/home/kyle12345/cvc/cvc_linux-rh-gcc3-3.5/src/k2.6/linux_wrapper.c:560: error: conflicting types for ‘dev_name’
[/COLOR]include/linux/device.h:411: error: previous definition of ‘dev_name’ was here
make[4]: *** [/home/kyle12345/cvc/cvc_linux-rh-gcc3-3.5/src/k2.6/linux_wrapper.o] Error 1
make[3]: *** [_module_/home/kyle12345/cvc/cvc_linux-rh-gcc3-3.5/src/k2.6] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'
make[2]: *** [kmod_build] Error 2
make[2]: Leaving directory `/home/kyle12345/cvc/cvc_linux-rh-gcc3-3.5/src/k2.6'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/kyle12345/cvc/cvc_linux-rh-gcc3-3.5/src'
make: *** [all] Error 2

---

### Post by suilix on 2009-03-25
Regarding "... copied cvc_linux-rh-gcc3-3.5e.tar.gz to cvc_linux-rh-gcc3-3.5.tar.gz so that the script would work...", the script contains a variable to define the default tarbar name.
```
DEFAULT_APANI_CVC_TAR_GZ=cvc_linux-rh-gcc3-3.5e.tar.gz
```
You can edit the script and change the name to match your download *or* enter the exact name when the script prompts for it.

Regarding the compilation errors in linux_wrapper.c, you are not alone, see [http://forums.fedoraforum.org/printthread.php?t=191038](http://forums.fedoraforum.org/printthread.php?t=191038).

---

### Post by gmoore777 on 2009-05-06
FYI:

I never got the Apani VPN version 3.5 to "successfully" work on HardyHeron.
(see old thread [http://ubuntuforums.org/showthread.php?t=110843&page=11](http://ubuntuforums.org/showthread.php?t=110843&page=11))

but, Apani has come out with a Beta version 3.6. (April 30, 2009)
I'm a Beta tester,
and it works fine "out of the box" on HardyHeron (which Apani will support now).
No longer have to change persmissions on several files, add that space, or need edits for the nlvcard.c files, etc. Still have to change the scripts to use bash. (and more edits if you plan on debian-izing the .tar file)
I've done minimal testing with more to follow.

Apani does support Intrepid, but I will not be testing on that platform.

The product also runs on JauntyJackelope (after compiling on that platform, of course). 
I've done minimal testing on that platform, but more to follow.

Note: Apani does NOT support the JauntyJackelope 9.04 platform.

I do not know when the GA will be available, but I imagine it will be in several weeks.

---

### Post by Zeratul7 on 2009-10-21
Where the hell is this 3.6 version? I have been waiting for years already to get it working.

---

### Post by Zeratul7 on 2009-10-22
Ok, I got the 3.6 working on my Jaunty. Well... at least for 10 seconds before total kernel freeze. I wonder if thiss will be fixed ever?

---

