---
title: "post-resume mouse pointer and remote repeat"
date: 2009-12-05
forum: Mythbuntu
---

### Post by matt06 on 2009-12-05
I have suspend/resume with my MCEUSB remote working[1] on a frontend running 0.22-fixes (22936) from the [Mythbuntu Automatic Daily builds]("http://www.mythbuntu.org/auto-builds").  After I resume from suspend, there are two issues.

The first is that mouse pointer/cursor appears and does not go away.  There is a [post about this on mythtv-users]("http://www.gossamer-threads.com/lists/mythtv/users/392081") with the solution of using [unclutter]("http://manpages.ubuntu.com/manpages/karmic/man1/unclutter.1.html").  I installed unclutter and set it up as a session startup program according to [this tutorial]("http://ubuntu-tutorials.com/2008/07/07/auto-hide-your-mouse-pointer-when-idle-with-unclutter/").

Unfortunately, it didn't work for me and the only way I can get rid of the pointer is to restart the frontend or play a video.  Playing music also works, but those are ugly fixes.  Unclutter is an acceptable solution so if I could get that working I'd be happy.  Does anyone know if this is a bug in Mythtv, Ubuntu or somewhere else?

The second problem is if you hold the remote power button down a split second too long when resuming the frontend will catch an additional button press and re-suspend the system.  I added a delay to the power button in my /home/{username}/.lirc/mythtv file as such:

```
# add button for remote suspend
begin
    remote = mceusb
    prog = irexec
    button = Power
    config = sudo /usr/sbin/pm-suspend
    repeat = 0
# add delay to prevent mythtv from picking up another
# button press when resuming from remote
    delay = 3
end
```

But that didn't seem to do anything.  If I hold the button down even for 1-2 seconds when resuming the system will suspend again.  Should I trying increasing the delay or should I be looking somewhere else for a fix?

[1] I used various info from the following pages and probably didn't do it as cleanly as I could have, but it works.

[http://www.mythtv.org/wiki/MCE_Remote#S3_.2F_Suspend_To_RAM](http://www.mythtv.org/wiki/MCE_Remote#S3_.2F_Suspend_To_RAM)
[https://help.ubuntu.com/community/MythTV/PowerSaving](https://help.ubuntu.com/community/MythTV/PowerSaving)
[http://ubuntuforums.org/showthread.php?t=675455](http://ubuntuforums.org/showthread.php?t=675455)
[http://ubuntuforums.org/showthread.php?t=1144999](http://ubuntuforums.org/showthread.php?t=1144999)

---

### Post by matt06 on 2009-12-05
Well I changed delay = 10 and it's still picking up another button press.  This is odd because my remote does not repeat any other buttons at all in the MythTV frontend (up, down, left, right, etc.).

---

### Post by gogee on 2009-12-09
I'm sorry I can't help with your IR problem, but I think I can lend a hand with the mouse cursor/pointer getting stuck on the screen after a resume from suspend.

From what I gather after having this exact problem myself, it has to do with the interaction of VDPAU of the Nvidia drivers and the hardware cursor setting in X/blitting plane something or other.

Anyways, if you add:

Option "HWCursor" "Off"

in the device section of your xorg.conf, I think you'll find your problem goes away.

Hope this helps.

---

### Post by matt06 on 2009-12-09
Thanks gogee, it worked wonderfully!  One more problem nailed down.

BTW, after Googling a bit I see people using both "Off" and "false" for this option.  I used "Off", but I suspect Off/On and false/true may be interchangeable when setting most of the device options.

EDIT:  Also, I am using an old Geforce4 card with the 96 drivers so there is definitely no VDPAU running on it.

---

