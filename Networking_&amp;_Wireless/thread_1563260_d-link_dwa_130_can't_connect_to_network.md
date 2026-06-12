---
title: "d-link dwa 130 can't connect to network"
date: 2010-08-28
forum: Networking &amp; Wireless
---

### Post by faintscrawl on 2010-08-28
Hi,

I just bought this usb wireless adapter. (I also have a mac using wireless here and it works fine.) I installed ndiswrapper and ndisgtk and then used it to open the .inf file on the driver cd that came in the box. It must  have worked reasonably well because if I click on network manager, I can see a number of networks, including my own. However, when I enter the security key for my network the icon spins for a while and then it asks for the key again. I've tried repeatedly and it never connects. I am definitely entering the key properly because I re-entered it on my mac and it worked.

I have attached a document with most of the information requested in the sticky.

Any help would be appreciated. Please note, it's probably obvious but my proficiency with Ubuntu is limited.

Thanks.

---

### Post by bkratz on 2010-08-28
> **faintscrawl said:**
> Hi,

I just bought this usb wireless adapter. (I also have a mac using wireless here and it works fine.) I installed ndiswrapper and ndisgtk and then used it to open the .inf file on the driver cd that came in the box. It must  have worked reasonably well because if I click on network manager, I can see a number of networks, including my own. However, when I enter the security key for my network the icon spins for a while and then it asks for the key again. I've tried repeatedly and it never connects. I am definitely entering the key properly because I re-entered it on my mac and it worked.

I have attached a document with most of the information requested in the sticky.

Any help would be appreciated. Please note, it's probably obvious but my proficiency with Ubuntu is limited.

Thanks.

I am on my Windows system so I could not look at the .odt document without installing open office, but i can guess what it says.  I use the A1 version of the DWA-130 with good results. I did find that I had to set my router to WPA2 with AES rather than WPA/WPA2 with TKIP/AES combination, try using one or the other, but not both.

---

### Post by faintscrawl on 2010-08-28
> **bkratz said:**
> I am on my Windows system so I could not look at the .odt document without installing open office, but i can guess what it says.  I use the A1 version of the DWA-130 with good results. I did find that I had to set my router to WPA2 with AES rather than WPA/WPA2 with TKIP/AES combination, try using one or the other, but not both.

Thanks.

I opened up the preferences for my router. It must be oldish. There is no WPA2 or AES, only WPA. I tried it and entered a passphrase and I'm afraid it didn't work (although it did on my Mac).

However, since you put me on that trail, I'll tried using no security and, indeed, I could connect--Yay!--but now I need to find a security method that will work on the Ubuntu machine because I don't want to leave my network open for all the neighbours to use.

My router is d-link Airplus G. DI524. Any advice on how to get wep or wpa working?

Thanks!

---

### Post by bkratz on 2010-08-28
> **faintscrawl said:**
> Thanks.

I opened up the preferences for my router. It must be oldish. There is no WPA2 or AES, only WPA. I tried it and entered a passphrase and I'm afraid it didn't work (although it did on my Mac).

However, since you put me on that trail, I'll tried using no security and, indeed, I could connect--Yay!--but now I need to find a security method that will work on the Ubuntu machine because I don't want to leave my network open for all the neighbours to use.

My router is d-link Airplus G. DI524. Any advice on how to get wep or wpa working?


Thanks!



Since you didn't specify which DI524 version you have I download the non-rev version and on page 25 it discussed allowing computer by MAC address filtering only.  You might look into that since it would only allow known users to utilize the network, but you would also have to do it on all machines. I never did get wep to work on mine, but maybe I gave up to soon.

This was the address in case you don't have it

[http://www.dlink.com/products/?tab=3&pid=DI-524&rev=DI-524](http://www.dlink.com/products/?tab=3&pid=DI-524&rev=DI-524)

---

### Post by faintscrawl on 2010-08-29
> **bkratz said:**
> Since you didn't specify which DI524 version you have I download the non-rev version and on page 25 it discussed allowing computer by MAC address filtering only.  You might look into that since it would only allow known users to utilize the network, but you would also have to do it on all machines. I never did get wep to work on mine, but maybe I gave up to soon.

This was the address in case you don't have it

[http://www.dlink.com/products/?tab=3&pid=DI-524&rev=DI-524](http://www.dlink.com/products/?tab=3&pid=DI-524&rev=DI-524)

Thanks for that. I'm just wondering if there is really no other way to get Ubuntu and my router to "authenticate" using the passphrase. Is it that Ubuntu only likes to work wpa2?

As I await more insight, I'll explore this MAC address route--starting with figuring out what a MAC address is :)

Thanks,

---

### Post by faintscrawl on 2010-08-29
Just to say thanks to Bkratz. The MAC address method seems to work just fine. Thanks for suggesting it. I never would have stumbled onto that myself.

Cheers.

---

### Post by bkratz on 2010-08-29
> **faintscrawl said:**
> Just to say thanks to Bkratz. The MAC address method seems to work just fine. Thanks for suggesting it. I never would have stumbled onto that myself.

Cheers.


Congratulations!


Sure am glad you found something that worked for you, by the way I use a passphrase for my security and it works fine on mine. Of course I am on WPA2--only and AES only.  Your mileage may vary. Anyway, you might go to the thread tools and mark it as [solved] just in case it helps someone else.

---

