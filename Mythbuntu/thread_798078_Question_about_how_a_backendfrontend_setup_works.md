---
title: "Question about how a backend/frontend setup works"
date: 2008-05-17
forum: Mythbuntu
---

### Post by Goobicon on 2008-05-17
So, right now I don't have any hardware or software set up, but I'm making sure I understand what hardware I'll need for a video server backend.  Does a backend actually utilize a video card?  I've done some reading in the myth wiki and I'm still not sure.  Doesn't it really just use the tuner (Hauppauge) to en/decode video and send it to the frontend via ethernet?  And then I would want the really nice video card for my frontend (depending on what I want it to be capable of or what I'm hooking my frontend to).  Again, right now I don't actually *have* the hardware but I've got a wishlist thrown together on newegg, all of the parts seem to be ones that will work with ubuntu/mythtv.  If I do need a nice video card for my backend, can someone explain how/why?  Thanks.

---

### Post by volkswagner on 2008-05-17
If your backend/server is not going to have a frontend, yes get a basic video card.  You just need it for the install and configuration.  

Your frontend machines will need better video cards for HD.  Standard definition tv works well on nvidia 440 cards from years ago.  Gforce 6200 and up work well for HD.  Either way you don't need high end gaming cards.

The decoding will be done on the frontend.  The server will act as a file server using network protocall.

---

