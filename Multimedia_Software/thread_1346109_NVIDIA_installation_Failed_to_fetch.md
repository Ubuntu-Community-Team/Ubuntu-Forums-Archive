---
title: "NVIDIA installation Failed to fetch"
date: 2009-12-04
forum: Multimedia Software
---

### Post by kordite on 2009-12-04
I've gotten a new PC with a new GeForce 6200 video card and installed an existing Ubuntu 7.10 drive. I am unable to install the NVIDIA drivers.

Attempting to use the Restricted Drivers Manager to install the NVIDIA accelerated graphics driver returns the error:

[FONT="Courier New"]W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.22/nvidia-glx-new_100.14.19+2.6.22.4-16.12_i386.deb](http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.22/nvidia-glx-new_100.14.19+2.6.22.4-16.12_i386.deb)
  404 Not Found[/FONT]

I had this problem previous on another machine and since Envy solved that issue, tried it again here. Downloading envy_0.9.10-0ubuntu10_all.deb and trying to run that threw errors: 

[FONT="Courier New"]Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/linux-libc-dev_2.6.22-16.62_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/linux-libc-dev_2.6.22-16.62_i386.deb) 404 Not Found[/FONT]

And so on. Lots of those.

On advise from the forums and the instruction at [http://www.funnestra.org/ubuntu/gutsy/]("http://www.funnestra.org/ubuntu/gutsy/") I tried [FONT="Courier New"]sudo apt-get install nvidia-glx-new[/FONT] and it threw similar errors. 

I've tried almost all the advise concerning this issue already on the forums and have not gotten it to work. What next?

---

### Post by HappyFeet on 2009-12-04
It won't work because ubuntu 7.10 is no longer supported. That's why it won't fetch anything, because the repos are shut down. Try ubuntu 8.04 or newer.

---

### Post by kordite on 2009-12-05
Well that sort of sucks. I had tried to upgrade some time back from 7 to 8 and it screwed up all sorts of things. Even wiping the drive and trying a fresh install of 8 didn't work right. I ended up going back to 7. A friend of mine, also having problems with updating 7, upgraded to 8 and now can't get some things to work. I also seem to recall problems when I tried to update from 6 to 7.

I don't have these particular problems with v8 on my laptop so I guess but me and my friends are going to have to wipe everything and start with a fresh install of 8 or 9. The upgrades seem to screw things up.

---

