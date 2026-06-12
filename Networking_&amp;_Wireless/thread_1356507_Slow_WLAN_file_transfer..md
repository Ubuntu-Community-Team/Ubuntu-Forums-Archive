---
title: "Slow WLAN file transfer."
date: 2009-12-16
forum: Networking &amp; Wireless
---

### Post by dimamali on 2009-12-16
Hello Community!
After a long research i decided to post my problem here for once more. I'll try to be quick.
Link-sys router WAG200G
Desktop PC and laptop currently running 9.10.
The Internet connection is fine. Streaming HD movies between pc' s works in speeds around 5MB/s but when it comes to simple file transfer the speed is approximately 500KB/s which is rather slow.
It's not a signal strength issue, it's not an interference issue, it's not a wifi channel traffic issue, it's not a bg/b/g mode issue. What's more it's not even Linux specific issue as i found out that many Windows users are also having the exact same problem (among many other problems i guess :-p).
Could it be samba problem (everything is set up to default)? 
Could it be a creepy invisible monster that feeds with unused bandwidth...?

The bandwidth is there, there must be someway to use it!

---

### Post by dimamali on 2009-12-16
No replies yet, i'll post my progress just in case i am not alone out there :-p
It looks as if it is a samba issue. 
Giver  (which does not use samba) seems to work fine for simple file sharing at a rate of 2MB/s. That proves that it's not a signal quality problem.
I tried some samba twicks and the speed got a slight boost to 800KB/s but i am still reaching for the stars.
So i was told to give gnome-user-share a chance to prove itself. Disabled samba, enabled that and my results where quite unstable. The transfer progress bar is freezing, even the file transfer itself is freezing and it looks like it is causing some more network problems, like weird wicd acting, disconections, time-outs etc. What is more the rate jumps from 50KB/s to 13MB/s (which is nonsense...) and back to 50KB/s, and up to 400KB/s etc etc etc.
Since the giver app works there must be a way to make it work better.
Any ideas???

---

