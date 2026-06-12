---
title: "nvidia from dapper to edgy, no more 1360x768"
date: 2006-10-27
forum: Multimedia &amp; Video
---

### Post by Tasu on 2006-10-27
I have the strange feeling that edgy's not all that on the edge... hmm! I mean: the xserver seems involuted, in dapper, when I installed the nvida closed source drivers, it auto setup 1360x768 as default resolution, I can say it autodetected bcause in the xorg.conf file there was listed 1024x768 as upper resolution, I think thi came from autodetecting modes from the TV and picking up the right one, the best one! Edgy's xserver neither detected the graphic card, nor the monitor, in the xorg.conf there is everything setup like Generic.
Because of this involution I'm now stuck to 1024x768 and even adding the modeline for 1360x768 at 60Hz (and obviously adding it to the possible modes for 24 bit depth) didn't resolved my problem.
This makes me think that xorg not only has lost the autodetection feature present in dapper, but it cannot even handle modelines different from the "standard ones"
I found this bug/problem/involution both upgrading from dapper and reinstalling edgy as a fresh install...
Can't understand how I could get back the proper resolution... and why this happened, I thought established improvementswhere... ehr! established... O_O

---

### Post by tseliot on 2006-10-27
Blame the Nvidia driver, not the Xserver.

Try point 10 of the Problems Section of this guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy#PROBLEMS_SECTION](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy#PROBLEMS_SECTION)

Then if that didn't solve the problem:

Try this guide:
[http://doc.gwos.org/index.php/ChangeResolution](http://doc.gwos.org/index.php/ChangeResolution)


OR this one (read where it says "Getting the Right Mode for an LCD monitor"):
[https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration](https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration)

---

### Post by Tasu on 2006-10-28
Indeed I have to blame nvidia driver, sorry for the rant... =_= I was a bit disappointed and... well! I aimed at the wrong cause! ^_^

Thanx for the howtos, I will try to follow them and will post the results! ^_^

---

