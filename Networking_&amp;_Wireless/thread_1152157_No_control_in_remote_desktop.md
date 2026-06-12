---
title: "No control in remote desktop"
date: 2009-05-07
forum: Networking &amp; Wireless
---

### Post by gsxruk on 2009-05-07
Hi,

I'm now running Jaunty and would like to remote desktop to it from a WinXP laptop.  I have configured the remote desktop feature by selecting "Allow other users to view your desktop" and "Allow other users to control your desktop".  For simplicity at this time I have left all security options disabled.  Currently, the connection is over LAN only.

I am using ultraVNC on the WinXP machine but have also tried realVNC and the results are the same.  When I connect, all is fine and the desktop is shown within seconds.  When I move the mouse, I can see the pointer moving on the Ubuntu desktop as well as the WinXP screen.  However, when a selection is made it is visible on the Ubuntu desktop but is not shown on the WinXP screen.

Does anybody have any ideas what is wrong?

Thanks.

---

### Post by gsxruk on 2009-05-08
bump.

---

### Post by mattgyver83 on 2009-05-08
Did you install x11vnc?  If not that could be the problem, you might not be connecting to the correct X display.

sudo apt-get install x11vnc

---

### Post by shabazzk on 2009-05-08
I am having this same exact problem, tried onver LAN and from work, but no joy.
it is funny that 9.04RC worked fine for viewing desktop and controlling it, in fact, so did HDMI (now I get this back border and have to set scaling to under-scan/0). Anyways, I will try your suggestion when I get home mattgyver83.

---

### Post by krunge on 2009-05-08
> **mattgyver83 said:**
> Did you install x11vnc?  If not that could be the problem, you might not be connecting to the correct X display.


To avoid the screen update problem when using x11vnc you **must** supply the "-noxdamage" option:
```
x11vnc -noxdamage ...
```

Or another option is to disable compiz.

More info:

[http://ubuntuforums.org/showthread.php?t=1097683](http://ubuntuforums.org/showthread.php?t=1097683)

[http://www.karlrunge.com/x11vnc/faq.html#faq-beryl](http://www.karlrunge.com/x11vnc/faq.html#faq-beryl)

---

### Post by gsxruk on 2009-05-08
Hi all,

Could someone please explain how the x11vnc fits with the remote desktop feature in System->Preferences->Remote Desktop?  Or are these completely separate?

I installed x11vnc and ran with the option as indicated and this did work but the port number had to be changed to 5901.

---

### Post by mattgyver83 on 2009-05-08
Remote Desktop Viewer allows you to connect to VNC servers so that you can work on them remotely.

On linux VNC will connect to the default display:1 i believe by default, which is not your 'working desktop'  your working desktop is actually on display:0

Without x11vnc present a remote session just creates a new gdm session, in fact if you have speakers setup or on (and near the computer itself), you probably heard the ubuntu login sound when you connected to the machine w/o x11vnc installed.

x11vnc allows the vnc session to be held on display:0 so that you can truly access it remotely in the manner that we all know and love.  As well, x11vnc might just fix the compiz issue itself, your sanity may be harmed by having it on though due the slow redrawing refresh.  This might not fix all issues though in reguards to compiz, it does what it wants.

Hope this helps, have fun.

---

### Post by krunge on 2009-05-08
> **gsxruk said:**
> Could someone please explain how the x11vnc fits with the remote desktop feature in System->Preferences->Remote Desktop?  Or are these completely separate?


They are completely separate.

If you (accidentally) run both at the same time they will both battle for port 5900, i.e. VNC display :0. By default x11vnc will autoprobe for a port working its way up from 5900 until it finds one.  It often winds up with port 5901, i.e. VNC display :1, if vino already has 5900.

To force the port x11vnc uses, supply "-rfbport 590X" (where you pick the X) to its command line.

---

### Post by shabazzk on 2009-05-08
Hey! What gives, so this is a separate program, and not some missing module for the already installed VNC.

Look, that's fine, but I would like to fix the problem with the one that comes installed. So that future users do not have to deal with this and it works out-of-the-box ( I like that expression). If it's a bug then we need to report it, otherwise just fix the bad setting now and make it widely known, so we do not have to deal with future post on the next release of Ubuntu.

Also, I have 2 Linux machines, back in 9.04RC days, I was able to remote in, back-and-forth, between the two, without installing x11VNC. So I would like to be able to now also. Im just confused why it doesn't work now, and what happeded to the ability to change the port in Remote VNC, where did they hide it:confused:

Dang, guess I will have to read the manual :(

---

### Post by shabazzk on 2009-05-09
> **gsxruk said:**
> Hi all,

Could someone please explain how the x11vnc fits with the remote desktop feature in System->Preferences->Remote Desktop?  Or are these completely separate?

I installed x11vnc and ran with the option as indicated and this did work but the port number had to be changed to 5901.

It doesn't, just turn off Compiz, and then see if that fixed the issue, it did for me. I have an ATi chipset, there is a bug filed for this apparently. If you can't do without Compiz, then you can try other VNC software such as x11vnc.

---

### Post by gsxruk on 2009-05-09
Thanks for all the answers.  It does seem that disabling compiz fixes the problem.

---

### Post by jmap82 on 2009-06-09
I wrote a short script to turn compiz off when I'm remotely viewing and back on again when I leave.  I'm no wiz at this stuff, so it may not be the best script ever, but you're welcome to use it if you want.

You can copy and paste from my wiki, [_here_]("http://script.jmap82.com/doku.php?id=jmap82sscripts:monitor").

Hope it helps :)

---

### Post by elhauk on 2009-06-10
> **jmap82 said:**
> I wrote a short script to turn compiz off when I'm remotely viewing and back on again when I leave.  I'm no wiz at this stuff, so it may not be the best script ever, but you're welcome to use it if you want.

You can copy and paste from my wiki, [_here_]("http://script.jmap82.com/doku.php?id=jmap82sscripts:monitor").

Hope it helps :)

What do you do with a script like that? just copy and paste to terminal?

---

### Post by jmap82 on 2009-06-19
> **elhauk said:**
> What do you do with a script like that? just copy and paste to terminal?

You would save it to a text file and give it the extension ".sh" and put it in a non obtrusive place.  Then You would start it with a command like: 
```
$HOME/scripts/MonVino.sh & disown
```*the '& disown' makes it so you can close that terminal window and not worry about it anymore.

I tried to set it up to run in my start up apps, but it doesn't work correctly when its started that way, for some reason.  So I suggest that you run it manually.  It doesn't use much cpu power, so you just leave it running in the background.

I hope it works for you.

---

### Post by elhauk on 2009-06-19
And is the script on the remote computer or the local computer?

---

### Post by jmap82 on 2009-06-19
> **elhauk said:**
> And is the script on the remote computer or the local computer?

The script will run on the computer you want to view... so the remote computer AKA the host computer AKA remotehost.

---

### Post by Greydog56 on 2009-06-22
I didn't try the script by jmap82 as I'd found a different one posted by p388l3s first (p388l3s gave credit to another for the script). The script I found in the Ubuntu forums was under thread: VNC - unable to do anything... just view.  This script temporarily shuts of compiz so vnc viewer can run the server. I'm running 9.04 64 bit and it worked for me. Thought I would link the two threads together.

---

### Post by RGPerson on 2009-07-12
Can someone tell me how to disable Compiz? I'm not even sure what it is, but I'd seen people discussing it here, so when I saw it in the update manager, I installed it.  Now I can't see what I'm VNCing.  So I'm perfectly willing to disable it. If someone could just tell me how.

Nevermind: lucked into it after a nearly fruitless search on this forum and compiz forum and Google.  Finally found something that helped me remove it from the terminal.

Gabrielle

---

### Post by krunge on 2009-07-12
> **RGPerson said:**
> Nevermind: lucked into it after a nearly fruitless search on this forum and compiz forum and Google.  Finally found something that helped me remove it from the terminal.

Please document in this thread everything you needed to do to disable compiz so that others with the same problem will be able to solve it too.

---

### Post by pgn674 on 2009-07-22
> **jmap82 said:**
> I wrote a short script to turn compiz off when I'm remotely viewing and back on again when I leave.Nice script. It didn't work on my system right away, so I made some edits. Primarily, I changed the way $met and $comp are checked to see if they have a value. I don't know why your way wasn't working on my system. I also made the script wait for the vino-server process to start before trying to get its PID, as that would be a problem if I wanted to start the script automatically on log-in. And I wrote out the process names that we're looking for in full, as I had some trouble with thinking a certain process was running when really it was a different process with a similar name.

For beginners that just want this to work, copy and paste the code below into a text file and save it. You might then need to right click the file > Properties > Permissions > check "Allow executing file as a program". Then, go to System > Preferences > Startup Applications > Add > Browse, select the file, and complete adding the startup program. Now just log out and back in, and it will be running. It will be automatically running after a reboot, too.```
#!/bin/bash
 
# A new Script by John-Michael Patino
 
#There is currently a bug (https://bugs.launchpad.net/Ubuntu/+source/vino/+bug/353126) 
#causing a conflict between Compiz, a fancy window management program, and Vino, the 
#default remote desktop server on Ubuntu.  I like having Compiz running when I am at 
#my console, but it isn't necessary when I'm remotely controlling my computer, so I 
#wrote this script to turn Compiz off and on depending on the activity of the vino-server.
#I don't claim that it's the best way, it is just a way, and it work for me.

#Fixed up by Paul Nickerson (pgn674)
#Sources of help with testing if a variable/string is null or not:
#http://tldp.org/LDP/abs/html/testconstructs.html
#http://www.linuxtutorialblog.com/post/tutorial-conditions-in-bash-scripting-if-statements
#Something useful for debugging: ps -e | egrep "compiz|metacity"
#If you use Ctrl+C to quit this, you may need to run "compiz --replace &" in the terminal to start up Compiz.
#To have this run at startup, just add it to System > Preferences > Startup Applications
#I left a bunch of echos in here, for debugging purposes. Uncomment them to write to a log, or take out the >/>> and everything after to write to the terminal.
 
#echo "Starting the VNC Connection Fix script" > "VNC Connection Fix log"	#the single > here overwrites the file and starts it fresh.

vin=`pgrep -x vino-server`										#Check to see if 'vino-server' is running using 'pgrep' and assign any value to the variable $vin. This is important to do before trying to grab its PID, especially if this script is set to run on user log-in.
while [ -z "$vin" ]												#Start a while loop to check if the variable $vin has a value. If it does, then vino-server is running and we can get its PID now.
do
#	echo "vino-server is not yet running." >> "VNC Connection Fix log"	#the double >> here appends to the file.
	sleep 5
	vin=`pgrep -x vino-server`									#re-attempt to assign $vin with a value, to see if the process is running yet
done

#echo "vino-server is running. PID is $vin" >> "VNC Connection Fix log"

vpid=`pgrep vino-server` 										#get the pid of the 'vino-server' process and assign it to $vpid.  'pidof' will also get you this information, but pgrep just seems easier at the time.
#echo $vpid > $HOME/vino.pid									#Record the pid to a file in your home directory.  I originally intended to used this script with 'monit', but later decided not to, so this file is unnecessary. This is not a debugging log line.

while :															#Start while-loop with no criteria.  This loop is constantly running until manually killed.
do
	sleep 5														#Sleeps the script for 5 seconds. Keeps the script from using too much processing power by running the loop every possible moment.
#	echo "Checking..." >> "VNC Connection Fix log"
	mem=`ps -p $vpid -o vsz,pid|grep $vpid|sed "s/ $vpid//g"`	#Get the virtual memory usage with 'ps', trim the fat with 'grep' and 'sed', and assign it to varible $mem.
	if [ $mem -lt 40000 ]										#Start if-statement to check if the virtual memory usage is less-than 40000 bytes - meaning there are no working connections to vino-server.
	then														#Start the then-statement.
#		echo -e "No connection present. vino-server virtual size is$mem KiB." >> "VNC Connection Fix log"
		met=`pgrep -x metacity`									#Check to see if 'metacity'(Ubuntu's default, non-Compiz window manager) is running using 'pgrep' and assign any value to the variable $met.
		if [ -n "$met" ]										#Start a nested if-statement to check if the variable $met has a value. If it does, then 'metacity' is the current window manager.
		then													#Start the then-statement.
#			echo "Starting up compiz. metacity PID is $met" >> "VNC Connection Fix log"
			compiz --replace & disown							#Run 'compiz --replace & disown' if 'metacity is running.  'disown' is new to me, but it basically means that the user/script/process that started the command before the '&' is no-longer responsible for it, and it is attached to the next parent on the process tree.  This is necessary because 'compiz --replace' will hold your script at that process, not allowing any further progress until you kill the script or process.
		fi														#Close nested if-statement.
	else														#Start the else-statement give instructions for when 'vino-server' is using more than 40000 bytes of virtual memory.
#		echo -e "Connection is present. vino-server virtual size is$mem KiB." >> "VNC Connection Fix log"
		comp=`pgrep -x compiz.real`								#Check to see if 'compiz.real' is running and assign any value to the variable $comp.  It is important to 'pgrep' with the phrase 'compiz.real' rather than just 'compiz' because there is likely more than one process running with 'compiz' in the command, and 'compiz.real' is the only one we care about.
		if [ -n "$comp" ]										#Start a nested if-statement to check of the variable $comp has a value. If it does, then "compiz" is the current window manager.
		then													#Start the then-statement.
#			echo "Starting up metacity. compiz.real PID is $comp" >> "VNC Connection Fix log"
			metacity --replace & disown							#Run 'metacity --replace & disown' if compiz is running.
		fi														#Close nested if-statement.
	fi															#Close if-statement.
done															#Close while-loop.
```

---

### Post by Melk79 on 2009-07-22
I was having this problem trying to access my brother's computer.  Disabling compiz also worked for me.  Used to just see a static image of his desktop and now can control. Thanks.

---

### Post by jmap82 on 2009-07-24
> **pgn674 said:**
> Nice script. It didn't work on my system right away, so I made some edits. Primarily, I changed the way $met and $comp are checked to see if they have a value. I don't know why your way wasn't working on my system. I also made the script wait for the vino-server process to start before trying to get its PID, as that would be a problem if I wanted to start the script automatically on log-in. And I wrote out the process names that we're looking for in full, as I had some trouble with thinking a certain process was running when really it was a different process with a similar name.


Thanks for the touch up :)  Yeah, I consider myself, very much a beginner in the world of programming, so I appreciate the chance to learn from someone more experienced.  Sometimes I stumble across an idea that I haven't seen posted on the forums yet and I get a bit zealous, but I know I still have a long way to go.

---

### Post by ryker on 2009-08-17
I had trouble with the original and the modified versions of this script.  Checking the memory usage of vino-server only worked for the first connection.  The memory usage didn't go down much after the viewer session terminated, so I modified the script to check for an established connection instead and simplified the code a bit.

```
#!/bin/bash

# A new Script by John-Michael Patino
 
#There is currently a bug (https://bugs.launchpad.net/Ubuntu/+source/vino/+bug/353126) 
#causing a conflict between Compiz, a fancy window management program, and Vino, the 
#default remote desktop server on Ubuntu.  I like having Compiz running when I am at 
#my console, but it isn't necessary when I'm remotely controlling my computer, so I 
#wrote this script to turn Compiz off and on depending on the activity of the vino-server.
#I don't claim that it's the best way, it is just a way, and it work for me.

#Fixed up by Paul Nickerson (pgn674)
#Sources of help with testing if a variable/string is null or not:
#http://tldp.org/LDP/abs/html/testconstructs.html
#http://www.linuxtutorialblog.com/post/tutorial-conditions-in-bash-scripting-if-statements
#Something useful for debugging: ps -e | egrep "compiz|metacity"
#If you use Ctrl+C to quit this, you may need to run "compiz --replace &" in the terminal to start up Compiz.
#To have this run at startup, just add it to System > Preferences > Startup Applications
#I left a bunch of echos in here, for debugging purposes. Uncomment them to write to a log, or take out the >/>> and everything after to write to the terminal.

# Fixed up yet again by John Alberts (ryker)
# Detecting a vnc session by memory usage did not work for me at all.
# Changed to detect vnc session by checking for an established vnc connection using netstat.
# I also simplified the code quite a bit.  Nothing really wrong with previous code, just a matter
# of preference i guess.  Took out the commented debug code as well.  No reason you can't add it back
# if you have problems.
# pgn674's install and debugging instructions still apply.


# Just sit in this loop until vino-server is running.
while ! pgrep -x "vino-server" > /dev/null 2>&1; do
  sleep 5
done
vpid=`pgrep -x "vino-server"`

# Main loop to swap WM depending on vncviewer connection.
while true; do
  sleep 5
  if netstat -n | grep 5900 | grep "ESTABLISHED" > /dev/null 2>&1; then
    # VNCviewer running, so make sure Metacity is running
    [ `pgrep -x metacity` ] || metacity --replace & disown
  else
     # No vncviewer session, so make sure compiz is running
    [ `pgrep -x compiz.real` ] || compiz --replace & disown
 fi
done
```

Hope this helps others who had the same problem I did.

Regards,
John

---

### Post by pgn674 on 2010-01-09
That's good, ryker, but I just figured out why the script will occasionally switch to Metacity on me when there is no VNC connection: It will switch when something is using ports 5900* or *5900, where * is any single digit. To fix this, just change the script from```
if netstat -n | grep 5900 | grep "ESTABLISHED" > /dev/null 2>&1; then
```to```
if netstat -n | grep ":5900 " | grep "ESTABLISHED" > /dev/null 2>&1; then
```

---

