---
title: "Supported USB IR receivers"
date: 2009-08-08
forum: Mythbuntu
---

### Post by WrathofthePenguin on 2009-08-08
I have an existing Tivo remote I want to use, but I'll need to buy an IR receiver. Are there any supported USB IR receivers?

---

### Post by WrathofthePenguin on 2009-08-09
Ok, no answers on supported USB IR receivers, how about people who have one working?

---

### Post by WrathofthePenguin on 2009-08-09
Well, I'm not encouraged. I found [this]("http://ubuntuforums.org/showthread.php?t=1219120"), which states that 9.04 has problems with usb IR receivers. I'd love to hear that this is not true - has anybody got one working in 9.04?

---

### Post by NTolerance on 2009-08-09
My recommendation is to get a [Microsoft MCE Remote/USB receiver combo](http://www.amazon.com/Microsoft-Control-Receiver-Windows-A9O-00007/dp/B00066FIO6) due to the fact that it's well supported and probably the most "standard" media center remote out there.  

Installation in Ubuntu is dead easy, just apt-get install lirc and pick the MCE remote from the list provided by the debconf installation prompt.

I understand that your intent is to use your existing remote, and while that may be possible, you may be in for a struggle to make a somewhat oddball combination work.  Hopefully someone here knows more about how that Tivo remote works with Ubuntu.

---

### Post by Lorenzo1985 on 2009-08-10
Unfortunately I agree with NTollerence, not what you wanted to hear but hey.. 

I've had custom lirc setups and there ok once you've got them working but any upgrades or changing computers could result in having to redo config. 

you can't really beat the Plug-n-play of the mce remotes

Plus the MCE remotes are really that exspensive, you can get then for about £10 here in the uk new on Ebay

---

### Post by WrathofthePenguin on 2009-08-10
> **Lorenzo1985 said:**
> Unfortunately I agree with NTollerence, not what you wanted to hear but hey.. 

I've had custom lirc setups and there ok once you've got them working but any upgrades or changing computers could result in having to redo config. 

you can't really beat the Plug-n-play of the mce remotes

Plus the MCE remotes are really that exspensive, you can get then for about £10 here in the uk new on Ebay

I decided last night to just go ahead and go with the Microsoft MCEs and ordered a couple. I definitely appreciate the input - thanks! If it were something like my laptop then I'd be willing to fight with it, but since my wife has to like the operation of the setup I'd better make sure I have the best chance of success as possible.

---

