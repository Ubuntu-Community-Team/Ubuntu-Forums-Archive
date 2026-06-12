---
title: "Anyone seen 64 Studio ?"
date: 2006-12-10
forum: Multimedia &amp; Video
---

### Post by mips on 2006-12-10
[http://64studio.com/](http://64studio.com/)

What do you think ?

---

### Post by Sethramoth on 2006-12-10
Here's an article about it at desktoplinux.com:

[http://desktoplinux.com/news/NS5486057047.html]("http://desktoplinux.com/news/NS5486057047.html")

It looks good for multimedia creation pro's.

---

### Post by damu on 2006-12-10
It works very well.
 
I do feel that for audio, it has the '64 bits syndrome" : you can't natively run wine, dssi-vst or fst. It means you can't open VST plug-ins or synths. And I don't think that you can have a distribution which targets professionnals and sound studios without vst support, or at least the possibility for the end user to add this functionnality. It is especially accurate for dynamic plug-ins and reverbs (SIR reverbs...).

Another point that bothers me is that it doesn't integrate jackdmp. So, for audio processing, you gain 3-5% of power on one core with a 64bits system , but still hardly use your second core in parallel processing. This approach for audio doesn't make sens to me. Let's focus first on getting all the power available of any recent DAW (dual core is the minimum. Some stations are already quad core, and at the end of next year will use 8 cores with the dual quad of AMD!)...and the main process (audio) should be handled by one core?!!!

There are less packages available for audio than with Ubuntu, but the essential ones are  here and the system is rock solid with rt-kernel out of the box, so if you don't need vsts, and that you didn't go dual core for audio processing, go for it, it's worth it.

---

### Post by mips on 2006-12-10
> **damu said:**
> It works very well.
 
I do feel that for audio, it has the '64 bits syndrome" 

i'm sure there is a 32bit version ?

---

### Post by October on 2006-12-10
Yes, there IS a 32bit version which neatly circumvents the lack of flash, etc. or running in a chroot.

I wrote a short review of the 32bit version on my blog if anyone is interested:

[http://oktyabr.wordpress.com/2006/12/02/64-studio-10-olympic-released/](http://oktyabr.wordpress.com/2006/12/02/64-studio-10-olympic-released/)

---

