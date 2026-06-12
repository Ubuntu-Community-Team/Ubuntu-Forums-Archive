---
title: "[SOLVED] How to install Mudbox 2017 on Ubuntu 16.04 LTS - in 2 easy steps"
date: 2017-08-20
forum: Multimedia Software
---

### Post by bvz on 2017-08-20
Hi,

I have finally (mostly) successfully installed Mudbox on my Ubuntu 16.04 LTS system.  Most of this work was done by others, but it was either not completely functional, or it was for debian and not Ubuntu specifically.  Most of this came from:  [https://gist.github.com/Sunderland93/5d879651996f7d6fd4e58182e6eacf70](https://gist.github.com/Sunderland93/5d879651996f7d6fd4e58182e6eacf70) and all of the credit goes to him.  I have just modified it a tiny bit for Ubuntu.

So here is a compilation of the steps that I did in order to get it to work.

1) Download your legal copy of Mudbox.  Seriously, don't pirate this.  It is free if you are a student or teacher, and only $70 a year if you aren't.  As a part of this you will get a serial number.  You will need this. After you download it, copy the downloaded file to:  /tmp/mudboxTempInstall/Autodesk_Mudbox_2017_EFGJ_Linux64.tgz

2) Run the following script. Note: this may take a while to run, don't give up on it. On my system (Dual hexacore Xeon x5675) it takes about 20 minutes and several times looks like it has hung.  So be patient with it.

```
#!/bin/bash
#2016 Aleksey Samoilov aka Sunderland93
#samoilov.lex@gmail.com

# This script assumes that you have downloaded your copy of the mudbox.tgz to /tmp/mudboxTempInstall, and that it is named: Autodesk_Mudbox_2017_EFGJ_Linux64.tgz


#Setup a few vars (Change the file name here if your .tgz file has a different name)
#Also change the PRODUCTID if you are not installing Mudbox 2017 (for example, Mudbox 2016 has a PRODUCTID 498G1)
export MUDBOXINSTALL='mudboxTempInstall'
export INSTALLFILE="Autodesk_Mudbox_2017_EFGJ_Linux64.tgz"
export RPM_INSTALL_PREFIX=/usr
export LD_LIBRARY_PATH=/opt/Autodesk/Adlm/R12/lib64/
PRODUCTID="498I1"


if [ `whoami` != root ]; then
    echo Please run this script using sudo
    echo Just type &#8220;sudo !!&#8221;
    exit
fi
#Check for 64-bit arch
if [/bin/uname -m != x86_64]; then
    echo Mudbox will only run on 64-bit linux. 
    echo Please install the 64-bit ubuntu and try again.
    exit
fi


#Install Message
echo "You&#8217;re about to install Autodesk Mudbox 2017"
echo ""
echo "Do you wish to continue [Y/n]?"
read RESPONSE
case "$RESPONSE" in
	n*|N*)
	echo "Install Terminated"
	exit 0;
esac

#Get serial number
echo "Enter the serial number"
read SERIALNUMBER
echo ""

export INSTALLDIR=/tmp/$MUDBOXINSTALL
cd $INSTALLDIR
sudo chmod -R 777 $INSTALLDIR

# Install Dependencies
sudo apt-get install csh tcsh libaudiofile-dev libglw1-mesa elfutils gamin libglw1-mesa-dev mesa-utils xfstt ttf-liberation ttf-mscorefonts-installer xfonts-100dpi xfonts-75dpi alien libgstreamer0.10-dev libgstreamer-plugins-base0.10-dev libtiff5 openssl
sleep 3s


# Extract Mudbox Install Files
tar xvf $INSTALLDIR/$INSTALLFILE
# Convert rpms to debs
for i in $INSTALLDIR/*.rpm; do sudo alien -cv $i; done
sleep 2s
#install the debs
sudo dpkg -i $INSTALLDIR/*.deb

#Required for license to install
sudo cp libadlmPIT.so.11 /usr/lib/libadlmPIT.so.11
sudo cp libadlmutil.so.11 /usr/lib/libadlmutil.so.11
sudo ln -s /usr/lib/libadlmPIT.so.11 /usr/lib/libadlmPIT.so
sudo ln -s /usr/lib/libadlmutil.so.11 /usr/lib/libadlmutil.so

# License Setup:
sudo echo -e 'MUDBOX_LICENSE=unlimited\nMUDBOX_LICENSE_METHOD=standalone' > /usr/autodesk/mudbox2017/bin/License.env
#Notice the lack of sudo.
/usr/autodesk/mudbox2017/bin/adlmreg -i S $PRODUCTID $PRODUCTID 2017.0.0.F $SERIALNUMBER /var/opt/Autodesk/Adlm/Mudbox2017/MudboxConfig.pit
 
# symbolic links:
# libtiff
sudo ln -s /usr/lib/x86_64-linux-gnu/libtiff.so.5.2.0 /usr/lib/libtiff.so.3
sleep 2s

# check to see if libtiff.so.3 exists
if [ ! -e /usr/lib/x86_64-linux-gnu/libtiff.so.3 ]; then
	if [ ! -e /usr/lib/x86_64-linux-gnu/libtiff.so.5 ]; then
		echo "=========================================================================================="
		echo "Cannot locate libtiff.so.3 OR libtiff.so.5"
		echo "You will need to find a version of libtiff somewhere and make a symlink from /usr/lib/x86_64-linux-gnu/libtiff.so.3 to point to that file."
		echo "Normally libtiff libraries live in /usr/lib/x86_64-linux-gnu/"
		echo "So, go to that dir and see if you can find a version of libtiff.so.<some value here>"
		echo "Then make a symlink to that file by using the command:"
		echo "sudo ln -s <path to the libtiff file you found above> /usr/lib/x86_64-linux-gnu/libtiff.so.3"
		echo "For example: sudo ln -s /usr/lib/x86_64-linux-gnu/libtiff.so.5 /usr/lib/x86_64-linux-gnu/libtiff.so.3"
		echo "Good luck!"
		echo "=========================================================================================="
	else
		sudo ln -s /usr/lib/x86_64-linux-gnu/libtiff.so.5 /usr/lib/x86_64-linux-gnu/libtiff.so.3
	fi
fi
 
#Everything should work now... 
echo "Installation Complete."
echo ""
echo "Start Mudbox Now?"
read RUNNOW
case "$RUNNOW" in
	n*|N*)
	echo "You can run mudbox any time by typing mudbox into the terminal"
	exit 0;
esac
mudbox
```




That should be it!  Let me know if you have any questions and I will try to help... but know that I am pretty knew to all of this myself.  I got it working on my machine, and there is no guarantee that it will work for yours.

Good luck!

Edit:

There is a slightly updated version of the script below.  Use that one instead (though it shouldn't actually run all that differently).

---

### Post by vocx on 2017-08-20
> **bvz said:**
> Hi,

I have finally (mostly) successfully installed Mudbox on my Ubuntu 16.04 LTS system.  Most of this work was done by others, but it was either not completely functional, or it was for debian and not Ubuntu specifically.  Most of this came from:  [https://gist.github.com/Sunderland93/5d879651996f7d6fd4e58182e6eacf70](https://gist.github.com/Sunderland93/5d879651996f7d6fd4e58182e6eacf70) and all of the credit goes to him.  I have just modified it a tiny bit for Ubuntu.

So here is a compilation of the steps that I did in order to get it to work.

1) Download your legal copy of Mudbox.  Seriously, don't pirate this.  It is free if you are a student or teacher, and only $70 a year if you aren't.  As a part of this you will get a serial number.  You will need this. After you download it, copy the downloaded file to:  /tmp/mudboxTempInstall/Autodesk_Mudbox_2017_EFGJ_Linux64.tgz

2) Run the following script. Note: this may take a while to run, don't give up on it. On my system (Dual hexacore Xeon x5675) it takes about 20 minutes and several times looks like it has hung.  So be patient with it.

```
...
if [ `whoami` != root ]; then
    echo Please run this script using sudo
    echo Just type “sudo !!”
    exit
fi
...
sudo chmod -R 777 $INSTALLDIR

```

At the beginning of the script, you check if the script is being run with root privileges, that is, "sudo". If it is not run with "sudo", the script terminates.

Later on you run many commands like "chmod" and "apt-get install". If the `whoami` test was successful, these commands are already using "sudo", so you don't need to put it here any more. In general, inside scripts you should not put "sudo" anywhere. You should make sure the script is started with "sudo", and later on just assume the permissions are there.

Remember that "sudo" has a timer. After giving the password, you don't need to give the password again for 10 minutes or so. But after that, if you use "sudo" again, you need to enter the password again. This can break a long running script. That is, maybe at the beginning you give the "sudo" password once, and later on you have to give it again, but if you are away from the computer and don't give it again, the script will just sit there, waiting for input and won't proceed to the next line. Thus, why I mention: once you start the script with "sudo", you don't use "sudo" again inside the script.

---

### Post by bvz on 2017-08-22
> **vocx said:**
> At the beginning of the script, you check if the script is being run with root privileges, that is, "sudo". If it is not run with "sudo", the script terminates.

Later on you run many commands like "chmod" and "apt-get install". If the `whoami` test was successful, these commands are already using "sudo", so you don't need to put it here any more. In general, inside scripts you should not put "sudo" anywhere. You should make sure the script is started with "sudo", and later on just assume the permissions are there.

Remember that "sudo" has a timer. After giving the password, you don't need to give the password again for 10 minutes or so. But after that, if you use "sudo" again, you need to enter the password again. This can break a long running script. That is, maybe at the beginning you give the "sudo" password once, and later on you have to give it again, but if you are away from the computer and don't give it again, the script will just sit there, waiting for input and won't proceed to the next line. Thus, why I mention: once you start the script with "sudo", you don't use "sudo" again inside the script.

Thanks for taking the time to look at the script.  Everything you mention makes sense to me (after a few readings).  As I mentioned, this was originally a script that I modified from another source.  That said, armed with my newfound knowledge (thanks!), here is an updated version of the script:

```
#!/bin/bash
#2016 Aleksey Samoilov aka Sunderland93
#samoilov.lex@gmail.com

# This script assumes that you have downloaded your copy of the mudbox.tgz to /tmp/mudboxTempInstall, and that it is named: Autodesk_Mudbox_2017_EFGJ_Linux64.tgz


#Setup a few vars (Change the file name here if your .tgz file has a different name)
#Also change the PRODUCTID if you are not installing Mudbox 2017 (for example, Mudbox 2016 has a PRODUCTID 498G1)
export MUDBOXINSTALL='mudboxTempInstall'
export INSTALLFILE="Autodesk_Mudbox_2017_EFGJ_Linux64.tgz"
export RPM_INSTALL_PREFIX=/usr
export LD_LIBRARY_PATH=/opt/Autodesk/Adlm/R12/lib64/
PRODUCTID="498I1"


if [ `whoami` != root ]; then
    echo Please run this script using sudo
    echo Just type “sudo !!”
    exit
fi
#Check for 64-bit arch
if [/bin/uname -m != x86_64]; then
    echo Mudbox will only run on 64-bit linux. 
    echo Please install the 64-bit ubuntu and try again.
    exit
fi


#Install Message
echo "You’re about to install Autodesk Mudbox 2017"
echo ""
echo "Do you wish to continue [Y/n]?"
read RESPONSE
case "$RESPONSE" in
	n*|N*)
	echo "Install Terminated"
	exit 0;
esac

#Get serial number
echo "Enter the serial number"
read SERIALNUMBER
echo ""

export INSTALLDIR=/tmp/$MUDBOXINSTALL
cd $INSTALLDIR
chmod -R 777 $INSTALLDIR

# Install Dependencies
apt-get install csh tcsh libaudiofile-dev libglw1-mesa elfutils gamin libglw1-mesa-dev mesa-utils xfstt ttf-liberation ttf-mscorefonts-installer xfonts-100dpi xfonts-75dpi alien libgstreamer0.10-dev libgstreamer-plugins-base0.10-dev libtiff5 openssl
sleep 3s


# Extract Mudbox Install Files
tar xvf $INSTALLDIR/$INSTALLFILE
# Convert rpms to debs
for i in $INSTALLDIR/*.rpm; do alien -cv $i; done
sleep 2s
#install the debs
dpkg -i $INSTALLDIR/*.deb

#Required for license to install
cp libadlmPIT.so.11 /usr/lib/libadlmPIT.so.11
cp libadlmutil.so.11 /usr/lib/libadlmutil.so.11
ln -s /usr/lib/libadlmPIT.so.11 /usr/lib/libadlmPIT.so
ln -s /usr/lib/libadlmutil.so.11 /usr/lib/libadlmutil.so

# License Setup:
echo -e 'MUDBOX_LICENSE=unlimited\nMUDBOX_LICENSE_METHOD=standalone' > /usr/autodesk/mudbox2017/bin/License.env

/usr/autodesk/mudbox2017/bin/adlmreg -i S $PRODUCTID $PRODUCTID 2017.0.0.F $SERIALNUMBER /var/opt/Autodesk/Adlm/Mudbox2017/MudboxConfig.pit
 
# symbolic links:
# libtiff
ln -s /usr/lib/x86_64-linux-gnu/libtiff.so.5.2.0 /usr/lib/libtiff.so.3
sleep 2s

# check to see if libtiff.so.3 exists
if [ ! -e /usr/lib/x86_64-linux-gnu/libtiff.so.3 ]; then
	if [ ! -e /usr/lib/x86_64-linux-gnu/libtiff.so.5 ]; then
		echo "=========================================================================================="
		echo "Cannot locate libtiff.so.3 OR libtiff.so.5"
		echo "You will need to find a version of libtiff somewhere and make a symlink from /usr/lib/x86_64-linux-gnu/libtiff.so.3 to point to that file."
		echo "Normally libtiff libraries live in /usr/lib/x86_64-linux-gnu/"
		echo "So, go to that dir and see if you can find a version of libtiff.so.<some value here>"
		echo "Then make a symlink to that file by using the command:"
		echo "sudo ln -s <path to the libtiff file you found above> /usr/lib/x86_64-linux-gnu/libtiff.so.3"
		echo "For example: sudo ln -s /usr/lib/x86_64-linux-gnu/libtiff.so.5 /usr/lib/x86_64-linux-gnu/libtiff.so.3"
		echo "Good luck!"
		echo "=========================================================================================="
	else
		ln -s /usr/lib/x86_64-linux-gnu/libtiff.so.5 /usr/lib/x86_64-linux-gnu/libtiff.so.3
	fi
fi
 
#Everything should work now... 
echo "Installation Complete."
echo ""
echo "Start Mudbox Now?"
read RUNNOW
case "$RUNNOW" in
	n*|N*)
	echo "You can run mudbox any time by typing mudbox into the terminal"
	exit 0;
esac
mudbox
```


My one question is with regard to the line in the original script that specifically is called out to NOT run with sudo privileges.  It is the line that reads:

```
/usr/autodesk/mudbox2017/bin/adlmreg -i S $PRODUCTID $PRODUCTID 2017.0.0.F $SERIALNUMBER /var/opt/Autodesk/Adlm/Mudbox2017/MudboxConfig.pit
```

I can't see where running it with sudo privileges would cause any problems, but I am not sure.

---

