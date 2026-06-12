---
title: "Intel GMA900 and X.org"
date: 2006-01-26
forum: Multimedia &amp; Video
---

### Post by audax321 on 2006-01-26
Hello,

I was just wondering how everyone had their GMA900 configured. I have a Pentium M 2.0 Ghz HP DV1000 notebook where I get about 818 fps in glxgears (yeah I know its not a good benchmark :) ). Anyway I was just wondering how it was working out for others. Also, I've read that it is now supposed to be possible to get composite running on it smoothly (transparency, shadows, etc.)... any idea how to do this because composite still runs pretty slow for me. Also anyone have any info about when Luminosity is going to be incorporated into Metacity. I heard it will run on much older video cards and is supposed to come out before Vista, but I haven't heard much about how its maturing.

Thanks..

---

### Post by darm on 2006-01-26
The default Breezy drivers seem to be a bit crappy. I can't normally play DVDs fullscreen and Exult is rather slow in high resolutions.

I'm going to try Dapper livecd this evening (evening is coming in about 6-7 hours here in Moscow) and check if X11R7 helps.

---

### Post by audax321 on 2006-01-26
Let me know how it works out. I read here:
[http://gentoo-wiki.com/HARDWARE_Gentoo_on_HP_Compaq_nc6220#X_Configuration](http://gentoo-wiki.com/HARDWARE_Gentoo_on_HP_Compaq_nc6220#X_Configuration)
that the GMA900 can be used with composite, transparency and all. The setup is for Gentoo though. On second look I think the drivers on Breezy are bad because its using version 6.8.2 of x.org. The how-to says you need at least 6.8.99.8. :(  So hopefully Dapper will perform much better :)

---

### Post by darm on 2006-01-27
well, you already know my experiment with new X from dapper has been unsuccessful =)

but I've just found this link: [intel drivers]("http://downloadfinder.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=2159&OSFullName=Linux%2A&lang=eng&strOSs=39&submit=Go%21")

You might as well give it a try instead of upgrading X. Wish I found that earlier myself!

---

### Post by Rollmops on 2006-01-27
[QUOTE=darm]The default Breezy drivers seem to be a bit crappy. I can't normally play DVDs fullscreen and Exult is rather slow in high resolutions.[/QUOTE]
Do you use xine or gstreamer? With totem-xine i can play DVDs without problems. Even in fullscreen with a resolution of 1400x1050. The gstreamer version instead seems to have some problems.

---

