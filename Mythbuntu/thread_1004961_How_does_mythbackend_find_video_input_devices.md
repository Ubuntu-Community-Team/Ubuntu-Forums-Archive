---
title: "How does mythbackend find video input devices?"
date: 2008-12-07
forum: Mythbuntu
---

### Post by uMuppet on 2008-12-07
I'm writing a small program to make the setup of MythTV easier in our country (New Zealand).  The first few releases have worked well and I've had some good feedback from people, but I'm having trouble with the next step.  

When you go into MythTv Backend Setup -> Capture Cards -> New Capture Cards 
it displays the connected cards and the inputs.  How does it get this info?  I want to display a list of found connected analogue and digital video cards so the user can pick which one to use.

I have a Hauppauge PVR-150 connected and when I do a 
```
lspci | grep video
```
I get 
05:00.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)

Nothing about Hauppauge there.  

I have attached the latest release, or you can go to [MythKiwi.com]("http://mythkiwi.com") to read more.

---

