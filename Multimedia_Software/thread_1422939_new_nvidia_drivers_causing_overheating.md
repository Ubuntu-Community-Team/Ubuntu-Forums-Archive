---
title: "new nvidia drivers causing overheating?"
date: 2010-03-06
forum: Multimedia Software
---

### Post by jejones3141 on 2010-03-06
BlizzPlanet [reports]("http://www.blizzplanet.com/blog/comments/nvidia_19675_drivers_causing_pc_and_graphic_cards_to_overheat/") that people are seeing their nvidia graphics cards overheat when running the Windows 196.75 driver and playing 3D games.

I have to wonder whether I fell afoul of this issue. A week ago I installed the 195.36 nVidia proprietary Linux driver on my Karmic Koala system, after adding the PPD nvidia-vdpau repository to my sources.list. I restarted so the new driver would take effect... and was surprised to see the graphics chip temperature soar to over 130 degrees Celsius. It fried itself. When I opened up the case, I checked the card's fan, and it spun freely, and I'd not heard any noise of the sort that accompanies a dying fan.

I'm sticking with 190.53 for now. Has anyone else seen overheating difficulties with the 195.36 driver?

---

### Post by Ferrat on 2010-03-06
sounds like a sensor problem perhaps but I installed drivers from nVIDIAs homepage less than a week ago and I got the 190.53 driver and searching now I just get up the 190.53 driver (on their homepage) so they might have retracted the later version?

EDIT:

found this by the driver download 

196.75 Alert!
We are aware that some customers have reported fan speed issues with the latest 196.75 WHQL drivers on NVIDIA.co.uk. Until we can verify and root cause this issue, we recommend that customers do not download this driver. Instead, please stay with, or return to 196.21 WHQL drivers. Release 196.75 drivers have been temporarily removed from our website and we also are asking our partners and others to remove temporarily this 196.75 WHQL driver as well.

---

### Post by cchhrriiss121212 on 2010-03-06
I'm using 195.36.03 and my temperature is at 60C which is normal. Did it happen immediately after you switched on? 
Reports seem to indicate this is a windows problem.

---

