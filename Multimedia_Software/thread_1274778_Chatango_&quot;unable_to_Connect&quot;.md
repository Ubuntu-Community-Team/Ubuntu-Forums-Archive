---
title: "Chatango &quot;unable to Connect&quot;"
date: 2009-09-24
forum: Multimedia Software
---

### Post by kwabena77 on 2009-09-24
Hello,

I installed a bunch of restricted extras and installed w64codec for ubuntu 8.04 64.  I did this to get .wmv files working

After I did this, I noticed something:

Chatango no longer works.  The Chatango Window comes up, but all I see is a red button next to "unable to cunnect."

Flash works fine in every other area: youtube, Google video, flash audio players, and so on.

Why won't Chatango work now?  What did installing w64 codecs and ubuntu-restricted-extras do to render me unable to load Chatango?

I have a 64bit machine, running the 64 bit version

---

### Post by earthpigg on 2009-09-24
what is chatango?

---

### Post by kwabena77 on 2009-09-25
Chatango is a Flash-powered, online chat room format, different than IRC.

As an example, here:

[http://www.chatango.com/](http://www.chatango.com/)

An increasing number of Internet radio talk shows are using Chatango for people to interact with the host and with other listeners.

As an example:

Oracle Broadcasting and Revere Radio Network both have Chatango applets embedded in their websites:

[http://mikechamberslive.com/?page_id=19](http://mikechamberslive.com/?page_id=19)

[http://www.revereradio.net/](http://www.revereradio.net/)

---

### Post by earthpigg on 2009-09-25
tried your second link, and it appears to work on 32 bit ubuntu 9.04. made a temporary handle and typed a message. 

have you tried it in any other web browsers to rule out it being a firefox issue?

will try 64 bit arch and 64 bit ubuntu when i get home.

purpose will be to narrow down the possible causes of your issue:

is it all 64 bit distributions of linux?
is it just 64 bit ubuntu?
8.04 64 bit?
your specific system?

if anyone else wants to pop in the thread and tell us if it does/does not work, and what architecture/version of ubuntu they are using, please do.

2nd link the OP posted takes literally about 15 seconds to test.

---

### Post by earthpigg on 2009-09-25
edit - whoops double post

---

### Post by kwabena77 on 2009-09-28
> **earthpigg said:**
> tried your second link, and it appears to work on 32 bit ubuntu 9.04. made a temporary handle and typed a message. 

have you tried it in any other web browsers to rule out it being a firefox issue?

will try 64 bit arch and 64 bit ubuntu when i get home.

purpose will be to narrow down the possible causes of your issue:

is it all 64 bit distributions of linux?
is it just 64 bit ubuntu?
8.04 64 bit?
your specific system?

if anyone else wants to pop in the thread and tell us if it does/does not work, and what architecture/version of ubuntu they are using, please do.

2nd link the OP posted takes literally about 15 seconds to test.

It's just Firefox; on Galeon it works fine.

---

### Post by kwabena77 on 2009-09-28
Hi, I found out what the problem was:

I went and removed the ubuntu-restricted-extras and removed all my flash players, and then installed Flash64 from another Ubuntu thread.  Everything was up and working fine, flash-wise (including Chatango).

So I then went into Synaptic and checked "Ubuntu-restricted-extras" again to look at it more closely.

I noticed that under the additional "to be installed" list was "flash-plugin-non-free"

In other words, when I went and downloaded the Ubuntu-restricted-extras (to get codecs to play .wmv files and so-on,) it *replaced* my working 64-bit flash player with another flash player that sucked.

Does everybody hear that?

On 64-bit Ubuntu, Ubuntu-restricted-extras, or the codecs you need to play Windows media files, and 64-bit flash are MUTUALLY EXCLUSIVE!

It's either-or; you can't have both.  You can't have a working 64-bit flash player AND windows codecs at the same time.  Because the Flash64bit player, the one that works for me anyway, is DIFFERENT than the flash player that Synaptic gives you when you install "ubuntu-restricted-extras"

The Flash Player that worked for me on my 64-bit machine I found here:

[http://ubuntuforums.org/showthread.php?t=1233235](http://ubuntuforums.org/showthread.php?t=1233235)

This Flash Player was tailor-made by JordanL, and it works great.

---

