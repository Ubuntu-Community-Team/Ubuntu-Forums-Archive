---
title: "Installing System Monitor"
date: 2009-12-07
forum: Mythbuntu
---

### Post by Caps18 on 2009-12-07
On my Linux Mint system (Ubuntu), there is a program called System Monitor that tracks CPU, memory usage, and network utilization.  Is there any way to run this program in Mythbuntu, or can I apt-get it?

I just remembered that there is the 'top' command, I'll have to see if that works.

Thanks

---

### Post by matt06 on 2009-12-08
Look in Synaptic for gnome-system-monitor.

---

### Post by stevanbt on 2009-12-09
Hi,
Instead of using 'top' you could use 'htop'.  It'll most likely need installing first:-

```
sudo apt-get install htop
```

Thanks, Steve.

---

### Post by Caps18 on 2009-12-09
> **matt06 said:**
> Look in Synaptic for gnome-system-monitor.

Will this command work:
sudo apt-get install gnome-system-monitor

I'll try that the next time I am on-line with it.

I was able to use top, but I like the htop improvements.  I'll try using that as well.

Thanks

---

### Post by Caps18 on 2009-12-15
> Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main libcairomm-1.0-1 1.2.4-2
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main libglibmm-2.4-1c2a 2.14.0-0ubuntu1
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main libgtkmm-2.4-1c2a 1:2.12.0-0ubuntu1
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main gnome-system-monitor 2.20.1-0ubuntu1
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/main libpcrecpp0 7.4-0ubuntu0.7.10.3
  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/c/cairomm/libcairomm-1.0-1_1.2.4-2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/c/cairomm/libcairomm-1.0-1_1.2.4-2_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/glibmm2.4/libglibmm-2.4-1c2a_2.14.0-0ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/glibmm2.4/libglibmm-2.4-1c2a_2.14.0-0ubuntu1_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gtkmm2.4/libgtkmm-2.4-1c2a_2.12.0-0ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gtkmm2.4/libgtkmm-2.4-1c2a_2.12.0-0ubuntu1_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/p/pcre3/libpcrecpp0_7.4-0ubuntu0.7.10.3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/p/pcre3/libpcrecpp0_7.4-0ubuntu0.7.10.3_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gnome-system-monitor/gnome-system-monitor_2.20.1-0ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gnome-system-monitor/gnome-system-monitor_2.20.1-0ubuntu1_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


I guess there is something blocking that IP address from where I am connecting to the internet.

Top works still to see CPU levels.  I would like the ability to terminate Mythfrontend sometimes without having to use the command line however.

---

