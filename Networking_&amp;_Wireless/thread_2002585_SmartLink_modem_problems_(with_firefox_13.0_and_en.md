---
title: "SmartLink modem problems (with firefox 13.0 and encrypted disk on Toshiba Tekra M5)"
date: 2012-06-12
forum: Networking &amp; Wireless
---

### Post by mcclary on 2012-06-12
[LEFT]I've been having trouble getting SmartLink dialup to connect reliably since moving to a Toshiba Tekra M5 (with internal SmartLink modem working through ALSA).
<br>
<br>
 I made this move with Maverick and by now have now moved to Oneiric (&quot;3.0.0-20-generic #34-Ubuntu SMP&quot;) with the problem persisting.
<br>
<br>
I've recently discovered a couple more pieces of the issue and am asking for help to find a fix.
<br>
<br>
The M5 has a Centrino Duo dual-core and a SmartLink (win)modem.  I'm running slmodemd, which works through the ALSA mechanism.  I'm also running with full disk encryption, which may be significant.
<br>
<br>
They symptoms have been that many attempts were needed before the modem would connect.  I had made configuration changes to the chat script, adding:
<br>
<br>
OK-AT-OK ATX1      (Show the connect speed.)
<br>
OK-AT-OK AT+MS=34  (Limit to v.34 for the long phone line.)
<br>
OK-AT-OK ATS7=120  (Wait up to 2 min for connect.)
<br>
<br>
But despite the S7=120 the connection would fail repeatedly with a NO CARRIER indication about 35 seconds after dialing. 
<br>
<br>
What I recently discovered is:
<br>
<br>
- Listening to the phone line:  During failing connection attempts the sound on one side (probably laptop-to-line) stuttered:  It was as if once or twice a second or so the software couldn't get the resources to generate the outgoing audio so it sent some silence - to a total of roughly half the time.
<br>
<br>
 - Stopping Firefox (13.0) would fix the problem.  Audio would be continuous and the modem would connect on the first (or at worst second) try.
<br>
<br>
- With Firefox restarted I could surf for a while.  But eventually the connection would drop.  Once that happened the PPP script would begin retrying the dialup connection establishment - which would again repeatedly fail until I killed Firefox.
<br>
<br>
Looking at &quot;top&quot; output I saw that:
<br>
<br>
- slmodemd was running at RT priority.
<br>
<br>
- Firefox was running at 20 (typical) and was usually eating 20-30 percent of one CPU (though it would settle down to 5%-ish once everything was loaded and the icons weren't doing the animated spin). 
<br>
<br>
- A process named &quot;crypt&quot; (along with a number of others which looked encrypted-file-system-related) was among those that were running at priority 0 (nice -20 = maximum).
<br>
<br>
IMHO nothing running at normal priority should be able to trash something running at realtime priority (if the other resources are being handled properly).  I'm guessing that Firefox somehow provokes - possibly indirectly - the hogging of a resource (CPU access, buffers, etc.) that is necessary for the generation of the modem output signal during connection attempts (but not while maintaining a connection).  Some of the likely culprits might be:
<br>
<br>
- Some modem-related task not running at RT when it should be.
<br>
<br>
- Some modem-related task not having enough privilege to get necessary buffers or not managing them correctly so it loses them and doesn't always get new ones in time.
<br>
<br>
- Disk encryption running higher than RT priority (or hogging buffers) and keeping some modem-related task from getting needed access.
<br>
<br>
- Some similar issue in ALSA or another of the many components supporting the modem.
<br>
<br>
Does anyone with more insight into these components have an idea what might be going on and (especially) how to fix it?[/LEFT]

---

### Post by mcclary on 2012-06-12
(Sorry for the awful formatting.  I'm on that slow dialup and haven't got enough access to try to straighten it out at this point.)

---

