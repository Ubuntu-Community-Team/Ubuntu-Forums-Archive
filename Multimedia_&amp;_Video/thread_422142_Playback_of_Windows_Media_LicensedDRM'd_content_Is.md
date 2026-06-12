---
title: "Playback of Windows Media Licensed/DRM'd content: Is it possible in Ubuntu?"
date: 2007-04-24
forum: Multimedia &amp; Video
---

### Post by jeznet on 2007-04-24
I really love Ubuntu and have been wanting to install it completely into my laptop to wipe out my slow clogged Windows XP. I have listed all my reasons to switch, including trying out alternative free applications. However there is one last thing in my checklist that I have to mark and that is Windows Media.

I have a monthly subscription from a site that delivers TV shows, live TV, etc.( IPTV is thats what its called?) and its main transport medium is Windows Media Video. Once a month, I download a licence via windows media player in order to playback content and renews itself after a month. 

Now in linux, there is no such thing as Windows Media Player but alternative programs such as Mplayer, Totem, etc...and expand its playback by downloading codecs..

My question is, is it possible to play licensed wmv content in Ubuntu? It is the only thing thats making me not uninstall windows.

-Jez

---

### Post by jeznet on 2007-05-09
Anyone?

---

### Post by Lord Illidan on 2007-05-09
> **jeznet said:**
> I really love Ubuntu and have been wanting to install it completely into my laptop to wipe out my slow clogged Windows XP. I have listed all my reasons to switch, including trying out alternative free applications. However there is one last thing in my checklist that I have to mark and that is Windows Media.

I have a monthly subscription from a site that delivers TV shows, live TV, etc.( IPTV is thats what its called?) and its main transport medium is Windows Media Video. Once a month, I download a licence via windows media player in order to playback content and renews itself after a month. 

Now in linux, there is no such thing as Windows Media Player but alternative programs such as Mplayer, Totem, etc...and expand its playback by downloading codecs..

My question is, is it possible to play licensed wmv content in Ubuntu? It is the only thing thats making me not uninstall windows.

-Jez

Not sure..Probably not..DRM content is a big issue. What you could do is run Windows in Ubuntu, with VMware.

---

### Post by jeznet on 2007-05-09
Well that kinda beats the purpose of not running windows...

---

### Post by markharding557 on 2007-05-13
> **jeznet said:**
> Well that kinda beats the purpose of not running windows...

don't think you can use drmed files in linux however if you run windows in vmware or virtualbox which is free you only need to run win when needed if it crashes it will not crash your pc because its in a vm and you will have windows at the click of a button without dual booting:)

---

### Post by Kadin2048 on 2007-05-13
> **jeznet said:**
> I really love Ubuntu and have been wanting to install it completely into my laptop to wipe out my slow clogged Windows XP. I have listed all my reasons to switch, including trying out alternative free applications. However there is one last thing in my checklist that I have to mark and that is Windows Media.

I have a monthly subscription from a site that delivers TV shows, live TV, etc.( IPTV is thats what its called?) and its main transport medium is Windows Media Video. Once a month, I download a licence via windows media player in order to playback content and renews itself after a month. 

Now in linux, there is no such thing as Windows Media Player but alternative programs such as Mplayer, Totem, etc...and expand its playback by downloading codecs..

My question is, is it possible to play licensed wmv content in Ubuntu? It is the only thing thats making me not uninstall windows.

-Jez

Basically ... no.

Theoretically, it ought to be possible to build some sort of a client program that downloads the licenses that you get monthly, and uses them to decrypt the content, but such a program would probably be illegal in the U.S. due to the DMCA because it could be used for "circumvention." If such a thing exists (and I'm not being cagey here -- I really don't think that it does, because frankly very few Linux users really care about DRMed WMA content) you'd have to troll forums like doom9.org.

There are programs on Windows that will use the WMP keys to decrypt Windows Media content and render it playable on non-Windows systems, but again, such software is illegal in the U.S. and you'll only find it on sites that deal with such things.

There's basically no way, and probably will never be any way, to implement a DRM system in a truly open-source OS, because DRM is fundamentally just a matter of hiding the decryption key from the user, and when you have open source, you can't pull the wool over their eyes. It's just not possible.

As other people have pointed out, if you really need the WM content, your best bet is probably to use VMWare. Linux and DRM just don't mix, and never will.

---

