---
title: "WICD and Network Manager NOT reconnecting properly"
date: 2009-12-30
forum: Networking &amp; Wireless
---

### Post by Hanto on 2009-12-30
[SIZE=4]Been using NM since 9.04, now in 9.10 and it pretty did the same thing in both O/Ss. I have tried WICD, but it does something just as bad as not reconnecting when it connects to access points that I had not selected as Auto-Reconnect. 
  Above sounds a little confusing I'm sure, so I will expound a little. NM will and does in both 9.04 and 9.10 TRY to reconnect about three times most of the time, and then it STOPS trying to reconnect forcing a person to manually restart the connection process or in some cases forces a person to do ' sudo restart network-manager ' to get the process working again for no more then three tries before it again shuts down forcing another manual restart of NM or another ' sudo restart network-manager '. All I want it to do is simply keep trying to reconnect as long as the session is active. i.e. Never stop trying to reconnect. 
  The problem with WICD is just a tad different, in that wicd does seemingly try to continually reconnect which I love, however it fails to reconnect to the AP that I told it to, i.e. it will connect to an AP that is NOT selected for auto-reconnect. 
  I've seen many of the stories that seem to indicate that wicd in the opinion of many is superior to that of NM, however IMO, if it allows itself to connect to sites I don't wish to be selected, it has already failed the most important test of all, the ability to select a preferred site for access. 
  So I have decided that it probably would be easier to somehow force or trick NM into continual attempts to reconnect rather then having it sit on its duff after about 3 tries. 
  Now many will probably wonder why I am having to reconnect so much, well lets just say that I am at an extended range to favored AP and these disconnects happen especially during the lunch hour and afternoon periods when people are out using their cell phones and shopping. At night and early morning I have far fewer issues with reconnects. 
  I had other issues with wicd compared to NM involving properly setting up  shared internet. With NM, it was absolutely easy to accomplish, but with wicd I couldn't make it work. 
  Also setting up the shares between Ubuntu/Windows machines was relatively easy using the Link-Local mode in NM. 
  So now, all I'm missing is a consistent process in NM that can be counted on to at least TRY to reconnect more then 3 times without being manually influenced by me. 
  Anyone got any good ideas????

  Thanks folks for taking the time to read this.
[/SIZE]

---

### Post by donato roque on 2009-12-31
Try spaces between paragraphs and normal fonts. please.

---

