---
title: "Frontend crashing when rewinding live TV"
date: 2011-09-17
forum: Mythbuntu
---

### Post by trentos on 2011-09-17
Hi guys,

I've recently installed Linux for the very first time, and I'm trying to set up a MythTV backend/frontend system in my house. I'm currently using Mythbuntu 11.04 on the following hardware:

Core i7 920
Geforce GTX 295
ASUS P6T SE Motherboard
MyGica T1680B DVB-T capture card

The biggest problem at the moment is my frontend crashes when I rewind live TV back to the beginning of the recording. This causes Myth to display error code 139 and immediately restart the client. This error is very easy to reproduce - it always happens when I rewind after only watching TV for a few seconds. The error doesn't occur if TV has been running for longer periods of time (e.g. 1 minute or more).

There's an option in the MythBuntu Control Center to upload the frontend log file to pastebin, so I have done so. I removed the part of the log relating to previous runs of the software as I get exactly the same error each time. Here's my log file:

[http://pastebin.com/xksYFk4z](http://pastebin.com/xksYFk4z)

This problem is not specific to MythBuntu as I was previously using Ubuntu 11.04 and installed Myth using the software center. The program was crashing in exactly the same way.

What can I do to fix this problem? Please remember I only just started using Linux so if you ask me to post more logs or run in debug mode, I'll need to know how to do this first.

Thanks

---

### Post by nickrout on 2011-09-18
mythbuntu has exactly the same packages as ubuntu so it's not sur[rising you get the same result in each.

I cannot see a crash in your log, can you identify approx which line co-incides with the crash?

---

### Post by trentos on 2011-09-19
> **nickrout said:**
> mythbuntu has exactly the same packages as ubuntu so it's not sur[rising you get the same result in each.

I cannot see a crash in your log, can you identify approx which line co-incides with the crash?

Line 101 is where the crash causes my client to restart. The crash must occur immediately before this.
"Player(0), Warning: Waited 100ms for decoder to pause" is either an indicator that the software is about to crash, or has already crashed.

---

### Post by trentos on 2011-09-25
Nobody has any suggestions? Well how about I upgrade my TV card drivers and eliminate those audio error messages in the log?

Are the drivers downloaded by Ubuntu automatically the latest version or are there more up to date TV card drivers avaliable elsewhere? How do I check what driver version I'm using? And where can I find newer drivers to download when the vendor for my card only lists the Windows drivers on their site?

---

### Post by trentos on 2011-12-30
I'm now using the new Mythbuntu with Ubuntu 11.10, and I'm having exactly the same problem.

The time I've spent trying to fix this is far too great to justify continued attempts. I should be able to just buy something that works already.

Does anyone have any suggestions for hardware combinations that are known to work properly, bug free, out of the box with a fresh Myth installation?

---

### Post by nickrout on 2011-12-30
> **trentos said:**
> I'm now using the new Mythbuntu with Ubuntu 11.10, and I'm having exactly the same problem.

The time I've spent trying to fix this is far too great to justify continued attempts. I should be able to just buy something that works already.

Does anyone have any suggestions for hardware combinations that are known to work properly, bug free, out of the box with a fresh Myth installation?

Firstly does this happen on playback of recordings? Or is it restricted to live tv?

Secondly, do you need to rewind livetv immediately after you start it? From your symptoms it sounds something like it is trying to go back further than the start of the file, but that is a guess.

Thirdly you should appreciate that LiveTV is not a priority for the myth developers. There are bound to be some bugs, maybe your unusual habit of rewinding soon after you enter livetv has uncovered one. Try recording what you want to watch and you can still watch the recording while it is being recorded. A small change of habits may get you what you want.

Thirdly try running the fontend with -v all and see if you come up with some more info around the time of the crash.

Fourthly, myth is at 0.24.1, not 1.0. There will be bugs. It is up to users to report them, once they are sure it is a bug and not a misconfiguration.

Let's see the more detailed logs (as above).

PS you are running the very latest 0.24.1 from mythbuntu repos aren't you?

---

