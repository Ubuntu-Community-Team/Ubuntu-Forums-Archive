---
title: "Network Manager &amp; Static IP issues"
date: 2010-07-04
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by VastOne on 2010-07-04
Running Meerkat Alpha 2

Network Manager pulls a DHCP no issues - Connect to the Internet

Tried to change to static first by editing /etc/network/interfaces

Results - No Internet

Changed to static within Network Manager 

Results - No Internet

Installed WICD, made the changes to static and restarted the network

Results - Internet

Disabled Network Manager - Ensured WICD still had the correct static 

Results - No Internet

Only way I have been able to get a static IP is to have Network Manager establish a DHCP and then start WICD to change to the static I need and restart the network.

Am I an island or has anyone else seen this bizarre behaviour?

---

### Post by hikaricore on 2010-07-04
I simply remove network mangler whenever i need a system with a static ip.
It's supposed to make things easier but it only does so if you never touch it...

---

### Post by cariboo on 2010-07-04
I use network-manager to set static ip addresses on all my systems running Ubuntu. Go to the IPv4 tab and set everything to manual, then enter your ip address, netmask and gateway, pressing enter after each address. I then enter my isp provided dns addresses, and click apply. To use the new settings, either reboot, or disable and then enable networking via the NM icon in the top panel

---

### Post by VastOne on 2010-07-04
> **cariboo907 said:**
> I use network-manager to set static ip addresses on all my systems running Ubuntu. Go to the IPv4 tab and set everything to manual, then enter your ip address, netmask and gateway, pressing enter after each address. I then enter my isp provided dns addresses, and click apply. To use the new settings, either reboot, or disable and then enable networking via the NM icon in the top panel

Did this to no avail.  Made sure to reboot and that the settings were maintained and still had the same issue - no internet.  Route and trace showed all DNS and gateways are as they should be.

Appreciate the help.

---

### Post by x-shaney-x on 2010-07-04
Think it may be a specific problem to your hardware/configuration.

I setup a static IP on 2 different comps here and both are connecting fine.
Didn't need to reboot, just clicked on the wireless connection in the panel menu and let it disconnect and reconnect.

Not sure if it is related to the static IP but I have noticed it takes much longer to connect than on lucid (20-30 seconds AFTER the desktop has loaded usually, sometimes a little quicker).

---

### Post by VastOne on 2010-07-04
> **x-shaney-x said:**
> Think it may be a specific problem to your hardware/configuration.

I setup a static IP on 2 different comps here and both are connecting fine.
Didn't need to reboot, just clicked on the wireless connection in the panel menu and let it disconnect and reconnect.

Not sure if it is related to the static IP but I have noticed it takes much longer to connect than on lucid (20-30 seconds AFTER the desktop has loaded usually, sometimes a little quicker).

Not specific to the hardware. I can boot to lucid on the same machine and it works as it should.

---

### Post by x-shaney-x on 2010-07-04
> **VastOne said:**
> Not specific to the hardware. I can boot to lucid on the same machine and it works as it should.

What I meant was something related to the drivers in meerkat that deal with your particular hardware or setup.
I remember way back when I upgraded to dapper drake, it was unusable due to networking and display problems even though the same hardware had been working 100% perfectly with the previous release.

---

### Post by VastOne on 2010-07-04
> **x-shaney-x said:**
> What I meant was something related to the drivers in meerkat that deal with your particular hardware or setup.
I remember way back when I upgraded to dapper drake, it was unusable due to networking and display problems even though the same hardware had been working 100% perfectly with the previous release.

I see..

Strange thing is that the drivers work fine for DHCP only.

But this is the nature of the beast of pre-Release beta and alpha testing.

I will look at some more options and try reproduce it on another machine and then head over to the bug reporting.

Thanks for your help.

---

### Post by lisati on 2010-07-04
<aside>

I prefer to set static IPs via my router, just in case I take my laptop somewhere and want to avoid allocation problems e.g. my choice of IP address is already in use or outside the netblock assigned to the network I'm connecting to.

Don't let this stop you from checking out the ways of doing it at Ubuntu's end..... :)

</aside>

---

### Post by VastOne on 2010-07-04
I solved this by removing Network Manager.  Wicd has always disabled it in any other setting and worked just on an install and config setup.  On this wicd setup, I had to use static DNS servers in the properties setup of the interface, which I have never had to do before on several machines and across many builds.

Once this was done, I was internet flying...

Just FYI

---

