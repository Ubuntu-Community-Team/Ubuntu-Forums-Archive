---
title: "No Airport Express found in Karmic?"
date: 2009-11-21
forum: Multimedia Software
---

### Post by gfunkdave on 2009-11-21
Hey all, I'm running Karmic and at least once in the past I was able to stream music over the network to my Apple Airport Express using the version of PulseAudio that ships with Karmic.

Now, the PulseAudio Applet in my menu bar says that it can't find any network devices. But I know the Airport is there (I can ping it, and in VirtualBox I can run the Airport Manager, which can manage the Airport just fine). 

I have verified that the two checkboxes in System - Preferences - PulseAudio Preferences (on the Network Access tab) are checked. I have also rebooted a couple of times. No luck.

Any ideas?

Thanks!

---

### Post by gfunkdave on 2009-11-22
Nobody?

Here's something else interesting. I noticed that my network suddenly had a lot of bandwidth being used on the LAN side (about 125 kB/s). I did a netstat and realized that my laptop had an open connection to the Airport Express, but PulseAudio still doesn't recognize that there's an Airport.

Going in to the PulseAudio manager and unchecking the boxes for Airport and Network device support results in the odd connection being closed.

Any help??

---

