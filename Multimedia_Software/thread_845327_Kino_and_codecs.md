---
title: "Kino and codecs"
date: 2008-06-30
forum: Multimedia Software
---

### Post by pompiuses on 2008-06-30
I've successfully been able to capture and edit video with Kino following this thread: [http://ubuntuforums.org/showthread.php?p=4649034](http://ubuntuforums.org/showthread.php?p=4649034)

Since I'm planning to put my video on the web, I need to export it into i.e. divx or xvid or any other suitable format that youtube or google will understand.

I've searched the forum and tried to install 'ffmpeg', but I can't see either divx or xvid anywhere inside Kino. There's only "Genereic MPEG2" or "MPEG4-AVI", which both doesn't give me the quality I want.

So does anyone know how to get and install some good codecs for Kino? I.e. divx or xvid?

I'm using Ubuntu 8.04 by the way.

Thanks!

---

### Post by wolfen69 on 2008-06-30
install the [Medibuntu]("http://www.psystar.com/index.php?&page=shop.product_details&category_id=13&flypage=flypage_images.tpl&product_id=1&option=com_virtuemart&Itemid=72") repos and then search synaptic for gstreamer. you can install the good, bad, and ugly codecs.

---

### Post by pompiuses on 2008-06-30
Thanks for the tip, but I already had all of those installed except for the ugly one. I installed that as well, but I don't get any more choices inside Kino.

---

### Post by pompiuses on 2008-07-01
Alright, it looks like everything is actually installed correct as I'm able to export to both mpeg and avi in various quality.

I discovered that Kino uses mpeg2enc to encode mpegs.

By default the "video pipe" kino uses looks like this:
mpeg2enc -v 0

I've looked at the mpeg2enc manual, but it's too cryptic to make any sense. At least to me.

So does anyone know a good tutorial/how-to for tweaking mpeg2enc?

---

### Post by otto67 on 2008-09-15
I would not bother within Kino. Your Kino has some scripts missing but i cannot help. Instead i would recommend to export your video to mpeg-2 or dv format. Then open the resulted file with Avidemux. There you can convert and resize etc.etc the video as you desire.

---

### Post by remeeraz on 2008-10-14
> **otto67 said:**
> I would not bother within Kino. Your Kino has some scripts missing but i cannot help. Instead i would recommend to export your video to mpeg-2 or dv format. Then open the resulted file with Avidemux. There you can convert and resize etc.etc the video as you desire.

If you do decide to use Avidemux for anything, download the latest version source;
[http://downloads.sourceforge.net/avidemux/avidemux_2.4.3.tar.gz](http://downloads.sourceforge.net/avidemux/avidemux_2.4.3.tar.gz)

and compile it from scratch;
[http://www.avidemux.org/admWiki/index.php?title=Compiling_Avidemux](http://www.avidemux.org/admWiki/index.php?title=Compiling_Avidemux)

It's just a whole lot better!

---

