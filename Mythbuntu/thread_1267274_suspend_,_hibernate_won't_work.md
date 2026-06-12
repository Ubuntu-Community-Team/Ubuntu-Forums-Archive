---
title: "suspend , hibernate won't work"
date: 2009-09-15
forum: Mythbuntu
---

### Post by Mapping on 2009-09-15
HI

How i can solve, why suspend or hibernate won't work.
When i choose hibernate or suspend, x goes down and only cursor blinks upper left corner.

I have tested bios settings , choices are S3 or S1 or auto. Same problem no matter which is selected.

---

### Post by AKADAP on 2009-09-15
What is your intent with suspend/hibernate? Depending on your purpose, you may not need them.

If the system is a back end, and you want it to shut down when idle, and wake to record, you do not need suspend/hibernate working as myth does not use those modes. Instead it shuts the system down using the RTC to turn the system on at the appropriate time.

---

