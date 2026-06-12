---
title: "&quot;The list of applications is not available&quot;"
date: 2008-01-31
forum: Multimedia &amp; Video
---

### Post by vestudio on 2008-01-31
I'm trying to install GStreamer for Totem. after clicking "Confirm" I get "List of applications not available". I click "Refresh" and I'm back to where I started. Over and over. It won't install it.

What's up?

Mike

---

### Post by taurus on 2008-01-31
Sounds like you either don't have any repos available in /etc/apt/sources.list or have a limited numbers of repos.  Therefore, go into System -> Administration -> Synaptic Package Manager -> Settings -> Repositories and make sure there is a check mark for all the lines except the last one, Source code, and the Cdrom in the bottom window.  Close it and press Refresh.  Now, see if you can install anything this time.

---

### Post by someguyonthestreet on 2008-02-05
I got the same thing, and it was easily rectified, just wondering if 7.10 does this on all computers.

---

### Post by FloiT on 2008-02-07
Thank you very much, mr. Taurus! I've been trying to solve that for weeks, and it's so easy when somebody helps you...

Regards from Spain (Catalonia!)
have a nice day, week and year

---

### Post by erfahren on 2008-02-07
> **someguyonthestreet said:**
> I got the same thing, and it was easily rectified, just wondering if 7.10 does this on all computers.
when there is no internet connection available when installing Gutsy it comments out the repos in the /etc/apt/sources.list

that's a new thing - it didn't happen in Feisty and seems to cause much confusion

---

### Post by TheWizzard on 2008-03-01
> **erfahren said:**
> when there is no internet connection available when installing Gutsy it comments out the repos in the /etc/apt/sources.list

that's a new thing - it didn't happen in Feisty and seems to cause much confusion

it's not a new thing. this did also happen in dapper and since then i have my computer hard-wired to the internet during install.

---

