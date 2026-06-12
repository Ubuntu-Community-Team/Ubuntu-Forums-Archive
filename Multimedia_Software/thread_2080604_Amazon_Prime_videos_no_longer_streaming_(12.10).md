---
title: "Amazon Prime videos no longer streaming (12.10)"
date: 2012-11-04
forum: Multimedia Software
---

### Post by cleentrax on 2012-11-04
We have used Amazon Prime for streaming video on our home theater PC with Ubuntu for months. In the last couple of days, it stopped working. The video tries to connect, and then there is a "player update" progress bar and then we get the following error:

"Player Update: An error occurred and your player could not be updated. This is likely because your Flash Player or Browser needs to be updated. this update is required to play back this video. "Click here to learn more about updating your player." Retry."

This happens in both Chromium and Firefox. I have Restricted Extras installed, including Flash.

Anyone else experiencing this?

---

### Post by voxelite on 2012-11-04
I'm also experiencing the same behavior. No luck finding a workaround yet. 

Anybody else have any ideas?

---

### Post by oldos2er on 2012-11-04
Maybe something here can help? [http://www.amazon.com/forum/amazon%20video%20on%20demand?_encoding=UTF8&cdForum=Fx3EQAX98ED5WQ3&cdPage=1&cdSort=newest&cdThread=TxFTGOK5LRL3JM](http://www.amazon.com/forum/amazon%20video%20on%20demand?_encoding=UTF8&cdForum=Fx3EQAX98ED5WQ3&cdPage=1&cdSort=newest&cdThread=TxFTGOK5LRL3JM)

---

### Post by SeijiSensei on 2012-11-04
You need to install **hal** ("sudo apt-get install hal").  HAL has been deprecated in favor of udev by all modern distros, but the DRM method Amazon uses requires it anyway.  I'm sure Amazon would prefer this not to be the case, but they have to do what the studios tell them if they want to stream the films.

---

### Post by cleentrax on 2012-11-09
ding ding! thank you.



> **SeijiSensei said:**
> You need to install **hal** ("sudo apt-get install hal").  HAL has been deprecated in favor of udev by all modern distros, but the DRM method Amazon uses requires it anyway.  I'm sure Amazon would prefer this not to be the case, but they have to do what the studios tell them if they want to stream the films.

---

