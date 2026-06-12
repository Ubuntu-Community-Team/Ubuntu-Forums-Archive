---
title: "No &quot;Enable Wireless&quot; entry in Network menu"
date: 2011-04-12
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by johnmollaghan on 2011-04-12
Using a Dell Inspiron 1501, had been using wireless on this for all previous Ubuntu versions. It does require installasion of a Broadcom driver using the additional drivers, never caused any problems.

Now after updating to 11.04 beta, when I drop down the Network menu from the toolbar, the "Enable Networking" is ticked but there is no menu entry labelled "Enable Wireless". Also, no sign of any wifi networks.

So, cannot activate the wireless.

Any ideas on how to enable wireless in 11.04 in this situation?

---

### Post by MightyMouse on 2011-04-12
Have you tried to check for 'Additional drivers'?
What happens when you do iwconfig in a terminal?

---

### Post by grahammechanical on 2011-04-13
Have you tried un-ticking the line Enable Networking and then ticking it again? I cannot say for sure but I think that when I installed 11.04 Beta Edubuntu about two weeks ago I had the same situation as you. I connect by ethernet but on standard ubuntu 10.10 I can also get a wireless connection. So, I switched of networking and then switched it back on and now this 11.04 Beta makes both an ehternet connection and a wireless connection and the line Enable wireless is in the menu.

Regards.

---

### Post by calvin mitchell on 2011-04-17
I'm having trouble with this also.  Ubuntu prompted me to allow the installation of proprietary drivers and the "Additional Drivers" module shows that Broadcom STA wireless drivers are installed and in use.  In previous Ubuntu installations the additional drivers worked with no problems.

However, in 11.04 there is no wireless connectivity.

I also manually installed b43-fwcutter and the firmware, but still can't get wireless.

Help?

---

### Post by stanz on 2011-04-17
> **calvin mitchell said:**
> I'm having trouble with this also.  Ubuntu prompted me to allow the installation of proprietary drivers and the "Additional Drivers" module shows that Broadcom STA wireless drivers are installed and in use.  In previous Ubuntu installations the additional drivers worked with no problems.

However, in 11.04 there is no wireless connectivity.

I also manually installed b43-fwcutter and the firmware, but still can't get wireless.

Help?

On my dell inspiron 1546 the STA driver is enough.
I had to configure my wireless 'for all users' when configuring ssid and such.
possible users & group modify--to give permissions?
Also, I've stopped using b43-fwcutter, with the STA, not needing it- or to install needlessly.

Wireless working at all?

---

