---
title: "Radeon X1200 HDMI Audio"
date: 2010-04-05
forum: Multimedia Software
---

### Post by vccowan on 2010-04-05
Hi I'm new Ubuntu: I want my computer to be used as a DVD/BD player, and as of recently it has rejected its windows install and refuses to reinstall. Ubuntu 9.10 installed without problem, but when I select the X1200 (hdmi) audio output via the top right icon no sound comes out. I've searched this topic and one theory was that if i ran ALSA mixer the x1200 audio might be muted by default; it was not muted. I've also been told to update my catalyst, but using synaptics packet manager to download the catalyst control center, when I run it I get the message no supported hardware found. 
 
Is there any way to get this to work, or am I stuck with my speakers/3.5mm jack?

---

### Post by Mark Phelps on 2010-04-05
Sorry, can't answer the specific question but I can tell you that there is no Catalyst driver that will work with your card and recent versions of Ubuntu.  Don't be tempted to download the driver from ATI or to use EnvyNG to force a driver install.  Either will simply trash your display and leave you without a desktop.

However, the new open source drivers are getting better all the time.  There are rumoured to be some major improvements with 10.04 -- but recent posts on that indicate that something has been broken in recent kernel updates.

So, if I were you, I would wait until 10.04 is releases before upgrading to it -- if you want to do that for driver improvements.

---

