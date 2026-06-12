---
title: "Intrepid - choppy or chirping streaming audio - Solved"
date: 2008-12-28
forum: Multimedia Software
---

### Post by tgilber1 on 2008-12-28
Had a problem with chirpy or choppy streaming audio that I have been trying to figure out for the past couple of days.  What made this problem more perplexing is the trouble would not manifest all the time.  It appears that the problem manifests when the streaming audio has tags.  The good news is I think I have isolated the problem to the proxy settings.

Setup:

Ubuntu 8.10
Dansguardian 2.9.9.7-2 - http/https are forwarded to port 8080
Squid 2.7.STABLE3-1u - transparent proxy on 3128
Gnome 2.24.1

Couple of iptables rules to make sure that no one bypasses dansguardian

iptables -t nat -A OUTPUT -p tcp -m tcp --dport 80 -m owner ! --uid-owner proxy -j REDIRECT --to-ports 8080

iptables -t nat -A OUTPUT -p tcp -m tcp --dport 3128 -m owner ! --uid-owner dansguardian -j DROP

gnome-network-preferences - enabled proxy to port 8080 so I could get my weather and stock ticker (Invest 2.24.1) applets going.

The chirping audio does not work when I apply the system-wide change for network proxy in gnome-network-preferences.  Additionally, any streaming audio with id tags will not come through because of this issue.

To fix:

1.  I had to set back proxy to direct, then I applied change, system-wide
2.  Next, I re-enabled the proxy and click the close button.  Note, do not apply change system-wide.

After following these two steps, the chirping audio stopped, and audio players (e.g., rhythmbox/exaile) displayed the id tags of the streaming songs.

Hope this helps!

---

