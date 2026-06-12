---
title: "Thoughts on a new USB IR Receiver/Blaster"
date: 2010-11-06
forum: Mythbuntu
---

### Post by tzoom84 on 2010-11-06
Hey all, 

I'm having a heck of a time getting my PVR-150 remote, blaster, and IR receiver working with LIRC in my new install of mythbuntu 10.10. So I decided to just pick up a new USB based receiver/blaster.

Now in the past this PVR150 receiver/blaster has given me a heck of a lot of trouble under a different distribution (Knoppmyth). So I'd prefer the easiest to set up IR device as possible.

It seems from some older (2007/2008) posts, the "mceusb2" was a common option:
1) Do these come with an IR BLASTER as well?
2) Which models are mceusb? i.e. where's a good place to buy?

Otherwise, any recommendations on any others, or potentially new or recent products?

Thanks!

---

### Post by Meph1st0 on 2010-11-06
I've always had pretty good success with any of the media center edition remotes.  They all usually work out of the box and they're usually pretty cheap.  The one I have is a SIIG Generic Vista MCE remote. [http://www.siig.com/ViewProduct.aspx?pn=CE-000022-S1](http://www.siig.com/ViewProduct.aspx?pn=CE-000022-S1)

One thing though; now that you've upgraded to 10.10, you'll have to follow this thread to get it working: [http://ubuntuforums.org/showthread.php?p=9984844#post9984844](http://ubuntuforums.org/showthread.php?p=9984844#post9984844)

---

### Post by tzoom84 on 2010-11-06
Thanks Meph1st0. Do you have a recommendation for an IR blaster? Need to control that cable box ...

---

### Post by klc5555 on 2010-11-06
> **tzoom84 said:**
> Thanks Meph1st0. Do you have a recommendation for an IR blaster? Need to control that cable box ...

The only USB blaster I've found that was reasonably trouble-free for me (or actually worked) was the IguanaIR, one of which I use on a Mythbuntu box, and another on a Slackware one. 

The only slight quirk I had was that Ubuntu 9.10 inexplicably didn't include the IguanaIR module in their version of lirc 0.8.6. (Though this may have since changed). As the standard compiling of source from lirc.org (which _does_ include the module) tends to put the files into the wrong directories from a Ubuntu perspective, the easiest thing to do with the IguanaIR was to use IguanaIR's own supplied .deb for lirc 0.8.6 instead of Mythbuntu's, and then the IguanaIR configured and fired right up.

---

### Post by tzoom84 on 2010-11-11
Just wanted to follow up on this. I picked up a MCE remote (Model VRC-1100) from a seller named gigacity on ebay for pretty cheap.

To my ABSOLUTE surprise, the thing worked immediately OUT OF THE BOX, no configuration required! I say to my surprise before because of past experiences of hours of frustrating lirc and hardware device configuration.  Amazing!

So now I'll have to pick up an IR blaster. Thanks for the tips all and klc5555 I'll probably take your advice on that IguanaIR.

---

