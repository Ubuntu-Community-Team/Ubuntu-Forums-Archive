---
title: "SSH into Ubuntu - Multiple VirtualBoxes behind Router"
date: 2013-08-09
forum: Networking &amp; Wireless
---

### Post by Greg_Bedsaul on 2013-08-09
Hi all,

I was just curious, I've used VirtualBox many times before in the past and it has been a God-send along with Ubuntu server being as amazing as well.

However, I'm having a weird problem that I seem to not be able to solve.

What happened is that I decided to create three separate Ubuntu VirtualBoxes. I also have a dyndns free address just to make it easier to connect to over the interwebs. I also have them each installed with OpenSSH and they're all using separate ssh ports and they are all forwarded through my Airport Extreme. (Save the laughs, I know, bad decision on my dads part) So, logically if I have the ports configured on my sshd_config files in each one I should be able to use a program like Kitty (great PuTTY alternative I might add) and connect to each address at example.com with whichever port that I specified in their configs.

Why wouldn't it work?

HELP!!! :O

( I might also add, I think it has something to do with how ssh works because is caching key files on the PC I'm local too, so it might be thinking to use the same key. However, I don't know how to configure that right)

---

### Post by sanderj on 2013-08-09
Can you access the different VM's from your LAN (using SSH)?

---

### Post by Greg_Bedsaul on 2013-08-12
To answer your question, yes I did. However, for future reference I figured out what went wrong with it.

I had them all setup to used the bridged adapter setting, which is apparently not cool in VirtualBox. What that means is that in either VirtualBox or Windows I created three more virtual adapters so that windows saw them as three different computers instead of three trying to bridge themselves on one virtual adapter. Also, for good measure I separated out all three computers in the VirtualBox settings to have one using adapter on, the other to adapter two, and the other to adapter three.

I doubt that was really necessary as long as each one had a separate virtual adapter to work with.



Thank you for your help.

---

