---
title: "Hauppauge Nova T-500 Keybindings"
date: 2009-08-17
forum: Mythbuntu
---

### Post by Elijah2104 on 2009-08-17
Hi, I have had [[COLOR="Blue"]this thread [/COLOR]]("http://www.mythtvtalk.com/forum/hardware/10973-hauppauge-nova-t-500-keybindings.html")on the MythTalk.com forum since February but no one appears to be able to help me.

I really hope that someone here can!

The essence of my problem is that not all the buttons work in MythTV for the remote control supplied with my Nova T-500.

IRW is showing all the correct output with every button.  To quote my original post:

> My lircd.conf corresponds exactly to the output from IRW.

My lircrc corresponds the remote control output to the same key configurations as is expected by MythTV (e.g. TV is ALT+T).

So why doesn't mythtv recognise that these buttons are working?

I have upgraded to version 9.04 but that hasn't made a difference.  Does anyone have any ideas on how to fix this?

---

### Post by Elijah2104 on 2009-10-30
Finally I've just solved it.

The problem was the version of lircrc that MythTV was using was not the one that I had verifed to be correct. It hadn't occurred to me that I was not logged on specifically as MythTV. 

I updated the file /home/<USER>/.mythtv/lircrc and it works a treat now.

It's only taken me eight months to work it out!

---

