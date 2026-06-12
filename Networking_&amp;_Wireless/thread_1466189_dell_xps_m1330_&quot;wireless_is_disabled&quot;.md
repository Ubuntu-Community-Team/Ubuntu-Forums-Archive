---
title: "dell xps m1330 &quot;wireless is disabled&quot;"
date: 2010-04-30
forum: Networking &amp; Wireless
---

### Post by sghod1212 on 2010-04-30
So I was using 9.10 64bit and now I'm on 10.04 64bit, but the problem remains the same: clicking on the network manager icon I see "Wireless is disabled" and it's grayed out, preventing me from connecting to a wireless network.

I searched around for a solution and I actually did find one that works, but it's not very convenient. In order to get wireless working, I have to start Ubuntu, put the physical wireless switch into the off position, restart the computer, and then put the switch back into the on position. Is there a better solution out there? 

Upon the initial boot into 10.04, wireless did work right off the bat, but after installing new apps, graphics drivers, and doing updates it no longer works.

Thanks in advance :)

---

### Post by brodson on 2010-05-03
I have had the same result.

One thing you can do, rather than reboot...

Switch the wireless switch to the off position and boot up Ubuntu.  Then, after ubuntu boots, hit Alt-F2 (brings up the run screen) and enter the following command:

rfkill unblock all

Then switch the wireless switch on.  It should work perfectly from there on.

I had this same problem dating back to Jaunty.  It is clearly a bug, but I can't figure out where it is.

---

### Post by maraja on 2010-06-08
> **brodson said:**
> It is clearly a bug, but I can't figure out where it is.

My xps1330 (10.04 64bit) worked without issues on wifi until today, then it started refusing to enable the wireless connection.


I can confirm this solution worked also for me, hope there will be a bug fix later.
):P

---

### Post by rykel on 2010-09-26
I am running Lucid on Dell XPS M1330 and yes, I confirm that there is something WRONG with the wireless... although in my case, it is that the adaptor can see the networks around it but connect to none. (I have my own wifi network, which works with all the other Ubuntu PCs around me.)

---

### Post by itachiniko on 2010-11-03
On my XPSM1330 I used the restricted Driver Tool (System > Administration > Additional Drivers) and installed the Broadcom STA driver. Seems that the STA driver does not work so the other one should. Problem is that when I reopened the Restricted Driver Tool the second wireless driver is no longer there...how do I get that back?

Never mind. Once I restarted it was back Broadcom B43 is the one.

---

