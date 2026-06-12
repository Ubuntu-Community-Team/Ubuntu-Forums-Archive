---
title: "Simple screensaver toggle"
date: 2008-06-22
forum: Multimedia Software
---

### Post by Labyrinth on 2008-06-22
**[COLOR="Red"]Please note: The newest version is [0.3](http://ubuntuforums.org/showpost.php?p=5452013&postcount=35)[/COLOR]**

Hello, everyone!

Since Miro does currently not disable the screen saver and I did not want to enter the screen saver dialog or move the mouse all that often, I wrote a simple toggle script.

It is intended to be used from the gnome panel, invoked with: "your/save/path/screensaver-toggle.py --toggle --gtk"


To add it to the panel, save the script to some location, probably in your home folder (which would make "your/save/path/" be "/home/your-login-name") and make it executable with "chmod u+x your/save/path/screensaver-toggle.py".

Then, right click the panel, select "Add to panel...", select "Custom application starter" (I am on a German machine, so those names are just my good guess) and click the "Add" button.

In the opening dialog, you can enter a name, like "Toggle Screensaver Idle Activation", the command "your/save/path/screensaver-toggle.py --toggle --gtk", changed to your actual path, and select a fitting icon, like "/usr/share/icons/Human/scalable/apps/kscreensaver.svg".

One click on the panel launcher will toggle the screensaver (from enabled to disabled, probably) and tell you about the current status.
When you're done with your video-app-that-does-not-handle-the-screensaver-properly, you'd just click it again to re-enable the screensaver.

The script is as follows:

[PHP]#!/usr/bin/python
# -*- coding: utf-8 -*-

# Licensed under the GPL
# Written by Klaus Bitto
# Version 0.1 from 2008-06-22

#    Screensaver toggle - simple toggle intended to be used from the gnome panel 
#    with "path/screensaver-toggle.py --toggle --gtk".
#    Copyright (C) 2008 Klaus Bitto (firstname.lastname@gmail.com)
#
#    This program is free software; you can redistribute it and/or modify
#    it under the terms of the GNU General Public License as published by
#    the Free Software Foundation; either version 2 of the License, or
#    (at your option) any later version.
#
#    This program is distributed in the hope that it will be useful,
#    but WITHOUT ANY WARRANTY; without even the implied warranty of
#    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#    GNU General Public License for more details.
#
#    You should have received a copy of the GNU General Public License
#    along with this program; if not, write to the Free Software
#    Foundation, Inc., 675 Mass Ave, Cambridge, MA 02139, USA.
#


import sys
import getopt
import gconf
import pygtk

pygtk.require('2.0')
import gtk


GCONF_KEY = "/apps/gnome-screensaver/idle_activation_enabled"

def activate_screensaver():
	return gconf.client_get_default().set_bool(GCONF_KEY, True)

def deactivate_screensaver():
	return gconf.client_get_default().set_bool(GCONF_KEY, False)

def toggle_screensaver():
	new_value = not get_screensaver_activation_status()
	return gconf.client_get_default().set_bool(GCONF_KEY, new_value)
	
def get_screensaver_activation_status():
	return gconf.client_get_default().get_bool(GCONF_KEY)

def print_screensaver_activation_status(use_gtk):
	status = "deactivated"
	message = "The screensaver deactivated.\n\nIt will NOT run, no matter how long you are idle."
	if get_screensaver_activation_status():
		status = "activated"
		message = "The screensaver activated.\n\nIt will run after a time out when you are idle."
		
	if use_gtk:
		dlg = gtk.MessageDialog(buttons=gtk.BUTTONS_OK,
				message_format=message)
		dlg.set_title("Screensaver %s" % status)
		dlg.run()
	else:
		print "Screensaver %s" % status
		print message

def print_usage():	
	print "Try using -a/--activate, -d/--deactivate, -t/--toggle or -s/--status."

def die():
	print_usage()
	sys.exit(2)

def main():
	try:
		opts, args = getopt.getopt(sys.argv[1:],"adtsg",["activate","deactivate","toggle","status","gtk"])
	except getopt.GetoptError:
		print "Wrong options given."
		die()
	
	if len(opts) < 1:
		print "No options given."
		die()
	
	show_message_dialog = False
			
	for opt,a in opts:
		if opt in ("-a","--activate"):
			activate_screensaver()
			
		if opt in ("-d","--deactivate"):
			deactivate_screensaver()
			
		if opt in ("-t","--toggle"):
			toggle_screensaver()
		
		if opt in ("-s","--status"):
			pass # Skip to printing status in the end, but wait for --gtk option first.
			
		# Fixme: -g or --gtk alone should throw an error and trigger die(). Instead, though, it acts like -s or --status.
		
		if opt in ("-g","--gtk"):
			show_message_dialog = True
			
	print_screensaver_activation_status(show_message_dialog)
	

if __name__ == "__main__":
	main()[/PHP]

Hope to make someone happy with this.

If you have some useful scripts, share them! =)

Happy ubuntuing, everyone!
-- Labyrinth

PS: After having read [ATTENTION ALL USERS: Malicious Commands]("http://ubuntuforums.org/announcement.php?f=334"), I think it would be useful if someone of a good name (an admin or mod) in this forum could "sign" this script to not be malicious. If you don't regard this as some kind of overkill.

---

### Post by Labyrinth on 2008-06-22
Somehow I was not paying attention for a moment.

So, please change "The screensaver deactivated." into "The screensaver is now deactivated.". 
The same for "The screensaver activated."...

---

### Post by Kulgan on 2008-07-17
That's a neat script! Definitely going to use that ^^
Thanks!

On a side note, do you know a command that will just "exit" from the screen saver - as if I had moved the mouse, so to speak. I'm thinking of things like download scripts. You finish a download and your screen goes back to normal kind of thing...

But either way, thanks!
-K

---

### Post by Labyrinth on 2008-07-17
Thanks!

I think you can artificially fire X events, like button clicks, etc... so I guess there's also a fake mouse move event. 
Or probably, there's something easier in the gnome libs, or perhaps you can send a dbus message to the gnome-screensaver process... 
Maybe google codesearch is a good start. ;) 
Can't tell more, though, sorry. I never needed this yet. 

PS: Of course you can just kill (-15) the screensaver process, but that might be a bit nasty. :D

---

### Post by Kulgan on 2008-07-17
Heh, I hadn't done my homework properly. xscreensaver-command is not around any more, since xscreensaver is not used on Gnome, but the equivalent is gnome-screensaver-command. I'm not sure whether it's --exit or -p I want, but it must be one of them. I'll do a few tests.

Oops! ;P

---

### Post by Labyrinth on 2008-07-17
Neither "gnome-screensaver --help" nor its man page mention anything...

---

### Post by Kulgan on 2008-07-17
That's cause it's not gnome-screensaver, it's gnome-screensaver-command.

So gnome-screensaver-command -p disactivates the screensaver without shutting down gnome-screensaver (so it will resume after another 10 minutes or whatever. Not sure wheter it will interrupt the blank screen (from power management settings), so am testing at the moment...

---

### Post by Labyrinth on 2008-07-18
Great! Tell me when you have results!

---

### Post by Kulgan on 2008-07-18
Sorry, went to sleep for a while there...

So -p will deactivate the screensaver. Yay. But it won't bring the screen to life if the power has been cut. 

-a and -d provide similar functionality to your code, allowing or preventing the screensaver to enable itself. 

--exit just shuts down gnome-screensaver, so that you have to start it again with "gnome-screensaver". 

Still looking for a way to override the powermanagement and turn the screen back on... I'll have a little poke around in the registry - gconf, I mean..

Edit:
Ok, so the thing that controls turning the screen off are the two keys
/apps/gnome-power-manager/timeout/sleep_display_ac and battery.

Changing them to 0 (the value it gets when the slider in the UI says "never") for a few seconds should get the screen back on, and it can then be set to it's original value. Get value, set to zero, sleep, poke with gnome-screensaver-command, restore value. Or something like that. Unfortuneately it's all XML, which goes beyond my bash skills. I can have a little go at it with your python, just to test, though. Brb ^^

---

### Post by Kulgan on 2008-07-18
Of course! This is Ubuntuforums, isn't it?

I'm working on it, but it's my first time with Python, and I don't know how to manipulate the gconf keys with anything else (other than editing the XML files directly with PHP). So it might take a while...

Labyrinth, if the code I produce is acceptable (and actually works), how about adding an option to your script, like -i/--interrupt sound? Just knocks the screen out of screensaver and power manager mode?

More to follow...

Oh, and is there a command to execute bash statements in Python? Something like PHP's system()?
Never mind, think I found it. subprocess.call("bash_command", shell=True), providing you have imported subprocess?

---

### Post by Labyrinth on 2008-07-18
You can invoke actions in gnome-power-manager via dbus ([GnomePowerManager FAQ]("http://live.gnome.org/GnomePowerManager/FAQ#head-ca9ddd6e2954f42fa6fb45b392ece499a6f8ab6f")), but it seems that you can only do the "hard" stuff, like hibernating, shutting down or locking the screen. 

The dbus interface description in the sources ([src/dbus/*.xml]("http://www.google.com/codesearch?hl=de&q=show:9K9Btj5lnEg:nAUdqsOGe0k&sa=N&ct=rdl&cs_p=http://ftp.gnome.org/pub/GNOME/desktop/2.18/2.18.0/sources/gnome-power-manager-2.18.0.tar.gz&cs_f=gnome-power-manager-2.18.0/src/dbus")) looks the same to me.

Since the screen blanking / powerOff is in gnome-power-preferences, not in gnome-screensaver-preferences, I'm still pretty sure that the power manager must be responsible for that.
(Also, the package descriptions says:
"gnome-power-manager manages [...] actions like:
  * [...]
  * Blank screen")



Maybe [src/gpm-idle.c]("http://www.google.com/codesearch?hl=de&q=show:T_AdS56epmc:UvLxxMC-Wk4:aRHrL_NyH6k&sa=N&ct=rd&cs_p=http://ftp.gnome.org/pub/GNOME/desktop/2.18/2.18.0/sources/gnome-power-manager-2.18.0.tar.gz&cs_f=gnome-power-manager-2.18.0/src/gpm-idle.c&start=1") helps.

Also, the [event watcher]("http://www.google.com/codesearch?hl=de&q=show:aI2GMtrQidg:ObUTkV20too:9Zy5SaQOH94&sa=N&ct=rd&cs_p=http://mirror.arcticnetwork.ca/pub/gentoo/distfiles/gnome-screensaver-2.18.1.tar.bz2&cs_f=gnome-screensaver-2.18.1/src/gs-watcher-x11.c&start=1") in gnome-screensaver could be interesting, since it shows how the screensaver notices what's going on around the desktop. (I still hope there's a dbus method, though.)

---

### Post by Labyrinth on 2008-07-18
> **Kulgan said:**
> -a and -d provide similar functionality to your code, allowing or preventing the screensaver to enable itself. 

Actually this doesn't seem to be true!

From [gnome-screensaver-command.c]("http://www.google.com/codesearch?hl=de&q=show:d85ChIXfauY:ObUTkV20too:5ThcAARRCJE&sa=N&ct=rd&cs_p=http://mirror.arcticnetwork.ca/pub/gentoo/distfiles/gnome-screensaver-2.18.1.tar.bz2&cs_f=gnome-screensaver-2.18.1/src/gnome-screensaver-command.c&start=1"):

```
static GOptionEntry entries [] = {
        [...]
        { "activate", 'a', 0, G_OPTION_ARG_NONE, &do_activate,
          N_("Turn the screensaver on (blank the screen)"), NULL },
        { "deactivate", 'd', 0, G_OPTION_ARG_NONE, &do_deactivate,
          N_("If the screensaver is active then deactivate it (un-blank the screen)"), NULL },
        { "poke", 'p', 0, G_OPTION_ARG_NONE, &do_poke,
          N_("Poke the running screensaver to simulate user activity"), NULL },
        [...]
};
```

So gnome-screensaver-command -a runs the screensaver right away instead of enabling it to run after an idle period.

To run the screensaver for 6 seconds, you can either run:
gnome-screensaver-command -a && sleep 6 && gnome-screensaver-command -d

or:
gnome-screensaver-command -a && sleep 6 && gnome-screensaver-command -p

Now I guess that -p does not unblank a screen after the powermanager did its work (that's what you tested, right?), but maybe -d does! Did you test it? (Testing it takes at least 12 minutes, since gnome-power-preferences doesn't want you to put the screen to black after less than 11 min :D)

---

### Post by Kulgan on 2008-07-18
Haha, you're posting to quickly for me to keep up ^^

Actually, you can make it blank after 2 mins if you turn the screensaver down to 1. Annoying though. 

I still don't think it will work though, since gnome-screensaver-command only seems to have control over the screen saver. As far as I have played with things, -d just stops it from going into screensaver mode in the first place, rather than kicking it out. Which is why I said is resebled your script in function. 

I'll give it a try though.. 1 min. Well, 3, really...

---

### Post by Labyrinth on 2008-07-18
No, you were right. (Actually, this could be a bug in gnome-screensaver-command!)

I set /apps/gnome-power-manager/timeout/sleep_display_ac to 10 using gconf-editor and ran both:
> gnome-screensaver-command -a && sleep 8 && gnome-screensaver-command -q && sleep 4 && gnome-screensaver-command -q && sleep 2 && gnome-screensaver-command -p

and 
> 
gnome-screensaver-command -a && sleep 8 && gnome-screensaver-command -q && sleep 4 && gnome-screensaver-command -q && sleep 2 && gnome-screensaver-command -d

Both print:
> Der Bildschirmschoner ist aktiv
Der Bildschirmschoner ist aktiv
(Which means that there is no difference between running screensaver and blanked screen - at least for "g-s-c --query".)

> 
Labyrinth, if the code I produce is acceptable (and actually works), how about adding an option to your script, like -i/--interrupt sound? Just knocks the screen out of screensaver and power manager mode?

--> Of course! This is Ubuntuforums, isn't it? ;)
I put it under GPL, after all... =)

---

### Post by Labyrinth on 2008-07-18
> **Kulgan said:**
> 1 min. Well, 3, really...

I was wrong about that. Since you can chose freely, using gconf-editor, you can blank the screen after 5 second, if you want.

> Get value, set to zero, sleep, poke with gnome-screensaver-command, restore value.

Are you sure this works?
For me, the screen doesn't get its power back with g-s-c [-d or -p] even when /apps/gnome-power-manager/timeout/sleep_display_ac is set to 0.

Code:
[PHP]def poke_screensaver():
	print "poking"
	client = gconf.client_get_default()
	ac_timeout = client.get_int(GCONF_KEY_SLEEP_DISPLAY_AC)
	bat_timeout = client.get_int(GCONF_KEY_SLEEP_DISPLAY_BAT)
	
	client.set_int(GCONF_KEY_SLEEP_DISPLAY_AC, 0)
	client.set_int(GCONF_KEY_SLEEP_DISPLAY_BAT, 0)
	
	print "Before trying to wake up:"
	print "AC: %s" % client.get_int(GCONF_KEY_SLEEP_DISPLAY_AC)
	print "Bat: %s" % client.get_int(GCONF_KEY_SLEEP_DISPLAY_BAT)
	
	subprocess.call(["gnome-screensaver-command","-d"])
	
	time.sleep(2) # in sec
	
	client.set_int(GCONF_KEY_SLEEP_DISPLAY_AC, ac_timeout)
	client.set_int(GCONF_KEY_SLEEP_DISPLAY_BAT, bat_timeout)
	print "poked"[/PHP]

Output:

> klaus@blaubeere:~/py/screensaver-toggle$ gnome-screensaver-command -a && sleep 10 && ./screensaver-toggle.py -p
poking
Before trying to wake up:
AC: 0
Bat: 0
poked
Screensaver activated
The screensaver is now activated.

It will run after a timeout when you are idle.
klaus@blaubeere:~/py/screensaver-toggle$ 

On screen:
- Electric Sheep (an amazing screensaver! You should try it!) starts up
- After 5 secs, the screen blanks
- Nothing else happens until I move the mouse. Actually, after 5 more seconds the screen should unblank again.

---

### Post by Labyrinth on 2008-07-18
There's a [bug report]("https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/213882") at launchpad since April 8th.

---

### Post by Kulgan on 2008-07-18
It disables it, but doesn't unblank the screen, is my interpretation:
```

$ sleep 3m && gnome-screensaver-command -q && gnome-screensaver-command -d && gnome-screensaver-command -q && gnome-screensaver-command -a && gnome-screensaver-command -q
The screensaver is active    (and screen is blank)
The screensaver is inactive   (and screen is blank)
The screensaver is active     (and screen is blank)

```

I don't think it's a bug so much as a part of it that just isn't there. I think there may be some comfusion of terms between gnome-screensaver and gnome-power-manager. For screensaver, "blank" means "screensaver on, dektop gone", but for power-manager, it means no power to screen. Or something like that. I dunno. 

In any case, here are some suggestions for the script. Basically the aim is to prevent the screen from blanking (ala power-manager) after whatever time it normally would have.
If there are things I'm doing wrong, please correct me. As I said, it's my first time with python.
For starters, this is what I did for the tests:
```

#!/usr/bin/python 
# -*- coding: utf-8 -*- 

import sys 
import getopt 
import gconf 
import pygtk 
import subprocess	# For issuing bash commands

pygtk.require('2.0') 
import gtk 

GCONF_KEY_AC 		= "/apps/gnome-power-manager/timeout/sleep_display_ac" 
GCONF_KEY_BATTERY 	= "/apps/gnome-power-manager/timeout/sleep_display_battery"

ac_status			= 0
battery_status		= 0

def read_values():
	# Store values of the two keys
	global ac_status
	global battery_status
	
	ac_status 		= gconf.client_get_default().get_int(GCONF_KEY_AC) 
	battery_status 	= gconf.client_get_default().get_int(GCONF_KEY_BATTERY) 
	return 0
	
def replace_values():
	gconf.client_get_default().set_int(GCONF_KEY_AC, 0)
	gconf.client_get_default().set_int(GCONF_KEY_BATTERY, 0)
	return 0
	
def wait_for_it():
	# Wait for a while before getting rid of the screensaver
	subprocess.call("sleep 3s", shell=True)
	subprocess.call("gnome-screensaver-command -q", shell=True)
	subprocess.call("gnome-screensaver-command -p", shell=True)
	subprocess.call("gnome-screensaver-command -q", shell=True)
	
def restore_values():
	# Set the keys back to their original values
	gconf.client_get_default().set_int(GCONF_KEY_AC, ac_status)
	gconf.client_get_default().set_int(GCONF_KEY_BATTERY, battery_status)
	return 0

def print_values():
	print "AC blank time:", 	 gconf.client_get_default().get_int(GCONF_KEY_AC)
	print "Battery blank time:", gconf.client_get_default().get_int(GCONF_KEY_BATTERY) 

def main():
	read_values()
	print_values()
	replace_values()
	print_values()
	wait_for_it()
	restore_values()
	print_values()
	return 0
	
if __name__ == "__main__": 
    main() 

```
(Not sure about exit codes, among other things - did it bash-style, 0 = success, but it doesn't really matter in this case anyway. 

Most of it is pointless, since it didn't work out, but I think the following could be used:
```

#!/usr/bin/python 
# -*- coding: utf-8 -*- 

# Licensed under the GPL 
# Written by Klaus Bitto 
# Version 0.1 from 2008-06-22 

#    Screensaver toggle - simple toggle intended to be used from the gnome panel  
#    with "path/screensaver-toggle.py --toggle --gtk". 
#    Copyright (C) 2008 Klaus Bitto (firstname.lastname@gmail.com) 
# 
#    This program is free software; you can redistribute it and/or modify 
#    it under the terms of the GNU General Public License as published by 
#    the Free Software Foundation; either version 2 of the License, or 
#    (at your option) any later version. 
# 
#    This program is distributed in the hope that it will be useful, 
#    but WITHOUT ANY WARRANTY; without even the implied warranty of 
#    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the 
#    GNU General Public License for more details. 
# 
#    You should have received a copy of the GNU General Public License 
#    along with this program; if not, write to the Free Software 
#    Foundation, Inc., 675 Mass Ave, Cambridge, MA 02139, USA. 
# 


import sys 
import getopt 
import gconf 
import pygtk 
import subprocess

pygtk.require('2.0') 
import gtk 

GCONF_KEY 	= "/apps/gnome-screensaver/idle_activation_enabled" 
AC_KEY 		= "/apps/gnome-power-manager/timeout/sleep_display_ac" 
BAT_KEY 	= "/apps/gnome-power-manager/timeout/sleep_display_battery"

AC_S		= 0
BAT_S		= 0

def read_pm_values():
	# Store values of the two keys
	global 	AC_S
	global 	BAT_S
	AC_S 	= gconf.client_get_default().get_int(GCONF_KEY_AC) 
	BAT_S 	= gconf.client_get_default().get_int(GCONF_KEY_BATTERY) 
	return 	1

def activate_screensaver(): 
	global AC_S
	global BAT_S
	gconf.client_get_default().set_int(AC_KEY,AC_S)
	gconf.client_get_default().set_int(BAT_KEY,BAT_S)
    return gconf.client_get_default().set_bool(GCONF_KEY, True) 

def deactivate_screensaver(): 
	# Stuff values in keys into bash vars
	subprocess.call("let TOGGLER_AC_S=",AC_S, shell=True)
	subprocess.call("let TOGGLER_BAT_S=",BAT_S, shell=True)
    return gconf.client_get_default().set_bool(GCONF_KEY, False) 

def toggle_screensaver(): # What you had here was sleek, but I couldn't fit the other stuff in.
    if get_screensaver_activation_status(): 
    	deactivate_screensaver()
    else:
    	activate_screensaver()
     
def get_screensaver_activation_status(): 
    return gconf.client_get_default().get_bool(GCONF_KEY) 

def print_screensaver_activation_status(use_gtk): 
    status = "deactivated" 
    message = "The screensaver deactivated.\n\nIt will NOT run, no matter how long you are idle." 
    if get_screensaver_activation_status(): 
        status = "activated" 
        message = "The screensaver activated.\n\nIt will run after a time out when you are idle." 
         
    if use_gtk: 
        dlg = gtk.MessageDialog(buttons=gtk.BUTTONS_OK, 
                message_format=message) 
        dlg.set_title("Screensaver %s" % status) 
        dlg.run() 
    else: 
        print "Screensaver %s" % status 
        print message 

def print_usage():     
    print "Try using -a/--activate, -d/--deactivate, -t/--toggle or -s/--status." 

def die(): 
    print_usage() 
    sys.exit(2) 

def main(): 
    try: 
        opts, args = getopt.getopt(sys.argv[1:],"adtsg",["activate","deactivate","toggle","status","gtk"]) 
    except getopt.GetoptError: 
        print "Wrong options given." 
        die() 
     
    if len(opts) < 1: 
        print "No options given." 
        die() 
    
    read_pm_values()
    
    show_message_dialog = False 
             
    for opt,a in opts: 
        if opt in ("-a","--activate"): 
            activate_screensaver() 
             
        if opt in ("-d","--deactivate"): 
            deactivate_screensaver() 
             
        if opt in ("-t","--toggle"): 
            toggle_screensaver() 
         
        if opt in ("-s","--status"): 
            pass # Skip to printing status in the end, but wait for --gtk option first. 
             
        # Fixme: -g or --gtk alone should throw an error and trigger die(). Instead, though, it acts like -s or --status. 
         
        if opt in ("-g","--gtk"): 
            show_message_dialog = True 
             
    print_screensaver_activation_status(show_message_dialog) 
     

if __name__ == "__main__": 
    main() 

```

It looks really messy. Might just be better to go with yours :/ I think there may be a problem with the bash variables, as well. It's throwing an indentation error I don't understand, as well, so I can't test it. But it's a start, if you want to use it.

---

### Post by Kulgan on 2008-07-18
Argh, too slow. 

So yes, it is a bug. I'm not going to dare do anything about it, though. Not that high up :P

I think I have an idea. I'll go back to your original version of the script, then forget all about everything else...

Would be nice to get it working though...

---

### Post by Labyrinth on 2008-07-18
> It disables it, but doesn't unblank the screen

Very good (and important) observation!

> Basically the aim is to prevent the screen from blanking (ala power-manager) after whatever time it normally would have.

That's easy: Just set /apps/gnome-power-manager/timeout/sleep_display_ac = 0 (like you said yourself).
But wasn't the actual aim to *unblank* the screen when it has powered off by calling screensaver-toggle.py --poke ?

About your code: I don't really understand a lot of it. What do you need the environment variables for? (You aren't using them anywhere, anyway...) [PS: Now I got it. Of course you can't store them inside the script variables. I'll try using gconf for that.]

---

### Post by Labyrinth on 2008-07-18
Version 0.2, should work... (at least it sets the values in gconf correctly. I'll test it during the week.)

[PHP]#!/usr/bin/python
# -*- coding: utf-8 -*-

# Licensed under the GPL
# Written by Klaus Bitto
# Version 0.2 from 2008-07-18

# Version history:
# 
# 0.2 2008-07-18
# + disable screen blanking in power management when disabling the screensaver
#
# 0.1 2008-06-22
# Initial release


#    Screensaver toggle - simple toggle intended to be used from the gnome panel 
#    with "path/screensaver-toggle.py --toggle --gtk".
#    Copyright (C) 2008 Klaus Bitto (firstname.lastname@gmail.com)
#
#    This program is free software; you can redistribute it and/or modify
#    it under the terms of the GNU General Public License as published by
#    the Free Software Foundation; either version 2 of the License, or
#    (at your option) any later version.
#
#    This program is distributed in the hope that it will be useful,
#    but WITHOUT ANY WARRANTY; without even the implied warranty of
#    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#    GNU General Public License for more details.
#
#    You should have received a copy of the GNU General Public License
#    along with this program; if not, write to the Free Software
#    Foundation, Inc., 675 Mass Ave, Cambridge, MA 02139, USA.
#


import sys
import getopt
import gconf
import pygtk
import time
import subprocess

pygtk.require('2.0')
import gtk


GCONF_KEY_IDLE_ACTIVATION = "/apps/gnome-screensaver/idle_activation_enabled"
GCONF_KEY_SLEEP_DISPLAY_AC = "/apps/gnome-power-manager/timeout/sleep_display_ac"
GCONF_KEY_SLEEP_DISPLAY_BAT = "/apps/gnome-power-manager/timeout/sleep_display_battery"

GCONF_KEY_BACKUP_AC = "/apps/screensaver-toggle/sleep_display_ac"
GCONF_KEY_BACKUP_BAT = "/apps/screensaver-toggle/sleep_display_battery"

def activate_screensaver():
	client = gconf.client_get_default()
	# enable screensaver
	client.set_bool(GCONF_KEY_IDLE_ACTIVATION, True)
	# restore power management timeouts from backup, only if backup is set!
	# otherwise, default values (0) were returned and the original values overwritten. Which sucks.
	sleep_display_ac_value = client.get_without_default(GCONF_KEY_BACKUP_AC)
	if sleep_display_ac_value != None:
		client.set_int(GCONF_KEY_SLEEP_DISPLAY_AC, sleep_display_ac_value.get_int())
	sleep_display_bat_value = client.get_without_default(GCONF_KEY_BACKUP_BAT)
	if sleep_display_bat_value != None:
		client.set_int(GCONF_KEY_SLEEP_DISPLAY_BAT, sleep_display_bat_value.get_int())
	

def deactivate_screensaver():
	client = gconf.client_get_default()
	# disable screensaver
	client.set_bool(GCONF_KEY_IDLE_ACTIVATION, False)
	# backup power management timeouts
	client.set_int(GCONF_KEY_BACKUP_AC, client.get_int(GCONF_KEY_SLEEP_DISPLAY_AC))
	client.set_int(GCONF_KEY_BACKUP_BAT, client.get_int(GCONF_KEY_SLEEP_DISPLAY_BAT))
	# set power management timeouts to "Never blank screen"
	client.set_int(GCONF_KEY_SLEEP_DISPLAY_AC, 0)
	client.set_int(GCONF_KEY_SLEEP_DISPLAY_BAT, 0)
	

def toggle_screensaver():
	activated = get_screensaver_activation_status()
	if activated:
		deactivate_screensaver()
	else:
		activate_screensaver()
	
def get_screensaver_activation_status():
	return gconf.client_get_default().get_bool(GCONF_KEY_IDLE_ACTIVATION)

def print_screensaver_activation_status(use_gtk):
	status = "deactivated"
	message = "The screensaver is now deactivated.\n\nIt will NOT run, no matter how long you are idle."
	if get_screensaver_activation_status():
		status = "activated"
		message = "The screensaver is now activated.\n\nIt will run after a timeout when you are idle."
		
	if use_gtk:
		dlg = gtk.MessageDialog(buttons=gtk.BUTTONS_OK,
				message_format=message)
		dlg.set_title("Screensaver %s" % status)
		dlg.run()
	else:
		print "Screensaver %s" % status
		print message
		
def print_usage():	
	print "Try using -a/--activate, -d/--deactivate, -t/--toggle or -s/--status."

def die():
	print_usage()
	sys.exit(2)

def main():
	try:
		opts, args = getopt.getopt(sys.argv[1:],"adtsg",["activate","deactivate","toggle","status","gtk"])
	except getopt.GetoptError:
		print "Wrong options given."
		die()
	
	if len(opts) < 1:
		print "No options given."
		die()
	
	show_message_dialog = False
			
	for opt,a in opts:
		if opt in ("-a","--activate"):
			activate_screensaver()
			
		if opt in ("-d","--deactivate"):
			deactivate_screensaver()
			
		if opt in ("-t","--toggle"):
			toggle_screensaver()
		
		if opt in ("-s","--status"):
			pass # Skip to printing status in the end, but wait for --gtk option first.
			
		# Fixme: -g or --gtk alone should throw an error and trigger die(). Instead, though, it acts like -s or --status.
		
		if opt in ("-g","--gtk"):
			show_message_dialog = True
			
	print_screensaver_activation_status(show_message_dialog)
	

if __name__ == "__main__":
	main()[/PHP]

Now that I think about it, though, I think all of that was crap, since previously (with only disabling the screensaver but not the screen power management) the screen was not powered off, either. So I solved a problem that wasn't there in the first place... Oh hell :rolleyes:


:lolflag:

---

### Post by Labyrinth on 2008-07-18
Actually, there is a dbus interface for disabling the screensaver - which e.g. totem [uses when playing movies]("http://svn.gnome.org/viewvc/totem/trunk/lib//totem-scrsaver.c?view=markup").

The screensaver is UnInhibited once the Inhibiting process ends, though. So this is no option for that small script.

> DBUS Service:	org.gnome.ScreenSaver
DBUS Object Path:	/org/gnome/ScreenSaver
DBUS Interface:	org.gnome.ScreenSaver

Inhibit

Request that saving the screen due to system idleness be blocked until UnInhibit is called or the calling process exits.
Direction	Type	Description
in	string	the application name, e.g. "totem"
in	string	the localized reason to inhibit, e.g. "playing movie"
out	unsigned integer	the cookie

A cookie is a random, unique, non-zero UINT32 used to identify the inhibit request.
UnInhibit

Cancel a previous call to Inhibit() identified by the cookie.
Direction	Type	Description
in	unsigned integer	the cookie

[http://svn.gnome.org/viewvc/gnome-screensaver/branches/gnome-2-22/doc/gnome-screensaver.html?view=log]("http://svn.gnome.org/viewvc/gnome-screensaver/branches/gnome-2-22/doc/gnome-screensaver.html?view=log")

---

### Post by Labyrinth on 2008-07-18
Back to the original problem...

In [gpm-screensaver.c]("http://www.google.de/codesearch?hl=de&q=SimulateUserActivity+show:lXuV9sdgUL8:G8m3hC9k3uM:sMK8A4ZwH6A&sa=N&cd=2&ct=rc&cs_p=http://people.debian.org/~nobse/etch/gnome2.16/gnome-power-manager/gnome-power-manager_2.16.3.orig.tar.gz&cs_f=gnome-power-manager-2.16.3/src/gpm-screensaver.c"), gnome-power-manager does the following:

[PHP]/**
 * gpm_screensaver_poke:
 * @screensaver: This screensaver class instance
 *
 * Pokes GNOME Screensaver simulating hardware events. This displays the unlock
 * dialogue when we resume, so the user doesn't have to move the mouse or press
 * any key before the window comes up.
 **/
gboolean
gpm_screensaver_poke (GpmScreensaver *screensaver)
{
	g_return_val_if_fail (GPM_IS_SCREENSAVER (screensaver), FALSE);

	if (! screensaver->priv->is_connected) {
		gpm_debug ("Not poke'ing, as gnome-screensaver not running");
		return FALSE;
	}

	/* shouldn't be, but make sure proxy valid */
	if (screensaver->priv->gs_proxy == NULL) {
		gpm_warning ("g-s proxy is NULL!");
		return FALSE;
	}

	/* shouldn't be, but make sure proxy valid */
	if (screensaver->priv->gs_proxy == NULL) {
		gpm_warning ("g-s proxy is NULL!");
		return FALSE;
	}

	gpm_debug ("poke");
	dbus_g_proxy_call_no_reply (screensaver->priv->gs_proxy,
				    "SimulateUserActivity",
				    G_TYPE_INVALID);
	return TRUE;
}[/PHP]

But doing the same in python fails:

[PHP]klaus@blaubeere:~/py/screensaver-toggle$ python
Python 2.5.2 (r252:60911, May  7 2008, 15:19:09) 
[GCC 4.2.3 (Ubuntu 4.2.3-2ubuntu7)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import dbus
>>> bus = dbus.SessionBus()
>>> iface = dbus.Interface(bus.get_object("org.gnome.ScreenSaver","/org/gnome/ScreenSaver"), "org.gnome.ScreenSaver")
>>> iface
<Interface <ProxyObject wrapping <dbus._dbus.SessionBus (session) at 0xb7b74adc> :1.2 /org/gnome/ScreenSaver at 0xb7d0226c> implementing 'org.gnome.ScreenSaver' at 0xb7b78eac>
>>> iface.SimulateUserActivity()
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/var/lib/python-support/python2.5/dbus/proxies.py", line 68, in __call__
    return self._proxy_method(*args, **keywords)
  File "/var/lib/python-support/python2.5/dbus/proxies.py", line 140, in __call__
    **keywords)
  File "/var/lib/python-support/python2.5/dbus/connection.py", line 607, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.[/PHP]

The first time I tried calling iface.SimulateUserActivity(), python segfaulted. :rolleyes:

Edit: 
Maybe the problem is that python expects a dbus reply from gnome-screensaver, but g-s isn't sending any on purpose.

In [gnome-screensaver-command.c]("http://www.google.de/codesearch?hl=de&q=SimulateUserActivity+show:d85ChIXfauY:ObUTkV20too:5ThcAARRCJE&sa=N&cd=4&ct=rc&cs_p=http://mirror.arcticnetwork.ca/pub/gentoo/distfiles/gnome-screensaver-2.18.1.tar.bz2&cs_f=gnome-screensaver-2.18.1/src/gnome-screensaver-command.c"), there is a function with this footprint:

[PHP]static DBusMessage *
screensaver_send_message_void (DBusConnection *connection,
                               const char     *name,
                               gboolean        expect_reply)[/PHP]

And it is called as:

[PHP]screensaver_send_message_void (connection, "SimulateUserActivity", FALSE);[/PHP]

So it clearly does not want any reply.

(Since this is only the internal of what "gnome-screensaver-command -p" does - which won't work anyway - I could just quit searching. But a) Why the hell doesn't it work? b) Why does the python dbus interface insist on getting a reply?)

---

### Post by Kulgan on 2008-07-18
After all that I think the totem/mplayer road is going to be best. At least then you're starting with something that *works*.

By "inhibiting process", would that mean the script or the command in the script? If it's the script, the solution should be easy. Just don't end the script. Infinite loop with sleep or so. The second call would then do a killall of it's own filename, ending both itself and the first instance, which is preventing the screensaver from appearing. 

But I'm not sure. I think there's a function in mplayer that specifically controls the screensaver... lemme look...

---

### Post by Labyrinth on 2008-07-18
> **Kulgan said:**
> After all that I think the totem/mplayer road is going to be best. At least then you're starting with something that *works*.

Erm... my script **does** work. ;) It did since its creation.

The only remaining problem is: How do we wake up a sleeping screen?
Preventing the screensaver from running at all (and preventing the screen from powering off) works like a charm already.

> **Kulgan said:**
> By "inhibiting process", would that mean the script or the command in the script?

The script.

> **Kulgan said:**
> If it's the script, the solution should be easy. Just don't end the script. Infinite loop with sleep or so. The second call would then do a killall of it's own filename, ending both itself and the first instance, which is preventing the screensaver from appearing. 
Which would make this a daemon. Far too complicated if you can just set one gconf value, no? ;D

---

### Post by Kulgan on 2008-07-18
```
Erm... my script does work.
```
Sorry, misunderstanding there. For me, that part is done. Your script works, that part of the problem is solved. So yes, the issue is now kicking some life into Sleeping Beauty. See these as two completely different parts of the task - and my thoughts about totem/mplayer were considering where to start from on the second section. 

> Which would make this a daemon. Far too complicated if you can just set one gconf value, no? ;D
I'm all for solutions that work. Since I can't get anything working, I generally don't like my solutions. Your solutions work, so go for it. Hell, I don't understand half of what I see anyway. 
Keep us posted!

---

### Post by Labyrinth on 2008-07-18
> Since I can't get anything working, I generally don't like my solutions. Your solutions work, so go for it. Hell, I don't understand half of what I see anyway.

Hey, keep trying! Python is really easy and it is well documented (especially through introspection) [and it is damn powerful... and suited for about any "desktop helper" task... quick file renaming, exif tagging, ... whatever you imagine!]. 

You can just start python in the command line and run commands interactively before putting everything together into a script.

If you have questions about my code, just ask! I'm glad if I can help! ;)


Oh, and: The daemon solution would solve the problem of feedback. I wanted to have a changing icon displaying the current enabled/disabled state. With a mere panel launcher, this is not possible, though. So I we could start changing this baby into a small app running in the system tray.

Rock on! :guitar:

PS: Before the poking is solved in gnome-screensaver, I doubt we can find a way to wake up the screen at all... sadly.

---

### Post by Kulgan on 2008-07-18
> So I we could start changing this baby into a small app running in the system tray.

Sounds awesome :D And I have NO idea how to go about it. 

I'll have a better look at Python next week. It seems an interesting language, from what I've seen, and more system oriented than PHP, object oriented without the stupid syntax of C++, and without the bloat of Java. 
I'm also burying myself a bit deeper in C at the moment, so it's going to go piecemeal. I won't have access to the Internet for most of next week, so are there any docs I should download beforehand? I'm thinking a quick tut to get me started, as well as the function docs (other than in the package python2.4-doc?). 
I'll get there eventually... Thanks for the encouragement!

---

### Post by Labyrinth on 2008-07-18
> **Kulgan said:**
> Sounds awesome :D And I have NO idea how to go about it.
I might try something tonight or tomorrow. Of course I'll keep you updated. 

> I'll have a better look at Python next week. It seems an interesting language, from what I've seen, and more system oriented than PHP, object oriented without the stupid syntax of C++, and without the bloat of Java. 
Well said. And that's what makes python so much fun to write and play with. No matter what you're about to code, you can just start without having to deal with any of that unnecessary boilerplate.

>  I won't have access to the Internet for most of next week, so are there any docs I should download beforehand? I'm thinking a quick tut to get me started, as well as the function docs 
Sure: [http://docs.python.org/tut/]("http://docs.python.org/tut/"). I haven't found a tar.gz of it, or a one-page html document, but I'm sure there's one somewhere, since I started learning python with that same tutorial, most of which I had printed in pretty small font on a lot of paper :D
Anyway, you can just wget the whole tut to read in your browser.

And then there's the extensive library reference at [http://docs.python.org/lib/lib.html]("http://docs.python.org/lib/lib.html"). Nothing to read through at once, but a wonderful source for reference.

Once you're back online you should also try the Python lib sidebar at [http://www.edgewall.org/python-sidebar/html/toc-tutorial.html]("http://www.edgewall.org/python-sidebar/html/toc-tutorial.html"). Just bookmark it and (if you're using firefox) check the "Load this bookmark in sidebar" toggle. An amazing little tool.

> (other than in the package python2.4-doc?). 
Why not 2.5?

PS: I just [read about the contents of python2.5-doc]("http://packages.ubuntu.com/de/hardy/python2.5-doc"):

> These is the official set of documentation for the interactive high-level object-oriented language Python (v2.5). All documents are provided in HTML format, some in info format. The package consists of ten documents:

  * What's New in Python2.5
  * Tutorial
  * Python Library Reference
  * Macintosh Module Reference
  * Python Language Reference
  * Extending and Embedding Python
  * Python/C API Reference
  * Installing Python Modules
  * Documenting Python
  * Distributing Python Modules

Which made me believe that this is exactly what I told you to download. So thanks to debian you don't need to download any other sources. The doc package has the best tutorial and reference you can find.

Edit: Confirming. I just installed python2.5-doc. It IS the same. Of course the online version might be a little more up to date, but there won't be any important differences.

---

### Post by Kulgan on 2008-07-18
Thanks, have all that prepared for tomorrow. So brb after the break.

:guitar:

---

### Post by Labyrinth on 2008-07-19
Guido's essays are a great resource for a convenient read, too: [http://www.python.org/doc/essays/](http://www.python.org/doc/essays/)

Also, "HOWTO Fetch Internet Resources Using urllib2" helped me a lot: [http://docs.python.org/dev/howto/urllib2.html](http://docs.python.org/dev/howto/urllib2.html)

You might find other howtos ([http://docs.python.org/dev/howto/index.html](http://docs.python.org/dev/howto/index.html)) useful, too. (sockets, regular expressioms...)

---

### Post by Labyrinth on 2008-07-19
So here comes screensaver-toggle-gtk 0.1!

It now lives in the tray. The screensaver can be enabled and disabled via the tray icon's popup menu or by just clicking the tray icon itself.

The screensaver is still being disabled by modifying the "enable idle activation" flag in gconf, but now that the script has a gtk.main(), it could also use dbus to send an Inhibit message to gnome-screensaver, like totem does.
I might try this just for fun for 0.2.
I'm also planning to add an "Start screensaver now" and maybe also a "Lock screen" menu item.

Python Code:
```
#!/usr/bin/python
# -*- coding: utf-8 -*-

# Licensed under the GPL
# Written by Klaus Bitto
# Version 0.1 from 2008-07-19

# Version history:
# 
# 0.1 2008-07-19
# Initial release, taking over some code from the non-gtk version

#    GTK Screensaver toggle - simple toggle to enable/disable the screensaver
#    running in the system tray.
#    Copyright (C) 2008 Klaus Bitto (firstname.lastname@gmail.com)
#
#    This program is free software; you can redistribute it and/or modify
#    it under the terms of the GNU General Public License as published by
#    the Free Software Foundation; either version 2 of the License, or
#    (at your option) any later version.
#
#    This program is distributed in the hope that it will be useful,
#    but WITHOUT ANY WARRANTY; without even the implied warranty of
#    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#    GNU General Public License for more details.
#
#    You should have received a copy of the GNU General Public License
#    along with this program; if not, write to the Free Software
#    Foundation, Inc., 675 Mass Ave, Cambridge, MA 02139, USA.
#


import sys
import gconf
import pygtk, gtk

GCONF_KEY_IDLE_ACTIVATION = "/apps/gnome-screensaver/idle_activation_enabled"

tray = None

def toggle_screensaver(*args):
	disable_screensaver() if is_screensaver_enabled() \
		else enable_screensaver()
	update_status_indicators()
	
def is_screensaver_enabled():
	return gconf.client_get_default().get_bool(GCONF_KEY_IDLE_ACTIVATION)
	
def enable_screensaver():
	client = gconf.client_get_default()
	client.set_bool(GCONF_KEY_IDLE_ACTIVATION, True)
	

def disable_screensaver():
	client = gconf.client_get_default()
	client.set_bool(GCONF_KEY_IDLE_ACTIVATION, False)

def get_toggle_text():
	return "Disable screensaver idle activation" if is_screensaver_enabled() \
		else "Enable screensaver idle activation"
		
def update_status_indicators():
	global tray
	enabled = is_screensaver_enabled()
	tray.set_tooltip("Screensaver enabled" if enabled else "Screensaver disabled")
	tray.set_from_pixbuf(
		gtk.gdk.pixbuf_new_from_file("screensaver-%s.png" % \
			("enabled" if is_screensaver_enabled() else "disabled") ))

def show_menu(status_icon, button, activate_time):
	menu = gtk.Menu()
	
	item = gtk.MenuItem(get_toggle_text())
	item.connect("activate", toggle_screensaver)
	menu.append(item)
	
	item = gtk.MenuItem("Quit")
	item.connect("activate", lambda(x): sys.exit(0))
	menu.append(item)
	
	menu.show_all()
	menu.popup(None, None, None, button, activate_time)
	

def main():
	global tray
	tray = gtk.StatusIcon()
	update_status_indicators()
	tray.connect("popup-menu", show_menu)
	tray.connect("activate", toggle_screensaver)
	
	gtk.main()
	

if __name__ == "__main__":
	main()


```

PS: The forum is eating backslashes before newlines. Very bad for posting python code with wrapping lines...
PPS: No, actually it's only the PHP tags. But other than the CODE tags, they add some nice syntax highlighting :/

---

### Post by Labyrinth on 2008-07-19
Version 0.2 

Now using dbus.
Neither subprocess nor gconf are needed anymore.
Downside (or possible upside?): Screensaver is only inhibited as long as the app is running in the tray.

You can now 
- Inhibit and UnInhibit (enable / disable) the screensaver with OneClick&#8482;
- Run the screensaver right away
- Lock the screen

Code:
```

#!/usr/bin/python
# -*- coding: utf-8 -*-

# Licensed under the GPL
# Written by Klaus Bitto
# Version 0.1 from 2008-07-19

# Version history:
#
# 0.2 2008-07-19
# Using dbus instead of gconf and subprocess(gnome-screensaver-command)
# 
# 0.1 2008-07-19
# Initial release, taking over some code from the non-gtk version

#    GTK Screensaver toggle - simple toggle to enable/disable the screensaver
#    running in the system tray.
#    Copyright (C) 2008 Klaus Bitto (firstname.lastname@gmail.com)
#
#    This program is free software; you can redistribute it and/or modify
#    it under the terms of the GNU General Public License as published by
#    the Free Software Foundation; either version 2 of the License, or
#    (at your option) any later version.
#
#    This program is distributed in the hope that it will be useful,
#    but WITHOUT ANY WARRANTY; without even the implied warranty of
#    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#    GNU General Public License for more details.
#
#    You should have received a copy of the GNU General Public License
#    along with this program; if not, write to the Free Software
#    Foundation, Inc., 675 Mass Ave, Cambridge, MA 02139, USA.
#


import sys
import gconf
import pygtk, gtk
import dbus

GCONF_KEY_IDLE_ACTIVATION = "/apps/gnome-screensaver/idle_activation_enabled"
DBUS_BUS_NAME = "org.gnome.ScreenSaver"
DBUS_OBJECT_PATH = "/org/gnome/ScreenSaver"
DBUS_INTERFACE = "org.gnome.ScreenSaver"

tray = None
dbus_iface = None
dbus_cookie = None

def run_screensaver(*args):
	global dbus_iface
	dbus_iface.SetActive(True)
	
def lock_screen(*args):
	global dbus_iface
	dbus_iface.Lock.call_async()

def toggle_screensaver(*args):
	disable_screensaver() if is_screensaver_enabled() \
		else enable_screensaver()
	update_status_indicators()
	
def is_screensaver_enabled():
	global dbus_cookie
	return not dbus_cookie
	
def enable_screensaver():
	global dbus_iface, dbus_cookie
	if dbus_cookie:
		dbus_iface.UnInhibit(dbus_cookie)
		dbus_cookie = None
		print "Screensaver uninhibited"

def disable_screensaver():
	global dbus_iface, dbus_cookie
	dbus_cookie = dbus_iface.Inhibit("GTK Screensaver Toggle", "User request")
	print "Screensaver inhibited"

def get_toggle_text():
	return "Disable screensaver" if is_screensaver_enabled() \
		else "Enable screensaver"
		
def update_status_indicators():
	global tray
	enabled = is_screensaver_enabled()
	tray.set_tooltip("Screensaver enabled" if enabled else "Screensaver disabled")
	tray.set_from_pixbuf(
		gtk.gdk.pixbuf_new_from_file("screensaver-%s.png" % \
			("enabled" if is_screensaver_enabled() else "disabled") ))

def show_menu(status_icon, button, activate_time):
	menu = gtk.Menu()
	
	item = gtk.MenuItem(get_toggle_text())
	item.connect("activate", toggle_screensaver)
	menu.append(item)
	
	menu.append(gtk.SeparatorMenuItem())
	
	item = gtk.MenuItem("Start screensaver")
	item.connect("activate", run_screensaver)
	menu.append(item)
	
	item = gtk.MenuItem("Lock screen")
	item.connect("activate", lock_screen)
	menu.append(item)
	
	menu.append(gtk.SeparatorMenuItem())
	
	item = gtk.MenuItem("Quit")
	item.connect("activate", lambda(x): sys.exit(0))
	menu.append(item)
	
	menu.show_all()
	menu.popup(None, None, None, button, activate_time)
	

def main():
	global tray, dbus_iface
	bus = dbus.SessionBus()
	dbus_iface = dbus.Interface(
		bus.get_object(DBUS_BUS_NAME, DBUS_OBJECT_PATH), DBUS_INTERFACE)
	
	tray = gtk.StatusIcon()
	update_status_indicators()
	tray.connect("popup-menu", show_menu)
	tray.connect("activate", toggle_screensaver)
	
	gtk.main()
	

if __name__ == "__main__":
	main()

```

Edit:
Mplayer does it the same way: [http://www.google.de/codesearch?hl=de&q=package:mplayer+gnome+screensaver+show:0yjhFHJ0dO4:M3ZKQBcxXq0:0yjhFHJ0dO4&sa=N&cd=2&ct=rc&cs_p=http://gnome-mplayer.googlecode.com/svn&cs_f=src/dbus-interface.c]("http://www.google.de/codesearch?hl=de&q=package:mplayer+gnome+screensaver+show:0yjhFHJ0dO4:M3ZKQBcxXq0:0yjhFHJ0dO4&sa=N&cd=2&ct=rc&cs_p=http://gnome-mplayer.googlecode.com/svn&cs_f=src/dbus-interface.c") (Scroll down - the two bottommost functions; dbus_disable_screensaver() and dbus_unhook())

---

### Post by Kulgan on 2008-07-24
Looks awesome!

I'm assuming that you also need two images, screensaver-enabled.png and screensaver-disabled.png in the same directory? The tray flickers, so I assume it tries to add something, then exits when it doesn't find the images. As, I notice, it tells me when it's run from the command line ^^

Care to share the nice shiny ones you were using? :P

Edit:
Sorry, just saw the archive in the earlier post. Thanks!

---

### Post by Labyrinth on 2008-07-24
Current version (v0.3 from 2008-07-20):

```
#!/usr/bin/python
# -*- coding: utf-8 -*-

# Licensed under the GPL
# Written by Klaus Bitto
# Version 0.3 from 2008-07-20

# Version history:
#
# 0.3 2008-07-20
# Now can be run from any dir - will always load icons.
# Added accelerator keys
#
# 0.2 2008-07-19
# Using dbus instead of gconf and subprocess(gnome-screensaver-command)
# 
# 0.1 2008-07-19
# Initial release, taking over some code from the non-gtk version

#    GTK Screensaver toggle - simple toggle to enable/disable the screensaver
#    running in the system tray.
#    Copyright (C) 2008 Klaus Bitto (firstname.lastname@gmail.com)
#
#    This program is free software; you can redistribute it and/or modify
#    it under the terms of the GNU General Public License as published by
#    the Free Software Foundation; either version 2 of the License, or
#    (at your option) any later version.
#
#    This program is distributed in the hope that it will be useful,
#    but WITHOUT ANY WARRANTY; without even the implied warranty of
#    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#    GNU General Public License for more details.
#
#    You should have received a copy of the GNU General Public License
#    along with this program; if not, write to the Free Software
#    Foundation, Inc., 675 Mass Ave, Cambridge, MA 02139, USA.
#


import sys
import os.path
import pygtk
pygtk.require("2.0")
import gtk
import dbus

DBUS_BUS_NAME = "org.gnome.ScreenSaver"
DBUS_OBJECT_PATH = "/org/gnome/ScreenSaver"
DBUS_INTERFACE = "org.gnome.ScreenSaver"

tray = None
dbus_iface = None
dbus_cookie = None

def run_screensaver( *args ):
	global dbus_iface
	dbus_iface.SetActive( True )
	
def lock_screen( *args ):
	global dbus_iface
	dbus_iface.Lock.call_async()
	
def screensaver_settings( *args ):
	from subprocess import Popen
	Popen( ["gnome-screensaver-preferences"] )

def toggle_screensaver( *args ):
	disable_screensaver() if is_screensaver_enabled() \
		else enable_screensaver()
	update_status_indicators()
	
def is_screensaver_enabled():
	global dbus_cookie
	return not dbus_cookie
	
def enable_screensaver():
	global dbus_iface, dbus_cookie
	if dbus_cookie:
		dbus_iface.UnInhibit( dbus_cookie )
	dbus_cookie = None
	print "Screensaver uninhibited"

def disable_screensaver():
	global dbus_iface, dbus_cookie
	dbus_cookie = dbus_iface.Inhibit( "GTK Screensaver Toggle", "User request" )
	print "Screensaver inhibited"

def get_toggle_text():
	return "_Disable screensaver" if is_screensaver_enabled() \
		else "En_able screensaver"
		
def update_status_indicators():
	global tray
	tray.set_tooltip( "Screensaver enabled" if is_screensaver_enabled() else "Screensaver disabled" )
	tray.set_from_pixbuf( 
		gtk.gdk.pixbuf_new_from_file( os.path.join( sys.path[0], \
			"screensaver-%s.png" % \
			( "enabled" if is_screensaver_enabled() else "disabled" ) ) ) )

def show_menu( status_icon, button, activate_time ):
	menu = gtk.Menu()
	
	item = gtk.MenuItem( get_toggle_text() )
	item.connect( "activate", toggle_screensaver )
	menu.append( item )
	
	menu.append( gtk.SeparatorMenuItem() )
	
	item = gtk.MenuItem( "_Start screensaver" )
	item.connect( "activate", run_screensaver )
	menu.append( item )
	
	item = gtk.MenuItem( "_Lock screen" )
	item.connect( "activate", lock_screen )
	menu.append( item )
	
	menu.append( gtk.SeparatorMenuItem() )

	item = gtk.MenuItem( "Screensaver s_ettings..." )
	item.connect( "activate", screensaver_settings )
	menu.append( item )
	
	menu.append( gtk.SeparatorMenuItem() )
	
	item = gtk.MenuItem( "_Quit" )
	item.connect( "activate", lambda( x ): sys.exit( 0 ) )
	menu.append( item )
	
	menu.show_all()
	menu.popup( None, None, None, button, activate_time )
	

def main():
	global tray, dbus_iface
	bus = dbus.SessionBus()
	dbus_iface = dbus.Interface( 
		bus.get_object( DBUS_BUS_NAME, DBUS_OBJECT_PATH ), DBUS_INTERFACE )
	
	tray = gtk.StatusIcon()
	update_status_indicators()
	tray.connect( "popup-menu", show_menu )
	tray.connect( "activate", toggle_screensaver )
	
	gtk.main()
	

if __name__ == "__main__":
	main()

```

(Attached the "disabled" cross in case you want to use a different icon as base.)

PS: Tomorrow I'm going to Tropea (Southern Italy! Yay!) for one week for an international dance workshop. So don't worry if I'm not answering. ;)

PPS: How's your python learning going? =)

---

### Post by Kulgan on 2008-07-24
Looking good. You've really got this thing flying! 

I haven't had time to read much (holidays seem to imply spending time with the family, after all), and most of what I have read was fairly obvious from looking at the code. I should have skipped some of it, but there could always have been something important hidden in there. And Python's version of arrays (lists?) seems really good compared to what I've been using so far, especially combined with the pimped-up fors. Been using them a lot in PHP and always wanted something a bit more advanced. Oh well, should have time to continue the tut and check out those links in the next few weeks. 

Enjoy Italy!

---

### Post by Labyrinth on 2008-08-03
Hi there!
So I'm back.

How are you progressing? Did you get to the functional programming part?
List comprehensions rock, I can tell you! =) :guitar:

---

### Post by Kulgan on 2008-08-11
Still going at it, in small parts at a time. Back to the grind today, so I won't have much time, but I'll see how much I can do in between everything else..

---

### Post by cajunlibra on 2010-06-11
Have you considered adding this awesome script to a repository? It would make updating it much easier.

---

### Post by Labyrinth on 2010-06-13
Hm. Probably not, for those reasons:

- I've never done packaging.
- It's never going to go into an official repository, since I am abusing the system tray. Following official policy this program should be run as a panel applet, AFAIK.
- I'm not using and developing it any further. (What else is there to do anyway?) But I GPLed it, so anyone can reuse and improve the code.

---

