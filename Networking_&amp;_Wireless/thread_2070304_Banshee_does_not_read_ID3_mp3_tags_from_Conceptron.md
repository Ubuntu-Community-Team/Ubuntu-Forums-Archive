---
title: "Banshee does not read ID3 mp3 tags from Conceptronic CH3HNAS"
date: 2012-10-12
forum: Networking &amp; Wireless
---

### Post by acrocephalus on 2012-10-12
Hello,
I have a Conceptronic CH3HNAS set up to work as a UPnP server. I upload files through sFTP with Filezilla. When I set up Banshee to connect to the UPnP server, it retrieves the files but it is not able to read the ID3 mp3 tags.However, these tags are on the file, as if I download the mp3 again Banshee is able to read the ID3 tag. Is there anything I'm doing wrong? Is there any workaround for it?
Cheers!

Dani

---

### Post by acrocephalus on 2012-10-14
I just waited some time and I got the ID3 tags. I guess it has something to do with the NAS refreshing time.

---

### Post by acrocephalus on 2012-10-16
Finally I discovered how to do this. I had to enable the DAAP server instead of the UPnP in the NAS in order to retrieve the ID3 tags.

Dani

---

### Post by Ichijoe on 2013-03-04
Funny I have a Freecom DDNC which is in all tense and purpose a CH3HNAS. In fact given how crappy Freecoms support is and the lack of Media Options on it (e.g. No valid Media License Key e.g. Twonky), I resorted to flashing the DDNC (Dual Drive Network Center - for those who'd care) with the last version of the CH3HNAS Firmware off Conceptronics Website. And I have never looked back nor had any reason to regret it either.

I never had a problem with the actual reading of ID3 tags on my CH3HNAS in DDNCs clothing. But to get to my cruft of my Question.
Can you actually use Banshee in this way to edit ID3 Tags off the Network. I really need to reorganize my stuff in this post iTunes era.
And where iTunes 10+ had failed me in DAAP (mt-dappd) Banshee seems to have no trouble with it at all.
I currently reset my /home/media/iTunes Folder to permissions 755. But, this hasn't changed anything for me and I'm still unable to make changes to my ID3 Tags.

And now that I come to think of it I just rescaned my Folder(s) thought the DAAP interface - Nope that didn't do it for me either.
So does anyone else have an idea?

Thanks...

[EDIT] I managed to solve this by setting my Media Folder recursively with $ chmod -R 777 /home/Media

---

