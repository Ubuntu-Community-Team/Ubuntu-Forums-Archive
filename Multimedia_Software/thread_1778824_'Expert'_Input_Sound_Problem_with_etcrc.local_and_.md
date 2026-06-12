---
title: "'Expert' Input Sound Problem with /etc/rc.local and rec script Ubuntu 11.04"
date: 2011-06-09
forum: Multimedia Software
---

### Post by hefferbh on 2011-06-09
Hi, i'm new in Ubuntu's Forums, 
so if i'm writing this problem in the wrong place please move it \o/

I'm no expert in Ubuntu but not a newbie i guess....

Ok, i'm having this trouble with INPUT SOUND trought Ubuntu 11.04:
I made a script that uses SoX to rec the INPUT SOUND trought commands made in a simple script...
Heres part of the code that runs in an infinite loop:

```
rec -c 2 22050 /mnt/hd2/audio/$arquivo.mp3 trim 0 15:00 || { zenity --error --text 'rec failed, closing censuraUFMG...'; exit 1; }
```The program always worked fine in ubuntu 8.04 LTS... more than a year of use....
And now i decide to change to Ubuntu 11.04, recompiled SoX to run with mp3, and set
the script to start in /etc/rc.local  with 'sudo' of course...

> angelop@Angelop-desktop:~$ cat /etc/rc.local
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
sleep 40

/mnt/hd2/censuraUFMG &

exit 0
And my problem is:
Starting ubuntu, everything seems to work fine ....
( Remeber that i have 40 seconds until the script starts )
In SOUND PREFERENCES, i can see in INPUT that the sound goes trought the bar of activity INPUT LEVEL....
The sound is being capture as it should.... ( receiving audio trought p2 cable trought other computer )
But when /etc/rc.local runs the script 'censuraUFMG'...
The sound stop trought INPUT LEVEL and no sound is capture any more.... 

If i remove "/mnt/hd2/censuraUFMG &" from /etc/rc.local and starts ubuntu again....
The INPUT LEVEL shows that everything is ok...
And if i run the script by a terminal comand '$ /mnt/hd2/censuraUFMG" trought  'screen'...
I can see that it does not cut out the INPUT LEVEL ... and the sound works fine, as the rec with SoX....

I don't really know and do not have any clue on HOW TO FIX THIS PROBLEM ...
So, anyone could HELP ME ?

> angelop@Angelop-desktop:~$ uname -a
Linux Angelop-desktop 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 i686 i386 GNU/Linux> angelop@Angelop-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
...
Thanks in advanced!

---

### Post by hefferbh on 2011-06-10
up up plzz =/

---

### Post by hefferbh on 2011-06-10
Updated: 
Well.. i have some news about my problem...
i reeeeeaaaally need somebody's helps!!!!!!

When i remove the start of the script **censuraUFMG** of ' /etc/rc.local  ' and starts trought 'Sessions Preferences' ( sessions aplications ) everything goes just fine !!! 

But when i remote acess this computer trought NX CLIENT it runs another 'censuraUFMG' script... and i do not want that ! =/

Does anyone know how to fix it ? I mean, when you remote access this computer i do not want another start of this script added in Sessions Preferences....

HELPPPP ANY ONE PLZZ =((((

---

### Post by hefferbh on 2011-06-13
Urgent up pleaase =( any comments are more than welcome..

---

