---
title: "Jack and alsa... whats going on?"
date: 2006-11-08
forum: Multimedia &amp; Video
---

### Post by phishman13 on 2006-11-08
Hello all,

I am relatively new to ubuntu and linux in general, so this is a newbie level question.

I have ubuntu 6.06 installed and all the apps recommended in the ubuntu studio prep guide.  I have gotten so far as to learn how to patch with jack, but when I get to that point, I go to the connect menu in jack and nothing appears in the audio tab.  No matter what program I open, its audio ins and outs dont get updated in jack.  The midi stuff works just fine, but I just can't see anything in the audio tab.  I have been searching and found something about the .asoundrc file and such, but have no idea how to create this or configure alsa to work with jack.  I am working with the soundblaster live 24-bit card at the moment.  If you guys could give me any help in resolving this matter, like creating the proper .asoundrc file or whatever other solutions might be better, I would greatly appreciate it!

Thanks a lot!

---

### Post by nerubian on 2006-11-11
hi,
i am also new to jack and audio programs in ubuntu.but i find some pages very useful.you can try the commands in this pages and maybe you can solve your problem.

[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)
[https://help.ubuntu.com/community/HowToQjackCtlConnections](https://help.ubuntu.com/community/HowToQjackCtlConnections)

i also had some problems with my sound card drivers and selection.then these pages may be helpful:
[http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Live+5.1.&chip=emu10k1&module=emu10k1#aso](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Live+5.1.&chip=emu10k1&module=emu10k1#aso)
this one is about configuring .asoundrc file.
but i think if you can play other stuff and hear sound appropriately, then there may be problems with some modules in alsa about jack.the first link may be helpful.
i am also new to forum and this my first post.sorry for any mistakes.

---

