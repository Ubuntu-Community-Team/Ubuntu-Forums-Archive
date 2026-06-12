---
title: "[Hardy] no nvidia support on older kernel 2.6.22.14"
date: 2008-05-05
forum: Multimedia Software
---

### Post by angryforumreader on 2008-05-05
Hi all I've recently notice that hardy hang/freezes up randomly I myself had gone through at least 4 of that. The whole screen just locks up mouse unmovable and nothing works except to do a hard reboot.

I was planning to go back to an older kernel 2.6.22.14 instead of the new one 2.6.24.16 hoping to avoid that freeze up problem.

On Hardy 2.6.22.14 the nvidia restricted driver 169.12 claims to be working (meaning it is ticked and in use) but everything is showing in low resolution. Highest resolution is 800 x 600. So far I have tried doing 

sudo dpkg-reconfigure -phigh xserver-xorg
and
sudo nvidia-xconfig

after using these commands and rebooting it still shows up low resolution. Always when it starts it complains about not being able to detect my screen and graphics card and ask me to configure it.

I have no trouble in 2.6.24.16 the newest kernel on my box now. Nvidia driver is working fine. But as I mentioned I wanted to shift to another kernel hoping to avoid the freeze problem. So anyone has any idea how to get nvidia driver working on older kernel such as 2.6.22.14?

I noticed that there seems to be 2 sets of restricted module for the new and old kernel in the synaptic. But theres only one version of the nvidia driver that is nvidia-glx-new for the new kernel. So I'm thinking that is the reason why it is not working. The only available nvidia-glx-new (169.12 + 2.6.24.12-16.34)restricted nvidia driver is for the new module. So is there a way i can get the nvidia-glx-new for the old kernel of mine (2.6.22.14).

Either I find a solution for this or the freeze up problem get solved very soon. Definitely unacceptable how Hardy freeze up randomly and unexpectedly.

---

### Post by Zorael on 2008-05-05
You can download a driver off of Nvidia's site. The installer should compile a driver kernel for you.

As for nvidia-glx, nvidia-glx-new and nvidia-glx-legacy, these are different driver versions, with which a given videocard may only work with one or two. Please see [http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html](http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html).

---

### Post by James_mtl on 2008-05-05
I do have the same problem.  I noticed that once in a while I get Xid in dmesg.  Also sometime it freeze completely with just the mouse still working and I have to hard reboot.  Installing 169.12 from Nvidia web site fixed that kind of issues in Gutsy for me.  It is sad that it's still there in Hardy.  I did not try to install the driver from the web site yet but I might give it a try when I have a few hours to spend for the cause !

---

### Post by angryforumreader on 2008-05-05
wow thanks for the reply guys =]. Till now I'm still not sure what is the cause of the freezing up. I just got another 3 freeze when I was playing neverwinter night in 1 hr +. That is seriously bad. I hope the frequency isn't going to be so often.

As for the cause of freeze anyone has any conclusions? Jamesmtl you said that there was similar problem on gutsy. I personally start using gutsy and had been using it without problems like this until I upgraded to hardy. So can I say the problem might have something to do with graphics drivers?

As for the different version of nvidia-glx-new, (to Zorael), I meant that there is a nvidia-glx-new for my newest kernel (2.6.24.16) currently but previously when I was on Gutsy(b4 my conversion to Hardy) the nvidia-glx-new was for (2.6.22.14 and the version was 100+ (can't remember the code))  Now after I upgraded from gutsy to hardy I have 2 kernels but only one newest nvidia-glx-new. I hope they don't clash if I compile another 169.12 driver for my old kernel. And I hope switching to the older kernel might help to avoid the random freeze from hardy

I'll take your advice to compile another nvidia driver on the older kernel Zorael.

Any comments on this issue is welcomed thanks.

---

