---
title: "Whats the &quot;best&quot; way to setup power saving in mythbuntu?"
date: 2009-08-08
forum: Mythbuntu
---

### Post by geekyhawkes on 2009-08-08
Hi, 

I currently have a single myth front/back end machine in my living room connected to my tv which i use as my primary home entertainment media center.  I am controlling myth using mythpiiwii and and wiimote.  I am also using this machine to throw music to my squeezebox upstairs via wifi.

The main question i have is regarding power saving, and the best way to set it up on my machine.  I am not fussed about screensaver and monitor shutdown style power saving as i just switch off the tv when not in use, but i am interested in my standby options for the myth box. 

Obviously I would like it to wake itself up should i have scheduled a recording during a standby period, but I would also require it to wakeup when i want to access my music via my squeezebox. 

Does anyone have any tips on the best way i could achieve this?  (I will be adding an additional front end within 8months, but I am willing to look at the powersaving setup again when the system design changes).

Thanks

---

### Post by dsbw on 2009-08-08
Well, the best way is for it to happen automatically.

Only part snark: The first successful box I set up automatically used PowerNowd, turning down the fan during low use, the current one doesn't even seem to know about it. (Both AMD, though.)

Have you read [this? ]("https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake")

---

### Post by geekyhawkes on 2009-08-10
Thanks for the link, i had missed that.  I will go through it later and see how i get on.  I dont suppose anyone knows if squeezebox requests will cause the myth box to wake up or not?

---

### Post by DrCrispPacket on 2009-08-11
> **geekyhawkes said:**
> Thanks for the link, i had missed that.  I will go through it later and see how i get on.  I dont suppose anyone knows if squeezebox requests will cause the myth box to wake up or not?

I'm not sure what squeezebox does, but any remote MythFrontend device can wake up the server using the wakeonlan or wol command (you may have to 
```
apt-get install wakeonlan
``` from your repository) provided the wake-on-lan feature is enabled in your server. 

Any other device that can issue the wake-on-lan command (specifying the hardware address of your server's network card, eg 
```
wakeonlan 00:40:ca:90:bd:97

```will also work.

For example, you can issue this from the command line in a linux machine, and there is probably a similar wake-on-lan client available for Windows machines.
There is a place to insert a wake-on-lan call in one of the MythFrontend setup screens.

Hope this helps

---

### Post by SiHa on 2009-08-11
I too use wakeonlan. My backend has scheduled shutdown between 11pm and 7am (unless recordings scheduled). I use the above to wake it from the remote frontend should I have a bout of insomnia (or my six-month old does!)

---

### Post by geekyhawkes on 2009-08-11
SiHA, how have you setup the sleep from 11 - 7 unless recording? If i could set this kind of shutdown up but more 12 - 4pm unless being used it would match my power saving needs pretty much spot on.  Currently im leaving my machine fully on all the time and im not sure its that effecient!

---

### Post by SiHa on 2009-08-11
Yes, I had my BE server running 24/7 for about six months until I got round to sorting it out. 

What follows is a bit dirty but it serves my needs:

I used the guide [[COLOR="Blue"]_here_[/COLOR]](https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake) using /proc/acpi/alarm, which is the method used in 8.04 and earlier. If you're using anything later, I think you have to use /sys/class/rtc/rtc0/wakealarm. Whatever, the basic methodology is still the same.

So.

1) I followed the above guide to simply get the system to shutdown when idle, and wakeup for a recording. **NB** to qualify as 'idle' the frontend (if on a BE/FE combo) must not be running.

2) was to write a pre-shutdown script that checks the time
```
#!/bin/bash
#
# Simple script to check the time, and whether it is safe to shutdown
# 24th Nov 09
#

hour=`date +%H`

if [ $hour -gt 22 ] || [ $hour -lt 6 ]; then
	echo `date +%F_%T` The hour is "$hour", it is nighttime, OK to shutdown
#	echo safe
	exit 0
else
	echo `date +%F_%T` The hour is "$hour", it is daytime, not OK to shutdown
#	echo not safe
	exit 1
fi

```
so even if the system decides it is idle, the above script will stop it shutting down if it is between 06:59 and 22:59. But the frontend is still running so it will never be idle.

3) I added an entry to my crontab:```
00 23 * * *  /usr/local/bin/killmyth

```
contents of killmyth:```
#! /bin/bash
#
# Kill Mythfrontend so that backend will go idle and shutdown

killall -9 mythfrontend.real

```
Now I know that 3) sort of nullifies 2) as the system will never go idle until the frontend is shutdown, but it's just belt 'n braces.

So now the system will shutdown (if after 23:00) and set the wakeup time for the next recording. To get it to wakeup at 7am, if the next scheduled recording is later, I modified the MythWakeSet script:
```
#!/bin/bash

# MythWakeSet
#
# set mythtv wake-up time with UTC-adjusted time
#

# temp file for working with time
temp_stamp=/home/mythtv/timestamp

# store the wake time passed from mythbackend
echo $1\ $2 > $temp_stamp

**[COLOR="Red"]# New Bit Start[/COLOR]**
# Addition to reset MythTV wakeup time to 0700hrs 'tomorrow'
# or the next time it occurs,  if 
# earlier than the next scheduled recording.
# uses 'date +%s' for calculations. %s = seconds since epoch, much simpler to
# do comparisons with a number, rather than days of week etc...


now=`date +%H`
if [[ $now -lt 7 ]] ; then
	tomorrow=`date +%c -d "0700"`          # after midnight, so set to 0700 today
	echo "today"
else
	tomorrow=`date +%c -d "+1 day 0700"`   # before midnight set to 0700 tomorrow
	echo "tomorrow"
fi

nextrectime=`date +%s -f "$temp_stamp"`

# if 0700 'tomorrow' is earlier than next scheduled recording then change it to 0700
# otherwise leave unchanged

if [[ `date +%s -d "$tomorrow"` -lt $nextrectime ]] ; then
	wakeup=$tomorrow
	echo $tomorrow > $temp_stamp
fi
**[COLOR="red"]# New Bit End[/COLOR]**

# Read the date in *locale* time format and tag the time-zone info to the wake time
localeadd=$(/bin/date -f $temp_stamp +%F\ %T\ %z)
echo $localeadd > $temp_stamp
#echo $localeadd

# adjust this to UTC and store the final wake time
utcadj=$(/bin/date -u -f $temp_stamp +%F\ %T)
#echo $utcadj

# set the alarm
echo $utcadj > /proc/acpi/alarm

```

This was the bit that gave me the headache. It took me a while to figure out how to define 0700 'tomorrow', and even longer to suss how to do comparisons with the date operator that actually worked. Who knows - perhaps that's the whole idea of 'seconds since the epoch' as an output.

Anyway, hope this helps a bit.

PS I believe Mythwelcome has a bit where you can specify daily 'awake' periods, but I didn't want to add another interface that might damage the (at the time)pretty poor WAF.

---

### Post by jb5 on 2009-08-12
> **SiHa said:**
> PS I believe Mythwelcome has a bit where you can specify daily 'awake' periods, but I didn't want to add another interface that might damage the (at the time)pretty poor WAF.

I went down the MythWelcome [MW] route. It does have a couple of definable 'always on' time periods.

The WAF shouldn't be too big a problem, MW uses the same theme as the frontend. 

I have it set up such that on boot it starts on the MW screen. 
If a recording is about to start MW 'realises' that it has woken automatically for a recording, and will shut down when it has finished. 
If **I** power on the box, then on the MW screen I press enter on the remote and that takes me into the frontend. 
When I have finished watching stuff for the day, I exit the frontend back to the MW screen. It will then sit there until it has finished any active recordings or start to shut down after a user definable period.

Once it's set up it works really well. The hardest part (for me) was determining which way round the MW and MythBE commands went. 
(On my system the commands were reversed when compared with those in the WIKI).

---

### Post by SiHa on 2009-08-12
Thanks. I'll probably be upgrading when the mythical 0.22 arrives to make use of VDPAU and DVB-S2. Perhaps I'll give Mythwelcome a go then.

---

