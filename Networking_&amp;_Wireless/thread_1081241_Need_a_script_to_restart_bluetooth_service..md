---
title: "Need a script to restart bluetooth service."
date: 2009-02-26
forum: Networking &amp; Wireless
---

### Post by Spyder89 on 2009-02-26
Hello,

I am currently running Ubuntu 8.04 and have a little knowledge in linux. I would like to create a launcher or a small script to restart the bluetooth service. When I hit the Fn+2 key it shuts of the bluetooth signal but doesn't fully restart the service or maybe it just doesn't recreate the connection to my bluetooth device. When I execute this command: sudo /etc/init.d/bluetooth it does. I can do this but I would rather make a clickable icon to do this for the users I have.

Please help!

---

### Post by tombogue on 2009-03-01
I know that the command

sudo /etc/init.d/*servicename* restart

will restart most services.  I tested this out with the bluetooth service, and it seemed to work.  So try out

sudo /etc/init.d/bluetooth restart

Hope this helps!

---

### Post by lswb on 2009-03-01
It is possible to run a script just by pressing the button or have it run because of some other hardware event. Unfortunately the details of this are beyond my experience at this time. I do know it is tied in with the files in /etc/acpi. These are scripts that run on events like open/close laptop lid, toggle wifi or bluetooth button, etc. Hope this info helps you find an answer.

---

### Post by ephemeralDream on 2009-03-03
Hey, I wrote a GUI script for it :)

It required zenity package so please install if you don't have it. You can add this script to desktop or panel as well.

Download it, then
% chmod +x bluezen

On a side note, if you found the information box is annoying then remove this line " zenity --info --text "$STATUS" "

Cheers,
Idyllic Tux
[http://idyllictux.wordpress.com/](http://idyllictux.wordpress.com/)

```

#!/bin/bash

SWITCH=""
PID=""
# Comment out if your is toshiba laptop
# TOSHSET=""

SWITCH=$(zenity  --list  --text "Please Select Bluetooth Option:" --radiolist  --column " * " --column "Option" TRUE "On" FALSE "Off" FALSE "Restart" FALSE "Status");
echo $SWITCH

if [ $SWITCH = "On" ]; then
	SWITCH="start"	
	# Comment out if your is toshiba laptop
	# TOSHSET="on"
	bluetooth-applet &			
elif [ $SWITCH = "Off" ]; then
	SWITCH="stop"		
	PID=$(pidof bluetooth-applet)
	kill $PID
elif [ $SWITCH = "Restart" ]; then
	# Comment out if your is toshiba laptop
	# TOSHSET="on"
	SWITCH="restart"
	PID=$(pidof bluetooth-applet)
	kill $PID
	bluetooth-applet &
else 
	#"Unknown parameter. Quitting."
	SWITCH="status"
fi

## Initialization
STATUS=`gksudo /etc/init.d/bluetooth $SWITCH`
zenity --info --text "$STATUS"
# Comment out if your is toshiba laptop
# gksudo toshset -bluetooth $TOSHSET

```

---

