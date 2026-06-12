---
title: "Mythwelcome Countdown when TV is off"
date: 2010-02-15
forum: Mythbuntu
---

### Post by vonda on 2010-02-15
Hi

I have a curious problem with mythwelcome.

My setup:

Mythbuntu Frontend + Backend combined hooked up to TV over VGA.

ACPI power-on setup with mythwelcome starting and counting down from 900 before restarting.

My problem:

The countdown works fine when the TV is on and set to the mythtv AV input. When I change inputs, or turn the TV into standby the countdown freezes. If I then return to the mythtv AV input the countdown resumes.

Any help on this would be great, even a pointer on where to start the troubleshooting as im totally baffled.

My electricity bill has just gone up for the 4th time this year and I think it's largely the mythtv box that's eating the power when it's sat idle for long periods of time.

---

### Post by gwagchunks on 2010-02-15
I recently got a LG LCD TV to replace my old CRT, and have it connected via DVI to HDMI input on the TV. I notice if I leave the input on HDMI (the mythbox), when the mythbox wakes up to record it'll switch the TV on if left in stand by. Similarly it will go into stand by when the mythbox powers down. I'm sure I have tried changing input to the satellite when the mythbox is counting down to power off and it has shut down OK. I've got to read the manual on the TV more closely as it is weird what it tries to do now with inputs. I'll check tonight to see if I get the same results as you.

---

### Post by vonda on 2010-02-15
After some more work tonight I lowered the count to 120 seconds so I could easily watch it count down. The count is getting to 0 then restarting instead of shutting down.

I have run a manual "mythshutdown -s;echo $?" from command line. It returns '0' which should mean its safe for shutdown but something is preventing it.

This is probably not linked to the count stopping when AV input is switched. Probably just a visual thing with the count actually progressing but looking like its stopped.

---

### Post by vonda on 2010-02-17
After some more digging around I have this solved.

I ran mythwelcome from the command line to check output, the shutdown command was being issued but not being acted on. Not much to troubleshoot there.

I then ran mythshutdown from the command line and kept getting an error: 'illegal time'. I eventually went back through the mythtv options for shutdown and prefaced all the commands with 'sudo -H'. 

I had also misspelt one option of mythshutdown. After following this process I restarted to find the machine shutting down as expected.  Problem solved!!

Now onto the wake-on-lan setup!

---

