---
title: "Problem with Grip"
date: 2008-08-02
forum: Multimedia Software
---

### Post by Kouki on 2008-08-02
I've just set up my old laptop as a ubuntu media player and am trying to rip all my CD's to it.  K3B doesn't work, audio cd extractor only seems to want to rip to OGG which won't work with my MP3 player and the best looking program so far (grip) tells me "Invalid encoder executable check your encoder config, and ensure it specifies the full path to the encoder executable"

I'm prepared to give up on k3b and audio cd extractor but could someone tell me how to check my encoder config and what exactly I'm meant to be checking it for.

Thanks

---

### Post by Kouki on 2008-08-02
I think this should help anyone who knows more than me on this.

I just installed lame by using synaptic package manager but it hasn't helped.

[IMG]http://i16.photobucket.com/albums/b15/stuarthyden/Screenshotlame.png[/IMG]

---

### Post by omar_mandeel on 2009-01-29
I had the same problem but managed to get it figured out.  I installed lame (I think youve already done that) but all I had to do was fill in the path for the encoder executable. 
In the box next to encoder executable change from ¨lame¨ to /usr/bin/lame
That did it for me. Good luck!

---

