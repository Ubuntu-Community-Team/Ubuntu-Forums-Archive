---
title: "Video Card reccomendations?"
date: 2009-01-15
forum: Multimedia Software
---

### Post by DforVendetta on 2009-01-15
I am an Ubuntu 8.10 x64 user of about 3 months. I am searching  the market for a new video card. Being a Linux novice, I would like something easily installed and very linux friendly. I use my computer to watch movies and my geForce 8500gt can't keep up as much as I'd like, even after performance overclocking. 

I play several games but mainly Mass Effect. As many of you probably know, it can be quit challenging for a card such as my geForce. I have a 16x PCI Express port, and would like to spend no more than $150.00 but willing to by used off of Ebay or the like.

Dell Inspiron 530 Q6600 
Intel quadcore 2.4ghz
PCI-E
6 gigs RAM

---

### Post by stefangr1 on 2009-01-15
Only mpeg4 movies can stress a system so much that a system like yours can't keep up with it. 

If you open a terminal while playing a movie and type "top", and then "1" (this will show the load of all cores seperately) you will see that the thread that decodes the mpeg4 stream is close to 100%, this is what causes your problem.

You have a perfect GPU, I assure you that replacing it will help you nothing. At the moment you can do only two things without spending a lot of money: overclocking (I'm not sure if I would do that personally, but I know a Q6600 is very good at it and a lot of people do it) or wait until the NVIDIA VDPAU is finished. The latter will enable to offload mpeg4 decoding to your GPU.

---

### Post by DforVendetta on 2009-01-15
Do you mean overclocking my CPU or my GPU? I have already overclocked my GPU, but I was under the assumption the my quad core would distribute the processing load evenly between the four cores. Is this not the case?

I have never head of NVIDIA VDPAU. What is this?

The "top" command is VERY helpful, as is the rest of your information. I'm very interested and thanks in advance

By the way, I am not using the onboard video. Should I be using it instead?

---

### Post by stefangr1 on 2009-01-15
I mean overclocking your CPU. 

Your GPU is basically doing nothing at all, leaving all the work to the CPU (while almost all mpeg4 movies are encoded in a way that makes multithreaded decoding impossible such that only single core performance counts). Overclocking your GPU won't give you any performance gain.

---

### Post by DforVendetta on 2009-01-15
If I were to overclock one or two cores of my CPU should I expect lockups? Could I permanantly damage my system with minimal overclocking?

---

### Post by stefangr1 on 2009-01-15
You can only over clock all cores simultaneously. 

However, there are special forums dedicated exclusively to over clocking (where your CPU, the Q6600, is actually one of the favorites), so I recommend you to google around a bit if you really plan to over clock. I think chances to damage the hardware are really small, but you can definitely screw up your system good. It might also affect stability (especially if you're overclocking more than a little).

It's an option, but I'm not sure it's a good one and it's definitely suboptimal.

---

### Post by DforVendetta on 2009-01-15
Thanks a lot for your help. I will research the topic well and make a decision. 

Thanks again.

---

