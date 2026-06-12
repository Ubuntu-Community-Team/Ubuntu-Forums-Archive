---
title: "Newbie Help with Resolution issue"
date: 2006-03-08
forum: Multimedia &amp; Video
---

### Post by chessieman on 2006-03-08
Hello all, I am Brand Spanking new to Ubuntu and Linux, I am considering swapping everything over to linux and need a little assistance. This is my second post, first post is my Firewire internet is not working althought it worked with the Live CD??

My situation
I decided on Ubuntu after some consideration and am now having an issue with my screen resolution. It is stuck in 1024X768 (which is not as bad as some people) but I really want it at the native 1280X1024. It is a flat screen monitor and is connected to an AMD box with a FIC motherboard (don't know the specs can get if need? ) 

I know this has already been addressed and I have looked at those posts but I have no idea what any of that means. Sorry, I know, Newbie blah blah blah. 

So if you think you can help me that would be great, otherwise I would just appreciate some "MANDATORY" reading for someone in my shoes and then when i figure out what is going on I will come back with more education.

Thanks in advance.

---

### Post by adamkane on 2006-03-08
Look at your xorg.conf file and see if you have 1280X1024 enabled.

```

sudo gedit /etc/X11/xorg.conf

```

My max resolution is more than 1024x768, but this is what I have in my xorg.conf.
Modes        "1024x768" "800x600" "720x350" "640x480"


I don't have any good advice. This is just a pointer.

---

