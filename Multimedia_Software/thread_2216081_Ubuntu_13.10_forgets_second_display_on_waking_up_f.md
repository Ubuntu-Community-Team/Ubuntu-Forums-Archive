---
title: "Ubuntu 13.10 forgets second display on waking up from suspend"
date: 2014-04-09
forum: Multimedia Software
---

### Post by paul0075 on 2014-04-09
Hi Guys,

I have a dual display set up on my computer running Ubuntu 13.10, using the latest Intel Q45/43 driver package.

When I boot the computer, my dual screens all work as they should, however, if I suspend the computer and then wake it again, the second display is no longer detected.

The main display is via the DVI output and the second via the DisplayPort. The second display is an LCD TV that also can double as a computer monitor, but only has HDMI in or Analog VGA in. The output on the computer only gives me the choice of DVI or Display Port. 

What can I do to get this 2nd display working without having to throw down on an additional video card (budget is very limited)?

I have been using Ubuntu on and off again for a few years, but still very much in the newbie class when it comes to troubleshooting. I migrated from Windows to Mac in 2006, and now decided this year to throw in the towel on Apple as well.

Here's the summary of my PC:


[LIST]
[*]Dell Optiplex 960 Core 2 Duo 3.0 GHz
[*]4GB RAM (shared with video)
[*]Intel Q45/Q43 onboard graphics with DVI and Display Port outputs
[*]500 GB Hybrid SSD HDD and 1TB SATA HDD
[*]DVD burner
[*]On board sound
[*]Micro form factor case
[*]No expansion slots being used
[*]Main display is Dell 23 inch (using DVI input)
[*]Second display is 21 inch ALDI Vivid brand TV (using HDMI input)
[/LIST]

Thanks in advance for what ever advice comes my way.

Paul0075

---

### Post by paul0075 on 2014-04-17
I have finally got it figured out. I changed the suspend mode in my BIOS from S3 to S1 and now the 2nd display comes back up from Suspend without issue.

---

