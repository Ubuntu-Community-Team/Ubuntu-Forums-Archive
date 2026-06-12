---
title: "IRSSI Beep on messages"
date: 2010-12-07
forum: Networking &amp; Wireless
---

### Post by P-Geist on 2010-12-07
Hey,

Could you please tell me how to make irssi beep through the speakers whenever i get a message on IRC? This would be really apreciatted :)

I have tried the set beep thing on but doesnt work.

P-Geist

---

### Post by andrew.46 on 2010-12-08
Hi,

Perhaps try this:

[http://ubuntuforums.org/showpost.php?p=8720989&postcount=4](http://ubuntuforums.org/showpost.php?p=8720989&postcount=4)

Andrew

---

### Post by P-Geist on 2010-12-08
/set beep_cmd play -q ~/.irssi/scripts/ding_dong.wav

The above command returned: Irssi: Unknown setting beep_cmd

---

### Post by andrew.46 on 2010-12-09
Hi PGeist,

Do you get an error running this command:

```
/script load beep_beep.pl
```

Andrew

---

### Post by P-Geist on 2010-12-13
No because that command isnt in there. I was following your TUT completely.

---

