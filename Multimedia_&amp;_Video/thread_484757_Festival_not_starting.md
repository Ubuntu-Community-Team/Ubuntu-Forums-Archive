---
title: "Festival not starting"
date: 2007-06-26
forum: Multimedia &amp; Video
---

### Post by haylocki on 2007-06-26
Hi, 

I am using Ubuntu Feisty, and have been trying to get voice output working with GpsDrive.

I know it works ok because I have had it working before.

typing:
> sudo /etc/init.d/festival start

Produced no output, and the festival daemon did not start

The cure for the problem was to edit the file "/etc/init.d/festival"

and comment out the second line here :

# Comment out the next line to start a Festival server at boot time.
#exit 0

Now typing sudo /etc/init.d/festival start" actually starts the daemon

This means festival starts with the computer on boot, which is not what I wanted, but at least it now works.

Surely there is a better way to stop festival from running on boot. As this method stops the festival daemon from loading at all, it's a pretty pants method.

How is someone new to Ubuntu going to find the solution to this problem ?
And why should I have to edit a /etc/init.d script to get some software to work ?
It's so user unfriendly.

Cheers, Ian

---

