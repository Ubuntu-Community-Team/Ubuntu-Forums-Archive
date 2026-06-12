---
title: "Video conferencing help needed"
date: 2009-04-05
forum: Multimedia Software
---

### Post by Excedio on 2009-04-05
Hey Guys/Gals
 
Not sure if this should be here or in the Networking forum, but here goes.
 
 
I need help with creating a video conferencing tool. The tool will be used for testing to make sure that the video equipment (we'll call it a videophone) is setup correctly. I will need to make sure that it can, both, make calls and receive calls successfully.On top of that, it will need to have a method of knowing if the video is going through.
 
Currently our setup is like this:

[LIST]
[*]Videophone dials an IP address.
[*]IP address is connected to a computer with a video softphone (Mirial Pro) on it.
[*]The Computer at the other end has a webcam sitting directly in front of it, pointing at Mirial.
[*]Mirial auto answers the incoming call.
[*]Webcam at the other end reflects the image of the caller back through the webcam to ensure that there is 2-way video.
[*]Mirial waits 15 seconds, hangs itself up, and re-dials the previously incoming IP address back out.
[*]Original videophone making the call then rings.
[/LIST]This setup is getting to be pretty old, and with our companies new technology, we are moving away from H.323 calling and now using SIP. Problem is, when our SIP videophone dials the IP address, it connects at the other end, but it is not able to call us back.
 
The IP address that is being picked up at the other end is not the actual IP address of the originating phone, but the IP of the SIP server that the call is going through.
 
I am looking to create a new method to this process that will be able to handle both H.323 & SIP based calls. I am looking to do this as simply as possible,no need to be fancy fancy.
 
Here are two options of what I am looking to build:
[LIST]
[*]RTP Reflector
[*]B2BUA (Back to Back User Agent)
[/LIST] 
Also, this will be running 24/7 on a Windows XP station (please no flaming, this is my companies work station, not my personal computer) and not an Ubuntu machine.
 
Any help appreciated guys...thanks.

---

### Post by Excedio on 2009-04-07
Bump

---

### Post by Excedio on 2009-04-09
Could one of the moderators please move this thread over to the Networking forum? I'd like to see if it will get any results over there.

Thanks

---

