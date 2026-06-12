---
title: "After years, still a very frustrating experience with wireless."
date: 2010-07-20
forum: Networking &amp; Wireless
---

### Post by lumix on 2010-07-20
I sincerely don't mean to insult, deride or otherwise denigrate any of the contributors to the Ubuntu experience, but, why *is* the wireless still so bad?  No, really.  I don't mean "bad" in the sense that someone's philosophy, or strategy, or choice of colors is bad, I mean that wireless is working *badly*.  Maybe it's working great for others, and for years I've assumed it's just me...but it kind of categorically isn't.  Four laptops and two desktops later I'm still embarrassed at work (as an IT professional) on a bi-weekly basis when I have to grin uncomfortably and ask that everyone wait while my laptop connects...which it often doesn't.  I've been using Ubuntu's out-of-the-box wireless (network manager?) since 7.something, and often tried gutting it and using iwconfig manually.

At the moment, I'm tethered to the wall, in spite of the fact that I'm less than 12 ft from the same wireless AP that I and the others here have been using for months.  One moment it works; but if I dare to disable my wireless interface (for testing or god knows what other reason) I'm really asking for it.  This happened this morning and now there's no going back...until tomorrow.  And that's how it happens.  By the magic of simply waiting, or rebooting enough times or coinciding with the equinox it will work again.

With iwconfig I can specify every detail right down to the AP's MAC address and frequency, but several times out of...I don't know...a few more than that it just won't connect.

Can someone enlighten me (without pointing me to another operating system, a doctor they know, a new profession, etc.)?

---

### Post by varunendra on 2010-07-21
I really feel sorry about your problem but at the same time, can't help laughing given the way you described it.
I have almost no experience of using Wifi in Ubuntu, but the same problem ocurred a lot in Windows (XP,Vista, 7) laptops also when they tried to connect after long intervals (typically, at the first time of the day). Those were laptops of students where I used to work & usually took too long to connect (sometimes hours!) even when there were plenty of empty leases on DHCP and the wifi signals were perfect.

One guaranteed solution was to assign the IPs manually. That is, whenever I assigned an IP address manually to a laptop, it used to connect instantly thereafter, even at low signal areas!

Have you tried the same with NetworkManager? (Assigning a permanent address manually). I'm assuming that you, being an IT professional, would have already had taken care of domain name/IP conflicts, etc.

---

### Post by chandra on 2010-07-21
You might want to```
sudo apt-get install wicd
``` and see if wicd fits your bill.

---

### Post by snowpine on 2010-07-21
As an IT professional, can you figure out the one very important detail you omitted from your post, that would elevate it from a "rant" to a "support request"? :)

---

### Post by dca on 2010-07-21
sudo lshw -C network

---

### Post by lumix on 2010-07-21
> **snowpine said:**
> As an IT professional, can you figure out the one very important detail you omitted from your post, that would elevate it from a "rant" to a "support request"? :)

No...it was rant. 

Going down?:)

---

### Post by lumix on 2010-07-21
> **varunendra said:**
> I really feel sorry about your problem but at the same time, can't help laughing given the way you described it.
I have almost no experience of using Wifi in Ubuntu, but the same problem ocurred a lot in Windows (XP,Vista, 7) laptops also when they tried to connect after long intervals (typically, at the first time of the day). Those were laptops of students where I used to work & usually took too long to connect (sometimes hours!) even when there were plenty of empty leases on DHCP and the wifi signals were perfect.

One guaranteed solution was to assign the IPs manually. That is, whenever I assigned an IP address manually to a laptop, it used to connect instantly thereafter, even at low signal areas!

Have you tried the same with NetworkManager? (Assigning a permanent address manually). I'm assuming that you, being an IT professional, would have already had taken care of domain name/IP conflicts, etc.

Well, if I've made just *one* person laugh, then...it's was a huge waste of time.

But your experience is interesting.  I've actually had excellent experiences with windows wireless config (as long as I didn't use any bloatware from the wifi mfr.).  I must say I have not used static ip in this context, but I can't even get associated, much less get dhcp working.

And hey, major kudos to the Ubuntu community for not entering into a force-5 tornado of nerdastic "oh no you di'nt" on this quasi rant, like some communities that (don't) answer *linuxquestions*.

---

### Post by cariboo on 2010-07-22
I was having the same sort of problem, as you describe, I have two access points, one encrypted, and the other open. If I set both connections to auto connect, my netbook always connects to the encrypted access point, even though In my shop, I'm less than 10 ft away from the open access point. By removing the auto connect option, All I do is choose the access point I'm closest to, and have zero problems connecting. 

Another benefit, is that when I'm out and about the netbook doesn't try to connect to an access point that is several kilometers away.

---

### Post by bigboy_pdb on 2010-07-22
lumix,

If this is a help request, can you please post the output of the command that dca requested? You will need to open a terminal to get it (Applications -> Accessories -> Terminal).

```

sudo lshw -C network

```

This will allow us to see what chip set is being used in your motherboard or on your networking card. If you're using a USB device to connect to the internet you'd want to use the following command:

```

lsusb

```

---

