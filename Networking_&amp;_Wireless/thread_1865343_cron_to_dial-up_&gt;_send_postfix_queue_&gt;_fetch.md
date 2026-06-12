---
title: "cron to dial-up &gt; send postfix queue &gt; fetch new mail messages"
date: 2011-10-20
forum: Networking &amp; Wireless
---

### Post by Nerdhacker on 2011-10-20
i have a home mail server where i plan to connect each 2 hours to send the mail queued in postfix and fetch the new mail for my users accounts in gmail.

so i want to crate a cron job to do all this and hang-up the dialup when all is done but i dont know how to do it?

i use
wvdial
postfix
fetchmail

the cron job should do the work in this order one process after another not all at the same time

**dial-up to establish internet conection >>> send/flush postfix queue >>> fetchmail the new messages >>> hang up dial up connection**

please can someone provide me a command line to perform this schedule at this order???
;)

---

