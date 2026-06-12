---
title: "How do reassign a conflicting device driver"
date: 2010-05-25
forum: Mythbuntu
---

### Post by petatkinson on 2010-05-25
I don't know a lot about Linux but hell I'm learning the hard way.In a  related post  I  explained that I  was having trouble setting up  a Hauppauge  Nova DVB-S2 card.Tried all the suggestions but nothing worked.As a last shot I restarted the system and surprise Kaffeine worked.As  soon as I  ran Myth config the device went down again.Luckily  I ran lsmod and dmesg while Kaffeine was working and it looks like cx88 and 26114 are sharing the same IRQ port 1 when the device is down as when it was working 26114 was assigned  to port 6.How can I permanently  assign 26114 to port without Myth overwriting this instruction,

---

