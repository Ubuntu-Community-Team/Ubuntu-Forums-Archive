---
title: "logitech v20 weirdness"
date: 2008-02-20
forum: Multimedia &amp; Video
---

### Post by MEGAMANULTIMATE on 2008-02-20
Contrary to what some might be thinking, the speakers in question; the Logitechs, that is, are working to a point. The only trouble is that I cannot seem to adjust the left speaker at all. Every time I bring up the Volume Control window and try to manually adjust the volume, the left speaker meter always retracts over and over again, making it impossible for me to hear out of it properly. Are there any thoughts as to why this is happening? Any help at all would be appreciated.

---

### Post by 1ll3xc on 2008-03-22
Did you ever resolve the problem? I had the same problem before the sound stopped completely. Extremely annoying issue and any tips on how to get this worked out would be much appreciated.

As mentioned I can't get any sound at all from them at the time being having tried all of the following:

1) Setting the speaker-soundcard as default with:
sudo asoundconf set-default-card Speaker

2) Setting all of the settings of the System > Preferences > Sound to ALSA except the standard mixer track to Logitech USB Speaker.

3)  Gnome-volume-control is also configured to use the Logitech USB Speaker (and as mentioned initially features problems with the left channel driving me crazy when configuring...).

Could the problem be related to using a USB-mouse (Logitech MX 518)? I noticed the response of the mouse changed after getting the speakers to work initially which made me configure the mouse anew. Sound was working ok after that but after some hour or so things started behaving a bit weird with sound suddenly disappearing and then reappearing within a few seconds until finally no sound at all...

Thanks in advance!

---

### Post by itsme_n8 on 2008-05-16
Did anybody resolve this?  I have problems with my Logitech USB Speakers, only I can't adjust the volume at all!  When they are in use they are at max volume and I can't get it to stop doing that.  I know not quite the same thing you are experiencing, but maybe if you found a fix, it might apply to mine?  I dunno worth a shot.

Nate

---

### Post by 1ll3xc on 2008-05-19
Nate,

Unfortunately I did not solve the problem and the lousy response from the Logitech had me basically throwing them back to the dealer. I went for a couple of not very portable Creative Gigaworks T40 speakers instead... Heck, if I can't follow the portable route I might as well go for the boombastic approach! ;)

Good luck anyway!

---

### Post by yugan on 2008-05-23
hey guys,
i had the same issue with my Logitech USB Speaker. I installed the 'alsamixergui' and adjusted the volume. its working now..!!

hope this is helpful!

---

