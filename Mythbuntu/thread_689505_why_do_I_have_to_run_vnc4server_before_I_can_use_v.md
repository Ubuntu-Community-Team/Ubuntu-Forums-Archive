---
title: "why do I have to run vnc4server before I can use vnc?"
date: 2008-02-06
forum: Mythbuntu
---

### Post by onesojourner on 2008-02-06
ok I think I have vnc pretty much set up. The only problem is that I have to run vnc4server in a terminal before I can log on from another machine.

---

### Post by bernied on 2008-02-06
This is the way it is meant to be.
If you want the vnc server to always be running, you can add a command to /etc/rc.local so that it will run at startup.

---

### Post by onesojourner on 2008-02-06
how do I go about doing that?

---

### Post by bernied on 2008-02-06
OK, I'm sorry, I was wrong. It's not quite that simple.
The problem with my idea was that you want the vncserver application to run as a normal user, but the rc scripts run as root. There is probably a way to sort this out, but I don't know it.

But it has been done before - see [here](http://ubuntuforums.org/showthread.php?t=191564).
I'd suggest you read the whole thread before starting, not just the first post, as the howto clearly has some problems which haven't been corrected.

You might also consider [XDMCP](http://happypixels.ca/2006/03/01/using-xdmcp-with-ubuntu-or-any-other-gdm-running-distro/). This might be better for you if both machines are on the same network, and both are running linux.

---

### Post by onesojourner on 2008-02-06
thats wierd. I was using vnc a month ago and it was on at startup. I wish I had paid more attention when I set that up.

---

### Post by superm1 on 2008-02-06
You just need to reboot after installing/configuring in mcc and it should work.

---

### Post by darkazurka on 2008-02-07
I've setup many programs to startup automatically. It's done through a GUI, so that's lucky for us newbies.

Menu: "System"=>"Preferences"=>"Sessions"=>Tab "Startup Programs"=>Click on "Add"=>In the field "Name" put something like ie. vnc4server. 

In the field command put "/usr/bin/vnc4server" (that's the path for me, hope it's the same for you)

There's also a comment field, where you can put anything you like or ie. "virtual network computing server application"

---

