---
title: "Installing Funplug in Conceptronic CH3HNAS"
date: 2012-05-03
forum: Networking &amp; Wireless
---

### Post by acrocephalus on 2012-05-03
Hello!
I tried to install the package on my NAS CH3HNAS as described in [http://nas-tweaks.net/256/installation-of-the-conceptronic-fun_plug-on-the-conceptronic-ch3hnas/]("http://nas-tweaks.net/256/installation-of-the-conceptronic-fun_plug-on-the-conceptronic-ch3hnas/"), but I didn't succeed. My firmware version is 2.4.9. I download and unpack the files, copying the two at the Public folder of my NAS. Then, I reboot but the NAS hangs and appears a red light in front of it and the webpanel keeps showing a "Loading" message. It seems that it does nothing. Then, if I turn off the NAS and turn on it again, it loads without any problem, but without the funplug installed. I'm working on Ubuntu 11.10 and I run the webpanel on Google Chrome. Could anyone help?
Cheers!

Dani

---

### Post by Ichijoe on 2013-03-04
Thread Resurrection...
The reason it likely don't work is 'cause the DDNC (What I have, and the CH3HNAS (What I turned my crappy Freecom DDNC into), are not really compatible with that version of the Funplug. Ya need to use the One off the Conceptronics Website. and then update it with the hfp package.
[http://http://visscher.dyndns-home.com](http://http://visscher.dyndns-home.com) (sadly at the moment of writing its currently down again). Thankfully it was up a week or so ago.
There you can find copies of Mediatomb and Transmission that just work.

BTW: Did you remember to unpack those Files into your /home/Public Folder?
Unless your Drives gone bad I can't think of a reason why you should have gotten a Red Light. Yeah the housing is a bit different but the DDNC is more or less identical to the CH3HNAS and this has never happened to me. Worse case the NAS would just continue booting and leave the funplug package alone.

---

