---
title: "2 dual-boot machines but only 3 wireless connections"
date: 2009-08-16
forum: Networking &amp; Wireless
---

### Post by fredz on 2009-08-16
Hello, all. I'm a newbie with a puzzle. My Toshiba laptop with Vista and Ubuntu 8.10 picks up my home wireless network just fine with either OS. 

  The problem is with my Samsung NC10 netbook. It has been picking up the wireless fine with Windows XP, but yesterday when I loaded Ubuntu 8.10 in dual-boot mode Ubuntu network icon found no wireless connection. (XP still gets wireless fine.) Live mode doesn't find wireless either.  With an ethernet cable, Ubuntu does find the network.

  Under Hardware Drivers, there is a green button in front of: "Support for Atheros 802.11 wireless LAN cards," and  another green button in front of: "This driver is activated and currently in use." (I notice that on my A-OK Toshiba, this same box is blank, except for the heading "No proprietary drivers are in use on this system," a heading also appearing in the Samsung box.)

  Thanks for any suggestions.

Fred

---

### Post by bluelamp999 on 2009-08-16
A quick look around found this...

[http://nc10linux.wordpress.com/2008/12/10/install-wireless-driver/](http://nc10linux.wordpress.com/2008/12/10/install-wireless-driver/)

Might help...

---

### Post by fredz on 2009-08-16
bluelamp,
  Thanks for the citation. It does indeed look to me like I need a better driver for the NC10 in order for it to make the wireless connection. I'm a little hesitant just yet to take the plunge as suggested on that page, though, since the instructions are a bit cryptic for someone of my level of expertise. 

  Here is my current state of deductions: The Atheros wireless card on the NC10 needs a more recent driver than the one out of the box in order to support Ubuntu 8.10. I could download a newer  driver but in order for it to work I would have to disable the current driver with blacklist commands. Newbie questions: Do I seem right so far? Can I find the driver in the Ubuntu archives somewhere or should I go to Samsung or Atheros? If I download it through XP onto the NC10 will it then be available to Ubuntu?

  Thanks again for your help.

---

### Post by bluelamp999 on 2009-08-16
Hi Fredz,

You might have better luck with your wireless with Ubuntu 9.04 ? 

You could either do a fresh install or upgrade from 8.10.

Here's a good blog for Ubuntu/NC10 install stuff... 

[http://nc10ubuntu.wordpress.com/](http://nc10ubuntu.wordpress.com/)

There's also an excellent Sammy community site here...

[http://sammynetbook.com](http://sammynetbook.com)

From a quick scan of the first site it looks like 9.04 might have better wireless support.


If the other stuff (blacklisting etc.) looks a bit daunting, my advice is just dive in and give it a lash. 

If everything goes pear-shaped remember Google is your friend and you'll also learn a bit about Ubuntu...

Good luck

---

