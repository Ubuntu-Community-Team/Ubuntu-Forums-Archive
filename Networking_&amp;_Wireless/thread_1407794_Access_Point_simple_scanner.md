---
title: "Access Point simple scanner"
date: 2010-02-15
forum: Networking &amp; Wireless
---

### Post by pcolamar on 2010-02-15
HI there,
  I am lookin gfor a simple AP scanner able to tell me the list of SSID around me and the channels they use.
I am  having some problem with channel overlap with several A.P. located around my apartment.
Please something simple and, possibly, with a GUI.

No WEP/WPA crack or whatsoever is requested, just the simple list of SSID and channel associated list.

Any suggestion ?

Palmer

------
Solved using the Swscanner package (.deb) downloaded directly from the swscanner.org website. The official version in Synaptic does not work for me

---

### Post by pcolamar on 2010-02-16
Bump !

---

### Post by underquark on 2010-02-16
What ones have you tried and what problems have you had with them or what have they not done that you wanted them to?

---

### Post by pcolamar on 2010-02-16
underquark, I have tried the SWscanner available under Synaptic but it crashes.
I thought it was a problem related to the fact that SWscanner runs uder KDE and I use gnome but few seconds ago I found a post pointing me to the version available diirectly from [http://www.swscanner.org]("http://www.swscanner.org") and actually although they have the same release number, the .deb dowloaded directly from swscanner.org works fine.

Thanks anyhow.

---

### Post by underquark on 2010-02-16
You can try this from the command line:

sudo iwlist scanning

---

