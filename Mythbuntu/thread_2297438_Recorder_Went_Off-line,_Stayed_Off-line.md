---
title: "Recorder Went Off-line, Stayed Off-line"
date: 2015-10-03
forum: Mythbuntu
---

### Post by bilkay on 2015-10-03
In the middle of recording two programs, the recorder stopped recording  with no hint given in the backend log as to why. Subsequent scheduled  programs did not record at all. The two truncated shows showed up in  yellow in the Recorded Programs list. The subsequent programs which did  not record were not on the Recorded Programs list at all, but did show  in the Previously Recorded list with red bullets, status "F" and the  notation "Recorder Off-line". The truncated programs and the  subsequently un-recorded programs were on two successive days with a  mythtv-backend (crontab) restart in between. I could, however, play  previously recorded programs while the recorder was "Off-line".  Everything back to normal following re-boot of computer.

What could possibly have caused this? If this is a recurring problem, it renders Mythtv more trouble than it's worth.

---

### Post by dmjenso on 2015-10-03
> **bilkay said:**
>  If this is a recurring problem, it renders Mythtv more trouble than it's worth.

Frustration duly noted.  

You didn't mention anything about your hardware so there isn't much to go on except in the 9 years I've been recording with MythTV, that has happened to me twice and it was hardware failing both times.  One time my system board failed and I had to replace that, and the other time my Hauppauge tuner failed.  After 3 or 4 reboots, the card was no longer recognized and I was afraid it was the system board again, but I swapped the HVR-1600 with another known good one and it came to life.  If you have an internal card, reseat the card and if it keeps happening, try cleaning the connector pads.  If you have an external tuner, try a different USB port if it happens again.

syslog or dmesg should let you know if your hardware is barfing up.

---

### Post by bilkay on 2015-10-04
Thanks for the good news/bad news. Now all I have to do (besides the hardware maintenance) is figuring out a way for the system to notify me when this happens.

---

### Post by Ken_Lightbody on 2015-10-04
I have also had this happen to me on numerous occasions.  I have two Mythbuntu systems each with two dual tuner cards.  When a tuner misbehaves all programs utilizing that card will fail.  On average I would say this occurs at least once a week in each system.  By having two systems duplicating my recording schedule I have only missed two nights where both systems had tuners that failed for the same set of programs (over a span of four years).  When presented I was told that this is a driver problem, but I believe upper layers should realize the failure and either reinitialize the failing tuner or place it out of service and reassign programs to working tuners. My specific tuners are [COLOR=#000000][FONT=arial]Hauppauge 1229 HVR-2250 dual tuner cards.  Over a three month period I have tried four different computer systems with six different tuner cards.  There seems to be no pattern that pointed to bad computer hardware.  I have had another user email me and confirm my findings. I automatically have cron shutdown my systems at 3 AM and have the BIOS  turn the system back on at 6:45 PM so that my tuner cards are initialized daily. [/FONT][/COLOR]

---

### Post by bilkay on 2015-10-05
A problem with the daily reboot is that if I reboot without the HDMI monitor on, the HDMI monitor won't work. I'd have to make sure the monitor was on when rebooting. This has only happened once with my Hauppauge 2255 card which I've been using since February.

To minimize the damage, I wrote the following script (run periodically by cron) to check for problems:

```
#! /bin/bash

admin={your e-mail}
cd /Mythtv

[ -f mythdiag.1 ] && mv mythdiag.1 mythdiag.0
echo "select title from recordedprogram where videoprop regexp 'DAMAGED' ;" | `which mysql`  -u mythtv -D mythconverg --password='mythtv' >  mythdiag.1
echo "select title from oldrecorded where recstatus = 12 ;" | `which mysql`  -u mythtv -D mythconverg --password='mythtv' >>  mythdiag.1

if [ -f mythdiag.0 ]
then
    x=$(diff mythdiag.?|grep "^>")
    if [ -n "${x}" ]
    then
        echo "${x}"|`which mail` -s "Mythtv Damaged or Missing Recording" ${admin}
        xmessage -c "Mythtv Recorder Problem"
    fi
fi
```

---

### Post by bilkay on 2015-10-08
> **Ken_Lightbody said:**
> [COLOR=#000000]...[FONT=arial] I automatically have cron shutdown my systems at 3 AM and have the BIOS  turn the system back on at 6:45 PM so that my tuner cards are initialized daily. [/FONT][/COLOR]

Is this effective? It happened for me again but only on one card this time. The last time, both cards (HVR-2255) failed simultaneously (or within seconds) while recording two programs. This time, one card failed at the end of a 30 minute program which was in the middle of an hour long program being recorded by the other card. Another 30 minute program immediately following the first did not record at all. The first program seems to have recorded in its entirety but shows up in yellow, i.e., videoprop = "DAMAGED" (in part).

---

### Post by bilkay on 2015-10-29
> **bilkay said:**
> Is this effective? It happened for me again but only on one card this time. The last time, both cards (HVR-2255) failed simultaneously (or within seconds) while recording two programs. This time, one card failed at the end of a 30 minute program which was in the middle of an hour long program being recorded by the other card. Another 30 minute program immediately following the first did not record at all. The first program seems to have recorded in its entirety but shows up in yellow, i.e., videoprop = "DAMAGED" (in part).

This just happened again. This time, I had the following script run at 28 and 58 minutes after the hours when I usually record:

```
#! /bin/bash

cd /Mythtv

[ -f mythdiag.1 ] && mv mythdiag.1 mythdiag.0
echo "select title from recordedprogram where videoprop regexp 'DAMAGED' ;" | `which mysql`  -u mythtv -D mythconverg --password='mythtv' >  mythdiag.1
echo "select title from oldrecorded where recstatus = 12 ;" | `which mysql`  -u mythtv -D mythconverg --password='mythtv' >>  mythdiag.1

if [ -f mythdiag.0 ]
then
    x=$(diff mythdiag.?|grep "^>")
    if [ -n "${x}" ]
    then
        echo "${x}"|`which mail` -s "Mythtv Damaged or Missing Recording" admin
        xmessage -c -display :0 "Mythtv Recorder Problem"
    fi
fi
```

Later, two programs recorded simultaneously with no problem. One oddity was that a program marked not to record that normally runs the same time as the two 30 minute programs showed up in my email as damaged or missing.

---

### Post by khPWXxF on 2015-10-30
The problem of blank screen if HDMI screen is turned on after the computer is discussed here:

 [http://ubuntuforums.org/showthread.php?t=2282465](http://ubuntuforums.org/showthread.php?t=2282465)

hth
Phil

---

### Post by bilkay on 2015-10-30
> **khPWXxF said:**
> The problem of blank screen if HDMI screen is turned on after the computer is discussed here:

 [http://ubuntuforums.org/showthread.php?t=2282465](http://ubuntuforums.org/showthread.php?t=2282465)

hth
Phil
I should have noted later that my HDMI "problem" was more operator stupidity than a real problem. But thanks for the pointer. It may be useful to somebody.

---

### Post by bilkay on 2015-10-30
> **dmjenso said:**
> Frustration duly noted.  

You didn't mention anything about your hardware so there isn't much to go on except in the 9 years I've been recording with MythTV, that has happened to me twice and it was hardware failing both times.  One time my system board failed and I had to replace that, and the other time my Hauppauge tuner failed.  After 3 or 4 reboots, the card was no longer recognized and I was afraid it was the system board again, but I swapped the HVR-1600 with another known good one and it came to life.  If you have an internal card, reseat the card and if it keeps happening, try cleaning the connector pads.  If you have an external tuner, try a different USB port if it happens again.

syslog or dmesg should let you know if your hardware is barfing up.

I cleaned the connector pads and it happened again - exactly like a previous episode. I mean "exactly" - the same programs at the same time and failed at EXACTLY the same second into the first program, i.e., right at the end. I'm having a hard time believing this could be a hardware problem. The odds against two EXACTLY identical failures is astronomical.

---

