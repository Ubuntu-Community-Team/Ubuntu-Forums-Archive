---
title: "Mythtv - Watch TV - frames dropped resulting in strobbed / choppy video"
date: 2008-02-19
forum: Multimedia &amp; Video
---

### Post by DominicF on 2008-02-19
Hi,

I have a problem that when I use the watch Tv function in mythfrontend the output to my display shows tv in a strobbing/ choppy video effect i.e. frames are being dropped.  I tried adjusting a number of settings but haven’t found the right one.

My system runs both a Mythbackend and Mythfrontend, the Mythfrontend reports that my hardware isn’t able to display at my chosen display setting of 1368x720 and frames will be dropped to sync with audio.  I tried adjusting the resolution of the monitor and also running mythfrontend in a much smaller gui window but still the same result of strobed /choppy video being displayed.  However, when I record a program and play it back it plays back perfectly.  Also, I tried both Kaffein and more recently Me-Tv and watching live TV with these applications without a fault.

So, my system consists of a dual core 2 Ghz Intel processor, 500Gb SATA hard disk and and a Nvidia 256Mb 8400GS video card.  2Gb RAM.  My DVB card is the Freecom USB DVB stick.  I’m usig the Nvidia video drivers.

I have a Nvidia 8400GS video card, I know that the current drivers for this card does not support XVMC for Linux and therefore I have to export NO_XV=1 and then execute mythfrontend from a terminal window.  Otherwise Mythfrontend crashes my session and I have to re-login everytime I select Watch TV.

I tried to monitor CPU usage when I run Watch Tv trying to see if my machine was being overloaded but it wasn’t.  The CPU usage levels out to 15-30%, RAM usage levels out to about 360 Mb.

Any suggestions what I can try next?

---

### Post by kaivalagi on 2008-05-09
Have the same problem it seems, I am running mythbuntu 8.04 on the backend, and ubuntu 8.04 on the frontend. The hardware is all definately high enough spec.

Do you discover what the problem was for yourself?

I am wondering if it is a network issue resulting in poor data transfer? I am using a 54MB wireless connection from the backend (media center box) to my router, which in turn is wired to the frontend (tower pc) at 100MB...

---

### Post by DominicF on 2008-05-12
Hi,

I managed to fix my issue but not untirley sure how I had done it as I had followed a number of different leads.  

The thing I can remember is that at the time I was trying to fix another issue and was installing a whole bunch of codecs for example LAME which I think might have been the trick.  Also, upto that time I was using a my own user account to run mythtv, then I followed some instuctions to do the autologin for the mythtv user... it was at this moment I noticed that LiveTv was working properly, I switched back to my normal user account and ran up mythtv and that too was running properly.

Since then, I've built another machine with 8.04 Hardy and Mythbuntu Contol Centre and Mythtv managed to work first time.  However, I did notice the Choppy LiveTv when I was playing around with the options on the Playback menu from the setup menu.  You might to set it to the setting 'Normal'.

Good luck.

---

