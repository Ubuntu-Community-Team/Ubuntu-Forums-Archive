---
title: "Mythbuntu Diskless &amp; Media MVP?"
date: 2009-01-02
forum: Mythbuntu
---

### Post by sabhain on 2009-01-02
Can they co-exist?

I've had a MediaMVP on a mythtv system for a while now.  It's installed per the guide documentation found in the following location:

[https://help.ubuntu.com/community/MythTV/MediaMVP_Frontend]("https://help.ubuntu.com/community/MythTV/MediaMVP_Frontend")

They're VERY straightforward and worked like a charm for awhile with no issues.

Now I'm trying to migrate some other front ends to diskless server within Mythbuntu.

My problem now is that mythbuntu diskless server and related packages (tftpd-hpa) seem to conflict with the atftpd package used in the guide for the mvpmc install.

Are the options for the tftpd for mythbuntu-diskless similar to those for atftpd?  I can tweak my settings easily enough, but I'm wondering if these things can peacefully co-exist?

When I try to install atftpd apt-get wants to uninstall mythbuntu-diskless server.  And vice versa.

Anyone encounter this?

Thanks!

---

### Post by NTBlade on 2009-01-15
Hi,
I've found this...
[http://quinnmadson.blogspot.com/2008/07/dual-network-booting-mythbuntu-mediamvp.html](http://quinnmadson.blogspot.com/2008/07/dual-network-booting-mythbuntu-mediamvp.html)
But so far I haven't been able to get it to work.
N

---

### Post by anonymousdog on 2009-01-18
It will most definitely work.

First, install diskless client support and get that running.

Then follow the community doc in the first post but don't install a new tftp server; leave tftpd-hpa in place.  Then, in /etc/inetd.conf copy the tftp line (to a line below) and replace "tftp" with "16869".  Put your dongles, settings and config files in /var/lib/tftpboot.

---

### Post by sabhain on 2009-02-22
Thanks for the reply.

I've tried this suggestion .. but didn't get very far.

One problem I have is that the rc.local is trying to call up a command that doesn't exist on the server .. atftpd ..

These lines were originally added per the documentation.

Are they now extra??

I've tried commenting them out .. but for some reason, mvprelay isn't starting automatically .. and when I start it manually on the commandline .. the mvp never fires.

I'll try this from scratch again in the next week or so .. but curious about the requirements for the first 2 adds to the rc.local file.

Thanks for your help!

---

### Post by NTBlade on 2009-03-04
Hi,
You shouldn't be using aftpd as it conflicts with the diskless tftp server.
Edit >(Oops!  you already know this!)

I'ne manged to get a diskless mythbuntu client booting and moved on the MediaMVP part.

My MVP starts up and gets an IP address, it can see the Mythbuntu server but never uploads dongle.bin

Any suggestions anyone?

Thanks
N

---

