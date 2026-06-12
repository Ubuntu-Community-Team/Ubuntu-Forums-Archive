---
title: "Odd output?"
date: 2008-12-16
forum: Mythbuntu
---

### Post by whaase on 2008-12-16
I've been trying to run Mythbuntu using the vga port to my tv. I have a ATI 1650 gfx card. On the Ubuntu desktop everything looks perfect. I get the perfect resolution for my tv. But when mythtv fires up, it looks almost like 2 screens side by side and unreadable. If I exit and go back to my desktop, looks perfect again.

What's wrong? Where can I change/fix it?

If I uninstall the drivers for the ATI card, I don't get the best resolution, but both the desktop and myth look good. Problem is, videos won't run with no drivers installed lol.

Other then getting a nvidia card (I may just do that) where can I try fixing it?

Thanks, Walter

---

### Post by tgm4883 on 2008-12-16
> **whaase said:**
> I've been trying to run Mythbuntu using the vga port to my tv. I have a ATI 1650 gfx card. On the Ubuntu desktop everything looks perfect. I get the perfect resolution for my tv. But when mythtv fires up, it looks almost like 2 screens side by side and unreadable. If I exit and go back to my desktop, looks perfect again.

What's wrong? Where can I change/fix it?

If I uninstall the drivers for the ATI card, I don't get the best resolution, but both the desktop and myth look good. Problem is, videos won't run with no drivers installed lol.

Other then getting a nvidia card (I may just do that) where can I try fixing it?

Thanks, Walter

Try starting mythfrontend from the command line with this command

```
mythfrontend -geometry 800x600
```

Let me know if it looks right

---

