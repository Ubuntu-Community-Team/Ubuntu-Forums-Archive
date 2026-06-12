---
title: "Expanding wireless network through a home server"
date: 2009-04-23
forum: Networking &amp; Wireless
---

### Post by Pappa K on 2009-04-23
I'm no expert in computers, and have a big question.
 
The internet connection at home is in a corner of the house and the wireless router (w1) doesn't reach the whole house. Also it's imposible to move the connection from there. 
 
So, I have a spare computer with wireless and a spare wireless router (w2). 
 
I want to know if I can use this computer (set it at the middle of the house) to connect through wireless to (w1) and get access to internet. Then use the computer as a bridge or server and through the ethernet port of the computer send the internet to the spare wireless router (w2) and thus making the wireless internet reach every point of the house... 
 
I don´t mind doing it throug ubuntu server or ubuntu desktop. I just need help.
If I can also use this computer as media server, better. 
 
Thank you.

---

### Post by Bucky Ball on 2009-04-23
You don't need the extra computer (or wasting the extra energy) you just need the router. Set that to a different IP address than your original router (eg. 192.168.0.1 and 192.168.0.2). 

Now the original router *should* pass through the second router and serve addresses to the computers using either router. You may need to fiddle with the config in the second router to achieve this. This way, you could have some computers using the original access point and some using the second, all depending on requirements.

If you can run a cable from one router to the next, it simplifies things. Let me know how you go.

** Edit: **Scratch that**, this page proves me wrong:

[http://ask-leo.com/can_i_use_a_second_wireless_access_point_to_extend_my_wireless_network.html](http://ask-leo.com/can_i_use_a_second_wireless_access_point_to_extend_my_wireless_network.html)

If you can cable the routers together you should have no problems. That is the setup I am running so I can probably help with that. Same as before:

1/ Set second to a different IP address than your original router, the one getting internet (eg. original: 192.168.0.1 and second: 192.168.0.2). To configure the routers, plug them directly into a computer with an ethernet cable one at a time, make sure they are not plugged together. This can get confusing and you can end up configuring the wrong one etc (I have two D-Links with the same config GUI).

2/ Plug ethernet cable from regular ethernet port on original router to regular ethernet port on second, ***not*** WAN port!

3/ Make sure machines are set to Auto DHCP and the original router is set to serve them (and the second router is not)

... and that should be it.

---

### Post by Bucky Ball on 2009-04-23
Scratch again! As the comments on that last link say, it seems to be possible to extend your range with a second router, but no-one's telling us how, just saying you can. I'll keep looking.

---

### Post by Pappa K on 2009-04-23
u

---

### Post by Bucky Ball on 2009-04-23
This might give you some clues:

[http://ask-leo.com/comments_000363.php?page=6](http://ask-leo.com/comments_000363.php?page=6)

It seems to be more about whether your hardware is capable rather than can it be done, if you know what I mean. Seems like WDA plays a part, which I know nothing about, but you might want to look into it. :)

---

### Post by Pappa K on 2009-04-23
That's the problem, I can not connect the second router through ethernet cable from the first router because it's far away, I don't want cables through the house, and can not pass them through walls because something is jammed there, so that's not a possibility. 

So since I would like to set up a home server, I could take advantage of it and expand wireless network coverage, if it is possible.

Thank you anyway.

---

### Post by Pappa K on 2009-04-23
also another thing. neither router has a repeater/bridge function.

---

### Post by Pappa K on 2009-04-23
As it says here [http://ask-leo.com/can_i_use_a_second_wireless_access_point_to_extend_my_wireless_network.html](http://ask-leo.com/can_i_use_a_second_wireless_access_point_to_extend_my_wireless_network.html)
 
"And you're expecting the access point to access point wireless connection to act as a virtual extension cable then this will probably not work. Access Points typically do not communicate with each other."

---

### Post by oldsoundguy on 2009-04-23
I use a repeater.

---

### Post by Pappa K on 2009-04-23
I don't want tu buy anything new... Just want to know if a computer can receive internet wirelessly, then act as a server, and send internet through the ethernet port to a wireless router, all other computers connect to internet an LAN through this second wireless router. ¿Can it be done? ¿How do I set it up? 
Please help

---

### Post by Bucky Ball on 2009-04-23
> **Pappa K said:**
> As it says here [http://ask-leo.com/can_i_use_a_second_wireless_access_point_to_extend_my_wireless_network.html](http://ask-leo.com/can_i_use_a_second_wireless_access_point_to_extend_my_wireless_network.html)
 
"And you're expecting the access point to access point wireless connection to act as a virtual extension cable then this will probably not work. Access Points typically do not communicate with each other."

You didn´t read far and seem to be missing my posts. In the comments below that post, a poster states Leo has no idea what he is talking about and he should research his facts before sticking up his threads as he is doing just that; using a second router to extend his network.

Keep digging.

---

### Post by oldsoundguy on 2009-04-24
A little light reading is called for, I believe.
[http://en.wikibooks.org/wiki/Wireless_Home_Network_Basics](http://en.wikibooks.org/wiki/Wireless_Home_Network_Basics)
[http://www.howstuffworks.com/home-network.htm](http://www.howstuffworks.com/home-network.htm)

I have 7 computers on my network and only 2 are hard wired. The rest are wireless. 
I have an access point, that, because of the construction of my place, had to be HARD WIRED into the router. (that took a 50' cat5 cord.)
The system works flawlessly.

---

### Post by Bucky Ball on 2009-04-24
Like oldsoundguy says, seek and ye shall find. This is the post I mentioned from the link I posted originally regarding Leo's claim that it is not really possible to use wireless access points (routers) to extend range being not possible:

> This is completely wrong.
I have setup long distance wireless LANs using Linksys WAP54g access points.
I have a home office with cable internet and I had to tie in a trailer at a construction site about a block away. I used 2 Linksys WAP54Gs with External Hawking directional antennas. It worked perfectly for over a year until we moved the trailer. The key is to use the same brand/model at each end.
  I've since used the same WAP54Gs at home as external wireless NICs for an old iMac that I didn't want to upgrade with an airport card. I'm now using the same WAP to connect my Direct TV HD Receiver to the wireless network to download my On demand movies. I can easily stick a switch on that end and add as many devices as I want.
  It's do-able and easy.  Leo, you should check your facts before publishing that this would 'probably' not work.
          Posted by: **ivan** at February  7, 2009  7:40 PM

From:

[http://ask-leo.com/can_i_use_a_second_wireless_access_point_to_extend_my_wireless_network.html](http://ask-leo.com/can_i_use_a_second_wireless_access_point_to_extend_my_wireless_network.html)

---

