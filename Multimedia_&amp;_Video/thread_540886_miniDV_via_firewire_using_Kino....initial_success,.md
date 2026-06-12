---
title: "miniDV via firewire using Kino....initial success, then failed"
date: 2007-09-02
forum: Multimedia &amp; Video
---

### Post by biomedtech on 2007-09-02
I read a couple of other 'closed'  threads, so I cannot ask questions there.  In my case there is a twist. 

My firewire is not built-in, but I had a CompUSA f/w card that is listed here at this url.

[http://www.linux1394.org/hcl.php?class_id=2](http://www.linux1394.org/hcl.php?class_id=2)

I was very relieved that my miniDV camcorder's image popped right up
in the Kino application.  I did not have control over the transport, but 
I was able to capture both Camera and Tape footage flawlessly. 

Then I shut down my pc for the evening. The next day, Kino gave me this warning. 

WARNING: raw1394 kernel module not loaded or failure to read/write /dev/dv1394/0

How could this work initially, then not at all? What output can I post here, that may
help explain what happened? Thank you.

---

### Post by Amazona aestiva on 2007-09-02
Connect Your camera then type
```
sudo chown * /dev/dv1394/0
```
[COLOR="Red"]replace * with your user name.[/COLOR]
And see the first link in my signature.

---

### Post by OsakaWilson on 2007-09-10
chown: cannot access `/dev/dv1394/0': No such file or directory

---

### Post by Amazona aestiva on 2007-09-10
Now a better solution:
1. Connect the camera.

2.
a) [COLOR="DarkOrange"]I use this but you might need...[/COLOR]
```
sudo chown 666 /dev/raw1394
```

or

b) [COLOR="DarkOrange"]... this.[/COLOR]
```
sudo chown 666 /dev/dv1394/0
```

---

### Post by rafttrip on 2008-06-25
I get the same warning but my DV camera has not worked yet.

I have a laptop with built in firewire....I have a Sony Vaio VGN-CR125E

Any help would be grate.:)

---

### Post by timcredible on 2008-06-25
that error message sounds like the firewire module didn't get loaded.  you may need to add the load command to /etc/rc.local (I think that's the file, it's been quite a while since i've had firewire issues on a distro).  do a search for modprobe 1394 to find more info.

---

