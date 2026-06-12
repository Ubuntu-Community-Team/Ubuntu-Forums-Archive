---
title: "Media Center Hardware Advice"
date: 2011-08-14
forum: Multimedia Software
---

### Post by Dan Again on 2011-08-14
I plan on building a computer to be used as a media center in the near future. I am going to hook the box up to my TV via HDMI and use it to download, store and access media (mainly music and HD video) and also to view streaming HD video from YouTube, Hulu, etc. This is my first try at something like this and I know I have lots to learn. I created the following wish list on NewEgg and am wondering if some people with more experience could chime in.
[LIST]
[*]Rosewill Blackbone Black Steel case ($44.99)
[*]Corsair CMPSU-750TX power supply ($119.99)
[*]Intel i7-2600K 3.4G processor ($314.99)
[*]ASRock Z68 motherboard ($249.99)
[*]G.Skill Ripjaw 8G RAM ($49.99)
[*]EVGA 1G NVidia video card ($189.99)
[*]HT|Omega Claro Plus+ 7.1 sound card ($174.99)
[*]Seagate Barracuda 1T hard drive (2 @ $59.99)
[*]Asus Black Blu-Ray drive ($59.99)
[*]Antec IR receiver and remote ($33.00)
[/LIST]
Am I missing anything? Am I going overboard on anything? On the one hand, I want to get good quality hardware so that my system works well, but on the other hand I'd like to save money where I can. I plan on running stock Ubuntu, but am open to other suggestions.

Thanks in advance!

---

### Post by Dan Again on 2011-08-14
Ooops, realized I forgot...
[LIST]
[*]Intel PCI desktop adapter ($34.99)
[/LIST]

---

### Post by Dan Again on 2011-08-15
Bump. Does anyone with experience have any advice to offer?

---

### Post by Bertrandization on 2011-08-15
I am using xbmc. YMMV for other programs.

1. Although you have it listed, I will emphasize that you should get an NVIDIA card for its better linux compatibility through VDPAU.

2. Having said that, the graphics card will do the rendering. Unless you have any particular need for software rendering, you can get a much cheaper CPU / motherboard.

3. There may be little point in getting a separate soundcard if you are going to be using HDMI for sound.

4. 2GB of RAM is sufficient for video playback.

5. Ensure your motherboard's wol / usb is ubuntu compatible. Fathomlessly, this usually depends on OS support(!)

6. Consider an external IR receiver. Although looking neater, these internal ones apparently don't support ir blasters. *Although I have not been able to get it to work*, being able to wake up all the other equipment once your computer boots up, and switch it off once it halts would be very convenient in my situation. It may also be convenient for you. Alternatively, get a Harmony remote.

7. If you want to spend more money, put it towards silence. (Bigger fans / passive cooling).

---

### Post by Dan Again on 2011-08-15
Awesome, this is just the kind of advice I'm looking for...I had a feeling I was going a little overboard, but just wasn't sure what components could be downgraded. So I'm considering replacing the CPU and motherboard with the following combo...
[LIST]
[*]AMD 2.6G processor + Gigabyte 6Gb/s motherboard ($227.98\)
[/LIST]
I definitely understand the importance of using an NVIDIA video card. Should I spend a little more money on the video card, or is what I have selected sufficient?

I got rid of the sound card and replaced the RAM with the following...
[LIST]
[*]G.Skill 2G RAM ($34.99)
[/LIST]
I don't really understand your points 5 & 6. If I get a Harmony remote, do I still need to get an IR receiver?

What are some specific pieces of hardware I would buy to accomplish your point 7?

---

### Post by jawilljr on 2011-08-15
As far as Video Cards go...[This is what I would get](http://www.newegg.com/Product/Product.aspx?Item=N82E16814500175)

It does VDPAU feature set C just fine.

Jerry

---

### Post by Bertrandization on 2011-08-15
> I definitely understand the importance of using an NVIDIA video card. Should I spend a little more money on the video card, or is what I have selected sufficient?

I am pretty sure it will be fine. My understanding is that the "Purevideo HD" capability equates to 1080p without stutter under VDPAU.

> I don't really understand your points 5 & 6. If I get a Harmony remote, do I still need to get an IR receiver?

Yes. You still need an IR receiver.

The point of the Harmony remote and/or the IR blasters are for controlling everything else. Generally you will want to change the volume through your TV or amp, etc. I assume you do not want to use more than one remote control.

The Harmony remote will do this, but you will need to:
a. use Windows to set it up and
b. be able to point it at what you need to control. (No housing things in closets, etc.)

The IR Blasters will also do this, and:
a. can (at least theoretically, [http://ubuntuforums.org/showthread.php?t=1824638](http://ubuntuforums.org/showthread.php?t=1824638)) be setup in Ubuntu, and
b. can be straightforwardly scripted in bash to eg. switch everything on after a wake on lan magic packet, etc.

(Although looking at the above summary of pros and cons, I am reminded of the 'Tornadoguard' xkcd strip. Perhaps I should place more emphasis on the "DOES NOT WORK" aspect of the IR blaster 'solution').

The other thing you should be aware of is that the Harmony remotes have very powerful and wide-angled IR transmitters. The 'free' ones I have received with IR receivers have been extremely finicky by comparison.

> What are some specific pieces of hardware I would buy to accomplish your point 7?

PSU: [http://www.seasonicusa.com/NEW_X-series_Fanless.htm](http://www.seasonicusa.com/NEW_X-series_Fanless.htm)
CPU: [http://www.thermalright.com/products/index.php?act=data&cat_id=27&id=95](http://www.thermalright.com/products/index.php?act=data&cat_id=27&id=95)
Video: [http://www.thermalright.com/products/index.php?act=data&cat_id=30&id=176](http://www.thermalright.com/products/index.php?act=data&cat_id=30&id=176)

You may also need a larger case to house these.

I do not own any of this equipment. They are examples of the kind of thing I mean. (Although you can't go wrong with Seasonic for PSUs. Corsair does not manufacture these. It rebadges them.)

---

### Post by drawkcab on 2011-08-15
I don't mean to rain on your parade but you're going to drop $1300-$1400 on an htpc?  The whole project seems overboard to me.  Hear me out for a minute.

I have had a modest ion dual core nettop htpc that does about 95% of what you're asking and is both energy efficient and silent.  With wireless keyboard and mouse it cost me $300.  This year I added a 2TB esata hdd (it doubles as my home server) for another $120 for a total of $420.

The only limitations that irk me is that it can't handle 1080p and hi def flash can be a bear.  On the other hand, the $$$, energy, silence and hdd space savings with 720 (with 1080p vids you'll fill up that 1TB hdd in no time!) are worth the trade off.

All I'm saying is that you can probably spec a rig that handles 1080p for $600-$700.  Put the other 1/2 of your budget toward upgrading your gaming and/or video editing rig where the extra snort will make a much bigger difference.

---

### Post by Dan Again on 2011-08-16
@Bertrandization - Thanks!

@drawkcab - You're totally right...no worries about raining on my parade. Like I said, I'm totally green with this sort of project and am relying on others' knowledge and advice. I actually came to a similar conclusion earlier today after reading [this]("http://gadgetscholar.com/2011/01/build-a-htpc-on-the-cheap-under-250/") (Build a HTPC on the Cheap (under $250)).

Although I don't think I'm going to be able to hit that low price point, it looks like I'll be able to achieve all my goals at about 1/3rd of the cost and in a much smaller package with the following configuration (all from NewEgg)...
[LIST]
[*]Biostar BD61 barebone computer ($149.99)
[*]G.Skill 4G (2 x 2G) 240 pin DDR3 1333 RAM ($39.99)
[*]Western Digital Caviar Black 1T 7200RPM SATA 3Gb/s (2 @ $89.99)
[/LIST]
I still have a couple of questions...
[LIST=1]
[*]Obviously I'm missing a processor and/or a video card. It looks like this box is made to use a CPU that does not require a separate GPU. Right now I have the Intel i3-2100 on my wish list. Will this chip be sufficient for my needs, or should I spring for something higher-end if I don't plan on using a separate GPU?
[*]Does this unit have a built-in Blu-Ray drive?
[*]Does this unit come with a remote?
[/LIST]
I know the last two questions are a little weird, but, although the product spec's don't mention either one of these features, the one review on NewEgg makes it sound like the case does have a Blu-Ray drive and remote. Just wondering if anyone else can make sense of that.

---

### Post by drawkcab on 2011-08-16
> **Dan Again said:**
> Although I don't think I'm going to be able to hit that low price point, it looks like I'll be able to achieve all my goals at about 1/3rd of the cost and in a much smaller package with the following configuration (all from NewEgg)...
[LIST]
[*]Biostar BD61 barebone computer ($149.99)
[*]G.Skill 4G (2 x 2G) 240 pin DDR3 1333 RAM ($39.99)
[*]Western Digital Caviar Black 1T 7200RPM SATA 3Gb/s (2 @ $89.99)
[/LIST]
I still have a couple of questions...
[LIST=1]
[*]Obviously I'm missing a processor and/or a video card. It looks like this box is made to use a CPU that does not require a separate GPU. Right now I have the Intel i3-2100 on my wish list. Will this chip be sufficient for my needs, or should I spring for something higher-end if I don't plan on using a separate GPU?
[*]Does this unit have a built-in Blu-Ray drive?
[*]Does this unit come with a remote?
[/LIST]
I know the last two questions are a little weird, but, although the product spec's don't mention either one of these features, the one review on NewEgg makes it sound like the case does have a Blu-Ray drive and remote. Just wondering if anyone else can make sense of that.

Seems like a good base to build on. I would say the i3 is more than sufficient and the reviewers seem to agree.

The unit seems to come with a remote but it seems you'll have to add your own bluray drive.  If you look at the bottom of that review, the reviewer lists his spec.

You'll have to get some pics up and tell us how the build went.

---

### Post by Dan Again on 2011-08-16
Okay, I see - the 5.25" expansion bay is for an internal Blu-Ray drive.

I'm super stoked...just waiting for a bonus to come in so I can make the purchase. I'll definitely post an update with pictures when I'm done.

Thanks for all the help, guys!

---

### Post by muddyh2o on 2011-08-16
This sub-$400 PC works really well as an HTPC.

You'd need to add something for IR, keyboard, and a HD, but it's absolutely silent and works very well as an HTPC, though it's now powering a MAME cabinet.

[http://www.avsforum.com/avs-vb/showthread.php?t=1327224](http://www.avsforum.com/avs-vb/showthread.php?t=1327224)

---

### Post by Dan Again on 2011-08-16
Hm, I appreciate the advice, but I'm kind of heart set on my build now. The integrated IR/remote and internal hard drive & Blu-Ray drive capabilities are big selling points for me.

---

### Post by FSUcyberpunk on 2011-08-16
Dan congrats on taking up the challenge to build your own system. I too am building another media/gaming system. You had some really good components picked out. Overkill for some people but I'm about to spend over $1800 on mine. I think a first build with a barebones is a good way to start out. Just a couple things to think about with your Biostar BD61.
1) Most power supplies that come with barebones are crap. So you may want to order one with your system. Look for a modular one. The Seasonic recommendation is a good one but I'm personally a little of fanless ones.
2) Are you going to converting any of your videos for phone or your ipod/mp3 player? If so you're going to want an i5 quad core.
3) What video formats will you be using? MKV videos with 1080p and Master Audio DTS or Dolby or both can be 25-40GB for one movie.
4) Most builders use after market cpu coolers. Go with one that cools well but is relatively quiet or look at Corsair and Antec liquid coolers.
One last suggestion get two 2TB Western Digital Black 64MB cache drives. Do a normal install on one and then add the other. Format it ext4. Then go to the Ubuntu Software Center and install PySDM(Storage Device Manager). Run the program and make your empty 2TB drive your mount point Videos folder(/home/user/videos). Since videos take the most space you have 2TBs just for them and if you ever upgrade you just pull the drive and add to videos in your new system.
Good Luck

---

### Post by Dan Again on 2011-08-17
Thanks for the tips. A few questions...
[LIST]
[*]How would I know if the power supply that comes with the barebones unit is crap? Did you look at the specs of the Biostar BD61? If so, do you think I should replace its power supply and why? What exactly is the difference in performance between a good power supply and a bad one? If I choose to replace it can I replace the internal power supply, or will I have to use an external one?
[*]I don't plan on using this unit for anything other than acquiring, storing and viewing media. I plan on using my other systems for any kind of media manipulation, but I'm still worried about the ability of the relatively low-end i3-2100 CPU to handle my needs, especially since I'm not using a separate GPU. Do you think that this processor will be sufficient to meet my needs, or do you think I should upgrade to a more powerful one? If so, do you have a recommendation? Also, I would like to use XBMC and I came across some chatter that seemed to indicate that there may be some issues using a Sandy Bridge processor with XBMC on Ubuntu. Do you have any experience with this?
[*]I typically just download BRRip movies, which are fairly compact (usually under 1G a piece). I'm confident that 2T is the right amount of storage for me at this point.
[*]I'm not quite sure I'm getting your point in #4, but I have a related question. The case has a PCI Express 2.0 x16 slot that I will not be using - will a standard PCI case fan fit in this slot?
[*]Regarding your last point, another board member suggested I used a RAID 0 hard drive configuration to maximize performance. What are your thoughts on that?
[/LIST]
Thanks!

---

### Post by drawkcab on 2011-08-17
> **muddyh2o said:**
> This sub-$400 PC works really well as an HTPC.

You'd need to add something for IR, keyboard, and a HD, but it's absolutely silent and works very well as an HTPC, though it's now powering a MAME cabinet.

[http://www.avsforum.com/avs-vb/showthread.php?t=1327224](http://www.avsforum.com/avs-vb/showthread.php?t=1327224)

Nice!  That beats the new Acer Revo which comes in about $350.

---

### Post by drawkcab on 2011-08-17
> **Dan Again said:**
> The integrated IR/remote and internal hard drive & Blu-Ray drive capabilities are big selling points for me.

I know that an IR remote is easy to set up in windows but I've heard that it can be problematic in linux.  Anyone know anything about this?

> **Dan Again said:**
> [*]I typically just download BRRip movies, which are fairly compact (usually under 1G a piece). I'm confident that 2T is the right amount of storage for me at this point.

A BRRip that comes in at 1gb is a High Def -->  Standard Def rip.  High Def rips at 720p are somewhere between 2-5 gb/ film.  1080p can top 10gb.

I don't hoard movies but, even so, I've reached 1.1 / 2 TB in 8 months with music, books, audiobooks, tv shows, etc.  All I'm saying is that it's quite easy to max out your storage with high def content.

---

### Post by FSUcyberpunk on 2011-08-17
Dan I have 2 friends that have the Biostar BD61. So yes, I have seen the power supply. You just unscrew 4 screws on the back of the case, pull the original one out, and put the new one in securing it with the 4 screws. Cheaply made power supplies go bad fast meaning you get random errors due to power flux and eventually just die so you have no power for your rig.
 That i3 will be plenty of processing power. I was just saying if you want to transcode video go with a quad core vs a dual core. A dual can do it but it takes a lot longer. Yes, there are some problem with sandy bridge and XBMC so if you're going that route you may want invest in a graphics card. 
As another poster pointed out your not get true hd video with 1GB downloads. Most are in the 4.4-8GB range. Your definitely not getting anything but 2 channel sound. If you want small file sizes go with Xvid ones. They're around 3.8GB.
Your case fans mount with screws to the inside wall of your case and use wires with a plug to plug into your motherboard or power supply. The PCIe 2.0 X 16 is for your video card.
Point 4 was the the i3 comes with a fan/heatsink. Don't use that one. Buy one and some thermal paste. The after market ones are quieter and better coolers. 
Finally I would recommend against RAID 0. Yes, there is a small perform boost but at the risk of losing all your data. Basically what RAID 0 does is use the processing power 2 hard drives to act as one. So your data is scattered over to 2 hdds vs being centrally located on one. So say you went with RAID 0 and one of the hdds failed, you couldn't get back the videos you down loaded because some only certain parts of the file are on the good drive.

---

