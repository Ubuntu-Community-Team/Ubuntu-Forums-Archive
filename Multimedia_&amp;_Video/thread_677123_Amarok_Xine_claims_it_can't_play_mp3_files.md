---
title: "Amarok: Xine claims it can't play mp3 files"
date: 2008-01-24
forum: Multimedia &amp; Video
---

### Post by barney_1 on 2008-01-24
I have long used Amarok to play mp3 files without any problems.  Today I opened Amarok and received the message "Amarok currently cannot play mp3 files" and asked if I would like to install the codecs.  I answered "no" because the codecs are already installed.  I then get the popup message:
"xine claims it can't play mp3 files".

I have had a couple of updates since I last tried using Amarok, I believe a bum update might be the culprit  

Any ideas on a fix for this?

Thanks!

-Mike

---

### Post by Lord Illidan on 2008-01-24
Does xine itself play mp3 files? Test it on your system.

---

### Post by lespaul_rentals on 2008-01-24
So, let me get this straight...

You're saying that Amarok won't play mp3s, when it specifically asked you if you wanted to install support, and you clicked no?  The xine plugin will automatically install itself if you click "Yes" when it asks you if you want to install.  An update could have caused the problem, but you should click "Yes" when it asks you.

---

### Post by Yellow Pasque on 2008-01-24
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by TorchlightJay on 2008-01-24
Try updating your xine and amarok. We had the same problem and installed the newest versions from source and it worked fine.

---

### Post by james_xxx on 2008-01-24
I have been having the very same problem on this laptop for the last few weeks, None of the suggested solutions I have tried have helped.

---

### Post by BladeOfAnduril on 2008-01-25
I have the exact same issue.  By the way, choosing "Yes" in Amarok when asked if you want to install mp3 support does nothing.  I hope there is a fix soon.

---

### Post by contialdo on 2008-01-25
Hi,

I know it might sound very silly and I did not really understand it myself, but.... I had the same problem, I got mad for a couple of days and then I found the solution on an Italian forum:

1) close all your audio applications
2) delete the .xine directory from your home
3) enjoy again your music.

I hope it works for you too.

Bye
Aldo

---

### Post by barney_1 on 2008-01-25
> **contialdo said:**
> Hi,

I know it might sound very silly and I did not really understand it myself, but.... I had the same problem, I got mad for a couple of days and then I found the solution on an Italian forum:

1) close all your audio applications
2) delete the .xine directory from your home
3) enjoy again your music.

I hope it works for you too.

Bye
Aldo

This method absolutely fixed my problem.  Thank you!

---

### Post by james_xxx on 2008-01-25
Thank you very much, sir. That did the trick! :)

---

