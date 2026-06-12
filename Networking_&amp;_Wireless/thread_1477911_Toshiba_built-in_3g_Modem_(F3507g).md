---
title: "Toshiba built-in 3g Modem (F3507g)"
date: 2010-05-09
forum: Networking &amp; Wireless
---

### Post by Weazel on 2010-05-09
Hey guys,

I've been going crazy for 2 years now trying with various types of ubuntu to be able to connect with my 3g modem on my Toshiba Tecra, I have a F3507g Ericcsson broadband modem.

The Network-Manager always seemed to find it, but whenever I configured an APN with the correct settings, It'll always return with GSM Network Disconnected message.

Apparently the 3g modem Radio is by default set to OFF.


What I did is write in terminal:

```
sudo toshset -3g on
```

and vuwala It worked like a charm!!!!

I bet this works around all toshiba laptops, though didnt really tested it!

Hope this helped!
Good Luck,

Weazel.:guitar:

---

