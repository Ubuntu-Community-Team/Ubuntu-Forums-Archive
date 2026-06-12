---
title: "HOWTO: YES! There IS an easy, safe way of reloading Xorg.conf without shutting down X"
date: 2008-01-26
forum: Multimedia &amp; Video
---

### Post by motin on 2008-01-26
I feel that there is a massively wide-spread belief that display settings in X cannot applied without having to shut down all running applications. 

All tutorials, howtos and forum replies that mentions reloading X configuration seem to recommend either pressing Ctrl + Alt + Backspace or Logging out and back in in order to restart X. Even if this is the most universally working method that requires the least amount of words to explain, THE CLASSIC Ctrl+Alt+Backspace METHOD IS VERY RISKY AND BY FAR THE QUICKEST NOR EASIEST WAY OF TESTING THE NEW CONFIGURATION. And, in case you are running Ubuntu Gutsy (or for that matter any modern distro using recent versions of X and Gnome) this quicker and safer way is easy as clicking "System -> Quit -> Switch User".

Some of the drawbacks with the classic recommendation:

[LIST=1]
[*]No graphical applications can be left running while trying out different display configurations
[*]In case the configuration doesn't work - the user is left into the hands of the rather unreliable X failsafe recovery software or even worse: no working graphical user interface at all
[*]It indicates that several X displays with separate configurations cannot run in parallell - and thus enforces the perception of that the generally used Linux display system is limited in nature and far behind the display systems of Mac OS X and/or Windows
[*]Especially, many new users that are wondering why their Fn + F4 laptop combination to switch video output modes are told that something like that just isn't possible with Linux computing.
[/LIST]

[SIZE="3"]Wouldn't you like to be able to:[/SIZE]

[LIST=1]
[*]Try out Xorg.conf changes without having to shutdown any applications?
[*]Try out Xorg.conf changes with a smaller risk of being forced to cope with a permanent black screen or have to resort to recovery mode in order to restore a working Xorg.conf configuration?
[*]Not have to choose between for different configurations (for instance Extended desktop, Cloned output, S-Video, drivers, input devices etc) - but instead be able to hot-switch between them when you see fit?
[*]Run a stable non-compiz desktop session for work while being able to quickly and safely switch to a compiz-enabled session in order to play around, show friends and to other tasks for which it doesn't matter if X locks up?
[/LIST]

Well, I am doing all of this without ever have had to resort to any complex command line voodoo. Everything is readily builtin and stable in Gutsy and called [Fast user switching]("http://fridge.ubuntu.com/node/1162"). Here's how:

**Preparation**
First we need to make it possible to login to a second X session. For this we need either to A. Add an extra user to the system, or B. Enable the option to allow multiple logins from the same user. 

*Alt A:*
Follow these instructions: [https://help.ubuntu.com/community/AddUsersHowto](https://help.ubuntu.com/community/AddUsersHowto)

*Alt B:*
Go to System -> Settings -> Login Window Preferences. Then untick the option "Disable multiple logins for a single user" and press Close. 

Now you are set and ready to do any of the tasks I mentioned:

[SIZE="5"]HOWTO: Try out xorg.conf changes without having to shutdown any applications and with a smaller risk of being forced to cope with a permanent black screen or have to resort to recovery mode in order to restore a working xorg.conf configuration[/SIZE]

Example:
1. Make a backup copy of the current xorg.conf (ALWAYS TO THIS!):
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.known-to-work
```
2. Alter xorg.conf in any appropriate way*. (Maybe run "dpkg-reconfigure xserver-xorg" to fix that missing resolution?)
3. Choose System -> Quit -> Switch User

A new X session will start on a second display, and you can now switch between them using the combination Ctrl + Alt + F7 to F12. (Normally, the default X session will be available on Ctrl + Alt + F7, and the second you start will be on Ctrl + Alt + F9)

If you are thrown back into your original session when attempting this - your new xorg.conf probably has an error in it! Check /var/log/Xorg.*.log (usually Xorg.20.log for this second display), and don't forget to restore your backup configuration before rebooting!

* A word of caution:
Some configurations in xorg.conf have the potential to lock your whole system (not only X) up. A  likely example being running two different X sessions with different Nvidia drivers (I've heard...). So use this methods only to try out modelines, changes to devices, resolutions and the likes and always go into maintenance mode (i.e. saving data and closing applications) before following these guidelines regardless.

[SIZE="5"]HOWTO: Not have to choose between for different configurations (for instance Extended desktop, Cloned output, S-Video, drivers, input devices etc) - but instead be able to hot-switch between them when you see fit[/SIZE]

If you use different X configuration files and want to use them in parallell - the trick is to start your first session with one of them, replace xorg.conf with an alternative version and then start a new X session. 

I just wrote a bash+zenity script that automates this process. Check out the screen-shots to get an idea of what it does.

Download:
Save the following to a file named "switchxconf":
```
#!/bin/bash

# switchxconf - Easily swap between X configuration files based on 
#               multiple copies of xorg.conf with different file endings
#
# Preparation:
# Put your X configuration files in /etc/X11/ using different file endings
# in the following style: /etc/X11/xorg.conf.FileEnding /etc/X11/xorg.conf.AnotherFileEnding
#
# Usage: ./switchxconf CONFIGURATION
#
# Where CONFIGURATION is the file ending of the configuration file to switch to 
# (for instance "FileEnding")
#
# If CONFIGURATION is not specified, a dialog will popup and let you choose an 
# appropriate X configuration file
#
# Requirements:
# Xorg 7.3 or later. Zenity for the dialogue.
# This script has been tested on an Ubuntu Gutsy laptop with Intel 915 GM 
# Graphics chipset, using driver i810 and various display configurations (Xinerama, 
# Cloned CRT, S-Video etc)
#
# Acknowledements and version history:
# v20080126 - Original version with the basic configuration selection, activation 
#             and backup functionality - Fredrik Wollsén
#
# License GPL v3
#
# Feel free to provide feedback on this script here:
# http://ubuntuforums.org/showthread.php?p=4211618
#
# Suggestions for improvements:
#  - Detect Gnome or KDE and if KDE is active - use kdialog instead of zenity.
#  - Integrate with a tool to generate different X configurations (xorg-edit for instance)
#    and add the option to add a configuration using this tool.
#
# THIS SOFTWARE IS PROVIDED BY THE AUTHOR ``AS IS'' AND ANY EXPRESS OR
# IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED
# WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE
# ARE DISCLAIMED. IN NO EVENT SHALL THE AUTHOR BE LIABLE FOR ANY
# DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL
# DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE
# GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS
# INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER
# IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR
# OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN
# IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.

# Settings:

X11_CONF_DIR=/etc/X11/;
ALWAYS_CREATE_BACKUP=0; # Set to 1 to always create a backup xorg.conf in X11_CONF_DIR before each switch (Note: a temporary backup to /tmp is always performed)

# Variables

TS=`date +'%Y%m%d-%H%M%S'`;
ZENITY_CMD_TMP_FILE=/tmp/switchxconf.zenity.$$.$TS.tmp;
CURRENT_XORGCONF_TMP_FILE=/tmp/switchxconf.xorg.$$.$TS.tmp;
CONFIGURATION=$1;

# Identify requested configuration

if [ "$CONFIGURATION" == "" ]; then

	CONFIGURATIONS=`find $X11_CONF_DIR -maxdepth 1 -name 'xorg.conf.*' | sort -f \
	| sed -r 's/\/etc\/X11\/xorg\.conf\.(.*)/"" "\\1"/g' | tee $ZENITY_CMD_TMP_FILE`;

	if [ "$CONFIGURATIONS" == "" ]; then

		echo "No available configurations were found. Please put your xorg.conf"
		echo "files in $X11_CONF_DIR with an additional file ending, for instance"
		echo "${X11_CONF_DIR}xorg.conf.Cloned-setup or ${X11_CONF_DIR}xorg.conf.Intel-test."

		exit 1;

	fi

	echo Found configurations: $CONFIGURATIONS;

	# Generate zenity selection script
	echo zenity --list --radiolist \
	 --title \"Change Display Mode\" \
	 --text \"Choose what configuration you want to activate.\" \
	 --height=300 \
	 --column \"\" --column \"File\" `cat $ZENITY_CMD_TMP_FILE` > $ZENITY_CMD_TMP_FILE;
	
	CONFIGURATION=`source $ZENITY_CMD_TMP_FILE`;

	# Remove tmpfile
	rm $ZENITY_CMD_TMP_FILE;

fi

if [ "$CONFIGURATION" == "" ]; then

	echo No configuration file chosen. Assumed program abort. Exiting...
	exit 0;

fi

echo Making sure that there is a backup of a working X configuration file...

BACKUPS=`find $X11_CONF_DIR -maxdepth 1 -name 'xorg.conf.known-to-work*'`;

if [ "$BACKUPS" == "" -o $ALWAYS_CREATE_BACKUP -gt 0 ] ; then

	echo None found - Creating backup...
	gksudo cp ${X11_CONF_DIR}xorg.conf ${X11_CONF_DIR}xorg.conf.known-to-work-$TS;
	echo Done!

else

	echo "Good - Found backup(s): $BACKUPS";

fi

# Always perform a backup of the current file to /tmp
cp ${X11_CONF_DIR}xorg.conf $CURRENT_XORGCONF_TMP_FILE;

echo Activating chosen configuration: \"$CONFIGURATION\" now;

gksudo cp ${X11_CONF_DIR}xorg.conf.$CONFIGURATION ${X11_CONF_DIR}xorg.conf;

APPLY_METHOD=`zenity --list --radiolist \
         --title "Active X Configuration changed!" \
         --text "How do you want to apply the new configuration?\n\nRemember that regardless of what method you \
choose here,\nthe newly activated configuration file will be the one\nused for the default session after a reboot. 
"\
	 --height=400 \
         --column "" --column "" --column "Choice" \
	"TRUE" 1 "Start a new X session in parallell (recommended)" \
	"" 2 "Log out the current session" \
	"" 3 "Kill X (forcingly shuts down the graphical interface)" \
	"" 4 "Do nothing right now (just leave as default boot option)"`;

#	"" 3 "Restart GNOME Display Manager (shuts down the graphical interface)" \

case "$APPLY_METHOD" in
      1          ) zenity --info --text "To return to this session, use one of the Ctrl + \
Alt + F7 to F12 key combinations (Try them one at a time until you arrive back to this session).\n\nRemember that you either need a second user to login with or enabled multiple logins for the same user (done in System -> Settings -> Login Window Preferences) in order to actually login using the new configuration.\n\nTip: If the newly activated configuration doesn't work at all - be sure to return to this session (before rebooting!) and either run \
this script again, choosing a working configuration, or restore your last configuration file found in \
$CURRENT_XORGCONF_TMP_FILE"\
 && gdmflexiserver;;
      2          ) gnome-session-save --kill --silent;;
      3          ) gksudo pkill Xorg;;
      4          ) echo "Doing nothing but exiting script...";;
      *          ) gksudo cp $CURRENT_XORGCONF_TMP_FILE ${X11_CONF_DIR}xorg.conf \
		   && zenity --info --text "Switch cancelled. Your previous X configuration has been restored.";;
esac

#      3          ) gksudo invoke-rc.d gdm restart;;   # Commenting because while it shuts down gdm, neither this nor "gksudo /etc/init.d/gdm restart" would bring gdm back up afterwards

exit 0;
```

And save the following to a file named "switchxconf.desktop":
```
[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Terminal=false
Exec=switchxconf
Name=Switch X Configuration
Icon=/usr/share/pixmaps/gnome-background.png
Categories=Application;System;
Hidden=false
```

Installation:
```

chmod +x switchxconf;
sudo cp switchxconf /usr/bin/;
sudo cp switchxconf.desktop /usr/share/applications/;
sudo apt-get install zenity;

```

Now, you should be able to click Applications -> System Tools ->Switch X Configuration in the GNOME Menu (you might need to logout and back in for it to show). 

You can also run "switchxconf" in a terminal.

Uninstallation:
```
rm /usr/bin/switchxconf;
rm /usr/share/applications/switchxconf.desktop;
```

Attached is my collection of X configuration files (attached). They are mostly for Intel 915GM cards, but should work with other Intel cards (like 945). All but the S-video versions are prepared to work with the Wiimote.
Thanks a million to featherking for his [original tutorial]("http://ubuntuforums.org/showthread.php?t=361124") on creating these config files.

[SIZE="5"]HOWTO: Make use of RandR 1.2 - or the ability to stick with one X configuration and dynamically add or remove screens and change display setups dynamically[/SIZE]

Basically if Gutsy is your first installation or you have run "dpkg-reconfigure xserver-xorg" using Gutsy - you will have a RandR 1.2 setup. Verify this by running "xrandr" in a terminal. If you get something like:

```
$ xrandr
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 2048 x 2048
VGA disconnected (normal left inverted right)
LVDS connected 1280x800+0+0 (normal left inverted right) 331mm x 207mm
   1280x800_60.00   60.0*+
   1280x800       60.0 +   60.0  
   1280x768       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
TV disconnected (normal left inverted right)

```

... then RandR 1.2 is active (it detects your output ports and whether or not there are screens attached). 

Here are some commands to get you started if you use a RandR based configuration (one is attached btw):

Turn on VGA-connected monitor output:
```
xrandr --output VGA --auto
```

Turn off VGA-connected monitor output:
```
xrandr --output VGA --off
```

Turn on Laptop monitor output:
```
xrandr --output LVDS --auto
```

Turn off Laptop monitor output:
```
xrandr --output LVDS --off
```

Change resolution on VGA-connected monitor:
```
xrandr --output VGA --mode "1024x768"
```

Setup extended desktop on VGA-connected monitor:
```
xrandr --output VGA --below LVDS
```

(You need to go with "below" because of a limit of a maximum 2048x2048 total resolution and still be able to use desktop effects)

Turn on S-Video (PAL color example):
```
xrandr --output TV --set TV_FORMAT PAL
```
```
xrandr --output TV --auto
```

Note: If the GNOME Panels are on the wrong screen, you can drag them to the correct screen. Where these show up after login is sadly yet not configurable. Hopefully the next version of GNOME will make it possible to take this into account on login.

---

### Post by Cyclops_ on 2008-01-27
Say... I don't have the "New Login" under Applications > System Tools.  Is there something I need to install for it?

Thanks

---

### Post by motin on 2008-01-29
> **Cyclops_ said:**
> Say... I don't have the "New Login" under Applications > System Tools.  Is there something I need to install for it?

Thanks

I have translated that from the Swedish translation and wasn't sure it was 100% correct. But, according to [this thread]("http://ubuntuforums.org/showthread.php?t=27965"), it is... and should be available in a default Gutsy installation. 

I am not sure what might be the issue. What you can do is use the script above as it will launch the New login command for you (gdmflexiserver).

---

### Post by archivator on 2008-01-29
Right click on the Applications menu -> Edit Menus -> System Tools -> make sure New Login has a tick in front of it.

---

### Post by eye208 on 2008-01-29
> **motin said:**
> THIS IS NO LONGER THE ONLY WAY IN CASE YOU ARE RUNNING UBUNTU GUTSY or for that matter any modern distro using recent versions of X and Gnome.
Running several instances of X has been possible for as long as I remember. All you need to do is switch to a tty console, then run e.g. "startx -- :1".

---

### Post by motin on 2008-01-29
> **eye208 said:**
> Running several instances of X has been possible for as long as I remember. All you need to do is switch to a tty console, then run e.g. "startx -- :1".

Yes, but when referring to easy I meant a stable method that doesn't involve switching to a tty console. Now it's plug-n-play :)

EDIT: I reworded that sentence in the OP now. Thanks for pointing it out.

---

### Post by motin on 2008-01-29
> **Cyclops_ said:**
> Say... I don't have the "New Login" under Applications > System Tools.  Is there something I need to install for it?

Thanks

> **archivator said:**
> Right click on the Applications menu -> Edit Menus -> System Tools -> make sure New Login has a tick in front of it.

Yeah I just realized that 1. archivator is correct - the choice isn't visible by default and 2. I was blind... there is a much easier way for which I have updated the tutorial: System -> Quit -> Switch User

Cheers!

---

### Post by eye208 on 2008-01-29
> **motin said:**
> Yes, but when referring to easy I meant a stable method that doesn't involve switching to a tty console. Now it's plug-n-play :)
There is nothing in your method that makes testing X.org configurations easier or safer than before. You wrote:
> Try out xorg.conf changes without having to shutdown any applications and without the risk of being forced to cope with a permanent black screen or have to resort to rescue mode in order to restore a working xorg.conf configuration
You are giving people a false sense of security encouraging them to make xorg.conf changes without going into maintenance mode, i.e. without saving data and closing applications. If someone tests a display driver this way, he may not be able to go back to the first instance of X in case of display corruption or freezing. Recovering the original xorg.conf file will still require him to use the recovery console. But unlike the conventional method, he may also have lost some application data due to the inevitable system restart.

The current X.org has not been designed to run with multiple configurations at once. The fact that you can trick it into doing so does not mean it's safe.

---

### Post by motin on 2008-02-13
> **eye208 said:**
> There is nothing in your method that makes testing X.org configurations easier or safer than before. You wrote:

You are giving people a false sense of security encouraging them to make xorg.conf changes without going into maintenance mode, i.e. without saving data and closing applications. If someone tests a display driver this way, he may not be able to go back to the first instance of X in case of display corruption or freezing. Recovering the original xorg.conf file will still require him to use the recovery console. But unlike the conventional method, he may also have lost some application data due to the inevitable system restart.

The current X.org has not been designed to run with multiple configurations at once. The fact that you can trick it into doing so does not mean it's safe.

Very true. I have updated my post accordingly. Thanks, man!

---

### Post by Ketahazure on 2008-04-04
Great How-to, thanks! dpkg-reconfigure xserver-xorg was one of the commands i had trouble with.

---

### Post by Kiri on 2008-04-10
Good tutorial. I have a couple of questions before I try it though:
1. Will it work with nvidia restricted drivers? I believe the randr method will not work with nvidia restricted drivers according to other posts I have seen...
2. Using the method of different xorg.conf and logging in multiple times, doesn't that mean that I will have to manage all my open applications seperately for each login?
I really want to find a way to switch on the fly between different setups..

---

