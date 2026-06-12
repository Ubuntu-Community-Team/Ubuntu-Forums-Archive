---
title: "No Sound in Feisty Fawn"
date: 2007-05-10
forum: Multimedia &amp; Video
---

### Post by ghostboy on 2007-05-10
I just installed Feisty on my Acer Aspire 5050.  I got the internet up and runnning and im happy about that.  Now, the question is how do i get sound to play on my laptop?  Can anyone point me in the right direction>?  Thanks in advance!

---

### Post by spin2cool on 2007-05-10
Start here:
[http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide)

---

### Post by Kobalt on 2007-05-10
Or try this : [https://help.ubuntu.com/community/DebuggingSoundProblems](https://help.ubuntu.com/community/DebuggingSoundProblems)

---

### Post by ghostboy on 2007-05-10
Ill check it out.  Thanks!!!!

---

### Post by EduMaxwell on 2007-05-15
I have an Acer Aspire 5051 and had a similar problem.  You may have already done this, but in ALSA mixer go to Edit > Preferences.  There you will find a number of unselected options, possibly including a "surround" option.  Using trial and error (by selecting certain volume controls and making sure they are NOT muted), you might find the solution to your problem without going into terminal mode.  After a lot of sweat and tears and reconfigurations, I finally solved my problem with this simple approach.  Try it and let me know if it works for you.

This is my description of a similar troubleshooting option found in this URL (pasted above by Kobalt)
[https://help.ubuntu.com/community/DebuggingSoundProblems](https://help.ubuntu.com/community/DebuggingSoundProblems)

---

### Post by ghostboy on 2007-05-15
> **EduMaxwell said:**
> I have an Acer Aspire 5051 and had a similar problem.  You may have already done this, but in ALSA mixer go to Edit > Preferences.  There you will find a number of unselected options, possibly including a "surround" option.  Using trial and error (by selecting certain volume controls and making sure they are NOT muted), you might find the solution to your problem without going into terminal mode.  After a lot of sweat and tears and reconfigurations, I finally solved my problem with this simple approach.  Try it and let me know if it works for you.

This is my description of a similar troubleshooting option found in this URL (pasted above by Kobalt)
[https://help.ubuntu.com/community/DebuggingSoundProblems](https://help.ubuntu.com/community/DebuggingSoundProblems)

That soltuion worked out great!  Thanks for the tip!

---

