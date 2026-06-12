---
title: "The Old STR question (again)"
date: 2009-10-17
forum: Mythbuntu
---

### Post by jonnybignote on 2009-10-17
So I'm only about 2 weeks into Mythbuntu 9.04 and have already got myself pretty messy - but in a good way...  One thing that I can't get my head round though, which I'm sure the smart people here will tell me - Why is there no Suspend-to-Ram options out there for a Frontend-Backend machine.  I have seen the numerous posts and wiki's detailing how to use ACPI or Nvram-wakeup etc.  All of these, as far as I can tell involve shutting down the machine, which is fine I guess if you or your patient wife don't mind sitting there for 2 mins waiting for your live TV watching experience to start.  
My machine  suspends and starts up great (as I would think many newer hardware configurations might), I just can't tune LiveTV - I'm assuming I have to re-initialize the tuner cards (2xHDTV Wonder) somehow.  

That aside, I can't really see why the standby/resume thing is not an option...  The 10 seconds it takes to resume would be something akin to the time a dedicated DVR would take, and is completely doable...  With the relative ease that this is acheived with other competing platforms, I think this maybe a glaring omission in an otherwise amazing piece of software.

So this is by no means a rant, just newbie questions from someone with a simple machine setup who doesn't want to leave it running 24/7.  I'm interested to know anyone's thoughts on the matter....

---

### Post by bcgrown on 2010-01-01
See here for how to make auto startup/shutdown work: [http://ubuntuforums.org/showthread.php?t=1353286]("http://ubuntuforums.org/showthread.php?t=1353286")

Add /usr/sbin/pm-suspend to the %mythtv line in sudoers.

Replace MythWelcome's shutdown command with "sudo /usr/sbin/pm-suspend"

(make sure pm-utils is installed)

I've also added this to my ~/.lirc/mythtv file so that my MCE remote's "Power" button puts puts the machine to sleep:
```
begin
    remote = mceusb
    prog = irexec
    button = Power
    config = /usr/local/bin/dctoffandsuspend
    repeat = 0
    delay = 0
end
```

"dctoffandsuspend" is a script that turns off my cable box and then calls pm-suspend only if "mythshutdown --check" says the backend is idle.

You could also just kill mythfrontend,  and then MythWelcome will suspend the machine after the configured idle timeout.

MythWelcome doesn't launch the frontend if it detects it was auto-started for a scheduled recording.  I don't know if this check is done again after resuming from suspend.

---

