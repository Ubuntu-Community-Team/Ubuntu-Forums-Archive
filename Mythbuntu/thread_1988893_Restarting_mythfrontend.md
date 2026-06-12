---
title: "Restarting mythfrontend"
date: 2012-05-28
forum: Mythbuntu
---

### Post by teeedubb on 2012-05-28
Hey all..

Im setting up a mythbuntu 12.04 combined fe/be for my parents. Im using mythwelcome and ACPI suspend and wakeup to not have it running 24/7 and as mythth doesnt have a 'exit when idle' option I want to have the power button on the remote kill the myth-frontend process so the htpc can power down.

When using:

```
killall mythfrontend.real
```I get: 

mythfrontend.real: no process found

If I try:

```
kill $(pidof mythfrontend.real)
```I get a notification saying mythfrontend has crashed and is being restarted, which is what not what Im after.

So does anyone know of a way I can kill mythfrontend from the command line and not have it restart? Any help is appreciated!

---

### Post by speed32219 on 2012-05-28
try killall mythfrontend first
then killall mythfrontend.re

could also use killall -9 mythfrontend and repeat with the .re

---

### Post by Lester_Burnham on 2012-05-29
Hi teeEdubb,

Can't they just exit out of mythfrontend and not have it auto start when the machine starts for recordings? It's only back and select yes.

I pretty much always use ACPI wake (complete shutdown) on all my backends now and I start the frontend manually. That way it can still shutdown when recordings are finished. To keep it awake, just start a Frontend. To start the frontend, I use irexec on the LIVE TV button.


I've tried suspending, but shutting down is far more reliable and way less trouble.

Ps: I'm pretty sure you can stop mythfrontend auto starting in the mythwelcome options.

Lester

---

### Post by nhtrader on 2012-05-30
teeedubb,

I too am having the endless loop problem - shutting down *.real

I use the following commands:
```

sudo su

ps aux|grep mythtv

user      3609  0.0  0.2  63832  7264 ?        S    12:02   0:00 xterm -title MythTV Setup Terminal -e taskset -c 0 /usr/bin/mythtv-setup.real --sysllog local7
user      3612  2.3  2.5 841368 88700 pts/1    Ssl+ 12:02   0:04 /usr/bin/mythtv-setup.real --syslog local7

kill 3609
kill 3612

```

Basically, there are two processes that need to be deleted and they are order specific. If you kill 3612 first, it doesn't disappear.

In addition, this is a symptom of the primary problem which seems to be here;
```


Window Contents Titled: "MythTV Setup Terminal"

Loading en_us translation for module mythfrontend
Writing settings file /home/user/.mythtv/mysql.txt
Unable to connect to database!
Driver error was [1/1045]:
QMYSQL: Unable to cnonect
Database error was:
Access denied for user 'mythtv@localhost' (using password: YES)

Cannot login to database?
Cannot login to database?
LIRC:Failed to connect to Unix socket '/var/run/lirc/lircd'  eno: No such file of directory
JoystickMenuThread: Joystock disabled - Failed to read /home/user/.mythtv/joystickmenurc
Binding to UDP 127.0.0.1:0
Binding to UDP 10.10.10.12:0
Binding to UDP [::]:0
Binding to UDP 10.10.10.255:0
Using Frameless Window
Using Full Screen Window
Using the Qt painter
Loading en_us translation for module mythfrontend


```

Apparently, on my system there are several problems. MYSQL access and the lack of a remote control are problematic. But I don't know exactly.

---

### Post by teeedubb on 2012-06-28
Hey guys, sorry for the lack of replies, been busy lately...

From what I can gather, the automatic restarting of the frontend has to do with the way mythbuntu launches mythfrontend. At first I wasnt using mythwelcome as I was just testing, but now I am, I dont have the problem (feature?) of mythfrontend restarting as its launched diectly via mythwelcome... So now I can kill mythfrontend and xbmc via the power button with irexec and have it return to the mythwelcome screen to do its thing (I have stopped mythfrontend from autostarting as it sometimes gets confused and with no "exit when idle" option in the frontend/backend it will stay turned on until user intervention).

Lester: Does ACPI wake (complete shutdown) allow the htpc to be powered on via remote?

nhtrader: Im not having issuse with the database or remote, although I havent checked any logs because everything seems to be working...

---

### Post by Lester_Burnham on 2012-06-28
> **teeedubb said:**
> 
Lester: Does ACPI wake (complete shutdown) allow the htpc to be powered on via remote?.

Nope, I use WOL or push the button.

---

