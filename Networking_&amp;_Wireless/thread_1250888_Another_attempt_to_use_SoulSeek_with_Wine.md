---
title: "Another attempt to use SoulSeek with Wine"
date: 2009-08-27
forum: Networking &amp; Wireless
---

### Post by deBALZAC on 2009-08-27
I've been searching these forums for running SoulSeek with Wine and I realized there's a lot of ppl who'd like to use this P2P application on Ubuntu. And all of them are having the same issue: even after a successful installation, SoulSeek can't connect to the server.

So I was wondering if that happens to other Windows apps running from Wine and I discovered some applications show to have the same connection issue.

Another program ppl love to run with Wine appears to be World of Warcraft. I thought if this is possible it means there's a way to connect an Windows application to the internet via Wine, it's an MMORPG after all. So I searched for the installation steps of WOW on Wine and among many informations I found that

>  The easiest way to open these ports is to use the firewall program Firestarter.  

[LIST]
[*]From the command line, install Firestarter with this command: sudo apt-get install firestarter.
[*]When it is running, select the "Policy" tab, right-click in the Allow Service area, and select Add Rule.
[*]Under port, type 6112 and make sure that the "Anyone" radio button is selected. Make a note in the comments field that this port relates to Blizzard.
[*]Repeat these steps for ports 3724 and for the range 6881-6999 (which will be recognized as [BitTorrent]("https://help.ubuntu.com/community/BitTorrent") ports).
[/LIST]
(quote from [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft) )

I have Firestarter already installed on my PC and it works great for its purposes.

It happens that I'm not an advanced Linux/Ubuntu user and I don't understand much about networking technical aspects, so I don't know what ports I could use to enable SoulSeek to go online and/or if there is a way to manage this at all.

So,

I'd like someone---kind of an adventurer, I may say---to plz check if it would be possible to do a similar operation as the quoted above to enable SoulSeek to go online,

and

If such strategy would be feasible, to plz share it step by step?

I'm considering the hypothesis that someone else had this idea before once it seems so obvious but still I had to try. I'm sure I'd not be the only one to thank for that LoL

---

