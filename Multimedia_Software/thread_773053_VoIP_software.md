---
title: "VoIP software"
date: 2008-04-28
forum: Multimedia Software
---

### Post by robertsaron on 2008-04-28
What I am looking to do is find some voip software that will allow me to call anywhere in the US. 

My company does a conference call once a week, with our contractor. I could call in on my cell phone, but it does not have a mute button. I would like to be able to call in, listen, then hang up as needed. I need t obe able to hit different combos, like # or *. The conference call lasts about 1.5 hours. I could use my cell phone, but the call happens when i am not at work, and its not worth my time to drive in.

Is there any Voip software for linux that will do this? I currently have wengo and ekiga installed. Are those what I need or is there some thing better? I would also like the ability to dial to cell phones or landlines.:confused:

---

### Post by cb951303 on 2008-04-28
Ekiga is a very very good and stable VoIP software and it has the pc-to-phone service you want but I never used it so I wouldn't know about the service quality

---

### Post by carpy on 2008-08-29
I'm looking for something better than Ekiga.

Ekiga works great... once. 
I've found Ekiga very flaky... quite "stable" as far as crashes are concerned... but it's very easily confused.

I run it on a laptop, arguably the most common configuration.  My laptop runs virtualization software (all my laptops do) which provide their own network interface (vmnet8 for example).  Ekiga constantly "adjusts" to using the vmnet8 interface when the wireless connection goes away (ie. every time I go somewhere).  I have no way to stop that behavior short of hacking the source code and using nonstandard software (I *like* the stability of debs).  Worse yet, I cannot just set it back to use the correct NIC when I get back on a wlan... I have to quit out of Ekiga and restart it.

Another example is when making changes to a SIP account.  No, I don't do this regularly.  But again, I seem to be confusing Ekiga so it cannot register until I quit and restart it.  This is not warm-fuzzy stuff.

Still, it rings me when I get a call, and does the minimal stuff well, so long as I never go offnet.

So, I *like* Ekiga.  But I'm open to alternatives...  Skype works very well but it's not FOSS and I've not found how to do SIP with it.  Gizmo seems to have a pretty interface but I'm not familiar with configuring it and making it work alongside Skype (which is required)

Any other good, solid VOIP software for Linux, I'm open to. (yes, I've filed bug reports)

---

### Post by treesurf on 2008-08-31
Skype is not required to use Gizmo.  Gizmo is a standalone program, and it functions easily and smoothly for me on Ubuntu.  It will do all that you need it to for those conference calls.  You can download a .deb from the Gizmo website here:

[http://download.gizmo5.com/GizmoDownload/gizmo-project_3.1.0.79_libstdc++6_i386.deb](http://download.gizmo5.com/GizmoDownload/gizmo-project_3.1.0.79_libstdc++6_i386.deb)

---

