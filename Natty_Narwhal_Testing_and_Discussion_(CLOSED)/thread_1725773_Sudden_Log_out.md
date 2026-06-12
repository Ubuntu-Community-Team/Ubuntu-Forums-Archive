---
title: "Sudden Log out"
date: 2011-04-10
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Steel-Bunz on 2011-04-10
I was browsing with Firefox (3 tabs open) and had just logged into Empathy. Then I suddenly got logged out and the login screen came up. I had to login again.

Any idea what actually had happened? Any system dump or log file I should refer to in order to understand what is going on? By the way, no error messages thrown up either.

Mystery!

---

### Post by mikewhatever on 2011-04-10
You could look at /var/log/Xorg.0.log, and I hope you like log files.:P

---

### Post by Steel-Bunz on 2011-04-10
Thanks Mike... Xorg log file is quite something... :)

It appears that Xorg.0.log.old file was created when the log out occurred. This is what I could find in the file,

[  1924.714] Segmentation fault at address 0xb9c90f8
[  1924.714] 
Caught signal 11 (Segmentation fault). Server aborting
[  1924.714]

Not sure if attaching the entire log file would help. Please let me know.

---

### Post by mikewhatever on 2011-04-10
A single logout on a testing release is no a big deal, but if the problem persists, you should consider filing a bug report.

---

