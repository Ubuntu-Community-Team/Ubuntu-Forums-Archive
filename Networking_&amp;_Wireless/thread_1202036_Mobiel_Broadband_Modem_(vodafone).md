---
title: "Mobiel Broadband Modem (vodafone)"
date: 2009-07-01
forum: Networking &amp; Wireless
---

### Post by beercz on 2009-07-01
Hello all

Earlier today I received a Vodafone Mobile Connect USB Stick - K3520-Z. (on a contract).

I plugged it in and Ubuntu does not seen to recognise it.

In the Network Connections application I have tried to set up the Mobile Broadband connection to no avail.

Anyone out there know how I can get this modem working?

Thanks in advance.

---

### Post by solitaire on 2009-07-01
Search the repos for "Vodafone-Mobile-Connect" 
It should be in Networking (Multiverse) It should get the USB working..

---

### Post by beercz on 2009-07-01
Thanks for the reply Solitaire

I have solved this.

I didn't manage to install "Vodafone-Mobile-Connect" from the repros - it wasn't found.

However, I managed to download the relevant packages from the [betavine]("https://forge.betavine.net/frs/?group_id=12") website and install them.

Then I had to make myself a member of the "dip" group:

> sudo addgroup ian dip

After that everything worked, I simply ran Applications->Internet->Vodafone Mobile Connect and walked through the wizard.

Simple in the end.

I hope others find this information useful.

---

