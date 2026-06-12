---
title: "Resolution for Atheros Chipset Users, who after a upgrading Kubuntu, Wireless Non Fun"
date: 2008-12-15
forum: Networking &amp; Wireless
---

### Post by ellannjohnson on 2008-12-15
Hi,
I am posting to help anyone with Atheros chipset. I know there are so many bugs and complaints pertaining to this wireless card. i thought I would share my experience to help all those in need, and unable to find a resolution.

After hell and high water getting my Atheros card to work on a fresh install of Kubuntu, I updated my system to the latest Kubuntu release.

Then it hit. No more wireless!!!! Again!!! After all that!!!! (Pulling hair out starts, now).

Well I found a solution: [http://unsharptech.com/2008/10/31/atheros-wireless-in-ubuntu-810-intrepid-ibex/comment-page-1/#comment-65](http://unsharptech.com/2008/10/31/atheros-wireless-in-ubuntu-810-intrepid-ibex/comment-page-1/#comment-65).

After using the instructions in this post, my wireless still did not work until I ran 

Code:
sudo modprobe ath5k

Like magic there it was.  My card was activated, and network manager was recognizing my wireless again.

But I have one small itsy bitsy problem. I have to run sudo modprobe ath5k after every reboot. How can I get this to load correctly on its own at start up?

Thanx in advance. I hop my post can keep someone else involved in the Ubuntu Revolution. Fight, the MS power!

---

