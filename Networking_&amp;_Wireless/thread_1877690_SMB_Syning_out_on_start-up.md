---
title: "SMB Syning out on start-up"
date: 2011-11-08
forum: Networking &amp; Wireless
---

### Post by Coyote23 on 2011-11-08
Hello all, 

I have noticed something funny and I have been unable to find a valid cause. When I start Thunar it takes roughly a minute to load - this is after a reboot/cold start. I discovered gvfsd-smb-brow is sending a syn to an external IP and waiting for a response. If I set my firewall to REJECT the connection Thunar loads immediately. 

The IP in question is 92.242.132.15. WHOIS lookups have revealed it to be owned by barefruit.co.uk. It seems rather odd for this to be hard coded into the application itself as my Arch laptop seems to do the same thing - my laptops quite sluggish so I never noticed until now.

Has anyone else noticed this?

Coyote23

---

### Post by capscrew on 2011-11-08
> **Coyote23 said:**
> Hello all, 

I have noticed something funny and I have been unable to find a valid cause. When I start Thunar it takes roughly a minute to load - this is after a reboot/cold start. I discovered gvfsd-smb-brow is sending a syn to an external IP and waiting for a response. If I set my firewall to REJECT the connection Thunar loads immediately. 

The IP in question is 92.242.132.15. WHOIS lookups have revealed it to be owned by barefruit.co.uk. It seems rather odd for this to be hard coded into the application itself as my Arch laptop seems to do the same thing - my laptops quite sluggish so I never noticed until now.

Has anyone else noticed this?

Coyote23

This is an incorrect DNS redirect by your whoever is suppling you DNS (ISP?).  I would use Google's DNS servers (8.8.8.8 and 8.8.4.4).

Edit:  When you block the request can you still browse for shares on the network?

---

### Post by Coyote23 on 2011-11-08
> **capscrew said:**
> This is an incorrect DNS redirect by your whoever is suppling you DNS (ISP?).  I would use Google's DNS servers (8.8.8.8 and 8.8.4.4).

Edit:  When you block the request can you still browse for shares on the network?

Yeah, I can use Samba without any issues with the rule in place. 
My DNS is provided by my ISP who can be a bit finicky, using Google's servers has crossed my mind before but I've never found a reason to set it up.

Coyote23

---

