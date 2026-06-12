---
title: "How can I automatically record from the mic input?"
date: 2007-03-05
forum: Multimedia &amp; Video
---

### Post by stealth17 on 2007-03-05
I have my stereo hooked up to the input line on my sound card. I want to automatically start record a radio show everyday from 9am-10pm. How can I do that?

Or better yet, I can get the same radio show on a live stream over the internet. Can I record it from a live stream?

---

### Post by Jussi Kukkonen on 2007-03-05
Use a command line recorder (like *arecord* from the package *alsa-utils*. arecord allows you to specify the length of the recording in secs) and run it using cron (read *man crontab*, and then run *crontab -e* and add your line there).

Saving streams is discussed here: [http://phossal.com/thread?view=702216934](http://phossal.com/thread?view=702216934)

---

### Post by stealth17 on 2007-03-05
> **Jussi Kukkonen said:**
> Use a command line recorder (like *arecord* from the package *alsa-utils*. arecord allows you to specify the length of the recording in secs) and run it using cron (read *man crontab*, and then run *crontab -e* and add your line there).

Saving streams is discussed here: [http://phossal.com/thread?view=702216934](http://phossal.com/thread?view=702216934)

Thank you very much!!

---

