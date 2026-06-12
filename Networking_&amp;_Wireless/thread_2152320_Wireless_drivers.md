---
title: "Wireless drivers?"
date: 2013-06-07
forum: Networking &amp; Wireless
---

### Post by ArminasAnarchy on 2013-06-07
Hi all!

I'm trying to get a wireless USB adapter working. The output of "lsusb" is as follows:

```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 050d:1102 Belkin Components F7D1102 N150/Surf Micro Wireless Adapter v1000 [Realtek RTL8188CE-VAU]
Bus 002 Device 002: ID 0c45:7428 Microdia
```

I googled the Realtek model number, and downloaded a zip file from their website. The readme inside that file states:

========================================================================================
        II. Compile & Installation
========================================================================================
You can enter top-level directory of driver and execute follwing command to
Compile, Installation, or uninstall the driver:

    1. Change to Super User
       sudo su

    2. Compile driver from the source code 
       make

    3. Install the driver to the kernel
       make install
       reboot

...I did this. Prior to rebooting, the adapter picked up and connected to the WLAN fine. After rebooting, the system doesn't seem to realise it's there at all (i.e. there is no option to "connect to wireless network" through the Network Manager applet). I thought it might be a case of the drivers not picking up the hardware, so issued modprobe -l. Output clearly states that the kernel at least recognises it though, these are the last two lines of output:
```

kernel/drivers/net/wireless/rtlwifi/rtl8188ee/rtl8188ee.ko
kernel/drivers/net/wireless/rtlwifi/rtl8723e/rtl8723e.ko
```

Not really sure how to procede at all tbh - help would be very much appreciated!

---

### Post by ArminasAnarchy on 2013-06-07
Reposting from the Networking forum, after an hour of no replies. Plus, my experience with wireless drivers is small, so I more or less fit the "Absolute Beginner" specification!

Hi all!

I'm trying to get a wireless USB adapter working. The output of "lsusb" is as follows:

 	Code:
 	
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 001 Device 002: ID 050d:1102 Belkin Components F7D1102 N150/Surf Micro Wireless Adapter v1000 [Realtek RTL8188CE-VAU] Bus 002 Device 002: ID 0c45:7428 Microdia 
I googled the Realtek model number, and downloaded a zip file from their website. The readme inside that file states:

==================================================  ======================================
        II. Compile & Installation
==================================================  ======================================
You can enter top-level directory of driver and execute follwing command to
Compile, Installation, or uninstall the driver:

    1. Change to Super User
       sudo su

    2. Compile driver from the source code 
       make

    3. Install the driver to the kernel
       make install
       reboot

...I did this. Prior to rebooting, the adapter picked up and connected  to the WLAN fine. After rebooting, the system doesn't seem to realise  it's there at all (i.e. there is no option to "connect to wireless  network" through the Network Manager applet). I thought it might be a  case of the drivers not picking up the hardware, so issued modprobe -l.  Output clearly states that the kernel at least recognises it though,  these are the last two lines of output:
 	Code:
 	
kernel/drivers/net/wireless/rtlwifi/rtl8188ee/rtl8188ee.ko kernel/drivers/net/wireless/rtlwifi/rtl8723e/rtl8723e.ko 
Not really sure how to procede at all tbh - help would be very much appreciated!

---

### Post by Rob Sayer on 2013-06-07
You started a thread in another section because you didn't get an answer in an *hour*?  For free support?

And started doing things you don't understand because you couldn't wait?

The tech support here is excellent.  Better than most you'd pay for.  But if you want instantaneous response install red hat and pay for the service contract.

In the meantime, post what you have put here in your original thread and wait until you have a response from someone who actually knows what they're doing before you start playing around with things you don't understand ... linux drivers are *not* simply loaded like in windows ... and possibly messing things up more.

---

### Post by Mark Phelps on 2013-06-07
The rule of thumb around here is NOT to bump a post any more frequently than once every 24 hours -- certainly not once EVERY hour!

This is an all-volunteer forum with contributors from around the world -- read that as 24 time zones.

If you're going to repost every hour you don't get a response, you're asking the Mods to kick you off the forum.

You need to show more patience -- we're not all sitting here waiting for you to post.

---

### Post by Elfy on 2013-06-07
Thread closed. Please do not post duplicates, it dilutes community effort.

---

### Post by matt_symes on 2013-06-07
Thread moved to **Networking and Wireless**.

---

### Post by matt_symes on 2013-06-07
.. **and threads merged**.

Now you have both threads closed. 

That is the havock that opening multiple threads can cause. 

Elfy closed your other thread while i was merging them together.

As they have been merged, i'll reopen this it.

So please don't create multiple threads on the same subject.

Anyway, have patience ;)

---

### Post by ArminasAnarchy on 2013-06-07
> **Rob Sayer said:**
> You started a thread in another section because you didn't get an answer in an *hour*?  For free support?

5And started doing things you don't understand because you couldn't wait?

The tech support here is excellent.  Better than most you'd pay for.  But if you want instantaneous response install red hat and pay for the service contract.

In the meantime, post what you have put here in your original thread and wait until you have a response from someone who actually knows what they're doing before you start playing around with things you don't understand ... linux drivers are *not* simply loaded like in windows ... and possibly messing things up more.

You raise a few points, and your reply is by far the most obnoxious, so I'm going to reply to it first.
The issue with the open source is that there is an implicit assumption amongst some that free (gratis AND libre) mandates inferiority somehow. Let's remember that Ubuntu isn't free out of the kindness of Cannonical, but out of the fact that if they want to get anyone at all onside, and if they don't want to create a incredibly expensive development department, they have to use source code which is freely available - and once it's freely available (i.e. libre) no one will be willing to pay for it (i.e. gratis status is a direct consequence of libre development). This applies both to the end product (I expect my distro to be as bug free, if not MORE bug free, than like for like proprietrary software), but also support in using it (solving queries, bug reporting infrastructures, package/repo management etc). If lots of users are signed up to the ethos of the distro, and there's a community behind it, as there is with Ubuntu - there's no reason that this can't be done on a purely volunteer basis; but in any event Ubuntu has a comercial backer. If we users don't initially accept (and demand) high quality, and a good (better?) experience, then why make the jump from preinstalled Windows? How do we DARE encourage friends and family to use Linux - if the end product isn't going to be better? I've come across your view a few times, and Idk if you actively hold it, or if it's just some vestigal preconcept, but it's dangerously insideous in any case. You do acknowledge the tech support is excellent here - something I'm glad you pointed out - but it seems at odds with the implicit assumptions stated before and after it: "You get what you pay for". Linux can't fight a battle on that ground (obviously), and it's the responsibility of the community to refute this argument in all its forms IMHO; certainly NOT to propagate.

Second thing to note: in my experience thus far, threads have been replied to really quickly. An hour with only ~10 or so views was unheard of in my experience (albeit limited) of the forum - and wondered "Hm, maybe I'm aiming to closely. The "Absolute Beginner" forum is generally a lot more active, and removing the [xubuntu] tag was the main reason for reposting - rather than just BUMPing this thread, or trying another site entirely (Kubuntu has it's own set, for instance). The sign of madness is doing the same thing over and over and expecting a different result, and I like to think of myself as not completely mad ;). Hence, repost. It's reasonable to assume that all my experiences up until now have been entirely typical, no? And if they are typical, the logical consequence of that is that they would be repeated.

The final line is both disgustingly patronising and completely wrong in its direction. The beauty of open source is that you can try things, and experiment, and find what suits you. So, knowing that "modprobe" probes kernel modules, and knowing that the "-l" argument gives a list output, it's sensible to put two and two together and see if the kernel was even picking up the USB card, since the GUI was implying otherwise. The kernel WAS picking up the card, so it's just a case of telling the rest of the system that it's there - something Idk how to do, and my reason for posting. Not using "sudo", either, the scope for damage is rather limited. Just what exactly have I "messed" with there? And even if I had ****ed something up - who the hell are you to dictate to me what to do with my software, in my home, on my machine? I'll mess with whatever I fancy, without seeking recourse from you, ta very much!

I note despite your condescending tone and vainity, you fail to provide a fix? Perhaps that is more telling and insightful than anything I can write here :P.

I have to say, I'm itching to post profanities directed heavily your way, in a tit-for-tat fashion. Strongly worded, though not too hot headed, is the tone I'm going for here, hopefully you'll learn by example; the example being insulting someone's intelligence is neither warranted nor welcome. Or at least you're not he only one who can play the "patronising prig" role to perfection ;).

On with the show, anyway...

> **Mark Phelps said:**
> The rule of thumb around here is NOT to bump a post any more frequently than once every 24 hours -- certainly not once EVERY hour!

This is an all-volunteer forum with contributors from around the world -- read that as 24 time zones.

If you're going to repost every hour you don't get a response, you're asking the Mods to kick you off the forum.

You need to show more patience -- we're not all sitting here waiting for you to post.

Thanks for the advice - I'll be careful to apply that rule in future. As stated, however, it's mismatched with my previous experiences, which even with relatively complex things have been much faster.

> **Elfy said:**
> Thread closed. Please do not post duplicates, it dilutes community effort.

I'm not entirely sure that that logic follows - Kubuntu has it's own site, but can also post here? Regardless of reason or rationale behind it, however, I'm happy to follow the rules as given - apologies for reposting. Hopefully you can see the reason I thought it necessary from above however - not being able to change the [xubuntu] tag in the headline, and possibly choosing one of the quieter forums mistakenly.

> **matt_symes said:**
> Thread moved to **Networking and Wireless**.

> **matt_symes said:**
> .. **and threads merged**.

Now you have both threads closed. 

That is the havock that opening multiple threads can cause. 

Elfy closed your other thread while i was merging them together.

As they have been merged, i'll reopen this it.

So please don't create multiple threads on the same subject.

Anyway, have patience ;)

As stated, point taken, and as stated, you're seen my reasoning/explanation above. Apologies none the less. Cheers for reopening the thread, and thanks for the advice. I (possibly) have a favour to ask too: can you move it into the AB forum and/or replace the [xubuntu] tagline with [all variants] to try and boost the viewing figures? Or, better still, can you close this thread, and/or de-merge them? Can't help but feeling this one has gotten somewhat off topic...

---

