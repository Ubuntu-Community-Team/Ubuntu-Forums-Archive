---
title: "Installation of Mythbuntu freezes"
date: 2007-10-28
forum: Mythbuntu
---

### Post by colinnwn on 2007-10-28
I'm new to Mythbuntu, but I had Knoppmyth running successfully for several months before the hard drive crashed.  I decided to try Mythbuntu this time, but when I chose "Start or install Mythbuntu" I then see

Starting lirc daemon:
...
*running local boot scripts /etc/rc.local
The screen flickers for a bit and then it bluescreens and says...
Display server shut down 6 times in 90 seconds.  It is likely something bad is going on.  Waiting for 2 min before trying again on display :0.

I was just starting to learn Linux when Knoppmyth crashed several months ago.  I don't understand the problem.  Can someone point me to a troubleshooting description for this?  

I can get my full hardware specs out in a while.  But I think the most relevant item would be this is using my Olevia 32" TV connected through its VGA port as the monitor.  I would have thought this would be fine.  But do I need to yank the box out of the home theater and hook it up on my desk?

Thanks.

---

### Post by superm1 on 2007-10-28
Try safe graphics mode.

---

### Post by colinnwn on 2007-10-29
I tried last night, same problem occurred.  Any other thoughts?
Thanks.

---

### Post by superm1 on 2007-10-29
Checkout /var/log/Xorg.0.log and /var/log/Xorg.0.log.old.  See if they indicate why the X server is crashing.

---

### Post by colinnwn on 2007-10-29
So I did the ctrl+alt+F1 thing and nano'ed the 2 files you pointed me to.  They were both like 1800 lines long.  I scanned them and nothing jumped out at my newbie self.  I searched them for 'error' and 'EE'.  The only thing that came up was
(EE) - AIGLX : Screen 0 is not DRI capable

Does this suggest anything, or is there something else I should look for?

Thanks.

---

### Post by superm1 on 2007-10-29
> **colinnwn said:**
> So I did the ctrl+alt+F1 thing and nano'ed the 2 files you pointed me to.  They were both like 1800 lines long.  I scanned them and nothing jumped out at my newbie self.  I searched them for 'error' and 'EE'.  The only thing that came up was
(EE) - AIGLX : Screen 0 is not DRI capable

Does this suggest anything, or is there something else I should look for?

Thanks.
Yeah, you can try to disable DRI or AIGLX.  See if that helps out.  Google for how to do it.

---

### Post by colinnwn on 2007-10-30
I looked around and I couldn't decipher what people were saying about DRI.  But it seemed like the prevailing opinion to disable AIGLX was to add the following section to /etx/X11/xorg.conf

Section "ServerFlags"
Option "AIGLX" "off"
EndSection

So I nanoed and added the above.  When I tried to save it I got xorg.conf can't be written to, access denied.  Then I tried saving it as xorg.conf.new and got the same error.  Then I realized since this is all of a few seconds into the install routine, it is probably referring to the CD drive and not the HD.

I have no idea how to go about altering the iso to burn on another CD.  Plus the way it takes 50 tries for me to get something to work means I would have a nice coaster collection quick.  

Does anyone know if there is a way to disable DRI or AIGLX through a command line flag?  I'm pretty far out of my realm of competence here.

Thanks.

---

### Post by superm1 on 2007-10-30
Yeah edit it with 

**sudo nano**

instead of just **nano**

After doing this, issue a **sudo /etc/init.d/gdm restart**

---

### Post by colinnwn on 2007-10-30
I followed your directions and successfully restarted GDM.  I am still getting the bluescreen.  Something weird now is that the flickering and bluescreening occurs even in the 1st text terminal while I am using nano (or whatever else).  Before it was just in the graphical terminal.  When it didn't work I verified in Xorg.0.log that AIGLX was off, and that no new errors were appearing.

Any other ideas? 
Thanks.

---

### Post by superm1 on 2007-10-30
> **colinnwn said:**
> I followed your directions and successfully restarted GDM.  I am still getting the bluescreen.  Something weird now is that the flickering and bluescreening occurs even in the 1st text terminal while I am using nano (or whatever else).  Before it was just in the graphical terminal.  When it didn't work I verified in Xorg.0.log that AIGLX was off, and that no new errors were appearing.

Any other ideas? 
Thanks.
Does this happen on a standard ubuntu disk too?  If not, you can scp in your xorg.conf in to the live boot session.  Also, if this is the case, you can really help the xorg developers corner a related bug by getting your non functional xorg.conf, Xorg.0.log* files, and the functional xorg.conf on a bug tracker.

---

### Post by colinnwn on 2007-11-01
I ran memtest for a couple days at the suggestion of someone on the Knoppmyth board.  It turned out fine.  So last night I tried loading generic 7.10 on this computer and the exact same thing happened.  You suggest I submit this as a bug then, or was it only if Generic 7.10 worked and Mythbuntu didn't?

Thanks for your help.

---

### Post by colinnwn on 2007-11-03
I didn't understand.  Since this happens with regular Ubuntu, should I submit a bug to Xorg?  Or was that only necessary if Ubuntu worked and Mythbuntu didn't?  Also I can't imagine transcribing all of those logs.  Is there a good reference for how to use SCP.  Would eth0 would be up yet to transfer it across the network?  Is there another storage medium I could use?  Currently there is no floppy attached, but I suppose I could.

Also, with Knoppmyth the display works until it freezes on formatting the HD at 14%, and Mythdora graphic installation procedure worked until it rebooted for use and then my TV started saying 'Invalid Format'.  I don't know if that has any bearing on whether this is an Xorg problem or an Ubuntu problem.
Thanks.

---

