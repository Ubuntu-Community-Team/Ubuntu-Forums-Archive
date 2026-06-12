---
title: "PiP (Picture in Picture) does nothing"
date: 2009-02-03
forum: Mythbuntu
---

### Post by laffinet on 2009-02-03
Hi !

I've successfully installed a Dvico Fusion Dual 4 rev.2 and it's working ok (sometimes get artefacts and digital picture noise, but that's a different issue).

However, PiP (picture in picture) is not working. When I select the option during LiveTv, nothing happens. Any ideas ?

---

### Post by scary_jeff on 2009-02-04
Have you configured both tuners in the backend configuration? A single card with more than one tuner needs each tuner to be set up individually.

If you have, check /var/log/mythtv/mythfrontend.log after trying to enter PiP mode, and see if it gives any errors.

---

### Post by laffinet on 2009-02-04
Thanks for the tip, did have both tuners working though.

I have PiP working since yesterday. Might have just been that I used the wrong buttons on the remote.

I went into the menu, highlightet PiP, highlighted Enabble/Disable and pressed OK. Nothing happened.
Did the same thing again, but pressed the "right cursor button" after highlighting enable/disable and it worked.

---

