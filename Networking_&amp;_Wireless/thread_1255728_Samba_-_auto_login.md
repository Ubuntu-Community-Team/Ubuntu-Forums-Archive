---
title: "Samba - auto login?"
date: 2009-09-01
forum: Networking &amp; Wireless
---

### Post by Roasted on 2009-09-01
Just curious - I run a simple LAN at home with a workgroup and all that. When a user connects to their Samba share, they have to log in. Is there a way for me to tie in their PC's login account + samba account so when they log into their PC, Samba automatically acknowledges "You are Bob and you have xyz permissions." etc?

Or do I need to have a domain setup for that to work? 

I was just thinking like at work we have a Windows file server that automatically does this. If I were to drop a Linux storage server in place I'm curious on whether or not users could auto-login to their files.

And yes - I know about "remember password" but that's not the reason I'm asking. I'm just trying to see if we could drop a Linux file server (samba) in place without users even knowing it...

---

### Post by falconindy on 2009-09-01
When creating Samba shares in Linux, its possible to allow guest access, which requires no credentials. If your users only need read access to the share, then this is probably a good solution. If you need write access to be distributed, then you would need some sort of central authority (domain controller) to bypass an active authentication.

---

### Post by Roasted on 2009-09-14
So ultimately, as long as I want the users to retain write access to the shares, there's really no way around doing this unless I put a domain in place.

How hard is it to get a domain set up on Ubuntu? I've never tried this. Is it something relatively easy that wouldn't effect the computers much? Cause you see, I dual boot since I game a lot, so I wouldn't want to be in Vista and suddenly the computers can't log in cause the domain isn't available or anything.

---

