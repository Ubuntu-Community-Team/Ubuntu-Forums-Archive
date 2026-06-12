---
title: "ATI vs nVidia new gpu recommendation"
date: 2008-10-01
forum: Multimedia Software
---

### Post by eponymous on 2008-10-01
I've set up the nVidia drivers about a million times on all ubuntu releases since dapper, just from constant tinkering with my media PC.

I'm shopping for a new mobo with onboard graphics, so should I switch to ATI?

If I remember correctly, ATI has open drivers and so I'd assume they're easier to install and display settings can be set through the main ubuntu GUI. But do the drivers support all card features such as 3d, compiz, etc?

This is not a question of what chipset is going to give me the best performance; i'm only concerned with compatibility and ease of installation.

**Short version:** if i'm already acquainted with installing and setting up nVidia drivers is there a reason to switch to ATI?

Specifically, I'm deciding between ATI HD 3200 onboard video and nVidia geforce 8200 onboard video chipsets

---

### Post by lnxnut on 2008-10-01
Back in July I built my boy a nvidia 8200 chipset computer and let me tell you its been nothing less than a nightmare, its probably actually ran right for maybe two weeks the entire time.  It is possible to install the driver in ubuntu however you have to log out of gnome into x to compile the driver, thats why I'm on here now because it quit working and I have to find the guide again.  

Now, let's talk about ATI, last friday I finally got to put my system together, I chose a Biostar Motherboard, actually the TFORCE TA790GX, it has the HD3300 video, which I think is basically same as the 3200, uses the same drivers at least. It had to be the best install I have experienced with new chipsets, everything installed right off the top.  With ubuntu when it says restricted drivers available that installs the video and everything and compiz works great with it. Unbelieveable.  Just in case your wondering I'm not affiliated with ati, biostar, newegg, just someone that has actually experienced both sides of the coin.  Here is a link to the mobo I purchased. [http://www.newegg.com/Product/Product.aspx?Item=N82E16813138128](http://www.newegg.com/Product/Product.aspx?Item=N82E16813138128)

good luck

---

### Post by Yellow Pasque on 2008-10-01
I was not able to get the Catalyst driver working with RadeonHD 3200 with 64-bit Ubuntu (on a Biostar TA780M2+ from newegg :lolflag: ) . Well, the userspace stuff installed, but the kernel module would not build. Same thing on Debian64 Lenny. In fact, I've never successfully gotten Catalyst built on a 64-bit Debian derivative since 8.40.4 back in the Feisty days.

The open-source ATI drivers do not currently have acceleration for the latest cards (though this should change by the end of the year at the latest). I even had to pop in my X300SE to do an Ubuntu Intrepid Alpha 4 install because it included an old release of radeonhd and I had to build the git version myself.

I refuse to buy nvidia products until they release some specs/docs to the open-source community.

---

