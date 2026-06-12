---
title: "nvidia drivers crashes desktop"
date: 2013-05-11
forum: Multimedia Software
---

### Post by kenha37 on 2013-05-11
I have installed ubuntu on my laptop, but i am having problems with the hdmi port. It doesnt seem to exist.

I have a nvidia gt 415m graphic card and a core i5 which would point at a problem with optimus technology, so i tried to install the new nvidia driver 319, which should help with this problem. The problem is then that the resolution is reduced to 640*480 after reboot, and no desktop is showing. The only solution for this problem i have found i purging the driver again.

This is a general problem for all the drivers i have tried to install from nvidia, so i haven't gotten to trying bumblebee.

Is there some solution which would solve the original problem with the hdmi port? Or just a solution for the problems with the nvidia drivers?

Thanks in advance.

PS. It's an asus u31jg btw.

---

### Post by pogopuschel on 2013-05-11
Your HDMI output is hardwired to your Nvidia GPU. The desktop is running on your intel GPU, which cannot access the HDMI port. Installing any Nvidia driver will fail due to your hybridgraphics when not using bumblebee, which installs the Nvidia driver in a way that does not break the Intel driver. Unfortunately using bumblebee will not make your HDMI work. Best solution -for now- might be using a MiniDisplayPort => HDMI adapter.

---

### Post by kenha37 on 2013-05-11
> **pogopuschel said:**
> Your HDMI output is hardwired to your Nvidia GPU. The desktop is running on your intel GPU, which cannot access the HDMI port. Installing any Nvidia driver will fail due to your hybridgraphics when not using bumblebee, which installs the Nvidia driver in a way that does not break the Intel driver. Unfortunately using bumblebee will not make your HDMI work. Best solution -for now- might be using a MiniDisplayPort => HDMI adapter.

Well that sucks...

Will i gain anything from installing bumblebee then?

---

### Post by pogopuschel on 2013-05-11
Yes, of course. Battery life increases drastically, because bumblebee (exactly bbswitch) turns off your power-sucking Nvidia GPU when not in use. And, you can use the Nvidia GPU if you want.

With the new Nvidia 319.xx it should be possible to use the HDMI output also, btw. Problem is, the whole desktop then runs on the Nvidia GPU, giving worst battery stamina. Since Nvidia's Linux Optimus support just began with 319.xx, I would be patient, maybe there is a solution in the near future.

---

