---
title: "How do I debug Ekiga not sending video?"
date: 2009-02-21
forum: Multimedia Software
---

### Post by gregscott on 2009-02-21
Hello - 

I am trying to make Ekiga bundled with Ubuntu 8.10 (64 bit) work.  I think the Ekiga version is 2.0.12.  The Ekiga system is a new HP laptop with builtin webcam.  

I am trying to run an H.323 call between the Ekiga laptop and another H.323 endpoint.  The other H.323 endpoint is a Tandberg 880MXP.  I know the Tandberg is good because I use it for other video calls.

The laptop and Tandberg are both are on the same 10.10.10/24 subnet and there is no firewall or router between them.  Both the Tandberg and Ekiga are set up with no NAT or STUN or any kind of address translation.  

Here is the problem.  I do not see any video on the Tandberg.  Audio works both ways - both the Ekiga laptop and Tandberg can hear the other side's audio.  The Ekiga laptop can see video from the Tandberg.  But the Tandberg cannot see video coming from the Ekiga laptop.  

I know the webcam on the Ekiga laptop is good - Ekiga gives me a little window to see what the webcam sees and I can watch myself sitting in front of the laptop.  But I am unable to see the webcam video on the other end of the call.  

It behaves this way both when the laptop calls the Tandberg and when the Tandberg calls the laptop.  

How do I debug this?  I can run tcpdump in a window on that Ekiga laptop and I see UDP packets flying back and forth like mad.  Should I forget about 64 bit Ubuntu and use 32 bit instead?  Should I install the latest and greatest Ekiga - and if so, how?

thanks

- Greg Scott

---

