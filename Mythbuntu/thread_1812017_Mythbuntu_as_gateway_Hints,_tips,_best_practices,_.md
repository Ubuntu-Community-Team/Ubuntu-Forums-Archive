---
title: "Mythbuntu as gateway? Hints, tips, best practices, etc.?"
date: 2011-07-25
forum: Mythbuntu
---

### Post by bs27975 on 2011-07-25
I have a new box on order. I gave up on LinuxMCE some time ago, and it seems to me that Mythbuntu (on top of Kubuntu) is the way to go. [Let's not debate OS choice, in this particular thread.]

I believe the Mythbuntu functionality to be very near to the LinuxMCE functionality (don't care about the home control / automation stuff, at least not at the moment). Granted, I believe, this really means the underlying MythTV functionality, let alone all the additional functionality Myth pulls in, such as 'asterisk' (whatever they're calling that today), caller id display on the TV screen, and so on and so forth.

Calling it an 'MCE' may be a misnomer, home server may be more accurate (file/media corralling, messaging, voip, dhcp, proxy, etc.) [i7-2600k, 8GB, ASRock Extreme 4 (i.e. onboard HD3000 video), 1080p hdmi TV] No matter what you call the purpose of the box, from an MCE perspective, more than MythTV is involved, and the purpose/advantage of MythBuntu is to help pull the disparate applications together into as much of a cooperative / coherent whole as possible.

To that end, it feels like there would be some synergy in having this box also be the gateway / having all this on one box - inter-application cooperation / 'ease' of configuration, not trying to coordinate two separate boxes, and so on and so forth.

Are there pointers to links and advice out there as to instructions / best practices of setting up this Mythbuntu box as a gateway? (Perhaps as an addendum [the gateway aspects] to Mythbuntu install docs, on the assumption such is not directly addressed within the Mythbuntu install docs?)

Thanks.

---

### Post by nickrout on 2011-07-25
It is very bad practice to use a firewall for anything else. Dedicate a box to that job. mythtv is very insecure, and should certainly NOT be put on a gateway.

PS have you opened another thread on a similar subject?

---

### Post by bs27975 on 2011-07-25
> **nickrout said:**
> It is very bad practice to use a firewall for anything else.

That is a misnomer, and it is no credit to you to spread the FUD.

There are circumstances where that is true, and circumstances where it might not be - the *circumstances must be considered* - the risk environment, the risk exposure, the scope of the risk, the likelihood of risk occurrence, cost of risk mitigation, and the potential cost of risk remediation. In a business environment, with lots of space, hardware, and dollars, it is most definitely true that separate firewall hardware is appropriate. Particularly as what is at risk is significant, perhaps even 'bet your business' risky.

In the home, the risk is most definitely different, the likelihood of the risk being realized much lower, and the impact of a risk being realized likely more bearable.

From a functionality perspective, your blanket statement is also not true. In a corporate environment, where the space and expertise likely exists to support multiple boxes - vpn endpoint, web server, IPSec passthru, routing, it makes sense, but, note that functionality such as UPnP or TV playback / recording is not normally present. Yet, there are many boxes out there, primarily for SMBs, that combine a number of these functions into one, again sans media capabilities - that are sufficiently secure or would not still be on the market. (They would have been laughed out of existence by now.) For the home, similar devices as these SMB ones are usually used, and include additional capabilities, such as UPnP, media sharing, and so on and so forth. Clearly, in appropriate circumstances, the desired functionality is only reasonably accomplished within one box.

Your blanket statement is most definitely incorrect - it is not true in all cases, all of the time.

Being in the business of computer network / security, I am making an experienced expert decision, in this case, to try running this way. My choice to make.

Returning, now, to the question posed ...

> **nickrout said:**
> Dedicate a box to that job. mythtv is very insecure, and should certainly NOT be put on a gateway.

In this case, I choose to trust Linux FOSS to have developed as sufficiently bulletproofed firewall by now.

If your statement here were true, distributions like LinuxMCE would not exist.

Do you have links that discuss the issues involved?


> **nickrout said:**
> 
PS have you opened another thread on a similar subject?

Sort of, but not the same. Gateway and firewall (app) are / can be distinct issues. Separate searches on each revealed no authoritative answers within the Mythbuntu forums, so I'm trying, here, to establish authoritative answers / posts / threads for people to find, via separate lines of questions.

---

