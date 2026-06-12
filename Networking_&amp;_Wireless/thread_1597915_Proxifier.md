---
title: "Proxifier"
date: 2010-10-15
forum: Networking &amp; Wireless
---

### Post by nojstevens on 2010-10-15
I am looking for a program similar to the Windows 'Proxifier' - the use case I have is I want to direct certain IP requests to TOR whilst leaving other IP requests directed via my normal route.

Can anyone recommend a package for ubuntu that would handle such a task?

Thanks

Jon

---

### Post by jago25_98 on 2010-10-15
I use FoxyFroxy for Firefox for this. 
If you wanted to do it with something outside the browser though... hmm... perhaps something could be done with `route` or `proxychains`... 

I came on here originally to find a sftp program supporting proxies (can't believe there isn't one out there for linux!!)

---

### Post by nojstevens on 2010-10-15
> **jago25_98 said:**
> I use FoxyFroxy for Firefox for this. 
If you wanted to do it with something outside the browser though... hmm... perhaps something could be done with `route` or `proxychains`... 

I came on here originally to find a sftp program supporting proxies (can't believe there isn't one out there for linux!!)

Thanks for the help - I am looking to force certain IP requests from XBMC over to Tor so I can watch BBC iPlayer from the USA without having all of my IP traffic go via Tor

Jon

---

### Post by jago25_98 on 2010-10-16
ah I getcha. 

To be honest I don't know exactly how to do that but I know for sure it's very possible... just trying to think how to approach it. 

I guess you could do it with iptables. First, tag everything you want somehow and then forward it to a different interface... that interface could be virtual. 

To be honest I don't think you're gonna get much help here on the Ubuntu forums. One thing I've noticed is that Ubuntu tends to have a higher % of n00bs... post anything on the forum (or indeed irc) needing a bit more skill and there's just no answers. Better to ask on linuxquestions.org for stuff like that, or another distro (being careful to think about the differences between the distros and sensitive of the fact that they're expecting you to use the same distro - don't waste time). 

Just trying to think laterally...
if it were me I'd try to find a simpler way of doing it. For example, 
have 2 ethernet cables to plug or something like that. 

Only reason I say this is because I personnally find iptables confusing enough as it is. So it may be just a whole lot simpler to find a simpler way of doing it. 

For example, have a Xen virtual machine just running iplayer. In that Xen machine connect to a VPN and route everything in the Xen machine through that. 

Other than that I guess it could be (is iplayer available for linux now?)

$proxychains ./iplayer
to run through a proxy. 

good luck. If you do go the iptables route with `mark` and all that post us how you did it here; would be handy to know. 

-j

---

### Post by jago25_98 on 2010-10-16
as I say though, I'm sure it could be done with the route command?

$man route


?

---

