---
title: "Monitor and Display  couldnt be loaded"
date: 2007-03-10
forum: Multimedia &amp; Video
---

### Post by Enroth on 2007-03-10
hi all,
I recently got a new flat panel wide screen monitor with DVI input, having connected it up, and turning on the computer i got the out of range message, reading other people's posts about this i went to try and fix it up in System Settings/ Monitor and Display and then I got the following message


                                  --------------------------------------------------------------


The module & Display could not be loaded.
The diagnostics is:

Possible reasons:
   * An error occurred during your last KDE upgrade leaving an orphaned control module
   * You have old third party modules lying around.

Check these point carefully and try to remove the module mentioned in the error message. If this fails, consider contacting your distributor or package.

                                  --------------------------------------------------------------

I believe this would have occurred during the setup for my graphics card, a Radon 850x pro, I followed these instructions to get it working [http://ubuntuforums.org/showthread.php?t=321766]("http://ubuntuforums.org/showthread.php?t=321766") although i did have a failed attempt using the 'Install from ati.com (latest version of drivers)" from here [https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-123c48c83c49553bdd4260ff972ffacdff04580e]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-123c48c83c49553bdd4260ff972ffacdff04580e") 

Apart from the computer not liking my DVI connection this hasn't seemed a problem.

I hope I have provided enough information.

 Thankyou for anyhelp

---

### Post by teaker1s on 2007-03-10
so you tried booting recovery and
```
sudo dpkg-reconfigure xserver-xorg
```  ?

---

