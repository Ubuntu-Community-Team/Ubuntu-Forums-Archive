---
title: "Connect Playstation 3 to MythTV"
date: 2007-11-24
forum: Multimedia &amp; Video
---

### Post by JBot on 2007-11-24
I have my media server running Ubuntu 7.10. I have mythTV backend installed and running properly, since i can connect to it from my other machines. 
However, on the Playstation3, it can see the mythTV setup, and it sees every individual file being hosted, (music, video, pictures) but instead of the file name, it says 'Unsupported Data'. I have tried installing mediaTomb as well, but i get the same problem, everything still comes up as Unsupported Data.

Now i know this should be posted on a playstation forum, since it is a playstation problem. The only reason i am posting it here is because on the playstation forums, it is full of kids who know more about the games, and not so much on the technical aspect. Im hoping someone on this forum has his Playstation streaming media off an ubuntu machine, and then they can help me out.

Thanks in advance!

---

### Post by yellowbean on 2007-11-29
To get Mediatomb working you need to add <protocolInfo extend="yes"/> to the ~/.mediatomb/config.xml.

Check out this site for the install how-to: [http://www.freesoftwaremagazine.com/blogs/upnp_mediatomb_ps3_and_me](http://www.freesoftwaremagazine.com/blogs/upnp_mediatomb_ps3_and_me)

---

### Post by xxLONESTARxx on 2008-01-29
> **yellowbean said:**
> To get Mediatomb working you need to add <protocolInfo extend="yes"/> to the ~/.mediatomb/config.xml.

Check out this site for the install how-to: [http://www.freesoftwaremagazine.com/blogs/upnp_mediatomb_ps3_and_me](http://www.freesoftwaremagazine.com/blogs/upnp_mediatomb_ps3_and_me)

If this works, I will have no reason to boot into XP... \\:D/  Thanks for the link yellowbean!=D>


EDIT: Worked like a charm!

---

