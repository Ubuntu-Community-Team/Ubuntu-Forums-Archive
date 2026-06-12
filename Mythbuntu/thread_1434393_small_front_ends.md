---
title: "small front ends"
date: 2010-03-20
forum: Mythbuntu
---

### Post by archeryrob on 2010-03-20
I was looking around and looked at the Sage TV HD200 their idea of a front end. Are their any small boxes like this you can load Mythbuntu on? I am not really a fan of the HD200, it seem nice but is locked with their software, no dvd player and such.

Looking for something smaller than the horizontal computer case.

---

### Post by lank23 on 2010-03-20
If you read this persons write up it talks about using telnet to  login to the Linux OS.  But still at best you could only use it as a frontend

[http://www.geektonic.com/2009/01/sagetv-hd200-hd-theater-geektonic.html]("http://www.geektonic.com/2009/01/sagetv-hd200-hd-theater-geektonic.html")

---

### Post by SiHa on 2010-03-20
For a build-it-yourself system, the Zotac ION boards are popular.

---

### Post by timconradinc on 2010-03-20
> **SiHa said:**
> For a build-it-yourself system, the Zotac ION boards are popular.

What he said. These [look pretty great for a mythfrontend]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813500028"). 

You could likely get by without a case at all, if that works for you.

I intend on getting a [USB adapter]("http://www.newegg.com/Product/Product.aspx?Item=N82E16815158163") and just using a regular USB storage device for the OS. Basically, this is a no-fan, no-moving parts myth frontend. 

There's some decent cases available for that form factor, as well, that look okay.

---

### Post by SiHa on 2010-03-21
> **timconradinc said:**
> 
There's some decent cases available for that form factor, as well, that look okay.

Sure are. I happen to be selling a few on eBay at the mo:D

---

### Post by My Name on 2010-03-21
£150 and you can get yourself an acer revo. I have one in my bedroom for a frontend and it works beautifully with full ubuntu and myhtv on it. it is HD aslo with a HDMI output. It isn't completely silent as it has a fan, but the fan only spins up on boot. it boots up very quickly too.

---

### Post by archeryrob on 2010-03-24
Anyone know if you can get the acer revo without software? They want $200 for one with windows on it and I bet it could be $150 without windows, which would get over written anyways.

---

### Post by My Name on 2010-03-24
They do a linux one. The distro on it is crap but it's easy to wipe and it is still better than paying the micro-tax.

The single core 230 one with 1gig of ram will do. you may have to shop around.
i stuck in another gig of memory to get full HD to work at it's best. I found also that loading mythbuntu made the machine run very sluggishly, but loading ubuntu and then installing mythtv on top works much better. i have no idea why, but it did.

Good luck.
PM me if you need any help setting it up. I needed a little help myself and will be more than willing to pass on the tips

---

### Post by archeryrob on 2010-03-24
I did a search and could not find any with linux on them. I would be nice to buy a bare bones type unit since anyone using linux should know how to install the operating system they want.

The only Linus I can find are in the UK, where you are and I am not.

---

### Post by archeryrob on 2010-03-24
I called ACER and get sent to India and they are no help. They tell me to call Home Shopping Club, again, no help. ;)

Call Newegg.com - No one knows anything. They can only help if I bought something and no idea how to order something if it's not a package deal on the website.

Companies build a nice product and they man the phone with people that know nothing and can't help. They can only read a line card that says the same crap I can read on the web site. Did they stop teaching people how to think?

---

### Post by My Name on 2010-03-24
sorry mate, I wasn't aware they were not available everywhere.
I'm sure you could get a re-furb or a second hand one for a bit cheaper.
The one i got was a refurb and it was listed as "no operating system".
As I say, it was a crappy distro but it was an OS non the less :)
$200 isn't too bad though seeing as the motherboard an CPU cost $150

---

### Post by archeryrob on 2010-03-24
My name,

  How did you connect to the TV? HDMI or DB25 and audio cable? Some where talking about problem with sound driver through HDMI with Win7 and only 720P other saying 1080P. What say you with MythTV?

---

### Post by My Name on 2010-03-24
I am using the hdmi port to connect to a large monitor via DVI. I get audio using usb speakers. I have it setup in the bedroom so i don't need 5.1 or anything.
There is an option in the audio section in mythtv to output throu HDMI though so there shouldn't be any problem.
I think it is important to use the hdmi port though as this means the graphics chip is doing the hard work and not the processor. To be fair I'm not sure how true this is, but it is my understanding.

Now I can watch BBC HD at 720 without any problems using the vdpau normal preset, but I think I messed around with some of the 1080 setting so I can't be counted on for advising you on that one. I have read others using the revo and getting 1080 without any problems at all. I'll see if I can find out the optimal setting for 1080 and report back.

---

### Post by My Name on 2010-03-24
I have just set up a custom profile with these settings

TV Settings->Playback
Page 1: Enable OpenGL vertical sync for timing
Page 3: I added a simple profile, with one setting for all resolutions
Decoder: NVidia VDPAU acceleration
Video Renderer: vdpau
OSD Renderer: vdpau
Primary Deinterlacer: One Field (1x, Hw)
Fallback Deinterlacer: Advanced (1x, Hw)

It plays BBC HD channel without any problems

---

### Post by jensk on 2010-03-25
I can confirm the experiences with the Revo 3600. I bought mine at amazon.co.uk for £140 with linux os.

I use it with HDMI to HDMI and are transfering sound via HDMI. it worked out of the box when enabled inside Myth.

I do have small picture errors within the first 15 pixels from the top of the screen. It's like the if the top 15 rows of pixels are a bit delayed from the rest of the picture. I am using Nvidia VDPAU version 185. i have tried to upgrade to version 195 without success.

What version of Nvidia drivers are you using?

---

### Post by My Name on 2010-03-26
I did have a little bash at getting the 190-195 drivers installed but I had no luck with that. i didn't really try that hard, but in the end it really didn't matter. I am using the 185 drivers with no probs.

Just thought, to get rid of those bad rows, you could zoom in 'til they are hidden off screen. It's a bit of a bodge but maybe those 15 rows aren't too important.
Have you tried connecting to a different TV or monitor to see if it is TV? also try out another cable. You have probably tried these already so please ignore me...

---

### Post by SiHa on 2010-03-26
> **jensk said:**
> 
I do have small picture errors within the first 15 pixels from the top of the screen. It's like the if the top 15 rows of pixels are a bit delayed from the rest of the picture.

Sounds like tearing. Have you tried disabling composite extensions, as mentioned in the [[COLOR="Blue"]_MythTV Wiki_[/COLOR]](http://www.mythtv.org/wiki/VDPAU#Troubleshooting)?

---

### Post by movieman on 2010-03-28
BTW, I just noticed that Intel is ending production of the first-generation Atom CPUs, so if you want an Ion motherboard you should probably get one quick; the new Zotac motherboards with the new Atom CPUs appear to have the Ion chip on a separate graphics card rather than the motherboard so they won't fit into a lot of mini-ITX cases.

---

### Post by archeryrob on 2010-03-29
Thanks guys,

my Name, What do you use for a remote with the revo?

I am considering several options. I would like a small case and cheap like the Revo, but I like the Zotac as I can include a small laptop DVD drive in some of the small cases. I don't like any of the preconfiged systems as they all come with 160gb hard drives and I would like to get a cheap 20 or 40 or smaller, just for a boot as it's a front end, not the storage server.

---

### Post by My Name on 2010-03-29
I am using a philips RC6. It looks like a microsoft mce remote but doesn't have microsoft written on it.  it was a lot cheaper than the branded microsoft remote but looks the same and works with the same default setup.

---

### Post by lmclaren on 2010-03-29
I purchased my Revo from ebay, I had no problems with the transaction.

The seller was 23port and they have the linux version.

I have "modified" mine slightly, I am using mine as a front end in the bedroom and wanted it to be very quite. I found that most of the noise was coming from the HDD, I removed that and network boot and there was a lot less noise. 
Further noise reduction can be had by leaving the top cover off, the cover interfears with the fan and creates noise, I will cut a hole in the top one day when I get around to it....

regards

Lee

---

