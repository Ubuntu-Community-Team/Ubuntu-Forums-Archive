---
title: "Network newbie mess"
date: 2010-11-19
forum: Networking &amp; Wireless
---

### Post by acrichardt on 2010-11-19
Ok guys.  I'm cutting my teeth on networking at my first IT type job (just a lab tech).  I haven't gotten into it yet at school, and they don't provide internet in the boonies where I live so bear with me.

My setup is unique.  I work in a testing center that has four labs.  2 are on the college network, and the other 2 labs are on a seperate network.  I rebuilt my office computer using discarded/off inventory parts from around the lab.  I have two NIC's and two cables, thus two seperate connections.  Both NIC's show up and both have different IP's when I ifconfig.  When I use smbtree it shows one network, the other, or none seemingly randomly.  I am also having trouble setting up ssh.  I have puTTY on a thumb drive I carry with me to all Windows test stations, and I've tried restarting ssh, and using sshd debug, but I'm still a neophyte when it comes to all of this.  I was hoping someone could point me in the right direction.  Can I even use ssh and 2 networks on one computer (like a hub between the two)?  I'm using Lubuntu 10.04.

I know this sounds kinda senseless, but I'm doing alot of backup/maintenance and trying to put in work up front, to make it easier later.  I have only one network drive to my complete disposal and am trying to store/access everything without running laps through the place.  Working with two networks on one box seems like trying to tame a wild horse at this point, and using puTTY to ssh into my station is fruitless at this point.  My end goal is to ssh into my office, access my file system via bash, and thus my mounted network drive.

Thanks in advance!

---

### Post by spiky001 on 2010-11-19
I have a setup something like that I have wired and wireless and can ssh into 2 different comps at once although i use ssh and not putty i have used putty awhile ago

---

### Post by pricetech on 2010-11-19
You'll have to remove the default gateway on one of your networks.  You can add a route if you need access to other subnets via that NIC.

If putty isn't working out, try NX from nomachine dot com.

---

### Post by acrichardt on 2010-11-22
Thank you.  I will have to research removing the default gateway.  I'm still very new to all of this.   Oh, and as far as NX I checked it out, but it is all for GNU/Linux?  I'm trying to use puTTY on the Windows test stations to ssh into my office pc which is Lubuntu.  Also, my office PC is not joined to any domain.  Could I join it to both network domains?  Will that make a difference?

---

