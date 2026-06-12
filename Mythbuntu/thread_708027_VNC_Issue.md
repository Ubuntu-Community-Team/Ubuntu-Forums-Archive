---
title: "VNC Issue"
date: 2008-02-25
forum: Mythbuntu
---

### Post by Lutiana on 2008-02-25
Hi all.

Here is the issue I am having. 

I am using Mythbuntu 7.10.

VNC was working just fine, but I changed my resolution to 1024x768 (from the native of my LCD panel, 1280 by something) and since then all I get in the realVNC client on my windows box is a scrambled image. See the attached image.

I am completely stumped on this issue, all the resources on the web tell me to edit various files that I simply do not have (at least not in the standard places).

Any help would be GREATLY appreciated.

---

### Post by straxus on 2008-02-29
I'm having the same problem.  Also using Mythbuntu 7.10.  It happened after changing resolution while connected via VNC.

---

### Post by straxus on 2008-02-29
Ah ha!  Fixed!

in /etc/X11/xorg.conf under the "Screen" section, comment out the line that begins with "Virtual".  Save, and restart X.  You'll be good to go.

---

### Post by DavidWhyte on 2008-03-10
I don't seem to have that lin in my xorg.conf file. Are there any other ways to fix it?

---

### Post by thatkidandy on 2008-03-11
I am also having this issue, below is my setup for the relevant XORG setup. Suggestions? I don't see/understand the 'virtual' fix mentioned...
```

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation Integrated Graphics Controller"
        Monitor         "Generic Monitor"
        Defaultdepth    16
        Option          "SecurityTypes" "VncAuth"
        Option          "UserPasswdVerifier"    "VncAuth"
        Option          "PasswordFile"  "/root/.vnc/passwd"
EndSection

Section "Module"
        Load            "vnc"
EndSection
```

---

### Post by DavidWhyte on 2008-03-12
I am not at home so I can't try, but someone has indicated to me the following:

> The answer is thus:

Subsection "Display"
...#blah .. your display modes here

Virtual 1024 768  #That's the chestnut! Mine was 1280 1024 when desktop was 1024 768
EndSubsection


Let me know if it works :)

---

### Post by DavidWhyte on 2008-03-12
Actually, I don't have any 'Virtual' line in my config, which is what I said already, so that didn't help *any*.

I have found a bug upstream though but it looks quite dormant.

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=431430](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=431430)

Cheers,
Whytey

---

