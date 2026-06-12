---
title: "Problem with suspend system via MCE remote"
date: 2008-12-20
forum: Mythbuntu
---

### Post by bmwman on 2008-12-20
I was following this thread:[http://ubuntuforums.org/showthread.php?t=675455]("http://ubuntuforums.org/showthread.php?t=675455")
I'm trying to set up my HTPC to go to StandBy and resume via the MCE remote. I tested it and here is what I get:

```
backend@backend:~$ ~/.mythtv/mythscripts/suspend.sh
 * Shutting down ALSA...                                                 [ OK ] 
 * Saving the system clock
/etc/acpi/sleep.sh: line 39: echo: write error: No such device
/etc/acpi/resume.d/17-video-restore.sh: line 5: /var/lib/acpi-support/vbestate: No such file or directory
Function not supported
 * Setting the system clock
ifup: interface eth0 already configured
 * Setting up ALSA...                                                    [ OK ] 
FATAL: Module acpi_sbs not found.
FATAL: Module acpi_sbs not found.
backend@backend:~$ 

```

Any ideas how to get it work?

---

### Post by bmwman on 2008-12-21
Any ideas?

---

### Post by t3chn0b0y on 2008-12-21
I was able to control the monitor to work with the TV button

I edited  /etc/rc.local and added   irexec -d /root/.lircrc
in my .lircrc in my home directory I added


begin
    remote = mceusb
    prog = irexec
    button = TV
    repeat = 4
    config = /usr/local/bin/monitorpowerbutton.sh
    end

and created /usr/local/bin/monitorpowerbutton.sh  as follows:

code snip ----->

#!/bin/bash

STATUS=`xset -q | grep "Monitor is" | awk '{print $3}'`

if [ "${STATUS}" = "On" ]
then
   xset dpms force off
else
   xset dpms force on
fi
exit 0

<-----------------

If no one responds back to your message I will give it a go
with the suspend here in a few with the PC button and see if I
can't get it going..  I was thinking something similar to what
i did with the TV button to control the monitor could be done
with the pc for the PC button and using the shutdown script...?

---

### Post by bmwman on 2008-12-25
I believe it's the "Sleep" script. I tried to manually put the computer to "Sleep" and it didn't work. Hibernate and Shutdown works fine. 

Any ideas?

---

### Post by bmwman on 2008-12-26
bump

---

### Post by bmwman on 2009-01-02
Well, for whatever reason my Suspend works fine now. I haven't really changed anything. So I am able to Suspend via the remote now. I'm using the /usr/share/mythtv/myth-halt.sh script and when I press the Power button on my remote, the machine goes to standby. Now I can't turn it back on with the remote though, I have to push the power button. At least i have some progress.

Any ideas why I can't turn on the PC via the remote?

---

### Post by uncle hammy on 2009-01-02
TO wake it up via the remote, you are going to find yourself very much at the mercy of your motherboard.  It will all depend on what sort "wake on" options you have in your BIOS.  You'll need a wake on usb, I suspect.

---

### Post by bmwman on 2009-01-02
I do have WakeOnUSB and it's enabled. I also have Wake on mouse(set to double click) and Wake on Keyboard (set to any key). Something else that I noticed, after i suspend the PC with the remote, the IR only blinks if I press the Power button on my  remote. Any other button doesn't register(no blinks).

---

