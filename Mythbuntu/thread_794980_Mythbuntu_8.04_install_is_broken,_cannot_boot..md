---
title: "Mythbuntu 8.04 install is broken, cannot boot."
date: 2008-05-15
forum: Mythbuntu
---

### Post by amphibem on 2008-05-15
OK so I have broken my mythbox and need some help fixing it, you guys have been great so far so I will try here before trying the general ubuntu forums.

I was playing with the media center via ssh setting up no-ip so i could get external access to mythweb. Done this plenty of times before while the backend and frontend do there thing with no problem. All I did in Mythbuntu is install no-ip, and change rc.local to include

```
/usr/local/bin/no-ip2
```

(maybe not exactly, but something to start the no-ip2 service at boot)

I then went to the box and found nothing on the screen and the MCE2 receiver flashing its red led. So I assumed it had crashed and rebooted from shh (which was obviosuly still up). I go to reboot and it says something about a BIOS reset, with F1 to edit the BIOS and F2 to carry on with defaults. I go into the BIOS, time and date are correct but my other settings have gone to default so I change them back. I reboot and it gets stuck at the mythbuntu splash screen with the progress bar at about a quarter of the way across.

I think it is the rc.local script that could be the trouble so boot into the Live CD (which works thankfully) but rc.local is the standard script. There is also an error on the taskbar about not being able to connect to the backend but I guess that is due to it being configured as 127.0.0.1 or something.


Any ideas on what I can do? I do not want to loose what is on the hard drive and do not have the time to do a recovery and re-install, this is a real pain. Would be handy to know what I may have done wrong too :P

Cheers

---

### Post by amphibem on 2008-05-15
OK so a quick update:

Managed to find the correct rc.local with the Live CD and deleted the line about no-ip2. Restarted and it didn't work, restarted again and it did! I am happy. However I restart to make sure it is alright and it doesn't work. Tried a couple more time and no luck.

So what to do? Is it possible to show text instead of the splash screen with progress bar at boot? Then I could see what it was locking up at. Is there something I can run to repair the install?

---

### Post by ozybushwalker on 2008-05-21
Here's how I got more information out of the boot. It didn't help me because it didn't conclusively point to one thing - over a number of boots the startup halted at quite different points. Nevertheless it might be helpful in your case.

At boot when the different kernel options are presented ('Ubuntu 8.04 ...', 'Ubuntu 8.04 ... (recovery mode)' and 'Ubuntu 8.04, memtest 86+') 
[LIST=1]
[*]The first entry (not the memtest86+ and not recovery mode) should be selected, if not use the arrows keys to select it
[*]press 'e' to edit the boot commands
[*]using the arrow keys move the cursor to the last line ('quiet') and press 'd' to delete it
[*]move the cursor up to the line starting 'kernel' and press 'e' to edit that line
[*]the cursor should be positioned at the right hand end of the line, if not press the right arrow key until it is
[*]use the backspace key to erase the words 'quiet' and 'splash'
[*]press 'b' to boot. This should boot without a splash screen and the startup should give you progress reports after the normal kernel startup output
[/LIST]

---

