---
title: "Hauppauge nova T 500 remote Escape dont work"
date: 2009-02-25
forum: Mythbuntu
---

### Post by johnvv on 2009-02-25
Coming from Mythtv 0.19 under Slackware (no change to hardware), Mythbuntu(Intrepid) works well except key Escape on the remote (the grey one).
Escape works well on the keyboard, but on the remote sends the Ubuntu Quit panel ... Is there somewhere inside Ubuntu  a hidden demon waiting the remote Escape code ?

Thanks

---

### Post by scary_jeff on 2009-02-25
Are you sure the button is bound to Esc and not ALT+F4? Check ~/.lircrc

---

### Post by johnvv on 2009-02-25
The keys  "Go" (0x0161) and "Back/Exit" (0x00AE)are bound to Escape. The key "Go" results in a Quit and this is not Quit from Mythtv, but Quit from Ubuntu (as Quit in the Ubuntu menu). This Quit is sent several times (I have to cancel 3 time to exit this panel). "Back/Exit" results in nothing at all.

Thanks for answer.

---

