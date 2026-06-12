---
title: "Problem with a webcam"
date: 2007-11-24
forum: Multimedia &amp; Video
---

### Post by Starlight on 2007-11-24
Hello!

I have a webcam, it's recognized by Ubuntu as "Aiptek mini PenCam" (it's actually a Medion webcam) and I decided to use it... yesterday it worked (almost) perfectly (it crashed aMSN, but everything was great in Kopete) and I was happy. But after some I went away from the computer for a while, with the webcam still connected. When I came back, the webcam window was very dark. Increasing brightness didn't help, because even on maximum brightness it wasn't really bright (the weird thing about brightness and other webcam options is that it doesn't seem to work in a linear way... for example, the highest brightness is a little to the right of the center of the brightness bar... if I try to move it more to the right, it gets darker instead of brighter. It's similar with contrast). Today I tried using my webcam again, but it's still really dark. I tried rebooting the computer, disconnecting the webcam and connecting it again, but nothing helped. Does anyone know how I can get my webcam to work well again? Is it a software problem, or can it be a broken webcam?

EDIT: I don't know if it's relevant, but here's the error I get when aMSN crashes during the webcam setup.

> 
can't read "brightness": no such variable
    while executing
"::Capture::SetBrightness $grabber $brightness"
    (procedure "setPic" line 31)
    invoked from within
"setPic $::CAMGUI::webcam_preview"
    (procedure "::AVAssistant::StartPreviewLinux" line 52)
    invoked from within
"::AVAssistant::StartPreviewLinux .assistant3.bodyf.contentf.left.chans SPCA504"
    ("after" script)


But I'm not sure if it's relevant, because I got it even when my webcam worked well in Kopete...

---

### Post by loell on 2007-11-24
it could be  broken, try it on a windows box and see if it is still working.

---

### Post by Starlight on 2007-11-24
> **loell said:**
> it could be  broken, try it on a windows box and see if it is still working.
I've just tried on Windows, but I haven't had any luck yet.... Windows was looking for the drivers on the internet for a few minutes, and said that it hadn't found any.

---

### Post by loell on 2007-11-24
okay, if it worked the first time, you can also try your ubuntu livecd ,

in there, try running ekiga , skip the account configuration, just hit the cammera button, and see if it can feed some images from your webcam.

---

### Post by ipatec on 2008-03-07
I have the same webcam but it's not recognised on Gutsy... any adivice?

---

