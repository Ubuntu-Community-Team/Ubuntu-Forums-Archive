---
title: "Can i delay resume when opening laptop lid? (Atheros problem )"
date: 2011-10-17
forum: Networking &amp; Wireless
---

### Post by dooper on 2011-10-17
I have done an install of 11.10 and my Atheros problems are back !

The problem is sporadic in that sometimes when i open my lappy lid and the lappy resumes,in network manager the network is shown but clicking on it doesnt get a connection. It just keeps trying and then says password fail. It doesnt do it all the time,,sometimes i open the lid and it works fine.

I am just wondering if i can introduce some kind of delay when i open the lid as maybe the atheros card doesnt have time to fully initialise and be ready to connect?

All other ideas welcome !

lspci

Ethernet controller: Atheros Communications Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) (rev 01)


Lappy is a Tosh A210-12U

EDIT OK i did some reading and it has been suggested that i edit the file /usr/lib/pm-utils/sleep.d/55NetworkManager and comment out the dbus suspend/resume routines. I tired this but even though i was logged on as sudo,it wouldnt let me save the file.


EDIT 25/10/11

Still havent made any progress on this one. Tried to use the chown command on the above file but not sure if im using it correctly as no luck.

Anyone have any thoughts please??

---

### Post by dooper on 2011-10-25
Still no progress..any thoughts please?:p

---

### Post by dooper on 2011-10-27
Latest update to this....

As i cannot seem to get the internal Atheros card in the lappy to work reliably I thought id try some other options. In my bag of bits i had a wireless pc slot card. Tried it but it only went half way into the slot of the tosh A210-12U lappy to obviously the slot isnt backwards compatible. I assume its a PCI bus slot?

Next i fished out an old Sweex USB wireless modem...bingo..works like a dream ,initially anyway..it might be unreliable next time i try !

So this will have to be the current solution until either Ubuntu sorts a fix for Atheros PCI cards for good or the gurus on this forum get round to having a look at it.

So anyone with similar issues awaiting a fix..this might be a good option in the interim..

---

