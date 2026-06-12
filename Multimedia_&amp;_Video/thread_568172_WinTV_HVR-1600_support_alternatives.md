---
title: "WinTV HVR-1600 support alternatives?"
date: 2007-10-05
forum: Multimedia &amp; Video
---

### Post by Hopworks on 2007-10-05
This is very frustrating!

I bought a WinTV HVR-1600 and was very anxious to get it into my Linux box and start working on a PVR. It's one of the main reasons I jumped into Linux. Well, Linux offers me a lot more than I ever dreamed anyway so no loss there, but when I put the card in, and started looking at what I had to install, I hit a major brick wall... no driver support for linux for this card. :mad:

I know, I should have researched support for the 1600 before buying it. I apparently overlooked that critical step when I was busy researching card capabilities, comparing features and cost, etc. sigh

It seems the need for linux drivers has been around for awhile, as far back as February of 2007 that I can see, maybe earlier. [http://ubuntuforums.org/showthread.php?t=364085]("http://ubuntuforums.org/showthread.php?t=364085")

That thread eludes to the fact that support usually takes about four months. It's been almost eight months since that thread started, and still no drivers.

So my question finally is... is there a work around or another way to get this card working in my Linux machine? I really DO NOT want to use my windows xp machine and the super crappy hauppauge windows software. I pretty much use my windows machine to play games now, and doing more with my Linux machine. That's the point right? I like Ubuntu Feisty 7.04 so much more. Having to use my Windows machine because hauppauge doesn't feel Linux support isn't important enough to release timely support drivers makes me very ill. :(

---

### Post by lemot66 on 2007-10-08
I'm very glad you brought this topic up!  I am about to purchase a video tuner and now I'm a bit weary of getting the WinTV-HVR-1600 since there is no Linux driver for it yet.  I could alternately get a standard def video tuner (like the Hauppauge WinTV-PVR-500) but there is no HD capability for those PVR cards.  I'm glad you shared your situation - I thank you for that.

Has anyone heard any updates on when this will be supported?? And who would be responsible for writing the driver in the first place?

Thanks,
Thor

---

### Post by Hopworks on 2007-10-08
Thanks to you too lemot66. I was beginning to think I was the only poor bastage that bought that card. Well, actually it looks like I'm still the only one, but it feels good I help keep someone else from making the same mistake I did. Now if I could only get someone responsible for writing the drivers to read this thread and push the issue a little. :)

Hop

EDIT: Hey lemot66, when you pick one and get it up and running, could you let me know what you picked? Just email, or page me on yahoo. I'd appreciate it. I'll keep the 1600 around on my bench in hopes that they do get a driver written, and run a compatible card for now. I figure that is a better approach than doing the winblows thing. Maybe run two in the same linux machine when the drivers are available. I did find some support for the IR blaster and the remote, somewhere. I downloaded the stuff so I'd have it when I do this card.  GOOD LUCK! =)

---

### Post by rstewartmailacct on 2007-10-26
Hi,

This is one of the problems with Linux.  Not enough help to write the drivers and the hardware companies are either too cheap to pay for development or afraid to p$#^@off M$Soft by writing them for the OS.  

I wish someone would get something going on this though because HP is selling these things in their media PCs.  I got two of 'em.  The 1600 is PCI and the 1800 is PCI express.  The came in the boxes so I didn't have a choice and the boxes are soooo cheap now you can't build one for the price of what you get from HP or Dell.  I can say one thing though, I'll never buy a Hauppauge product on my own just because of the pass the buck attitude related to Linux that they seem to have.

The boxes I have are great and everything works with Gutsy but the tuner cards only work with Vista, yuk!

Keep responses coming on this and maybe a driver will come  Meanwhile I'm learning to live with Vista.

;-)
:lolflag:

---

### Post by Hopworks on 2007-10-28
> **rstewartmailacct said:**
> Hi,

This is one of the problems with Linux.  Not enough help to write the drivers and the hardware companies are either too cheap to pay for development or afraid to p$#^@off M$Soft by writing them for the OS.  

I wish someone would get something going on this though because HP is selling these things in their media PCs.  I got two of 'em.  The 1600 is PCI and the 1800 is PCI express.  The came in the boxes so I didn't have a choice and the boxes are soooo cheap now you can't build one for the price of what you get from HP or Dell.  I can say one thing though, I'll never buy a Hauppauge product on my own just because of the pass the buck attitude related to Linux that they seem to have.

The boxes I have are great and everything works with Gutsy but the tuner cards only work with Vista, yuk!

Keep responses coming on this and maybe a driver will come  Meanwhile I'm learning to live with Vista.

;-)
:lolflag:
Yeah, I agree, although I did write a fairly nasty email to Hauppauge and did get phone call and a few emails. There is still no driver support, but the tech that emailed me said he would send my concerns up to those writing it and get back to me if there was anything about an ETA. That was the last time I heard from him. :-k

I bought a PVR-150 after reading posts here and talking with a few forum members and it is working great with MythTV, except it didn't come with a remote or IR device. My 1600 did though, but now there are more disappointments. 

The remote, receiver, and 'IR Blaster' that came with my 1600 is for Vista only. After researching the receiver device, SMK Model RXX6000-0141E and the remote, RRS9002-86XXF, I found that there is limited support for the devices that allow the remote to be used, according to this [COLOR="Blue"]_[link]("http://www.mythtv.org/wiki/index.php/MCE_Remote")_[/COLOR] (my remote is the black one on the right), but not the IR Blaster. After another email to Hauppauge, they offered to swap the devices for supported ones which is fine, and I'm about to do that. I would rather keep them though if someone can post here that has those and is using them with MythTV. The most important thing about these devices for me is the IR Blaster, since I have to use my cable box to tune, and MythTV needs to be able to change the channel on the box to be fully functional.

---

### Post by houstonbofh on 2008-02-10
I saw one of these at the CompUSA everything must sell, even the paint on the walls deal for $65..  Glad I checked first.  I just need to buy the more expensive Linux supported cards.  Life is too short for unsupported hardware.

---

### Post by bdtgp on 2008-02-11
There is a beta driver with directions on the Hauppauge support page for the 1600.  I have the driver installed and i can run 

```
 cat /dev/video0 > /home/brett/Desktop/test.mpg
```

After waiting a few seconds you can watch what you recorded.  This has basically no benefit since the card isn't yet supported in MythTV or tvTime from what I can tell.  But if you want to be able to watch a recording of a channel that you can't select, run that command after installing the driver only with your username instead of "brett"

---

### Post by houstonbofh on 2008-02-11
I can get a cheap vidcap board from China for $7, with 4 ports...  And the drivers for this haven't moved on 6 months. [www.pchdtv.com](www.pchdtv.com) for me.  Support Linux hardware vendors.

---

### Post by Hopworks on 2008-02-13
> **bdtgp said:**
> There is a beta driver with directions on the Hauppauge support page for the 1600.  I have the driver installed and i can run 

```
 cat /dev/video0 > /home/brett/Desktop/test.mpg
```

After waiting a few seconds you can watch what you recorded.  This has basically no benefit since the card isn't yet supported in MythTV or tvTime from what I can tell.  But if you want to be able to watch a recording of a channel that you can't select, run that command after installing the driver only with your username instead of "brett"

Wow! A beta finally, that's at least progress! Maybe they'll have working release by the time this technology is integrated into motherboards. ](*,)

Seriously though, thanks for the heads-up. I'll hold off until they offer more functionality with the card, since I already have a PVR-150 in there that does analog.

---

### Post by irwinr on 2008-04-28
I'm in the same boat, I've got an HVR-1800 which is basically a very expensive paperweight.  I've tried installing the cx18 drivers linked on Hauppage's driver page with no luck.

Does anyone have any updated information on this issue?

-Jeremy

---

