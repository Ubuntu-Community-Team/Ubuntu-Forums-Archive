---
title: "Email won't send"
date: 2011-06-17
forum: Networking &amp; Wireless
---

### Post by Roger49 on 2011-06-17
[B]Email won't send

Apologies, I first posted this in "Absolute Beginner" and have realised its in the wrong place.
Roger.
[/B]             
                                                                [SIZE=3]Hi  all,
I'm using Ubuntu 10.10, with a Huawei E156G dongle on the Three network.  I can send webmail, but when I try from Thunderbird the smtp server  times out. I have received test messages sent from a webmail front end. I  have checked using telnet that the relevant ports are available.
The telnet message for the smtp server included the following line:
"220 three.co.uk mail relay -= NO UNAUTHORISED USE =- ESMTP"
I have copied all my ports and server details from my working Windows  installation.
I'm sure I'm not the only one who has had this problem.
Hope someone can help on this problem.
Regards,
Roger.[/SIZE]

---

### Post by crispy_420 on 2011-06-17
[http://www.3g.co.uk/3GForum/showthread.php?t=92807](http://www.3g.co.uk/3GForum/showthread.php?t=92807)

[http://www.pcadvisor.co.uk/forums/18/networking/355501/3-payg-dongle-cannot-send-email/](http://www.pcadvisor.co.uk/forums/18/networking/355501/3-payg-dongle-cannot-send-email/)

These get you anywhere?

---

### Post by Roger49 on 2011-06-20
[SIZE=3]Hi Crispy,
Thanks for those links.
One of them recommended using smtp port 587, and that, along with using port 110 for incoming seems to work. I have to switch off SSL though, otherwise nothing happens.
Any suggestions how to improve things? It's a very old email account, going back to when I was using a 56k modem, maybe I ought to upgrade it in some way? (Currently BTYahoo Classic).
Regards,
Roger.
[/SIZE]

---

