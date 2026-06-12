---
title: "need help setting up midi"
date: 2008-02-28
forum: Multimedia &amp; Video
---

### Post by rouge568 on 2008-02-28
Ok, so I had a few hours free the other afternoon and decided to try and get rosegarden working again. I knew that I needed a realtime kernel, so I downloaded it, rebooted, and it worked! This is where I got hung up before, so this was a very exciting step. After working through some hours of documentation and trial and error, this is what I've come up with:
1) jack hooks together all of the parts I need to get this working. I am able to get this up and running without any xruns, so this is all good.
2) I need a software synthesizer, since I don't have a dedicated soundcard, and I am not actually using any real instruments. I am using qsynth (which is a frontend for fluidsynth), and have a soundfont loaded. It is receiving an output from rosegarden, which I know since the little light on the frontend flashes in rhythm when I play my little demo piece on rosegarden.
3) I am getting no sound from my speakers. This is the big problem, and I have no clue where it's at. Attached is a screenshot of patchage (great little app), which is showing my jack connections. I am happy to provide any additional information you may need to get this fixed. Any and all help is appreciated.

---

