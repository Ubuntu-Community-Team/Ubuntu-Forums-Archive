---
title: "mythbuntu alpha questions"
date: 2007-07-05
forum: Multimedia &amp; Video
---

### Post by toecutter on 2007-07-05
I've got several components for a media PC on the way and want to use Mythbuntu for my MythTV setup. I don't mind using an alpha release but since I'm relatively new to the Linux scene and meda PC's in particular I've got a couple of questions:

1. I'm assuming that Mythbuntu can do everything that 'regular' MythTV can do, like play ROM emulators, do news feeds, etc., is this correct?
2. the big question - since I don't do regular installs and re-installs of my Ubuntu stuff (just have one machine running it at the moment) I just need to know how this alpha release thing works. I install the current version and when a new version comes out I just install over it? Or is it more complicated than that? Are there any issues to resolve along the way, like dealing with settings? **I see from the mythbuntu site that it's just a matter of doing 'sudo apt-get upgrade' so that should answer this question**
3. Assuming it IS just as simple as installing over the old version, what sort of partition setup do I need? Should I make separate /home and other partitions? I have a separate /home partition on my daily/gaming computer so future upgrades will be theoretically painless, that's why I have this assumption. 
4. What is hardware setup and detection like in the new alpha version? I don't have PVR-xxx like most MythTV devotees use, I have a different Hauppage card (Nova T-500) that apparently has slightly different parameters and requirements, but I'm assured this will work fine.

That's all I've got for now, I'm sure more will come after I build the machine up! :)

---

### Post by toecutter on 2007-07-12
bump...

I'm getting my case, m/b and RAM today, so really need to have some answers before I try installing anything :)

I've edited the questions as I've found out a bit more info as well.

How do I add tags to a thread? I wasn't given the option when I first posted.

---

### Post by toecutter on 2007-07-13
...

I must say I'm pretty disappointed there haven't been any answers to my questions, considering the thread has been around for a week - is there a different forum where the Mythbuntu gurus hang out?

---

### Post by tgm4883 on 2007-07-13
> **toecutter said:**
> I've got several components for a media PC on the way and want to use Mythbuntu for my MythTV setup. I don't mind using an alpha release but since I'm relatively new to the Linux scene and meda PC's in particular I've got a couple of questions:

1. I'm assuming that Mythbuntu can do everything that 'regular' MythTV can do, like play ROM emulators, do news feeds, etc., is this correct?
2. the big question - since I don't do regular installs and re-installs of my Ubuntu stuff (just have one machine running it at the moment) I just need to know how this alpha release thing works. I install the current version and when a new version comes out I just install over it? Or is it more complicated than that? Are there any issues to resolve along the way, like dealing with settings? **I see from the mythbuntu site that it's just a matter of doing 'sudo apt-get upgrade' so that should answer this question**
3. Assuming it IS just as simple as installing over the old version, what sort of partition setup do I need? Should I make separate /home and other partitions? I have a separate /home partition on my daily/gaming computer so future upgrades will be theoretically painless, that's why I have this assumption. 
4. What is hardware setup and detection like in the new alpha version? I don't have PVR-xxx like most MythTV devotees use, I have a different Hauppage card (Nova T-500) that apparently has slightly different parameters and requirements, but I'm assured this will work fine.

That's all I've got for now, I'm sure more will come after I build the machine up! :)

1.  Yes, providing that you install the necessary plugins.

2.  yep, just apt-get upgrade
 
3.  Depends on the type of setup you want.  If it is just a frontend, or a combined frontend/backend, or if you also want a desktop.  How do you want this setup to be?

4.  I'm not sure how the auto detection works, but if it works in regular mythtv, and the auto detection doesn't pick it up, then we could still manually add the card.

I don't think I need to say that as with anything Alpha, breakage can occur

---

### Post by toecutter on 2007-07-16
Thanks very much! :) You've answered just about everything I need to know.

The machine I'm building will be a combined frontend/backend, doing nothing else but MythTV stuff. I might want to do web browsing down the road but first things first, I want to get timed recordings, etc., to function first. 


I see you have MythTV on a 64-bit Feisty system, do you know if it is any different or more difficult than using the Mythbuntu setup?

---

### Post by tgm4883 on 2007-07-16
> **toecutter said:**
> Thanks very much! :) You've answered just about everything I need to know.

The machine I'm building will be a combined frontend/backend, doing nothing else but MythTV stuff. I might want to do web browsing down the road but first things first, I want to get timed recordings, etc., to function first. 


I see you have MythTV on a 64-bit Feisty system, do you know if it is any different or more difficult than using the Mythbuntu setup?

This is the mythtv guide.  For partitioning, follow this.
[https://help.ubuntu.com/community/MythTV](https://help.ubuntu.com/community/MythTV)

As for using Mythbuntu over Feisty with Mythtv.  It should be easier to setup Mythbuntu (as that is what it is designed for).  Just remember that Mythbuntu is still alpha (as is gutsy, which is what Mythbuntu is based on)

---

### Post by toecutter on 2007-07-16
> **tgm4883 said:**
> Just remember that Mythbuntu is still alpha (as is gutsy, which is what Mythbuntu is based on)

Yeah, this is leading me to re-think using Mythbuntu, I'll install Feisty as shown in the MythTV wiki and install Myth from there. 

The only hitch now is the m/b I got is PCI-E only and the nVidia 5200 I have is AGP (oops) so I'll need to pick up a PCI-E card now! Which one of these would you recommend? [http://www.quietpc.com/gb-en-gbp/products/components](http://www.quietpc.com/gb-en-gbp/products/components)

I need S-VHS out at the moment (don't have HDTV yet) but if I'm going to buy new anyway, I'm thinking I may as well get a card which has HDTV-out plug so when I get an HD ready flat screen I don't have to upgrade the internals of the media PC again. 

From what I can gather the DVI plugs can do HD video , so should I go with one of the cards that has these notes:
S-Video Output 
Supports HDTV function with HDTV Cable enclosed

What do you think?

---

### Post by tgm4883 on 2007-07-16
> **toecutter said:**
> Yeah, this is leading me to re-think using Mythbuntu, I'll install Feisty as shown in the MythTV wiki and install Myth from there. 

The only hitch now is the m/b I got is PCI-E only and the nVidia 5200 I have is AGP (oops) so I'll need to pick up a PCI-E card now! Which one of these would you recommend? [http://www.quietpc.com/gb-en-gbp/products/components](http://www.quietpc.com/gb-en-gbp/products/components)

I need S-VHS out at the moment (don't have HDTV yet) but if I'm going to buy new anyway, I'm thinking I may as well get a card which has HDTV-out plug so when I get an HD ready flat screen I don't have to upgrade the internals of the media PC again. 

From what I can gather the DVI plugs can do HD video , so should I go with one of the cards that has these notes:
S-Video Output 
Supports HDTV function with HDTV Cable enclosed

What do you think?

I was using a 7300GS in my Mythbox, worked great and had a dongle that did both Svideo and component out. (as well as VGA out on the card).  Ideally you would want component out, vga, or DVI (or HDMI).  The 7300GS worked great for me.  The only reason I don't use it in my Mythbox anymore is that im instead using the onboard video which is an nVidia 6200.  IMO, I think probably anything > 7600 would be overkill, but thats just me.

---

### Post by toecutter on 2007-07-17
That's excellent advice, I've ordered a fanless MSI 7300GT which should do the business :D

Once I get it I'll get installing!

---

