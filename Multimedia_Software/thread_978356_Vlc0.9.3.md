---
title: "Vlc0.9.3"
date: 2008-11-11
forum: Multimedia Software
---

### Post by adityabankar on 2008-11-11
Hi All,

I saw that I was not getting vlc0.9.3 as an update for existing vlc on my ubuntu 8.04. I have compiled one and installed. What is the reason for vlc0.9.3 not appearing in online repository of ubuntu?
Can I upload my compiled version so others can directly use it?

Thanks,
Aditya

---

### Post by OrelEagle on 2008-11-11
Hi,

Yes, it's normal. If you check [here]("http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=vlc") you'll see that Hardy uses version 8.6 and Intrepid 0.9.4. If others want to use the new version of VLC I'd rather suggest that they upgrade to Intrepid.

The main reason for not upgrading every piece of software in an Ubuntu version is stability, and it's the "strategy" of Ubuntu: software versions upgrade with the new version of Ubuntu (every 6 months) and in the meantime you only get security updates. Some other Linux distributions offer continuous updates of software, but most of them follow the same idea as Ubuntu.

I would not recommend to upgrade software manually (by compiling it), except if you really need it.

---

### Post by adityabankar on 2008-11-11
Thanks for you explanation :)

---

### Post by WYzzard on 2008-11-18
I repeat the above question at the beginning of thie thread, referencing this item from the VideoLAN wabsite [http://www.videolan.org/]("http://www.videolan.org/") containing this news release 

> End of support for VLC 0.8.6 series

2008-10-26

The VideoLAN team ceases all form of support for VLC media player the 0.8.6-bugfix tree. After several several call for help, it is apparent that there is no interest in the community to maintain the 0.8.6 branch of the VLC media player. As a consequence, it has not been possible to put sufficient efforts to ensure adequate continued quality of the 0.8.6-bugfix branch. Effective immediately, there will be no more security and critical fixes for VLC 0.8.6. Binary releases of the 0.8.6-bugfix branch had already stopped as of July 2008. The VideoLAN team will continue to provide major or security-related bug fixes for the VLC media player 0.9-bugfix branch. If you have not already upgraded to VLC version 0.9.5, please do so urgently (exploits for vulnerabilities found in older versions are widely available as of today).

In light of the fact that Hardy is a(an?) LTS release, it would seem to me that there should be a VLC 0.9x package made available in the Hardy repos. I'm not sure if I have the ability to create a package to submit for inclusion, nor am I sure of where to submit such a package, as I am relatively new to Ubuntu and Linux.

---

