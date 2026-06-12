---
title: "Suspend doesn't work in Mythbuntu 8.04.1"
date: 2008-12-26
forum: Mythbuntu
---

### Post by bmwman on 2008-12-26
My BE/FE machine works perfect for the most part. I was trying to put it to "Sleep" the other day and it doesn't work. Hibernate works fine but I want to use Suspend so I can wake it with a keyboard. This works fine on my frontend computer upstairs which is an older PC.

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

Please help me figure this out.

Thanks

P.S. Here is my sleep.sh
> 
#!/bin/bash

. /etc/default/acpi-support
. /usr/share/acpi-support/power-funcs
. /usr/share/acpi-support/device-funcs
. /usr/share/acpi-support/policy-funcs

DeviceConfig;

if [ x$ACPI_SLEEP != xtrue ] && [ x$1 != xforce ]; then
  exit;
fi

# If gnome-power-manager or klaptopdaemon are running, let them handle policy
if [ x$1 != xforce ] && [ x$1 != xsleep ] && [ `CheckPolicy` = 0 ]; then
    exit;
fi

if [ x$LOCK_SCREEN = xtrue ]; then
    if pidof xscreensaver > /dev/null; then 
	for x in /tmp/.X11-unix/*; do
	    displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
	    getXuser;
	    if [ x"$XAUTHORITY" != x"" ]; then	    
		export DISPLAY=":$displaynum"
		. /usr/share/acpi-support/screenblank
	    fi
	done
    fi
fi

# Generic preparation code
. /etc/acpi/prepare.sh

if [ x$DISABLE_DMA = xtrue ] && [ -b /dev/hda ]; then
  hdparm -d 0 /dev/hda
fi

echo -n $ACPI_SLEEP_MODE >/sys/power/state

if [ x$RESET_DRIVE = xtrue ] && [ -b /dev/hda ]; then
    hdparm -w /dev/hda
    hdparm -C /dev/hda
    hdparm -C /dev/hda
    hdparm -C /dev/hda
    hdparm -d 1 /dev/hda
fi

if [ x$DISABLE_DMA = xtrue ] && [ -b /dev/hda ]; then
  hdparm -d 1 /dev/hda
fi

# Generic wakeup code
. /etc/acpi/resume.sh

---

### Post by jboehm on 2008-12-27
Do you have Hauppauge PVR-X50 cards?  The kernel module need to be unmounted before sleep and restored afterwards.  Without doing this a system will crash when it powers back up and tries to access these cards.  There is a solution out there if you do some searching, and probably also a bugreport.  I chose to go a greener route and power down and up all the way using /sys/class/rtc/rtc0/wakealarm.  Find help here
[http://www.mythtv.org/wiki/index.php/ACPI_Wakeup](http://www.mythtv.org/wiki/index.php/ACPI_Wakeup)

Look about half way down the page.  The one trick is cron jobs.  I wrote a little script that forces a boot time of 6am and relocated all of my cron jobs and filldatabase durring that time.

Jon

---

### Post by bmwman on 2008-12-28
I had the ACPI wake working but I don't use it.  I rarely use my HTPC for recording TV. Mostly i use to listen music or watch a movie. So I want to manualy wake it either by the power button, keyboard or remote. The machine is inside my TV cabinet and it get's really hot in there so i want it to suspend when i don't use it. I currently have my cable box plugged via firewire but I don't use it. I also have HDhomerun but it's not plugged in right now. I don'thave any PVR-X50 cards.

---

