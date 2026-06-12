---
title: "Missing Music"
date: 2009-02-28
forum: Mythbuntu
---

### Post by craigmarti on 2009-02-28
Hi all,
     I just set up my first mythbuntu box and the install went very smoothly.  I have been using Ubuntu for quite some time but this is my first mythbuntu box.  I have a slight problem with all of my music showing up.  I have quite a bit of music on my external hard drive (900GB).  I created a symbolic link from /var/lib/mythtv/Music to my external hard drive.  I then had Mythtv scan my music (took about 10 minutes) and it returned with no errors.  When I went to "All My Music" only about 10% of my music was available.  The music that was listed was completely random and I don't see any logic behind it.  I have tried to rescan three times now and I have had no luck.  Has anyone seen this before or do you have any suggestions on how I can get mythtv to see all my music.  Thank you in advance.

Craig

---

### Post by craigmarti on 2009-02-28
Update:  I feel like an idiot but I figured it out.  My music was being sorted by its  id3 tag and not the directory structure.  The majority of my music was missing id3 tags.  I now need to decide if I want to use the id3 tag or the directory structure.  Thank you to all who spent any time thinking about this issue.

---

