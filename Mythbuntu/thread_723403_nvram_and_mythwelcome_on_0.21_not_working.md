---
title: "nvram and mythwelcome on 0.21 not working"
date: 2008-03-13
forum: Mythbuntu
---

### Post by moonkuh on 2008-03-13
Hi all i have a problem with nvram-wakeup and the new version of mythtv.

nvram-wakeup works if i use it manuell

```
htpc@htpc-desktop:~$ sudo -H /usr/sbin/nvram-wakeup -C /etc/nvram-wakeup.conf --directisa --settime $((`date +%s` + 20 * 60))

All values are displayed as they are stored in the nvram/rtc.
(and do not correspond necessarily to the system date/time)

WakeUp  : Enabled (0x1B)
Day     : 13 (0x1B)
Hour    : 17 (0x11)
Minute  : 21 (0x15)
Second  : 12 (0x0C)
rtcDay  : 13 (0x13)
Checksum: 0x7CA7

Enabling (0x1B) WakeUp-on-RTC in nvram.
New Day     : 13 (0x1B)
New Hour    : 18 (0x12)
New Minute  : 34 (0x22)
New Second  : 58 (0x3A)
New rtcDay  : 13 (0x13)
New Checksum: 0x7CE3

Now really WRITING into /dev/nvram...

```

i have to use --directisa because without i get

```
htpc@htpc-desktop:~$ sudo -H /usr/sbin/nvram-wakeup -C /etc/nvram-wakeup.conf --settime $((`date +%s` + 20 * 60))
nvram-wakeup: /dev/nvram: No such file or directory

```

After a restart

```
htpc@htpc-desktop:~$ cat /proc/acpi/alarm
2008-00-13 18:34:58

```

show's me the correct time
Everything is working fine, but if mythwelcome and mythbackend have to do this i only get this

```
2008-03-13 18:43:46.155 CheckShutdownServer returned - OK to shutdown
2008-03-13 18:43:46.177 Running the command to set the next scheduled wakeup time :-
                                                mythshutdown --setwakeup 2008-03-13T19:13

All values are displayed as they are stored in the nvram/rtc.
(and do not correspond necessarily to the system date/time)

WakeUp  : Enabled (0x1B)
Day     : 13 (0x1B)
Hour    : 17 (0x11)
Minute  : 21 (0x15)
Second  : 12 (0x0C)
rtcDay  : 13 (0x13)
Checksum: 0x7CA7

2008-03-13 18:43:46.440 Running the command to shutdown this computer :-
                                                sudo -H mythshutdown --shutdown


```

nvram-wakeup don't put the time in the bios.
Manuelly it works, backend and mythwelcome it doesn't.
An error message would help me alot.......

Can it be this one ?
 mythshutdown --setwakeup 2008-03-13T19:13
The wrong time format?

I don't know where the error is :(

---

### Post by majoridiot on 2008-03-13
from the mythwelcome wiki @ [http://www.mythtv.org/wiki/index.php/Mythwelcome](http://www.mythtv.org/wiki/index.php/Mythwelcome) 

> nvram-wakeup command -  command to set wakeup time in bios
	                        
                            ''recent changes(post 0.20.2) to the time format code cause problems''
                            
                             nvram-wakeup only accepts time_t (seconds since
                             unix epoch) as a date/time format. mythshutdown only uses
                             ISO-8601 (yyyy-MM-ddThh:mm:ss). Both programs now use the 
                             same setting name in the database for their format
                             token. Since getting the wakeup time in the BIOS involves
                             using both programs, it's now impossible.
                             
                             You can get around this like this
                             
                             "date -d "`echo $time | sed "s/T/ /"`" +%s | xargs nvram-wakeup -s"
                             
                            [b] Replace the preset arguments on the end with the ones that work
                             for you.[/b]
                             
                             The sed is in there to strip the "T" because gnu date can't parse ISO-8601 format
                             properly (a bug known for at least 3 years), despite being
                             able to produce it.

---

### Post by moonkuh on 2008-03-13
Thank you :)

But I don't get it :(
Where I have to put this "date -d "`echo $time | sed "s/T/ /"`" +%s | xargs nvram-wakeup -s" ?

Is this right?

```

 "date -d "`echo $time | sed "s/T/ /"`" +%s | xargssudo -H /usr/sbin/nvram-wakeup -C /etc/nvram-wakeup.conf --directisa

```

or must it be in the mythtv-setup under "set wakeuptime" or somewhere else?

---

