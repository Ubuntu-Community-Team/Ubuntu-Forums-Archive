---
title: "ATI 4650 fglrx"
date: 2009-02-27
forum: Multimedia Software
---

### Post by doktormiod on 2009-02-27
Hi, I have bought a new card - ATI 4650 as it is written in the title but after swapping it with the old one Xs won't start.
The system (Kubuntu 9.04) is loading as it usually does but at the moment when normally xserver starts the screen just goes black. 
I tried dpkg-reconfigure xserver-xorg but it didn't help.

Second issue - i've been using open drivers for my X1800GTO for quite a long time so could anyone tell me if there's any catalyst(fglrx) version that will run on kubuntu 9.04 with ati4650?

Thanks for Your help
Doktormiod.

---

### Post by markbuntu on 2009-02-27
What you need to do is boot into recovery mode and use the fix x option. That should get x up on the vesa driver. Then you need to remove and reinstall the radeon driver.

In answer to your second question, not yet but soon.

---

### Post by doktormiod on 2009-03-03
Thanks for the reply but unfortunately it didn't help. LiveCd acts the same way :/...

---

### Post by budde on 2009-04-11
Bump.

Trying to install ubuntu on my Asus N51 with ATI 4650 with no luck. X won't boot from the live cd, claiming "no screen".

Any suggestions?

---

### Post by markbuntu on 2009-04-11
For the live cd, at the first menu option click f4 and choose safe graphics mode.

---

### Post by budde on 2009-04-11
Tried the F4 thing, didn't help. Still no X at all. 

Can't really copy+paste the log since it's from the live cd. 

Don't know if it's a problem with the ATI 4650, or the screen, but it says "No screens found".

Edit: 
"$ glxinfo | grep vendor" => Error: unable to open display

"$ lspci -nn | grep VGA" => Can find the graphics card "ATI Technologies Inc Device" etc..

---

### Post by markbuntu on 2009-04-11
Did you remove the old driver before you swapped the cards?

---

### Post by Sephoroth on 2009-04-12
> **markbuntu said:**
> Did you remove the old driver before you swapped the cards?

I believe Budde's ATI 4650 came on his laptop (Asus N51) and is trying to install Ubuntu meaning old drivers wouldn't be present.  Note that he isn't the OP.

---

### Post by suavecu on 2009-04-12
I'm running into a similar problem with an older ATI card, what you might want to do is install ubuntu with the text based installer off the alternate cd that way you can at least boot into the command line, and get help from there. Live CD doesn't work with me either.

---

### Post by suavecu on 2009-04-12
Just got the answer to my problem. Do you by chance have a DVI output so that you can use dual monitors? If so, you might want to try the other VGA output as the open source ATI driver does not support dual monitors, resulting in it not being able to pick up the monitor from one of the jacks. If that is not it, I am out of luck. Still a novice myself.

---

### Post by budde on 2009-04-15
Sephoroth: You are very right, that was exactly what I was trying to do.

Apparently Ubuntu 8.10 doesn't work too well with Radeon 4650. However I did manage to get it to work with 9.04 alpha 5, so I'll just go from there and upgrade to stable later. Not too much of a wait.

Thanks for the help though guys!

---

