---
title: "RStudio &amp; MATE 16.10"
date: 2016-10-16
forum: Multimedia Software
---

### Post by RichardET on 2016-10-16
I upgraded to 16.10 but, alas, RStudio is now broken.  I am loathe to switch back to 16.04, perhaps I should try another R GUI ?  It's a pity, because RStudio is really super.

The above upgrade was on my travel netbook;  my desktop is still version 16.04 and given my desire to use RStudio, will not be upgraded anytime soon.

---

### Post by monkeybrain20122 on 2016-10-17
It is because rstudio depends on  gstreamer-0.1.0 but it is deprecated in 16.10,  see [here.]("https://bugs.launchpad.net/ubuntu/+source/gst-plugins-good0.10/+bug/1575496")  It is annoying but can be easily fixed. Just need to grab the two missing packages from xenial's repo. For details ee my comment [here]("https://support.rstudio.com/hc/en-us/community/posts/221967507-Not-installing-in-Ubuntu-16-10"). I have filed a bug at rstudio's forum. It has not been approved by the moderator yet.  Once it is I will post a link here maybe you can add an affect me too or something to the effect.

P.S. shouldn't have rushed to upgrade. :) I am sticking to 16.04 for a while. It is the best release for me so far (Screenshot is from a test 16.10 install on a damaged laptop that I don't use)

P.P.S This should really be a support thread since there is a solution. :)

---

### Post by Bucky Ball on 2016-10-17
*Moved to **Multimedia Software**.*

Presume you *are* looking for support and not just wanting a chat. If so, best to post in a support area ...

> **monkeybrain20122 said:**
> P.S. shouldn't have rushed to upgrade. :)

Best to wait a month or six and by then it is almost EOL (interim releases are supported for nine months). Often wonder why people rush for the latest (which is generally not always the greatest) when the OS they are running is supported for five years and working perfectly ... :-k

I generally install new releases on a separate partition or as a virtual machine and fiddle with them if I'm curious. Stick to LTS releases myself. Haven't got the time or inclination to be reinstalling and reconfiguring every six months.

---

### Post by monkeybrain20122 on 2016-10-17
Actually Rstudio is not a multimedia software, it is an IDE for the statistical/data mining software R, so it is more of an application for development, even though it for some reasons requires gstreamer. :)

---

### Post by Bucky Ball on 2016-10-17
Apologies, my mistake. In that case ... 

*Thread moved to **General Help**.*

---

### Post by RichardET on 2016-10-17
I know.  I know.  my bad.

---

### Post by monkeybrain20122 on 2016-10-17
They told me that they have already switched to gstreamer-1.0 in the developmental branch. If you don't want to install gstream-0.1.0 from xenia you can get Rstudio 1.0.102 or higher from [here]("https://dailies.rstudio.com/rstudio/ubuntu/amd64/") (actually 1.0.102 seems to be the highest) It should install in 16.10.

---

### Post by RichardET on 2016-10-17
it took a couple hours, but I reverted back to 16.04;   All's well that ends well!

---

