---
title: "Spinning Pin Wheel of Death"
date: 2008-03-06
forum: Mac OSX
---

### Post by cprofitt on 2008-03-06
I just decided to try to get a Mac configured with AD today at work...

I booted up -- launched iTunes - selected to listen to SomaFM Groove Salad - went back to my linux box (IBM T42p) to research adding the Mac to AD.

In the middle of doing the research the music stops... I look over and the screen saver has engaged... I tap the mouse... and get the spinning wheel of death.

No error.

Just a spinning wheel.

Its been ten minutes now.

Um...

I guess I prefer the blue screen of death -- it at least tells me that I have an issue... and reboots. To be honest though I haven't had a BSOD in over two years on my WIndows XP or Vista machines.

Mac users must have the answer... right?

Well here is a sampling of the suggestions:

> Just hold down the power button til it shuts off, then turn it on again.

> Worst case scenario:
You may need to boot from your install disks and reinstall the base system. Done properly this will not cause any issues other than needing a few software updates.
It does sound like an issue with a startup application. Though, I’m guessing here because there really isn’t enough info to go on.

What? Oh... my... reinstall due to a spinning wheel of death?

>  **Limiting the number of open applications** If you aren't able to purchase additional memory, or if your system continues to experience routine slow-downs despite the presence of adequate RAM, try limiting the number of open applications. 
  Every open application, even if it is not performing any noticeable tasks, uses a portion of the Mac OS X virtual memory block. Closing unnecessary or infrequently used applications can therefore result in a reduction of spinning-wheel episodes.

I had one app open...

> **More uptime, more stalls: Restart more often** Although Mac OS X was designed to run 24 hours a day without a restart and does so well in most cases, some user set-ups may -- for varying reasons -- benefit from more frequent restarts.


I thought it 'just works' was the moto. I see that is not quite the case. Could OSX have a memory leak?


Well... I am glad I only have to help the OSX guys get their computers joined to AD... I got tired of complete computer lockups back with Windows 98... good to see Apple's OS is still back in the 1990s except for their gee-wiz GUI.


OK... being serious... is there any solution to this w/o a cold reboot?

---

### Post by LaRoza on 2008-03-06
I keep getting something like that in my Mac also (10.1.5).

I haven't found a way to fix it except by rebooting.

---

### Post by handy on 2008-03-08
I don't! :-)

---

### Post by cprofitt on 2008-03-08
> **handy said:**
> I don't! :-)
 
You don't what?

---

### Post by handy on 2008-03-08
> **PrivateVoid said:**
> You don't what?

Experience the problem.

---

### Post by cprofitt on 2008-03-09
The machine was an 'image' that the Mac tech had developed (and deployed on other iMacs and iBooks) so I decided after getting the spinning pin wheel more than ten times that I should rebuild it.
 
Since rebuiling it I have not experienced the issue.
 
At this point it I have to say it was likely a conflicting piece of software or misconfiguration of the OS, but I sure would have liked an actual error message instead of a spinning pin wheel... do Macs log errors?

---

### Post by handy on 2008-03-09
> **PrivateVoid said:**
> The machine was an 'image' that the Mac tech had developed (and deployed on other iMacs and iBooks) so I decided after getting the spinning pin wheel more than ten times that I should rebuild it.
 
Since rebuiling it I have not experienced the issue.
 
At this point it I have to say it was likely a conflicting piece of software or misconfiguration of the OS, but I sure would have liked an actual error message instead of a spinning pin wheel... do Macs log errors?

Perhaps Apple don't expect their customers to have the desire for error messages like the dreaded BSD, which most people find arcane & next to nobody deciphers the Hex.  Though I did meet someone once who could make a little sense of the hex.

I do agree, a simple message giving a clue to what's going wrong is surely a big help.

I expect that they do log errors, you will most likely have to grab a piece of software that will allow you to see the hidden OS.  Software does exist & it is free, though I can't remember what it is called.  Your Mac tech should know?

---

### Post by scramasax on 2008-03-10
> **handy said:**
> Perhaps Apple don't expect their customers to have the desire for error messages like the dreaded BSD, which most people find arcane & next to nobody deciphers the Hex.  Though I did meet someone once who could make a little sense of the hex.

The equivalent to the BSoD on OS X (or other Unixes) would be a kernel panic:

[http://docs.info.apple.com/article.html?artnum=106227](http://docs.info.apple.com/article.html?artnum=106227)

But that's *not* what the OP has got.  He's got a wait cursor.  That would be equivalent to the hourglass on Windows.

The first thing to do would be to run Activity Monitor and see what processes are using a lot of CPU.  It's in /Applications/Utilities.

As for the logs, there are, of course, logs.  They're in /Library/Logs and ~/Library/Logs.

Anyway, let's hope the OP is fine now and hasn't got an incipient hardware problem or something.

---

### Post by cprofitt on 2008-03-10
> **scramasax said:**
> But that's *not* what the OP has got.  He's got a wait cursor.  That would be equivalent to the hourglass on Windows.

The first thing to do would be to run Activity Monitor and see what processes are using a lot of CPU.  It's in /Applications/Utilities.

I was coming out of screen saver with no apps running... I was not able to force quit or get beyond a black screen with the spinning wheel.

> **scramasax said:**
>  As for the logs, there are, of course, logs.  They're in /Library/Logs and ~/Library/Logs.

If this happens again I will know to look there -- thanks.

> **scramasax said:**
>  Anyway, let's hope the OP is fine now and hasn't got an incipient hardware problem or something.

I did a complete reinstall of the OS and so far so good.

---

### Post by tgalati4 on 2008-03-10
It was probably iTunes waiting for a credit card verification.

Seriously, can you force quit?  I forget the key sequence, apple-command-F?

Sometimes you can just open a terminal and shut down to offending process (like in Linux--sudo kill -9 'process_ID').  What version of OSX?  Tiger 10.4.8 has been stable for me.  Almost 200 days uptime for a laptop that is used daily and put to sleep at night.

---

### Post by scramasax on 2008-03-11
> **PrivateVoid said:**
> I was coming out of screen saver with no apps running... I was not able to force quit or get beyond a black screen with the spinning wheel.

There's more going on that there seems to be.  Have a look at Activity Monitor, and you'll see plenty even when the drop-down menu is set to "My Processes".  Set it "All Processes" and you'll see even more.  (Top left of window.)

For example, you should see mdworker in there.  That's Spotlight, busy indexing in the background if it needs to.

I suppose some process could go runaway and need to be killed, just as you might on Ubuntu.  Nautilus froze up on me the other day, so that I couldn't even log out.  I had to kill it from the command line.  I could imagine similar problems with OS X's Finder --  or any one of a number of things that might be running in the background.

---

### Post by sebz2005 on 2008-03-12
What version of Mac OS X have you got?
Because 10.0 had many, many bugs and 10.1 had a few too, but I'm running 10.5.2 on my MBP and I've had it up for over two weeks running very CPU hungry programs, and I didn't experience any problems, nor and 'beach ball' freezes.

---

### Post by scramasax on 2008-03-12
> **sebz2005 said:**
> What version of Mac OS X have you got?
Because 10.0 had many, many bugs and 10.1 had a few too, but I'm running 10.5.2 on my MBP and I've had it up for over two weeks running very CPU hungry programs, and I didn't experience any problems, nor and 'beach ball' freezes.

The guy says earlier in the thread that he's using the machine and work and:

> The machine was an 'image' that the Mac tech had developed (and deployed on other iMacs and iBooks) so I decided after getting the spinning pin wheel more than ten times that I should rebuild it.

I'd doubt there's any professional users still deploying 10.1 to their users.

---

### Post by cprofitt on 2008-03-12
> **scramasax said:**
> The guy says earlier in the thread that he's using the machine and work and:



I'd doubt there's any professional users still deploying 10.1 to their users.

It was 10.5.2 and I rebuilt it to 10.5.2

---

### Post by sebz2005 on 2008-03-14
Huh. Well that's interesting.
Must be the version that your IT guy created.

---

### Post by cprofitt on 2008-03-14
> **sebz2005 said:**
> Huh. Well that's interesting.
Must be the version that your IT guy created.

It must have been the version my Mac IT guy created... funny that me the Linux/Windows IT guy was able to rebuild it and then have no issues.

---

