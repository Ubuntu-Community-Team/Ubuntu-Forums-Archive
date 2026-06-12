---
title: "LIRC  blaster setup with second PVR 150"
date: 2008-09-06
forum: Mythbuntu
---

### Post by ptipton on 2008-09-06
I have added a second PVR 150 connected to a satellite box to mythbuntu 8.04 and am having issues getting the ir blasters to work. With one card the ir blaster worked fine but now neither work.
I looked at the  section 12.4 Setting Up Multiple devices in the Installation Manual  but the changes to /etc/lirc/hardware.conf and  /etc/init.d/lirc seem to relate only to remotes rather than transmitters ( Its a backend only setup so dont have any remotes installed) so I'm needing advice on how to do this for transmitters.
I tried following these instructions for adding a second blaster [http://notepad.bobkmertz.com/2007/11/pvr150-with-set-top-box-knoppmyth.html](http://notepad.bobkmertz.com/2007/11/pvr150-with-set-top-box-knoppmyth.html) but no joy.
My current /etc/lirc/hardware.conf  is:
# /etc/lirc/hardware.conf
#
# Arguments which will be used when launching lircd
REMOTE_LIRCD_ARGS="--device=/dev/lirc0"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD=false

#Try to load appropriate kernel modules
LOAD_MODULES=true

# Run "lircd --driver=help" for a list of supported drivers.
REMOTE_DRIVER=""
# If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
# automatically used instead
REMOTE_DEVICE=""
REMOTE_MODULES=""

# Default configuration files for your hardware if any
REMOTE_LIRCD_CONF=""
LIRCMD_CONF=""
REMOTE="None"
TRANSMITTER="Custom"
TRANSMITTER_MODULES="lirc_dev lirc_pvr150"
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE="/dev/lirc0"
TRANSMITTER_LIRCD_CONF="/usr/share/lirc/transmitters"
TRANSMITTER_LIRCD_ARGS=""
START_LIRCD="true"
START_LIRCMD=""
FORCE_NONINTERACTIVE_RECONFIGURATION="false"

and /etc/init.d/lirc is:
#! /bin/sh
### BEGIN INIT INFO
# Provides:          lirc
# Required-Start:    $syslog
# Required-Stop:     $syslog
# Should-Start:      $local_fs
# Should-Stop:       $local_fs
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Starts LIRC daemon.
# Description:       LIRC is used to control different
#                    infrared receivers and transceivers.
### END INIT INFO

load_modules ()
{
    local MODULES_MISSING=false
    local UDEV=false

    log_daemon_msg "Loading LIRC modules"
    for mod in $*
    do
        if [ $mod != "udev" ]; then
            modprobe -k $mod 2> /dev/null || MODULES_MISSING=true
        else
            UDEV=true
        fi
    done
    log_end_msg $?

    if test -x /sbin/udevadm && [ $UDEV != true ];
    then
        if ! /sbin/udevadm settle; then
          echo "timeout waiting for devices to be ready"
        fi
    fi

    if $MODULES_MISSING; then
        log_failure_msg "Unable to load LIRC kernel modules. Verify your"
        log_failure_msg "selected kernel modules in /etc/lirc/hardware.conf"
        START_LIRCMD=false
        START_LIRCD=false
    fi
}

build_remote_args ()
{
    local REMOTE_ARGS="$*"

    #For remote only detection support, we need
    #both REMOTE_DEVICE and TRANSMITTER_DEVICE undefined
    if [ -z "$REMOTE_DEVICE" ] && [ -z "$TRANSMITTER_DEVICE" ]; then
        for dev in /dev/lirc0; do
            if [ -c $dev ]; then
                REMOTE_DEVICE="$dev"
                break
            fi
        done
    fi

    #If we have a REMOTE_DEVICE or REMOTE_DRIVER defined (either because no devices
    #were defined, OR if we explicitly did), then populate REMOTE_ARGS
    if [ ! -z "$REMOTE_DEVICE" ] || [ ! -z "$REMOTE_DRIVER" ]; then
        if [ -n "$REMOTE_DEVICE" ] && [ "$REMOTE_DEVICE" != "none" ]; then
            REMOTE_ARGS="--device=$REMOTE_DEVICE $REMOTE_ARGS"
        fi
        if [ -n "$REMOTE_DRIVER" ] && [ "$REMOTE_DRIVER" != "none" ]; then
            REMOTE_ARGS="--driver=$REMOTE_DRIVER $REMOTE_ARGS"
        fi

        #Now, if we ALSO have a transmitter defined, add some args
        #To make the first lircd listen up
        if [ ! -z "$TRANSMITTER_DEVICE" ] || [ ! -z "$TRANSMITTER_DRIVER" ]; then
            REMOTE_ARGS="$REMOTE_ARGS --output=/dev/lircd --listen"
        fi
    fi
    echo $REMOTE_ARGS
}

build_transmitter_args ()
{
    local TRANSMITTER_ARGS="$*"

    #Transmitters must be explicitly be defined
    if [ ! -z "$TRANSMITTER_DEVICE" ] || [ ! -z "$TRANSMITTER_DRIVER" ]; then
        if [ -n "$TRANSMITTER_DEVICE" ] && [ "$TRANSMITTER_DEVICE" != "none" ]; then
            TRANSMITTER_ARGS="--device=$TRANSMITTER_DEVICE $TRANSMITTER_ARGS"
        fi
        if [ -n "$TRANSMITTER_DRIVER" ] && [ "$TRANSMITTER_DRIVER" != "none" ]; then
            TRANSMITTER_ARGS="--driver=$TRANSMITTER_DRIVER $TRANSMITTER_ARGS"
        fi

        #Now, if we ALSO have a remote defined, add some args
        #To make the second lircd connect
        if [ ! -z "$REMOTE_DEVICE" ] || [ ! -z "$REMOTE_DRIVER" ]; then
            TRANSMITTER_ARGS="$TRANSMITTER_ARGS --output=/dev/lircd1 --connect=localhost:8765 --pidfile=/var/run/lircd1.pid"
        fi
    fi
    echo $TRANSMITTER_ARGS
}

. /lib/lsb/init-functions

test -f /usr/sbin/lircd || exit 0
test -f /usr/sbin/lircmd || exit 0

START_LIRCMD=true
START_LIRCD=true

if [ -f /etc/lirc/hardware.conf ];then
    . /etc/lirc/hardware.conf
fi

if [ ! -f /etc/lirc/lircd.conf ] \
    || grep -q "^#UNCONFIGURED"  /etc/lirc/lircd.conf;then
    if [ "$1" = "start" ]; then
    	log_success_msg "No valid /etc/lirc/lircd.conf has been found."
        log_success_msg "Remote control support has been disabled."
        log_success_msg "Reconfigure LIRC or manually replace /etc/lirc/lircd.conf to enable."
    fi
    START_LIRCD=false
    START_LIRCMD=false
fi
if [ ! -f /etc/lirc/lircmd.conf ] \
    || grep -q "^#UNCONFIGURED" /etc/lirc/lircmd.conf;then
    START_LIRCMD=false
fi

case "$1" in
    start)
        if [ "$LOAD_MODULES" = "true" ] && [ "$START_LIRCD" = "true" ]; then
            load_modules $REMOTE_MODULES $TRANSMITTER_MODULES $MODULES $2
        fi
        if $START_LIRCD; then
            log_daemon_msg "Starting remote control daemon(s) : LIRC "
            REMOTE_LIRCD_ARGS=`build_remote_args $REMOTE_LIRCD_ARGS`
            TRANSMITTER_LIRCD_ARGS=`build_transmitter_args $TRANSMITTER_LIRCD_ARGS`

            #if we have a remote defined, it is primary process
            if [ ! -z "$REMOTE_LIRCD_ARGS" ]; then
                start-stop-daemon --start --quiet --exec /usr/sbin/lircd -- $REMOTE_LIRCD_ARGS < /dev/null
                log_end_msg $?

                #now if we additionally have a transmitter defined, it is secondary process
                if [ ! -z "$TRANSMITTER_LIRCD_ARGS" ]; then
                    /usr/sbin/lircd $TRANSMITTER_LIRCD_ARGS < /dev/null
                fi
            elif [ ! -z "$TRANSMITTER_LIRCD_ARGS" ]; then
                start-stop-daemon --start --quiet --exec /usr/sbin/lircd -- $TRANSMITTER_LIRCD_ARGS < /dev/null
            else
                log_end_msg 1
            fi
        fi
        if $START_LIRCMD; then
            log_daemon_msg "Starting remote control mouse daemon : LIRCMD "
            start-stop-daemon --start --quiet --exec /usr/sbin/lircmd < /dev/null
            log_end_msg $?
        fi
        ;;
    stop)
        if $START_LIRCMD; then
            log_daemon_msg "Stopping remote control mouse daemon: LIRCMD"
            start-stop-daemon --stop --quiet --exec /usr/sbin/lircmd
            log_end_msg $?
        fi
        if $START_LIRCD; then
            log_daemon_msg "Stopping remote control daemon(s): LIRC"
            start-stop-daemon --stop --quiet --exec /usr/sbin/lircd
            log_end_msg $?
        fi
        ;;
    reload|force-reload)
        if $START_LIRCD; then
            start-stop-daemon --stop --quiet --signal 1 --exec /usr/sbin/lircd
        fi
        if $START_LIRCMD; then
            start-stop-daemon --stop --quiet --signal 1 --exec /usr/sbin/lircmd
        fi
        ;;
    restart)
        $0 stop
        #passes parameter $2 which is possibly our udev paramater
        $0 start $2
        ;;
    *)
        echo "Usage: /etc/init.d/lircd {start|stop|reload|restart|force-reload}"
        exit 1
esac

exit 0

Any help much appreciated.

---

### Post by anonymousdog on 2008-09-07
It'd be awesome if we knew what you are trying to control with the transmitters; with the hardware.conf file below, it appears nothing or some default device (since TRANSMITTER_LIRCD_CONF="/usr/share/lirc/transmitters" is just the default directory for transmitter conf files).  I'm also unsure what edits there are to /etc/init.d/lirc (and a diff was too difficult because your text was munged by the board [and your not entering it as 'code' formatted]).  I'd revert that to backup before proceeding.

As long as you have a /dev/lirc1 and a /dev/lircd1, you're pretty golden.  The steps on page 117 of the Installation guide should get you exactly the results you want.  They basically change the init script to start two instances of the daemon, one controlling each transmitter.  As long as the transmitters are the same hardware controlling the same type of set-top-box, no changes in hardware.conf were ever required.  I'd also revert that to a backup.

Your channel change scripts for both tuners will now have to accommodate a '--dev /dev/lirc[whatever]' option to irsend, /dev/lirc0 for your original tuner, and /dev/lirc1 for your second.

If the second stb is different, changes will have to be made to hardware.conf and your channel change script (to designate the new "remote" name in the irsend command).

---

### Post by ptipton on 2008-09-07
Anonymousdog- thanks. I must have messed up the the TRANSMITTER_LIRCD_CONF line somwhere in the process and restoring that to point at the correct file has restored my original blaster to functionality- much to the relief of my family!!!
Still no joy with the second blaster.
I have posted the hardware.conf and /etc/init.d/lirc at pastebin so hopefully wont be messed up.
[http://pastebin.com/m538900](http://pastebin.com/m538900)

I think I have lirc1 and lircd1 see terminal output below

administrator@ubuntuserver:~$ ls -l /dev/lirc*
crw-rw---- 1 root root 61, 0 2008-09-07 18:18 /dev/lirc0
crw-rw---- 1 root root 61, 1 2008-09-07 18:18 /dev/lirc1
srw-rw-rw- 1 root root     0 2008-09-07 18:18 /dev/lircd
srw-rw-rw- 1 root root     0 2008-09-07 18:18 /dev/lircd1
administrator@ubuntuserver:~$ 

I think this is the result of following the Knopmyth instructions at Bobs notepad that I mentioned in the first post. If thats the case do I still need to make the changes to /etc/init.d/lirc and /etc/init.d/lirc ? ( Note the transmitters are identical and controlling identical setop boxes)
If I do need to make the changes to these files as per page 116/117 of the Installation manual then I am struggling with the following:
For hardware.conf it states " Modify LIRCD_ARGS="" to match ...... Is this referring to REMOTE_LIRCD_ARGS=" -- device etc"  line 4 of the file or TRANSMITTER_LIRCD_ARGS="" in line 28 of the file?? LIRCD_ARGS="" on its own does not exist in my file.
For  etc/init.d/lirc the block that the instructions say replace doesn't seem to exist in my file.
Thanks again your help is much appreciated.

---

### Post by anonymousdog on 2008-09-07
Since the hardware is all the same stuff, there is only one change to make in hardware.conf.  You have to come up with a variable for the second transmitter device and assign it a "/dev/lirc1" value.  I also added a TRANSMITTER1_LIRCD_ARGS to better work within the structure of the init script.

Your only other tasks are to start a second instance of lircd associated with the second IR transceiver, and modifying channel change scripts to call the correct lirc[n] device for the correct tuner/stb combination.  Re: the first, my apologies re: what appears to be a major change in lirc init scripts since the install guide was written.

Looks like you have a bone-stock lirc init script (at least it manages those on my boxes); so, the changes should flow pretty well from the install doc (p 117), but don't :confused:.

Instead, it looks like we'll have to define a new function, build_transmitter1_args () and initialize a second instance of lircd based on those args.

I started to explain the edits, but just changed you files posted on [pastebin](http://pastebin.com/m2348b25d).

That should do it (if I haven't made any mistakes).

Warning!  Warning!  Warning!  This fix is severely hacked together and WILL break if a remote driver, module or device is defined.  It probably won't work (well) for anyone that has a setup at all deviating from that of the original poster.  You have been warned; I take no responsibility for what you do with these scripts or changes to them.

---

### Post by ptipton on 2008-09-08
Anonymousdog thanks. Thought I was almost there but seem to have some weirdness going on now. When I got home family complaining that channel not changing and the original blaster had stopped working. Not sure how this could have happened as was working fine last night but power cuts are fairly common here so maybe it rebooted.
.
Tried looking for the dev/lircs and got the following.
administrator@ubuntuserver:~$ ls -l /dev/lirc*
srw-rw-rw- 1 root root 0 2008-09-08 23:13 /dev/lircd1

Note lircd1 is actually created by the lirc1 file in init.d that came from the instructions I followed at Bobs notebook. If i remove this file and whether I use the hardware.conf and init.d/lirc from your post or my original files I get:

administrator@ubuntuserver:~$ ls -l /dev/lirc*
ls: cannot access /dev/lirc*: No such file or directory
administrator@ubuntuserver:~$ 

So basically lirc0  and lirc1 have disappeared.

Thanks again for your help.

---

### Post by anonymousdog on 2008-09-08
You've probably exhausted my expertise on this subject, but *I think* those device nodes are created when lircd loads modules.  So, I'd try rebooting the system after making really sure that the transmitters are connected securely to the PC.  If you've done nothing more than what you wrote, you should at least be able to fallback to backups of hardware.conf and lirc (init script) with the second transmitter unplugged and get functionality out of the first transmitter.  If you can't get that, there's something more at play here.

If so, I'd be VERY tempted to (backup and move your config files and) use the MCC to recreate a working config for your original blaster.

At this point it's most important that you're able to fall back to a known, working state or diagnostics starts becoming a guessing game.

---

### Post by ptipton on 2008-09-09
Anonymousdog .Am making some forward progress. Uninstalled lirc and mythbuntu control centre, cleared out all the related files and then reinstalled. After reconfiguring the transmitter in the control center my original blaster is back to working.
The new hardware.conf and init.d/lirc are here [http://pastebin.com/m59fb00c](http://pastebin.com/m59fb00c)
Get the following when looking at /dev/lirc
root@ubuntuserver:/home/administrator# ls -l /dev/lirc*
crw-rw---- 1 root root 61, 0 2008-09-09 20:55 /dev/lirc0
crw-rw---- 1 root root 61, 1 2008-09-09 20:55 /dev/lirc1
srw-rw-rw- 1 root root     0 2008-09-09 20:55 /dev/lircd
root@ubuntuserver:/home/administrator# 

However if a replace hardware.conf and init.d/lirc with the files you modified for me then neither blaster works and  ls -l /dev/lirc* gives no such file or directory.

Feels like must be very close ! Thanks

---

### Post by anonymousdog on 2008-09-09
Ok, now backup those files and /etc/lircd.conf :)

Can you also post just your channel changing script as well (with no other files)?  In fact, from now one, please post each file to a unique url, it makes parsing, calculating line number changes, diffs and all else much easier (for me).  So, why not post that /astro/general.conf too?

Let's just troubleshoot the new transmitter now.  Since it's all the same hardware (just duplicated), lircd should already have loaded all the appropriate modules, and it has clearly detected the hardware AEB /dev/lirc0 and /dev/lirc1.  The init script is what creates /dev/lircd (AFIK); so, I probably hosed the hacks on the init script.

To ensure that the overall process is going to work, let's just start up the second instance of lircd manually for testing (and allow service startup changes to be a separate task).

With your first blaster working, issue this command:```
sudo /usr/sbin/lircd --device=/dev/lirc1 --output=/dev/lircd1 --connect=localhost:8765 --pidfile=/var/run/lircd1.pid & < /dev/null
```

Now, you should be able to send some commands to your second stb via irsend```
irsend --device /dev/lircd1 --send_once <remote name as defined in transmitters/astro/general.conf> <some command in same file>
``` To see the commands available for that remote, you can issue,```
irsend list <remote name> ""
```including the doubled double quotes (i.e., a null).  As long as the transmitter's hooked up and IR blaster dongle is working, that should control your stb as expected (for the commands you send this way).

Write back after attempting this.

---

### Post by ptipton on 2008-09-10
OK the fist command seems to work as after executing it i get :
administrator@ubuntuserver:~$ ls -l /dev/lirc*
crw-rw---- 1 root root 61, 0 2008-09-09 20:55 /dev/lirc0
crw-rw---- 1 root root 61, 1 2008-09-09 20:55 /dev/lirc1
srw-rw-rw- 1 root root     0 2008-09-09 20:55 /dev/lircd
srw-rw-rw- 1 root root     0 2008-09-10 20:02 /dev/lircd1
administrator@ubuntuserver:~$ 

Am having problems with the second command:
administrator@ubuntuserver:~$ irsend --device /dev/lirc1 send_once blaster POWER
irsend: could not connect to socket
irsend: Permission denied
administrator@ubuntuserver:~$ 

channel change script for second blaster here:[http://pastebin.com/m53e63d1](http://pastebin.com/m53e63d1)
chanel change script for first blaster ( working blaster) here: [http://pastebin.com/m3af7b02f](http://pastebin.com/m3af7b02f)
astro/general.conf here:[http://pastebin.com/m2ff3a983](http://pastebin.com/m2ff3a983)
hardware.conf here:[http://pastebin.com/m52dec2da](http://pastebin.com/m52dec2da)
init.d/lirc here:[http://pastebin.com/m606a90c5](http://pastebin.com/m606a90c5)

Thanks again

---

### Post by ptipton on 2008-09-11
Ok now we are getting somewhere:
changed the command to:
irsend --device /dev/lircd1 send_once <remote name as defined in transmitters/astro/general.conf> <some command in same file>
and with this the second blaster works

Guess now just have to get the hardware.conf and init.d/lirc  correct then its sorted

---

### Post by ptipton on 2008-09-11
looks like I spoke too soon. After the success with the second blaster in above post went back to mythtv and neither blaster works. According to family the first blaster stopped working several hours before i took the steps posted above.
tried restoring the backed up hardware.conf and init.d/lirc and restarting lirc but no joy.
tried removing and reinstalling lirc and myth control center and still no joy.
So now stuck with neither blaster working again.

---

### Post by anonymousdog on 2008-09-11
Ok; so, kill the second lircd process (or reboot).  Since you made no changes to the configuration files, you should be back to a working 1st blaster after that.  If not, refer back to your backed up or originally posted hardware.conf, init script and astro/general.conf files and restart lircd.

If you're still having trouble, unplug the second blaster, restart lircd, and ensure you only have /dev/lirc0 and /dev/lircd.  Then try 'irsend --device /dev/lircd send_once <remote> <command>' to test the first blaster.

You've been working with an out-of-the-box init script; so, all the config for your fist blaster is /etc/lirc/hardware.conf, /etc/lircd.conf (which should "include" your hardware config files), and your astro/general.conf file...that's it.  I have duplicate lircd.conf files in /etc and /etc/lirc on at least one machine; so, you may want to check that they are the same (I'm not sure which lircd attends).

Sorry about the typo on the irsend command.

Your channel change scripts will have to be modified to include the '--device <lircd instance device node>' option to irsend (way at the bottom).  Go ahead and do that (after backing them up) now; it can't hurt and may prevent problems caused by family changing channels while you test.  Once you bring up the second lircd instance, I'm not sure what problems might come up with scripts that don't include the device option.

You're really close.  The fact that the blaster worked during your diagnostic session proves it.

---

### Post by anonymousdog on 2008-09-11
BTW, reinstalling the MCC is probably not of any help; I think that was coincidence that your doing that preceded the last "recovery" of lircd.

---

### Post by ptipton on 2008-09-11
Thanks. I did try going to the backup files and had no joy, so tried removing and reinstalling everything and again no joy. However thinking about it the first time I did a reinstall and recovered the first blaster  I deleted the lirc files in var/run and this time I didn't so will try that again tonight.
What I'm struggling with at the moment is that something seems to break when I just leave the system alone. e.g. had the first blaster working fine last thing at night, come home the next day and its stopped!
Got to be close I think. Of course would be nice to be able to configure multiple ir devices from the control center.

---

### Post by anonymousdog on 2008-09-11
Yeah, the MCC is one bad <shut your mouth!>.  That one tool makes Ubuntu so friendly it's ridiculous.  But, when all's said and done, it's lipstick on a pig...a pretty, user-friendly, accessible UI to nothing more than a bunch of scripts configuring a miasma in the trenches.  The MCC is made to cover the usual cases, the lion's share; just your having two blasters with no remote probably makes your machine a corner case.  Don't get me wrong; I love linux, OSS and ubuntu, but, when you build a mutli-purpose box with it, and use it long enough, you obtain an appreciation of just how much it's all a hacked together conglomeration of discrete efforts.  It's not that it's less elegant than commercial offerings; it's that you get to see the underlying evil: the complication and integration; the crude technique to make it work, and the ephemeral beauty of doing it "the right way".  Wow...a few too many drinks at the bar tonight :).

I'd recommend reverting to the closest thing you can get to stable via file backups and unplugging new hardware.  If that yields a stable system; then, you can go forward.  Otherwise it's wolves in the mist.

Oh, yeah: You have lirc files (plural) in /var/run?  I have mostly pid marker files in /var/run, and only that for lircd.

---

### Post by ptipton on 2008-09-12
I deleted the lircd pid file in var/run reinstalled lirc and am now back to the original state of having 1 working blaster.

---

### Post by anonymousdog on 2008-09-12
Great!  Now edit your first blaster's channel change script to include the device flags (as [here](http://pastebin.com/m73d1dd46).)  You've already done that for the second blaster's channel change script; I'm not sure what lirc will do with the command if there are two lircd nodes and no device argument.  Actually, I'd edit the script, and make sure it works before making any more changes.

Then, plug in your new blaster, and restart lircd.  Test your original blaster again via channel change script commands and MythTV frontend (you can see we're taking the [paranoid] one-change-then-test path since you've had instability during more "free range" testing).

Then, do the corrected commands from post #8.  If that works, it's just a job of editing the init script and adding a few arguments to hardware.conf.  (Or you can try starting it up...<cough>hack<cough>...in /etc/init.d/rc.local if the init script proves tough to modify successfully.)

---

### Post by ptipton on 2008-09-13
OK now some significant progress. Modified the channel change script as you suggested, restarted and blaster 1 working fine.
Ran the corrected commands from post 8 and the first time got an error " No such file or directory" Restarted lirc and entered the commands again and now second blaster works from the command line and first blaster still works fine also. ( Looks like I have a problem with the setup of the second PVR150 in the myth backend as the second tuner isnt picking up the channels correctly so cant change channel from there yet).
So guess now need to edit the hardware.conf and the init script and sort the tuner in the backend.

---

### Post by ptipton on 2008-09-13
modified init.d/lirc and hardware.conf using the files from earlier post. Now neither blaste works and when i try either from the command line get:
root@ubuntuserver:/home/administrator# irsend --device /dev/lircd1 send_once blaster POWER
irsend: could not connect to socket
irsend: No such file or directory
root@ubuntuserver:/home/administrator# irsend --device /dev/lircd send_once blaster POWER
irsend: could not connect to socket
irsend: No such file or directory
root@ubuntuserver:/home/administrator# 

so still some tweaking to be done!

---

### Post by ptipton on 2008-09-13
Unreal, back to square one, no blasters working and no amount of restoring backup files or deleting lirc and staring from scratch makes any difference,
Frustrated to say the least!

---

### Post by anonymousdog on 2008-09-13
Glad to hear of the progress and sorry about the setbacks.

If you can find a way back to the status at post #18, you're 95% there.  Definitely don't reuse any of the old hardware.conf or init script edits; those clearly were broken.

If you can get the blaster to work from the shell, you can get it to work from mythtv.  It must have been a typo or syntax error in the backend setup.

As soon as you have that much, I'd just enter your corrected post #8 lircd command in /etc/init.d/rc.local and call it a day.  As long as there aren't timing issues with the main lircd startup (i.e., as long as modules/drivers are already loaded), it should be fine.

---

### Post by ptipton on 2008-09-15
Progress again. Found that some of the problems with blaster 1 were actually physical in that the position of the connector into the blaster socket on the card is very sensitive and if it gets knocked or moved slightly it doesnt work.

Having sorted that out and sorted the second card settings in mythtv I am now at the stage where if I boot the computer and enter:( from the previous post)
sudo /usr/sbin/lircd --device=/dev/lirc1 --output=/dev/lircd1 --connect=localhost:8765 --pidfile=/var/run/lircd1.pid & < /dev/null

Then both blasters work fine  and myth controls them OK.
So next I will try and enter this into /etc/init.d/rc.local and see if this works.

Would be nice to get it working in the " normal" way as think this would probably make life easier for upgrades etc. but right now will be very happy just to get it fully functional!

---

### Post by anonymousdog on 2008-09-15
There are only two issues with putting the command in rc.local:
[LIST=1]
[*]Timing issues (like the modules/drivers not being loaded by lircd prior to rc.local's execution.
[*]lircd1 not getting restarted with the normal init script (may yield unexpected behavior in any number of situations [where stopping lircd may be scripted]).  I'd stop rc.local prior to any upgrades/updates/other manipulations of lircd.
[/LIST]
I'm glad it looks like you're almost entirely sorted.  If you'd like to work on the init script, I'm willing to help.

---

### Post by ptipton on 2008-10-01
OK am back from my travels and keen to get this fully sorted.
Situation at present is that if after reboot I enter
sudo /usr/sbin/lircd --device=/dev/lirc1 --output=/dev/lircd1 --connect=localhost:8765 --pidfile=/var/run/lircd1.pid & < /dev/null

and then restart lirc then I have two working blasters. Haven't entered this into rc.local yet as am hoping to be able to correctly modify the init script.

One thing I have learnt from this so far is that its crucial to make sure that the PVR cards are fully seated in the PCI slot and that the ir cable is fully seated in the ir socket. Seems even a mm makes a difference with both of these.

---

### Post by ptipton on 2008-10-02
Just to sure, given had some hardware problems, I tried using the hardware.conf and init.d/lirc suggested in post 4 but this did not work and get :
root@ubuntuserver:/home/administrator# ls -l /dev/lirc*
ls: cannot access /dev/lirc*: No such file or directory

---

