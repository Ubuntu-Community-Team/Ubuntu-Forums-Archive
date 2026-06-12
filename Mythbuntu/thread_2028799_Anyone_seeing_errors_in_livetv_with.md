---
title: "Anyone seeing errors in livetv with"
date: 2012-07-18
forum: Mythbuntu
---

### Post by speed32219 on 2012-07-18
"Video Frame Buffering Failed Too Many Times"?  running .25.1 frontend only with latest fixes.  Had it happen before ocassionaly but after latest updates using repo it seems to be getting worse. Going to try the BE/FE combo and see if it fails at the same time. I'm using a 10/100 network, maybe I need more BW, but I usually only have one TV running when the failure happens.  Sometimes it locks the FE and I need to kill the process and re-start the FE to get it back working again.

**EDIT:** It seems that my FE (networked only) was running .25.0, I thought I had upgraded it.  I removed the FE and re-installed it from the PPA, it updated to 25.1+fixes and my BE/FE errors are gone.  FE is now stable, backend I still get massive "ringbuffer Waited 0.2 seconds for data #012#011#011#011to become available" posting in the log.  Seraching I have found that many ppl have these so it must just be part of mythtv functionality.  If so would be nice to remove the posting to the log. Otherwise it is nice to have it stable again.  Setting the BE to update from the repos and **not** setting the networked frontend PC's to update is not a good practice.

---

