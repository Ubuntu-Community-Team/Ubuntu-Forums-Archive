---
title: "Ati radeon7000"
date: 2009-08-23
forum: Mythbuntu
---

### Post by Shawn_Ky on 2009-08-23
I have searched high and low for answers and have rarely needed help. I have cometo the cross-roads...  I recently upgraded from Mythbuntu 8.10 to 9.04. I never used TV-OUT before so I don't know if it worked, but would assume it does. I have it working up until X Server starts, then just a blank screen on the television. If I switch out and go back to the OS, it is on the television.
 
Any ideas? I have used the driver ati and radeon. In order to get the tvout working (s-video) my magic command was: Option "ForceTVOut" "true"  just in case anyone else searches on how to get the S-Video out on this card. All of the other options seemed pointless and did not work; however, they may have helped.
 
Any help is much appreciated.

---

### Post by Shawn_Ky on 2009-08-23
Just in case anyone else tries to pull their hair out like I did, the fix for me was to add: 
Option "DRI" "off" to my xorg.conf
 
Everything worked fine after this.
 
Now to configure everything else...

---

### Post by kreggz on 2009-08-23
The latest ATI Catalyst Control centre is really good too.

---

### Post by Shawn_Ky on 2009-08-23
Where can that be found? I'll search, but...

---

