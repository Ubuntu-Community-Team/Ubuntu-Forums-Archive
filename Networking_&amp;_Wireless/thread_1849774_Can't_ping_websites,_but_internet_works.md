---
title: "Can't ping websites, but internet works"
date: 2011-09-25
forum: Networking &amp; Wireless
---

### Post by tame_lx_tech on 2011-09-25
Hi all,

Basically, I'm on a university system and can access the internet (with firefox, elinks etc), yet I can't ping anything.

I am trying to create a router from an old box, but IP masquerading doesn't work, and I think this may be the reason why.

This isn't just a ubuntu problem, as the same thing happens under Win7 and Arch.

Thanks in advance.

---

### Post by haqking on 2011-09-25
> **tame_lx_tech said:**
> Hi all,

Basically, I'm on a university system and can access the internet (with firefox, elinks etc), yet I can't ping anything.

I am trying to create a router from an old box, but IP masquerading doesn't work, and I think this may be the reason why.

This isn't just a ubuntu problem, as the same thing happens under Win7 and Arch.

Thanks in advance.

I suspect that IP masquerading is not allowed on your University network and contravenes the Acceptable Use Policy and terms of Service.

Why do you need a router on that network if it is a University network and you have access to a router to get out the outside world ?

---

### Post by tame_lx_tech on 2011-09-25
I was going to use it as I only have one ethernet port in my room.
And They probably won't let me do IP masquerading, but That doesn't explain why i can't ping.
Thanks

---

### Post by haqking on 2011-09-25
> **tame_lx_tech said:**
> I was going to use it as I only have one ethernet port in my room.
And They probably won't let me do IP masquerading, but That doesn't explain why i can't ping.
Thanks

Perhaps you have a firewall or the University firewall prevents outbound ICMP.

---

### Post by tame_lx_tech on 2011-09-25
Right, I think I might go and ask about it.

Thanks for your help and speedy replies.

---

### Post by haqking on 2011-09-25
> **tame_lx_tech said:**
> Right, I think I might go and ask about it.

Thanks for your help and speedy replies.

No worries, always best to ask your sysadmin for network problems.

Good luck

peace

---

### Post by agillator on 2011-09-25
Unless I misunderstand your setup, why do you need a router? The school provides the router services. All you should need is a hub - much cheaper than a router.

---

