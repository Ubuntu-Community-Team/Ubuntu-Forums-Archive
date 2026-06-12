---
title: "Why can Linux not support instant messaging webcam conversations?"
date: 2009-04-05
forum: Multimedia Software
---

### Post by talking Llama on 2009-04-05
Just a quick question that has been bugging me, not necessarily help: Why do very few (if any) IM clients not support webcam viewing/sending in Linux? Is the code hard to write? Is the feature owned by a particular company? What is it?

Thanks.

---

### Post by orethrius on 2009-04-05
Interesting you should ask, the best I've been able to determine is that it's some complex combination of all those factors and more.  One of the major issues getting webcams to function within Linux is the propogation of so-called "softcams" - hardware cameras that rely on parts of the Windows API existing in order to properly run the camera.  Some work has been done to reverse-engineer the more popular models, but a number of also-rans still have basic - if any - support.  In that regard, it's very similar to the issue with "Winmodems".

Beyond that, the support of webcams within multi-clients is up to their respective development communities.  Whereas Skype is known to have decent support, it also subscribes to a "mass audience" support approach wherein any hardware that utilizes the Windows API can work with their own proprietary code.  Who knows how much Skype paid Microsoft to exercise that right.  When it comes to Pidgin, Kopete, and the like, the software is developed according to what users are willing to contribute.  If you can pitch in some hardware logs and maybe a software configuration or two, the developers are more likely to respond to your requests; otherwise, they're more concerned with their own interpretations of what makes a good IM client.  The prevailing attitude is that the only thing stopping you from making your own plugin is a lack of education (in C, in hardware interrupts, etc etc).

Even bearing this in mind, the individual result - assuming you can get a developer to cooperate in supporting your hardware - cannot be applied universally.  Your hardware will be supported, but the simple fact is that no webcam API has been widely established yet.

---

### Post by bgerlich on 2009-04-05
Almost every SIP client supports Video conversation. Skype has video conversations. If you are thinking about yahoo and google talk then yes - the protocol is proprietary, obfuscated, probably patented and probably encoded.

---

### Post by bgerlich on 2009-04-05
> **orethrius said:**
>  Your hardware will be supported, but the simple fact is that no webcam API has been widely established yet.

[http://en.wikipedia.org/wiki/Video4Linux](http://en.wikipedia.org/wiki/Video4Linux)

---

### Post by talking Llama on 2009-04-05
Thanks for all the replies concerning my question. Why don't all the IM clients in Linux use this Video 4 Linux approach to webcam? Surely it would make a lot more sense?

---

### Post by orethrius on 2009-04-05
Yes, there is always V4L.  The simple fact is that it's a capture-card software package forced into the role of webcam go-between.  The major issue that I've seen is that this approach works well with cameras that exist entirely in hardware, but not with cameras that rely on particular parts of Windows APIs existing.  A $20 Logitech camera doesn't work well with v4l because it relies on the system responding a certain way, but an $80 camera probably would.  Technically speaking, it would behoove the authors of v4l to incorporate as many webcam packages as possible in that regard, but that's an issue of choice between the developers of both v4l and specific webcam backends.

---

### Post by hessczoo on 2009-04-05
Good question, I actually had been wondering that just the other day. From what i can see from reading developer's forums it is just a lot of work to have such a protocol, and have supported hardware for it. Besides that, webcam isn't that important of a feature, it is more important to have a stable, fuctional client, and webcam is more of a luxury. Unless you can help contribute, or at least start to write the code like orethrius said, good luck getting much attention.

---

### Post by talking Llama on 2009-04-05
OK. Thanks for the replies everyone, I think I'm starting to understand now... Perhaps one day I could help contribute to the code for webcam integration? However that is most unlikely... And I agree, webcam isn't important, as such, but more of a luxury. It would just be nice to have.

An ironic side note: My webcam is a Microsoft LifeCam VX-5000, I've completely integrated/switched to Linux (Ubuntu) and there are drivers for my webcam and it works perfectly.[]("http://www.microsoft.com/hardware/digitalcommunication/productdetails.aspx?pid=014")

---

