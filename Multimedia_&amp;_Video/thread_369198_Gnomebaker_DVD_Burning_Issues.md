---
title: "Gnomebaker DVD Burning Issues"
date: 2007-02-24
forum: Multimedia &amp; Video
---

### Post by Kung Fu Hamster on 2007-02-24
PROBLEM: I have a huge stack of nice new coasters sitting next to my computer. :)

Whenever I try to burn a DVD with Gnomebaker, it will ALWAYS die with the same error message. The burning log is as follows:

```

Executing 'mkisofs -gui -V GnomeBaker data disk -A GnomeBaker -p Michael Johnson -iso-level 3 -l -r -hide-rr-moved -graft-points --path-list /tmp/GnomeBaker-kungfuhamster/gnomebaker-EPSa4W | builtin_dd of=/dev/sr0 obs=32k seek=0'
INFO:	UTF-8 character encoding detected by locale settings.
	Assuming UTF-8 encoded filenames on source filesystem,
	use -input-charset to override.
/dev/sr0: "Current Write Speed" is 8.2x1385KBps.
:-[ WRITE@LBA=1eda0h failed with SK=5h/ASC=21h/ACQ=02h]: Invalid argument
:-( write failed: Invalid argument
/dev/sr0: flushing cache
/dev/sr0: updating RMA
/dev/sr0: closing disc

```

I tried sing k3b, and had the same problem. I'm using a Plextor PX-712A SATA DVD burner and Ubuntu 6.06 at the moment. I've tried uninstalling and reinstalling the apps, with no luck. I couldn't get any info from either Google or the #ubuntu channel.

---

### Post by sdk7_25 on 2007-02-25
So I'm new to linux but I've been having a lot of minor burning issues.  I've been lurking around trying to answer all my questions and I, coincidentally, have found the answer to yours.  Since it's a little more obscure, I'll share:

Andy Polyakov, who is the creator of dvd+rw-tools discusses this issue with specific Plexor models:

> Recording speed chosen by Plextor PX-708A, possibly other units... 	

growisofs expects recorder unit to readjust the list of supported velocities and pick optimal one upon every media re-load. Plextor unit (and possibly some other units) reportedly tends to retain once chosen velocity value. E.g. if you set 2.4x for 4xDVD+RW media and then load 4xDVD-RW media, even then it will pick 2x. Unless you explicitly tell otherwise that is. Therefore you have keep track of current velocity and explicitly pick one for every recording. If you wish to unconditionally default to highest speed, possible workaround is to "alias growisofs 'growisofs -speed=256'." Yes, this means that whenever you specify -speed option, there will be two -speed options passed down to growisofs. But that does the trick as it's the last one in command line which applies. -speed=256 alone effectively means "pick highest possible." Well, any insainly high value would do...

Both Gnomebaker and K3B are front-ends for growisofs, btw.  While this is not your exact model, I think it's included based on info from Plexor about a feature of your drive:

>                      
PoweRec&#8482; technology is a sophisticated entire DVD write strategy providing superior quality recording at maximum speed for your chosen media


I think that you're trying to tell the drive a speed to burn at and it's trying to set it's own speed.  I don't know what the aformentioned work around does exactly (like I said, I'm still very new to linux) but hopefully this helps.

Oh, and here's the links to where I got the info:
[dvd+rw-tools: Hardware Compatibility Notes]("http://fy.chalmers.se/~appro/linux/DVD+RW/hcn.html")

[PX-712A]("http://www.plextor.com/english/Archive/products/712A.htm")
(Note: there might be a firmware update for your burner)

And one more thing:

> Executing 'mkisofs 

I did notice this in your log,[ however]("http://fy.chalmers.se/~appro/linux/DVD+RW/") 
> It should be explicitly noted that growisofs is a front-end to mkisofs
So I think it still applies

---

