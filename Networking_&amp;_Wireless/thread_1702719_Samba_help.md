---
title: "Samba help"
date: 2011-03-08
forum: Networking &amp; Wireless
---

### Post by s.ezhilmani on 2011-03-08
HI,
I have ubunto desktop 10.04 LTS
I installed samba and able to access the share on windows machines.However i want to access the share on 300 windows machine(for example) systems at a time 
Is it possible.
Pls help me.

---

### Post by new_tolinux on 2011-03-08
Should be no problem, the only bottlenecks are your hardware.
If your "server"-hardware and networking is able to handle it, there should be no reason why samba couldn't.

---

### Post by s.ezhilmani on 2011-03-08
Thanks.
Then what is the difference between ubuntu deskto edition and server edition?

---

### Post by new_tolinux on 2011-03-08
More or less the GUI and what's installed....
The server edition comes without the GUI and therefore needs less programs to be installed by default.

---

### Post by s.ezhilmani on 2011-03-08
thank you.

shall i install desktop version in IBM Rack server.x 3650 intel xeon processor.

---

### Post by new_tolinux on 2011-03-09
I, for myself, never install the server edition, although I do alter the grub-configuration so that it does not boot into the gui by default.

Because (for me) some things are easier to do in the gui, sometimes I just login to the text-interface and then start the gui manually.

---

