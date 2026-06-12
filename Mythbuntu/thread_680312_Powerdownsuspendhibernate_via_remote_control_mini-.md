---
title: "Powerdown/suspend/hibernate via remote control mini-howto"
date: 2008-01-27
forum: Mythbuntu
---

### Post by stdPikachu on 2008-01-27
Following on my earlier dealings with [LIRC]("http://ubuntuforums.org/showthread.php?t=678835") I've been tackling how to use LIRC to shut down the machine from the comfort of your sofa. You'll still need to get off your lazy **** to turn it back  on ;) unless you have some nifty wake-on-something-else set up.

Note that the rest of this howto assumes that you've already tested suspend/hibernate and that you know your machine can wake up properly from it. In my case, suspend isn't an option (argh) because my TV doesn't detect that the machine has been turned back on again; I use hibernate to force the BIOS to go through VGA POST again, and it's still faster than booting. However, the instructions here should be a good starting point to cannibalise for your own purposes.

My first problem was finding out which commands were used in ubuntu to shutdown, hibernate, etc, until someone pointed me in the direction that it was actually the login manager (which runs as root) that took care of all that, not the DE itself (which runs as you). With that in mind I had a look in the GDM config:
```
banquo@banquo:~$ grep -i shutdown /etc/gdm/gdm.conf | grep -v '#'
RebootCommand=/sbin/shutdown -r now "Rebooted via gdm."
HaltCommand=/sbin/shutdown -h now "Shut Down via gdm."
banquo@banquo:~$ grep -i suspend /etc/gdm/gdm.conf | grep -v '#'
SuspendCommand=/usr/sbin/pmi action suspend
SystemCommandsInMenu=HALT;REBOOT;SUSPEND;CUSTOM_CMD
AllowLogoutActions=HALT;REBOOT;SUSPEND;CUSTOM_CMD
banquo@banquo:~$ grep -i hibernate /etc/gdm/gdm.conf | grep -v '#'
HibernateCommand=/usr/sbin/pmi action hibernate
```
So we know we need to set the program `pmi` to run as root, since a regular user doesn't have the privelige. This is accomplished with sudo. First we need to know who we're running as, and then edit the sudoers file.
```
banquo@banquo:~$ whoami
banquo
banquo@banquo:~$ sudo visudo
```
At the bottom of the sudoers file add a line like this:
```
banquo ALL= NOPASSWD: /usr/sbin/pmi
```
Save and quit. That entry basically says that the user "banquo" can act as root, without having to type in a password first, but ONLY for the purposes of running `/usr/sbin/pmi`. Technically, this is a slight security risk (running anything as root without proper oversight is a risk - although I beleive the benefits outweigh the downsides in this case) and be very wary of adding lines to your sudoers file in this fashion. Those of you with multiuser setups might even want to go to the lengths to add all users to this sudo rule:
```
%users ALL= NOPASSWD: /usr/sbin/pmi
```

Now that's done you should be able to run `sudo pmi action hibernate` from your standard shell without having to enter your password, and the machine should hibernate. We can put this is a script if we like:
```
banquo@banquo:~$ cat ~/bin/user_hibernate
#!/bin/bash
sudo /usr/sbin/pmi action hibernate
```

Don't forget to make it executable! You should be able to `./bin/user_hibernate` and have the machine hibernate as if you'd run the command itself. Similarly, you can use the contents of this mini-howto to execute any script you wish via IRExec, even to the point of restarting your apache server or starting global thermonuclear war - such is the power of UNIX :D. Even more mind-nimbingly simple, you could just set a keyboard shortcut to run the script as well (finally, a use for all those stupid multimedia keys!). I've not tested it, but you should also be able to define a sudoers rule for this script itself rather than for pmi and run that with root privs instead, probably a more secure setup.

One gotcha to be aware of: remember when you run things as another user, they're running as another user ;) Sounds very daft, but just remember than if you `sudo ~/bin/someapp`, the ~ will evaluate to /root instead of /home/youruser and you'll end up running the wrong program (or, more frequently, a program that doesn't exist). Similarly, any custom aliases or suchlike that live in your user profile won't exist for root. This is another reason why it's often a good idea to use absolute paths wherever possible.

Once that's working we can move on to IRExec.

IRExec is an LIRC program used to launch arbitary commands for apps that don't support LIRC natively (like Myth does). Slightly annoyingly, it isn't started by default so we have to create our own launcher for it. Assuming you're using XFCE you can go to Applications > Settings > Autostarted applications (you should see network manager and mythfrontend in there already) and click "add";
Name: IRExec
Command: /usr/bin/irexec

Once we've got IRExec running all we need to do is assign one of the keys on our remote and get it to point at the script we made; this is also very easy to do. Go into your ~/.lircrc file and create an entry like this:
```
begin
        remote = hauppauge_nova_t
        button = power
        prog = irexec
        config = /home/banquo/bin/user_hibernate
        repeat = 0
        delay = 0
end
```
Please note that you shouldn't use a button that's already defined for another program; IRExec will ALWAYS execute it, even if you're running MythTV at the time. As it is, my "power" button isn't assigned any other duties. If you want to test whether irexec is working, set the config to "beep" and a press on the button should make a beep come out of your computer speaker.

Note that it's possible you may press the remote accidentally; I'm working on methods to mitigate this at the moment  (a popup in mythnotify perhaps? With, say, feedback and a 30s grace time?). I'd also like to use mythshutdown, but it doesn't support any of the funkier things like hibernation or suspend so I'm ignoring it for now. If anyone enterprising out there has something similar I'd love to hear about it.

Happy power-and-noise savings!

---

### Post by stdPikachu on 2008-01-27
OK, I've modified my shutdown script so that it now:
a) plays a sound to notify the user (couldn't get mythtvosd to work)
b) waits for 30s
c) if the poweroff button is pressed again within those 30s it cancels the shutdown
d) otherwise runs the command specified above
It's all very hackish at the moment but can probably be turned into something a bit more useful with a bit of work.
```
#!/bin/bash
LOCKFILE='/home/banquo/.mythtv/autoshut.lock'

# check for existing semaphore
if [ -e "$LOCKFILE" ]; then
        # write "cancel to existing lockfile
        echo 'cancel' > $LOCKFILE

        # exit
        exit 0
else
        # write semaphore
        touch "$LOCKFILE"

        # play a sound to notify user we're shutting down
        aplay -q ~/.mythtv/autoshut.wav

        # sleep for 30s
        sleep 30

        # check sempahore
        SHUTDOWN_STATUS=`cat $LOCKFILE`

        if [ "$SHUTDOWN_STATUS" == "cancel" ]; then
                # remove semaphore
                rm "$LOCKFILE"

                # ignore, exit nicely
                aplay -q ~/.mythtv/work.wav
                exit 0
        else
                # remove sempahore
                rm "$LOCKFILE"

                # shutdown
                aplay -q ~/.mythtv/exiting.wav
                sudo /usr/sbin/pmi action hibernate
        fi
fi
```
FWIW the WAV files are recordings of a TTS engine, the sort I used to have as sounds for windows events (ah, the folly of youth...!), sure most of you out there have something similar you can use. Did think of using festival but it's a bit of a big hammer to crack a nut with.

---

### Post by stdPikachu on 2008-01-27
In a word: bah. My scripts all seem to work fine, but LIRC seems to be b0rken when resuming from hibernate - myth doesn't respond to anything, and irw doesn't report anything either.

Oddly enough, there also seem to be two instances of irexec running after resuming from hibernate:
```
banquo@banquo:~$ ps aux | grep irex
banquo    5675  0.0  0.0   1692   340 ?        Ss   03:42   0:00 irexec -d
banquo    5713  0.0  0.0   1696   340 ?        Ss   03:42   0:00 /usr/bin/irexec -d
banquo    6571  0.0  0.0   2980   768 pts/0    S+   03:48   0:00 grep irex
```
which I'm pretty sure shouldn't be happening. Does anyone have any idea why? Seems that the one with the PID of 5713 is the one launched by XFCE;
```
banquo@banquo:~$ grep irexec .*/*/*
.config/autostart/IRExec.desktop:Exec=/usr/bin/irexec -d
```
...no idea where the other one has sprung up from. Since it's the only appreciable change I've so far seen I'm chalking up my LIRC woes to this at the moment, unless I've made a stupid mistake somewhere else.

After a clean boot there's ever only one instance of irexec running but it doesn't appear to be an XFCE problem (unless XFCE itself has problems with hibernate) since if I restart GDM after doing a `killall irexec` I still end up with two processes running.

For the moment I've just changed my hibernate options to shutdown instead, so I can at least get some utility out of it.

Further bah: irexec is still executing on startup even though I've disabled the autostart entry. Where the hell is it coming from?!

---

### Post by stdPikachu on 2008-01-28
OK, disaster over. Firstly I got around the multiple irexec problem by removing the -d option; it seems that it isn't killed even when all of its parents are, though I suppose that's the point of a daemon.

LIRC failing to work was due to a typo I made in my config file. D'oh!

Decided to use festival for my script in any case with entries like this:
echo "Computer shutting down, press again within thirty seconds to cancel" | festival --tts

---

### Post by yankcrime on 2008-02-07
would you mind posting your entire script (after you made the changes)?  I am having the issue that when I come back from suspend (using s2back), lirc seems to work (irw returns codes, etc.) however MythTV doesn't seem to be communicating with lirc.  I think this may have to do with unloading the lirc modules and reloading while Myth is running, but I am not quite sure.
Thanks!

---

### Post by 1jackjack on 2008-04-13
Hey, I've been looking for a way set hotkeys for suspend/reboot for ages! Thanks!
Do you know what the command is to turn off the monitor? That would just be everything I ever dreamed of!

hehe,
thanks,
Jack

---

### Post by laga on 2008-04-13
I'd like to point out that next MythTV upload (available in a few days on Hardy) will have some scripts in /usr/share/mythtv/: myth-halt.sh, myth-reboot.sh, myth-shutdown.sh and myth-hibernate.sh.

These use HAL/dbus to do their work and don't rely on playing with /etc/sudoers.

Maybe this will make someone's life easier :)

---

### Post by 1jackjack on 2008-04-14
found the display off command if anyones interested:
/usr/bin/xset dpms force off

regarding your command to suspend, is there any way to get it to require password on resume?

thanks,
jack

---

### Post by bmwman on 2009-01-02
OK, i got the Power down(suspend) via the remote to work. Now how do you turn it back on with the remote?

---

### Post by soderman on 2009-04-11
> **bmwman said:**
> OK, i got the Power down(suspend) via the remote to work. Now how do you turn it back on with the remote?

[http://www.mythtv.org/wiki/MCE_Remote](http://www.mythtv.org/wiki/MCE_Remote)

```
In order for the button to wake, you need to specify the USB hub in /proc/acpi/wakeup. If you cat /proc/acpi/wakeup, you should see something like this:

Device  S-state   Status   Sysfs node
HUB0      S5     disabled  pci:0000:00:08.0
HUB1      S4     disabled
USB0      S3     disabled  pci:0000:00:02.0
USB1      S3     disabled  pci:0000:00:02.1

If you issue the following command, the disable status will toggle to enabled

sudo sh -c 'echo "USB0" > /proc/acpi/wakeup'

Should result in:

Device  S-state   Status   Sysfs node
HUB0      S5     disabled  pci:0000:00:08.0
HUB1      S4     disabled
USB0      S3     enabled   pci:0000:00:02.0
USB1      S3     disabled  pci:0000:00:02.1

This command can be saved in your local.start

It also might be useful to change the MythTV exit settings to issue hibernate-ram on shutdown
```

/Söder

---

