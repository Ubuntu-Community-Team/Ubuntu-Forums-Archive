---
title: "Help Me Find a Prism * Device, Please!"
date: 2006-05-29
forum: Networking &amp; Wireless
---

### Post by polo_step on 2006-05-29
[FONT="Courier New"]The second part to the business of Linux being near-crippled in terms of wireless is that in addition to modern devices being weakly supported by the OS, a great many Linux programs that involve wireless will themselves not work on modern wireless products, even once you have achieved net connectivity.

I was having a look at the very interesting new "BackTrack" live CD but was sad to see that almost all of the programs seem to be for the old Prism 2 chip or its descendants.

I really would like to be able to fiddle about with this stuff, but I need to find some sort of a wireless thingy that will work.  All the online lists I see are about four years out of date.

Can anyone give me some helpful advice here?

As always, thanks for any assistance!

[http://www.remote-exploit.org/index.php/BackTrack]("http://www.remote-exploit.org/index.php/BackTrack")[/FONT]

---

### Post by dicecca112 on 2006-05-29
Dlink DWL-G122 A2.  use the drivers off the cd with Ndiswrapper 1.16 by following the directions off the ndiswrapper wiki.  Works perfectly

---

### Post by jml on 2006-05-30
Another card that has the Prism 2 chip set is the original Orinoco Gold 802.11b card.  Not the version sold currently by Proxim.  You may have to go to e-Bay and see if there are any for sale.

By the way, if the applications you want can run on the Atheros chip set, there are several cards that work well.  NetGear WG 511T, Cisco Aironet 350 802.11b card, and Cisco Aironet 802.11 a/b/g wireless card.  These work well with Ubuntu and I can get them to work with Kismet on the Bactrack CD.  Have not tried any of the other apps yet.  Hope this helps.

Joe

---

### Post by hw-tph on 2006-05-31
Ralink RT2500 and similar chips from the same manufacturer have open docs and - as a result of that - open drivers as well. Real drivers, not that [evil ndiswrapper crap](http://acx100.sourceforge.net/ndis_cludge.html).


Håkan

---

### Post by polo_step on 2006-06-03
[QUOTE=hw-tph]Ralink RT2500 and similar chips from the same manufacturer have open docs and - as a result of that - open drivers as well.[/QUOTE]
[FONT="Courier New"]I have numerous RT2500 devices here and as far as I know, they don't work properly with most programs on the BackTrack CD.

On the other hand, I can't figure out how to make recognized wireless devices that have **apparently** been installed at boot actually start and run in that distribution anyway. :-k  

Maybe I need a tip on that here first, y'think?
 [/FONT]

---

