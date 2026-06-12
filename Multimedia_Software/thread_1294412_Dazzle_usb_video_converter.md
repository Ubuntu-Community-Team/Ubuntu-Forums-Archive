---
title: "Dazzle usb video converter"
date: 2009-10-18
forum: Multimedia Software
---

### Post by Ka Fish on 2009-10-18
I bought [http://images.tigerdirect.com/skuima...21-8122-a1.JPG]("http://images.tigerdirect.com/skuimages/large/P121-8122-a1.JPG"). The light comes on when I plug it in, but the computer does not recognize it. I just installed Wine, but I don't know how to configure it. I put the pinnacle install disk in & it does nothing either. Can someone give me directions on how to get the thing working? I'm fairly new to Ubuntu so step by step directions would be appreciated.

---

### Post by redxine on 2009-10-18
I also own the same card (DVC 170) and it is the cause of all my pain from pinnacle. The card was made with an encrypted MPEG stream that can only be decoded using Pinnacle's Studio 9+ video editor. Many people have complained about it not working with third party applications, so I wouldn't expect it to work in linux any time soon. I have tried running XP in virtual box, but the entire thing went down in a blue screen after about 1 second of capture. Wine doesn't have the libraries required to get the hardware working either. My recommendation to you for A/V capture is to check out a DV Camera. Some cameras, like my Sony Handycam DCR-TRV740, when in 'VCR' mode will take input from the component cables (the ones that usually output to the TV) and stream it to DV, and that can be read without failure using dvgrab. You might have to flip through the options on the camera to enable it though. On mine it's under "VCR SET" and is called "A/V > DV OUT". Set that to on and capture away. It should display the input on the LCD also.

---

