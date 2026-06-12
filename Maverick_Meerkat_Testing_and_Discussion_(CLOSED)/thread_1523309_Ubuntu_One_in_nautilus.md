---
title: "Ubuntu One in nautilus"
date: 2010-07-03
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by MrGreen on 2010-07-03
Hi,

I have updated to Ubuntu 10.10 and nautilus has the Ubuntu One across toolbar [enable] is there a way to remove it?

Thanks

MrG

---

### Post by Perfect Storm on 2010-07-03
Thread moved to Meerkat Testing and Discussion.

---

### Post by gnomeuser on 2010-07-03
Even when you click disable it doesn't go away. It's like a huge banner ad right there in my filebrowser that won't respect a no.

---

### Post by andrewabc on 2010-07-03
I agree. this is very annoying.

I went into system->preferences->startup applications->uncheck ubuntu one.

After a restart it is still asking in nautilus.

I don't think people with low res screens (netbooks/laptops) would appreciate a big space being taken up by ubuntu one asking if they want to enable/disable it.

Does someone with 10.10 in front of them want to take a screenshot for others to see, and explain what happens if you click enable/disable button?

---

### Post by Tim Sharitt on 2010-07-03
The toolbar is part of a nautilus extension installed by ubuntuone-client-gnome. Removing this and restarting nautilus will remove the toolbar plus any other integration with gnome (context menu entries, etc).

Remove ubuntuone-client-gnome:
```
sudo apt-get purge ubuntuone-client-gnome
```

---

### Post by Mr. Picklesworth on 2010-07-03
That it is present is a bug in the extension. Don't worry.

(If you aren't depending on Maverick, though, it would be helpful if you'd avoid applying a workaround so that it's clear when the problem is fixed).

Edit: I *think* it's a bug in the extension. Thinking about it, it could be a feature that's been implemented in a really ugly way (because Nautilus is ugly) and my suggestion to relax and ignore it would then be a poor approach. Has anyone filed a bug report on this one?

---

### Post by mc4man on 2010-07-03
> That it is present is a bug in the extension
Have been using ubuntu one and it actually seems  handy to add (enable) or remove (disable) dir.'s. 

Atm don't see anything in the r. click menu to replace it. (or anything for ubuntu one at all..

---

### Post by Tim Sharitt on 2010-07-03
> **Mr. Picklesworth said:**
> That it is present is a bug in the extension. Don't worry.

(If you aren't depending on Maverick, though, it would be helpful if you'd avoid applying a workaround so that it's clear when the problem is fixed).

Edit: I *think* it's a bug in the extension. Thinking about it, it could be a feature that's been implemented in a really ugly way. (Ugliness mostly attributable to Nautilus being ugly). Has anyone filed a bug report on this one?

If anything, I'd say that it is an incomplete feature (i.e. no way to enable/disable the toolbar or choose the directories where it is displayed). The question is: are there any plans to do anything about it?

---

### Post by cariboo on 2010-07-03
Personally I'd wait until at least **alpha 3** before complaining, things should be sorted by then.

---

### Post by kyleabaker on 2010-07-04
> **Mr. Picklesworth said:**
> Thinking about it, it could be a feature that's been implemented in a really ugly way.

I really hope its less of a feature and more of a bug.

In theory, this would be a very handy and ideal solution to simplifying Ubuntu One. However, the reality of the situation is that this banner uses a lot more space than is actually required and is not (currently) removable.

As has already been mentioned, small screen owners won't appreciate this much. I've held off on reporting it, but seeing this thread leads me to believe that many people will not like this...so it will likely change before Final.

Personally, I find the menu method that Dropbox uses to be sufficient.

I haven't started relying on Ubuntu One like I do Dropbox, but if they would implement it better and bring the web interface up to speed then I would certainly start the switch.

---

### Post by ranch hand on 2010-07-04
I figured it was a feature.  Crude advertising to entice you to hang your personal data out on the web.

Then you should secure your computer of coarse.

Idiosy.

---

### Post by gnomeuser on 2010-07-04
it is a bug that it can't be dismissed as it wastes some of the horizontal space we have been working so hard to gain. It's useful but it should hide itself away nicely.

---

### Post by stevetxt on 2010-07-18
sudo apt-get purge ubuntuone-client-gnome

Thanks for this!  I'm using a netbook and there's no real estate to spare.  The banner in Nautilus for Ubuntu One with no choice given to close it was a bit of a problem.

---

### Post by MarkieB on 2010-08-02
no longer participating in ubuntuforums.org

---

### Post by gnomeuser on 2010-08-02
Similarly it may be useful only to display the sync offer in folders the current subscription supports in terms of size and remaining cloud storage.

Having it offer to sync my 1TB DVD backup folder e.g. isn't even remotely useful.

---

