---
title: "What caused network connection to fail? Leap year bug?"
date: 2009-01-02
forum: Networking &amp; Wireless
---

### Post by LisaM on 2009-01-02
This isn't a new install.  I've been using Ubuntu 8.04 happily for months now.  Then, this morning, boom - no network connection!   What could have caused this?  Is it a hardware failure?  end of year software bug?   How can I diagnose and solve this problem?   Please help me!

I'm running a Dell Inspiron 1420 laptop, connecting via wireless to a home network.  The network is running fine.  Something's wrong with the laptop, only I can't tell what it is.  I haven't made any system changes recently.

Thanks!

Lisa

---

### Post by superprash2003 on 2009-01-03
post output of
1)iwlist scanning
2)iwconfig
3)ifconfig

 from the terminal

---

### Post by LisaM on 2009-01-04
Sorry for the newbie question, but since I can't connect to the internet on the laptop, can you tell me how to output this information to a file?  (so I can copy to a jump drive)

Thanks!

---

### Post by Iowan on 2009-01-04
Quick way is to use redirect operator (>>) - eg. **ifconfig >> ifconfig.txt**.


 The redirect operator is actually just ">".  The example above *appends* data to a file.  If the file doesn't exist, it creates it - so the result is the same, but if the file already exists, ">" will replace it, ">>" adds to it. Sorry if I've caused any confusion.

---

### Post by LisaM on 2009-01-11
Thanks, everybody.  We have resolved the problem.  

The problem was caused by a wireless card failure.  I ordered a new wireless card from Dell. (not an easy thing to accomplish - that company has serious customer service problems)  After replacing the card, we had to Remove the connection to our family network, because the configuration wasn't accepting the password, then let the card find it again, prompt us to enter the password, and everything was working again!

---

