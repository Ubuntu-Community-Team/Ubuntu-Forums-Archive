---
title: "Microphone on HP dv6 not working"
date: 2009-12-29
forum: Multimedia Software
---

### Post by Neezer on 2009-12-29
So my microphone stopped working on my HP dv6 for skype. I really am at a loss. I thought it might have been a problem with my Skype, so I reinstalled it. The mic worked on a test call, but then I restarted my computer and it didn't work after that. 

I have no idea where to even begin troubleshooting the mic.

---

### Post by Neezer on 2009-12-29
A bump for the afternoon.

---

### Post by Neezer on 2009-12-31
I fixed it!!! If you use your alsamixer app in the terminal you can change the gain on the inputs....

use 
```

alsamixer

```

Then press tab to get into the inputs menu...I just turned on the microphone and voila!

---

