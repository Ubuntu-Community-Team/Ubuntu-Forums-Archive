---
title: "gateway stuck at 0.0.0.0 in 9.10 manual nic"
date: 2010-03-30
forum: Networking &amp; Wireless
---

### Post by jstateson on 2010-03-30
I just switched to manual from auto (dhcp) and cannot configure the network using that preferences - network connections applet.

I can put 192.168.0.1 into the gateway field, but when I click on DNS (to type in the DNS address) the address is set to 0.0.0.0 and I am asked for my password.  OK - I get the password in, but every time I enter the 192.168.0.1 the value is set to 0 when I click on apply or attempt to fill in the DNS name.

Googleing I see where this was mentioned in 8.1 and the suggestion was to edit some interface file.  Surely this would have been fixed in 9.10   I just got thru setting the gateway (using this same tool) in my Dotsch_UX 1.2 (8.1) system and also in my 8.04 system but my 9.1 POS seems broken.

sorry for the rant and thanks for looking.

---

### Post by iponeverything on 2010-03-30
> **jstateson said:**
> I just switched to manual from auto (dhcp) and cannot configure the network using that preferences - network connections applet.

I can put 192.168.0.1 into the gateway field, but when I click on DNS (to type in the DNS address) the address is set to 0.0.0.0 and I am asked for my password.  OK - I get the password in, but every time I enter the 192.168.0.1 the value is set to 0 when I click on apply or attempt to fill in the DNS name.

Googleing I see where this was mentioned in 8.1 and the suggestion was to edit some interface file.  Surely this would have been fixed in 9.10   I just got thru setting the gateway (using this same tool) in my Dotsch_UX 1.2 (8.1) system and also in my 8.04 system but my 9.1 POS seems broken.

sorry for the rant and thanks for looking.

Didn't see it as rant. 

Nm is little flaky. Fill in IP, netmask and gateway - then click back into the IP address field and then jump down to DNS field.

---

### Post by terazen on 2010-03-30
It might sound like a dumb question, but are you hitting enter after you type the gateway in?  I've had that problem sadly.;)

---

### Post by 98cwitr on 2010-03-30
You gotta hit the enter key for it to save the keyboard input

Pretty dumb and annoying huh? You'd think they'd fix that

---

### Post by frankie55 on 2010-04-02
Thank you, thank you, thank you for this answer. New to Ubuntu and I had been tearing my hair out over this for about a week. I had previously loaded Ubuntu on a half dozen machines but they already had their MAC addresses registered with our DHCP servers so they just acquired a DHCP lease. This is the first one I had to assign a static ip to, thank you again

---

### Post by Iowan on 2010-04-02
I would suggest you try via Network Manager - but it sounds like you already have it [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

---

