---
title: "MPD and LAN help"
date: 2009-04-09
forum: Multimedia Software
---

### Post by passonno on 2009-04-09
Hello,

So I have mpd setup on my main computer, with 'mpd' as my user, and am able to use ncmpd/sonata to browse the files in my music folder (though with no sound)but I cannot for the life of me figure out why I cannot access mpd on the LAN via my netbook.  

When I attempt to connect, it tells me that the connection was refused on port 6600, and it times out with error 15, which I cannot find information on anywhere, and I did open this port in my firewall for this purpose.  

Does anyone have any idea what I could be doing wrong?

---

### Post by passonno on 2009-04-09
Ok, so I figured out the first part, which was to make sure and comment out the "bind to address  "localhost" in order to connect.  

Now, how do I make it make sound?

On the server pc or the client pc?

---

