---
title: "HTPC NVidia Graphics Card HDTV Settings"
date: 2008-12-28
forum: Multimedia Software
---

### Post by Syndicate5 on 2008-12-28
I used to work with a friend of mine that built the old 3-gun CRT projectors. We installed alot of home theater and projector systems. He knows alot about RGB-HV connections. I asked him about the VGA to component cables that you see that come with some new projector systems these days.

(I was curious about hooking the VGA output of my PC directly to my Tv component inputs. I knew it was a stretch.)

He says that there will be a sync issue unless the graphics driver settings in my PC are able to add the sync signal to a different pin on my VGA output? I think the one that feeds the green RCA connector at the other end of the cable.

Anyone heard of these settings?

---

### Post by hougSTAR on 2008-12-28
What video card is it?  I know my Nvidia allows me to choose what connectors I am using and has a few Sync options in the settings.  I'm not really sure what each one does, but that is probably what he is referring to.

---

### Post by Syndicate5 on 2008-12-28
Its a built in NVidia GeForce 6100. I did see some settings, but dont know exactly what they do yet.

Ive attached a screenshot.

---

### Post by wackston on 2009-01-03
A direct connection of a VGA output to a TV component input will not work
well / at all.  They're electrically different.  TV component-in is electrically a balanced transmission line intend for co-ax connections with a strictly band-limited signal.  VGA is ... a mess.  Also TV-Component input expects composite (H and V sync) sync signal overlaid on the green channel.  VGA normally has seperate syncs.  For NTSC / 60Hz HDTV component is, furthermore, not RGB but YPbPr (basically luma, blue-luma, red-luma).

The necessary electrical conversions are what those little 
"component out" bits on graphics cards / add-on cards / adaptors do.

---

### Post by Syndicate5 on 2009-01-03
After talking with some guys at work, Ive pretty much came up with the same answer. It just wont work. I didnt know the exact reasons ,thanks for taking the time to point them out.

Im basically going to buy an HDMI output card. 

[IMG]http://mooretechnology.net/gigabyte.jpg[/IMG]

---

