---
title: "flashplayer sse2"
date: 2014-01-15
forum: Multimedia Software
---

### Post by helgacecil on 2014-01-15
Hello,
my english is not so very good,but I`ll try.I`m a very linux-beginner.I`ve installed Ubuntu12.04 on my pc.
At time I can`t look flash-streams on youtube or on tv -channel.I heard about that this doesn`t work in linux,if you you don`t have a 
cpu with sse2.(athlon xp 1800)
But when I boot with an antix-live-cd ,I can look every youtube-stream and so on.
So there must be a possibility.Can someone help me?
Ok,thanks

---

### Post by carl4926 on 2014-01-15
If the live cd includes a old version of flash which doesn't require sse2 in the cpu,then it might well work

---

### Post by helgacecil on 2014-01-15
Yes,then I would like to have an old version of flash in ubuntu too.How can I make it work?

---

### Post by carl4926 on 2014-01-15
Somewhere, someone will have a download available I think it's version 10.3 of flash you need
I think, Linux Mint in it's 13 release, which is the same as 12.04 in Ubuntu, has this old flash in it's repos

I think I found it
[http://download.macromedia.com/pub/flashplayer/installers/archive/fp_10.3.183.90_archive.zip](http://download.macromedia.com/pub/flashplayer/installers/archive/fp_10.3.183.90_archive.zip)

You will need to extract the archive and you just need the file
libflashplayer.so

---

### Post by helgacecil on 2014-01-15
Now I found libflashplayer.so.But what shall I do with this?

---

### Post by carl4926 on 2014-01-15
First remove the current flash plugin, which will have been installed if you have installed the ubuntu-restricted-extras

copy the new file first to your home folder

then open a terminal and do

```
sudo mv libflashplayer.so /usr/lib/flashplugin-installer
```

---

### Post by helgacecil on 2014-01-19
Hello,
this didn`t work,because the terminal allways told me,that this is an old version (error),but I found a page[http://forums.debian.net/viewtopic.php?f=16&t=89675](http://forums.debian.net/viewtopic.php?f=16&t=89675).This worked.Anyway,thank you for your friendly help.

---

### Post by eric13 on 2014-04-15
I've been reading the advices on the debian forum and [here](https://wiki.mageia.org/en/Flash_Plugin_Installation#Installing_on_.22old.22_.28non-SSE2.29_machines)

The no SSE2 11.2.x lib recommanded there is the 11.2.202.236 from June 2012 ([[www.adobe.com/support/security/bulletins/apsb12-14.html]security](www.adobe.com/support/security/bulletins/apsb12-14.html]security) bulletin[/url])

When I see the so many critical security issues in Flash Player ( [http://www.cvedetails.com/vulnerability-list/vendor_id-53/product_id-6761/Adobe-Flash-Player.html](http://www.cvedetails.com/vulnerability-list/vendor_id-53/product_id-6761/Adobe-Flash-Player.html) ), we should STOP to recommend any old 11.2 lib!

The lastest 10.x is already better, one year younger: the version 10.3.183.90 was released on 2013-06-11  (fix CVE-2013-3343)
But it is probably also affected by more recent bugs.

So the more secure way would be to go with the free alternative Gnash
or hope than Adobe fix the compilation flag of the 11.2.202.xx releases.

---

### Post by monkeybrain20122 on 2014-04-16
Totally agree that  old flash is a security risk that should never be recommended. But gnash is a waste of time and space that never works except maybe on one or two demo videos on Youtube(along with lightspark), it is a non solution.

The best though imperfect solution in this case would be Viewtube [http://userscripts.org/scripts/show/87011](http://userscripts.org/scripts/show/87011), it works better than flash when it works, but only on a few popular sites (Youtube is the big one) You may also want to install the toggle-mixed-active-content addon for Firefox so it won't block the media plugin backend for Viewtube. [https://addons.mozilla.org/en-us/firefox/addon/toggle-mixed-active-content/](https://addons.mozilla.org/en-us/firefox/addon/toggle-mixed-active-content/)

---

### Post by doctorwho on 2014-10-20
I know this thread is a few months old, but I would like to suggest the possibility of using the Pipelight plugin with Firefox (since Chrome doesn't support non-sse2 processors either now) and use the Windows version of Adobe Flash. For some reason, the latest Windows versions of Adobe Flash still work on non-sse2 processors. So this is a viable option. And for some sites like Youtube, you should be able to watch many videos without Flash if the browser and the video support HTML5.

---

