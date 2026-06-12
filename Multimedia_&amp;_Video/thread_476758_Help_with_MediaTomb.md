---
title: "Help with MediaTomb"
date: 2007-06-17
forum: Multimedia &amp; Video
---

### Post by Narcoleptic_Insomniac on 2007-06-17
Hey guys, I'm new to this UPnP stuff, and read some of the documentation on the MediaTomb site ([www.mediatomb.cc]("www.mediatomb.cc")) and had hard time finding anything. So I'll ask you guys.

My first question is, how do I run any of the commands in terminal? stuff like "--config" or "-c". When I type "mediatomb --config" it just brings up a list of options but I can't actually use them. 

My second, and more important question is, how can I stop mediatomb from searching in certain folders, I am using it on my PS3 and it is always picking up crap in Limewires incomplete folder. I just want it to read my Shared folder and nothing else. I was looking in the xml files with gedit but I am not too smart with the xml stuff so I wasn't sure what to type.

Thanks in advance for the help.

---

### Post by Narcoleptic_Insomniac on 2007-06-17
Help

---

### Post by joshuapurcell on 2007-06-18
Here's from their website:
> Debian and Ubuntu

The best way to install Debian or Ubuntu packages is via our APT repository. To use it properly, you will need our GPG key (for all distributions except &#8220;sarge&#8221;). To install it, issue the following command as root:
wget [http://apt.mediatomb.cc/key.asc](http://apt.mediatomb.cc/key.asc) -O- -q | sudo apt-key add -
(key id: A2DCDB57; fingerprint: F1A6 C581 6BC1 AD55 80E9 EEFE 48AD 7164 A2DC DB57)

Below you will find the appropriate &#8220;deb&#8221; line to add to your /etc/apt/sources.list for all supported distributions and a direct download to the &#8221;.deb&#8221; file in case you don&#8217;t want to use the APT repository. We also provide source packages for these distributions (add the same line, but with &#8220;deb-src&#8221; instead of &#8220;deb&#8221; at the beginning), so you should be able to build MediaTomb for platforms other than i386, AMD64 and ARM.

If you want APT to automatically install all dependencies on Ubuntu, you have to enable the &#8220;universe&#8221; component. (Spidermonkey isn&#8217;t part of the &#8220;main&#8221; component there.) This doesn&#8217;t apply to Debian.

There are basically two ways of starting MediaTomb: you can either start it directly as a normal user or run it as a deamon. For the latter a &#8220;mediatomb&#8221; user and group will be added automatically and you&#8217;ll find the configuration under /etc/mediatomb/config.xml, the logfile under /var/log/mediatomb and the database under /var/lib/mediatomb/. If you want MediaTomb to be started at boot time, change the NO_START option from "yes" to "" in the file /etc/default/mediatomb. To access the UI of the MediaTomb daemon open the file /var/lib/mediatomb/mediatomb.html in your browser.

The binaries for ARM were built on hardware donated by eXcito.

Ubuntu 6.06 LTS (&#8220;dapper&#8221;)

APT (i386, AMD64):
deb [http://apt.mediatomb.cc/](http://apt.mediatomb.cc/) dapper main
i386 .deb: mediatomb_0.9.1-1dapper1_i386.deb
AMD64 .deb: mediatomb_0.9.1-1dapper1_amd64.deb
Ubuntu 6.10 (&#8220;edgy&#8221;)

APT (i386, AMD64):
deb [http://apt.mediatomb.cc/](http://apt.mediatomb.cc/) edgy main
i386 .deb: mediatomb_0.9.1-1edgy1_i386.deb
AMD64 .deb: mediatomb_0.9.1-1edgy1_amd64.deb
Ubuntu 7.04 (&#8220;feisty&#8221;)

APT (i386, AMD64):
deb [http://apt.mediatomb.cc/](http://apt.mediatomb.cc/) feisty main
i386 .deb: mediatomb_0.9.1-1feisty1_i386.deb
AMD64 .deb: mediatomb_0.9.1-1feisty1_amd64.deb

[http://mediatomb.cc/pages/download](http://mediatomb.cc/pages/download)

---

