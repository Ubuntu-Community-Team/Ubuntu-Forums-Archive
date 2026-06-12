---
title: "Wireless slow and spotty in new home"
date: 2012-05-30
forum: Networking &amp; Wireless
---

### Post by solutionorppt on 2012-05-30
Hey all,

     I am dealing with an older (2008) HP desktop that I gave to my mom a year or two ago.  It runs 10.04 just fine (dual boot with Vista).

I just helped her move down to Florida from NJ after her retirement.  A week ago, everything was fine with connectivity; the Comcast modem/router got set up down here in FL and all of a sudden the wireless won't work properly.

It connects and drops seemingly randomly and even when connected to the wireless it has trouble loading pages.

The irony is that I just booted Vista for the first time in ages to post this and the connectivity seems to be fine (4.2 Mb/s down, 3.21 up).  I can't even think of a Terminal output to post.

Lil' help anyone?

---

### Post by solutionorppt on 2012-05-30
Just realized I forgot to mention this -

I had the original user profile on the machine.  I set up a separate admin account after I transferred all my old files off of mine and then deleted my original profile.

Could this have been a factor?

I really would like to avoid a fresh install but will if I have to.

---

### Post by carl4926 on 2012-05-30
One thing you could try is create a new user, just for testing purposes. Login and see if you can get wireless working.

---

### Post by solutionorppt on 2012-05-31
Tried creating a new user, but no change.

I'll check back in the morning (EDT) before I just reinstall... probably due for it anyway.

---

### Post by carl4926 on 2012-05-31
> **solutionorppt said:**
> Tried creating a new user, but no change.

I'll check back in the morning (EDT) before I just reinstall... probably due for it anyway.
You shouldn't really need to re-install
But if wireless normally works from a live cd for you, why not fire it up and see if it does.

---

### Post by mattsvensson on 2012-07-13
I had connectivity issues as well and was able to finally narrow it down (with help from other forums) to adding the below entries to the below two files. Looks like Ubuntu was trying to resolve the DNS servers and having DNS resolution issues doing so (ironic, no?).

Entries to add - these are Comcast DNS servers:
nameserver 75.75.75.75
nameserver 75.75.76.76

Files to add it to:
/etc/resolv.conf
/etc/resolvconf/resolv.conf.d/head

Before there was just:
nameserver 127.0.0.1
search hsd1.ga.comcast.net

---

### Post by mike acker on 2012-07-14
my first thought is RF field strength?  is it marginal?  you might be getting too much error-correction and/or time-outs.  if so they have range-booster things for WiFi nets

Ubuntu has a beautiful performance monitor (search: monitor).  any hints there? My U-box is RJ-45 connected so I don't get a wireless signal strength indicator on it

---

### Post by Kirk Schnable on 2012-07-15
> **mike acker said:**
> my first thought is RF field strength?  is it marginal?  you might be getting too much error-correction and/or time-outs.  if so they have range-booster things for WiFi nets

Ubuntu has a beautiful performance monitor (search: monitor).  any hints there? My U-box is RJ-45 connected so I don't get a wireless signal strength indicator on it

If you run:
```
iwconfig
```

You will get an actual reading of signal strength and link quality.  

Kirk

---

