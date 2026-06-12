---
title: "tvtime flashes on  then off"
date: 2011-12-06
forum: Multimedia Software
---

### Post by Mark_in_Hollywood on 2011-12-06
lspci:

03:00.0 Multimedia controller: Philips Semiconductors SAA7160 (rev 01)

mark@Lexington-19:~$ tvtime-scanner
Reading configuration from /etc/tvtime/tvtime.xml
Scanning using TV standard NTSC.
videoinput: Driver won't tell us its norm: Invalid argument
videoinput: Can't get tuner info: Invalid argument
videoinput: Driver won't tell us its norm: Invalid argument
videoinput: Can't get tuner info: Invalid argument

    No tuner found on input 0.  If you have a tuner, please
    select a different input using --input=<num>.

mark@Lexington-19:~$ tvtime
Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
I/O warning : failed to load external entity "/home/mark/.tvtime/tvtime.xml"
I/O error : Permission denied
I/O error : Permission denied
Cannot change owner of /home/mark/.tvtime/tvtime.xml: Permission denied.
videoinput: Driver won't tell us its norm: Invalid argument
videoinput: Can't get tuner info: Invalid argument
videoinput: Driver won't tell us its norm: Invalid argument
videoinput: Can't get tuner info: Invalid argument
mixer: find error: Success
mixer: Can't open mixer default, mixer volume and mute unavailable.
mixer: Can't open device default/Line, mixer volume and mute unavailable.
videoinput: Can't read frame. Error was: Invalid argument (0).
videoinput: Can't read frame. Error was: Invalid argument (0).
Found "USB Device 0x46d:0x807 : USB Audio (hw:1,0)"
I/O error : Permission denied
I/O error : Permission denied
videoinput: Can't read frame. Error was: Invalid argument (0).
videoinput: Can't read frame. Error was: Invalid argument (0).
videoinput: Can't mute card.  Post a bug report with your
videoinput: driver info to [http://tvtime.net/](http://tvtime.net/)
videoinput: Include this error: 'Invalid argument'

where is the list of tuners that tvtime recognizes and how do I determine which number is for mine? My device is an AverMedia HDTV duet (model A188).

---

