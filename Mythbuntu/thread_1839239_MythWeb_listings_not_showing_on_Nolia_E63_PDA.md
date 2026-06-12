---
title: "MythWeb listings not showing on Nolia E63 PDA"
date: 2011-09-05
forum: Mythbuntu
---

### Post by Tonyr63 on 2011-09-05
Previously I used my Nokia E63 to connect to MythWeb and selected “Listings” and then the channel to see what was scheduled on that channel at that particular time and could scroll forward and back as required and select recording etc.  Following the upgrade from 0.23 to 0.24 I can no longer get listings to work from my E63 and all works as normal from any PC based web browser client connecting to MythWeb.
   
  Now when I select listings and then the channel I am taken to a screen with the current date and the  Jump button with no listings below.  I cannot figure out why this no longer works.  I downloaded a different browser to the E63 with no good effect.  I tried the reset MythWeb template default command from the PDA browser (?RESET_TMPL=true) which also did not work.
   
  Everything work Ok using MythWeb from any computer or laptop based browser but does not work anymore from the Nokia.  >From the Nokia all of the other MythWeb functions also work fine – Upcoming Recordings, Recorded Programs and Backend status display all the required data but not Listings.
   
  How do I fix this.
   
  Many Thanks

---

### Post by joshoekstra on 2011-09-07
What does apache tell you?
Might shed some light on the cause of your problem.

---

### Post by Tonyr63 on 2011-09-16
The Apache2 error log files telles me nothing about the nature of this error.

Note it worked fine in version 0.23 and on upgrade to 0.24 it stopped working in version 0.24 and it would appear no one has a resolution or troubleshooting suggestion.  I received confirmation from another user that the Nokia E71 has a similar problem with Mythweb 0.24 so mythweb canot be used reliably on PDA devices and no one will provide any support.  This is very frustrating as it is a very important user convience taken away with a so called improved release of Myth.  So many people use smartphones these days and MythWeb does not properly support these devices.  Obviouslu there is no backward compatability testing conduct on each new release because my Kworld  DVB 160 also was killed off by the upgrade with no assistance provided on this issue either.

---

### Post by joshoekstra on 2011-09-19
> **Tonyr63 said:**
> The Apache2 error log files telles me nothing about the nature of this error.

Note it worked fine in version 0.23 and on upgrade to 0.24 it stopped working in version 0.24 and it would appear no one has a resolution or troubleshooting suggestion.  I received confirmation from another user that the Nokia E71 has a similar problem with Mythweb 0.24 so mythweb canot be used reliably on PDA devices and no one will provide any support.  This is very frustrating as it is a very important user convience taken away with a so called improved release of Myth. ** So many people use smartphones these days and MythWeb does not properly support these devices. ** Obviouslu there is no backward compatability testing conduct on each new release because my Kworld  DVB 160 also was killed off by the upgrade with no assistance provided on this issue either.

I don't have any problem with my android-phone and tablet, I can switch to the 'normal' desktoptemplate and that's shown fine as well. I don't like the iPhone like menu, but there's choice.

Testing backward compatibility is pretty much impossible as there are way too many commbinations possible, besides as long as the device works via one of the supported API's it shouldn't matter which version of mythtv you use.

---

