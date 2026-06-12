---
title: "ubgraded to ubuntu but the network is still widows..."
date: 2012-06-10
forum: Networking &amp; Wireless
---

### Post by naftali mich on 2012-06-10
I was dual booting windows 7 and ubuntu on my desktop. I  configured a tp-link wr940N router from the windows 7 desktop, and I'd  use a windows 7 laptop via wifi.
  
I just wiped windows and installed ubuntu 12.04 on both the desktop  and the laptop. No problem connecting to the internet, whether on the  ubuntu desktop or the ubuntu laptop (through wifi) but the network  definition is still a 'windows' network, and I'm not able to see one  computer from the other. I guess the router is just doing it's thing, as  if nothing changed.

  I'm know I'm missing something. What do I need to do to have a regular home network?

(edit 1, from response to VE6EFR, below)
 
When I opt to share a folder, the system prompts me  that "You need to install the Windows networks sharing service in order  to share your folders. " When I click the 'install sharing' button, it  goes into my wanting to install samba, which maybe i could do, and maybe  would work, but since all the computers on the network (2) are ubuntu  machines, I'd hope to find a way to reconfigure the network correctly,  if possible.


(edit 2) 

I can ping one computer from the other, so I guess at the ip layer and down, at least, all is good. So maybe I can just work with it as is...., but I really do want to understand what's going on, and what happened, even if I can't fix it. 

If anyone can explain what going on, even if you don't know a solution, please chime in.

(edit 3)

so I created a shared folder using samba on each of the two machines, and though I can see an icon representation of the two machines on the machines, in browse network -> windows network -> workgroups. I can't actually view anything when I click on the icons. The operation simply fails. I can provide more detail, should it prove important.

---

### Post by VE6EFR on 2012-06-10
I have not tried it here, but you may need to share the folder on each computer that you want to share from.

If you right click on a folder you can set sharing options.

---

### Post by naftali mich on 2012-06-10
Thanks for that. When I opt to share a folder, the system prompts me that "You need to install the Windows networks sharing service in order to share your folders. " When I click the 'install sharing' button, it goes into my wanting to install samba, which maybe i could do, and maybe would work, but since all the computers on the network (2) are ubuntu machines, I'd hope to find a way to reconfigure the network correctly, if possible.

---

