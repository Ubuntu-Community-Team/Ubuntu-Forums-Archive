---
title: "Mythbuntu 10.04 Not booting/loging on"
date: 2010-07-19
forum: Mythbuntu
---

### Post by Macka01 on 2010-07-19
Hi,

I noticed our mythbox was on at an unusual time (it starts up, records and shutsdown again), so I turned on my TV and switched over to the Mythbox only to find the purple loading/shutting down screen (I'm unsure as to which it was).

The system appeared to have frozen. Being a windoze user I hit Ctrl+Alt+Del, was greeted with some very fast white writing and the computer reset.

BIOS came up as usual, it appeared to be booting normally. Then up pops a message box.

I deeply regret not writing down the message; I read it and clicked OK (the only option).

I will post what I can remember, in the hopes someone will know what I saw:
error in <some> server <something>
/<something it may have been lib64 but I'm not so sure any more>

After pressing OK I was greeted by an unfamiliar login screen (probably the usual one for non frontend systems). The login screen had 1 user name and the option to login as Other. I clicked the username and entered the password. Screen goes black for a few seconds and I'm dumped back to the login screen. I try again, in case I mistyped the password. No luck. I clicked other and tried mythtv, root MythTV, mythTV. All presented me with Authentication Error.

I pressed alt+F2 no reaction CTRL+ALT+F2 dropped down to prompt. I pressed alt+F1 - F8
F1-F7 changed TTYs (not sure what they are exactly, they seem to be alternate terminals.)
F8 brought up the login screen again.

I am at a complete loss as to what I should do. Under windows I'd attempt to enter safe mode... but this is not windows :(

Thankfully I have a separate partition for video, but I'd rather not wipe my current partition if I can help it.

To be honest, I think I've had more problems with 10.04 then I ever had with 9.10.

Any ideas would be greatly appreciated.

---

### Post by jonnybignote on 2010-07-19
Hi,
I've been getting this within the last week or so.  My machine suspends (s2ram) usually when not in use, but to keep running smoothly, after maintenance at 4am, it performs a reboot.  Now, I often wake to find the machine stuck at non functioning frontend or at the login screen as you mentioned.  Syslog shows some kind of authentication problem though I'm at a loss.

I believe that running filesystem checks can temporarily cure the problem (after many useless reboots I hard reset the machine that prompted a check which seemed to fix it until the next time..)

I actually got on the site for the purpose of enquiring about the very issue which I can't seem to get around.  I could probably modify my cron script to force the disk check every morning but that is only a bandaid on the issues.

I suspect this has to do with a recent update (after many months of denying updates I finally relented and updated a lot of files)

Interestingly, my machine is 9.10...64bit

---

### Post by Macka01 on 2010-07-19
As glad as I am to hear that I'm not the only one experiencing this, it is a shame that it is happening at all.

I haven't done any updates at all. I am running the 64-bit version I can't remember whether I used 64 or 32 bit for 9.10

EDIT: I should also add that using top, it appears mythbackend is running, however the webUI is unreachable

EDIT2: I noticed a very fast message when the system was booting, I only had the time to read the word "error" so I filmed the start up. This is what the error reads:
[    8.477356] nForce2_smbus 0000:00:01.1: Error probing SMB2

---

### Post by Macka01 on 2010-07-20
I managed to find something in the bug tracker on this problem, but the solutions didn't help, most likely because I'm a linux noob.

So I slaughtered the Lynx and reinstalled.

---

