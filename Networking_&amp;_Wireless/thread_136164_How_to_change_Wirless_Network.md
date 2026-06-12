---
title: "How to change Wirless Network????"
date: 2006-02-25
forum: Networking &amp; Wireless
---

### Post by mexlinux on 2006-02-25
Hi: I have posted this on kubuntu, I think that was the wgrong forume, and this should be the right one.. so here it goes, sorry for the double post.

Hi:
I have just installed kubuntu, during installation it detected wifi, and asked for WEP key, did manual config, and gave static IP..... That was in my office.

Now, I'm at home, on a diffrent network, and, it does not work...
BUT I do not know wehre to modify and which values???

I do not have network on the laptop, please help or point to the instructions.

Please don't point to installing packages instructions, since I have not network, so I can't install.... but everithing should already be installed since it worked at the office.

In mandriva there was a nice tool net_applet showing all the avialble conections, and allowing you to change the network, what will be the kubuntu alterative?

Thanks,
Miguel

---

### Post by Lambert on 2006-02-25
I don't use kubuntu and have little experience with kde but believe there is an app called kwifi manager that you can use to manage wireless connections.

[http://docs.kde.org/stable/en/kdenetwork/kwifimanager/index.html](http://docs.kde.org/stable/en/kdenetwork/kwifimanager/index.html)

---

### Post by aosmith on 2006-02-25
for what its worht in ubuntu you would use:
System->Administration->Networking
then select your wirless card hit properties...

---

### Post by mexlinux on 2006-02-25
OK, I solved the hard way....
Since I have home in it,s own partition.... reinstalled kubuntu! so the wilress was detected again during installation.
(Yes it might me stupid, but worked)

After installation I got internet, did some reserch, and then decide to install wifi-radar, this is the solution, and MUST be placed in the standard packages (kwifimanager sucks).

The menu added from installation called the kdesu replacement gtk program , so it does not work from menu, and I had to modify menu entry.

Solved now.

By the way, it's own partition from home shuld also be the default configuration, why don't kubuntu does that?

Regards,
Miguel

---

