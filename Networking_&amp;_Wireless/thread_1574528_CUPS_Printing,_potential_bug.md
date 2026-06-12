---
title: "CUPS Printing, potential bug"
date: 2010-09-14
forum: Networking &amp; Wireless
---

### Post by barnaclekarl on 2010-09-14
I had an issue with a print job looping in the queue endlessly. It was caused by putting an unbuntu lucid client to sleep before its jobs had completed printing. The ubunu lucid print server did not show the job in its queue on the gui or in lpstat. 

I gave up on gracefully fixing the problem after seeing nothing in the queue and trying to delete and re-add the printer.

I deleted the job from /var/spool/cups. I crossed my fingers and rebooted. Everything looks OK now.

I'd like feedback. Was that a bad idea? Is there a graphical admin tool that would have allowed me to purge the queue? 

Thanks, Karl

---

