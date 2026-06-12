---
title: "NVIDIA meltdown...."
date: 2008-07-29
forum: Mythbuntu
---

### Post by DadAgain on 2008-07-29
So everything was working pretty good - 

I only had 1 out 4 DVB tuners working and couldnt get my listings to show  but everything else was good:

1080p output - check
DVD ripping - check
Music playing - check
VNC working - check
Samba shares setup - check...

So I spent a day copying my data back into place confident that the tuner problems would soon get sorted out and I'd be back to a fully functional mythbox.... Today the wife got a stack of DVDs form the rental place with the expectation of watching them over the coming week.... so I started my ripping....

I explored the tuners a bit futher and noticed a card was lose - so I pushed it firmly into place and the box seized...

on reboot I get a nasty message:

"Your screen and graphics card could not be detected correctly. To use higher resolutions, visual effects or multiple screens you have to configure the display yourself" - and I'm forced to run in 640x480 resolution (real ugly on a 46" screen)

I've tried reinstalling the latest NVIDIA drivers and the install runs ok - but still when I restart X I cnat get any resolution beyond 640x480. The Nvdia driver utility detects my GeeForce6600 card (and the Sony Screen attached to it which it recognises as 1080p)

So what have I done - and how can I undo it? Any thoughts? or do I have to abandon the work done in the last week and start from scratch again with a fresh install?:(

Also noticed on reboot I get a strange set of messages that are tough to read becuase of the overscan I get on the 720p output whilst booting up so I miss2 characters at teh start of each line:
```

  ading, please wait
  int: name_to_dev_t(/dev/disk/by-uuid/6fblahblahblah)=sda(8,5)
  int: trying to resume from /dev/disk/by-uuid/6f00blahblahblah
  int: No resume image, doing normal boot...

```

What does that mean? Have a fried a bit of disk? or is something just out of whack that a magical "rebuild/refresh" command of some description would fix up?

---

### Post by laga on 2008-07-29
I'm not sure if I understand correctly: did you push the tuner into the slot while the box was running?

---

### Post by DadAgain on 2008-07-29
errr... yeah kind of - I was wiggling the antenna cable around to improve my reception and noticed the card move - so I jammed it in properly and it then sat in the PCI slot correctly.

All this was whilst the machine was running... naughty I know...

Is that significant to the symptoms I now have?

---

### Post by agamotto on 2008-07-29
Congrats, you may have just shorted your PCI slots.  Not to be an ***, but you never move anything inside your computer with the power on!!  To be safe, take your system to a local shop and have them check your pci slots and your card/s before you attempt to further tinker with your system.

---

### Post by DadAgain on 2008-07-29
> **agamotto said:**
> Congrats, you may have just shorted your PCI slots.  Not to be an ***, but you never move anything inside your computer with the power on!!  To be safe, take your system to a local shop and have them check your pci slots and your card/s before you attempt to further tinker with your system.

Surely if I'd shorted a PCI slot wouldnt I have compelte failure? i.e. no output from video card - or non-functioning tuner?

I *do* get output from the video card - its just default 640x480 and not using nvidia drivers properly.

..and my DVB-T card works perfectly...


In fact if I ignore the fact that MythTV resolution is 'fugly' the rest of my functionality is bearable.

I think I'll plop in a different disk and go the full reinstall on that to see if I can verify whether or not I have some kind of borked hardware now!

---

### Post by Lester_Burnham on 2008-07-30
Can you change the resolution once it's started with "sudo nvidia-settings" in a terminal. That is if you can read it.

---

### Post by DadAgain on 2008-07-30
whatever happened it doesnt matter now!

I rebuilt on a fresh drive I had lying around and everything came up clean (much cleaner and uicker than original install).

So I'm happy - 2 hours in now and stuck waiting for me to copy tonnes of content from one disk to another....

Only thing I havent got working is shepherd tv listings grabber which should be straightforward and and to remap a few keys so my remote works then its ALL sweet! 

(Good lesson though - dont dick around with PCI cards whilst machine is running!!)

:)

---

### Post by EthanMN on 2008-07-30
ok ok you got the lectures. As an aside, people should be especially careful using low profile cards that lack screw-down backplates. Many use the retaining bracket and torsion from video cables can cause them to pop out of the slot while running. Bad!

---

