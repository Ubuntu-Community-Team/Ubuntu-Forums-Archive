---
title: "How do I figure out what wireless driver I'm using?"
date: 2009-02-25
forum: Networking &amp; Wireless
---

### Post by jimbren on 2009-02-25
I feel like this is a completely stupid question, but I've asked and answered my share of there over the years here, and one more isn't going to hurt anything, right?

I've got a Dell laptop that I use for work that has a Broadcom wireless card.  A few months ago my boss challenged me that I couldn't do everything in Linux as efficiently as I can do it in Windows, so I used Wubi and installed Ubuntu as a dual boot.  It turns out that I can do about 98% of what I need to do in Ubuntu just fine, if not better, than I can do it in XP, but the 2% that requires me to use Windows is a major pain in my ***.   I'm ready to do a fresh install of Ubuntu and just do a VM for Windows.  

My hesitation is that in getting the Wireless to work, I had to use some combination of three different howtos, with some creative despiration thrown in, to get the Broadcom up and running, and I can't take the three or four days this time that I had to take last time.  

I know I should be able to go to a command line and find the exact driver version I'm using, and avoid all the hoops I had to jump through before.  But, I have no idea how.  

Thoughts?

Thanks,

jimbo

---

### Post by x33a on 2009-02-25
try
```

lshw -C network
```

---

### Post by jimbren on 2009-02-25
Thanks very much!

---

