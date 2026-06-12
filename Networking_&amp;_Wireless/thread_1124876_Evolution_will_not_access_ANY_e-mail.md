---
title: "Evolution will not access ANY e-mail"
date: 2009-04-13
forum: Networking &amp; Wireless
---

### Post by Macintosh SE on 2009-04-13
I have tried to use Evolution with Yahoo, Verizon, and Gmail. It always fails to connect with the same message:

"Could not connect to pop.gmail.com: Connection refused"

It shows the same message with Verizon and Yahoo. Strangely enough, I also tried the Verizon account with Thunderbird, which failed with a VERY similar message. Do I have to open ports or something? How should I fix this?

---

### Post by lisati on 2009-04-13
Are you updating the incoming server to reflect whether it's gmail or yahoo etc? It seems odd that your email software is complaining about pop.gmail.com when you're accessing Yahoo mail.
For gmail you might want to use pop.googlemail.com instead
(see screenshot for settings)

[http://mail.google.com/support/bin/answer.py?answer=13287](http://mail.google.com/support/bin/answer.py?answer=13287)

---

### Post by Macintosh SE on 2009-04-13
I guess I worded that badly. It provides the same "connection refused" error, but the server specified was specific to what I input into Evolution.


Now, it provides a list of errors unrelated to Gmail, even though I deleted the other accounts:

"Could not connect to smtp.mail.yahoo.com: Connection refused

Could not connect to plus.smtp.mail.yahoo.com: Connection refused

Could not connect to smtp.googlemail.com: Connection refused"



I changed "gmail" to "googlemail". Evolution seems to recognize the ports needed automatically, but still won't connect.


Any more ideas?

---

### Post by Macintosh SE on 2009-04-15
OK, it was my firewall blocking the necessary ports. I just whitelisted them, and all my email works (except for Yahoo, but that's a different problem - they want me to pay). This problem is now SOLVED.

---

