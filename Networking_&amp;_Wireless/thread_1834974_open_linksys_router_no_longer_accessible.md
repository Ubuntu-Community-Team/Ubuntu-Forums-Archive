---
title: "open linksys router no longer accessible"
date: 2011-08-28
forum: Networking &amp; Wireless
---

### Post by harryharryharry on 2011-08-28
Hi all,

This is my first post on these forums (normally I try to search for an answer first, but this problem is kind of particular), so if something is inappropriate, please notify me and I will try to adjust. :)

I have a linksys router in my basement and physical access is pretty much blocked by a stuck trap-door. I could try to shut off the main power switch, but I like to see that as a last resort...

The problem I have is that I have an open (= no encryption) wifi connection between my pc and linksys router, yet I cannot connect to it. Until a couple of days ago I could connect to it with my android handheld device, my linux laptop, and my windows desktop. All these devices are now unable to connect. I attached the wicd log from my linux laptop. 

Could you guys help me gain access to my router again ?
If you need more information about my setup please let me know.

-Harry

---

### Post by kerry_s on 2011-08-28
go to 192.168.1.1 in to your browser.
could be just your router has finally died, how old is it?

---

### Post by harryharryharry on 2011-08-28
its a WAG54G2 i dont know how old, definitely not new :)
i cant reach 192.168.1.1 because no connection is established. For some reason the laptop takes a very long time trying to connect (tried with dhcp on and off) but says it cant `associate to ap` (as seen in the wicd logfile).

Any ideas ?

---

### Post by bkratz on 2011-08-28
> **harryharryharry said:**
> its a WAG54G2 i dont know how old, definately not new :)
i cant reach 192.168.1.1 because no connection is established. For some reason the laptop takes a very long time trying to connect (tried with dhcp on and off) but says it cant `associate to ap` (as seen in the wicd logfile).

Any ideas ?



If this is a wireless connection, do you see your AP in

```
sudo iwlist scan
```

in the terminal?

---

### Post by harryharryharry on 2011-08-28
yes; see attached output file (cell 09)

(I know 'power' is quite low, but in the right circumstances i can get it to ~-75)

---

### Post by bkratz on 2011-08-28
> **harryharryharry said:**
> yes; see attached output file (cell 09)

(I know 'power' is quite low, but in the right circumstances i can get it to ~-75)



well there are three other AP's on channel six, at least 1 (#2 I believe) has a stronger signal than yours). Normally I would suggest moving to an used channel, but I realize that is not practical in your case. I really don't have a good suggestion, but will look more.

---

### Post by harryharryharry on 2011-08-28
Its fairly ironic i changed the channel from 11 to 6 about 2 weeks ago to get better reception. This change worked initially...

btw, the problems started when the adhoc `hpsetup` showed up on channel 6 recently (about a week ago). I dont know if its the cause though...

---

### Post by harryharryharry on 2011-08-28
One more addition:
I dont think interference is the main issue here, because none of the devices (android handheld, linux laptop, windows desktop) can connect to the linksys, no matter how i position them...

a weird side note:
I have another linksys router, with ddwrt installed (I use it in wireless client mode to connect my desktop pc to the linksys in question) and it wont find the wireless network the ´troubled´ linksys sends out, while it did until recently.

---

### Post by kerry_s on 2011-08-28
i'm thinking you need to get past that stuck trap door & see what state the router is in. i hope it's not some where hot or dusty, they get pretty hot all on there own.

---

### Post by harryharryharry on 2011-08-29
As per my first post, I'd like to see that as a last resort. The weird thing is I can still see the open wifi with tools such as aircrack and kismet, so I'm assuming the router is still running an unencrypted wifi signal, only not accepting my devices. Isn't there a way to retrieve the rejection message the router is giving me ?

---

