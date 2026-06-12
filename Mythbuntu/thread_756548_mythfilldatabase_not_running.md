---
title: "mythfilldatabase not running"
date: 2008-04-15
forum: Mythbuntu
---

### Post by tube013 on 2008-04-15
I have a myth setup that I recently updated to mythbuntu 8.04 beta, and since the update my backend (dedicated backend machine) isn't running mythfilldatabase automagically...  it never used to be an issue.  

I ran the default install (custom partition/drive setup) and then just cleared the new db and imported my saved db from my last install.. my old backend that died.

I noticed the other day I only had 3 days of listings left..   how do I set this up so that it pays attention to the suggested times from schedulesdirect?

---

### Post by tgm4883 on 2008-04-16
I believe under general settings in the frontend you can set up mythfilldatabase to run daily

---

### Post by tube013 on 2008-04-16
> **tgm4883 said:**
> I believe under general settings in the frontend you can set up mythfilldatabase to run daily

I actually tried that, even though I don't run a frontend on that machine (I have frontend installed just for testing).  I don't know if that matters.. but it def. isn't running automatically.

---

### Post by tgm4883 on 2008-04-16
Any errors in the backend log?

---

### Post by tube013 on 2008-04-16
I had to go back a few logs, but I found it.. should of looked harder.. seems the database had /usr/local/bin/mythfilldatabase not /usr/bin/mythfilldatabase

I made the change, so that should fix things.

---

