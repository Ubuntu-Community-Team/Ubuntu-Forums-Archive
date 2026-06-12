---
title: "Intermittent DNS resolution issue 9.10"
date: 2009-12-03
forum: Networking &amp; Wireless
---

### Post by rhsanborn on 2009-12-03
I am having an intermittent issue on two computers running vanilla Ubuntu 9.10. The first is an HP laptop with a built-in Broadcom chipset running the proprietary driver. The second is a custom built desktop with a USB Belkin card that has a ralink chip in it. I believe it, too, is running a proprietary driver. Both computers have an intermittent problem where they appear to resolve all addresses to a seemingly random address (I've seen yahoo, amazon, a cincinatti state university site...) or it's failing to find the address and forwarding it as a query to my default search, which it also isn't handling properly, since I've never set my default search for Cincinatti State's website.

After several minutes, the problem tends to clear up and I can browse normally. I've tried using alternative browsers including Firefox 3.5, Opera 10, and even Lynx. The problem appears on all of them.

Has anyone seen anything similar. I've done a couple searches on DNS and haven't come up with anything.

EDIT:

While this problem is happening on the Ubuntu 9.10 box, I can browse to the same sites just fine using Windows XP, Vista, or Maemo via my Nokia Tablet.

EDIT 2: 

Shortly after submitting this, I had an issue getting to slashdot on the laptop. I tried pinging the laptop resolved slashdot to 75.146.48.33 while the tablet resolved it to 216.34.181.45. Both attached to the same, Verizon provided, DSL modem/wireless router.

---

### Post by rhsanborn on 2009-12-05
Update: I'm having issues right now. I found a site that I couldn't get to: ws.arin.net. Ubuntu laptop is resolving it as 32.1.5.0 (which isn't correct). My Nokia tablet (Maemo, debian based) and Windows 7 desktop resolve ws.arin.net to 199.71.0.44 which is correct and goes to the right place.

I tried the following command to flush the dns cache:
sudo /etc/init.d/dns-clean start 

It didn't change anything, the Ubuntu machine still resolves to 32.1.5.0. All three machines are going to the same two DNS servers. The first DNS server is the wireless router, and the second is a DNS server provided by the ISP (Verizon).

---

### Post by rhsanborn on 2009-12-06
I removed both of the DNS servers provided by the router via DHCP and replaced them with the free Google DNS servers as a test. I haven't had any trouble in the last day (which is exceptional). I suspect Ubuntu and the kernel it's built on uses the DNS servers differently than my tablet and Windows machines. Does it, perhaps, query the DNS servers in a round-robin fashion? Whereas Windows may only use the primary? In any event, it appears to have been resolved. I'll keep researching it before putting it in solved status.

---

### Post by yelvington on 2009-12-19
I think you're absolutely right: Ubuntu 9.10 is round-robin querying multiple DNS servers. **This is an undesirable change from previous behavior.**

On my home network, I have a server running dnsmasq to provide internal DNS services. For years, I have had my wi-fi routers set up to use the internal server first, and fail over to external DNS if, for any reason, my internal server isn't working.

Suddenly I can't get my email from my internal server. Then, I can. Then, I can't. WTF?

Running the "host" command returns the internal address, so I start to blame the problem on Thunderbird. But then I run "host" again ... and again ... and again. I get alternating results: Internal address, then external address, then internal address again.

There's no delay, no hang ... so it's not a DNS failover. It's Ubuntu 9.10 playing Russian roulette with DNS. This sucks.

Now I suppose I have to reconfigure my routers so there is no failover at all, which I do not like.

---

