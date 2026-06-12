---
title: "devinput remote configuration"
date: 2013-01-01
forum: Mythbuntu
---

### Post by milhouse on 2013-01-01
After many happy years on 10.04/0.24 I recently upgraded the house to 12.04/0.26 (backend) and 12.10/0.26 on the frontends. Everything went fairly smoothly but this remote business is a mess.

I was unaware of the handling of remotes via devinput and for a couple of days struggled to get lirc working. I read many blog and forum posts and eventually gave up on lirc. With lirc removed, I was able to get the remote to mostly work but I did need to edit the appropriate keymap in /lib/udev/rc_keymaps following hints in [[COLOR="Sienna"]this[/COLOR]]("http://wyliecoyoteuk.wordpress.com/2012/01/30/how-to-forget-lirc-for-mythtv-remotes/") blog post.

So I'm close but the last nagging issue is that some buttons also trigger Unity/desktop actions. For example, the "Windows" button (I am using an MCE remote) opens up Rhythmbox even when within Mythtv.

How do I disable these other actions? I have been unable to figure out where the config file exists and how to disable these "features".

Any help/hints are appreciated.

---

### Post by nickrout on 2013-01-01
> **milhouse said:**
> After many happy years on 10.04/0.24 I recently upgraded the house to 12.04/0.26 (backend) and 12.10/0.26 on the frontends. Everything went fairly smoothly but this remote business is a mess.

I was unaware of the handling of remotes via devinput and for a couple of days struggled to get lirc working. I read many blog and forum posts and eventually gave up on lirc. With lirc removed, I was able to get the remote to mostly work but I did need to edit the appropriate keymap in /lib/udev/rc_keymaps following hints in [[COLOR="Sienna"]this[/COLOR]]("http://wyliecoyoteuk.wordpress.com/2012/01/30/how-to-forget-lirc-for-mythtv-remotes/") blog post.

So I'm close but the last nagging issue is that some buttons also trigger Unity/desktop actions. For example, the "Windows" button (I am using an MCE remote) opens up Rhythmbox even when within Mythtv.

How do I disable these other actions? I have been unable to figure out where the config file exists and how to disable these "features".

Any help/hints are appreciated.

Use mythbuntu-contol-centre.

---

### Post by milhouse on 2013-01-01
> Use mythbuntu-contol-centre.

Thanks for the response, though a bit more detail would be helpful. Are you suggesting that disabling the default actions of some of the MCE remote keys (like the aforementioned starting of Rhythmbox) can be accomplished via mythbuntu-control-center? If so, please elaborate since all I am able to achieve is disabling **all** keys of the remote if I enable lirc. In other words, the remote doesn't work. I've searched the forum, tried numerous configurations, but the best I can do is get raw output from /dev/lirc0 when lirc is installed. I never get output from, say irw.

My remote is naively supported in kernel 3.5.0 and I've mostly worked the devinput keymap out. I just want to disable Unity (or whatever is getting in the way) from, er, getting in the way.

---

### Post by milhouse on 2013-01-01
It just dawned on me to look at the keyboard configuration (System Settings->Hardware->Keyboard). There, under the shortcuts tab, was the solution to my problem. Under Sound and Video I simply disabled all of the shortcuts.

---

