---
title: "Media streaming"
date: 2009-07-14
forum: Mythbuntu
---

### Post by NautiusMaximus on 2009-07-14
I have a reasonably powerful Mythbuntu box in my living room, on which I can quite happily record as many TV programmes as I like.

I would like to watch some of those programmes in a different room in my house. I had toyed with the idea of building a low-spec Mythbuntu box to use as a front end to it, but I wonder if a neater idea might be to buy a media streamer?

I had a look at a media streamer on a website today, and it seemed to be designed to do exactly what I want, eg pick up TV programmes stored on a computer elsewhere on the network and stream them to a TV. However, it only claimed to be compatible with Windows.

Does anyone know if this setup can work with Mythbuntu? Any recommended hardware?

Thanks
NM

---

### Post by newlinux on 2009-07-14
This setup can work, but it depends on the product. I've used a couple of different networked media players (I think this is the same thing you are referring to as a "media streamer") with myth. Some will work with the UPnP server that myth comes with, and others can read NFS and/or SAMBA shares and play your media that way (for recordings you'll probably want to use the "mythrename.pl" script to make the filenames useful - if you go the SAMBA route).

the one I still have is a zensonic (ziova) z500 which I'm sure is no longer made, so unfortunately I can't recommend one personally. But for ones that work with myth's UPnP server you could look at:

[http://www.mythtv.org/wiki/UPnP#UPnP-client_hardware:](http://www.mythtv.org/wiki/UPnP#UPnP-client_hardware:)

What you'll lose with these is the ability to use the full frontend interface and extending the features of the box like you could with a computer, but if the device supports the codecs your TV shows and videos are recorded in, you'll be able to watch everything.

You could also look into the popcorn hour, which I know some use with myth.

---

