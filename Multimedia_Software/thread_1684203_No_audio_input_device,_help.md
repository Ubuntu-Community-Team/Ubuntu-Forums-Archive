---
title: "No audio input device, help"
date: 2011-02-08
forum: Multimedia Software
---

### Post by mubtasim123 on 2011-02-08
No audio input device can be found in sound preference>input
but in sound preference>hardware>it shows the input webcam recorder device.[IMG]http://3.bp.blogspot.com/_dPYxq1NjsFU/TVHdV5UgKGI/AAAAAAAAAHY/KNS3bn-e-FI/s1600/Screenshot-1.png[/IMG]
[IMG]http://1.bp.blogspot.com/_dPYxq1NjsFU/TVHdcOwpj4I/AAAAAAAAAHg/42dNv32mVSA/s1600/Screenshot-2.png[/IMG]
When I use ```
alsamixer
``` onto terminal it shows this
[IMG]http://4.bp.blogspot.com/_dPYxq1NjsFU/TVHeOJtah0I/AAAAAAAAAHk/1jHphfGCOrc/s1600/Screenshot-3.png[/IMG]:(
and also i checked cable device and everything. And it was working till I last hour. I rebooted computer then there's some problem, I haven't change anything before or after rebooting. 
:?:-(
Can anyone help me with this situation?

---

### Post by tqft on 2011-02-09
See the alsamixer screen you posted.

Underneath Front Mic it has "MM".  That means the  mic is muted.

use the arrow key to move across the items until the Front Mic is selected and press "M".

use the tab key or F4 to navigate to the Capture bit in alsamixer and make sure everything is turned on.  You may need to flip a few different bits to get it to work depending on which input alsa thinks you selected versus what "Sound Preferences" can see

try it then

---

### Post by lidex on 2011-02-09
You need to use a duplex profile or one with an input.

---

### Post by mubtasim123 on 2011-02-09
Thanks @tqft and @lidex :rolleyes::D\\:D/
it was really muted
I am really noob at ubuntu (first time on any linux distro):oops: where can I find most common cool codes that I can use to fix this type of simple problem when happens,:-k or any tutorials on using terminal would be ver helpful to me.8)
And thanks again for the help it works fine now.:p\\:D/

---

