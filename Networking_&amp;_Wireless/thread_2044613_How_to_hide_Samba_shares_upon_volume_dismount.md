---
title: "How to hide Samba shares upon volume dismount?"
date: 2012-08-19
forum: Networking &amp; Wireless
---

### Post by zamar28 on 2012-08-19
I configured Samba server on a Linux machine and can browse its shares on Win7 PC and another Linux PC. But when I dismount a shared volume on Linux server, its still remain visible as a shared drive in Win Explorer - Network (I don't assign a drive letter to it), and I can browse this empty share folder.

 If I stop Samba, the shared drives disappear - at times after reloading Explorer - or if not, the folders are no longer browsable.

 So my question is, how to configure Samba server via terminal to automatically hide shared folders on a client PC (Windows or Linux), when the volume is unmounted from the folder on the server? Does it require running some extra script or just editing Samba config file?

 As a separate question, how to delete obsolete Samba shares from Win Explorer after shutting down Linux machine or Samba daemon, if they persist? Any command I can run on Linux machine to do that?

---

### Post by zamar28 on 2012-08-20
I'm surprised standard Samba package doesn't have such feature... Why leave empty folders around the network?

---

### Post by zamar28 on 2012-09-01
Is there a dedicated Samba forum anywhere on the net? Or a mailing list?

---

