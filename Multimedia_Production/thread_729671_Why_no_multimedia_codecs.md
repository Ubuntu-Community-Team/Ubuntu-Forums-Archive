---
title: "Why no multimedia codecs?"
date: 2008-03-20
forum: Multimedia Production
---

### Post by tshrinivasan on 2008-03-20
Friends.

Ubuntu is fine.
But It needs internet to update the multimedia codecs.

For villages who dont have net connection,
what to do?

---

### Post by Sef on 2008-03-20
You can order a [repository DVD from OSdisc]("http://www.osdisc.com/cgi-bin/view.cgi/products/dvd/ubuntu/repo.html") or another company, which would have the codecs.

[Restricted Formats]("https://help.ubuntu.com/community/RestrictedFormats")

---

### Post by DaV|d on 2008-03-20
You might also want to try this_ if you know what packages you need to download,_ and _can get internet connection from another linux_ computer.

First open up synaptic (**System > Administration > Synaptic Package Manager**) and select all the packages for download. (Take note of which packages you selected)
Afterwards, go to **File > Generate package download script**
Save the generated script to a pendrive (or other portable media), and execute the script on the internet connected computer.
This script downloads the packages you need to the folder it is executed from. Save the downloaded packages on the pendrive.
Start Synaptic on the non-networked computer and re-select the packages you selected before.
Finally, go to **File > Add downloaded package**s and navigate to the folder where you stored the downloaded packages.

Hope this helps! :)

---

