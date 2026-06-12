---
title: "Question about X over SSH"
date: 2009-12-11
forum: Networking &amp; Wireless
---

### Post by pepsifx357 on 2009-12-11
By using the sudo ssh -X command, logging into a networked computer, then running an application, does the process, or computing power come from the computer you are using, or the computer you are logged onto?

---

### Post by lewisforlife on 2009-12-11
The computer you are logged onto, with the exception of the processing required to display the graphics on your computer.  For instance, if you were rendering a 3d model through ssh, the remote computer that you are connected to does the processing to render the model.

---

### Post by pepsifx357 on 2009-12-11
> **lewisforlife said:**
> The computer you are logged onto, with the exception of the processing required to display the graphics on your computer.  For instance, if you were rendering a 3d model through ssh, the remote computer that you are connected to does the processing to render the model.

Thanks!

---

