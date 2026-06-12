---
title: "Hercules Deluxe Optical Glass Webcam Issue"
date: 2010-06-29
forum: Multimedia Software
---

### Post by voltaic on 2010-06-29
Hi everyone,

I've recently purchased a "Hercules Deluxe Optical Glass Webcam" (in retrospect I really should've thought more about which camera to buy, and made sure it was an easy work with ubuntu... but oh well) and I'm having some trouble getting it to work (I'm running 10.04 32-bit)

I plugged it in and nothing happened, I ran lsusb and see this line in there:

Bus 001 Device 004: ID 06f8:300d Guillemot Corp. 

After doing a bit of research on the camera I see one previous post in this forum about an issue with it, and a couple of things scattered about the web, but no definite fixes. Before I start screwing things up I was just wondering if anyone has had any luck with this camera, or has any suggestions as to what I should do to get it working.

-Regards,
Daniel

P.S. This is especially tricky because I'm actually installing it for my girlfriend on the other side of the world so I have to do everything through SSH/VNC, and my internet connection where I am now is terrible so everything takes ages to do.

---

### Post by voltaic on 2010-06-30
ok I compiled GSPCA 2.9.45, and now the webcam works, however there is an issue with skype; when I open skype and go to video settings I can test the video feed and it works fine, but when I make a call to another skype contact skype crashes as soon as I start the video feed. This one has me a bit stumped, any ideas?

---

### Post by voltaic on 2010-06-30
In the spirit of this conversation with myself, I have found a workaround for this issue, and will post it here

The computer that was having the issue is older, and has crap integrated intel graphics, according to xvinfo, there is only 1 xv port, so skype was crashing as a result of having the video preview for the local camera, and the video feed from the remote camera open simultaneously, by disabling the local camera preview in skype and only having the remote video feed open skype works.

Next issue however is that the integrated microphone in the camera is not working, I'll do some googling to see if I can sort it out, but if anyone has any ideas in the meantime, please let me know.

---

### Post by YannBuntu on 2010-07-03
Hi,

if it is a Skype problem, I recommand you try either:
- Ekiga (with the PPA [http://wiki.ekiga.org/index.php/HowTo_install_Ekiga_packages#10.04_Lucid_Lynx_.28Long_Term_Support.29](http://wiki.ekiga.org/index.php/HowTo_install_Ekiga_packages#10.04_Lucid_Lynx_.28Long_Term_Support.29) )
- Empathy (with Telepathy PPA)

---

