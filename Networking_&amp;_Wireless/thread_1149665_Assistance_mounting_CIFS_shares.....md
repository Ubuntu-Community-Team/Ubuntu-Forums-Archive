---
title: "Assistance mounting CIFS shares...."
date: 2009-05-05
forum: Networking &amp; Wireless
---

### Post by tonyps on 2009-05-05
Morning,
I am learning to use this latest version of ubuntu, which by the way, is really a good product.
I cannot seem to make connections to the network shares that I need to use. I would like to do it in a way that makes them easy to get to when I need them!
The shares are cifs enabled on a few of our NetWare 6.5 servers. I frequently accessed them through opensuse 11.0 so I know they work.
Would anyone offer some assistance with how to get this done?

Thanks in advance for the help!

Tony ...

---

### Post by mattgyver83 on 2009-05-08
I dont really think I have enough information to give you an exact answer but you can mount the network drives using 

sudo mkdir /dir/tomount
sudo mount -t cifs //IPPADDR/Share /mount/point

you could have to specify login info

sudo mount -t cifs //IPPADDR/Share /mount/point -ouser=username,pass=password

Maybe? yEs? no?

You will have to mount them each time, or you could add them to fstab to automount each time.

---

