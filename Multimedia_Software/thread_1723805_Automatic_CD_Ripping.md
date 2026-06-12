---
title: "Automatic CD Ripping"
date: 2011-04-07
forum: Multimedia Software
---

### Post by msmith78 on 2011-04-07
Hi,

I currently have a little box with Mediatomb installed which I use to stream to my Linn DS. Is there an application that I can use that will automatically rip a CD when it is inserted into the machine and then eject when it is complete?

---

### Post by mc4man on 2011-04-07
I only use these 2 which both can -  rubyripper (cli) and abcde can be run non interactivly and can easily be set as the default autorun option
rubyripper would be set up as needed in the gui, abcde as set in .abcde.conf (preferably a custom one in ~/

You could either set directly in File management > media > CD Audio > open with other application > use a custom command or make a small script, put in path, and just use script name as the custom command

Other choice would be whether to run silently in background or have a terminal open while rip is going on (I prefer the later for various reasons

Ex. of scripts in ~/bin (terminal opens as rip starts and closes when done
for rubyripper (current 0.6) named arip1

```
#!/bin/bash
gnome-terminal -e "rrip_cli -d"
```

for abcde named arip2 (you'd just use abcde instead of abcde-nero

```
#!/bin/bash
gnome-terminal -e "abcde-nero -N"
```

side note - both RR and abcde work off of a default cdrom device in their respective settings.
I've not found any **non**-interactive command line switch to adjust the device in RR, but abcde does have one.

So with multiple cd/dvd drives  i use this script instead, will auto rip from any internal or external drive

```
#!/bin/bash
CD=/dev/`echo $1|sed -e "s/.*\(sr[0-9]\).*/\\1/"`
gnome-terminal -e "abcde-nero -N -d //$CD"

```

---

