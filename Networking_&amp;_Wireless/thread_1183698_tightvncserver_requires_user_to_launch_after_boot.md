---
title: "tightvncserver requires user to launch after boot"
date: 2009-06-10
forum: Networking &amp; Wireless
---

### Post by linuxtest on 2009-06-10
Tightvncserver is installed and works well on Ubuntu 9.04 Server.  When power is lost the computer automatically reboots (BIOS setting), but tightvncserver requires a user (with appropriate rights) to physically enter "tightvncserver" into a terminal window to start it.  Is there a way for Ubuntu to start tightvncserver during OS boot-up that requires no physical contact with the machine?  An example would be that a file server has lost power for a few minutes, but after power has been restored the computer boots up and tightvncserver is fully ready to accept remote logins without anyone baby-sitting it.

---

### Post by keithrussell on 2009-06-24
I'm new to this but after trying for a few weeks I've settled for cheating.
Connect with PuTTY
Log on to the terminal as USER with USER PASSWORD
type vncserver
Logout, or not.
Job done you can run a vnc session as USER on 5901 (assuming no-one else got there first.
If anyone knows a definite, easy to follow, method of auto-starting tightvnc in 9.04 please write it down.
Most of the threads I've followed crash & burn because files or directories don't exist, even with hidden files showing.
The most promising suggested inserting a file/script in /etc/rc3.d but that was for an older version of Ubuntu.
I've wrecked one installation & I don't fancy going through that again.

---

### Post by mattgyver83 on 2009-06-24
I dont have your exact answer, but you can use x11vnc and when you set it up create an xinetd service for x11vnc.... when your machine reboots the service should be restarted.

At least thats how i think it works, and does for me.  heres a link.  Step 3 is where all this magic takes place.

[http://ubuntuforums.org/showthread.php?t=363236&highlight=vnc](http://ubuntuforums.org/showthread.php?t=363236&highlight=vnc)

---

### Post by keithrussell on 2009-06-25
Thanks for reply, I'll follow it up
 
In the meantime I have been hunting & found an easy way to launch tightvnc during boot. The remaining problem is to get a working desktop instead of a blank X terminal
 
The instruction was to edit /etc/rc.local This is what I have at present . I've bolded the text that's working
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
# su - root -c "/usr/bin/vncserver :1 -geometry 1024x768 -depth 16 #> /tmp/vncserver.log 2>&1 &" & ; didn't work
# su root -c "cd /root && vncserver :1" 
# su root -c "cd /root/.vnc && vncserver :1"
# PATH="$PATH:/usr/X11R6/bin/" ; didn't help
** su root -c "cd /root/.vnc && vncserver :1 -geometry 1280x1024 -depth 16"** 
# startx &    ; didn't help either
# su --command=vncserver - <root> ;  --command = -c
# su --command=tightvncserver - <root>
**exit 0**
 
I've tried a few things but, so far with no luck. The 2 stage login gives me the right desktop. I know I'm trying to start a "root" session, I'll change to a "user" session if I ever get it working. Messing (sorry, editing) xstart up hasn't helped & I think it stopped the 2 stage boot up at one time.

---

### Post by keithrussell on 2009-06-26
Thanks for the url
Unfortunately, either I'm getting thicker or it led me astray again.
The folder & files either didn't exist or were in different locations.
I created the file & folder as instructed + a copy of the file in the existing init.d folder
I rebooted and, at least, I was no worse off.
There must be a script to duplicate the command path follwed when I type "vncserver" at the command prompt that would start the same gnome desktop session from rclocal before I log on.
I'll keep looking

---

