---
title: "pavucontrol not working properly in 10.10 Maverick"
date: 2010-11-11
forum: Multimedia Software
---

### Post by sosaited on 2010-11-11
I had installed pavucontrol in Ubuntu 10.04 to record the sounds being played on the system, by changing the "Record stream for" value to "Monitor of Internal Audio Analog Stereo".

I installed pavucontrol in Maverick as well, but here it doesn't capture and show the sounds being played at all, not even in playback (No sound meter bar activity below each entry). The sound can still be decreased/increased and it shows all the devices playing back or recordong. Also if I change the hardware to "Digital duplex" from Analog stereo Duplex" it starts capturing and showing the streams, but then I can't hear anything from the speakers. I even compiled the newest pavucontrol, but still the same.

---

### Post by lidex on 2010-11-11
Do you have paprefs? 'System > Preferences > Pulse Audio Preferences'

---

### Post by sosaited on 2010-11-11
Yes I do. But I hadn't set anything specific in it on 10.04 neither, and same is the case here. I don't think any from paprefers is the problem. Though I have noted that the padevchooser had a earphone.headphone type of icon on the panel when I ran it on 10.04 (I was using a Azenis theme) but here I get an icon of a window/ractangle with a "stop" sign (circle with a line across it) in it. But again, I had not used this to change anything in 10.04. After installing pavucontrol, I could see the sound output monitor meter working and I could choose the Monitor of.... option for the recording application. Can't here.

---

### Post by lidex on 2010-11-12
> **sosaited said:**
> Yes I do. But I hadn't set anything specific in it on 10.04 neither, and same is the case here. I don't think any from paprefers is the problem. Though I have noted that the padevchooser had a earphone.headphone type of icon on the panel when I ran it on 10.04 (I was using a Azenis theme) but here I get an icon of a window/ractangle with a "stop" sign (circle with a line across it) in it. But again, I had not used this to change anything in 10.04. After installing pavucontrol, I could see the sound output monitor meter working and I could choose the Monitor of.... option for the recording application. Can't here.

The sound scheme has changed and PA Manager as well as PA Device Chooser have been deprecated. You can use paprefs to loopback audio to your speakers.

---

### Post by sosaited on 2010-11-15
I tried almost every option I could in the paprefs, including loop to speakers, but none worked. I just don't get any output from the output sound monitor "bars". Neither in the PulseAudio Volume Meter.

---

### Post by FM33 on 2011-03-17
Hello,

I have exactly the same problem, except it was working a few months ago. I didn't use this functionality frequently so i have no idea of what (an update ?) created the problem.
My sound card info :
lspci : MCP51
alsamixer : chip AD1986A

---

### Post by kettlefish on 2012-02-15
Hi,

I realise this thread is a bit old, but I have just experienced a similar problem. I have sound playing, but I get no levels showing in the playback section of pavucontrol. 

After 45 mins of searching I accidentally stumbled on the solution for my system, and I thought I'd post it in case anyone has the same issue.  For me, it was a simple case of the monitor being muted. Doh!

In pavucontrol go to input devices, then in the show button at the bottom switch it to All input devices.  I believe it's normally set to all except monitors, so the monitor doesn't show up.  In my case it was this monitor that was muted, but I could still hear sound  because the internal audio wasn't muted (I think).

Hope it helps someone

toodle.

---

