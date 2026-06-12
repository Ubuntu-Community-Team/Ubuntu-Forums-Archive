---
title: "No Wireless?"
date: 2009-05-06
forum: Networking &amp; Wireless
---

### Post by askates on 2009-05-06
I have a Toshiba Satellite L350 laptop I got recently. I was fed up of Vista, so I changed to Ubuntu (9.04 Jaunty Jackalope). I'm completely new to Ubuntu here. I could find my way around Windows, but I was lost in Ubuntu.

I spent most of yesterday trying to configure my laptop to work... :/ The main issue seems to be I can't connect to any wireless. The wired connection works fine, but where I'd normally get excellent signal, I get nothing. This is more in part due to the fact that the wi-fi doesnt work at all, than a weak signal or anything.

My Wireless card is an Acer AR5BXB63. Google tells me there seems to be a bit of an issue in terms of compatibility with ubuntu... Any suggestions? Wi-fi is a pretty essential feature to me, and I don't want to have to go back to Windows (well, maybe XP. But not Vista.).

Any help would be appreciated.

---

### Post by nrostn on 2009-05-06
As you googled, did you find out about this page:

[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)

That document and the other ones mentioned in the "Getting started" paragraph provide a step-by-step guide on resolving connection issue.

Hopefully it can help you.

---

### Post by askates on 2009-05-06
According to that article, if you type ```
lspci
``` into the terminal, it lists your wireless adapter under 'Network Controller'. Nowhere does it say Network Controller. It has an ethernet controller listed, but ethernet controllers deal with connecting to LAN, don't they...?

---

### Post by askates on 2009-05-06
Argh, I'm seriously irritated with this. I called up a computer store to see if they could help, but they said they dont really know linux, and would charge £40 p/h.

I've tried everything I've found on Google. Madwifi doesn't seem to support my wireless adapter. I can't get Ndiswrapper to work, and linux-backports-modules-jaunty doesn't seem to work... Neither do the many other things I tried. Im stuck.

Anyone?

---

