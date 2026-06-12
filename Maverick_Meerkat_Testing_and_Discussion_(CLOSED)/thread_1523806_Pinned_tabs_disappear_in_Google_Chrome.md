---
title: "Pinned tabs disappear in Google Chrome"
date: 2010-07-04
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by RTrev on 2010-07-04
I've been using Google Chrome Unstable, and the pinned tabs are now invisible.  They still work, and space is allocated for them, but they don't show up.

Seemingly related is that the "Favicons" for each page now flicker wildly while the page is loading or reloading.

This change occurred somewhere during the most recent updates, but I'm not sure exactly when.

Anyone else?  Suggestions?

---

### Post by maniandram on 2010-07-04
Which site?

---

### Post by RTrev on 2010-07-04
> **maniandram said:**
> Which site?

It's not related to any specific site.  All sites do it.  Just pin any tab, and some space will open up on the left of the tab bar, and hovering your mouse over it will show the name of the site as usual.  It's just that the pinned tab isn't visible.

Same version of Chrome under Lucid does *not* do this.

---

### Post by hrhnick on 2010-07-04
same issues here. the flickering is really annoying.

google chrome unstable.

---

### Post by nilarimogard on 2010-07-04
> **RTrev said:**
> I've been using Google Chrome Unstable, and the pinned tabs are now invisible.  They still work, and space is allocated for them, but they don't show up.

Seemingly related is that the "Favicons" for each page now flicker wildly while the page is loading or reloading.

This change occurred somewhere during the most recent updates, but I'm not sure exactly when.

Anyone else?  Suggestions?

They keep adding/removing this feature. A while back they removed the "Pin tab" option altogether. That's why it's a development build, because it quickly gains and loses features...

---

### Post by krishnandu.sarkar on 2010-07-04
Google Chrome has released an Stable version. Why don't you upgrade to it??

---

### Post by nilarimogard on 2010-07-04
> **krishnandu.sarkar said:**
> Google Chrome has released an Stable version. Why don't you upgrade to it??

That's basically a downgrade :D

---

### Post by RTrev on 2010-07-04
> **nilarimogard said:**
> That's basically a downgrade :D

Precisely. <g>

Let me try to be more clear.  The problem is with Maverick, not with Chrome/Chromium.

I've tried various versions of both Chromium and Chrome, and of those which do have the "Pinned Tab" feature it works fine *except* under Maverick.

I just installed plain old chromium-browser from the repository to double-check this, and it does the same thing.

Open any page, then right-click on the tab and choose "Pin Tab".  It works, but all you see to the left, where the pinned tabs go, is some empty space open up.  Hover the mouse pointer over it, and it will give you the page title.  Click on it, and it will take you to the page.  It works fine, it's just *invisible*. <g>

Now, simultaneous with this breakage, page loads and reloads cause the Favicon to flicker wildly until the load is complete.

I suspect, but don't know, that these two anomalies are related.

I've ruled out that it has anything to do with the "unclutter" which is causing people issues with the mouse pointer.

So, again, this only happens under Maverick, and only with a recent update of something.. which unfortunately I can't put my finger on.

BTW, Google's "unstable" code is what most companies would call "Release Candidate" code.  How many years did they keep Gmail in "beta"? :D

---

### Post by Naddiseo on 2010-07-04
> page loads and reloads cause the Favicon to flicker wildly until the load is complete.


I noticed this too. It started around the same time unclutter was installed, but I also don't believe that to be the problem. Could you report on launchpad so I can subscribe :)

---

### Post by RTrev on 2010-07-04
> **Naddiseo said:**
> I noticed this too. It started around the same time unclutter was installed, but I also don't believe that to be the problem. Could you report on launchpad so I can subscribe :)

Well, what I was leading up to was trying to find out if this was a known bug, and, if not, how it should be reported? ;)

I have no idea what part of Maverick is to blame, and as far as I can tell there's nothing wrong with Chromium/Chrome.

Can someone give me a pointer on how to best initiate a bug report on this?

---

### Post by RTrev on 2010-07-04
Ah, I was looking around, and it appears it's already been reported:

[https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/601494](https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/601494)

---

### Post by hugmenot on 2010-07-05
For me some of the tabs disappear as soon as there are too many open. I don’t use pinned tabs. Just open many normal tabs.

---

