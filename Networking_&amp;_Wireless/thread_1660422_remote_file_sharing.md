---
title: "remote file sharing"
date: 2011-01-05
forum: Networking &amp; Wireless
---

### Post by jymboche on 2011-01-05
I apologize if this isnt in the right forum category. Anyway, I am starting up a business and need to have a server that me and a couple other people can connect to and share files. Im not sure what the best protocol is to do this. Right now, I have samba installed and I create an ssh tunnel to access the samba share remotely. This works fine for me, but its not a very user friendly method for other people. What are my options, or best option, for sharing files remotely and securely. If it matters, all three of us use OSX, but it would be nice if the chosen protocol could be easily accessed on windows as well.

---

### Post by Ceiber Boy on 2011-01-05
> **jymboche said:**
> I apologize if this isnt in the right forum category. Anyway, I am starting up a business and need to have a server that me and a couple other people can connect to and share files. Im not sure what the best protocol is to do this. Right now, I have samba installed and I create an ssh tunnel to access the samba share remotely. This works fine for me, but its not a very user friendly method for other people. What are my options, or best option, for sharing files remotely and securely. If it matters, all three of us use OSX, but it would be nice if the chosen protocol could be easily accessed on windows as well.

if this is on a LAN just use samba as that can be accessed by OSX Windows and Linux, DO Not use this for WAN access. if you want to use it on WAN and you have untrusted work mates use FTP if you trust your work mated use SSH. FTP you can block out the root file system and confine people to a specific folder where SSH allows you to brows the entire file system, measures can be implemented to prevent this but can become extremity complicated very quickly!

---

### Post by jymboche on 2011-01-05
hmm, I guess to clarify my situation and question i should be more specific. We have a server at an office but we often work in different locations. So, 90% of the time file sharing wouldnt be local. I for sure "trust" the other two people that would be accessing it. BUT, i set up chrooted ssh accounts using jailkit. Then just create an ssh tunnel and connect to the samba share through finder.

What are my other options for file sharing, as in mounting a network drive in osx/windows?
I dont have much networking experience and just kinda got thrown into this. What about AFP(netatalk) or creating a VPN(which i dont know much about either)? What would a professional do?:p

---

