---
title: "HTPC lirc initiate xbmc custom shortcut"
date: 2009-12-31
forum: Multimedia Software
---

### Post by wardy277 on 2009-12-31
I have been setting up my HTPC. I have it all how i wanted with the remote working fine with lirc.

What i want is to press the MCE green button to launch XBMC just like MCE in windows. I have tried creating the shortcut but it doesnt let me use the remote at all for this. is there a way to manualy set this?

Chris

SPEC:
Zotac Ion mini itx
intel atom 330
ubuntu karmic
XBMC (latest)

---

### Post by Dugger5688 on 2010-02-06
I'm working on this right now, used to have it working but my NTFS drive decided to crap out and for some reason got marked as bootable which trashed everything. I will post up the way to get this when I figure it out.

Looks like I got it. 

So from clean install to getting this set up:

0) install XBMC
1) run:
```
sudo apt-get install lirc
```
2) in a terminal:
```
gedit ~/.lircrc
```
Then add the following text into your lircrc:

```

begin
    prog = irexec
    button = Home
    #we'll create the script later, assumes that the script is in /home/$USER/scripts
    config = ~/scripts/startxbmc.sh
end

```
Save, and exit gedit
3) in a terminal
```

cd && mkdir scripts && gedit ~/scripts/startxbmc.sh

```

Now put in the 'startxbmc.sh' script:

```

#!/bin/bash
if pidof -s /usr/share/xbmc/xbmc.bin ; then
	echo "XBMC already running"
else
	echo "Starting XBMC"
	/usr/bin/xbmc &
fi

```
Save, exit gedit. The in your terminal again:

```

chmod +x ~/scripts/startxbmc.sh

```

4) Test it out (in your terminal):
```

sudo /etc/init.d/lirc restart
irexec -d

```

Now push the HOME button on your MCE remote, xbmc should start up. If so, then get out of XBMC.

5) start irexec on boot:

In terminal:
```

cd && gedit scripts/startirexec.sh

```

Put the following in the script:
```

#!/bin/bash
irexec -d

```

back in you terminal:
```

chmod +x ~/scripts/startirexec.sh

```

Now go to System->Preferences->Startup Applications and click on Add. For the name pick something that you is obvious like "start irexec daemon". Then under command click browse and browse to your startirexec.sh script.

Log out your user, then log back in and you should be set to go. The first time I did it for some reason xbmc didn't start fullscreen, just go to your settings in xbmc and fullscreen it if this happens and it'll take care of it. 

You can also look around the net for various similar setups, including some that kill xbmc on a key input. I never got any of those to work so I stripped it all down to just starting it.

---

### Post by wardy277 on 2010-02-07
Excellent just what i was looking for 

thanx!

---

### Post by ntetreau on 2010-02-10
Thanks, that really got me going.  Do you have this issue sometimes when two instances of xbmc would open?  I need to investigate this issue.

EDIT: I've added a repeat = 0 to my .lircrc file, and so far so good. 

```
begin
    prog = irexec
    button = Home
    repeat = 0
    #we'll create the script later, assumes that the script is in /home/$USER/scripts
    config = ~/scripts/startxbmc.sh
end
```

Additionally, I wanted to max out pulseaudio's volume when starting xbmc, so I followed the instructions from this [thread]("http://ohioloco.ubuntuforums.org/showthread.php?t=1313076") which led me to create a script called ./scripts/pa-vol.sh

```
if [ -z "$1" ] ; then
    echo "Usage: $0 VOL"
    echo "       where VOL is an integer from 0 thru 65535"
    exit 1
fi

exec pacmd << ! > /dev/null 2>&1
set-sink-volume 0 $1
!
```

with scripts/startxbmc.sh

```
#!/bin/bash
if pidof -s /usr/share/xbmc/xbmc.bin ; then
	echo "XBMC already running"
else
	echo "Starting XBMC"
        /home/$USER/scripts/pa-vol.sh 98302
	/usr/bin/xbmc &
fi
```

where 65535 is 100% and 98302 is 150% on my system.

---

### Post by wardy277 on 2010-02-10
Awsome, i didnt even think about looking how to set the volume by command. That has been bugging me for a while now. I havent noticed any multiple instences, but i havent pressed the initialize button more than once.

All i need not is to be able to turn on my pc from the remote. I think its possible from a suspend bu not sure its possible from shutdown. any idea?

Chris

PS. I am using a ZOTAC IONITX-A
(the analog 5.1 took me ages to get working cos not wasnt even clear it could do it!)

---

### Post by ntetreau on 2010-02-10
Ok, I finally figured it out.

First, to suspend using the Power button, I had to install powermanagement-interface to get pmi command.

Now my .lircrc file:
```
begin
    prog = irexec
    button = Home
    repeat = 0
    config = ~/scripts/startxbmc.sh
end

begin
    prog = irexec
    button = Power
    repeat = 0
    config = ~/scripts/suspend.sh
end

```

where the script suspend.sh is

```
#!/bin/bash
pmi action suspend
```

you need to chmod +x scripts/suspend.sh

after restarting lirc, i can suspend without problem.

Now, to resume using the power button isn't trivial.  First, you need to setup /proc/acpi/wakeup so that your USB device can wake up the system.  Examples on the web were for USB0 but USB3 worked for my remote.  The easiest is to try the different USB interfaces one by one.

To list the wakeon devices:
```
sudo cat /proc/acpi/wakeup
```

To toggle (enable/disable) an interface, e.g. USB3

```
sudo sh -c 'echo "USB3" >> /proc/acpi/wakeup'
```

each time, suspend then try to resume using the power button.  Once you have found the right interface, e.g. USB3, you need to add the command to rc.local so that the interface is enabled after each reboot.

Here's my /etc/rc.local
```
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
 echo "USB3" >> /proc/acpi/wakeup
exit 0
```

Unfortunately, I haven't found a way to turn the computer On with the remote, but I'm quite happy with suspend and resume working.

---

### Post by Dugger5688 on 2010-02-10
How did you get 5.1 working, just curious because I was looking at that board for a new build.  For [ON] from. USB you might be out of luck. It only works if your board allows USB to boot your computer (meaning, your usb port can send a signal to boot up, not necessarily boot from USB disk). Even then the most you can do is have it boot on any remote keypress.  Assuming you have a USB remote.

---

### Post by wardy277 on 2010-02-11
I have researched about the usb waking o nthe Zotac ION boards, the new ones have this feature.

for 5.1 all i did was add
```
options snd-hda-intel model=3stack-6ch-dig
```
to the end of /etc/modprobe.d/alsa-base

I also changed  
```
; default-sample-channels = 2
```
to be 6 in /etc/pulse/daemon.conf, but no sure if that was needed

After a reboot and a restart of the pulse audio server i saw there were surround sound options in the sound preferences.

I had to connect my orange lead to the pink microphone jack and black lead to the blue line in jack

Another note, It took me ages to find but there is a test to check that the speaker configuration is correct:

```
speaker-test -Dplug:surround51 -c6 -l1 -twav
```

---

### Post by SalmonSella on 2010-03-03
I was fine up until step 4. But when I press the HOME button (the green middle one, yes?), I get no response. When I restart Lirc re step 3 I get the following:

 * Stopping remote control daemon(s): LIRC                              [ OK ] 
 * Loading LIRC modules                                                          [ OK ] 
 * Starting remote control daemon(s) : LIRC                              [ OK ]
user@user-desktop:~$ irexec -d

Is this expected. Once XBMC is open it functions fine, just getting it to launch XBMC is a pain.

---

### Post by Dugger5688 on 2010-03-03
> **SalmonSella said:**
> I was fine up until step 4. But when I press the HOME button (the green middle one, yes?), I get no response. When I restart Lirc re step 3 I get the following:

 * Stopping remote control daemon(s): LIRC                              [ OK ] 
 * Loading LIRC modules                                                          [ OK ] 
 * Starting remote control daemon(s) : LIRC                              [ OK ]
user@user-desktop:~$ irexec -d

Is this expected. Once XBMC is open it functions fine, just getting it to launch XBMC is a pain.

Well yes that is the correct output. 

Try typing in 'irw' to a terminal, then pressing your HOME key while irw is running. Paste output here. Otherwise you can try manually running the scripts one by one and adding in some debugging output ie.

```
echo [some text to help you out] 
```

---

### Post by ntetreau on 2010-03-04
Dugger is right, try running the startxbmc.sh script manually and see if XBMC starts.

Additionally, I'm having problems with irexec either crashing or not restarting after suspend/resume, if someone has an idea...

---

### Post by wardy277 on 2010-03-04
I have also noticed it crashing. I mainly notice it when XBMC freezes (not very often) i have setup a command to open gedit, which normally brings me back to gnome with xbmc minimized(not full screen). This works if xbmc hasn't crashed, but when it does, it seems like lirc doesn't respond.

---

