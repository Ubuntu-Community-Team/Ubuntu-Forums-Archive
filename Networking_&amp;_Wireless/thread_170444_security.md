---
title: "security"
date: 2006-05-04
forum: Networking &amp; Wireless
---

### Post by dogeatery on 2006-05-04
I had been using the internet and the little icon came up that says new updates are available.  I clicked it and got a message saying 'could not grab mouse' and then 'could not grab keyboard, someone may be eavesdropping on your activities.'  Then the whole thing just froze up and so I killed the power.

I use a wireless network, could it be that someone hijacked my signal and decided to crack into my computer?  DID someone crack into my computer?

---

### Post by linuxusr50 on 2006-05-04
I doubt you have been hacked.  Some things you can try from the command prompt are

history > This will give you a list of the last 500 commands that were entered.  See if you recognize any.

Review the following logs to see if there is anything that looks suspicious.

/var/log/syslog
/var/log/userlog
/var/log/authlog
/var/log/messages

Also look at running processes with the following command.

ps -A | less

Look for anything out of the ordinary and Google to see what it is.

If you are not using a strong password then change it to a more secure one.

Luck,
Dan

---

