---
title: "Dial-up modem in Jaunty"
date: 2009-08-16
forum: Networking &amp; Wireless
---

### Post by pcal on 2009-08-16
Hello folks. I'm trying to help my Father get his pc going again, after he took my advice and upgraded from an old version of Xandros (which was working ok), to Ubuntu 9.04, in which he can't get his dial up modem to work. [boy am I in trouble] Hardest part is, he lives quite some way away, and I'm doing it all by phone.

I talked him into signing up for an adsl connection (trying to bypass the problem), but the isp has just come back with the fact that all available ports in the exchange are full, so the old 56k modem is the only option. (lucient chip based external hardware modem via serial port)

I already installed gnome-ppp for him when he had the machine here at my place. When he got home and connected the modem, gnome-ppp would dial the modem ok, and the isp confirmed that a valid connection was being made, but none of his internet applications could find a route to the net. They all just tried, and fell back to "offline mode".

Then I found the 9.04 documentation at [https://help.ubuntu.com/9.04/internet/C/modem-connect.html](https://help.ubuntu.com/9.04/internet/C/modem-connect.html) which promised to solve the problem. I faxed him a hardcopy of that page. He followed the instructions (had to download the gnome-network-admin package on a neighbours pc), which seemed to work ok, but still no connection joy. The modem doesn't even dial now when network applications are run. The modem is set to default route to internet, but nothing seems to be happening.

While I know more about linux than he does, I'm certainly no expert. My pc reputation is teetering on the brink, and I have to make a trip to his place to "sort it all out", but have no idea what is going on. Can anyone point me in the right direction? Please!

Regards,

Pcal

---

### Post by pcal on 2009-08-18
Please folks. Any suggestions more than welcome...

---

### Post by cascade9 on 2009-08-18
I would guess that the old lucent serial modem is a winmodem. When I tried to get a winmodem running with linux, it was no end of trouble.Probably less than you, as ppp wouldnt even find the modem. 

I would try removing whatever software you've installed to try to get it running, and see if the linmodem drivers help-
[http://www.linmodems.org/](http://www.linmodems.org/) 

This is assuming that ubuntu hasnt got the linmodem drivers already (last time I tried winmodem with linux it was mid-2004, there wasnt even a ubuntu around then). 

The only other option I can think of is to try to find a 'real' modem, you know..one with a hardware controller. If you can find one, they should be very cheap now...I picked up one for about $15 US brand new in 2006. 

Sorry if that doesnt help much

---

### Post by pcal on 2009-08-18
Thanks for the suggestion Cascade. Unfortunately, it is already a hardware modem, not a winmodem. And it was working fine under Xandros, which has a common ancestor with Ubuntu in Debian.

If Xandros was still offering service - I'd downgrade him back to that, but the old CD for the version that worked is cactus now, and Xandros got into bed with M$ a while ago if I recall correctly - which is the main reason I ditched Xandros some time ago in favour of Ubuntu.

I figure there must be a disconnect somewhere within the os. The modem can connect if we use gnome-ppp - but the apps can't find the net...

Can anyone suggest a diagnostic tool that can "traceroute" the data flow from firefox etc through the os to the net? I'm fairly confident we have the net at one end of the system, it's just got lost somewhere!

Thanks again,

Pcal

---

### Post by Iowan on 2009-08-18
[Here]("https://help.ubuntu.com/community/DialupModemHowto") is another modem help page.

---

### Post by pcal on 2009-08-19
Thanks Iowan. Was wading through that page when I got a call from dad...

He was messing about with the settings, trying every combination of all options, and found that it started working! He's not sure exactly what he did, but it worked.

He spent about 2 hours on-line checking a few things that he hasn't been able to get to for a while, and as Murphy would have it, 2 minutes after he disconnected got a call from the Telco telling him they had just allocated him a recently vacated port in the exchange, and his ADSL was going live today!!!

So - problem solved somehow, and then made obsolete.

Thanks for the suggestions guys.

Regards,

Pcal

---

