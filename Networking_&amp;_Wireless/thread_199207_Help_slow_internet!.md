---
title: "Help slow internet!"
date: 2006-06-18
forum: Networking &amp; Wireless
---

### Post by LopsidedElf on 2006-06-18
I've been using ubuntu for about a week now and all of a sudden my internet is unbearably slow. I'm plugged directly into a router and i have a wireless card plugged in but ive never done anything to install the drivers or anything. I've tried using the internet on my mac and its fine.

Thanks for any help. :)

---

### Post by LopsidedElf on 2006-06-18
When i type sudo pppoeconf it recognizes my eth0 connection but when i click continue it fails and says that there may be another app using the connection but nothings open.(sorry i dont remeber the exact error my internet isnt working on my linux comp.)

---

### Post by LopsidedElf on 2006-06-18
It fails when looking for the service concentrator or somthing similar and it fails saying it couldn't access the service concentrator. Any help would  be much appreciated, Thanks

---

### Post by ianmac on 2006-06-19
What type of router are you using?  Presumably a standard 802.11 router?  In that case, you should not have to run pppoeconf...  all you should have to do really, is plug your ethernet card into the router...  are you using 802.11 wifi?  I was a bit confused...  I assumed that you have a wireless card, but are not using it, and are using an ethernet cable to connect to the router.

What should be happening is that your router acts as a pppoe client and then provides straight dhcp access to the rest of your network...

If you provide further information I can try and help...

Ian

---

### Post by LopsidedElf on 2006-06-21
Thanks for your help I'm using an ethernet card to connect to the internet. I recently reinstalled Linux without my wireless card plugged in and now i dont have any internet at all inside linux, i can open the add-remove programs menu but i tried to install more repositories (or whatever its called) and that failed.

Any help would be much appreciated, with the internet not working I'm not using  Ubuntu at all.

What other information can I provide?

Thanks.

---

