---
title: "Difficulty getting new net card to work"
date: 2010-02-23
forum: Networking &amp; Wireless
---

### Post by tidan on 2010-02-23
My onboard lan card was cutting out during samba file transfers so I put in a PCI lan card and disabled the integrated one.  
Now I'm having trouble getting it to work.   
I appologize in advance,  I'm completely ignorant as to how to change net cards in Ubuntu and am quite new to Linux in general.

I've searched and searched but cannot find any solutions.

I'd copy and paste my lspci,  but I can't connect to that computer nor the internet with it now.

Thanks for any help you can offer!

---

### Post by maxpathan on 2010-05-16
> **tidan said:**
> My onboard lan card was cutting out during samba file transfers so I put in a PCI lan card and disabled the integrated one.  
Now I'm having trouble getting it to work.   
I appologize in advance,  I'm completely ignorant as to how to change net cards in Ubuntu and am quite new to Linux in general.

I've searched and searched but cannot find any solutions.

I'd copy and paste my lspci,  but I can't connect to that computer nor the internet with it now.

Thanks for any help you can offer!

Did you manage to resolve this? I am having a similar problem.
On board lan is dead, installed a pci network card. I expected UBUNTU to pick it up, but it doesnt.

---

### Post by tidan on 2010-05-16
I was rather suprised to find that no one offered help on this.   But to answer your question,  yes I did finally resolve it.
As embarrassing as it sounds,  it was simply a matter of me accidentally pluggin the lan cable into the old port instead of the new one.   Once I realized I had plugged the cable back into the old port and moved it to the new one,  everything worked like a charm.

---

