---
title: "can not get dvd's to play"
date: 2010-01-10
forum: Multimedia Software
---

### Post by mdquince on 2010-01-10
can someone please help me.  I can not get dvd's to play on either movie player that comes with ubuntu and vlc.  can you please explain in detail because I'm new to linux

---

### Post by diesch on 2010-01-10
Please see [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by mdquince on 2010-01-10
libdvdcss2 is already installed and still no dvd will play.

---

### Post by diesch on 2010-01-10
What happens if you try to play a DVD? Do you get any error messages?

---

### Post by Gillen on 2010-01-10
Hi mdquince, here is what I normally do to get DVD's to play.

Ubuntu 9.10

Using Synaptic Install the following packages

(System/ Administration/ Synaptic Package Manager)

gstreamer0.10-ffmpeg
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-ugly

---

libdvdcss ((To play incrypted DVD's) Download and install from Medibuntu [http://packages.medibuntu.org/karmic/index.html](http://packages.medibuntu.org/karmic/index.html) )

Hope this helps.

---

### Post by ubudog on 2010-01-10
Open a terminal and type ```
sudo apt-get install ubuntu-restricted-extras
``` Hope that helps.

---

### Post by shantiq on 2010-01-10
[COLOR=Blue]**another route you can take to get all the extras[  is here]("http://www.stchman.com/dvd_rip.html")**[/COLOR]    ;);)

---

### Post by Tourdog on 2010-01-10
Ubudog,
copied your "Sudo ...........................-extras" and after 29 mB plus 164 mB I have a locked screen (package configuration)  showing the Sun Micro Systems  "Sun-Java6-Jre" license agreement.  I would like to agree and move on with the next steps but what's up with this????
Help!?   :(

---

### Post by HappyFeet on 2010-01-10
> **Tourdog said:**
> Ubudog,
copied your "Sudo ...........................-extras" and after 29 mB plus 164 mB I have a locked screen (package configuration)  showing the Sun Micro Systems  "Sun-Java6-Jre" license agreement.  I would like to agree and move on with the next steps but what's up with this????
Help!?   :(

There's a box you check off and then hit next.

---

### Post by ubudog on 2010-01-10
Just check the "I Agree" box and hit next.

---

### Post by 73ckn797 on 2010-01-10
Restricted extras, as previously mentioned, is good

Look here also: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by Tourdog on 2010-01-10
HappyFeet & Uberdog,

That whole screen is locked .......................  no way to get to the "I agree" ck box!

I moved on to HappyFeet's "Sudo" and that ends up with at least No Public key and resultingly........... unable to unlock...........

I've just done a shutdown and backup on 9.10 Karmic and see if redoing HappyFeet's sudos will work now. 

thankyou both for coming back here......

---

### Post by ubudog on 2010-01-11
About the locked screen:  Did you try using the arrow keys to get to the very bottom?

---

### Post by HappyFeet on 2010-01-11
> **ubudog said:**
> About the locked screen:  Did you try using the arrow keys to get to the very bottom?

I read in another thread that the problem was solved by using the tab key. Strange I've never needed to use the tab key myself.

---

