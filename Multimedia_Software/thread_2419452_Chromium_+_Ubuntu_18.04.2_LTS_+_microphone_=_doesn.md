---
title: "Chromium + Ubuntu 18.04.2 LTS + microphone = doesn't work!"
date: 2019-05-22
forum: Multimedia Software
---

### Post by flix3 on 2019-05-22
Hi everybody! My problem is the following:
[B]
What I'm trying to do[/B]

I'm using Ubuntu 18.04.2 LTS, I have a headphones+microphone set and I'd like to find a free app to dictate text inside a document.
After a bit of googling, I've discovered that the only possible and reliable way of doing it is by using an online speech recognizer, that requires the Chrome browser. So I've installed Chromium from  "Ubuntu Software" and I've tried one of the many available online speech recognizers (docs.google.com, but the same problem happens with all the others).

[B]What happens

[/B]When "listening" is active in Chromium, the microphone keeps connecting and disconnecting continuously (many times per second) and no text is recognized. 
[B]
What I can understand about it[/B]

[LIST]
[*]This always happens when Chromium captures audio. 
[*]This never happens when every other desktop program captures audio (I can save my voice into a wav file without any problem). 
[*]In the "pulse audio control panel" the connection in the following image (click to enlarge it) keeps blinking (this happens only with Chromium): 
[/LIST]
 [ATTACH=CONFIG]283304[/ATTACH]

What can I do to solve the issue ?
Thank you in advance for all your possible help...

P.S. I'm using Chromium [COLOR=#5F6368][FONT=Roboto]Version 73.0.3683.86 (Official Build) Built on Ubuntu , running on Ubuntu 18.04 (64-bit)[/FONT][/COLOR].

---

### Post by flix3 on 2019-05-22
Just to say that this is probably the same issue as [https://ubuntuforums.org/showthread.php?t=2393830](https://ubuntuforums.org/showthread.php?t=2393830)

It's a bug in Chromium reported here ([https://bugs.chromium.org/p/chromium/issues/detail?id=902217#c29](https://bugs.chromium.org/p/chromium/issues/detail?id=902217#c29)) and not yet fixed...

---

### Post by flix3 on 2019-05-23
According to this issue: [https://ubuntuforums.org/showthread.php?t=2396947](https://ubuntuforums.org/showthread.php?t=2396947) Chrome is not affected by this problem.

How can this happen? Isn't Chrome based on Chromium? Is there some interest in forcing users to install Chrome instead of Chromium?

---

### Post by bjohas on 2019-08-08
Hello,
are there any fixes for this in sight?

---

### Post by jonjenkins on 2019-08-08
Only fix is to install Slimjet, works fine there, this is Chromium issue, no fix insight ....

---

