---
title: "Internet connection sharing using SSH"
date: 2009-06-24
forum: Networking &amp; Wireless
---

### Post by roady89 on 2009-06-24
Total newb here, I have been doing lots of reading here and set up and Ubuntu home server and then decided to go full on and install Ubuntu on my laptop. Loving it so far.

My question is: I use an SSH connection to surf the web. I'm wondering how I could set up internet connection sharing and allow PC2 to share the ssh connection that PC1 is using?

I know how to set up internet connection sharing but I don't think the guides show how to do it via SSH.

For example: PC1 has 2 nics, 1 wireless and 1 wired. PC1 is using an SSH connection for internet surfing via wireless. PC2 will use a crossover cable and somehow share the SSH connection with PC1. How would I go about accomplishing my goal? Any tips, help or other are greatly appreciated.

---

### Post by DGortze380 on 2009-06-24
> **roady89 said:**
> Total newb here, I have been doing lots of reading here and set up and Ubuntu home server and then decided to go full on and install Ubuntu on my laptop. Loving it so far.

My question is: I use an SSH connection to surf the web. I'm wondering how I could set up internet connection sharing and allow PC2 to share the ssh connection that PC1 is using?

I know how to set up internet connection sharing but I don't think the guides show how to do it via SSH.

For example: PC1 has 2 nics, 1 wireless and 1 wired. PC1 is using an SSH connection for internet surfing via wireless. PC2 will use a crossover cable and somehow share the SSH connection with PC1. How would I go about accomplishing my goal? Any tips, help or other are greatly appreciated.

I'd like to help, but am a little confused (actually, I think you may be a little confused) ... how exactly are you using ssh as an internet connection? Do you mean you use a proxy?

---

### Post by roady89 on 2009-06-24
LOL! Yes, its me whose confused. I proxy through an SSH connection. I was wondering how I could share that proxy connection using internet connection sharing....or if its even possible.

---

### Post by DGortze380 on 2009-06-24
This should get you started: [http://ubuntuforums.org/showthread.php?p=6060607](http://ubuntuforums.org/showthread.php?p=6060607)

It shouldn't make any difference how your current connection is configured. If your proxy is set-up and working correctly for a given interface, you should be able to set up your Ubuntu machine as a gateway for other computers through a second interface.

---

