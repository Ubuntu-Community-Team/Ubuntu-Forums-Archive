---
title: "Getting gpg key issues -- installing FreeNX repository"
date: 2009-05-13
forum: Networking &amp; Wireless
---

### Post by hansoffate on 2009-05-13
I am trying to follow this guide to install FreeNX on our ubuntu-server system.

[http://bigbrovar.wordpress.com/2009/05/09/login-graphically-to-your-desktop-from-a-remote-location/](http://bigbrovar.wordpress.com/2009/05/09/login-graphically-to-your-desktop-from-a-remote-location/)

However, after adding the respository, and running this command:
```

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2a8e3034d018a4ce

```

it says, gpg: no valid OpenPGP data found.

Any ideas?  Can anyone else add the repository?

Thanks,
-Hans

---

### Post by pro003 on 2009-05-13
you must add repo in your sources list and then add the key.

# sudo gedit /etc/apt/sources.lst

add these two lines if for jaunty

deb [http://ppa.launchpad.net/freenx-team/ubuntu](http://ppa.launchpad.net/freenx-team/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/freenx-team/ubuntu](http://ppa.launchpad.net/freenx-team/ubuntu) jaunty main

save changes

add key 

# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2a8e3034d018a4ce


# sudo apt-get update 
# sudo apt-get install freenx

---

### Post by hansoffate on 2009-05-13
> **pro003 said:**
> you must add repo in your sources list and then add the key.

# sudo gedit /etc/apt/sources.lst

add these two lines if for jaunty

deb [http://ppa.launchpad.net/freenx-team/ubuntu](http://ppa.launchpad.net/freenx-team/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/freenx-team/ubuntu](http://ppa.launchpad.net/freenx-team/ubuntu) jaunty main

save changes

add key 

# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2a8e3034d018a4ce


# sudo apt-get update 
# sudo apt-get install freenx

Yup, I did that.  It turns out our EGRESS rules on our firewall wasn't allowing the correct port to be able to connect to our ubuntu-server.  

For future reference, you need to have port 11371 for tcp and udp traffic open.

---

### Post by pro003 on 2009-05-14
am glad it worked fo you.

have a nice day

---

