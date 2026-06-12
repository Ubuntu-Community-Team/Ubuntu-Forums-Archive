---
title: "External Hard Drive Berserk?"
date: 2010-07-03
forum: Mythbuntu
---

### Post by dsbw on 2010-07-03
I added another USB hard drive to my system (I have three now) and this third one seems to go berserk.

That is, the computer will be on for a while, sometimes not very long at all, and it'll start flickering. Shows that are on this drive appear in the recordings area but with black previews and file-not-found errors. The back-end will sometimes become unreachable, and the web server.

I'm goin' nutso trying to figure out what the hell this thing is doing! Nothing's recording there aren't any commercial flagging jobs that I see. I've been looking at top and ps but I can't really make heads or tails out of it. Nothing looks untoward as far as CPU time.

Not sure where to look on this one!:eek:

---

### Post by Dr_Willis on 2010-07-03
when it acts up check the output of the 'dmesg' command, or monitor the log
files in 

/var/log/messages  and /var/log/kern.log   You can watch them in real time with the command like.

```
tail -f /var/log/messages
```

I have had a few external usb HDs that like to power/spin down, or have other issues and constantly get 'reset'  This can cause all sorts of annoyances.

At least this is where i would start to get some info on the problem.

---

### Post by dsbw on 2010-07-04
I have a real problem doing that because the activity tends to make it impossible to get a terminal in there. I do have a keyboard attached but it's awkward.

I didn't have a ton of messages in either log, just this one:

 kernel: imklog: Cannot read proc file system, 1.

---

### Post by dsbw on 2010-07-10
OK, tail -f /var/log/messges doesn't show anything but dmesg shows a bunch of:

xfs_log_force: error 5 returned

---

### Post by GuiGuy on 2010-07-10
[QUOTE=dsbw;9570960]OK, tail -f /var/log/messges doesn't show anything but dmesg shows a bunch of:

xfs_log_force: error 5 returned[/[URL="http://www.google.com.au/#hl=en&safe=off&q=%22xfs_log_force%3A+error+5+returned%22&aq=f&aqi=&aql=&oq=&gs_rfai=&fp=f70e2b427ce54872"]QUOTE]

Google shows a whole bunch of stuff[/URL] relating to that error.

---

### Post by dsbw on 2010-07-10
Yeah. I'm trying an xfs_repair. It's been twelve hours.

---

### Post by dsbw on 2010-07-17
xfs_repair failed. Reformatted. All was well for a week.

Now it's going crazy again.

Bad drive?

---

### Post by ian dobson on 2010-07-18
Hi,

Bad drive or bad USB case (may not be bad, rather a dodgy USB bridge chip). Note xfs isn't that good at recovering from fs corruption.

Maybe try using a different file system (ext3 or ext4). I've been using ext4 for about 12months now for my recordings fs and haven't had any problems/corruption even under really heavy loads (6 recordings at the same time - 3 HD, 1 SD from PCI tuner and 2 from ethernet tuners).

Regards
Ian Dobson

---

