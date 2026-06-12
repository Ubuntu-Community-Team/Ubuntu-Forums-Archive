---
title: "Need remote help. Only partially works."
date: 2009-09-18
forum: Mythbuntu
---

### Post by JamesClark on 2009-09-18
I have a PSR-2000 remote: [http://www.pstc.com.tw/homepage/RemoIR.htm](http://www.pstc.com.tw/homepage/RemoIR.htm)

Now, only some of the remote works. Right out of the box, the power button, as well as the mouse functionality works. But no other buttons do.

I found that if I do sudo cat /dev/hidraw0, that a bunch of gibberish is output when I use the mouse. When I do sudo cat /dev/hidraw1 it prints out gibberish whenever I press any of the other buttons. So it looks like the remote and receiver are working fine, but I need some way for MythTV to use the signals being picked up by hidraw1. 

Any direction would be greatly appreciated, thanks!

---

### Post by williammanda on 2009-09-19
1st...it sounds like your remote is working through hal and not lirc.
2nd if you installed mythbuntu you have to install lirc, which is a section in the control center. Once you have that done you can you run irw from terminal. Then press each key on the remote and you should get a hexidecimal output. This will show you that the remote is working with the lirc program. If you have selected a remote that is supplied by mythbuntu you should be really to go. If your remote isn't supported by mythbuntu then you are in for a bit of work to get it working if at all possible. During the selection of the remote...if yours is not listed then select custom...this will at least allow you to run irw and test the remote.

---

### Post by JamesClark on 2009-09-19
Do you know how I can get it working through LIRC over HAL?

I'm pretty sure my remote isn't supported already. I didn't see anything that looked like mine. If I change the remote to Custom in the control center and then run irw, I get no response at all from pressing any buttons.

---

### Post by williammanda on 2009-09-20
> **JamesClark said:**
> Do you know how I can get it working through LIRC over HAL?

No...

> I'm pretty sure my remote isn't supported already. I didn't see anything that looked like mine. If I change the remote to Custom in the control center and then run irw, I get no response at all from pressing any buttons.

Well...either write drivers for the remote or scan the internet for someone who has or get a remote that is supported.

---

