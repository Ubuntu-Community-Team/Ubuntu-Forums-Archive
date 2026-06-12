---
title: "cheese missing: gconfaudiosrc, gconfvideosink"
date: 2011-06-07
forum: Multimedia Software
---

### Post by trash on 2011-06-07
I've never had problems with Cheese and it's been a while since i used it but now when i start it I have no image from cam and cheese gives me this error message. I've searched for said elements but they don't seem to exist.. anybody got a solution? Lucid 2.6.32.32

GStreamer elements are missing: gconfaudiosrc, gconfvideosink

---

### Post by kostkon on 2011-06-07
gst-inspect, i.e.
```
gst-inspect-0.10 gconfaudiosrc
gst-inspect-0.10 gconfvideosink
```
says that these elements are in the gstreamer good plugins package.
Do you have it installed?
```
apt-cache policy gstreamer0.10-plugins-good
```

---

### Post by trash on 2011-06-08
thanks for the quick reply!
seems i do have it installed
gstreamer0.10-plugins-good:
  Installed: 0.10.29-1~lucid1
  Candidate: 0.10.29-1~lucid1
  Version table:
 *** 0.10.29-1~lucid1 0
        500 [http://ppa.launchpad.net/gstreamer-developers/ppa/ubuntu/](http://ppa.launchpad.net/gstreamer-developers/ppa/ubuntu/) lucid/main Packages
        100 /var/lib/dpkg/status
     0.10.21-1ubuntu3 0
        500 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates/main Packages
     0.10.21-1ubuntu2 0
        500 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid/main Packages

and when i do gst-inspect-0.10 gconfaudiosrc
gst-inspect-0.10 gconfvideosink
it tells me No such element or plugin

---

### Post by kostkon on 2011-06-08
> **trash said:**
> Version table:
 *** 0.10.29-1~lucid1 0
        500 [http://ppa.launchpad.net/gstreamer-developers/ppa/ubuntu/](http://ppa.launchpad.net/gstreamer-developers/ppa/ubuntu/) lucid/main Packages
        100 /var/lib/dpkg/status
     0.10.21-1ubuntu3 0
        500 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates/main Packages
     0.10.21-1ubuntu2 0
        500 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid/main Packages
Hmmm, it seems that you have added the gstreamer ppa and thus you have a newer (and different) version of the package than the one offered by the ubuntu repos. The version from the ppa doesn't come with these two elements, for some reason.

---

### Post by trash on 2011-06-08
Oh dear.. there must have been a reason why i did that but I can't recall what it could be. Thanks for pointing that out though, I'll try to figure out why i'm not using the ones in the repos.
Thanks!

---

### Post by kostkon on 2011-06-08
Actually, try giving a
```
apt-cache policy gstreamer0.10-gconf
```

---

### Post by trash on 2011-06-08
and we have a winner!
gstreamer0.10-gconf:
  Installed: (none)
  Candidate: 0.10.29-1~lucid1
  Version table:
     0.10.29-1~lucid1 0
        500 [http://ppa.launchpad.net/gstreamer-developers/ppa/ubuntu/](http://ppa.launchpad.net/gstreamer-developers/ppa/ubuntu/) lucid/main Packages

I installed it and sure enough cheese works again.. thanks so much, I don't think i would have found that solution haha:)

---

### Post by janesdaddy on 2011-06-12
I had the same issue. It took me a moment to see the line with 
> Installed: (none)but as soon as I did I ran
```
sudo apt-get install gstreamer0.10-gconf
```and everything was good again. Thanks

---

### Post by basthen on 2011-06-18
yup, that did it for me also. thank you

---

### Post by Paddy Landau on 2011-06-25
It helped me, too, thank you.

Please mark this thread as solved.

---

### Post by trash on 2011-06-26
glad you got helped too, thanks for the reminder:)

> **Paddy Landau said:**
> It helped me, too, thank you.

Please mark this thread as solved.

---

### Post by rajsaluja on 2011-07-27
oh i'm sorry bt when i type the command on the terminal
sudo apt-get install gstreamer0.10-gconf
i get the message 'Couldn't find package gstreamer0.10-gconf'
can anybody help me in tht, i would greatly apprecialte

---

### Post by Paddy Landau on 2011-07-28
> **rajsaluja said:**
> oh i'm sorry bt when i type the command on the terminal
sudo apt-get install gstreamer0.10-gconf
i get the message 'Couldn't find package gstreamer0.10-gconf'
can anybody help me in tht, i would greatly apprecialte
I'm not entirely sure this will help, but try the following commands:
```
sudo add-apt-repository ppa:gstreamer-developers/ppa
sudo apt-get update
```Then try again.

---

### Post by prosist on 2012-01-02
y

---

### Post by prosist on 2012-01-02
> **kostkon said:**
> Actually, try giving a
```
apt-cache policy gstreamer0.10-gconf
```

worked for me on lucid 64. thanks!

---

### Post by txapelgorri on 2012-03-07
Nice answer, works so fine :D

Cheers, Ibon.

---

