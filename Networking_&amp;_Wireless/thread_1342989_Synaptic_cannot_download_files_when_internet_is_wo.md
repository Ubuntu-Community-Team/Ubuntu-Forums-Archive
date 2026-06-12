---
title: "Synaptic cannot download files when internet is working fine."
date: 2009-12-01
forum: Networking &amp; Wireless
---

### Post by MadnessRed on 2009-12-01
I am using the internet fine. I am writing this here, for example on my laptop. However, if I now try and download anything using synaptic it doesn't work. I cannot even reload the package list.It just says downloading file 2 of 256 and stays there. If I press more info it doesn't even appear as though the file has started. There are no entries, its just a blank box.

I have a desktop which also runs Ubuntu and Synaptic, however that is working perfectly, the only difference as the the Desktop is 9.10 and laptop 9.04.

Any help would be great.

Thanks



edit:: I think I have found the problem, some reason it is trying go via a proxy. I have a proxy that I have to use on some networks. However, even though synaptic is configured to connect directly it is still using the proxy. Any ideas how I can stop it?


edit::
I have tried using chrome to apply no proxy system wide.

I have opened up /etc/bash.bashrc and the proxy wasn't defined there.

I have opened up /etc/apt/apt.conf and that file is blank.

I have tried every menu in synaptic in the hope of finding some more proxy settings but nothing. The options at "Settings > Preferences > Network" as blank.

I have tried the KDE package manager and that fails as well.

If I do sudo apt-get update it says:
1%  [Connecting to 172.16.0.205 (172.16.0.205)] [Connecting to 172.16.0.205 (172.16.0.205)] [Connecting to 172.16.0.205 (172.16.0.205)]

I am now going to see if I can fnd any proxy settings in the KDE package manager.


edit::
I have tried to find anything in KPackageKit, no luck, so I pressed the Default button a few times. Still no luck, sudo apt-get update says the same. Please can someone help. I don't understand.

---

