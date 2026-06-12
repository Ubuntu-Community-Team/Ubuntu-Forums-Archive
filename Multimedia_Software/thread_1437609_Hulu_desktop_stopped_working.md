---
title: "Hulu desktop stopped working?"
date: 2010-03-24
forum: Multimedia Software
---

### Post by bedhead75 on 2010-03-24
I'm wondering if anyone is having a similar problem as mine when running Hulu Desktop.  The application starts fine, but when I try to select anything to watch, the green progress bar continually resets over and over again as it tries to buffer a video, and playback never starts as a result. This happens for low, medium, and high quality.  Hulu Desktop was working perfectly fine a few months ago.  I've always been running Ubuntu 9.10 (64-bit) with the latest 64-bit Flash pluggins, and didn't have a problem before.  Running Hulu Desktop from the command line doesn't reveal any error messages either.

---

### Post by Chronon on 2010-03-24
I had some problems streaming yesterday, but not today.  Do you still have trouble?  It might have been a problem on their end.

---

### Post by Talys on 2010-03-31
I'm having this problem as well.  Did you ever manage to fix it?

---

### Post by JohnnyVW on 2010-03-31
I went to run Hulu Desktop...  and it doesn't even start.  Any ideas?  I tried uninstalling/reinstalling, but it didn't work.

---

### Post by dredknot420 on 2010-06-15
> **bedhead75 said:**
> I'm wondering if anyone is having a similar problem as mine when running Hulu Desktop.  The application starts fine, but when I try to select anything to watch, the green progress bar continually resets over and over again as it tries to buffer a video, and playback never starts as a result. This happens for low, medium, and high quality.  Hulu Desktop was working perfectly fine a few months ago.  I've always been running Ubuntu 9.10 (64-bit) with the latest 64-bit Flash pluggins, and didn't have a problem before.  Running Hulu Desktop from the command line doesn't reveal any error messages either.

I was having this exact same issue. I seemed to have fixed it though. Please provide feedback if this doesn't work for anyone.

-Right click anywhere in Hulu Desktop and select flash settings.
-Select the storage tab and slide the bar over to unlimited.

I believe its an issue with the buffer cache not dumping properly. I have posted this on the Hulu site, so hopefully it will be fixed in the next update.

Edit: Something new I discovered as well. If I scale up my processor to Performance mode it breaks this fix. As long as I switch it back and leave it as On Demand, then this fix continues to work perfectly so far.

---

### Post by bedhead75 on 2010-06-17
I tried this and it doesn't fix it for me.  Hulu still fails to buffer properly.  I didn't change my processor scaling though.  Where and how do I toggle it between on demand and performance?

---

### Post by dardack on 2010-07-25
Did anyone else get huludesktop to start working again on 64bit?  It doesn't even work with sudo huludesktop.  I did try the storage unlimited, didn't fix it.

---

### Post by dardack on 2010-07-25
Sigh and now it's not working on my 32bit mythtv frontend.  Sigh.

---

