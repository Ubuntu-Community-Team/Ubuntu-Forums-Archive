---
title: "HDMI monitor boot issue..."
date: 2009-11-28
forum: Multimedia Software
---

### Post by carrollguthrie on 2009-11-28
I'm not sure if this issue goes here or in the Desktop environment forum. Oh well, here goes...
 
I have installed Ubuntu 9.1 on my home theater computer and after much research and work I have it displaying on my JVC LCD TV quite nicely. I have one issue I can't get past yet.. 
 
the mobo is a Gigabyte GA-MA785GM-US2H and has three video outputs, 1 HDMI, 1 DVI and 1 D-Sub. I can get the video to work on any of the three outputs AFTER booting up with the D-Sub but I can't get X to start unless there is a monitor plugged into the D-sub output. 
 
for instance...
 
If I have the LCD TV connected to the computer with only the HDMI cable, the computer will boot and I can see the BIOS information on the screen. I can see Grub loading and since I have it configured as a dual boot, I can choose which OS I want to boot into. 
 
The problem is at this point. Ubuntu starts booting and the LCD TV screen just goes blank and the boot process won't continue. If I have a second monitor plugged into the D-sub output this doesn't happen, X11 boots up and everything works fine. 
I did a test where I let the system hang and waited several minutes, then plugged a LCD monitor into the D-sub and it u-hanged (Look I made a new word) and continued to boot up X11. 
 
In conclusion, it seems that without something plugged into the D-sub, X11 won't initialize and start. 
Is X11 looking for some kind of input signal that it only gets from the D-sub and not the HDMI? 
Is there a way to force X11 to not look for this feedback? 
Can I make X11 skip this hardware check. 
IF I can get this figured out, will I still be unable to play the piano?
 
Any ideas would be greatly appreciated..
 
Carroll
Ubuntu convert

---

### Post by SpeedSk8X on 2009-11-29
We're having the same problem in my thread from a couple days ago.

[http://ubuntuforums.org/showthread.php?t=1333717](http://ubuntuforums.org/showthread.php?t=1333717)


Can you SSH in to your box when this happens?

---

### Post by efflandt on 2009-11-29
I added a solution to the thread SpeedSk8X linked to.

---

### Post by carrollguthrie on 2009-11-29
> **SpeedSk8X said:**
> We're having the same problem in my thread from a couple days ago.
 
[http://ubuntuforums.org/showthread.php?t=1333717](http://ubuntuforums.org/showthread.php?t=1333717)
 
 
Can you SSH in to your box when this happens?
 
----------------------------------------------------------------------------------------
 
Ok, I tried the fix Efflandt posted on the above thread and in my instance, no luck.  I tried several other tests and here are my findings...
 
---  No, I can't SSH into the box when it hangs.  this is a little puzzling because if you look in /etc/rc2.d SSH is the first thing that is loaded.  SSH is S16 and grub-common is S99.  Shouldn't SSH already be alive and listening before grub even starts to load?
 
---  I changed 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

to:

#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
# Use "" to see boot messages or "quiet" to hide them
GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX=""
 
and rebooted but I still get the blinking curser and the endless black screen.  the boot process still hangs.  AGAIN, at this point, even if it has been sitting at the blank screen for 5 mins, if I plug in a VGA monitor to the D-Sub connector on the back of the computer it will resume the boot process and finish booting up.  It is waiting for some kind of feedback from the monitor that it's not getting from the LCD TV on the HDMI connector.  Strange...
 
---  Just to make clear, it doesn't matter if I have the LCD TV plugged into the HDMI port or not, it will boot only if I have the VGA monitor plugged into the D-Dub port. 
 
---  NOTE:  I did another test where the LCD TV was plugged into the HDMI port and the VGA monitor was plugged into the D-sub port AND the VGA monitor was UNPLUGGED from the wall, NO power to the VGA monitor.  NO hangup, Ubuntu booted normally. 
 
It seems that grub does some kind of check to see if there is a monitor and waits for one to be present..  I took a look at /etc/grub.d/00_header and found this...
 
case ${GRUB_TERMINAL_INPUT}:${GRUB_TERMINAL_OUTPUT} in
  serial:* | *:serial)
    if ! test -e ${grub_prefix}/serial.mod ; then
      echo "Serial terminal not available on this platform." >&2 ; exit 1
    fi
    if [ "x${GRUB_SERIAL_COMMAND}" = "x" ] ; then
      grub_warn "Requested serial terminal but GRUB_SERIAL_COMMAND is unspecified. Default parameters will be used."
      GRUB_SERIAL_COMMAND=serial
    fi
    echo "${GRUB_SERIAL_COMMAND}"
  ;;
esac
 
so I know that grub is looking at the terminal input for something..  could this be my issue?  Is there a way to make grub ignore this test?
 
 
Right now I just have an old monitor plugged into the D-sub output and turned off and my LCD TV plugged into the HDMI output.  This works but I have a dead monitor sitting in my living room floor just waiting for me to kick it with my little toe. (s*&t that hurts).
 
Any help would be appreciated...
 
Carroll

---

### Post by carrollguthrie on 2009-11-29
OK,
 
I'm feeling a little stupid at the moment. AFTER I posted that last reply, I had a brain f**t and realized that I didn't do an update-grub after making changes to /etc/default/gru and before I rebooted.. 
I went back and did the work around that Efflandt posted, did an update-grub and now grub boots without the VGA monitor plugged into the D-sub output of the mobo...
 
dare I ask how to keep the stream of garbage from echoing on the screen during boot? 
 
Efflandt, thanks for your help... my little toe is no longer in danger of kicking the dead monitor sitting in the middle of the living room floor...
 
Carroll

---

