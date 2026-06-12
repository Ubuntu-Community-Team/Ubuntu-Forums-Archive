---
title: "ubuntu 7.10 sees DVB card, still need replace kernel?"
date: 2008-02-17
forum: Multimedia &amp; Video
---

### Post by yardern on 2008-02-17
I have installed ubuntu gutsy (7.10), it sees DVB card (Skystar2), and I even can get the channels with nscan.

Do I still need replace kernel as descripted in
[http://www.hoochvdr.info/viewtopic.php?f=37&t=439](http://www.hoochvdr.info/viewtopic.php?f=37&t=439)

And what about the official VDR package here?
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=vdr](http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=vdr)


Please.

Thank you.

---

### Post by yardern on 2008-02-18
I think it is not needed.

But can I use VDR in ubuntu, or I have to compile by myself?

---

### Post by steefjeqv on 2008-02-20
Hi,

If your DVB card is recognized and you're able to scan for channels, you don't need to change the kernel.

You can always use Kaffeine to check if your DVB card is fully functional.

The Ubuntu VDR version is available through synaptic, along with some vdr plug-ins.

The Skystar2 is a budget card, which means you're going to have to use the xineliboutput plug-in in order to get VDR working. It's also available in Ubuntu.
This can be a bit tricky to set up. I've never used Ubuntu together with VDR.
I can confirm that it works using Sidux and Etch as operating system.

Greetings,
Steven

---

