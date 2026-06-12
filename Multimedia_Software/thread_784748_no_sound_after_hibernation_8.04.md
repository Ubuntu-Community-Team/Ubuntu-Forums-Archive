---
title: "no sound after hibernation 8.04"
date: 2008-05-06
forum: Multimedia Software
---

### Post by n8makar on 2008-05-06
I have been using hardy for a few days now and everytime I return from putting my laptop in hibernation I get no sound. If I reboot I have sound no problem. My card is recognized and I'm using ALSA. 

I've tried uninstalling and reinstalling the drivers. I've tried muting, then going into hibernation, then on return unmuting, but still no sound. 

I've heard it's a kernel problem, but that was a while back and i figured it was fixed. Is this just me or are others experiencing this too?

---

### Post by n8makar on 2008-05-06
just posted on bug as well [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/25896]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/25896")

also posted output of lspci, lspci -vv, lspci -vvn and dmidecode. will attach on here too.

---

### Post by n8makar on 2008-05-06
hmm must just be me...

---

### Post by chrisby on 2008-05-07
Its not just you.  I have the same problem on my acer extensa 5620Z.

---

### Post by n8makar on 2008-05-07
you would think someone would have put some time into fixing this

---

### Post by pedro_orange on 2008-05-07
From what I heard on a Podcast a while ago:

Laptops do hibernation differently on different laptops. And just be thankful that hibernation even works on your linux laptop!
I think manufacturers actually tweak Windows to be able to cope with their way of hibernating. 
So if things don't work after your hibernation; I don't think it will be fixed. 
I could; and usually am wrong. 
Just my 2 cents.

---

### Post by n8makar on 2008-05-07
yea i suppose so. maybe it is a toshiba satellite thing since suspend or hibernate didnt work for me in gutsy

---

### Post by studo77 on 2008-05-07
it is not only on laptops. I think this issue is for a lot of people. I have it on my stationary, Audigy 2 LE (ca0106) card.
But hibernation does not kill my network, it did in 7.10.

So, can agree on that you should just feel lucky that most of it works

---

### Post by n8makar on 2008-05-07
yea i think im gonna agree too. I'm going to feel a lot better when I get home for this semester and can put Hardy on my more powerful desktop. One would think there wouldn't be too many problems there. Then again...

---

### Post by chrisby on 2008-05-14
I fixed my no sound after hibernation issue.  I have a realtek alc268 sound card, if you have the same a modification of my code could probably help.  See [http://ubuntuforums.org/showthread.php?t=791639]("http://ubuntuforums.org/showthread.php?t=791639")

---

