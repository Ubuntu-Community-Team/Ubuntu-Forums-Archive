---
title: "XFX 8400GS Nvidia card problems, tv out etc"
date: 2007-09-14
forum: Multimedia &amp; Video
---

### Post by Poet with a Gun on 2007-09-14
I bought an XFX 8600GS card because my on board nvidia card doesn't have TV out. The problem now is that I still don't have TV out.

I am using the s video cable to connect to the TV. I tired using NVtv out and it didn't support my card apparently, I tried to clone the desktop to the tv with the nvidia tool, but that screwed up my xorg.conf file. 

Any leads?

---

### Post by Poet with a Gun on 2007-09-14
Nothing eh? This is one of the frustrating things about Ubunutu and linux in general,  out of the box functionality.

I hate Windows, and I know the lack of driver's and mfg support is due to the world being a window's world, but hell it work.

I can live without tv out for a while, hopefully when GG comes out this will magically start working, but if not I'm going to have to look at other options, this is the family computer/media center and if I can't get vids to the TV then it's not doing half of it's job :(

God I hope I can get it working, I Don't want to go back. Ever.

---

### Post by Poet with a Gun on 2007-09-15
So I gave this another swing, and I don't think the problem is so much that I can't get my tv out to work I think that's a symptom of something else.

When I lspci  my schtuff I get this for my VGA

```
02:00.0 VGA compatible controller: nVidia Corporation Unknown device 0422 (rev a1)
```

Which maybe the half the damndable problem. Also, I don't think I'm properly detecting my TV. I'm hooking to it via the svideo cable that came with my card (already tried the monster cable I spent $20 on...) and nothing.

I configure it as a twin view, to the right of CRT1 and save to my conf file and reboot.

Start nvidia settings up again and the tv is disabled (again or still).

I think I screwed up at buying a newer card rather than an older one, but still, any help you fellas cans gives me would be greats. 

This PC not detecting my vid crd would also explain why it doesn't seem to run as "snappY" as the on board nvidia 6100.

---

### Post by Poet with a Gun on 2007-09-16
I feel so damn burned out. Hopefully something gives here. I can't get my cd burner to work right either and I understand that might be a bug, I Can live without that until October when the update comes out.

But this No TV out thing burns me. 

I'm beginning to think the only way to get a free world changing Ubuntu linux to work right is to throw money at Dell. 

Any hints at all to get this damn thing to work? Anything?

I talked to a friend and he said that the lscpi not recognizing the card was a small thing, shouldbe causing the problem, so now it's gotta be an issue with my .conf file, or something. I've only started messing with this stuff this month :/

---

### Post by Poet with a Gun on 2007-09-16
The S video out is a seven pin plug, that should work fine with a 4 pin cable right? it's the plug that came with the card.

Still fighting with this damn thing.

---

### Post by Poet with a Gun on 2007-09-20
*sigh*

It's a good damn thing I have a short attention span and don't focus on these kind of let downs long enough to let them bring me down.

I'm holding out for the Gutsy Gibbon, and if that don't fix it, I'm going to spend MORE money getting suported devices as required by a FREE OS again, and SHAME on me for not checking compatibility before buying something.

damn me.

This whole linux thing is like a bad relationship with a pretty girl. You wanna hang in there, but you know she'll just break your heart over and over and over again, and the only real relationship alternatives would be to either pay a gal(windows), or settle on one that's just not quite as good looking but, but easier to get along with (old, reliable stable hardware).

---

### Post by funkstar101 on 2008-04-02
hi there poet

am a newbie on the site. did u manage to sort out your no tv out problem. i have exactly the same problem and i'm using xp so dont feel bad. i sent a request to xfx for product support if theres anything we can use i'll pass it on. have u solved the problem in the interim pm me or post here.

---

### Post by Poet with a Gun on 2008-04-12
Sold the card to my brother at a 15$ loss and bought the next card down that I "kniew" was supported.

Suckey doo eh?

---

### Post by funkstar101 on 2008-04-14
hi there poet ta for replyin. i dont hav anythin that solves my prob. gonna post on nvidia forums and see if i can get a solution. at the moment i'm using toggle feature.

---

