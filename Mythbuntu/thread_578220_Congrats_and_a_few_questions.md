---
title: "Congrats and a few questions"
date: 2007-10-17
forum: Mythbuntu
---

### Post by vv88 on 2007-10-17
Well I've been at MythTV for about 2 years and admittedly found it easier to use another self installer.  Recently I switched to Feisty in order to get a 64 bit system running MythTV and it worked out great.  About a week ago I built a frontend to replace and old existing PC and decided to give MythBuntu another try.  I say "another" because I was scared away while installing an alpha version earlier, but as they say...there's a reason it;s called an alpha version.

You guys did a fabulous job on this distrobution.  Everything that is expected (plus more) is available for configuration on the self installer.  You combine that with a fantastic looking and efficient interface and you have a real contender.

One suggestion I must make is to add an IR blaster to the options in setup (Com1 or Com2).  It's not a huge deal, just takes a little more time to set up and get things right.

Another suggestion would be to offer some sort of alternate cd for partitioning an lvm.  Currently I am running my backend with one drive for recording and the other to store the rest (music, video, etc)  btw, thanks gparted. 

A question for those who are using a wireless frontend to connect to the backend.  I have a very sporadic nfs share set up between pcs and I'm looking for a more efficient way for the two to communicate.  The connection itself is strong and my current settings are taken from the help documentation (feisty)::

```

servername:dir /mntpoint nfs rw,hard,intr 0 0
``` 


A question regarding Linux 64 bit:

I would like to get my DWL-G120 (D-Link) working in 64 bit, but it does not seem to be supported yet.  Does anyone have any information regarding this.  It seems like the issue is similar to that of my FCA202 firewire audio card.  Both are supported in WINDOWS as 32 bit compatible hardware, but neither work (as far as I know)  in 64 bit.

In closing this rather long, drawn out post, I want to say that I appreciate all the hard work you guys put into this project.  Furthermore, I also want to make it clear that I think it's great the way it is.  Take my few suggestions as suggestions and not insults.  Again, great job guys.

---

### Post by superm1 on 2007-10-17
> **vv88 said:**
> Well I've been at MythTV for about 2 years and admittedly found it easier to use another self installer.  Recently I switched to Feisty in order to get a 64 bit system running MythTV and it worked out great.  About a week ago I built a frontend to replace and old existing PC and decided to give MythBuntu another try.  I say "another" because I was scared away while installing an alpha version earlier, but as they say...there's a reason it;s called an alpha version.

You guys did a fabulous job on this distrobution.  Everything that is expected (plus more) is available for configuration on the self installer.  You combine that with a fantastic looking and efficient interface and you have a real contender.

One suggestion I must make is to add an IR blaster to the options in setup (Com1 or Com2).  It's not a huge deal, just takes a little more time to set up and get things right.

Another suggestion would be to offer some sort of alternate cd for partitioning an lvm.  Currently I am running my backend with one drive for recording and the other to store the rest (music, video, etc)  btw, thanks gparted. 

A question for those who are using a wireless frontend to connect to the backend.  I have a very sporadic nfs share set up between pcs and I'm looking for a more efficient way for the two to communicate.  The connection itself is strong and my current settings are taken from the help documentation (feisty)::

```

servername:dir /mntpoint nfs rw,hard,intr 0 0
```
A question regarding Linux 64 bit:

I would like to get my DWL-G120 (D-Link) working in 64 bit, but it does not seem to be supported yet.  Does anyone have any information regarding this.  It seems like the issue is similar to that of my FCA202 firewire audio card.  Both are supported in WINDOWS as 32 bit compatible hardware, but neither work (as far as I know)  in 64 bit.

In closing this rather long, drawn out post, I want to say that I appreciate all the hard work you guys put into this project.  Furthermore, I also want to make it clear that I think it's great the way it is.  Take my few suggestions as suggestions and not insults.  Again, great job guys.

Thanks for all the great feedback.

As per your question, does it work in *64-bit windows* at all?  If so you can likely use the 64 bit windows driver and ndiswrapper.  If not, then i say you're better off with 32 bit.

---

### Post by vv88 on 2007-10-19
As far as I know, no compatible drivers for any 64 bit system (including Windows) have been released.  Although, I read awhile ago that some were making progress using ndiswrapper.  Like you said, it works fine on 32bit.

Any advice on the fstab settings?

---

