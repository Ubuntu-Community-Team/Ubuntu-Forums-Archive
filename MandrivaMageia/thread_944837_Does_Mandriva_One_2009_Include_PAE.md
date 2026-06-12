---
title: "Does Mandriva One 2009 Include PAE"
date: 2008-10-11
forum: Mandriva/Mageia
---

### Post by Vince4Amy on 2008-10-11
I'm going to give Mandriva One 2009 a go, I don't need to download the DVD Image because I'll just get all the software I need from the repositories. 

I am aware that there is no 64 bit version of Mandriva One Available and I have 4GB of RAM. Older versions of Mandriva One did not include PAE so not all of my RAM was usable. I'd rather not have to download the full DVD just for the sake of having a 64 bit edition.

If it's not included is there an easy way of enabling PAE on the system?

---

### Post by Antman on 2008-10-11
Posting this for others to see as well:
[http://forum.mandriva.com/viewtopic.php?t=96032&highlight=pae]("http://forum.mandriva.com/viewtopic.php?t=96032&highlight=pae")

---

### Post by AdamWill on 2008-10-12
The kernel in One supports up to 4GB of RAM (no PAE) so in practice it may miss a few hundred MB. If you want PAE support, though, you can just install One and then switch to kernel-server (which has PAE support).

Do note, though, that kernel-server won't likely work with the NVIDIA proprietary driver, as it includes Xen support, which conflicts with the proprietary NVIDIA driver.

---

### Post by Vince4Amy on 2008-10-12
> **Antman said:**
> Posting this for others to see as well:
[http://forum.mandriva.com/viewtopic.php?t=96032&highlight=pae]("http://forum.mandriva.com/viewtopic.php?t=96032&highlight=pae")

That was me, I posted in both forums to see which was the most active. Thanks for the help everyone.

---

### Post by AdamWill on 2008-10-12
The reason I replied here and not there is that this forum is *less* active so I can check it quickly on a weekend :)

---

