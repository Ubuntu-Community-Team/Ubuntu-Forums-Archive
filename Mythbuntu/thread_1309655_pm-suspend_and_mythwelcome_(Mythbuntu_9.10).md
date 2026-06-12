---
title: "pm-suspend and mythwelcome (Mythbuntu 9.10)"
date: 2009-11-01
forum: Mythbuntu
---

### Post by Milan Knizek on 2009-11-01
Hello,

I am using mythbuntu 9.10 on Zotac ION ITX-A - it works great, even that making it "as I want" takes quite an effort ;-)

I have a working pm-suspend, when run from the command line. Before suspending, I have to stop mythtv-backend and remove USB DVB-T modules. This is done within /etc/pm config dirs.

When I set the command "/usr/sbin/pm-suspend" in MythWelcome settings as the shutdown command, then the following behaviour occurs:


1. When I select "Shutdown now" from MythWelcome's menu, the HTPC suspends just fine. When waking up, the screen saver asks me for a password. How to avoid the screen saver locking feature at all? Is it something gnome-screensaver or gnome-power-manager related? Why the screen is not locked when suspending from command line?


2. When I wait until idle and count-down to zero, MythWelcome displays a message that it cannot connect to the backend and nothing else happens. According to logs, the pm-suspend did not finish and probably got locked in /etc/pm/sleep.d/01myscript during stopping the backend daemon.

Note that the "shutdown command" in mythwelcome is actually run by "sudo mythshutdown --shutdown" from the backend setup. My HTPC has the backend and the frontend on a single machine.

---

### Post by Milan Knizek on 2009-11-01
> **Milan Knizek said:**
> Hello,

1. When I select "Shutdown now" from MythWelcome's menu, the HTPC suspends just fine. When waking up, the screen saver asks me for a password. How to avoid the screen saver locking feature at all? Is it something gnome-screensaver or gnome-power-manager related? Why the screen is not locked when suspending from command line?

While I still do not know what program is causing the locked screen, by searching the various acpi scripts I found that commenting out the lines in script /usr/share/acpi-support/screenblank "solves" the problem:
```
#if [ `pidof xscreensaver` ]; then
#       su $user -c "(xscreensaver-command -throttle)"
#               if [ x$LOCK_SCREEN = xtrue ]; then
#               su $user -c "(xscreensaver-command -lock)"
#       fi
#elif [ `pidof dcopserver` ]; then
#       dcop kdesktop KScreensaverIface lock
#fi
#
#xset dpms force off
#if [ x$RADEON_LIGHT = xtrue ]; then
#    [ -x /usr/sbin/radeontool ] && radeontool light off
#fi
```
This is an ugly workaround. However, setting the LOCK_SCREEN=false in /etc/default/acpi-support did not help:
```
#
# LEGACY BUILT IN SUSPEND SUPPORT (DEPRECATED)
# --------------------------------------------
#
# These options only work for the "acpi-support" suspend method. This is NOT
# recommended, but is retained for backward compatibility reasons.
...
# Comment this out to disable screen locking on resume
LOCK_SCREEN=false
```
I guess some other daemon keeps the variable set to true, but I did not found, which could be that.

---

### Post by Milan Knizek on 2009-11-02
> **Milan Knizek said:**
> 2. When I wait until idle and count-down to zero, MythWelcome displays a message that it cannot connect to the backend and nothing else happens. According to logs, the pm-suspend did not finish and probably got locked in /etc/pm/sleep.d/01myscript during stopping the backend daemon.
Well, I finally "solved" this trouble as well. As for the first problem, it is an ugly workaround:
```
if [ "$1" = "suspend" ]; then
# kill `pidof mythwelcome` # not needed anymore
 /usr/sbin/service lirc stop
 echo 1
# /usr/sbin/service mythtv-backend stop
 kill -15 `pidof mythbackend`
# /usr/sbin/service mythtv-backend restart # does not work, suspend is cancelled
# /usr/sbin/service mythtv-backend restart # does not work, suspend is cancelled
 echo 2
```
The mythbackend daemon is immediatelly respawned by the upstart service, but it seems to provide enough time to "free" the DVB-T tuners and remove their modules by suspend:
```
Nov  2 20:44:20 myth01 init: mythtv-backend main process (9216) terminated with status 143
Nov  2 20:44:20 myth01 init: mythtv-backend main process ended, respawning
Nov  2 20:44:22 myth01 NetworkManager: <info>  Sleeping...
Nov  2 20:44:22 myth01 NetworkManager: <info>  (eth4): now unmanaged
Nov  2 20:44:22 myth01 NetworkManager: <info>  (eth4): device state change: 8 -> 1 (reason 37)
Nov  2 20:44:22 myth01 NetworkManager: <info>  (eth4): deactivating device (reason: 37).
Nov  2 20:44:22 myth01 NetworkManager: <WARN>  check_one_route(): (eth4) error -34 returned from rtnl_route_del(): Sucess#012
Nov  2 20:44:22 myth01 NetworkManager: <info>  (eth4): cleaning up...
Nov  2 20:44:22 myth01 NetworkManager: <info>  (eth4): taking down device.
Nov  2 20:44:22 myth01 NetworkManager: <info>  (wlan0): now unmanaged
Nov  2 20:44:22 myth01 NetworkManager: <info>  (wlan0): device state change: 3 -> 1 (reason 37)
Nov  2 20:44:22 myth01 NetworkManager: <info>  (wlan0): cleaning up...
Nov  2 20:44:22 myth01 NetworkManager: <info>  (wlan0): taking down device.
Nov  2 20:44:22 myth01 NetworkManager: <info>  (eth4): carrier now OFF (device state 1)
Nov  2 20:44:22 myth01 kernel: [ 4310.229059] usbcore: deregistering interface driver dvb_usb_dib0700
Nov  2 20:44:22 myth01 kernel: [ 4310.554143] dvb-usb: AVerMedia AVerTV DVB-T Volar successfully deinitialized and disconnected.
Nov  2 20:44:22 myth01 kernel: [ 4310.672034] usbcore: deregistering interface driver dvb_usb_af9015
Nov  2 20:44:22 myth01 kernel: [ 4310.672070] dvb-usb: generic DVB-USB module successfully deinitialized and disconnected.
Nov  2 20:44:22 myth01 kernel: [ 4310.704659] dvb-usb: AVerMedia AVerTV DVB-T Volar X successfully deinitialized and disconnected.
Nov  2 20:44:23 myth01 kernel: [ 4310.796536] usbcore: deregistering interface driver usbhid
Nov  2 20:44:23 myth01 kernel: [ 4310.869440] usbcore: deregistering interface driver hiddev

```
I still do not know, why use of /usr/sbin/service leads to cancelled suspend in this particular case only and what is worse, that before another suspend can be initiated, the computer must be restarted.

---

### Post by bcully on 2009-11-26
> **Milan Knizek said:**
> 
The mythbackend daemon is immediatelly respawned by the upstart service, but it seems to provide enough time to "free" the DVB-T tuners and remove their modules by suspend

Upstart will probably behave better if you use ```
stop mythtv-backend
``` instead of manually killing mythbackend.

---

### Post by Milan Knizek on 2009-11-27
> **bcully said:**
> Upstart will probably behave better if you use ```
stop mythtv-backend
``` instead of manually killing mythbackend.

I expected so as well, but the trouble is that using ```
service mythtv-backend stop
``` or ```
stop mythtv-backend
``` causes the suspend freeze (just blinking cursor and nothing in logs) and requires a hard reset.

Definitely a trouble with the usb dvb-t dongles...

---

### Post by perceptron on 2009-11-29
I have the same problem (your second issue) on my machine, i.e. pm-suspend terminating before making the machine sleep. Actually, I don't think that it has anything to do with your dvb-t dongle: I use a dvb-s PCI card.

Two things that might help solve the problem (which I think won't be straightforward):

1. My guess would be that the error occurs as the mythtv-backend (which is started with upstart) triggers the pm-suspend-call, which then causes upstart's "stop" to kill itself. So I would think that the "stop" command kills the mythtv-backend process and also terminates child processed including the non-complete "pm-suspend". I think so as there are no "freezed" processes, it just seems that pm-suspend is terminated at the "suspend" section, i.e. before completion. I currently use your work-around (and "restart mythtv-backend" in the pm resume section).

2. Instead of rebooting your machine after one erroneous pm-suspend call, you might just delete the suspend lock file in /var/lib/pm-utils. Subsequent calls will at least not terminate immediately.

Maybe someone who has experience with upstart/d-bus is able to read this and could give us some hints. Also, I would think that using d-bus for the **complete** control of backend and frontend and shutdown/sleep would simplify many issues, but actually it's just a vague recommendation.

---

### Post by Milan Knizek on 2009-11-30
> **perceptron said:**
> 
2. Instead of rebooting your machine after one erroneous pm-suspend call, you might just delete the suspend lock file in /var/lib/pm-utils. Subsequent calls will at least not terminate immediately.

Thanks, I was not aware of that lock file.

---

### Post by schaze on 2009-12-19
Hi,

I am having the exact same problem and cannot find a way around ( I am having a solid state disk which lets mythbacken reload so fast that I do not have time unloading the kernel modules.. )

I do have a nice solution for the lockscreen however:
You simply need to install the xfce4-power-manager package and then you can disable the lockscreen on the xfce settings panel under the power options.
(no idea why the gnome-powermanager is installed here anyways since it is a xfce system...)

Did have any progress regarding the stop service problem? 

I tried it with 'nohup' for the pm-suspend command, but that somehow simply does not work. No idea why.

/schaze

---

### Post by schaze on 2009-12-19
Hi,

allright I have a solution (or better a workaround -- waaaay around) for this problem.

It is a bit more complex then I like but at least it is working now 100%.

The basic idea is: If pm-suspend cancels when its calling service is stopped via upstart (which is something that should be looked into) then I have to have somebody else do the pm-suspend on the system. Thus I need a 'suspend-daemon'.

Lukily in linux writing something like that is as easy as cake.

Here is what you do to make it work:
(I expect you know how to use the vi/vim editor, if not please ask google first or use an editor of your choice)

_**1. Create the suspend-daemon**_

Fire up vi editor:
```
sudo vi /usr/local/bin/suspendDaemon
```Copy & Paste the following into it:
```
#!/bin/bash
# suspendDaemon, by schaze (schazet at gmail.com)
# Listens on a FIFO pipe for a suspend command and then executes pm-suspend.

if [ -p /tmp/suspendDaemon ]; then
  rm  /tmp/suspendDaemon
fi

mkfifo /tmp/suspendDaemon
chgrp mythtv /tmp/suspendDaemon
chmod 775 /tmp/suspendDaemon

command=""

while [ "$command" != "endDaemon" ]; do
  command=$(cat /tmp/suspendDaemon)
  
  if [ "$command" == "suspend" ]; then
    pm-suspend
  fi
done

rm -f /tmp/suspendDaemon
```Then make sure the scipt is executable
```
chmod 755 /usr/local/bin/suspendDaemon
```_**2. Create upstart service that controls the suspend-daemon**_
Now we have the suspenDaemon ready and working but we need the system to have it started and also keep it up and running. For this we will create an upstart service.
In Ubuntu Karmic all upstart service config files are located in [FONT=Courier New]/etc/init/.
[/FONT]
So we fire up our beloved vi once more:
```
sudo vi /etc/init/suspend-daemon.conf
```Copy & Paste the following into it:
```
# SuspendDaemon service

description    "Suspend-Daemon, waits on input over a FIFO to suspend the sytem independantly from its caller process"
author        "schaze (schazet at gmail.com)"

start on (local-filesystems and net-device-up IFACE=lo)
stop on runlevel [016]

#expect fork
respawn

script    
    exec /bin/su -c "/usr/local/bin/suspendDaemon"
end script
```Ok, thats it already, you should now be able to start your daemon with:
```
sudo start suspend-daemon
```Do a quick test if it really works with:
```
sudo echo suspend > /tmp/suspendDaemon
```This should suspend your PC.


_**3. Integrate into MythTV**_
So now we have everything ready and set up. In order to use it now you simply have to create a little script that you can use as the shutdown command in your mythwelcome config, or if you already have your script replace the[INDENT][FONT=Courier New]pm-suspend [/FONT]
[/INDENT]command with a:[INDENT][FONT=Courier New]echo suspend > /tmp/suspendDaemon[/FONT]
[/INDENT]As an example, I am using the following 'script' for suspend:

```
#!/bin/bash
LOGFILE=/var/log/mythtv/shutdown.log

date >> $LOGFILE
echo "MythSuspend executing... " >> $LOGFILE

echo suspend > /tmp/suspendDaemon

```That's it, with this it should be working like a charm. (it does so for me)

I know this is a bit a long way around the problem and probably there are some caveats regarding to security, but it works. And it does so in a clean and structured way.

Have fun with your mythtv box!
schaze

---

### Post by jms-ubuntu-en on 2009-12-20
schaze, your suspend solution works great for me as ran from command line, thank you! The problem is that I can't assign "the final" suspend script to supersede "shutdown". 
By "the final" suspend script I mean following:
```
#!/bin/bash
LOGFILE=/var/log/mythtv/shutdown.log

date >> $LOGFILE
echo "MythSuspend executing... " >> $LOGFILE

echo suspend > /tmp/suspendDaemon
```
I named the script mythsuspend.sh and I replaced the shutdown command in mythwelcome's setup using this mythsuspend.sh. However, when I select shutdown it actually shuts down :)
Any idea what's the problem?

I'm using mythbuntu 9.10 in my frontend computer and mythfrontend is configured to start automatically...

---

### Post by schaze on 2009-12-20
> **jms-ubuntu-en said:**
> I named the script mythsuspend.sh and I replaced the shutdown command in mythwelcome's setup using this mythsuspend.sh. However, when I select shutdown it actually shuts down :)
Any idea what's the problem?

Hi,

please be aware that my solution does not include the whole setup to be done for automatic shutdown etc... for mythtv. 
Did you check the wikis for that already? (e.g. [http://www.mythtv.org/wiki/ACPI_Wakeup](http://www.mythtv.org/wiki/ACPI_Wakeup) and [http://www.mythtv.org/wiki/Mythwelcome](http://www.mythtv.org/wiki/Mythwelcome))

If you use the Mythfrontend for the shutdown you will have to check the command used for the shutdown in Setup/Tools->Setup->General. There is a screen where you can configure the 'System Menu Key' and also the commands for shutdown. I would suspect that you use a normal shutdown there still.

There are actually 3 location where shutdown commands are configured:

_**1. Mythfrontend**_
Setup/Tools->Setup->General

Here you specify what command to be executed when you select shutdown/reboot in Mythfrontend system menu.

_**2. Mythbackend**_
In the General settings

Here you specify the command used to shutdown when the backend has decided to shutdown (e.g. because no frontends are connected any more). You can also specify here what commands to be used if a shutdown condition is met.

_**3. Mythwelcome**_
Press F11 in Mythwelcome

Here you specify the shutdown command to be executed when [FONT=Courier New]mythshutdown --shutdown[/FONT] is executed and also the command for setting the mainboard acpi wakeup time.


For **_1._** you won't need my solution at all as you can simply add pm-suspend there and it will work.

For the solution with **2.** and _**3.**_ where the backend uses mythwelcome to shutdown/suspend you need at the moment my setup.


I hope this helps.

I have my setup now cleaned up very nicely and I think I will probably create a comprehensive little tutorial (one more besides the 20 out there can't hurt :) ) thread over the holidays...

/schaze

---

### Post by jms-ubuntu-en on 2009-12-20
The first option (mythfrontend's setup) was the correct place in my case - now suspend works like a charm, thank you again!

---

### Post by Milan Knizek on 2009-12-20
> **schaze said:**
> 
```

while [ "$command" != "endDaemon" ]; do
  command=$(cat /tmp/suspendDaemon)

```


I am not so skilled with FIFO pipes, however, will the $command variable ever become equal to "endDaemon"?

Anyway, I will try on my mythbox, too.

---

### Post by schaze on 2009-12-20
> **jms-ubuntu-en said:**
> The first option (mythfrontend's setup) was the correct place in my case - now suspend works like a charm, thank you again!

Glad to hear that! You are welcome :)

> **Milan Knizek said:**
> I am not so skilled with FIFO pipes, however, will the $command variable ever become equal to "endDaemon"?

Anyway, I will try on my mythbox, too.

Hi Milan,

it will if you send a 'endDaemon' to it by e.g.: ```
echo endDaemon > /tmp/suspendDaemon
```This is thought as a clean way of shutting down the daemon. But with the upstart service it has basically no use as upstart will respawn another process as soon as it is ended.

It is in for those who will not use upstart but e.g. normal init scripts.

upstart will simply kill the process of the suspend-daemon when you do a  ```
stop suspend-daemon
```So I also could have done a ```
while [ "1" == "1" ]; do
...
```it does not really matter.

/schaze

---

### Post by Milan Knizek on 2009-12-21
> **schaze said:**
> So I also could have done a ```
while [ "1" == "1" ]; do
...
```it does not really matter.

/schaze
I thought so, but thanks for clarification.
mk

---

### Post by srllorente on 2009-12-30
> **schaze said:**
> Hi,

allright I have a solution (or better a workaround -- waaaay around) for this problem.

It is a bit more complex then I like but at least it is working now 100%.

The basic idea is: If pm-suspend cancels when its calling service is stopped via upstart (which is something that should be looked into) then I have to have somebody else do the pm-suspend on the system. Thus I need a 'suspend-daemon'.

(....)

schaze

Schaze, thanks for the solution. It looks pretty promising.
Still I cannot test it because for some reason suspend does not work on my Acer Aspire Revo with mythbuntu 9.10
When I try it, it just goes blank screen with a cursor blinking in the top left corner ... have to do hard reset to get out of there

Has anyone encounter similar problems with suspend? (it happens the same if I just suspend from xfce logout menu). I have googled it intensively but no luck.
Thanks

s.

---

### Post by perceptron on 2010-02-27
After changing the hardware of my Mythbuntu system, I ran into the same problem that is described here and that I commented on end of November 2009.

I noticed that a a suspend daemon has been proposed in this thread recently. It basically allows to stop the mythtv-backend service from an external scope. However, upstart provides an event mechanism that serves the exact same purpose. So there are two necessary steps only:

[LIST=1]
[*] Create /etc/init/mythtv-suspend.conf in which a custom event (mythtv-suspend) is mentioned as a trigger for pm-suspend
```

# MythTV Suspend command
description	"MythTV Suspend"
author          "Fabian Wenzel <notshownhere>"

start on mythtv-suspend
exec pm-suspend

```
[*] Define ```
sudo sh -c "initctl emit mythtv-suspend"
``` as shutdown command in mythtv, replacing the call to pm-suspend (or the echo to the suspend daemon proposed in December in this list)
[/LIST]

At least, on my machine, it works without problems.

---

### Post by schaze on 2010-02-27
Hi perceptron,

using upstart is actually pretty neat! I knew about the events but I did not think about it this way. That is actually a lot cleaner and nicer that my solution. :D I will give it a try and see how it works. Thanks a lot for sharing!

/schaze

---

### Post by Saubazi on 2010-06-14
This one looks exactly like the problem I am struggling with. I have also a shell script I want to have carried out for suspend (of loading dvb modules stopping lirc etc.). Now I have logging during the script and it seems to hang immediately at stop mythtv-backend, never coming near pm-suspend. There are some other services in between that are supposed to be stopped so the point is that the script execution is stopped long before getting to suspend.

I suspect that my script execution is terminated by shutting down the backend. I have now tried to include nohup or backgrounding to my command but with no real success. sudo nohup suspend2ram.sh did not work - I do not know whether sudo exec suspend2ram.sh would be
correct - somewhere in the back of my mind I have a recollection of fighting this one with my old box and I have a recollection of exec.

In anyway I can try the daemon solution - should be intereseting.

---

### Post by Milan Knizek on 2010-07-22
@Perceptron: thanks for the solution with the separate "service".
I finally got back to the issue and updated my Mythbuntu - works like a charm.

The only trouble is that I have failed at defining sudoers rule for running "sudo sh -c "blabla"" without a password - I ended up with separate definition, however I do not find this a good solution:

```
%mythtv ALL= (ALL) NOPASSWD: /bin/sh, /sbin/initctl emit mythtv-suspend
```

Edit: sorry, I was too quick without prior thinking. Since I am running the initial command in mythtv backend as "sudo -H /usr/bin/mythshutdown --shutdown", the initctl from MythWelcome is already run with a privileged user - hence no need for another sudo there... Anyway, I still do not know the answer to above sudoers problem - a little off-topic now.

---

### Post by lespedeza on 2010-11-11
perceptron and others,

Thanks for getting to the bottom of this.  Perceptron's solution is the only one that worked for me to get my myth BE to suspend and wake the way I wanted. It took a while to find and implement this, but I'm finally pleased with the results.  Thanks again.

---

