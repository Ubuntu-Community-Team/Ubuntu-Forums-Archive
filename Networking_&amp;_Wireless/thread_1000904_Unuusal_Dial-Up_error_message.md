---
title: "Unuusal Dial-Up error message"
date: 2008-12-03
forum: Networking &amp; Wireless
---

### Post by Trevor4706 on 2008-12-03
I have DSL at home but have dial-up configured on my laptop for use on the road where WiFi or wired connection to the INet is not available.  I also use dial-up all summer long at our cottage where it is the only alternative.  I recently had to do a clean install of Ubuntu 8.10 on my faithful laptop, on which I have successfully used dial-up on versions of Ubuntu from 6.04 forward.  After configuring Gnome PPP as I have in the past I attempted to connect via dial-up.  After my ISP's local dial-up number was dialled and all the hand-shaking had taken place, I see the "Authentication" annunciation and then the dialer disconnects.  The Log says "belotwcnas24 line 168 Unauthorized Access Permitted".  I have checked with my ISP (Bell Sympatico) to find out the significance of the message, but they have no information to offer.  Even more confusing for me is the fact that my wife has an identical laptop running 8.10 and configured for dial-up in exactly the same way, and it connects with no problem.

Do I have some kind of permissions issue here?  Any suggestions greatly appreciated.

---

### Post by jonobr on 2008-12-03
It would be interesting to see the log

Looking at the message you posted I think the ISP should help you more,

Heres what I am guessing at you message you received

belotwcnas24

belotwc Im guessing references a location and service providor (bel(l) (sympatic)o = belo )
The twc could reference a location to identify where the equipment is 
nas24 Im guessing indicates the device you are hitting.
(A nas is a carrier name for a network access server, the device you are hitting which I am guessing has an ID of 24, this could be an identifier which refers to which one you are on)
Im wondering if you are using AOL, if so, its going to be hard for the ISP to help you without going to them as your authentication is done to AOL, not to the local provider.
Again, if its aol, they keep track of service provided to its users by local providers using a token method. AOL used to provide metrics to the provider about their service, and in some cases penalties could be issued to that providor, or they could loose their agreement with AOL. They dont like unhappy customers becuase of the providors messup.

If its not AOL, you ISP should be able to help you more then they are.

What I recommend, try your account on your wifes laptop, (if you havent already.)If that works, post the logs of the PPP session here and there may be other clues. If it doesnt work on your wifes machine, recommend you kick some a and take names at your local ISP.

---

