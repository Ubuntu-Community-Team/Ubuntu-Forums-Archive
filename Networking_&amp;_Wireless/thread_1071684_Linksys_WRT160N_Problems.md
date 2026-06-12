---
title: "Linksys WRT160N Problems"
date: 2009-02-16
forum: Networking &amp; Wireless
---

### Post by PrinceArithon on 2009-02-16
OK my last wireless router died on me yesterday so today I got a new one it's the Linksys WRT160N.  It seems to work well with Windows Vista...but the laptops with XP and Ubuntu have some problems.

My XP laptop falls off the network every so often and needs to re-authenticate.  But the big problem is the Ubuntu one of course.

What happens is, it is really slow.  It stays on the network but it's just horribly slow.  Like sometimes it will take 30 seconds for a page to load, and other times 5 minutes.

Now here is how I've configured it.

First I did the WPA and WPA2 configurations and it was slow, then I tried WEP, and it still didn't work, so I tried turning off the security but only letting people be able to use the router if their MAC address was on it, and it still did the same thing.

I've tried broadcasting and hiding the SSID and it's all not worked.  I even called Linksys and worked with the tech support which wasn't too bad.  It still didn't work.

Now they said maybe I should call HP and find out if there is something up with the wireless card that could be causing the problem.

Anyway just for a fast run down of what I'm using.  It's an HP Pavilion dv5 Laptop, and as I said before it's a Linksys WRT160N router.  The operating system is the current 32 bit Ubuntu operating system.

So if anyway can help me I'd appreciate it.

---

### Post by PrinceArithon on 2009-02-17
I hope no one minds but I'm going to bump this in hopes for an answer.

---

### Post by dBLiSS on 2009-07-01
Has anyone solved this issue?

---

### Post by chinarut on 2009-08-19
another bump from me - got this issue too.

no problems connecting over WPA with my Fonera which I'm looking to replace....

---

### Post by chinarut on 2009-08-25
ok - i can't conclusively say how I got it all working but following this thread helped:

[How To: Manual Network Configuration without the need for Network Manager]("http://ubuntuforums.org/showthread.php?t=571188")

what helped the most was taking it one step at a time and verifying that an unsecured connection worked, then WPA, then WPA2

something I also want to note is I don't think I am using wpasupplicant (even though I installed it) - I'm back to using wicd.

I think the real issue was disabling broadcasting my SSID - when I broadcasted it again, things seem to behave more predictably and have all my clients on the  network again! :)

---

### Post by bjordan555 on 2013-04-18
Replying to a 4 year old thread seems a bit pointless, but...

I confirm that I had the same problems with my Ubuntu 12.04 running on Macbook Pro and connecting to a Linksys WRT160N router with firmware revision 3. I tried the single fix suggested by the above post, i.e. disable, save, and re-enable and save the broadcast SSID setting in the router admin web page. This fixed my problem and I am happily connected now. Good thing internet connectivity is still as slow as it was in 2009, and I haven't had to replace my router.

---

### Post by wildmanne39 on 2013-04-18
Thread closed. Please do not post in old threads.

---

