---
title: "Miro will not run without root privelages"
date: 2013-06-08
forum: Multimedia Software
---

### Post by KratosCrux on 2013-06-08
I've installed miro from the PPA as the directions on the website tell me (miro 6.0). The program does not start, but when I run "sudo miro" it seems to work fine. I have tried installing the latest stable build from source but it has the same issue. Is there a way to make Miro always start as root from the launcher, or are there some permissions I need to set to use Miro without sudo? I have tried "sudo chown -R <username> .miro" and "chmod o=rx .miro" but neither have worked. Any input is good input, thanks in advance.

---

### Post by kostkon on 2013-06-08
What messages are you getting when you run it in the terminal (without sudo)?

---

### Post by KratosCrux on 2013-06-08
it only says "using /usr/bin/miro.real" and then immediately returns to console

---

### Post by KratosCrux on 2013-06-11
I had to manually install libtorrent rasterbar6 from [this link]("http://www.ubuntuupdates.org/package/core/quantal/universe/base/libtorrent-rasterbar6") before I could install from source.

Now miro crashed when I restarted and gave me an error:
> 
The crashed program seems to use third-party or local libraries:

/usr/local/lib/python2.7/dist-packages/miro/plat/xlibhelper.so
/usr/local/lib/python2.7/dist-packages/miro/ngrams.so
/usr/local/lib/python2.7/dist-packages/miro/data/namecollation.so
/usr/local/lib/python2.7/dist-packages/miro/frontends/widgets/gtk/fixedliststore.so
/usr/local/lib/python2.7/dist-packages/miro/frontends/widgets/gtk/pygtkhacks.so

It is highly recommended to check if the problem persists without those first.

Do you want to continue the report process anyway?


Is there any proper way to remove the selected libraries?

---

