---
title: "flash player broken"
date: 2010-01-17
forum: Mythbuntu
---

### Post by benlyboy on 2010-01-17
hi all

After a weekly update I seem to have developed a problem with mythweb.

Well to be precise with the flash player in mythweb. When I try to view a recording, I get this message. 

> 
200,Stream not found, NetStream,Play, NetStreamNotFound, clip:
'[Clip] 'http://xxxxxx
xxx:80//mythweb/pl/stream/1054/1263529140.fvl"


The "x's" are obviously my ip address

I took a look at everything else, on both mythweb and the frontend and everything else seems to be working ok.


One last thing not sure if it has something to do with it but the last time I switched the box on, at one point while booting it said something like "it had to do a database update"

Hope someone can help :)

---

### Post by benlyboy on 2010-01-17
Can no one help?

I have no idea where to start looking

---

### Post by benlyboy on 2010-01-20
I guess no one here can help ...

Maybe someone can give me some ideas where I might look for an answer.

One thing I notice the other night it seems that at some point by accident  I moved from build .22 to build .23. I'm thinking that this is what upset my mythweb flash player....

I would be grateful for any help

 Thanks

---

### Post by benlyboy on 2010-01-23
Hi 
Been doing some investigating and have noticed that the permissions for the thumbnails and the recordings are different. The thumbnail under group access has read write, while the clip has read only.

Not sure why this would make a difference, but it is interesting that the thumbnail works but the recording will not.

What permissions are needed for this to work...?

---

### Post by benlyboy on 2010-01-24
I am trying to fix this but am working blind. As I have very little to work with.
Is there any logs that I should be looking at that might show what is going on when I click on the flash player?

I've really hit a wall on this. So any help would be gratefully accepted

So please help :(

---

