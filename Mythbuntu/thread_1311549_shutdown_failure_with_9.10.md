---
title: "shutdown failure with 9.10"
date: 2009-11-02
forum: Mythbuntu
---

### Post by kja999 on 2009-11-02
Hi,

After a fully successful upgrade to mythbuntu 9.10 the last thing I can't get to work anymore is a decent automatic shutdown.

My shutdown script basically (after setting the wake-up time), just sends a shutdown -h now.

When this is triggered by myth, the box goes down, the power light goes off, but it's still running. I can hear the disks and my TV still thinks there is some output.
The pc will hang indefinitely at this point... it never powers off.

I can run the same script by switching to the mythtv user and all works ok, its only when its auto triggered it fails.

This is all on a intel mac mini.

Any ideas ? I'm all out...

---

### Post by AKADAP on 2009-11-02
Is someone logged in when the auto-shutdown fails?
I noticed a new message box come up on 9.10 requesting a password when I tried to restart the computer when someone (me) was logged in.

---

### Post by kja999 on 2009-11-02
No, there are no other sessions running at the time :-(

There are lots of reports of issues of failure to power off after a shutdown for earlier kernels and mainly APM, but nothing seems to match current setups.

---

### Post by Milan Knizek on 2009-11-02
> **kja999 said:**
> 
My shutdown script basically (after setting the wake-up time), just sends a shutdown -h now.


What about "shutdown -P now"?
```
       -h     Requests that the system be either halted or powered  off  after
              it has been brought down, with the choice as to which left up to
              the system.

       -P     Requests  that  the  system  be  powered  off  after it has been
              brought down.
```

---

### Post by kja999 on 2009-11-03
Thanks for the idea, unfortunately changing the flag didn't work.

I think I have sorted it now by, changing sudo to no password for mythtv on the shutdown command, and changing the script to sudo the shutdown.
This has worked for the last 3 test shutdowns, although no idea why it should.
Previously I had set the sticky bit on the shutdown command, so authorisations were ok.

A mystery ...

---

### Post by kja999 on 2009-11-03
I spoke too soon .. after leaving myth to shutdown again, it failed....

---

### Post by DominicF on 2009-11-04
Hi,

I'm having the same problem.  I had this problem of shutting down the PC cleanly before I setup the script for Mythtv. Sometimes it would power down completely and other times not (as you describe with fan actvity etc. in the PC box).

I have a feeling that when I was using 9.04 with the ubuntu desktop instead of Xfce I was getting more clean shutdowns.  I plan to change to the ubuntu desktop tonight, I'll let you know how I get on with my tests.

---

### Post by johnnybirdman on 2009-11-04
Don't know if it is the same issue but check this thread:
[[COLOR="DarkOrange"]**_http://ubuntuforums.org/showthread.php?t=1299948_**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1299948")

---

### Post by kja999 on 2009-11-05
> **johnnybirdman said:**
> Don't know if it is the same issue but check this thread:
[[COLOR=DarkOrange]**_http://ubuntuforums.org/showthread.php?t=1299948_**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1299948")


I have done the actions .. just need to wait for a break in the recording schedule to have a try ..

Will let you know what happens

---

### Post by kja999 on 2009-11-05
Ok, just done a couple of boots .. no joy.
Interestingly, it does always seem to be the time after a wake-up event, that the next shutdown doesn't work.

---

