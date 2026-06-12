---
title: "Another network Catch 22?"
date: 2010-12-27
forum: Networking &amp; Wireless
---

### Post by mango42 on 2010-12-27
Hi. It seems every time I upgrade Ubuntu (**Studio 10.04** in this instance) there are new network issues. It's a continual 'catch 22' as I can't get on the net to get the files needed to get on the net! See what I mean?

Normally with the studio versions (that don't come with network manager installed) I just use another machine to get all the files that lead up to installing **nm-applet**(xxx).deb

This time however, nm-applet *itself* won't install until I get a copy of **mobile-broadband-provider-info** - a file I can't seem to find anywhere and I don't even *use* mobile broadband anyway!

Aaarrrggghhh! Is there perhaps some 'political' issue here that makes net access impossible without a whole lot of unnecessary grief?

I thought Ubuntu was supposed to be inclusive - yet, as the versions roll by, it doesn't ever seem to 'include' people without net access!

_This is not a criticism of Ubuntu itself_, which IMO is utterly brilliant - but there does seem to be a counter-productive (and perhaps antagonistic!) gremlin at work here...

---

### Post by cchhrriiss121212 on 2010-12-27
Hi mango,
This is specific to Ubuntu Studio, and it is something that I hope the devs will review in the future. There are no end of threads with this exact problem, but hardly any devs actually check the forums.

However: All the network manager files you need are included on the studio image. Just open up file manager, browse to your image or mounted DVD and search for whatever package you need. None of this is mentioned in the release notes, it is just something I found out a while ago by accident. 

Network manager is left out of Studio as it was found to interfere with audio processes. On my machine it has unnoticeable effect, but you may find otherwise.

My advice for you:
Stick to LTS releases
Start using a "regular OS" and then add the audio packages you like. Studio is a good introduction to FOSS audio, but once you know what you want, it is better to customize the OS for audio yourself.

---

### Post by mango42 on 2010-12-28
Sound advice, thanks **cchhrriiss**

Yeah, I raided my USB install for the nm-applet stuff but still can't find this blasted and (to me) totally unnecessary 'broadband' database. Sounds like a big brother 'initiative', to me ;)

---

### Post by cchhrriiss121212 on 2010-12-28
I just had a look at the image for Studio 10.10, here is the path:
/pool/main/m/mobile-broadband-provider-info/

---

### Post by mango42 on 2010-12-29
Duh! Thanks again - I guess it'll probably be the same path in 10.04

Edit: It is. Just shows what a lousy 'looker' I am!
/pool/main/m/mobile-broadband-provider-info/mobile-broadband-provider-info_20100407-1_all.deb

---

