---
title: "Ubuntu Not Accepting SSH Password"
date: 2013-04-15
forum: Networking &amp; Wireless
---

### Post by giliinc1 on 2013-04-15
it doesent work when i put password on mac i do "ssh user@ipaddres" and i put password but i does not work

---

### Post by Iowan on 2013-04-15
Unfortunately, your question seems a bit brief and vague. 
Can you SSH into this machine from a different computer?
You have set up the keys on server and client?
Do you get an error message, or no response?
Can you **ping** the machine?
Is "mac" an Apple (or media access control )?

---

### Post by Cheesehead on 2013-04-15
Did you perhaps mistype the password? Your one-sentence description has several spelling and grammatical errors - sometimes that's a keyboarder typing too fast and making mistakes.

Did you install an SSH server?
Did you configure the SSH server?
Did you perhaps disable passwords on the SSH server?
What kind of error message you you get? Don't summarize. Paste the entire message here.

---

### Post by permittivity22 on 2013-04-16
try  doing a verbose output of ssh and repost:

ssh -vvv username@ip

of course, mask the username and ip (if it's a public IP) before posting.

---

