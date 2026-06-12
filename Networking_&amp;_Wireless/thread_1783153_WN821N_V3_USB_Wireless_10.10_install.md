---
title: "WN821N V3 USB Wireless 10.10 install"
date: 2011-06-15
forum: Networking &amp; Wireless
---

### Post by warmstrong99 on 2011-06-15
I have an aging Toshiba Satellite Pro A60 EN on which I installed XUbuntu 10.10  To successfuly make my TP-Link WN821V3 USB Wireless adaptor work with Xubuntu 10.10, I had to do the following:-

This is the result of several days Googling and Forum searching and reading and some very severe head scratching.

My apologies if this has been posted elsewhere - but I couldn't find it.

Note that this is for the WN821N V3.  There are other hardware versions out there that probably have other (and better) solutions.

My thanks go to Gadaph at [http://myubuntunotes.wordpress.com/](http://myubuntunotes.wordpress.com/) whose site pointed me in the right direction.

Download the latest (as at 15 June 2011) compat drivers at:- 

[http://wireless.kernel.org/en/users/Download/stable/#compat](http://wireless.kernel.org/en/users/Download/stable/#compat) wireless_3.0_stable_releases
 
untarr it and save in Downloads
 
Then open up a terminal and enter:
 
  cd Downloads
 
  cd compat-wireless-*
 
  ./scripts/driver-select ar9170   (Note: I don't know if 'ar9170' was the correct driver to select here but it seemed to work for me.)
 
  make

NOTE:At this point I had to go and get a cup of tea as it took forever (at least 1 hour) to come back to the $ promp.

 
  sudo make install

NOTE: Another lengthy wait.
 
  sudo make wlunload
 

 
The firmware, htc_7010.fw  and htc_9271.fw, I found at: 
 
[http://wireless.kernel.org/download/htc_fw/](http://wireless.kernel.org/download/htc_fw/)

 
Download these and move them into the ubuntu /lib/firmware directory:-
 
  sudo mv ~/Downloads/htc_7010.fw /lib/firmware
 
  sudo mv ~/Downloads/htc_9271.fw /lib/firmware
 

Reboot and you should have wireless.

The only issue at the moment is that I can only connect at 54Mbs(g) and NOT 300Mbs(n) as I want to, but that's the challenge for another day.


Please try not to ask me any questions on the above. 
It worked for me but I am a total noob when it comes to Unix based systems so it'll be the blind leading the blind.

Google is your friend.
 
Good Luck

---

