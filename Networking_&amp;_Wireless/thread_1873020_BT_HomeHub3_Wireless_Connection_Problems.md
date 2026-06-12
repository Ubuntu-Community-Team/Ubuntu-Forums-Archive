---
title: "BT HomeHub3 Wireless Connection Problems"
date: 2011-10-31
forum: Networking &amp; Wireless
---

### Post by djadams on 2011-10-31
Hiya,  I'm a complete newbie on here but have been using Ubuntu for four years on an aged desktop and (about a year ago) I installed Netbook Edition on this Samsung N220 netbook from new.  I'm no natural, but until now have managed to solve all the little niggles I've had by lurking on here and checking out the solutions given to other peoples' problems.  This time however, I've done quite a bit of reading on here and on BT's support forum and am still struggling.  

Last week I had BT install a new line and equip it with BT Infinity high speed broadband.  With ndiswrapper installed and working fine, I've never had any problems connecting the Samsung to any wireless routers before, and sure enough, initially it seemed to connect to the newly supplied BT HomeHub3 just fine.  However, within a few minutes it was nolonger connected to the internet, although Network Manager claimed it was still connected to the wireless network.  That said, it was not possible to view the router setup page, implying all was not well...

To sanity check that the router still had internet access through the modem, I could watch streamed BBC iPlayer content through a wired ethernet connection on another machine throughout.  If I plugged the netbook in with an ethernet lead (as I have now) it all works just fine - so the modem is robust and the router is seeing the internet through it.

[LIST]
[*]Following some advice online, I uninstalled Network Manager and substituted Wicd - that made no difference but I've not switched back

[*]Following more advice, the next thing to try was a static IP address - no difference

[*]Starting to clutch at straws, I then had a go after setting up a DHCP client identifier in dhclient.conf as per instructions  [here]("http://community.bt.com/t5/BB-Speed-Connection-Issues/BT-HomeHub-firmware-upgrade-broken-network-connectivity-Ubuntu/td-p/176473/page/9")
...which other people with problems seemed to have had success with (though on a previous version of the homehub) - no difference

[*]Finally also tried turning off the network security - no difference

[*]The same netbook booted into Windows 7 connects just fine, as does my Android phone (though I only tried these two options after I'd already had the problems, so I don't *think* it's the "dual boot" or Android specific problems that some have suffered).
[/LIST]
Anyone had a similar experience?  (And fixed it!?)  

The HH3 is supposed to be high-spec so I want to use it rather than reverting to an old Netgear I used to use with my virgin cable service.  Besides, I'm a stubborn sort of geek and would like to make it work properly...

---

### Post by djadams on 2011-10-31
Have now solved this after more tinkering - posting here in case it helps someone else with similar problems...

What seemed to do it was changing the "Wireless interface type" in the HomeHub3's "advanced settings" from BT's recommended "802.11 b/g/n" to "802.11 b/g".

This also seems to have improved wireless speed when running under *(insert involuntary shudder)* Win7.

---

### Post by ninorc on 2011-12-31
I am bumping this thread because I have exactly the same problem, albeit with a different model of Samsung netbook. 

I can't implement the suggested solution because BT won't give me an admin. password to access the router settings. BT drones keep telling me that Ubuntu is unsupported!

Irritatingly, the Total bb I had before worked fine over the same hub, The only solution BT is offering me is to have Infinity un-installed.

More creative suggestions will be gratefully received. Be gentle with me, for I'm new around these parts.

---

### Post by djadams on 2011-12-31
That's very odd on two levels.  There's no secret about the admin password, [click here]("http://bt.custhelp.com/app/answers/detail/a_id/11383/session/L2F2LzEvdGltZS8xMzI1MzI2MDg2L3NpZC9sbXkyd1lNaw%3D%3D") (lists all three versions, HH3 is at the bottom)

More bizarre is that the same router used to talk to you fine when it got its broadband through ADSL...  Do you have other things connected to the hub which still work fine?

My N220 was problematic on wireless n (and a friend with a different "n" router had the same problem with his Samsung NC10).  Since switching our respective routers to "b/g" neither my nor my mate's machine has given problems.  It just seems the Samsung wireless card can't handle n - but that shouldn't depend on what internet connection the router is connected to!

HTH, dj.

---

### Post by ninorc on 2011-12-31
Ah, thanks. All I needed was the p/w that's on a plastic card that slips into a slot on the Hub3 (ahem).
Told you I'm not v. bright. All sorted now, thanks very much. 
I guess my netbook won't work on other networks, which is a drag.

---

### Post by djadams on 2011-12-31
Glad to hear it works for you too.

> **ninorc said:**
> I guess my netbook won't work on other networks, which is a drag.

Seems to be the case, and it's not a Ubuntu issue either as the same is true for mine on Win7.  I don't know if it's genuinely a hardware issue, or whether there could one day be a driver update that would make the little Samsung speak "n".  Not a big problem for me though, it has to be said.

---

### Post by ninorc on 2012-01-01
Oops, I spoke too soon. Changing the wireless interface type to  "802.11 b/g" from BT's recommended "802.11 b/g/n" - i.e.: using 'G' rather than 'N' - worked yesterday, but not today! This morning, the problem is back. Strange, but as you said:

> **djadams said:**
> 
More bizarre is that the same router used to talk to you fine when it got its broadband through ADSL...  Do you have other things connected to the hub which still work fine?HTH, dj.

My netbook - it's an N310 - works when connected  by ethernet. I'm currently getting 30+Mbps, wired, and nothing much, wirelessly, although the connection is showing as 95% strong! Switching between Auto eth0 & wireless, testing  the speed drops slowly (i.e.: not immediately) away. I also had the same problem (but no ethernet cable) at the house I visited over Xmas. 

> **djadams said:**
> 
My N220 was problematic on wireless n (and a friend with a different "n" router had the same problem with his Samsung NC10).  Since switching our respective routers to "b/g" neither my nor my mate's machine has given problems.  It just seems the Samsung wireless card can't handle n - but that shouldn't depend on what internet connection the router is connected to!
HTH, dj.

Exactly. Having read BT's online advice, I realise that my N310 must be 'N' compatible. Part of the reason I swithced to BT was to get a stable wireless signal & it's been fine for 2 months, but I needed more bandwidth and was persuaded to switch to Infinity because it's the same price for a better service.
My netbook is a couple of years old and has  so far worked faultlessly, everywhere.

---

