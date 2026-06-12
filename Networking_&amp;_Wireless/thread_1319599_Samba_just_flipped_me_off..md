---
title: "Samba just flipped me off."
date: 2009-11-08
forum: Networking &amp; Wireless
---

### Post by Roasted on 2009-11-08
I'm on my main computer which is a samba file server for the entire house. Okay, fine. I'm also playing with a 2nd computer of mine via SSH that's here on the work bench. I was setting up samba on the 2nd computer and I was connecting to it from my main computer. Out of no where, I go to places - network - windows network... and bam... nothing is there.

Why did Samba magically just decide, nah, I'm not interested in showing you your Windows machines on the LAN or your own file sharing service.

From XP in a virtual machine I can still hit my file server just fine, so I know the service is running (I've restarted the service several times). But I don't know why my own file server can't see it's own shares. 

W... T... F...

EDIT - So I think I know what happened. I'm remotely setting up a 2nd samba server on the network, and I was having an error when connecting to it. I realized it was because the user I was logging in as didn't have authentication to the share on my 2nd samba server. So I had to edit it quick. When I tried again to connect, it errored out with unable to retrieve server list. I'm not sure if this is because I tried to log in so many times or not, but it errored out. Ultimately, I did nothing, and minutes later I went to places - network and the shares showed up again. What was samba doing that it stopped showing them and, oh, actually, here they are again?

But just now I repeated the EXACT same thing and it gave me the same error, and now no shares (linux or windows) show up under places - network. I assume they will come back in another 2-3 minutes like they did last time.

What kind of issue is this? Ubuntu? Network? Router? DNS?

---

