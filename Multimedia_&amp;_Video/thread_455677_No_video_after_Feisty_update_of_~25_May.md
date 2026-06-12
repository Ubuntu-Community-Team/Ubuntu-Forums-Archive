---
title: "No video after Feisty update of ~25 May"
date: 2007-05-26
forum: Multimedia &amp; Video
---

### Post by Seine on 2007-05-26
Yesterday I was using my Feisty and casually updated a new package. I don't recall what it was, some lib. Today I boot up and I get the all-too-familiar could not start x-server display.

Does anyone know:

What that package was? 
Why it might have destroyed my X (or why it couldn't have)? 
How I can get video back?

Cheers
Seine

---

### Post by Seine on 2007-05-26
I'm using Lynx to view this page. Wow, what an experience. At a guess I tried sudo dpkg-reconfigure xserver-xorg. It responded by saying that xserver-xorg is not installed. I'm not sure what that implies. Any help is appreciated.> **Seine said:**
> Yesterday I was using my Feisty and casually updated a new package. I don't recall what it was, some lib. Today I boot up and I get the all-too-familiar could not start x-server display.

Does anyone know:

What that package was? 
Why it might have destroyed my X (or why it couldn't have)? 
How I can get video back?

Cheers
Seine

---

### Post by Seine on 2007-05-26
I tried sudo dpkg-reconfigure -phigh xserver-xorg and this this fixed it. Phew.

---

