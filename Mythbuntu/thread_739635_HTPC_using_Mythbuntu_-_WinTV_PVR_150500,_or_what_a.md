---
title: "HTPC using Mythbuntu - WinTV PVR 150/500, or what about an HVR-1300?"
date: 2008-03-29
forum: Mythbuntu
---

### Post by hihp on 2008-03-29
Hi,

first, I've never gotten around to using Linux so far but for my project of building an HTPC, I plan to use Mythbuntu... so what I am looking for is a solution that does not require recompiling kernels too often ;-)

Right now I am wondering what kind of tv card I should put into my system. I am using analog tv right now (via cable, but this is Germany, so "cable" has not got much to do with cable in the US or other places), so I definitely need an analog tuner card.

Seeing how being able to watch one program while recording the other is nice, I was originally planning to go with two Hauppauge WinTV PVR-150s, or one PVR-500 (to save a PCI slot). These seem to be well-supported with the ivtv drivers and therefore should run with Mythbuntu 7.10 out of the box, right?

However, while browsing around I found the Hauppauge HVR-1300, which looks interesting... because DVB-T **is** available in my area. So now I am wondering if maybe I should use two HVR-1300s instead of the PVR-150s.

Question of course: how is support for the HVR-1300 these days? Stuff I found on the web ranges from "not supported at all" to "works out of the box with other variations of Linux". Does anybody have an idea about support in Ubuntu -> Mythbuntu?


(FYI: my system is planned to consist of a ASUS M2N-VM DVI or Gigabyte GA-M68SM-S2(L) with an AMD Athlon X2 BE-2300, 2 Gigs of RAM and and MSI NX7300LE-TD128EH providing TV-out... does that sound reasonable, or does any of these components strike anybody as problematic?)

---

### Post by williammanda on 2008-03-30
Reference this site for use of the HVR-1300:
[http://www.linuxtv.org/wiki/index.php/Main_Page](http://www.linuxtv.org/wiki/index.php/Main_Page)

Thanks

---

### Post by hihp on 2008-03-30
> **williammanda said:**
> Reference this site for use of the HVR-1300:
[http://www.linuxtv.org/wiki/index.php/Main_Page](http://www.linuxtv.org/wiki/index.php/Main_Page)
Well, thanks! Of course I **had** searched linuxtv.org already, but the fs***king Wiki search is so bad that searching for "HVR" actually turns up no hits; searching for "HVR-1300" however **does** turn up a [result on the v4l project](http://linuxtv.org/hg/v4l-dvb?cmd=changeset;node=3e90edbf7c53584f109fe091d7380e8bda9fa282;style=gitweb).
So it looks like basic support is there, but no support for the hardware MPEG encoder of the card. In that case, I think I'll play save with the PVR 500; I can always add a HVR 1300 later.

Any input on the rest? :-)

---

