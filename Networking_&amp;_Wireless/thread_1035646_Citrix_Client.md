---
title: "Citrix Client"
date: 2009-01-09
forum: Networking &amp; Wireless
---

### Post by broecher on 2009-01-09
I have Hardy with gnome. I tried to follow the directions at:
 
[https://help.ubuntu.com/community/CitrixICAClientHowTo](https://help.ubuntu.com/community/CitrixICAClientHowTo)

and when I get to the installing of the client:

sudo ./setupwfc

it says command not found. When I navigate to the folder and attempt to "run in terminal", the terminal window flashes on the screen, disappears, and no dialog box opens as described in the how-to. If I select "run" nothing happens.

Any suggestions?

---

### Post by PilotJLR on 2009-01-10
It sounds like you are not in the right directory.

Are you sure you followed this verbatim:
```

  mkdir /tmp/citrix-install
  cd /tmp/citrix-install
  mv ~/Desktop/en.linuxx86.tar.gz ./
  tar xvf en.linuxx86.tar.gz

```

If so, then change back into the directory where you ran the tar command and post the output of "ls"

ALSO - did the "mv" command post an error? Are you sure you downloaded this en.linuxx86.tar.gz file onto your desktop? Can you SEE this on your desktop?

---

### Post by broecher on 2009-01-10
OK, I was copying and pasting without changing anything. After the mv command it disappeared from the desktop but wasn't going to the citrix-install directory.I guess I do not understand the function of the "./" in the command. The citrix install folder was empty even after the tar command.

Using the graphical interface, I dragged and dropped the tar.gz file into the citrix-install folder. Then I went back to terminal and changed directory to that folder, typed the command "sudo ./setupwfc" and it worked no problem.

Well, thanks, now I am off to figure the security certificate out...

---

