---
title: "songbird + ipod = AHHHHHH!"
date: 2008-10-07
forum: Multimedia Software
---

### Post by Flynn555 on 2008-10-07
can seem to get my ipod photo to work with songbird.  infact songbird doesnt even recognize it :(. i installed the ipod support and still nothing... 

ipod works fine with amarok. just wanted to try something new

---

### Post by blaise69 on 2008-10-14
I also have this problem with a second generation iPod Shuffle, it works fine in Rhythmbox, I have installed Songbird in my /opt directory, is this a bad idea, I once found a post that it may be a permission or Group issue with Songbird, but I have since not been able to find this post, and can't remember how to test any changes

---

### Post by rockstarmode on 2008-12-01
Specifically as it relates to the iPod Photo not working in Songbird ver > 5 they've closed the official bug as WONTFIX

[http://bugzilla.songbirdnest.com/show_bug.cgi?id=9042](http://bugzilla.songbirdnest.com/show_bug.cgi?id=9042)

I opened another bug before I found the above closed one.  It turns out (at least on Fedora 8/9/10 x86_64) that Songbird is happy with the iPod Photo as long as you use the Firewire connector that came with the device.  

[http://bugzilla.songbirdnest.com/show_bug.cgi?id=13545](http://bugzilla.songbirdnest.com/show_bug.cgi?id=13545)

As not all users have firewire this obviously isn't a great solution.  Since firewire works fine with this device and libgpod/amarok/gtkpod have all figured out how to use the iPod Photo over USB it seems that this would be a pretty trivial fix for the Songbird team.  Make some noise and we'll see..

I don't know if this bug applies to the 2nd gen iPod Shuffle

EDIT

The second bug was closed as WONTFIX and this issue was added to the release notes for Songbird 1.0:

[http://wiki.songbirdnest.com/Release_Notes/1.0.0](http://wiki.songbirdnest.com/Release_Notes/1.0.0)

Look under Linux Specific.  I'm happy that the Songbird team got back to me so fast but it's a shame our hardware has been excluded.

---

### Post by Flynn555 on 2008-12-02
i dont think im going to use songbird until it works better with compiz...its so annoying how the window doesnt wobble :(

---

