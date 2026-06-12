---
title: "Songbird Problem"
date: 2007-10-28
forum: Multimedia &amp; Video
---

### Post by Neo4 on 2007-10-28
can anyone tell me how do I put the Album applet working on the 0.3rc? i have shockwave plugin and javascript debugger but in [www.java.com](www.java.com) if i click on see if java is installed it says no...
but on firefox says yes.

thanks

---

### Post by 4KvRMU7Nnv on 2007-11-24
are you using 64 bit ubuntu?

---

### Post by Neo4 on 2007-11-24
nop

---

### Post by employeeno5 on 2007-11-29
I have this same issue. Java 6 run time environment is fully installed and working in my Gutsy 7.10 and the Firefox plugin as well.
Java tests as working correctly with the latest version in Firefox, but not working in Songbird. I need to get it running in Songbird and the only installation instructions I've found indicate to just install Java, which as I said already is installed. Everywhere I've looked including the Songbird support stuff seems to think that if Java is installed for Firefox than it's also installed for Songbird, which seems reasonable enough, but it just isn't the reality on my computer. 
Any help would be great.

---

### Post by employeeno5 on 2007-12-01
To the original poster,

As I posted above I have the same issue of having Java installed and working in Ubuntu and the plugin running in Firefox, but not in Songbird. The documentation for the sun-java6-plugin says that it should set-up automatically for firefox and any other mozzila based browsers (this includes songbird). So, I attempted to reinstall my java runtime environment and java plugin. They sucessfully reinstalled and are working everywhere they were before but still do not work in songbird. 
Someone told me that copying the contents of the firefox extension folder into your songbird extension folder would work. I tried this also and had not effect.
Maybe these approaches will work for you though if you've not yet tried them. Otherwise, I'm at a loss and any help from anyone would be much appreciated. Goodluck!

---

### Post by employeeno5 on 2007-12-01
Aha! I've got it working
So yes, this is very simple. I should figured it out sooner. Copy the contents of you firefox plugins directory to you songbird plugins directory. Someone had told me to try this with the extensions directory but they probably meant plugins, because after all java is a plugin for mozilla not an extension. I don't know why I didn't reason that out sooner. Your firefox plugin directory is probably on this path /urs/lib/firefox/plugins and your  songbird plugins folder is in whatever directory you unpacked songbird to. This worked for me. Hope it works for you.

---

### Post by boyofford on 2008-01-30
> **employeeno5 said:**
> Aha! I've got it working
So yes, this is very simple. I should figured it out sooner. Copy the contents of you firefox plugins directory to you songbird plugins directory. Someone had told me to try this with the extensions directory but they probably meant plugins, because after all java is a plugin for mozilla not an extension. I don't know why I didn't reason that out sooner. Your firefox plugin directory is probably on this path /urs/lib/firefox/plugins and your  songbird plugins folder is in whatever directory you unpacked songbird to. This worked for me. Hope it works for you.

That sort of helped, I may still being stupid LOL,
[www.java.com](www.java.com) now says I have the correct java installed when tested through songbird, but still not got Album Applet working. 
I will post if i find solution...........

---

