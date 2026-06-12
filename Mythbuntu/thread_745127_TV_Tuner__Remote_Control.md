---
title: "TV Tuner / Remote Control"
date: 2008-04-04
forum: Mythbuntu
---

### Post by DigitalDuality on 2008-04-04
I currently already have a DVR service provided to me by Comcast, but if MythBuntu works out great I might be ditching it to save me some money.

So i have several questions up front, they may have been answered numerous places but all the wikis, documentation and even this forum.. i think I'm just not getting it.

I see many tv tuner cards come with a remote control.  When i see if TV Tuner cards are supported it says nothing about their remote control functionality.

Also going through various wikis, i don't see any tv tuner card where all functionality is supported.  

Should  i get a remote seperate from the tv tuner card?

And  what is a great tv tuner card for a decent price that people have verified that works?

I'm not planning to do anything with HD Stuff so my hard-ware requirements shouldn't be too steep.

Last question, for anyone that's used Tivo or Comcast DVR, is mythbutnu a decent replacement for that?  Or is it a pain? Mind you i will not be the only person using this, and the other individual is not linux savy.

---

### Post by majoridiot on 2008-04-04
> **DigitalDuality said:**
> I currently already have a DVR service provided to me by Comcast, but if MythBuntu works out great I might be ditching it to save me some money.

So i have several questions up front, they may have been answered numerous places but all the wikis, documentation and even this forum.. i think I'm just not getting it.

I see many tv tuner cards come with a remote control.  When i see if TV Tuner cards are supported it says nothing about their remote control functionality.

Also going through various wikis, i don't see any tv tuner card where all functionality is supported.  

Should  i get a remote seperate from the tv tuner card?

And  what is a great tv tuner card for a decent price that people have verified that works?

I'm not planning to do anything with HD Stuff so my hard-ware requirements shouldn't be too steep.

Last question, for anyone that's used Tivo or Comcast DVR, is mythbutnu a decent replacement for that?  Or is it a pain? Mind you i will not be the only person using this, and the other individual is not linux savy.

there are a lot of affordable tuner/remote solutions you could employ.  i use 2 pvr-150 tuners in
my backend server and they work flawlessly.  you can find very good deals on these tuners online- many
times starting from $40 or so.  i *think* most of the pvr-150s come with remotes, but there are two
different styles... one where the remote receiver plugs into the pvr-150 and another where the
receiver is USB.  the USB is preferable as it tend to work much better- at least in my experience.

the USB versions are generally called "pvr-150 MCE" or some variation that includes MCE.

also, it is possible to buy a cheaper pvr-150 with the lesser remote and pick up an MCE remote and
receiver from ebay for $20 or so.

whichever tuner you settle on, you should be aware that it will tune *only* the analog stations from your
cable line-up.  the digital channels are demuxed/decrypted by the DVR and can not be tuned on the 150
or any other analog capture card.  with my comcast line-up, this limits me to channels 3-75 only.

you might also consider using the firewire output of your dvr as a capture device.  this could give you
access to digital channels, too... depending on the encryption status of your channels.  info on this can
be found here: [https://help.ubuntu.com/community/MythTV_Firewire](https://help.ubuntu.com/community/MythTV_Firewire)

note that significant changes are being made to firewire for mythbuntu 8.04 and once they are
incorporated, it *should* be plug and play for most people and the procedures on that page will no 
longer be needed.

---

