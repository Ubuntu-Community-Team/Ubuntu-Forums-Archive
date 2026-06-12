---
title: "Access existing logged in session via NX"
date: 2010-06-02
forum: Networking &amp; Wireless
---

### Post by FooAtari on 2010-06-02
I am trying to setup NX to access me home PC remotely from Windows, so far I have been able to login to a new sessions and it worked great. Fast and responsive and very easy to setup.

But...

I want to be able to login to my existing session.  Right now I have Firefox open, Pidgin, Transmission a Terminal window etc etc, that I want to see when I login remotely. I want to login to exactly the same session I am using right now as I would be able to with VNC.

From what I can gather from Google this wasn't possible previously, but, it is now. However I can't get it work.

I install neatx, as per instructions [here]("https://help.ubuntu.com/community/FreeNX") and am running the [NX Client for Windows]("http://www.nomachine.com/select-package-client.php")

So, am I shooting into the wind here trying to login to an existing session with NX? Should I be looking at VNC via SSH or Team Viewer?

---

### Post by venik212 on 2010-06-20
It is called shadowing.  If you click CONFIGURE in the NX client window, you can choose shadow from the left downlist (under Desktop).  There is more information on that here on the forum, but you'll have to dig for it-- I lost the url.

---

