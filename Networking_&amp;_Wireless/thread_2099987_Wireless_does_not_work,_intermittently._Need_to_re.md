---
title: "Wireless does not work, intermittently. Need to restart."
date: 2012-12-31
forum: Networking &amp; Wireless
---

### Post by Paddy Landau on 2012-12-31
When I boot my computer, sometimes the wireless works and other times it does not.

[LIST]
[*]When the wireless works, it continues to work correctly until I turn off the computer.
[/LIST]

[LIST]
[*] When it fails, I have to keep restarting the computer until it works; sometimes once, sometimes several times. (Maybe there is a quicker way?)
[/LIST]
 I have no clue how to diagnose and fix this problem. To try to help, I have run [FONT=Lucida Console]sudo[/FONT] [FONT=Lucida Console]lshw[/FONT] and attached the results.

I am running Ubuntu 12.04 64-bit fully updated.

Any ideas on how to fix this problem?

---

### Post by Pjotr123 on 2012-12-31
Is there always a Windows boot in between? If so, try this:
[https://sites.google.com/site/easylinuxtipsproject/internet#TOC-No-wired-or-wireless-internet-on-a-dual-boot-computer](https://sites.google.com/site/easylinuxtipsproject/internet#TOC-No-wired-or-wireless-internet-on-a-dual-boot-computer)
(item 3, right column)

---

### Post by Paddy Landau on 2012-12-31
Thank you for that. I have not noticed whether or not this is the case. I shall test it, notice what happens, and let you know.

Whoever would have thought that a Windows bug could affect Linux? LOL

---

### Post by Paddy Landau on 2012-12-31
So far, the link you gave seems to be the diagnosis and solution, thank you.

BTW, [that site]("https://sites.google.com/site/easylinuxtipsproject/") is a rather nice one.

I shall mark this as solved. However, I would like to know the equivalent of the [FONT=Lucida Console]ipconfig[/FONT] [FONT=Lucida Console]/renew[/FONT] command in Linux. Perhaps running this at Linux start-up would do the trick?

**EDIT:**

It has just failed to work. In fact, despite even powering off the computer and then restarting it, what finally worked was rebooting my router.

Oh well, such is life. It seems that a bug in Windows stops Linux from working. :???:

---

### Post by Paddy Landau on 2012-12-31
I'm marking this thread as unsolved. It is definitely not Windows. I have restarted, even powering off for a couple of hours, without going into Windows; and the problem recurs.

So…

What next?

---

### Post by Pjotr123 on 2012-12-31
Is your router running on the latest firmware for it?

---

### Post by Paddy Landau on 2012-12-31
> **Pjotr123 said:**
> Is your router running on the latest firmware for it?
Yes, it is. The router is quite old; I bought it August 2008, but the firmware is up-to-date.

Do you think it may be the router and not the computer? Mind you, Windows has never had this problem; only Ubuntu.

---

### Post by Pjotr123 on 2012-12-31
It might be the combination.... And it's the trial and error I like best: actions that can do no harm at all, and are easily reversible.

You might try some of the items in this roadmap:
[https://sites.google.com/site/easylinuxtipsproject/internet](https://sites.google.com/site/easylinuxtipsproject/internet)

I suggest the items 1.4, 1.5, 2.1 and 2.3.

They might help, and if not, won't harm.

---

### Post by Paddy Landau on 2013-01-01
> **Pjotr123 said:**
> I suggest the items 1.4, 1.5, 2.1 and 2.3.
Thank you for the advice.

1.4 and 1.5 did not help; 2.1 was already set to off; and 2.3 is not suitable for our use.

Oh well. Damn computers!

---

