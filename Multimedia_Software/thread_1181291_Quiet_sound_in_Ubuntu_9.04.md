---
title: "Quiet sound in Ubuntu 9.04"
date: 2009-06-07
forum: Multimedia Software
---

### Post by miocene on 2009-06-07
I am running my pc's sound output thorugh a 100Watt AV receiver which is usually ridiculously loud but it is coming out very quiet through Ubuntu and I need to put the volume over half to get a decent level...
Sound is much louder in Windows 7,
Here is a ss of my sound settings:

[IMG]http://i41.tinypic.com/auavt5.png[/IMG]

Any recommendations of how to get a decent level without pumping my amp up so high? it's only a matter of time before I switch the source to something else forgetting to turn the amp down and deafen myself

---

### Post by tolotos on 2009-06-08
i would suggest taking a look at the volume levels in alsa. Although you are using Pulsaudio, you can still influence the volumes by alsa. The easiest way to change the levels is to type "alsamixer" in terminal. Then look for something like "Analog F" or whathever channel you have plugged your receiver to. 
Hope that helps a bit.

---

### Post by caver1 on 2009-06-08
First thing I would do is open Volume control and see where
levels are set.
Right click the speaker on your top panel.
caver1

---

