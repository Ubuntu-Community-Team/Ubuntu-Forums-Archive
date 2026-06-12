---
title: "Hardy(64) 8.04 Mythtv 0.21 Mythwelcome - shutdown hangs occasionally"
date: 2008-05-05
forum: Mythbuntu
---

### Post by jb5 on 2008-05-05
Hardy-64 MythTV - Mythwelcome - Machine doesn't always power off fully

Hi - First Upgrade path was as follows :-

Gutsy(64)- Clean Install
Mythtv 0.20
Mythtv 0.21 via Gutsy Backports
Hardy(64) - Upgrade

It's a combined frontend/backend & utilized MythWelcome successfully to turn off/on my Myth box via ACPI as required by recording schedule.

After upgrade to Hardy I noticed that sometimes the box would not shut down completely. 
In Gutsy mythwelcome was able to successfully wake and shutdown the mythtv box fine every time but now Hardy sometimes only gets as far as spinning down the hard drives then hangs at that point. 
The last command seen is ```
[some long number]Power Down
``` and a blinking cursor, the fans are still powered as is the GPU etc.

Some digging showed that some people had success with a similar problem by booting the kernel with the nosplash option set. I tried this but with no success. The other solutions I found involved using APM rather than ACPI, but I use ACPI to wake my box up so I think that avenue is closed to me.

I thought I would give the new scripts a go, that shutdown via HAL i.e. ```
/usr/share/mythtv/myth-halt.sh
```
This command shuts down the myth box when run from the command line, but when run from within mythwelcome the countdown just keeps cycling, starting again when it reaches the end! At this point I'm stuck and would welcome any suggestions / ideas!

For completeness my setup is :-
Mythwelcome
```
 
set wakeup      mythshutdown --setwakeup $time --settime $time
time format     yyyy-MM-dd hh:mm:ss
restart         <left blank>
reboot          sudo shutdown -r now  --- this was changed to -----   /usr/share/mythtv/myth-reboot.sh
shutdown        sudo shutdown -P now  --- this was changed to -----   /usr/share/mythth/myth-halt.sh 
xterm           xterm
start Front end /usr/bin/mythfrontend

```

& in Myth Backend - shutdown and wakeup options
```

startup                   <left blank>                
block shutdown before client connected <checked>
idle                      50
max wait                  15
startup before recording  300
wake-up time format       yyyy-MM-dd hh:mm:ss
command set wakeup        sudo /usr/bin/MythWakeSet $time
server halt               mythshutdown --shutdown
pre-shutdown              mythshutdown --check
```

---

### Post by jb5 on 2008-05-08
OK - The only way I could get the /usr/share/mythtv/myth-halt.sh script
to work from MythWelcome was to put sudo in-front of it and add the file to sudoers!

Is this the expected behaviour, or is there something peculiar about my setup?

To be clear Ubuntu was installed first followed by Myth Control Centre, which was then used to install and setup Mythtv. The system was then upgraded as documented above.

The machine was setup via MCC to auto login to my jb user account and run MythWelcome / MythTV from there, but as MythWelcome runs as MythTV user it is unable to run the shutdown script unless I add sudo to the front of the command!

The command works as expected when run from a terminal, as user jb. i.e. no sudo required!

Is anybody else successfully using these scripts in MythWelcome?

[NB - This may be moot anyway as using the script under sudo still doesn't resolve my occasional failed shutdowns!]

---

