---
title: "Module raw1394 not found."
date: 2012-12-20
forum: Multimedia Software
---

### Post by nimraLinx on 2012-12-20
Hello everyone,

I have been trying to get my audio interface (echo audiofire 4 , firewire) working in ubuntu studio, with no luck. I have given root controls to /dev/raw1394 but upon using :

sudo modprobe raw1394

the module does not load and I get 

FATAL: Module raw1394 not found.

any suggestions?

---

### Post by dannyboy79 on 2012-12-20
which version of ubuntu? newer versions don't use that device location  anymore. you can create a symlink to it, check this blog post out
[http://sharpeespace.blogspot.com/2012/06/capturing-firewire-1394-camcorder.html](http://sharpeespace.blogspot.com/2012/06/capturing-firewire-1394-camcorder.html)

---

### Post by nimraLinx on 2012-12-20
> **dannyboy79 said:**
> which version of ubuntu? newer versions don't use that device location  anymore. you can create a symlink to it, check this blog post out
[http://sharpeespace.blogspot.com/2012/06/capturing-firewire-1394-camcorder.html](http://sharpeespace.blogspot.com/2012/06/capturing-firewire-1394-camcorder.html)

Thanks for the answer I tried to make a symlink but got this :

ln: failed to create hard link `/dev/raw1394': File exists

I am using the latest stable( 12.04 )

---

### Post by dannyboy79 on 2012-12-20
it appears like that's already there then. have you checked your /etc/modprobe.d/firewire-blacklist.conf or whatever it's named. I think I uncommented some modules if I recall correctly. I use kdenlive to capture my firewire source.

i too am using 12.04 but with xubuntu

---

### Post by nimraLinx on 2012-12-20
> **dannyboy79 said:**
> it appears like that's already there then. have you checked your /etc/modprobe.d/firewire-blacklist.conf or whatever it's named. I think I uncommented some modules if I recall correctly. I use kdenlive to capture my firewire source.

i too am using 12.04 but with xubuntu

again thanks for the quick answer,

I uncommented everything but still the same msg.

here is the contents of the file: (blacklist-firewire)

blacklist ohci1394
blacklist sbp2
blacklist dv1394
blacklist raw1394
blacklist video1394

blacklist firewire-ohci
blacklist firewire-sbp2

---

### Post by dannyboy79 on 2012-12-20
did you comment out the last 2? then try to restart. also, have you added your user to the video group? what are the permissions of /dev/raw1394?

---

### Post by nimraLinx on 2012-12-22
> **dannyboy79 said:**
> did you comment out the last 2? then try to restart. also, have you added your user to the video group? what are the permissions of /dev/raw1394?

Hi again,

sorry for the late answer and baring with me. 

I just checked the file again, they are uncommented. and here is the permissions of 
/dev/raw1294 :

crwxrwxrwx 2 root root 251, 0 Dec 22 12:49 raw1394

any other ideas what might be going wrong?

---

### Post by dannyboy79 on 2012-12-22
i am using 12.04 and don't use /dev/raw1394 anymore. I use kdenlive to capture firewire so I am not sure where it's grabbing it from but I have
```
crw-rw----+  1 root video   251,   1 Dec 21 18:15 fw1
``` which I believe is where it's grabbing feed from. Did you add your user to the video group?
This is what my blacklist-firewire.conf file looks like
```
blacklist ohci1394
blacklist sbp2
blacklist dv1394
blacklist raw1394
blacklist video1394

#blacklist firewire-ohci
#blacklist firewire-sbp2

```
here's a screen grab of kdenlive capturing firewire from my xbox 360
[IMG]https://lh5.googleusercontent.com/-8-KA7aeIUyY/UNXBSNufoBI/AAAAAAAAA0k/F3Z_YZ6NEt4/s705/kdenlive%2520firewire.png[/IMG]

and here's the relevant dmesg output
```
[    1.620299] firewire_ohci 0000:00:0c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.676106] firewire_ohci: Added fw-ohci device 0000:00:0c.0, OHCI v1.0, 4 IR + 8 IT contexts, quirks 0xb
[    2.176138] firewire_core: created device fw0: GUID 00506256000010be, S400
[    2.176144] firewire_core: phy config: card 0, new root=ffc1, gap_count=5
[    7.267155] firewire_core: created device fw1: GUID 0003f30011806080, S100, 1 config ROM retries

```

---

### Post by nimraLinx on 2012-12-26
ok after a long struggle with device I had to find out that the firmware on the device was outdated and no longer supported by FFADO, I updated it with a MAC machine (shame!)
and now everything goes just fine,

so this is done!

---

### Post by dannyboy79 on 2012-12-26
> **nimraLinx said:**
> ok after a long struggle with device I had to find out that the firmware on the device was outdated and no longer supported by FFADO, I updated it with a MAC machine (shame!)
and now everything goes just fine,

so this is done!

so are you capturing from fw0 or fw1 or did you get /dev/raw1394 back?

---

