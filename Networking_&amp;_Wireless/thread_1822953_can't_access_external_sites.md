---
title: "can't access external sites"
date: 2011-08-11
forum: Networking &amp; Wireless
---

### Post by trspencer on 2011-08-11
Strangest thing...yesterday my 11.04 box lost the ability to access anything external. I can ssh to the box from outside my network, and all other boxes on my network are fine, but this one box can't hit anything external. If I attempt to ping a site it's doing the same resolution, but no packets are delivered. 

Up until yesterday it was running fine, and I didn't make any changes to my home network or install any updates. Totally stumped. Any ideas?

Thanks,
Tim

Edit: this is a wired connection with a static internal IP.

---

### Post by ajgreeny on 2011-08-11
Can you ping your router (IP will be on a label underneath, probably)?  What about pinging other computers on the same network, or are you classing them as external?

---

### Post by lmarmisa on 2011-08-11
Please, post the results of these two commands:

```

ping -c3 8.8.4.4
ping -c3 google.com

```

---

### Post by trspencer on 2011-08-11
Yep...I'm able to ping my router. 

I found the problem, and it turns out it's Linksys related. Port forwarding config was all hosed, their support asked me to delete all port forwarding/triggering, and add back the ones I needed. After doing so everything started working again. They weren't able to tell me why rules that had been in place for almost two years reared their heads today, but I'm functional again and didn't have to modify anything at the os level. 

Thanks guys for your replies...much appreciated.

---

