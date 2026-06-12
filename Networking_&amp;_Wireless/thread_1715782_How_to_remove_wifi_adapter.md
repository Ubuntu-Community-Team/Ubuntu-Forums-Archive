---
title: "How to remove wifi adapter?"
date: 2011-03-27
forum: Networking &amp; Wireless
---

### Post by dBuster on 2011-03-27
Okay, I have an AWLL5088 Airlink 101 usb micro adapter which is wireless N capable.  I do have some N networks that I could use the benefit of this adapter for and know how to get it installed.

My question though is, I want to be able to uninstall this wireless N adapter and go solely with the internal wifi adapter how would I do that?  

The following is the install script for the Airlink101 adapter:

```

#!/bin/bash
# Writed by Realtek : willisTang
# September, 1 2010 v 1.0.0
###########################################################################
echo "		Auto install for 8192cu"
echo "		September, 1 2010 v 1.0.0"
cd driver
Drvfoulder=`ls |grep .tar.gz`
tar zxvf $Drvfoulder
Drvfoulder=`ls |grep -iv '.tar.gz'`
echo "$Drvfoulder"
cd  $Drvfoulder
echo "Authentication requested [root] for make driver:"
if [ "`uname -r |grep fc`" == " " ]; then
	sudo su -c make; Error=$?
else	
	su -c make; Error=$?
fi
module=`ls |grep -i 'ko'`
if [ "$Error" != 0 ];then
	echo "Compile make driver error: $Error, Please check error Mesg"
	read REPLY
	exit
else
	echo "Compile make driver ok!!"	
fi
if [ "`uname -r |grep fc`" == " " ]; then
	echo "Authentication requested [root] for remove driver:"
	sudo su -c "rmmod $module"
	echo "Authentication requested [root] for insert driver:"
	sudo su -c "insmod $module"
	echo "Authentication requested [root] for install driver:"
	sudo su -c "make install"
else
	echo "Authentication requested [root] for remove driver:"
	su -c "rmmod $module"
	echo "Authentication requested [root] for insert driver:"
	su -c "insmod $module"
	echo "Authentication requested [root] for install driver:"
	su -c "make install"
fi
echo "################################################################"
echo "The Setup Script is completed !"
echo "Plese Press any keyword to exit."
read REPLY
echo "################################################################"

```

I see in the install where it looks like it removes the driver and then installs it so I am sure I am looking for something along those remove lines in order to take the wireless N adapter out of the setup.

I remember when I setup the wireless N adapter under Jaunty I could only have one installed at a time and when I wanted to go back to the internal I just ran the madwifi drivers as that is how I got the internal atheros to work.  Now with Lucid the internals worked out of the box fresh install so I am a little leery...

Thanks in advance.

---

### Post by dBuster on 2011-03-30
nobody wants to take a stab at this question?

Once installed how to remove a driver???  Blacklist it?  If so where?  How???

---

