---
title: "Solution to: How to have multiple different Xorg.conf's"
date: 2008-01-16
forum: Multimedia &amp; Video
---

### Post by Zugzwang on 2008-01-16
Hi all,

I've noticed that quite a couple of Ubuntu users have the same problem I had, but no real solution was ever posted here. I'm presenting one here and hopefully that helps anyone.

I've got the following setting:
[LIST]
[*]My laptop has a 1280x800 internal screen which I'm using when travelling
[*]I've also got a nice 1280x1024 LCD screen at home which I'm using as replacement whenever I'm at home
[/LIST]

The problem is that Ubuntu doesn't detect which is the case when booting. **By using the following solution, I can now manually choose from a list of possible X-server configurations which to use during booting**. 

_How to install the solution_
[LIST=1]
[*]First of all, create a Xorg.conf file for one of the settings (if you don't have one already). The most common way to do so is to do:
```
sudo su
dpkg-reconfigure xserver-xorg

```
Then create a directory for all of your possible configuration files:
```
mkdir /etc/X11/selection
```
Finally copy your current configuration file to the newly created directory and give it a good name. In this case, I name it after the resolution used.
```
cp /etc/X11/Xorg.conf /etc/X11/selection/Xorg.conf.1280x800
```
[*] Now shut the computer down, attach the other screen and boot again (in Ubuntu's "safe mode" so that the X-Server doesn't start). Depending of the differences between **your** desired configurations, you may not have to do so. Then we apply the same procedure to create the new configuration file:
```

dpkg-reconfigure xserver-xorg
cp /etc/X11/Xorg.conf /etc/X11/selection/Xorg.conf.1280x1024
```
If you don't bootup in safe mode, you will have to execute
```
sudo su 
```
beforehand.
[*]Now we have configuration files for each of the settings. What we need is the possibility to choose one during the boot process. To make things easier, I suggest starting the desktop at this point:
```

startx
```
Then open a terminal and type:
```

gedit /etc/etc/init.d/bootup.displayconfig
```
Make sure to switch to the root user beforehand if you aren't at that point ("sudo su" again). Copy the contents of the following script into the file:
[PHP]
#!/bin/bash

if [ "$1" = "start" ]
then
 echo "=============================================="
 echo " Select your screen configuration:"
 echo ""
 echo " [1] 1280x800   -  Laptop mode"
 echo " [2] 1280x1024  -  Desktop mode"
 echo "=============================================="
 DONE=0

 while [ "$DONE" = 0 ]; do
  read -s -n 1 VIDEO
  if [ "$VIDEO" = 1 ]; then
   echo "Selected Laptop Mode!"
   cp -f /etc/X11/selection/xorg.conf.1280x800 /etc/X11/xorg.conf
   DONE=1
  elif [ "$VIDEO" = 2 ]; then
   echo "Selected Desktop Mode!"
   cp -f /etc/X11/selection/xorg.conf.1280x1024 /etc/X11/xorg.conf
   DONE=1
  else
   echo "Incorrect number"
  fi
 done
fi[/PHP]
Save the script and close the editor. We need to make it executable before it can work:
```

chmod 755 /etc/init.d/bootup.displayconfig
```
[*] Finally, we install the script into the booting process. This is done using the command:
```

update-rc.d bootup.displayconfig start 18 2 .
```
[/LIST]

That's it. Of course you have to adjust the script for your personal settings, but it should be pretty straight-forward how to change it accordingly. Note that you can uninstall the stuff by invoking:
```

update-rc.d -f bootup.displayconfig remove

```
This is recommended before upgrading your system. Make sure that you also delete the file "bootup.displayconfig" and the "selection" directory from /etc/X11 in that case.

Notes for the experts:
[LIST]
[*]Would you please confirm that the runlevel 2 is an appropriate point in the boot order process. Order number 18 is before cups and the nvidia stuff is started (at least on my system).
[*]If some shell scripting expert wrote a script that automatically scans the "selection" directory and shows all possible choices, that would simplify the installation.
[/LIST]

Hopefully future versions of Ubuntu come with build-in support for multiple configurations.

P.S. I know that there exists a switch-statement for bash scripts. ;)

---

### Post by heindsight on 2008-01-16
Interesting, but I think there may be a simpler solution.
When I switched from SuSE to Ubuntu I was looking for something similar to SCPM (SuSE Configuration Profile Manament) which can do what you want and more. Somewhere on a mailing
list someone mentioned switchconf (which is available in the Universe section of the repos) which
> 
allows users to easily change their system's settings, choosing between the possible configurations for different environments 

I ended up deciding that I don't really need it, so I haven't actually used it, but according to [this]("http://pwet.fr/man/linux/administration_systeme/switchconf"), it's perfect for what you want to do.

You can put each of your xorg.conf files in a different switchconf scheme, and then have a boot script which lists all the configuration schemes, prompts the user to choose one and then switches to that configuration. You could even write a script that parses the kernel parameters (looking for something like say: switchconf=<scheme>) to look for a configuration scheme to switch the system to.

EDIT:
OK, it looks like you wouldn't even have to write a script at all. The switchconf package in the repos includes an initscript which parses the kernel command line looking for a switchconf=<scheme> argument
and switches the configuration accordingly. So all you'd need to do is set up switchconf with different schemes for your X configurations, and then edit /boot/menu.lst

---

### Post by Keith Hedger on 2008-01-16
This is a general purpose script i use when i need to select from a list of files from the terminal maybe you can use it```

#!/bin/bash
cd /SOME/DIRECTORY
FILENAME=*
lst=$FILENAME
array=( $lst )

cnt=0
for fil in $lst ; do
echo $cnt $fil
(( cnt += 1 ))
done

echo Choose?
read sel

echo ${array[$sel]}

```
just change the cd and the FILENAME pattern to suit

---

### Post by mintar on 2008-02-05
Very nice! I tried this and it works great. I've written my own bootup.displayconfig, which checks if the lid is closed and makes its decisions based on that. Also, it checks the md5sum of the config files and refuses to overwrite the xorg.conf if it has changed:

```

#!/bin/bash

if [ "$1" = "start" ]
then
	ORIGINAL_MD5=`md5sum /etc/X11/xorg.conf | cut -d " " -f 1`
	DOCKED_MD5=`md5sum /etc/X11/selection/xorg.conf.docked | cut -d " " -f 1`
	UNDOCKED_MD5=`md5sum /etc/X11/selection/xorg.conf.undocked | cut -d " " -f 1`

	grep -q closed /proc/acpi/button/lid/*/state
	if [ $? = 0 ]
	then
		# assume docked mode
		if [ $ORIGINAL_MD5 = $DOCKED_MD5 ]
		then
			# nothing to do
			/bin/true
		elif [ $ORIGINAL_MD5 = $UNDOCKED_MD5 ]
		then
			cp -f /etc/X11/selection/xorg.conf.docked /etc/X11/xorg.conf
		else
			echo "!!! xorg.conf was changed, will not overwrite it !!!"
		fi
	else
		# assume undocked mode
		if [ $ORIGINAL_MD5 = $DOCKED_MD5 ]
		then
			cp -f /etc/X11/selection/xorg.conf.undocked /etc/X11/xorg.conf
		elif [ $ORIGINAL_MD5 = $UNDOCKED_MD5 ]
		then
			# nothing to do
			/bin/true
		else
			echo "!!! xorg.conf was changed, will not overwrite it !!!"
		fi
	fi
fi

```

---

