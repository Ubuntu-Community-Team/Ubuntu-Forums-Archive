---
title: "Ups"
date: 2011-04-07
forum: Mythbuntu
---

### Post by lmclaren on 2011-04-07
Hi,

I installed a UPS on the system yesterday due to the unreliable power in the area.

I used an Eaton 5110 and was ready to install nut etc but found mention of "Eaton IPP"

Basically it is a native full browser based GUI for the UPS with good graphing etc.
I was pleasantly surprised by how easy to install and how good it is.

After you choose an OS you still need to select on the left hand side Linux - Xen - KVM to see the Linux options, there is a .deb for Ubuntu.


I have no connection with Eaton etc, just surprised that to find a well supported under Linux product.

Lee

---

### Post by LowSky on 2011-04-10
Linux is super popular in the Server world. UPS are needed for any business that needs its components to stay up in any situation.

---

### Post by SeijiSensei on 2011-04-10
Does Eaton provide daemons that monitor the power and shut down the system gracefully when needed like [**apcupsd**]("http://packages.ubuntu.com/lucid/apcupsd") for APC power supplies?  What's especially nice about apcupsd is you can configure one machine as a server to monitor the power supply, and any other machines on the network can be configured as clients that will be notified if the server decides a loss-of-power condition requires a shut down.

---

