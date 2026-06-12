---
title: "[SOLVED] Sound card question.."
date: 2008-03-20
forum: Multimedia &amp; Video
---

### Post by Brookeorama on 2008-03-20
I have an outboard usb sound card (m-audio quattro), and while it is selected as the only card to use, firefox still uses the stock card. quite annoying because i have my sound system, going through the outboard
any idea?? Does this even make any sense??

---

### Post by wolfen69 on 2008-03-20
did you disable the onboard sound in BIOS?

---

### Post by Yellow Pasque on 2008-03-21
If ALSA doesn't support the device, try OSS4 (link in sig).
> ossusb  usbif763,2001   M Audio USB AudioSport Quatro (BETA)

---

### Post by Brookeorama on 2008-03-22
how noob do i look? =]
it functions in amarock and all other applications just fine, but only in firefox.
first I had head of flash pluggin issues that were similar to my complaint,m but its all sound out of firefox, even streamed data

---

### Post by Yellow Pasque on 2008-03-22
> how noob do i look? =]
well, you can't spell nvidia... :o

Try installing libflashsupport or do a search for it. I believe that is the crux of your problem.

---

