---
title: "suggestions for a capture card no tuner"
date: 2008-05-16
forum: Mythbuntu
---

### Post by rickyble on 2008-05-16
I am looking for a capture card, no tuner just a strait up capture card with a digital input.  Rather not have hdmi but would take it in a pinch.  Much rather have dvi or component. This is of course for the mythbuntu and to be used on the backend.  Any suggestions and thanks in advance.

---

### Post by volkswagner on 2008-05-16
You may have to wait for the Hauppauge HD-PVR.

I know I am anxious, as I am unaware of any other solution.

[http://www.gossamer-threads.com/lists/mythtv/users/319270]("http://www.gossamer-threads.com/lists/mythtv/users/319270")

I hope I can afford one.  :)

---

### Post by rickyble on 2008-05-16
I have found some like black magic but I dont think there are linux drivers or work with linux.  Also they are expensive.  It really really sux.  Why in the world in this day and age would you want to capture and use analog or take a receiver/source with perfectly good digital video and capture it as analog.  Its just ridiculous.  And if you use one of the hd tuner cards it has on a coax input or some sort of analog input.  GEEZ!

---

### Post by newlinux on 2008-05-16
The black magic HDMI capture card wouldn't work for TV even if it had linux drivers because It doesn't support HDCP (last I checked). The component capture card would require a hefty processor and very large, very fast hard drives to capture uncompressed hd. the Hauppage DVR has dedicated hardware to compress the analog capture.

No consumer wants to capture digital broadcasts via analog, however the content providers have strong content protection on the digital outputs - eliminating 3rd party solutions. That's why you don't see them.

tha analog input (coax) on the hd tuner cards is really no different than the analog coax inputs on digital cable boxes. The signal for the digital stations comes across the analog line, thus they need an analog input which they simply capture to digital (mpeg-2) stream. So the quality is just as good as any digital cable set top box.

---

### Post by rickyble on 2008-05-16
Thats one reason I want the DVI vs HDMI.  You dont have to deal with the HDCP.  I have hd receivers from Directv and I wanted to deliver the signal straight to the Media Server Backend of Myth with out having to go from digital back to analog.  Right now I do that but I have to involve another PC for the transfer from the DVR to the backend.  I wanted to combine that two step process into one.  Actually I will have to disagree with on the quality.  I have source strait from HD to DVD transcoded and the same shows from analog to DVD and there is no comparison.  The original source is so much better the quality of the DVD or the VOB files stored on the Media Server is unbelievable. Digital sources recorded and replaying digital sources to digital displays.  Anyway I think its a real shame that broadcasters have been able to manipulate the industry.  Thats why you dont see DVI anymore.  The HDCP was not implemented as part of the DVI not like HMDI.  Digital should be no different then analog.  Anyway I take it there are no such capture cards.  I did find some but the price was outrageous.

---

### Post by newlinux on 2008-05-16
I'm not saying digital to digital and  analog to digital produce the same quality. I'm saying QAM/ATSC tuner cards capture the signal from coax in exactly the same way as a cable box captures the signal from coax. Despite its analog input, it is in essence tuning and capturing a truly digital stream in the same manner and quality as a digital cable box does for digital station. What you are talking about with transcoding is a completely different topic. 

Believe it or not, most DVI interfaces on TVs and set top boxes also support HDCP. The true difference is the ability to transmit digital audio (which dvi can't do but HDMI can). So getting a DVI capture card would have the same problems as HDMI with the added complication of mixing in the audio signal from a separate input. This is because capturing from a cable or satellite digital video output will always run into HDCP whether it be DVI or HDMI.

---

