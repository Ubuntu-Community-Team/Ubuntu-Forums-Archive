---
title: "Dual Monitor problems"
date: 2006-05-28
forum: Multimedia &amp; Video
---

### Post by bean1975 on 2006-05-28
I attached my xorg.conf and logs when ran in dualhead and the current, when I remarked out the two lines that make it dualhead.

As you can see, currently the first device uses DFP-1. That's because if I try to use DFP-0 I get both monitor black. I am afraid that one of the DVI connectors on board is dead. Is this feasible from what you read here? Is something utterly wrong with my xorg.conf?

---

### Post by chrestomanci on 2006-05-28
I see from your xorg.conf that you have an nVidia card (You should have put it in the post, as it is important).

nVidia have some good documention about how to setup their cards. If I where you I would go to their website & download the linux driver. There is a lenghtly readme that documents all the settings you can use.

If you are worried that one of your DVI connectors is bad, then check as your PC boots up. When it is in the BIOS screens there should be the same display on each output.

---

### Post by bean1975 on 2006-05-28
That's sad because on boot only the LCD plugged into the connector marked as "2nd LCD" works :(

---

