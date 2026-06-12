---
title: "Intel Ultimate-N (iwlwifi) users?"
date: 2013-01-18
forum: Networking &amp; Wireless
---

### Post by Ranko Kohime on 2013-01-18
I'm asking for some feedback from people using the Intel Ultimate-N 6300 wifi card, which uses the iwlwifi kernel module.  My experience with this module has been, less than pleasant.

In 2011, I built a laptop with this wireless card, and though I did not know it at the time, it was causing random kernel lockups.  (The laptop also had Nvidia Optimus graphics, which I had attributed to the lockups).  This was with Ubuntu 11.04, shortly after it came out, not sure what version of iwlwifi it had.

Now, I'm running the same wifi card in a different laptop, on Fedora 17 presently.  I'm experiencing the same random lockups as before.

I didn't find the grass greener with Fedora, so I'm migrating back to Ubuntu shortly, and I'd like to hear from people running the aforementioned card: has there been any improvement in the driver as of 12.10?  How about in 13.04 testing?

---

### Post by praseodym on 2013-01-18
There is (still) a bug with the N-mode of the driver. Deactivate it via:
```

echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```

---

### Post by ahallubuntu on 2013-01-18
I'm using the Intel 5100 card with this same driver (in several laptops), and it has worked beautifully since 10.04.  I've just installed two Dell laptops that have a 5100 with 12.04 and they have also worked perfectly.  Solid connections, fast data rates.  I have never had to disable 802.11n either.  I get great sustained file transfer rates over my local network with 802.11n.

Where did you get this card and what kind of laptop are you using it in?  Is this laptop designed to work with this card?

I bought a couple of Intel cards via eBay from vendors in China and Hong Kong and have had bad luck with them.  Some of them were mismarked and did not match what I ordered; some did not work at all.  (I have since stopped buying them that way.)  I have had great luck buying used cards on eBay within the US, however.

---

### Post by Nr90 on 2013-01-18
sorry, double post

---

### Post by Nr90 on 2013-01-18
I had a laptop with that same wireless card.
Wireless N was always a pain. 

I gave up and bought a new laptop ;)

---

### Post by fyfe54 on 2013-01-18
I have the N6200 card (iwlwifi driver) and it was a pain until I disabled the wireless.N.

---

### Post by chili555 on 2013-01-18
My 6200 works perfectly. I have no N router so I can't speak to N.

---

### Post by Ranko Kohime on 2013-01-18
> **ahallubuntu said:**
> Where did you get this card and what kind of laptop are you using it in?  Is this laptop designed to work with this card?
Newegg, and Lenovo E420, and this specific, individual card, no.  While Lenovo hawks their own version of this same card, (which the whitelist is setup to accept) I did not go that route, because I was unaware I had to, and ended up having to do a firmware upgrade to fix that issue.  :p

---

### Post by Ranko Kohime on 2013-01-18
> **praseodym said:**
> There is (still) a bug with the N-mode of the driver. Deactivate it via:
```

echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```
I will try this next time I test the driver.

---

### Post by ahallubuntu on 2013-01-18
> **Ranko Kohime said:**
> Newegg, and Lenovo E420, and this specific, individual card, no.  While Lenovo hawks their own version of this same card, (which the whitelist is setup to accept) I did not go that route, because I was unaware I had to, and ended up having to do a firmware upgrade to fix that issue.  :p

Yeah, I was wondering about how you were able to POST.  I wonder if the firmware wasn't exactly the same for this card as the generic 6200?  Could be a Lenovo/HP flavor 6300 would work fine.

---

### Post by Ranko Kohime on 2013-01-19
> **ahallubuntu said:**
> Yeah, I was wondering about how you were able to POST.  I wonder if the firmware wasn't exactly the same for this card as the generic 6200?  Could be a Lenovo/HP flavor 6300 would work fine.
I would tend to doubt it, since the exact same card in another laptop, which had no whitelist, had the exact same problem.  :neutral:

---

### Post by Ranko Kohime on 2013-02-04
I went ahead and marked this as solved, as I've been running for about two weeks now without any hangs, (at least, the kernel kind.  GUI is another story)

---

