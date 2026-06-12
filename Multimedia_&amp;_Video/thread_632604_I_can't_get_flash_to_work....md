---
title: "I can't get flash to work..."
date: 2007-12-05
forum: Multimedia &amp; Video
---

### Post by Luigi239 on 2007-12-05
Hey everybody, I for the life of me can't get flash to work. I installed the flash plugin from Firefox, as well as the community restricted extras, and can't get it to work. Firefox always says that it cannot find the right plugin, and when I try and install, the installer says it's already installed. I know this is a popular topic, but I have searched through some threads, and nothing so far has helped.

This has happened on both 64bit and 32bit versions of Ubuntu. (I switched over to 32bit for compatibility.)

Thanks all.

---

### Post by kamilvb on 2007-12-05
I've got exactly the same problem and tried everything I could find on the net.
Hope someone can shed some light here... Thanks in advance!

---

### Post by jimmj43 on 2007-12-05
I'm using Feisty and this worked for me:

Applications > 
Add/Remove > 
Other > at top right:  *open all source applications*  select --> *all available applications*  > Macromedia flash plugin

Go from there.
 
For what it's worth, the day after I did that I encountered a NEW Flash vid that refused to play: Flash 9. Somehow I muddled thru D/Ling it & getting it to work.  My next mission [should I choose to accept it] is to try to get WMV 9 vids to play...

---

### Post by Luigi239 on 2007-12-05
Hmm, with a little more searching I found the answer for Gutsy. (Thank you misfitpierce for these steps, from [http://ubuntuforums.org/showthread.php?t=632107](http://ubuntuforums.org/showthread.php?t=632107)) One of his steps I had to change however to make it work for me.

Go to [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash) and download the tar.gz.

Unpack it to the desktop, and find the libflash.so file.

Then, run the command:
sudo nautilus /usr/lib/firefox/plugins/

And drag the libflash.so file into the folder that opens. Just restart firefox, and you are done.

Hope this helps.

---

### Post by kamilvb on 2007-12-05
Yes! :D
Finally, thank you!

---

### Post by Don1500 on 2007-12-05
> **Luigi239 said:**
> Hmm, with a little more searching I found the answer for Gutsy. 

Thanks that should help me also.

---

### Post by Yellow Pasque on 2007-12-06
Note that it takes a couple extra steps for 64-bit (see the multitude of threads on this subject in the x86-64 forum)

---

### Post by Van_Man on 2007-12-23
> **Luigi239 said:**
> Hmm, with a little more searching I found the answer for Gutsy. (Thank you misfitpierce for these steps, from [http://ubuntuforums.org/showthread.php?t=632107](http://ubuntuforums.org/showthread.php?t=632107)) One of his steps I had to change however to make it work for me.

Go to [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash) and download the tar.gz.

Unpack it to the desktop, and find the libflash.so file.

Then, run the command:
sudo nautilus /usr/lib/firefox/plugins/

And drag the libflash.so file into the folder that opens. Just restart firefox, and you are done.

Hope this helps.

Thnx you!

---

### Post by hirou on 2008-01-12
Thankyou very much, I got stuck trying to get flash to work, but now it's fine :) :lolflag:

---

### Post by mlyons16 on 2008-03-11
> **Luigi239 said:**
> Hmm, with a little more searching I found the answer for Gutsy. (Thank you misfitpierce for these steps, from [http://ubuntuforums.org/showthread.php?t=632107](http://ubuntuforums.org/showthread.php?t=632107)) One of his steps I had to change however to make it work for me.

Go to [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash) and download the tar.gz.

Unpack it to the desktop, and find the libflash.so file.

Then, run the command:
sudo nautilus /usr/lib/firefox/plugins/

And drag the libflash.so file into the folder that opens. Just restart firefox, and you are done.

Hope this helps.

This really worked! I think its the best flash installation method for Firefox yet.

---

### Post by 6205 on 2008-03-11
> **mlyons16 said:**
> This really worked! I think its the best flash installation method for Firefox yet.

Or you can install *.deb file with latest Flash plugin from this link [http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb](http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb)

---

