---
title: "How to access MythTV config via text editor?"
date: 2012-06-18
forum: Mythbuntu
---

### Post by Personatech on 2012-06-18
OK, I think I may have inadvertently turned on LCD Output when I have no LCD. Both FrontEnd and BackEnd programs are now apparently sending output to the non-existent LCD so I can't see standard output, meaning I can't simply go back and correct my error via the usual configuration utilities.  The Mythbuntu Control Centre doesn't seem to offer LCD Output as an option so it looks like I need to manually change a configuration file but can't seem to find it.  I'm running Mythbuntu 12.04.  Can someone point me in the right direction?  Thanks!

---

### Post by klc5555 on 2012-06-18
Can you ssh -Y in from another machine and then run mythtv-setup from that remote machine?

---

### Post by tgm4883 on 2012-06-18
> **Personatech said:**
> OK, I think I may have inadvertently turned on LCD Output when I have no LCD. Both FrontEnd and BackEnd programs are now apparently sending output to the non-existent LCD so I can't see standard output, meaning I can't simply go back and correct my error via the usual configuration utilities.  The Mythbuntu Control Centre doesn't seem to offer LCD Output as an option so it looks like I need to manually change a configuration file but can't seem to find it.  I'm running Mythbuntu 12.04.  Can someone point me in the right direction?  Thanks!

With LCD output on, you would still see the frontend. The backend has no notion of LCD output. Further, all configuration is in the database, so there is no text file to edit. So it might be better to explain what it's doing now and figure out how to get it to do what you want, as I really can't see how enabling LCD output would break anything.

---

### Post by Personatech on 2012-06-18
> **tgm4883 said:**
> With LCD output on, you would still see the frontend. The backend has no notion of LCD output. Further, all configuration is in the database, so there is no text file to edit. So it might be better to explain what it's doing now and figure out how to get it to do what you want, as I really can't see how enabling LCD output would break anything.
Thanks, that gives me something to go by.  I was working with reconfiguring output resolutions - perhaps that's my problem since the only screen output is to a SDTV.  I'll connect a monitor and see if that doesn't give me an avenue to correct the output problem.  I'll let you know...

---

### Post by Personatech on 2012-06-18
I seem to have corrected the problem but, to be honest, I'm not sure what caused it.  It was obviously not a MythTV problem per se - seems to have been rooted in either the mobo BIOS or nVidia graphics driver.  Reset the BIOS, reinstalled driver, works now.  Thanks everybody for stepping in, especially you, tgm4883, as I would have probably been barking up the wrong tree for the rest of the afternoon at least!

---

