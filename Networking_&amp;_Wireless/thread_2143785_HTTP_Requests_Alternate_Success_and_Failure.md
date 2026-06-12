---
title: "HTTP Requests Alternate Success and Failure"
date: 2013-05-10
forum: Networking &amp; Wireless
---

### Post by MithrilHawk on 2013-05-10
I am attempting to download information from the public API for the RuneScape Grand Exchange, and some of my packets seem to get lost or ignored. I have used wget to download a particular page multiple times in succession and I have found that wget is successful twice, then times out after 120s twice, then is successful twice, etc. I don't understand why they come in pairs like that. This behavior also happens when I make requests to the Grand Exchange in Node.js and Python as well, and even adding ?rand=1234 and other random numbers at the end of the URL doesn't appear to have any effect.

Disabling the firewall on my router didn't help. I took my laptop to a coffee shop to try another Internet source and still had the problem. I used a separate laptop booted with a fresh install of Ubuntu and it still stalled every 2 requests. Then I SSHed into a lab computer and it had no problem downloading the same page more than twice in succession.

I'm wondering what could be causing these hangs from these two laptops, and with two different Internet sources, but not from a lab computer. Any help would be appreciated.

---

