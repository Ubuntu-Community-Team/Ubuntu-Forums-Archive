---
title: "[SOLVED] Swiftfox does not play flash video like YouTube, but Firefox does... Help!"
date: 2007-09-11
forum: Multimedia &amp; Video
---

### Post by tak1150 on 2007-09-11
I've been very happy with Swiftfox b/c it does load much faster than Firefox on my laptop. I have encountered a problem: it does not play YouTube videos!

What's strange is Firefox does play them perfectly. I have checked /opt/swiftfox/plugins/ and libflashplayer.so is in there.

Could somebody point me in the right direction here? Thank you! :)

---

### Post by tak1150 on 2007-09-11
OK...
I fixed it.

I did the following (hopefully useful for somebody else);

```
sudo cp /usr/lib/firefox/plugins/* /opt/swiftfox/plugins/
```
and done!

---

### Post by bashologist on 2007-09-11
Another way would be to run the flash installation script as root, then enter "/usr/lib/swiftfox/", or "/opt/swiftfox/", for the path when asked. Don't forget to mark you thread as solved btw.

---

### Post by tak1150 on 2007-09-11
How do I mark it as solved? I tried editing the title, but it was not updated. Thanks.

Edit: figured it out!

---

